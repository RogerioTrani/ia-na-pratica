# Astra e Fable não divulgam o número de parâmetros

_2026-11-23 · reportagem_

A divulgação de Astra e Fable trouxe um sinal: o número de parâmetros deixou de ser o cartaz dos lançamentos. Esta apostila explica como a mistura de experts pode reduzir a parte acionada do modelo e por que modelos especializados em código estão no centro da aposta. Você vai entender a conta entre parâmetros, contexto, velocidade e hardware, incluindo as referências a 50 a 100 bilhões, 256 GB, Mac Studio e RTX 5090. Também vai aprender a separar projeções de fatos e a avaliar programação local, agentes remotos, caching e custo de tokens.

## O contexto: dois lançamentos sem o número de parâmetros

A divulgação de Astra e Fable trouxe uma ausência notável: nenhum dos dois anuncia quantos parâmetros tem. Modelos anteriores chegaram a ser vendidos com 1 trilhão de parâmetros no cartaz. O número funcionava como sinal de escala.

Essa mudança pode ser lida como sinal de que parâmetro a mais chama menos atenção. Essa é uma interpretação. O fato observável é a omissão do número; ela não permite concluir, sozinha, o tamanho ou a arquitetura de Astra e Fable.

## Por que o número de parâmetros perdeu o destaque

Parâmetros são valores ajustáveis que o modelo aprende durante o treinamento. A quantidade total ajuda a descrever a escala da rede, mas não mede sozinha a qualidade das respostas, a especialização em uma tarefa ou a memória necessária para executar uma passada.

Quando a arquitetura aciona somente parte do conjunto, o total perde força como previsão de custo. Um modelo pode ter muitos parâmetros e, ainda assim, utilizar uma fração deles em cada tarefa. A disputa passa a ser sobre entregar o modelo certo para cada trabalho.

Para quem vai escolher uma ferramenta, a consequência é direta. Comparar duas opções apenas pelo número de parâmetros pode esconder diferenças de velocidade, consumo de memória e desempenho em programação.

## O contexto: nuvem, execução local e custo

A discussão sobre programação local começa com uma possibilidade econômica: se o preço dos tokens subir muito, parte dos programadores pode procurar alternativas locais ou voltar a programar manualmente. O argumento é que os provedores dependem dos desenvolvedores e que a competição entre serviços pode limitar esse aumento.

Executar um modelo aberto na própria máquina reduz a dependência de uma chamada à nuvem, mas transfere para o usuário a responsabilidade pela memória, pela velocidade e pela compatibilidade do software. Ter o arquivo do modelo disponível não garante que ele funcione bem no hardware que você tem.

O custo também depende de como os tokens são processados. Em um uso relatado, o caching gera economia de 90%. Esse percentual pertence àquele uso e não serve como promessa para qualquer configuração. Um modelo pode produzir mais tokens mantendo o preço unitário e aumentar o gasto sem entregar uma resposta proporcionalmente melhor. Quantidade de tokens mede consumo, não qualidade.

## Modelos densos e mistura de experts

Em um modelo denso, o conjunto dos parâmetros precisa estar disponível na memória durante a execução. É por isso que o tamanho total pesa diretamente na conta de RAM ou de memória de vídeo.

Na mistura de experts, o modelo é dividido em blocos especializados. Um componente de seleção escolhe quais blocos participam de cada tarefa. O total pode continuar grande, mas a parte acionada em uma passada é menor. Isso permite trabalhar com uma fração do modelo carregada na RAM.

Imagine que uma equipe reúne especialistas em banco de dados, interface e servidor. Para resolver uma consulta, o coordenador chama o especialista em banco de dados. Ele não precisa colocar todos os especialistas para trabalhar ao mesmo tempo. A analogia mostra por que o número total de parâmetros diz menos sobre o custo de cada tarefa. O mecanismo ajuda a interpretar o debate, mas não identifica a arquitetura de Astra ou Fable.

## A aposta: modelos especializados em código

O cenário projetado troca o assistente genérico por um modelo focado em código. Ele mantém o vocabulário mínimo para conversar com o usuário e compreender o contexto da tarefa, mas dispensa a profundidade de especialistas em assuntos que não utiliza.

A faixa de 20 bilhões de parâmetros é descartada nesse cenário. As referências passam a ser 50, 70 ou talvez 100 bilhões. Em resumo, a aposta fica entre 50 e 100 bilhões de parâmetros. Esses valores são uma projeção, não uma configuração anunciada de Astra ou Fable.

Um trilhão corresponde a 1.000 bilhões. Portanto, 100 bilhões representam um décimo daquele total. A comparação mostra a mudança de escala, sem provar que um modelo menor produz respostas melhores ou piores. A vantagem procurada é combinar foco em programação com uma demanda de memória mais administrável.

## Programação local: desempenho e limites

O veredito sobre Qwen, Llama, Phi-4 e DeepSeek é direto: nenhum desses modelos abertos funciona para programação no nível dos serviços de nuvem, como Claude e Codex. A mesma avaliação reconhece utilidade em muitas outras tarefas, como classificar e-mails, e admite o Qwen para um script pequeno, de brincadeira. O recorte importa: o veredito trata desse tipo de programação.

A velocidade entra como critério separado. No padrão adotado, menos de 100 tokens por segundo torna a programação local inviável. Qwen é descrito abaixo de 20 tokens por segundo, chegando a cerca de 10. Tokens por segundo medem o ritmo de geração; não medem a qualidade do código. Os valores citados vêm dessa avaliação e não devem virar uma regra para todos os modelos e hardwares.

32 GB de memória são muito pouco: segundo a avaliação, não existe modelo de 32 GB capaz de programar no nível que se pretende comparar. Um modelo pode servir para uma tarefa simples e não sustentar um fluxo intenso de programação, mesmo que o nome da família apareça em uma lista de modelos abertos.

## Memória: o modelo e o contexto disputam espaço

Os pesos do modelo ocupam memória, mas o contexto também precisa de espaço. O contexto reúne as informações disponíveis naquela execução, como instruções, histórico da conversa e material da tarefa. Quanto mais informação o modelo precisa considerar, maior tende a ser essa demanda.

No exemplo, 100 bilhões de parâmetros seriam tratados como cabendo em 128 GB quando se olha apenas para o modelo. Ao incluir o contexto, a referência passa a 256 GB. Essa é a conta usada para o cenário, não uma conversão universal entre parâmetros e gigabytes. O espaço necessário depende também da implementação e do formato dos pesos.

Planejar somente a memória do modelo deixa uma armadilha: o arquivo pode caber, mas a tarefa real pode ficar sem folga para o contexto. Por isso a decisão de compra ou de teste precisa considerar modelo e contexto juntos.

## Hardware: a folga de memória do Mac Studio

A linha do Mac Studio inclui configurações com 256 GB ou 512 GB de memória unificada. Destaca-se a possibilidade de alocar até 400 GB para a GPU. A memória unificada permite que CPU e GPU trabalhem com o mesmo espaço de memória, o que interessa para carregar modelos grandes e seus contextos.

Nessa conta, uma configuração de 256 GB aparece como candidata para o cenário de 100 bilhões de parâmetros mais contexto. O limite de até 400 GB alocados para a GPU não significa que toda essa capacidade esteja livre para o modelo. O restante do sistema e as outras necessidades da execução continuam ocupando memória.

Ter capacidade de sobra resolve apenas uma parte do problema. O desempenho depende também de o software reconhecer a plataforma e usar bem essa memória.

Fonte: <https://www.apple.com/mac-studio/specs/>

## CUDA, RTX 5090, AMD e Mac

A RTX 5090 tem 32 GB de memória. Esse valor fica muito abaixo da referência de 256 GB usada para o modelo de 100 bilhões com contexto. A diferença ilustra a vantagem de memória do cenário do Mac Studio diante da placa citada.

CUDA é a plataforma de computação da NVIDIA. A crítica é que as melhores ferramentas ficam sob esse ecossistema e que boa parte do software roda mal em AMD ou Mac. A alegação de patrocínio e monopólio é uma interpretação. O cuidado prático é verificar o suporte real da ferramenta e do modelo à sua plataforma antes de assumir que a memória disponível garantirá um bom resultado.

Uma GPU com memória generosa não elimina limites de software. Da mesma forma, um modelo aberto não se torna adequado à programação apenas por rodar localmente.

Fonte: <https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/>

## Como funciona na prática

Imagine que um desenvolvedor quer substituir parte do uso de um serviço em nuvem por um assistente de código local. A decisão começa pela tarefa: ele precisa de um modelo capaz de programar de verdade, e não apenas classificar mensagens ou responder perguntas simples.

Em seguida, ele verifica a memória disponível para o modelo e para o contexto. Uma máquina com 32 GB esbarra no limite já citado: não há modelo desse porte que programe nesse nível. Um Mac Studio com 256 GB ou 512 GB oferece a folga discutida, mas ainda exige conferência da compatibilidade do software.

Depois, ele testa a mesma tarefa de programação e observa qualidade, tokens por segundo e consumo de memória. Se o ritmo ficar abaixo do critério de 100 tokens por segundo, o uso pode ser inviável mesmo com o modelo carregado. O exemplo mostra a ordem da decisão: tarefa, modelo, memória, software e velocidade.

## Agentes remotos e segurança

Um agente remoto executa seu trabalho na infraestrutura do provedor e entra em contato com a máquina do usuário quando precisa de algo local. Isso muda a rotina de hardware, mas aproxima a segurança das permissões concedidas ao agente.

Agentes que verificam e-mails periodicamente e podem executar ações com a conta autenticada merecem atenção. Deixar contas conectadas em vários lugares aumenta o alcance de um erro ou de uma ação indesejada. A prática recomendada é evitar entregar credenciais pelo chat e não autenticar o agente em tudo.

Uma forma de pensar o acesso é separar a tarefa da conta inteira. Se o agente precisa processar mensagens, o ideal é conceder apenas o acesso necessário para essa atividade. O resultado esperado é um agente capaz de trabalhar com um limite claro de permissões.

## AGI e a discussão sobre inteligência

A pergunta sobre reunir vários modelos especializados para formar uma AGI recebe uma resposta negativa. O argumento começa pela definição: não há um significado único de inteligência artificial geral. Sem estabelecer o que conta como AGI, vários modelos trabalhando juntos não resolvem a questão.

Também se critica a redução da inteligência à repetição de padrões. Se esse fosse o único critério, um termostato ou uma calculadora poderiam ser classificados como inteligentes. Essa posição distingue aprender padrões de refletir sobre as próprias ações, criar e compreender a própria identidade.

Na prática, o rótulo AGI não funciona como uma especificação técnica. Para avaliar um sistema, é mais útil observar quais tarefas ele executa, em quais condições e com quais limites.

## Modelos abertos e a hipótese da versão reduzida

A expressão open source aparece associada a modelos liberados com seus arquivos e pesos abertos. A distinção útil é que pesos abertos permitem examinar e executar o modelo, enquanto os direitos de uso vêm da licença. A disponibilidade do arquivo não significa que todos os detalhes do treinamento ou do serviço comercial tenham sido publicados.

A hipótese levantada é que um laboratório poderia liberar uma versão menor ou menos ajustada que a executada em seus servidores. A metáfora da Ferrari no servidor e do fusca entregue ao usuário comunica essa diferença. O argumento liga a escolha à proteção de parâmetros e ajustes que poderiam ser estudados por engenharia reversa.

Essa é uma interpretação, não uma comprovação sobre todos os modelos abertos. O outro lado do argumento é a evolução do ecossistema: com o tempo, outros laboratórios podem alcançar ajustes parecidos e testar caminhos diferentes. Para o usuário, a atitude prática é medir a versão liberada na tarefa desejada, sem presumir que ela reproduz o modelo interno de uma empresa.

## Quem ganha e quem perde

Se a aposta em modelos especializados se confirmar, quem trabalha com código pode ganhar uma ferramenta mais focada e com demanda de memória menor. Hardware com bastante memória unificada também ganha relevância nesse cenário. Quem depende de uma máquina com memória limitada encontra mais restrições para acompanhar essa mudança.

Os modelos genéricos perdem espaço como argumento de venda baseado no tamanho. Os provedores de nuvem não necessariamente perdem todo o mercado: agentes remotos e serviços de programação continuam fazendo parte da discussão. A execução local aparece mais como alternativa para tarefas específicas do que como substituto automático de toda a nuvem.

O resultado depende da tarefa. Um modelo especializado pode ser suficiente para programar e inadequado para outra função. A comparação justa usa o mesmo trabalho, o mesmo critério de qualidade e as condições reais de memória e velocidade.

## O que ainda não se sabe

O debate reúne fatos de anúncio, medidas de teste e projeções. Separar essas categorias evita transformar uma interpretação em especificação técnica.

- Parâmetros de Astra e Fable: a não divulgação não confirma que os modelos sejam menores.
- Arquitetura: a mistura de experts explica o mecanismo de memória, mas não comprova que Astra ou Fable use essa organização.
- Tamanho projetado: 50 a 100 bilhões de parâmetros descreve uma aposta, não uma configuração confirmada dos dois lançamentos.
- Velocidade: o limite de 100 tokens por segundo e os valores atribuídos a Qwen pertencem a essa avaliação; a medição precisa considerar a tarefa e o hardware.
- Memória: 256 GB é a referência do cenário de 100 bilhões com contexto, não uma garantia de que qualquer modelo dessa escala funcionará bem.
- Modelos abertos: a suspeita de versões comerciais superiores é uma hipótese; a versão liberada precisa ser julgada pelo próprio desempenho.
- Hardware: alegações de patrocínio, monopólio e escassez artificial de componentes são interpretações. Rumores de retirada da RTX 5090 do mercado também não servem como confirmação.

## O que você pode fazer

1. Escolha uma tarefa real de programação e defina o que seria uma resposta correta; você terá um critério para comparar modelos sem depender apenas do número de parâmetros.
2. Teste um modelo especializado em código na mesma tarefa e observe a qualidade do resultado; isso mostra se o foco do modelo corresponde ao trabalho que você precisa fazer.
3. Meça os tokens por segundo durante a tarefa e compare com o critério de 100 tokens por segundo; o resultado ajuda a perceber se o ritmo permite trabalhar ou se a espera atrapalha.
4. Verifique a memória disponível para o modelo e para o contexto; você terá uma estimativa de folga antes de iniciar uma execução longa.
5. Confirme se o software e o modelo oferecem suporte à sua plataforma, incluindo o ecossistema CUDA quando relevante; você saberá se o hardware escolhido tem compatibilidade para o fluxo pretendido.
6. Compare o custo local com o da nuvem considerando tokens, caching e preço unitário; a conta ficará mais próxima do gasto real do que a multiplicação simples por tokens produzidos.
7. Revise as permissões concedidas a agentes remotos; o resultado será um acesso limitado às contas e ações necessárias para a tarefa.

## Glossário

- Parâmetro: valor ajustável aprendido pelo modelo e usado para processar informações.
- Pesos: valores armazenados no modelo depois do treinamento e aplicados durante a execução.
- Modelo denso: arquitetura em que o conjunto dos parâmetros participa do processamento.
- Mistura de experts: arquitetura que divide o modelo em blocos especializados e aciona uma parte deles por tarefa.
- Modelo especializado: modelo ajustado ou planejado para um conjunto específico de tarefas, como programação.
- LLM: sigla para modelo de linguagem de grande escala.
- Contexto: informações disponíveis para o modelo durante uma execução, incluindo instruções, histórico e material da tarefa.
- Token: unidade em que o texto é dividido para processamento e contabilização pelo modelo.
- Tokens por segundo: ritmo de geração de tokens; mede velocidade, não qualidade.
- RAM: memória de acesso aleatório usada para manter dados disponíveis durante a execução.
- GPU: unidade de processamento gráfico usada também para acelerar o trabalho de modelos de IA.
- Memória unificada: espaço de memória compartilhado entre componentes como CPU e GPU.
- GB: gigabyte, unidade de capacidade de memória ou armazenamento.
- CUDA: plataforma de computação da NVIDIA usada por ferramentas e modelos para executar trabalho na GPU.
- Caching: reuso de parte do processamento já realizado para reduzir trabalho repetido em chamadas seguintes.
- Modelo aberto: modelo cujos pesos são disponibilizados para execução e análise.
- Open source: termo usado para modelos liberados; o uso e a distribuição dependem da licença aplicada.
- AGI: sigla para inteligência artificial geral, conceito sem definição única.

## Para onde ir depois

- Pratique com uma tarefa de código que você já saiba verificar e repita a comparação entre um modelo local e um serviço de nuvem.
- Anote qualidade, tokens por segundo, memória usada e custo para transformar a escolha em uma decisão baseada no seu trabalho.
- Repita o exercício com um agente remoto usando apenas as permissões necessárias e observe se ele consegue concluir a tarefa dentro desse limite.
- Acompanhe os próximos anúncios de Astra e Fable e compare arquitetura, memória e desempenho quando forem divulgados, separando dados confirmados de projeções.
