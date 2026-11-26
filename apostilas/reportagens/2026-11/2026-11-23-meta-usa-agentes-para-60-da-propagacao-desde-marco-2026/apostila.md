# Meta usa agentes para mais de 60% da propagação desde março de 2026

_2026-11-23 · reportagem_

Desde março de 2026, agentes de IA conduzem mais de 60% da propagação de técnicas entre os modelos de ranking de anúncios da Meta, segundo estimativa da empresa. A propagação adapta melhorias comprovadas a modelos com arquiteturas, dados e restrições diferentes. Esta apostila explica como Discovery, Generalization e Adoption transformam essa adaptação em um processo priorizado, testado e levado à produção. Você também vai entender os resultados iniciais, as metas, as métricas de validação e o papel dos engenheiros. Ao final, terá um roteiro para mapear técnicas, priorizar modelos e criar pontos de revisão humana no próprio trabalho.

## O contexto: uma técnica, muitos modelos

O sistema de recomendações de anúncios da Meta é sustentado por muitos modelos de ranking distintos. Cada um atende a uma superfície de produto ou a um objetivo de anunciante, com arquitetura, dados de treino e restrições de execução próprias. Uma melhoria que funciona bem em um desses modelos encontra condições diferentes no próximo.

A Meta chama de técnica qualquer mudança que melhore um modelo de ranking. Entre os avanços de arquitetura estão camadas de fatorização Wukong e redes de interação Interformer, além de representações de dados mais completas, otimizações de treino e melhorias de eficiência no treino e na inferência. A técnica resolve um problema identificado em um modelo específico.

Passar essa solução para o restante da frota exige propagação de técnicas. A adaptação quase nunca é uma cópia direta, porque o modelo de destino pode consumir outras features, operar com outro orçamento de inferência ou exigir uma configuração diferente de treino. O prazo também importa: uma técnica pode perder valor em poucos ciclos de desenvolvimento de modelos.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/>

## O fato: agentes conduzem mais de 60% da propagação

Desde março de 2026, os agentes passaram a conduzir a execução da propagação na Meta. A empresa estima que eles respondem por mais de 60% de todo esse trabalho. O restante fica abaixo de 40%, mas o anúncio não identifica essa parcela como trabalho exclusivo de engenheiros.

Propagação significa pegar uma técnica já comprovada e adaptá-la aos modelos em que ela pode gerar valor. O processo inclui escolher os destinos, modificar a implementação, treinar, avaliar e reunir propostas para produção. Os agentes atuam nessas decisões e também na operação dos experimentos.

Esse trabalho faz parte de uma sequência. O post anterior apresentou o Ranking Engineer Agent, ou REA, um sistema autônomo que gera hipóteses, desenha experimentos e comprova novas técnicas de machine learning em modelos de ranking de anúncios. O anúncio atual trata da etapa seguinte: espalhar essas descobertas pela frota.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/>

## Por que isso importa: velocidade com orçamento limitado

Cada combinação entre técnica e modelo exige esforço de engenharia e uma rodada de treino. O número de combinações cresce mais rápido do que a capacidade da equipe. Especialistas ainda produzem as adaptações mais fortes, sobretudo nos modelos de maior receita, mas esse método limita a quantidade de modelos que podem receber uma técnica.

O segundo limite é o compute disponível. Muitas tentativas geram ganhos pequenos ou insuficientes. Com orçamento finito, é preciso decidir quais experimentos começar, quanto procurar por hiperparâmetros e quando interromper uma rodada. A pergunta não é apenas testar tudo, mas navegar pelo espaço de possibilidades sem desperdiçar capacidade.

A padronização resolve os passos repetíveis. Os agentes entram nas decisões que dependem de contexto: escolher uma combinação promissora, diagnosticar uma falha, ajustar a busca e equilibrar a fila de treinos. Assim, a empresa busca aumentar a velocidade sem abandonar a avaliação e a aprovação humana.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/>

## A base anterior: Standard Model Templates

Antes dos agentes, a Meta organizou o desenho dos modelos em um conjunto pequeno de blocos reutilizáveis e combináveis. Essa abordagem ficou conhecida como Standard Model Templates, ou SMT. Quando uma técnica é validada no nível do template, ela pode chegar automaticamente a todos os modelos construídos com aquela estrutura.

Ao longo dos últimos dois anos, a padronização e a automação permitiram enviar mais de 5.000 combinações entre técnicas e modelos. A empresa também relata uma redução de 92% no tempo de engenharia por modelo. Esses resultados pertencem à etapa de templates, não aos agentes.

Os templates resolvem a parte determinística. Ainda faltavam decisões como quais técnicas mereciam atenção, qual modelo deveria receber cada uma, como ampliar a busca de hiperparâmetros e por que um treino não apresentava ganhos. Essa lacuna abriu espaço para agentes que combinam raciocínio com ferramentas especializadas de ML.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/>

## As três frentes dos agentes

O sistema de propagação se organiza em três capacidades. Discovery mantém uma visão atualizada das técnicas comprovadas e estima onde cada uma pode funcionar. Generalization adapta a técnica aos modelos de destino. Adoption transforma as adaptações validadas em modelos prontos para produção.

Os agentes combinam raciocínio baseado em LLM com ferramentas de machine learning. Eles usam esse conjunto para escolher adaptações, investigar falhas, aplicar correções e percorrer espaços de busca por hiperparâmetros. Também gerenciam a capacidade distribuída entre centenas de trabalhos simultâneos.

As três frentes compartilham uma base de conhecimento acumulada. Ela reúne treinos anteriores, arquiteturas de modelos e resultados de técnicas. Em vez de recomeçar do zero, cada agente parte do que já foi aprendido. O conhecimento comum liga a escolha inicial à execução e à avaliação final.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/>

## Discovery: escolher onde tentar

Discovery responde a duas perguntas: quais técnicas já foram comprovadas e em quais modelos elas têm chance de gerar ganhos. Antes, especialistas faziam essa avaliação modelo por modelo. Eles acompanhavam pesquisas e resultados e usavam seu conhecimento do domínio para julgar a aplicabilidade.

Os agentes consultam a base compartilhada e avaliam a frota inteira de uma vez. Eles identificam técnicas disponíveis, estimam a transferência entre modelos e produzem uma lista priorizada de combinações, ordenada pelo impacto esperado. O engenheiro passa a revisar essa avaliação e decidir a partir dela.

Priorizar evita espalhar compute por tentativas sem potencial. Ainda assim, a seleção precisa ser medida. Um modelo que poderia se beneficiar e ficou fora da lista não recebe outra oportunidade naquela etapa. Por isso, o acompanhamento da seleção importa tanto quanto o ganho obtido nas combinações escolhidas.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/>

## Generalization: adaptar a técnica ao modelo

A ideia central de uma técnica costuma ser transferível, mas sua implementação muda conforme o destino. O ajuste pode envolver hiperparâmetros, features já consumidas pelo modelo, tamanho da arquitetura e orçamento de inferência. Em alguns casos, a técnica precisa ser redesenhada para preservar o benefício dentro das restrições do modelo.

Para modelos construídos com templates padronizados, os agentes ajudam a construir, avaliar e melhorar os próprios templates. Eles propõem hipóteses de otimização a partir de técnicas comprovadas, executam experimentos em conjuntos representativos, avaliam resultados, diagnosticam falhas e repetem o ciclo. Validar uma vez no template custa uma fração do compute necessário para adaptar cada modelo separadamente.

Nos modelos de maior receita, a customização continua individual. O agente acompanha o engenheiro durante a aplicação inicial em um número pequeno de modelos. Registra mudanças de configuração, ajustes de hiperparâmetros e resolução de falhas, além de separar decisões gerais daquelas específicas de cada modelo. Com essa base, propõe e testa adaptações para os demais modelos, enquanto o engenheiro revisa e orienta.

O agente também usa milhões de treinos anteriores e as propriedades de cada modelo para começar com configurações mais promissoras. Os resultados de cada rodada reduzem o espaço de busca para a próxima. Ele decide quais experimentos continuam e quais podem parar cedo. Em combinações selecionadas, a Meta observou uma redução mediana de 4 vezes no compute de treino.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/>

## Adoption: levar a adaptação validada à produção

Adoption é a etapa que transforma técnicas generalizadas em modelos enviados. Os agentes iniciam experimentos, gerenciam treinos assíncronos de vários dias, fazem o ajuste fino de cada modelo, acompanham a convergência, recuperam falhas e montam propostas validadas. O trabalho ocorre modelo por modelo, mesmo quando vários fluxos avançam ao mesmo tempo.

O ajuste fino depende da origem da técnica. Quando ela chega individualmente, o agente ajuda a encontrar a melhor configuração de conjuntos de técnicas para aquele modelo. Em modelos baseados em template, um ciclo automático de pesquisa procura ajustes sobre a configuração compartilhada para capturar ganhos que ela sozinha não entregou.

Falhas podem vir de infraestrutura, divergência do treino ou erro no pipeline de dados. A depuração integrada identifica a causa e aplica correções específicas ou novas tentativas. A automação também precisa escolher quais trabalhos recebem prioridade quando centenas de fluxos disputam capacidade.

Essa escolha é um problema global de otimização. Os agentes ordenam trabalhos pela importância de receita, potencial da técnica e proximidade do prazo. Eles também recuperam capacidade de execuções paradas ou de baixo valor. O engenheiro mantém supervisão nos pontos de decisão, aprova planos e define prioridades. O resultado relatado é que cada engenheiro consegue cuidar de 3 vezes mais adaptações entre técnicas e modelos.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/>

## Como funciona na prática

Imagine que uma camada de fatorização Wukong foi comprovada em um modelo de ranking e a frota contém modelos de template e modelos customizados. O trabalho começa em Discovery: o agente consulta os resultados anteriores, verifica a compatibilidade e ordena as combinações pelo impacto esperado. O engenheiro revisa a lista antes de liberar a execução.

Na Generalization, o agente testa a técnica no template quando esse é o caminho disponível. Nos modelos customizados, acompanha as primeiras decisões do engenheiro e registra quais ajustes são gerais e quais pertencem apenas àquele modelo. A implementação pode mudar para respeitar features, arquitetura e orçamento de inferência, sem perder a ideia central da técnica.

Na Adoption, os experimentos entram na fila, os treinos de vários dias são monitorados e as falhas são diagnosticadas. A proposta segue para produção apenas depois de passar pelas métricas offline, pelos limites de proteção e pelo teste A/B online com ganho estatisticamente significativo. O exemplo termina na validação, sem presumir que toda tentativa terá sucesso.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/>

## Linha do tempo

- Ao longo dos últimos dois anos: a padronização e a automação enviaram mais de 5.000 combinações entre técnicas e modelos e reduziram em 92% o tempo de engenharia por modelo.
- Março de 2026: os agentes começaram a conduzir a execução da propagação. A estimativa atual é que respondam por mais de 60% do trabalho.
- Até o fim do ano: a Meta estima uma economia de compute de US$ 45 milhões ou mais.
- Momento do anúncio: ainda pode levar mais de um ano para cada técnica comprovada alcançar todos os modelos aplicáveis.
- Objetivo anunciado: reduzir esse prazo para três meses e buscar um aumento de 5 vezes no throughput de ponta a ponta.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/>

## Os números, com o recorte certo

- Mais de 60%: estimativa da parcela de toda propagação de técnicas conduzida por agentes desde março de 2026. A parcela restante fica abaixo de 40%.
- 3 vezes: produtividade inicial por engenheiro, comparada ao mesmo trabalho antes dos agentes. Cada engenheiro pode lidar com 3 vezes mais adaptações entre técnicas e modelos.
- 4 vezes: redução mediana no compute de treino medida em combinações selecionadas entre técnicas e modelos. O resultado não descreve toda a frota.
- Mais de 5.000: combinações entre técnicas e modelos enviadas ao longo dos últimos dois anos com padronização e automação.
- 92%: redução no tempo de engenharia por modelo atribuída à etapa de Standard Model Templates.
- US$ 45 milhões ou mais: estimativa de economia de compute até o fim do ano.
- Três meses: prazo pretendido para uma técnica comprovada alcançar todos os modelos aplicáveis, hoje capaz de levar mais de um ano.
- 5 vezes: aumento de throughput de ponta a ponta buscado para aproximar a propagação da velocidade das inovações.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/>

## Como a Meta avalia os agentes

Técnicas propagadas por agentes passam pela mesma avaliação das propagadas por engenheiros. Primeiro, precisam melhorar métricas offline de desempenho preditivo, como normalized entropy, sem piorar limites de proteção relacionados a custo de treino ou inferência. Depois, precisam mostrar ganho estatisticamente significativo em teste A/B online antes do envio.

Cada etapa produz um artefato diferente, então cada uma exige métricas próprias. Em Discovery, a empresa mede precisão e revocação das combinações selecionadas. Precisão é a parcela dos modelos escolhidos em que a técnica acaba sendo enviada. Revocação é a parcela de todos os modelos viáveis para aquela técnica que os agentes trouxeram à análise. A revocação recebe atenção especial porque um modelo omitido ali não recebe uma segunda chance.

Na Generalization, a avaliação começa em versões reduzidas dos modelos. Essa triagem ampla permite testar muitas adaptações com menos compute. As técnicas que passam seguem para um conjunto representativo de modelos em tamanho real, onde precisam melhorar a métrica NE e cumprir todos os limites de proteção antes da adoção.

Na Adoption, as métricas de desempenho continuam valendo, mas a operação também é medida. A empresa observa quantas intervenções humanas cada experimento exige e qual porcentagem dos problemas os agentes diagnosticam e mitigam sozinhos. Pessoas continuam presentes para revisar decisões importantes, confirmar julgamentos e aprovar o que será enviado.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/>

## Quem ganha e quem perde

Os engenheiros ganham capacidade de acompanhamento. Em vez de executar cada adaptação e observar cada treino manualmente, eles revisam avaliações, aprovam planos e definem prioridades. A Meta relata que cada engenheiro pode cobrir 3 vezes mais adaptações. Nos modelos de maior receita, o conhecimento especializado continua necessário na customização individual.

A frota ganha alcance. Técnicas comprovadas podem chegar a mais modelos aplicáveis, e a base de conhecimento acumulada evita que cada execução comece sem histórico. A padronização permite reutilizar validações, enquanto os agentes ajudam a decidir onde o trabalho vale o compute disponível.

O trabalho repetitivo de adaptação, monitoramento e triagem perde espaço. Ao mesmo tempo, a alocação de capacidade cria uma prioridade explícita: execuções paradas ou de baixo valor podem ser interrompidas para liberar recursos. O modelo operacional depende de prioridades claras e de revisão humana nos pontos de decisão.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/>

## O que ainda não se sabe

O anúncio combina resultados iniciais, estimativas e objetivos. O recorte de cada número muda o que se pode concluir sobre o sistema.

- Mais de 60% é uma estimativa do volume de propagação conduzido por agentes, não uma medida de qualidade ou de sucesso de cada técnica.
- A produtividade 3 vezes maior é um resultado inicial comparado ao mesmo trabalho antes dos agentes. A redução mediana de 4 vezes no compute foi observada em combinações selecionadas.
- A economia de US$ 45 milhões ou mais é uma projeção até o fim do ano. O prazo de três meses e o aumento de 5 vezes no throughput são metas declaradas.
- O aprendizado que aperfeiçoa as próprias estratégias a partir dos resultados acumulados é uma área de investimento da Meta. O texto não o apresenta como uma capacidade já concluída em toda a frota.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/>

## O que conferir antes de confiar

- Recorte da técnica e do modelo: confirme se o resultado vale para a combinação testada, para um template ou para toda a frota.
- Métricas de proteção: verifique se o ganho preditivo veio com aumento de custo de treino ou inferência.
- Validação online: um ganho offline não substitui o teste A/B com significância estatística.
- Caminho de generalização: modelos de template podem compartilhar uma validação; modelos customizados exigem adaptação individual.
- Capacidade e prioridade: observe quais experimentos recebem recursos, quais podem parar cedo e como a fila é ordenada.
- Revisão humana: identifique quem aprova planos, prioridades e propostas de produção.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/>

## O que você pode fazer

1. Liste as técnicas comprovadas e os modelos do seu sistema em um registro compartilhado. Para cada técnica, anote onde já funcionou e quais modelos são candidatos. O resultado esperado é um inventário que permita priorizar combinações.
2. Separe modelos construídos sobre templates dos modelos customizados. Marque quais compartilham blocos e quais têm arquitetura, dados e restrições próprios. O resultado esperado é saber onde uma validação pode servir a vários modelos e onde exige adaptação individual.
3. Defina as métricas offline, os limites de proteção e o teste online antes de iniciar as adaptações. Registre o que precisa melhorar e o que não pode piorar. O resultado esperado é um critério claro para continuar ou interromper cada tentativa.
4. Priorize as combinações entre técnicas e modelos pelo impacto esperado. Reserve compute para as candidatas mais promissoras e mantenha uma forma de perceber modelos viáveis deixados de fora. O resultado esperado é uma fila de trabalho com justificativa explícita.
5. Teste primeiro as adaptações em versões reduzidas dos modelos e depois em um conjunto representativo em tamanho real. O resultado esperado é uma triagem ampla com menor consumo antes da validação completa.
6. Registre decisões, mudanças de configuração e resultados de cada treino. Separe ajustes gerais dos específicos de cada modelo. O resultado esperado é uma base de conhecimento que pode orientar as próximas execuções.
7. Reserve pontos de revisão humana para aprovar planos, definir prioridades e decidir o que segue para produção. O resultado esperado é automação com supervisão nos momentos que mudam o rumo do trabalho.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/>

## Glossário

- Propagação de técnicas: processo de adaptar uma melhoria comprovada em um modelo para outros modelos da frota.
- Técnica: mudança que melhora um modelo, como uma arquitetura, uma representação de dados ou uma otimização de treino.
- Frota de modelos: conjunto de modelos diferentes que atendem a superfícies, objetivos e restrições distintas.
- Modelo de ranking: modelo usado para ordenar itens ou oportunidades dentro de um sistema de recomendação.
- Standard Model Templates: abordagem que organiza os modelos em blocos reutilizáveis e combináveis para padronizar seu desenho.
- Agente: sistema que combina raciocínio e ferramentas para executar decisões e fluxos de trabalho.
- LLM: modelo de linguagem grande, usado no sistema para apoiar o raciocínio sobre adaptações e falhas.
- Base de conhecimento: registro acumulado de treinos, arquiteturas e resultados usado para orientar as próximas decisões.
- Discovery: etapa que identifica técnicas comprovadas e prioriza os modelos em que elas podem gerar impacto.
- Generalization: reimplementação de uma técnica para funcionar em modelos com características diferentes.
- Adoption: etapa que transforma adaptações validadas em modelos enviados para produção.
- Hiperparâmetro: configuração escolhida para orientar o treino e avaliada durante a busca por uma boa adaptação.
- Compute: capacidade de processamento consumida por treinos e experimentos.
- Inferência: uso de um modelo já treinado para produzir resultados.
- Convergência: estabilidade do comportamento do modelo durante o treino, acompanhada para detectar problemas.
- Métricas de proteção: limites que precisam ser respeitados, como custo de treino e inferência, para que um ganho não cause regressão.
- Normalized entropy: métrica de desempenho preditivo usada no texto para avaliar os modelos.
- Precisão: em Discovery, parcela dos modelos selecionados em que a técnica acaba sendo enviada.
- Revocação: em Discovery, parcela de todos os modelos viáveis para uma técnica que os agentes selecionaram.
- Teste A/B: comparação online entre condições usada para confirmar um ganho estatisticamente significativo.
- Throughput: volume de trabalho concluído de ponta a ponta em um determinado intervalo.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/>

## Para onde ir depois

O próximo passo é aplicar o raciocínio do sistema a um conjunto pequeno de trabalho. Comece pelo inventário de técnicas e modelos, separe o que pode compartilhar templates e defina as métricas antes de executar. Depois, registre cada decisão para que a rodada seguinte use o que já foi aprendido.

A leitura seguinte é o post oficial da Meta sobre o uso de agentes na propagação de técnicas. Ele também remete ao post sobre Standard Model Templates, que explica a base de padronização usada antes dos agentes. A visão mais ampla da empresa é levar agentes a todo o ciclo de desenvolvimento de modelos, da exploração e geração de hipóteses até a experimentação e o lançamento em produção.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/>
