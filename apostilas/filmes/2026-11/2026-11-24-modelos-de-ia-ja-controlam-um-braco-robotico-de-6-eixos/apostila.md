# Modelos de IA já controlam um braço robótico de 6 eixos

_2026-11-24 · filme_

A Artificial Analysis lançou em 14 de outubro de 2026 o AA-Robotics v0.1, um teste que mede como modelos de linguagem entendem, planejam e agem por meio de um braço robótico de verdade. O GPT-6 Astra lidera a média das oito tarefas de mesa com 69,4 pontos, mas leva cerca de 30 minutos e custa US$ 16,36 por tarefa em média. Ao ler esta apostila, você vai entender o aparato do teste, os critérios de cada tarefa e as diferenças entre pontuação, tempo, custo e precisão. Também vai reconhecer os erros físicos e de julgamento que separam um resultado promissor em pesquisa de um sistema pronto para produção.

## O contexto

Em 14 de outubro de 2026, a Artificial Analysis apresentou o AA-Robotics v0.1. O projeto é uma versão de pesquisa que mede o desempenho de modelos de linguagem de fronteira na compreensão, no planejamento e na atuação no mundo físico. A primeira leva reúne oito tarefas realizadas com um braço robótico em uma mesa.

Desde o começo de 2026, os modelos de fronteira avançaram no controle de braços robóticos. A Artificial Analysis avalia que o futuro da robótica tende a envolver agentes generalistas fortes. Por isso, a empresa criou um experimento para acompanhar esse progresso e testar modelos dentro de ferramentas de código que controlam o braço diretamente.

IA incorporada é a aplicação de IA que percebe um ambiente, planeja uma ação e interfere nele. No AA-Robotics, essa cadeia aparece de forma concreta: o modelo recebe imagens das câmeras, interpreta a cena, escreve código e envia movimentos ao braço. O teste observa o resultado físico de todo esse processo.

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## Por que isso importa

Um modelo pode produzir uma resposta escrita correta e ainda assim falhar ao mover um objeto. No mundo físico, uma posição mal estimada, uma garra fechada cedo demais ou uma força mal calculada pode mudar o resultado da tarefa. O braço torna esses erros observáveis.

O AA-Robotics reúne três capacidades. O controle e a destreza aparecem nas agarras e no manuseio de objetos. O raciocínio espacial aparece na relação entre peças, caixas e superfícies. A adaptabilidade aparece quando o modelo precisa reagir a um imprevisto durante a execução.

Os resultados confirmam que modelos de linguagem em ferramentas de código já conseguem manipular um braço em tarefas simples. Eles também expõem a distância para a produção: o tempo e o custo continuam muito acima da referência humana. O valor do teste está em mostrar onde essa distância vem.

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## Como o teste funciona

Cada modelo recebe o controle de um braço robótico de 6 eixos, com 5 juntas e uma garra. Os modelos GPT rodam no Codex, os modelos Claude no Claude Code e o Gemini 4 Argon no Antigravity. Todas as ferramentas usam a configuração high effort.

O modelo roda dentro de um contêiner isolado. Ele recebe instruções breves sobre como alcançar o braço por uma API HTTP simples, qual braço está usando e como encerrar uma tentativa. O equipamento é identificado como Hiwonder NexArm. A cena pode ser vista por quatro câmeras: três ao redor da mesa e uma no pulso do braço.

Dentro do contêiner, o modelo escreve e executa código para planejar e enviar movimentos. Quando envia a tentativa para revisão, o estado final da mesa é comparado com os critérios da tarefa. A conclusão completa vale 100 pontos; um resultado incompleto pode receber pontos pelo progresso. Todas as tentativas são zero-shot.

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## As oito tarefas de mesa

As tarefas usam atividades cotidianas para testar partes diferentes do controle robótico. O botão e o crocodilo exigem contato e posicionamento. Servir a bebida envolve força, inclinação e estabilidade. A torre e a combinação de formas exigem relações espaciais mais complexas.

Cada tarefa tem um objetivo e um critério de aprovação observável. Ler os dois é essencial: aproximar-se do resultado não basta quando a condição final exige precisão, estabilidade ou ausência de derramamento.

- Apertar o botão vermelho: pressionar o botão com a garra; a tarefa passa quando o botão pisca.
- Colocar o crocodilo de brinquedo no retângulo: posicionar o brinquedo dentro da área; ele precisa ficar inteiramente dentro do retângulo.
- Despejar a bebida no copo: transferir a bebida da garrafa para o copo; o líquido precisa estar no copo, sem derramamento e sem quebrar nada.
- Guardar os blocos na caixa: colocar os quatro blocos dentro da caixa e recolocar a tampa; todos precisam estar dentro, com a tampa nivelada e encaixada.
- Completar o desafio de combinar formas: colocar os blocos no tabuleiro para reproduzir a figura; as peças precisam corresponder à imagem.
- Escrever "hello world": escrever a frase com a canetinha no papel, dentro da caixa preta; o texto precisa ser legível e permanecer dentro da área.
- Construir a torre mais alta: empilhar os blocos de espuma; a torre precisa ficar de pé, sem apoio externo, e alcançar a maior altura possível no teste.
- Medir a caixa: medir comprimento, largura e altura; cada dimensão precisa ficar a até 2 mm do tamanho correto.

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## Como a pontuação é calculada

Cada tentativa recebe uma nota de 0 a 100 pontos. A conclusão da tarefa vale 100. Um resultado parcial recebe de 1 a 99 pontos pelo progresso alcançado. O zero representa a ausência de resultado pontuável na avaliação final.

A nota geral do modelo é a média das oito tarefas. Por isso, um número como 69,4 resume resultados diferentes e não indica que o modelo executou uma parcela fixa dos movimentos de todas as tarefas. A tabela por tarefa é necessária para entender a composição dessa média.

A avaliação considera o estado final enviado para revisão. Uma execução pode passar por um estado adequado durante o processo e terminar em outra condição. Os pontos parciais reconhecem progresso, mas o critério de aprovação continua sendo a referência para a conclusão.

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## Os números do ranking

O GPT-6 Astra ficou em primeiro lugar no AA-Robotics v0.1. A ordem geral foi GPT-6 Astra, GPT-6.1 Sol, Gemini 4 Argon, Claude Opus 5.5 e Claude Fable 5.1.

As médias medem o conjunto das oito tarefas. A liderança do GPT-6 Astra não significa notas máximas em todas elas, e a posição de cada modelo precisa ser lida junto com tempo, custo e resultados individuais.

- GPT-6 Astra: 69,4 pontos, a maior média entre as oito tarefas.
- GPT-6.1 Sol: 64,6 pontos, menos de cinco pontos abaixo do líder.
- Gemini 4 Argon: 55,3 pontos, em terceiro lugar.
- Claude Opus 5.5: 48,8 pontos, em quarto lugar.
- Claude Fable 5.1: 46,3 pontos, em quinto lugar.

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## O que os resultados por tarefa mostram

A tabela detalhada revela capacidades que a média esconde. Os cinco modelos concluíram as duas tarefas iniciais, mas divergiram bastante nas seguintes. Servir a bebida, combinar formas e construir a torre separaram especialmente os participantes.

Os resultados parciais indicam progresso sem atingir o critério completo. Os zeros precisam ser lidos com a regra da avaliação final: o estado enviado ao término da tentativa é que recebe a nota.

- Apertar o botão vermelho e colocar o crocodilo no retângulo: os cinco modelos receberam 100 pontos em cada tarefa.
- Despejar a bebida no copo: GPT-6 Astra e Gemini 4 Argon receberam 100 pontos; GPT-6.1 Sol recebeu 0; Claude Opus 5.5 recebeu 25; Claude Fable 5.1 recebeu 30.
- Guardar os blocos na caixa: GPT-6.1 Sol recebeu 100 pontos; GPT-6 Astra, Gemini 4 Argon, Claude Opus 5.5 e Claude Fable 5.1 receberam 40 pontos cada.
- Combinar as formas: GPT-6.1 Sol e Claude Fable 5.1 receberam 100 pontos; GPT-6 Astra recebeu 44; Claude Opus 5.5 recebeu 38; Gemini 4 Argon recebeu 0.
- Escrever "hello world": GPT-6 Astra e GPT-6.1 Sol receberam 100 pontos; Gemini 4 Argon e Claude Opus 5.5 receberam 45; Claude Fable 5.1 recebeu 0.
- Construir a torre: GPT-6 Astra recebeu 71 pontos; Gemini 4 Argon recebeu 57; Claude Opus 5.5 recebeu 25; GPT-6.1 Sol e Claude Fable 5.1 receberam 0.
- Medir a caixa: GPT-6.1 Sol e Claude Opus 5.5 receberam 17 pontos; GPT-6 Astra, Gemini 4 Argon e Claude Fable 5.1 receberam 0.

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## Tempo e custo: a distância para produção

Os modelos levam cerca de meia hora por tarefa, contra uma média humana de 20 segundos. Isso corresponde a aproximadamente 100 vezes mais tempo. Quatro dos cinco modelos ficaram perto de 30 minutos por tarefa; o Gemini 4 Argon foi o mais lento, com 52 minutos.

As médias escondem diferenças grandes entre tarefas. O GPT-6 Astra apertou o botão vermelho em 2,2 minutos. O Claude Fable 5.1 gastou cerca de dez minutos entendendo e planejando antes da primeira ação. Na colocação do crocodilo, o GPT-6.1 Sol se declarou concluído após cinco minutos, enquanto o Claude Opus 5.5 levou 45 minutos, uma diferença de nove vezes.

No custo, o GPT-6.1 Sol foi o mais barato, com US$ 1,93 por tarefa em média. O GPT-6 Astra custou US$ 16,36, mais de oito vezes o valor de Sol, por uma vantagem inferior a cinco pontos. Boa parte da despesa vem das imagens e das informações de entrada: 70% do gasto foi com contexto.

A referência humana usa o tempo da tarefa feita à mão, precificado a US$ 37,81 por hora. Esse valor é a média dos ganhos por hora de todos os empregados da folha privada não agrícola dos EUA, em dados preliminares de setembro de 2026 do US Bureau of Labor Statistics. Nessa comparação, o modelo mais econômico custou cerca de dez vezes o trabalho humano pelo tempo da tarefa.

- Cerca de 30 minutos por tarefa: tempo médio dos modelos, aproximadamente 100 vezes a referência humana.
- 52 minutos: média do Gemini 4 Argon, a mais lenta entre os cinco modelos.
- 21 minutos: tempo médio do Gemini 4 Argon até a primeira ação, quase o dobro do observado nos outros modelos.
- US$ 1,93: custo médio por tarefa do GPT-6.1 Sol, o menor do grupo.
- US$ 16,36: custo médio por tarefa do GPT-6 Astra, o maior do grupo.
- 70%: parcela do gasto destinada ao contexto de entrada.
- US$ 37,81 por hora: valor usado para calcular o custo da referência humana.

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## Onde o tempo é gasto

No início da tentativa, os modelos dedicam bastante tempo a calibrar o braço e entender a cena. Depois da primeira ação, a maior parte do tempo passa a ser usada no planejamento dos movimentos. O braço executa trajetos relativamente curtos e precisos entre etapas mais longas de planejamento.

A análise separa compreensão da cena e do braço, planejamento de movimentos, revisão das câmeras, movimento físico e outras atividades. A categoria outras inclui espera pela execução de código, escrita de notas e relatório final. Cada etapa é classificada a partir do código, das imagens e das mensagens.

Os tempos do Gemini 4 Argon são estimativas. O Antigravity não registra o horário de cada etapa individualmente; o teste distribui essas etapas entre os comandos do braço, que têm marcação exata, proporcionalmente à quantidade de tokens.

- GPT-6 Astra: 20% de compreensão da cena, do braço e dos movimentos; 59% de planejamento; 6% de revisão das câmeras; 13% de movimento do braço; 242 minutos de tentativa no conjunto das tarefas.
- GPT-6.1 Sol: 17% de compreensão; 61% de planejamento; 6% de revisão das câmeras; 13% de movimento do braço; 224 minutos no conjunto.
- Claude Fable 5.1: 33% de compreensão; 37% de planejamento; 9% de revisão das câmeras; 18% de movimento do braço; 249 minutos no conjunto.
- Claude Opus 5.5: 21% de compreensão; 45% de planejamento; 9% de revisão das câmeras; 23% de movimento do braço; 253 minutos no conjunto.
- Gemini 4 Argon: 42% de compreensão; 45% de planejamento; 6% de revisão das câmeras; 6% de movimento do braço; 419 minutos no conjunto, com tempos estimados.

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## Precisão física e agarras

Agarrar e manipular objetos com precisão são habilidades centrais no AA-Robotics. Elas servem tanto para tarefas de posicionamento quanto para o uso de ferramentas, que abre um leque maior de ações físicas.

O teste analisou as agarras em seis tarefas: colocar o crocodilo, despejar a bebida, guardar os blocos, combinar formas, construir a torre e medir a caixa. Uma agarra é considerada bem-sucedida quando o modelo mantém o objeto pretendido durante a elevação ou o transporte.

Falhas incluem fechar a garra no vazio, fechar sobre o objeto e deixá-lo escorregar, derrubá-lo, não conseguir levantá-lo ou pegar outro objeto. As porcentagens abaixo são sobre tentativas de agarrar, e o número de tentativas está indicado em cada linha. O GPT-6.1 Sol, segundo colocado no ranking geral, teve a menor taxa de agarras bem-sucedidas.

- GPT-6 Astra: 45% de agarras bem-sucedidas em 95 tentativas.
- Claude Fable 5.1: 44% em 89 tentativas.
- Claude Opus 5.5: 40% em 100 tentativas.
- Gemini 4 Argon: 36% em 75 tentativas.
- GPT-6.1 Sol: 28% em 111 tentativas.

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## O julgamento sobre terminar

Muitas vezes, os modelos continuam refinando a execução depois de alcançar um estado que atende aos critérios. Isso transforma uma possível conclusão em novas oportunidades de erro. O teste registrou casos em que o objeto estava posicionado corretamente e foi empurrado para fora durante ajustes posteriores.

Em uma execução, o crocodilo já estava dentro do retângulo aos 23:22. O modelo continuou ajustando por mais 22 minutos e empurrou o brinquedo para fora da borda três vezes. Em outro caso, o crocodilo estava dentro do retângulo aos 24:34, e o modelo gastou mais sete minutos reposicionando o brinquedo para ganhar margem.

O julgamento também falhou sem alterar a cena. Um modelo relatou que o tabuleiro correspondia à figura enquanto o hexágono vermelho não estava encaixado. Outro disse que a tampa estava nivelada e alinhada quando ela repousava sobre uma cunha apoiada em um cubo. Depois de escrever "hello world" de forma ilegível, um modelo reescreveu a frase na mesma região do papel pelo menos seis vezes.

Os erros físicos têm outra origem. Sondagens de contato empurraram blocos soltos para um aglomerado. Uma aproximação pelo ângulo errado impediu que a garra retirasse o triângulo verde da abertura quadrada. Um erro irreversível é aquele que impede o modelo de alcançar a nota máxima a partir dali.

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## Como funciona na prática

O caso do GPT-6.1 Sol na tarefa da torre mostra a diferença entre alcançar um objetivo durante a execução e terminar com um resultado válido. O modelo construiu uma torre que atendia ao critério em cerca de 17 minutos. Depois, continuou trabalhando e terminou a tarefa em estado de falha.

Na tabela final, o GPT-6.1 Sol recebeu 0 pontos nessa tarefa. O motivo é a regra de avaliação: o estado final enviado para revisão determina a nota. O momento em que a torre passou não preservou a pontuação depois que o resultado foi alterado.

Para acompanhar uma execução, observe três marcos: a primeira ação, o primeiro estado aprovado e o erro irreversível. Eles ajudam a separar o tempo de preparação, o momento de conclusão e a alteração que inviabilizou a nota máxima.

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## Linha do tempo

- Desde o começo de 2026: a Artificial Analysis registra um grande avanço dos modelos de linguagem de fronteira no controle de braços robóticos.
- Setembro de 2026: mês de referência dos dados preliminares do US Bureau of Labor Statistics usados para calcular o custo humano por hora.
- 14 de outubro de 2026: lançamento do AA-Robotics v0.1 com os resultados das oito primeiras tarefas.

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## Quem ganha e quem perde

Em pontuação geral, o GPT-6 Astra ganha. Em custo médio, o GPT-6.1 Sol ganha. Em tarefas específicas, o destaque muda: o Gemini 4 Argon, assim como o GPT-6 Astra, concluiu o despejo da bebida, e o Claude Fable 5.1, assim como o GPT-6.1 Sol, concluiu o desafio de combinar formas. Cada modelo tem um perfil diferente de acertos e falhas.

Na referência de tempo e custo usada pelo teste, a execução humana leva vantagem sobre todos os modelos. O modelo mais barato custa cerca de dez vezes o valor do trabalho humano pelo tempo da tarefa, e os modelos levam aproximadamente 100 vezes mais tempo.

A medição da caixa expõe outro limite coletivo. Nenhum dos cinco modelos atingiu 100 pontos; os melhores resultados foram 17 pontos. Para quem precisa de precisão física ou de uma rotina de produção, os dados atuais sustentam uma conclusão direta: os modelos ainda não substituem a operação humana nesse recorte.

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## O que ainda não se sabe

O AA-Robotics v0.1 é uma versão de pesquisa com oito tarefas de mesa. Os resultados descrevem esse conjunto, com esse braço, essas câmeras e essas ferramentas. Eles não estabelecem o desempenho dos mesmos modelos em outros ambientes ou na operação de uma instalação inteira.

A leitura também precisa preservar as condições do experimento. Modelo, ferramenta, esforço de execução, tempo, custo e critério de aprovação fazem parte do resultado.

- Julgamento de conclusão: ainda não se sabe como os modelos vão melhorar a capacidade de reconhecer quando uma tarefa física terminou.
- Escopo das tarefas: oito atividades de mesa testam controle, raciocínio espacial e adaptabilidade; a média não deve ser transferida automaticamente para outros cenários.
- Custo do contexto: 70% do gasto foi com entrada de informações, diante da novidade do braço e da cena e do volume de imagens processadas.
- Tempo do Gemini 4 Argon: os tempos por atividade são estimativas porque o Antigravity não registra cada etapa individualmente.
- Modelo e ferramenta: os GPTs rodam no Codex, os Claudes no Claude Code e o Gemini 4 Argon no Antigravity, todos em high effort; o resultado pertence a essa combinação.
- Referência humana: o custo usa o tempo da tarefa manual e a média salarial por hora indicada no teste; ele não é um orçamento completo de implantação robótica.
- Expectativa da empresa: a Artificial Analysis espera uma mudança rápida no cenário atual; essa é uma previsão da responsável pelo teste, não um resultado já observado na v0.1.

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## O que você pode fazer

1. Abra o artigo oficial do AA-Robotics v0.1 e localize a tabela Results per Task; o resultado é enxergar as notas individuais por trás da média de cada modelo.
2. Escolha uma das oito tarefas e leia o objetivo junto do critério de aprovação; o resultado é saber exatamente qual condição física conta como sucesso.
3. Compare a mesma tarefa na linha dos cinco modelos, incluindo notas parciais e zeros; o resultado é identificar uma força específica sem tratar o ranking geral como desempenho uniforme.
4. Cruze a pontuação com os gráficos de tempo e custo; o resultado é verificar se uma vantagem de nota compensa o gasto adicional para o objetivo que você está avaliando.
5. Confira as condições do experimento: zero-shot, ferramenta usada, high effort, quatro câmeras e braço Hiwonder NexArm; o resultado é manter a comparação dentro do recorte em que ela foi feita.
6. Acompanhe uma execução no artigo e marque a primeira ação, o primeiro estado aprovado e o erro irreversível; o resultado é aprender a distinguir progresso, conclusão e perda da chance de nota máxima.

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## Glossário

- IA incorporada: IA que percebe um ambiente, planeja uma ação e atua fisicamente nele.
- Modelo de linguagem de fronteira: modelo de ponta usado no teste para compreender instruções, planejar e controlar ações.
- Agente generalista: agente capaz de atuar em diferentes tipos de tarefa, em vez de executar apenas uma função estreita.
- Braço robótico de 6 eixos: braço com seis eixos de movimento; no teste, ele tem 5 juntas e uma garra.
- Junta: articulação do braço que permite mudar sua posição ou orientação.
- Garra: componente que abre e fecha para segurar objetos.
- Zero-shot: tentativa realizada sem exemplos anteriores específicos da tarefa.
- Contêiner isolado: ambiente separado em que o modelo escreve e executa o código de controle.
- API HTTP: interface usada para enviar comandos e controlar o braço robótico.
- Harness de agente de código: ferramenta que organiza as instruções, as imagens, a execução de código e o envio de ações do modelo.
- Critério de aprovação: condição observável que o estado final precisa atender para concluir a tarefa.
- Pontuação parcial: nota de 1 a 99 pontos concedida pelo progresso em uma tarefa incompleta.
- Tempo até a primeira ação: intervalo até o primeiro pressionar, agarrar, empurrar, despejar ou traço de caneta.
- Erro irreversível: situação em que o modelo já não pode alcançar a nota máxima.
- Contexto: informações de entrada processadas pelo modelo, incluindo imagens; no teste, essa categoria respondeu por 70% do custo.
- High effort: configuração de esforço usada nas três ferramentas que executaram os modelos.
- Baseline humano: referência de tempo e custo humano usada para comparar os modelos.
- Fronteira de Pareto: conjunto de opções em que melhorar uma medida exige abrir mão de outra; aparece nos gráficos que relacionam pontuação, tempo e custo.

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## Para onde ir depois

Pratique a leitura das execuções pelo estado final e pelos marcos da tentativa. O caso da torre do GPT-6.1 Sol é um bom exercício para entender por que um objetivo alcançado no meio do processo pode não virar uma nota máxima.

Ao comparar modelos, mantenha juntas as três medidas: pontuação, tempo e custo. Depois, verifique o critério da tarefa e as condições do teste antes de levar uma conclusão para outro cenário.

- Explique o caso da torre do GPT-6.1 Sol usando três conceitos: primeiro estado aprovado, erro posterior e avaliação do estado final.
- Refaça a comparação entre GPT-6 Astra e GPT-6.1 Sol, separando a vantagem de pontuação da diferença de custo e dos resultados por tarefa.
- Escolha uma tarefa no artigo oficial e transforme seu critério de aprovação em uma lista de observação para praticar a avaliação do resultado físico.

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## Além do vídeo

- Um modelo fechou a garra três vezes no gancho da fita e, na terceira soltura, a fita retraiu para dentro do estojo.
- Uma oscilação de deslocamento varreu o hexágono amarelo ainda não colocado até a base do braço.
- O círculo azul escapou durante dois transportes e caiu no recorte do hexágono.
- O modelo fechou a garra quatro vezes em 80 segundos, sempre no vazio, com o cubo ao lado dos dedos.
- Uma descida com a garra vazia arrastou o círculo azul até a borda do tabuleiro, de onde ele caiu.
- O bloco comprido foi segurado por um canto e deslizou do cubo antes de a garra abrir.
- O pulso do braço pressionou a bandeja e a empurrou para frente, tornando cada tentativa de agarrar a garrafa mais difícil.
