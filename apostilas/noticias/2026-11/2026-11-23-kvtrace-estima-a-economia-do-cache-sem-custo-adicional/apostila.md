# KVTrace estima a economia do cache sem custo adicional

_2026-11-23 · noticia_

A AWS apresentou uma skill no Agent Toolkit for AWS que avalia e configura cache distribuído de KV para LLMs hospedados em GPUs. O fluxo começa pela leitura da frota, estima a economia com o tráfego real pelo KVTrace e só cria infraestrutura depois de confirmar que a economia cobre o custo. Ao ler esta apostila, você vai entender o prefill, o ponto de virada entre ler e recalcular o cache e a função do LMCache no vLLM ou SGLang. Também vai saber quais requisitos conferir, como proteger prompts sensíveis e validar a implantação antes de enviar tráfego de produção.

## O fato

A AWS apresentou, no Agent Toolkit for AWS, uma skill que orienta o agente de código a avaliar e configurar cache distribuído de KV para LLMs hospedados em GPUs. A proposta é decidir com dados da própria frota antes de criar qualquer recurso pago.

O fluxo cobre quatro trabalhos: diagnosticar um primeiro token lento, dimensionar e precificar o cache, montar a infraestrutura e corrigir uma falha de transferência. A skill funciona com Kiro, Claude Code, OpenAI Codex e outros agentes que suportam Agent Skills.

O anúncio cita redução de até 40% no custo de inferência e de até 80% no tempo até o primeiro token. Esses tetos variam conforme o modelo, o tráfego e o roteamento dos prompts.

Fonte: <https://aws.amazon.com/blogs/machine-learning/cut-self-hosted-llm-cost-and-latency-with-the-distributed-kv-caching-agent-skill/>

## Por que isso importa

Hospedar LLMs em GPUs dá controle sobre custo, precisão e latência, mas cria um desperdício comum: o mesmo contexto é recalculado a cada turno. Agentes de código, chats e assistentes de perguntas sobre documentos reenviam históricos que crescem ao longo da conversa.

Os caches pequenos de cada servidor têm capacidade limitada e ficam isolados. Quando outra GPU recebe a conversa, ela pode não ter aquele histórico na memória. O servidor então recalcula os estados de atenção de chave e valor, conhecidos como KV, para todos os tokens do contexto. Esse trabalho é o prefill e acontece antes de a resposta começar.

Um assistente jurídico ilustra o problema. Ele pode acumular centenas de milhares de tokens com o histórico de um caso. Se a pessoa volta depois do almoço, outra GPU pode receber a solicitação sem esse histórico, e a resposta pode levar minutos. O cache distribuído cria uma camada compartilhada para que qualquer servidor da frota reutilize o estado KV.

Fonte: <https://aws.amazon.com/blogs/database/announcing-distributed-kv-caching-for-self-hosted-llms-with-amazon-elasticache/>

## Como funciona o cache distribuído de KV

O cache distribuído de KV coloca uma camada compartilhada ao lado da frota de GPUs. Ela guarda os estados de atenção que já foram calculados e permite que outro servidor os encontre. O estado pode ser reutilizado por dias, atravessando sessões, mudanças de roteamento e falhas de servidores.

Em um acerto, o servidor lê o KV pelo Remote Direct Memory Access, ou RDMA, e evita refazer o prefill daquele contexto. Em uma falha, o trabalho de gerar o estado precisa acontecer novamente. Para que os servidores encontrem as mesmas entradas, todos usam o mesmo mecanismo de identificação por hash e seed e o mesmo tipo de dados KV.

Ler o cache também tem custo de tempo. Em prompts curtos, carregar o estado pela rede pode demorar mais do que recalculá-lo. Acima de determinado comprimento, chamado de ponto de virada, a leitura passa a ganhar. Esse limite e a frequência com que os prompts se repetem definem se o cache compensa.

Fonte: <https://aws.amazon.com/blogs/database/announcing-distributed-kv-caching-for-self-hosted-llms-with-amazon-elasticache/>

## O que a skill do Agent Toolkit for AWS faz

Uma Agent Skill reúne orientações que o agente de código carrega para executar um fluxo específico. No Kiro, o agente pede aprovação antes de carregar a skill. Depois disso, ela conduz a verificação de compatibilidade, o dimensionamento, a configuração para teste ou produção e a solução de problemas de cache.

A skill adiciona o conector LMCache ao vLLM ou ao SGLang que já está em uso. Isso inclui workers do vLLM executados em estruturas de serviço como llm-d e Ray Serve. O roteamento e as configurações do motor são preservados, para que a mudança de cache não exija trocar toda a pilha de inferência.

A configuração também padroniza hash, seed e tipo de dados KV entre os servidores. Essa uniformidade evita chaves incompatíveis, quando um servidor grava um estado que os outros não conseguem encontrar. Antes da produção, o fluxo esvazia os níveis locais e compara duas execuções com carregamento do cache. Criar, alterar ou excluir recursos exige aprovação explícita.

Fonte: <https://github.com/aws/agent-toolkit-for-aws/tree/main/skills/specialized-skills/database-skills/distributed-kv-caching>

## Etapa 1: diagnosticar e ler a frota

A avaliação começa com uma chamada somente leitura ao describe-instances. Ela lista as instâncias de GPU e conta as interfaces Elastic Fabric Adapter, ou EFA. O agente usa o que consegue observar e pergunta apenas pelos dados que faltam.

Entre esses dados estão o motor de inferência, o modelo, o tamanho de tensor paralelo, o tipo de dados KV, o preço do servidor e a frequência de repetição dos prompts. No diagnóstico do assistente jurídico, a conversa também levanta número de réplicas, roteamento e tempo de espera entre os turnos.

O agente identifica se a latência vem de prefill a frio e verifica se o caso se encaixa na solução. Quando algum requisito não corresponde, ele interrompe o fluxo e explica o motivo. Essa parada acontece antes de qualquer gasto com cache.

Fonte: <https://aws.amazon.com/blogs/machine-learning/cut-self-hosted-llm-cost-and-latency-with-the-distributed-kv-caching-agent-skill/>

## Primeiro, verifique o cache que já existe

Antes de avaliar infraestrutura compartilhada, o agente procura ajustes que não exigem novos recursos. Se o prefix caching estiver desligado, reativá-lo pode acelerar turnos consecutivos porque o servidor reaproveita partes do contexto já processado.

A afinidade de sessão também muda o resultado. Ela mantém a conversa no mesmo servidor para aproveitar o cache local. Se a taxa de acerto do cache de prefixo já estiver acima de 90% com afinidade de sessão, pode não haver necessidade de um cache KV compartilhado. Essa verificação evita pagar por uma camada que não resolve um problema presente na frota.

Fonte: <https://aws.amazon.com/blogs/machine-learning/cut-self-hosted-llm-cost-and-latency-with-the-distributed-kv-caching-agent-skill/>

## Etapa 2: estimar a economia com o KVTrace

O KVTrace estima os benefícios a partir do modelo e do tráfego da própria operação antes da criação de infraestrutura, sem custo adicional. Ele registra eventos de cache do vLLM ou do SGLang e reproduz esses eventos offline contra caches compartilhados de vários tamanhos candidatos.

A gravação acontece em cada servidor de GPU durante uma janela representativa, como um dia útil completo. O relatório usa os hashes de blocos e a contagem de tokens para estimar a taxa de acerto e testar capacidades. Quando essa taxa não foi informada, o agente apresenta cenários e recomenda o KVTrace para medi-la.

No dimensionamento do exemplo com 8 instâncias p5, o agente consultou os preços de GPU e do nó de cache na lista de preços da AWS. A taxa de prefill e o tamanho do KV vieram de benchmarks. Cada número precisa manter essa procedência para que a recomendação não pareça mais certa do que os dados permitem.

Fonte: <https://github.com/aws-samples/amazon-elasticache-samples/tree/main/kvtrace>

## Privacidade e isolamento entre tenants

Os traces do KVTrace guardam hashes de blocos e contagem de tokens. O gravador não escreve IDs de tokens nem o texto dos prompts. Como os hashes vêm do conteúdo dos tokens, prompts sensíveis pedem a opção de anonimização indicada pela AWS.

Um cache compartilhado também cria uma questão entre tenants. Pelo tempo de resposta, um tenant pode perceber se outro tenant enviou o mesmo texto. Casos que precisam ficar isolados usam caches separados. Quando os tenants compartilham o cache, cada um adiciona seu próprio ID ao hash do KV para manter a distinção no mecanismo de identificação.

```
--anonymize-key-file
```

Fonte: <https://github.com/aws-samples/amazon-elasticache-samples/tree/main/kvtrace>

## Requisitos para estimar e configurar

Os fluxos de estimativa e configuração dependem de uma pilha compatível. As versões abaixo fazem parte dos pré-requisitos descritos no anúncio e devem ser verificadas antes de seguir para a implantação.

O requisito do ElastiCache vale quando o objetivo inclui montar o cache. A etapa de diagnóstico e estimativa acontece antes dessa infraestrutura existir.

- Use um agente de código que suporte Agent Skills, como Kiro, Claude Code ou OpenAI Codex.
- Use instâncias de GPU compatíveis com escrita EFA RDMA, como as instâncias p5.
- Tenha LMCache 0.5.8rc1 ou posterior e vLLM 0.11.1 ou posterior; para SGLang, use 0.5.13 ou posterior.
- Para montar o cache, use ElastiCache for Valkey 9.1 ou posterior em nós cache.i8ge.48xlarge.

Fonte: <https://aws.amazon.com/blogs/machine-learning/cut-self-hosted-llm-cost-and-latency-with-the-distributed-kv-caching-agent-skill/>

## Etapa 3: montar o cache compartilhado

Depois da estimativa, o agente propõe a quantidade de nós e o preço. Antes de criar qualquer recurso, ele pede confirmação para montar os nós sugeridos na Availability Zone escolhida. Com a aprovação, cria o security group com permissões de EFA e um cluster Valkey 9.1 com grupo de parâmetros personalizado e políticas de eviction.

O LMCache recebe um usuário de cache próprio, com a senha armazenada no AWS Secrets Manager. O agente prepara os servidores de GPU e inicia um servidor LMCache para cada servidor de GPU. O conector passa a integrar o motor de inferência existente, mantendo o roteamento e as configurações da frota.

A configuração dos servidores usa um único mecanismo de KV ID, baseado em hash e seed, e um tipo de dados KV explícito. Esses ajustes precisam coincidir entre os participantes para que uma entrada gravada por um servidor possa ser encontrada pelos demais.

Fonte: <https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/distributed-kv-caching-getting-started.html>

## Verificação e falhas de transferência

A implantação é verificada com um pequeno objeto de teste. O agente confirma que prompts repetidos carregam o estado KV do cache por RDMA. Na frota de GPUs, a participação medida do L2 é comparada com a previsão do KVTrace.

Antes de receber tráfego de produção, os níveis locais são esvaziados e duas execuções com carregamento do cache precisam produzir a mesma saída. Uma incompatibilidade de layout pode gerar contadores de acerto saudáveis e respostas erradas. Por isso, o número de acertos sozinho não valida a configuração.

O fluxo de solução de problemas mostra um sintoma diferente: o servidor LMCache se conecta ao cluster e BLOB.RDMA_HELLO tem sucesso, mas as transferências de dados falham. O comando INFO largeobj mostra rdma_write_errors aumentando. A causa provável indicada pela skill é um security group que bloqueia tráfego EFA entre seus próprios membros. O agente então fornece comandos para verificar e corrigir a regra.

```
INFO largeobj
```

Fonte: <https://aws.amazon.com/blogs/machine-learning/cut-self-hosted-llm-cost-and-latency-with-the-distributed-kv-caching-agent-skill/>

## Os números

Os tetos de desempenho vieram do anúncio do cache distribuído de KV. Eles não definem o resultado de qualquer frota. O valor efetivo depende do modelo, do padrão de tráfego, do roteamento e do ponto de virada entre ler e recalcular o contexto.

Os demais valores pertencem a exemplos específicos. Cada um indica o cenário em que foi usado e o limite da conclusão que se pode tirar dele.

- Até 40%: teto citado para redução do custo de inferência com cache distribuído de KV. A economia financeira depende de rodar menos servidores ou atender mais tráfego nos mesmos servidores.
- Até 80%: teto citado para redução do tempo até o primeiro token. A medida não representa a duração total da resposta e varia conforme a operação.
- 64K tokens: tamanho de contexto do assistente jurídico no exemplo de diagnóstico com instâncias p5. Indica o histórico que pode ser reprocessado, não o tamanho da resposta.
- 13 segundos: tempo até o primeiro token no retorno das conversas desse assistente jurídico, quando a GPU recalcula todo o histórico. É um caso específico de prefill a frio.
- 8 instâncias p5: frota usada no exemplo de dimensionamento para um assistente RAG de vários turnos. O número não é uma recomendação geral.
- 64.000 tokens: comprimento dos prompts servidos por essa frota no exemplo de estimativa. O valor orienta o cenário de custo, mas não substitui a medição da taxa de acerto.
- 2 nós cache.i8ge.48xlarge: recomendação do agente para o exemplo de 8 instâncias p5, após consultar preços e benchmarks. Outros tráfegos podem exigir outra capacidade.
- Acima de 90% de taxa de acerto no cache de prefixo com afinidade de sessão: condição em que pode não ser necessário um cache KV compartilhado. Refere-se ao cache local e ao roteamento com afinidade.
- 90% do teto de economia: capacidade recomendada no relatório de tráfego sintético de demonstração do KVTrace. O relatório escolhe a menor capacidade que alcança essa parcela do teto estimado.

Fonte: <https://aws.amazon.com/blogs/machine-learning/cut-self-hosted-llm-cost-and-latency-with-the-distributed-kv-caching-agent-skill/>

## O que muda para você

Exemplo: um assistente jurídico usa contextos de 64K tokens em instâncias p5. Quando a conversa volta após o almoço, o primeiro token leva 13 segundos porque a GPU recalcula o histórico completo. O diagnóstico identifica prefill a frio e verifica primeiro se o prefix caching e a afinidade de sessão já resolvem o caso.

Se a camada compartilhada for adequada, o estado KV calculado por outra GPU poderá ser reutilizado no lugar desse prefill. A estimativa precisa confirmar que o tempo economizado cobre o preço do cache. O exemplo jurídico também exige separar casos sensíveis ou incluir o ID do tenant no hash quando houver compartilhamento.

A mesma lógica vale para agentes de código retomados, assistentes agênticos e ferramentas de perguntas sobre documentos que reenviam contexto. O tempo de GPU liberado só vira economia se a operação rodar menos servidores ou atender mais tráfego nos mesmos servidores.

Fonte: <https://aws.amazon.com/blogs/machine-learning/cut-self-hosted-llm-cost-and-latency-with-the-distributed-kv-caching-agent-skill/>

## O que fazer hoje

Siga a sequência de diagnóstico antes de aprovar infraestrutura. Cada etapa produz uma informação necessária para a decisão seguinte.

1. Carregue a skill oficial de cache distribuído de KV em um agente que suporte Agent Skills para que ele reconheça o fluxo de avaliação e configuração.
2. Descreva o motor, o modelo, o tamanho de TP, o tipo de dados KV, o preço do servidor, a repetição dos prompts, as réplicas, o roteamento e a espera entre turnos para que o agente consiga verificar a frota e o cenário.
3. Confira se o prefix caching está ativo e meça a taxa de acerto com afinidade de sessão antes de pedir um cache compartilhado; o resultado mostra se já existe uma solução local suficiente.
4. Defina a exigência de isolamento dos tenants no planejamento, usando caches separados para casos isolados ou o ID do tenant no hash quando o cache for compartilhado.
5. Grave eventos com o KVTrace em cada servidor de GPU durante uma janela representativa, como um dia útil completo, usando a opção de anonimização para prompts sensíveis; o resultado será um conjunto de traces com hashes e contagem de tokens.
6. Compare os cenários de economia com o custo do cache e verifique a origem dos preços, da taxa de prefill e do tamanho do KV; a decisão de seguir exige que a economia estimada cubra o custo.
7. Peça a configuração somente após confirmar a quantidade de nós, a Availability Zone e o preço estimado; o resultado esperado será o cluster, as permissões e a integração do LMCache com o motor existente.
8. Valide prompts repetidos por RDMA, compare a participação do L2 com a previsão e repita duas execuções com os níveis locais vazios; só siga para produção se as saídas coincidirem.
9. Planeje como usar a capacidade liberada, reduzindo servidores ou aumentando o tráfego atendido nos mesmos servidores, para transformar o ganho de GPU em economia financeira.

Fonte: <https://github.com/aws/agent-toolkit-for-aws/tree/main/skills/specialized-skills/database-skills/distributed-kv-caching>

## O que conferir

Os pontos abaixo mudam a decisão entre avaliar, instalar ou manter o cache. Eles também indicam onde uma métrica isolada pode levar a uma conclusão errada.

- Trate os 40% de economia e os 80% de redução do primeiro token como tetos do anúncio, usando o KVTrace para estimar o resultado da sua frota.
- Considere o ponto de virada e a repetição dos prompts, porque carregar o KV pode ser mais lento do que recalculá-lo em prompts curtos.
- Separe a avaliação sem custo adicional do custo da infraestrutura de cache e interrompa a proposta quando a economia estimada não cobrir esse custo.
- Quando a taxa de acerto não tiver sido medida, trate os cenários como cenários até concluir a gravação representativa com o KVTrace.
- Mantenha hash, seed e tipo de dados KV iguais entre os servidores para evitar entradas que são gravadas mas não podem ser encontradas.
- Esvazie os níveis locais e compare a saída de duas execuções antes da produção, porque acertos contados não garantem respostas corretas.
- Proteja prompts sensíveis com a opção de anonimização e respeite o isolamento entre tenants, já que hashes derivam do conteúdo e o tempo de resposta pode revelar repetição de texto.
- Exija aprovação explícita para criar, alterar ou excluir recursos e confirme quantidade de nós, Availability Zone e preço estimado antes da criação.
- Verifique as permissões de EFA no security group quando as transferências falham, mesmo que a conexão e o handshake RDMA tenham sucesso.
- Converta tempo de GPU liberado em ação operacional, usando menos servidores ou mais tráfego na mesma capacidade para obter a economia financeira.

Fonte: <https://aws.amazon.com/blogs/machine-learning/cut-self-hosted-llm-cost-and-latency-with-the-distributed-kv-caching-agent-skill/>

## Glossário

- Agent Skill: conjunto de orientações que um agente de código carrega para executar um fluxo específico.
- Cache local: memória de estados KV mantida no próprio servidor de GPU.
- Cache distribuído de KV: camada compartilhada que permite a diferentes GPUs reutilizarem estados de atenção.
- KV: sigla para chave e valor; neste contexto, são os estados de atenção calculados durante o processamento do contexto.
- Prefill: cálculo dos estados KV dos tokens do contexto antes de a geração da resposta começar.
- TTFT: tempo até o primeiro token, usado para medir a espera antes do início da resposta.
- LMCache: conector integrado pela skill ao vLLM ou ao SGLang para usar o cache compartilhado.
- L2: camada compartilhada de cache que guarda o estado KV fora do cache local.
- Taxa de acerto: parcela dos tokens recalculados que o cache passaria a atender.
- Ponto de virada: comprimento de prompt a partir do qual ler o KV se torna mais rápido do que recalculá-lo.
- TP: tensor paralelo, divisão do trabalho do modelo entre GPUs; seu tamanho entra no dimensionamento.
- Tipo de dados KV: formato dos valores de chave e valor, que precisa ser explícito e coincidir entre os servidores.
- Hash e seed: mecanismo de identificação usado para localizar entradas de KV de forma consistente na frota.
- EFA: Elastic Fabric Adapter, interface de rede usada nas instâncias compatíveis para comunicação por RDMA.
- RDMA: Remote Direct Memory Access, acesso direto à memória entre máquinas durante a transferência do KV.
- RAG: geração aumentada por recuperação, em que conteúdo recuperado entra no contexto antes da geração.
- Afinidade de sessão: roteamento que mantém uma conversa no mesmo servidor para aproveitar o cache local.
- Tenant: cliente ou grupo de usuários que utiliza um ambiente compartilhado.
- Availability Zone: zona de disponibilidade da AWS escolhida para os nós do cache.
- Security group: conjunto de regras de rede que controla o tráfego permitido, incluindo as permissões de EFA.
- Política de eviction: regra que define quais entradas em cache serão removidas.

## Para onde ir depois

O próximo passo é levar o diagnóstico da sua frota ao agente com a skill oficial e produzir um relatório KVTrace com uma janela representativa. Pratique a leitura da taxa de acerto, do ponto de virada e do cenário de capacidade antes de aprovar qualquer recurso.

O anúncio do cache distribuído de KV no Amazon ElastiCache detalha a arquitetura e os benchmarks. A documentação de primeiros passos reúne o fluxo de configuração, e o repositório do KVTrace concentra a ferramenta de medição. O Agent Toolkit for AWS também oferece o AWS MCP Server como caminho de integração com o agente.

Fonte: <https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/distributed-kv-caching-getting-started.html>
