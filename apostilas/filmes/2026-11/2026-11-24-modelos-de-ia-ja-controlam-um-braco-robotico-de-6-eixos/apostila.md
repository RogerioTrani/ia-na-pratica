# Modelos de IA já controlam um braço robótico de 6 eixos

_2026-11-24 · filme_

A Artificial Analysis lançou o AA-Robotics v0.1, uma prévia de pesquisa que mede quão bem modelos de linguagem operam um braço robótico de 6 eixos em oito tarefas de mesa. O GPT-6 Astra lidera com 69,4 pontos de 100, seguido por GPT-6.1 Sol, Gemini 4 Argon, Claude Opus 5.5 e Claude Fable 5.1. Os modelos já mexem no braço em tarefas simples, mas levam cerca de meia hora por tarefa contra 20 segundos de uma pessoa. Esta apostila reúne o método, o ranking, os números de tempo e custo e o achado sobre modelos que continuam mexendo depois de acertar.

## O que é o AA-Robotics v0.1

É a prévia de pesquisa da Artificial Analysis para medir o desempenho de modelos de linguagem de fronteira em entender, planejar e agir no mundo físico. Cada modelo recebe o controle de um braço robótico de 6 eixos (5 juntas e uma garra) e um objetivo simples.

A conclusão do artigo: modelos de linguagem em ambientes de agente de código já conseguem manipular um braço robótico em tarefas simples. Hoje são lentos e caros demais para uso em produção, quase duas ordens de grandeza piores que a referência humana. A Artificial Analysis espera que isso mude rápido.

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## Como o teste funciona

O modelo roda num contêiner isolado, com instruções curtas: como chegar ao braço (por uma API HTTP simples), qual é o braço (um Hiwonder NexArm, sem mais especificações) e como entregar a tentativa como concluída.

Ele enxerga a mesa por quatro câmeras, três ao redor da mesa e uma no pulso do braço, e escreve e executa código no contêiner para planejar e enviar os movimentos. Depois da entrega, o estado final é avaliado contra o critério de aprovação da tarefa. Toda tentativa é zero-shot.

- Aprovação vale 100 pontos; tarefa incompleta recebe pontos parciais pelo progresso.
- Os modelos GPT rodaram no Codex, os Claude no Claude Code e o Gemini 4 Argon no Antigravity, todos no esforço alto.

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## As oito tarefas

São tarefas de mesa inspiradas em atividades do dia a dia. Elas testam controle e destreza (agarrar com precisão, manusear objetos), raciocínio espacial (como os objetos interagem) e adaptação a imprevistos.

- Apertar o botão vermelho com a garra: passa se o botão piscar.
- Colocar o crocodilo de brinquedo no retângulo: passa se ele ficar inteiro dentro.
- Servir a bebida no copo: passa se a bebida estiver no copo, sem derramar e sem quebrar nada.
- Arrumar os quatro blocos na caixa e recolocar a tampa: passa com todos os blocos dentro e a tampa rente.
- Combinar as formas: colocar os blocos no tabuleiro até bater com a imagem.
- Escrever "hello world" no papel com o marcador, dentro da caixa preta: passa se estiver legível e dentro da caixa.
- Montar a torre mais alta com blocos de espuma: passa se a torre ficar em pé sozinha e na altura máxima possível.
- Medir comprimento, largura e altura da caixa: passa se cada medida tiver erro de até 2 mm.

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## Ranking

A nota é a média por tarefa, de 0 a 100. O GPT-6 Astra ficou em primeiro.

- GPT-6 Astra: 69,4
- GPT-6.1 Sol: 64,6
- Gemini 4 Argon: 55,3
- Claude Opus 5.5: 48,8
- Claude Fable 5.1: 46,3

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## Tempo: cem vezes mais lento que uma pessoa

Os modelos levam cerca de meia hora por tarefa. Um humano leva em média 20 segundos. Quatro dos cinco modelos ficam perto de 30 minutos por tarefa, e o Gemini 4 Argon é o mais lento, com 52 minutos.

As médias escondem diferenças grandes entre tarefas. O GPT-6 Astra apertou o botão vermelho em 2,2 minutos, enquanto o Claude Fable 5.1 gastou cerca de dez minutos entendendo e planejando antes da primeira ação. Na tarefa do crocodilo, o GPT-6.1 Sol se declarou pronto em cinco minutos e o Claude Opus 5.5 levou 45, uma diferença de nove vezes.

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## Custo: onde a diferença é menor

Em média, o GPT-6 Astra gastou 30 minutos e US$ 16,36 por tarefa. O GPT-6.1 Sol é o mais barato, com US$ 1,93 por tarefa, e ficou menos de cinco pontos abaixo na nota (69,4 contra 64,6). O Astra custa mais de oito vezes o que custa o Sol.

Na comparação com uma pessoa, o custo pesa menos que o tempo: o modelo mais econômico custa cerca de dez vezes o que se pagaria a uma pessoa pelo tempo da tarefa, ao salário médio por hora dos EUA (US$ 37,81, ganho médio por hora dos empregados da folha privada não agrícola, segundo o US Bureau of Labor Statistics, dado preliminar de setembro de 2026). No tempo, a distância é de quase cem vezes.

Como o braço e a cena são novos e há muita informação visual para processar, 70% do gasto vai para entrada de contexto.

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## O achado: continuar mexendo depois de acertar

Os modelos gastam boa parte do tempo inicial calibrando o braço e entendendo a cena, até a primeira ação. Depois, a maior parte vai para planejar movimentos, entremeados por movimentos curtos e precisos do braço.

Eles costumam continuar refinando a tentativa muito depois de chegar a um estado aprovado. O GPT-6.1 Sol montou uma torre válida em cerca de 17 minutos e, ao seguir mexendo, falhou na tarefa. Ainda não se sabe como os modelos vão melhorar o julgamento sobre quando uma tarefa física está terminada.

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## Além do vídeo

- Notas por tarefa: todos fizeram 100 em apertar o botão e em colocar o crocodilo. Em medir a caixa, nenhum passou de 17 pontos (GPT-6 Astra, Gemini 4 Argon e Claude Fable 5.1 tiraram zero).
- Taxa de agarres bem-sucedidos: GPT-6 Astra 45%, Claude Fable 5.1 44%, Claude Opus 5.5 40%, Gemini 4 Argon 36% e GPT-6.1 Sol 28%.
- O Gemini 4 Argon gastou em média 21 minutos observando e raciocinando antes da primeira ação, quase o dobro de qualquer outro modelo.
- Os tempos de atividade do Gemini 4 Argon são estimativas, porque o Antigravity não registra horário de cada passo.
- Na torre, o GPT-6.1 Sol, o Gemini 4 Argon e o Claude Fable 5.1 tiveram resultados bem diferentes: Sol e Fable tiraram 0, Argon fez 57 e o Astra fez 71.
