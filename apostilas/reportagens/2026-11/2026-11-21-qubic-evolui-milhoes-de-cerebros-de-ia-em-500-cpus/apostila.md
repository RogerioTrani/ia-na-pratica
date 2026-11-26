# Qubic evolui milhões de cérebros de IA em 500 CPUs

_2026-11-21 · reportagem_

Esta apostila explica como a Qubic usou a evolução para projetar cérebros Neuraxon e testá-los no ARC-AGI-3 com cerca de 500 núcleos de CPU, sem GPU e sem modelo pré-treinado. Você vai entender a diferença entre treinar uma rede e buscar sua arquitetura, como os cérebros jogam e por que o 0,41 precisa de contexto. Também verá os limites dos experimentos, o desenho do Neuraxon 3.0 e como examinar o código e os dados públicos.

## O contexto

Em 4 de novembro de 2026, a equipe científica da Qubic registrou no Neuraxon Intelligence Academy Vol. 14 mais de 110 configurações de busca e milhões de cérebros evoluídos. O trabalho usou cerca de 500 núcleos de CPU, sem GPU e sem modelo pré-treinado, para testar os cérebros no ARC-AGI-3. A melhor pontuação offline foi 0,38; a última submissão no Kaggle chegou a 0,41, novo recorde pessoal da equipe.

Os dois números pertencem à Qubic. A avaliação privada do Kaggle terá seu resultado oficial divulgado pela ARC Prize Foundation em 4 de dezembro de 2026. O interesse do trabalho está na pergunta que ele testa: até onde uma estrutura de IA pequena, escolhida por evolução e obrigada a descobrir cada jogo, avança quando começa sem conhecimento prévio.

## Busca por arquitetura neural e a aposta na evolução

A busca por arquitetura neural, ou NAS, automatiza o desenho de uma rede: quantas unidades existem, como se conectam e quais regras as atualizam. O treinamento ajusta a força das conexões dentro de uma estrutura definida; a NAS escolhe a estrutura. Mudar a taxa de aprendizado ou o tamanho de lote é ajuste de hiperparâmetro, porque altera como uma rede dada aprende.

Elsken, Metzen e Hutter, na revisão da JMLR de 2019, dividem a NAS em três partes: o espaço de busca reúne as arquiteturas possíveis; a estratégia define como explorá-las; a estimativa de desempenho decide qual candidato é melhor, sem treinar completamente cada um. A analogia da cozinha ajuda: treinar ensina a receita, enquanto projetar a arquitetura decide onde ficam o forno, a pia e a bancada.

A evolução tem uma justificativa biológica. Nos animais, o aprendizado ajusta sinapses durante a vida, e a evolução molda a estrutura do cérebro ao longo das gerações. Anthony Zador descreveu em 2019 o gargalo genômico: o genoma é pequeno demais para especificar cada conexão, então codifica uma receita compacta de conexão e aprendizado. Hinton e Nowlan já haviam mostrado em 1987, em simulação, que a capacidade de aprender pode guiar a evolução, fenômeno chamado efeito Baldwin.

O NEAT, de Stanley e Miikkulainen, em 2002, cresce topologias de simples a complexas. O Transformer segue outro caminho: sua arquitetura foi projetada manualmente e permanece fixa durante o uso. O Neuraxon aposta nos dois níveis, evolução para escolher a estrutura e aprendizado dentro de cada vida. Uma busca só justifica seu custo quando supera a busca aleatória com o mesmo orçamento.

- Busca aleatória: amostra arquiteturas ao acaso e funciona como linha de base. Li e Talwalkar, em 2020, compararam os métodos usando o mesmo orçamento.
- Aprendizado por reforço: uma rede controladora propõe arquiteturas e recebe recompensa pela precisão. O experimento de Zoph e Le, em 2017, usou 800 GPUs em paralelo.
- Busca evolutiva: uma população muta, e os melhores indivíduos sobrevivem e se reproduzem. Real et al., em 2019, reportaram 450 GPUs por cerca de 7 dias.
- Busca diferenciável: relaxa a escolha da arquitetura para que um gradiente possa otimizá-la. O DARTS, de Liu, Simonyan e Yang, em 2019, reportou de 1,5 a 4 dias-GPU.
- Como ler os custos: as cifras pertencem aos principais experimentos de cada artigo e não representam um preço universal para usar a estratégia.

## O Neuraxon por dentro

Neuraxon é uma unidade computacional inspirada no cérebro, desenvolvida por conselheiros científicos da Qubic. Um neurônio artificial clássico produz um número a cada passo; o Neuraxon funciona em tempo contínuo e assume três estados: excitatório (+1), neutro (0) ou inibitório (-1).

Cada sinapse carrega três pesos, com mudanças em escalas rápida, lenta e meta. As conexões também podem se formar, colapsar ou se reconectar. Por isso, a estrutura do cérebro permanece dinâmica, em vez de depender apenas de números fixos.

Quatro neuromoduladores simulados, dopamina, serotonina, acetilcolina e noradrenalina, atuam por nove subtipos de receptores. Células semelhantes a astrócitos regulam a plasticidade, e quatro loops homeostáticos mantêm a atividade em um intervalo saudável. O framework Aigarth, da Qubic, usa a evolução para explorar as dezenas de escolhas estruturais que esse conjunto cria.

Fonte: <https://github.com/DavidVivancos/Neuraxon>

## ARC-AGI-3: jogos sem manual

O ARC-AGI-3 é o primeiro benchmark interativo da série ARC, lançado em 25 de março de 2026 pela ARC Prize Foundation. O jogador vê uma grade de cores, age por turnos e precisa descobrir o que significa vencer. O conjunto público tem 25 jogos de desenvolvimento. A dificuldade vem de não receber instruções sobre as regras.

No lançamento, humanos pontuaram 100%, e a IA de ponta, 0,51%. Esses percentuais descrevem aquele momento do benchmark. Eles mostram o desafio de resolver situações novas por interação, em vez de responder a uma pergunta com regras conhecidas.

A pontuação premia eficiência. Para cada nível, a metodologia divide o número de ações usado por um humano pelo número usado pela IA e eleva o resultado ao quadrado. Um agente que faz dez vezes mais ações que uma pessoa marca 1% naquele nível. Níveis posteriores pesam mais, e a pontuação final é a média de todos os jogos.

O Prêmio ARC 2026 oferece US$ 2 milhões em três categorias. A avaliação no Kaggle acontece sem acesso à internet, sistemas baseados em API são barrados, e os participantes principais precisam liberar código aberto de suas soluções para concorrer aos prêmios.

Fonte: <https://arcprize.org/competitions/2026>

## Como um cérebro Neuraxon é criado e joga

Durante o jogo, um cérebro Neuraxon recebe a grade como números, seleciona ações e continua aprendendo por meio da plasticidade. A busca por arquitetura acontece antes: define quais regiões da tela ele observa, como as cores viram entradas, como equilibra explorar o ambiente com aproveitar o que aprendeu e até onde seus cliques podem alcançar.

A equipe adotou uma fronteira de informação. Estudar jogos públicos, jogadas humanas e análises para escolher o espaço de busca é legítimo; entregar essas informações ao agente durante a partida não é. O protocolo evolutivo usa três fases para testar se a solução resiste a condições novas.

1. Fase 1, evolução: crie cérebros para um jogo específico. O resultado esperado é identificar candidatos capazes de resolver alguma parte daquele jogo.
2. Fase 2, exame curto: faça milhares de cérebros jogarem alguns jogos em algumas sementes, variações com layouts iniciais diferentes. O resultado esperado é verificar se a solução resiste a mudanças de layout.
3. Fase 3, exame longo: leve os melhores cérebros aos 25 jogos públicos, usando sementes nunca empregadas na seleção. O resultado esperado é medir se o desempenho se mantém fora dos dados usados para escolher os candidatos.

## A escala em CPUs e a rede Qubic

A busca evolutiva é paralela por natureza: cada cérebro de uma população pode ser avaliado de forma independente. A equipe testou mais de 110 configurações e milhões de cérebros em cerca de 500 núcleos de CPU. Os processadores eram comuns, e os experimentos do ARC-AGI-3 não usaram GPU.

O arquivo principal do Neuraxon é Python puro. O repositório também tem kernels CUDA opcionais para redes Multi Neuraxon maiores, o que é diferente do hardware usado nesses experimentos.

A proposta da Qubic combina paralelismo com verificação. Pelo Useful Proof of Work, a capacidade computacional que protege a rede também pode ser direcionada a tarefas de IA. A rede é operada por 676 Computors, que chegam a acordo por um quórum tolerante a falhas bizantinas. Assim, um resultado distribuído pode ser conferido por muitas partes independentes, em vez de depender da confiança em uma única máquina.

## Os números: 0,38, 0,41 e o contexto

A melhor nota offline atingiu 0,38, e a última submissão da equipe no Kaggle marcou 0,41. Os valores são da própria Qubic, e o resultado oficial da avaliação privada será anunciado em 4 de dezembro de 2026. Até lá, o 0,41 é um recorde pessoal informado pela equipe.

As melhores entradas da competição usam modelos de linguagem open-weight de 27 a 31 bilhões de parâmetros dentro de envoltórios de agente, segundo análise de outubro de 2026 da Metir AI, e pontuam muito mais alto. Os cérebros Neuraxon começam sem conhecimento pré-treinado de linguagens ou imagens. Nesse recorte, o 0,41 mede o alcance da evolução em um cérebro pequeno que descobre cada jogo; não serve como comparação direta com sistemas que já trazem bilhões de parâmetros de conhecimento.

A equipe reconhece duas capacidades das entradas líderes: prever o que mudará na tela antes de agir e aprender com os erros. O Neuraxon 3.0 mira essa direção.

- 0,38: melhor pontuação na versão offline do Kaggle, atribuída à equipe da Qubic.
- 0,41: última submissão no Kaggle e novo recorde pessoal da equipe, ainda sujeito à avaliação privada oficial.
- Mais de 110 configurações: volume de configurações de busca testadas, e não a quantidade de neurônios de um cérebro.
- Milhões de cérebros: escala da população avaliada ao longo das buscas, e não o tamanho de uma única rede.
- Cerca de 500 núcleos de CPU: hardware usado nos experimentos, e não a quantidade de cérebros.
- 27 a 31 bilhões de parâmetros: faixa de tamanho das melhores entradas citadas, e não o tamanho do Neuraxon.

## O que deu errado nos experimentos

Um grupo de cérebros venceu um jogo em todas as sementes usadas para selecioná-los e não venceu em nenhuma semente nova. É a maldição do vencedor: ao escolher o melhor entre muitos candidatos nos mesmos dados, a busca pode premiar uma combinação favorecida pela sorte. Cawley e Talbot já haviam descrito esse problema em 2010. A imagem do aluno que decorou a prova do ano passado mostra o que aconteceu.

Em jogos simples, uma política fixa com alguma exploração pode passar um nível sem entender as regras. Os sucessos também se concentraram em poucos jogos, quase sempre no primeiro nível. Uma pontuação alta, por si só, não demonstra aprendizado durante a partida. A equipe resume a limitação: selecionar o resultado final não revela se houve aprendizado interno.

Os fracassos viraram três regras para as próximas buscas.

- Separe as sementes: selecione em algumas e relate o resultado em outras, para medir resistência a layouts novos.
- Reserve jogos públicos: mantenha alguns jogos inteiramente fora da busca, para evitar que a seleção os conheça de antemão.
- Subtraia uma linha de base: compare sempre com ações aleatórias executadas no mesmo orçamento, pois a busca aleatória pode ser uma competidora forte.

## Neuraxon 3.0: cinco mecanismos para aprender

O Neuraxon 3.0 está em design, com testes preliminares. Em 6 de novembro de 2026, o repositório público chegava ao Neuraxon 2.0. A versão seguinte busca fechar uma lacuna observada no ARC-AGI-3: os cérebros atuais exploram e se adaptam durante o jogo, mas ainda não definem metas nem encadeiam ações para alcançá-las.

O novo desenho acrescenta cinco mecanismos, cada um em uma escala de tempo diferente. A busca cobre esses mecanismos e seus intervalos, limitados pela fisiologia. Cada um pode ser desligado para medir sua contribuição individual.

- Plasticidade dependente da ordem do pico: fortalece ou enfraquece uma conexão conforme qual neurônio dispara primeiro.
- Marcas sinápticas: marca uma sinapse e espera segundos por um sinal neuromodulatório antes de consolidar a mudança.
- Plasticidade em escala de tempo comportamental: inspirada no hipocampo, conecta eventos que acontecem segundos apartados.
- Domínios astrocíticos: limita quanto um grupo de sinapses pode mudar ao mesmo tempo.
- Homeostase multi-escala: mantém a rede estável sem congelar sua capacidade de mudança.

## Velocidade de aprendizado e salvaguardas

O Neuraxon 3.0 troca a pergunta de qual rede vence pela pergunta sobre quais mecanismos e constantes de tempo ajudam um cérebro a aprender em um ambiente novo. O critério anunciado recompensa a rapidez com que o cérebro reduz seu erro de previsão por ação em jogos que nunca viu. O erro de previsão é a diferença entre a mudança esperada e a observada na tela. Nesse critério, vencer por sorte não rende recompensa.

O protocolo é fixado antes de qualquer dado ser visto. A seleção da arquitetura é selada por uma impressão digital, ou hash, antes de o conjunto de testes ser gerado. Esse registro permite verificar depois se a seleção da arquitetura foi alterada.

Cada busca será comparada com uma busca aleatória de mesmo orçamento. As sementes serão pareadas, os resultados passarão por correção para comparações múltiplas, e um tamanho mínimo de efeito será declarado antes do experimento. Nenhum experimento será interrompido antecipadamente porque os resultados pareçam favoráveis. Os resultados completos serão publicados quando os experimentos terminarem, qualquer que seja a conclusão.

## Código aberto e dados abertos

O repositório oficial é https://github.com/DavidVivancos/Neuraxon. Ele reúne o Neuraxon 1.0 e 2.0, o Multi Neuraxon 2.0, kernels CUDA opcionais, uma configuração de conectoma de mosca-da-fruta, exemplos e testes. O início rápido mostra como construir uma rede, alimentar entradas, aplicar neuromodulação e rodar uma evolução Aigarth em poucas linhas de Python. O arquivo principal não exige dependências externas.

As licenças variam por recurso. O núcleo usa MIT; os recursos híbridos do Aigarth usam a licença Aigarth, que proíbe uso militar. Essa distinção precisa ser lida antes de reutilizar qualquer parte do projeto.

Os cérebros evoluídos estão no conjunto oficial Nxon2ArcAGI3Brains, em https://huggingface.co/datasets/DavidVivancos/Nxon2ArcAGI3Brains. São 603.054 linhas sob licença CC BY-SA 4.0. A página registra 82,7 GB em Parquet e 100,3 GB para o conteúdo bruto. Parquet é um formato de armazenamento colunar, adequado a conjuntos grandes. O Construtor de rede Neuraxon também permite montar e visualizar uma rede no navegador.

Fonte: <https://huggingface.co/datasets/DavidVivancos/Nxon2ArcAGI3Brains>

## Como funciona na prática

Imagine que uma população de cérebros seja criada para um jogo público. Um candidato vence nas sementes usadas na seleção e passa para o exame longo. Se ele falhar nas sementes novas, a vitória inicial não resistiu à mudança de layout. Esse é o padrão observado no trabalho da Qubic.

Uma política fixa também pode atravessar um nível simples apenas por explorar o ambiente. Para separar sorte de aprendizado, a equipe mantém jogos fora da busca, usa sementes distintas para seleção e relato, e desconta uma linha de base aleatória no mesmo orçamento.

No desenho do Neuraxon 3.0, a avaliação deve observar a rapidez da redução do erro de previsão em jogos inéditos. Um cérebro que apenas repete uma sequência vencedora fica em desvantagem diante de outro que aprende a prever as mudanças da tela.

## Linha do tempo

- 1987: Hinton e Nowlan mostram, em simulação, que o aprendizado pode guiar a evolução, fenômeno conhecido como efeito Baldwin.
- 2002: Stanley e Miikkulainen apresentam o NEAT, que cresce topologias neurais de simples a complexas.
- 2019: Elsken, Metzen e Hutter organizam os métodos de NAS em espaço de busca, estratégia e estimativa de desempenho; Anthony Zador descreve o gargalo genômico.
- 25 de março de 2026: a ARC Prize Foundation lança o ARC-AGI-3, primeiro benchmark interativo da série ARC.
- 2 de novembro de 2026: encerram-se as submissões do Prêmio ARC 2026.
- 4 de novembro de 2026: a equipe científica da Qubic publica o Neuraxon Intelligence Academy Vol. 14.
- 6 de novembro de 2026: o repositório público do Neuraxon ia até a versão 2.0; as páginas do GitHub e do Hugging Face são consultadas nessa data.
- 8 de novembro de 2026: vence o prazo dos artigos para a trilha de artigos do Prêmio ARC 2026.
- 4 de dezembro de 2026: a ARC Prize Foundation divulgará os resultados oficiais da competição.

Fonte: <https://arcprize.org/competitions/2026>

## Quem ganha e quem perde

O avanço favorece pesquisadores e desenvolvedores que querem estudar inteligência emergente em sistemas pequenos. O código e os dados abertos permitem inspecionar cérebros evoluídos, repetir comparações e testar novos critérios. Para a Qubic, o trabalho oferece uma aplicação concreta de computação paralela e verificação distribuída.

Fica em desvantagem quem escolhe um candidato apenas pela vitória nas sementes de seleção. Projetos que precisam de metas e ações encadeadas também encontram um limite nos cérebros atuais. Os modelos de linguagem de 27 a 31 bilhões de parâmetros continuam nas melhores posições citadas; o resultado do Neuraxon amplia a investigação sobre evolução, sem substituir essa comparação.

## O que ainda não se sabe

O 0,41 ainda não é um resultado oficial da avaliação privada. A classificação será conhecida em 4 de dezembro de 2026. Os experimentos também deixaram aberta a questão central: um cérebro pode marcar pontos sem aprender durante o jogo, e os sucessos se concentraram no primeiro nível.

O Neuraxon 3.0 está em design com testes preliminares. Seus mecanismos precisam mostrar contribuição própria, e sua seleção por velocidade de aprendizado precisa ser testada em jogos inéditos. O protocolo anunciado foi criado para tornar essas respostas verificáveis.

- Resultado da competição: acompanhe a nota oficial antes de tratar o 0,41 como posição no ranking.
- Aprendizado interno: observe se o cérebro reduz seu erro de previsão e melhora em sementes novas, além de vencer.
- Generalização: examine o desempenho por jogo e por nível, porque a média pode esconder concentração no primeiro nível.
- Contribuição dos mecanismos: compare cada mecanismo do Neuraxon 3.0 ligado e desligado antes de atribuir a ele uma melhoria.
- Revisão humana: confira sementes, jogos reservados e linha de base aleatória antes de aceitar uma comparação evolutiva.

## O que você pode fazer

Os arquivos públicos permitem examinar o trabalho e montar uma comparação própria. O caminho começa pelo código, pelas licenças e pelo conjunto de cérebros. Depois, vale aplicar as separações de sementes e jogos que os próprios experimentos mostraram como necessárias.

1. Abra https://github.com/DavidVivancos/Neuraxon e localize o Neuraxon 1.0 e 2.0, o Multi Neuraxon 2.0, os exemplos e os testes. O resultado esperado é identificar as peças disponíveis antes de reproduzir o trabalho.
2. Leia a licença de cada recurso: MIT para o núcleo e licença Aigarth para os recursos híbridos, com proibição de uso militar. O resultado esperado é saber quais condições se aplicam ao seu uso.
3. Acesse https://huggingface.co/datasets/DavidVivancos/Nxon2ArcAGI3Brains e confira as 603.054 linhas, os 82,7 GB em Parquet e a licença CC BY-SA 4.0. O resultado esperado é planejar o armazenamento e respeitar as condições do conjunto.
4. Use o Construtor de rede Neuraxon no navegador para montar e visualizar uma rede. O resultado esperado é relacionar as unidades e conexões antes de executar uma evolução.
5. Ao montar um teste, separe sementes de seleção e relato, reserve jogos fora da busca e inclua uma busca aleatória no mesmo orçamento. O resultado esperado é uma comparação menos vulnerável à sorte.
6. Acompanhe https://arcprize.org/competitions/2026 em 4 de dezembro de 2026. O resultado esperado é localizar a avaliação privada oficial e situar o 0,41 na competição.

Fonte: <https://github.com/DavidVivancos/Neuraxon>

## Glossário

- Arquitetura neural: organização das unidades, conexões e regras de atualização de uma rede.
- Busca por arquitetura neural (NAS): processo automatizado que escolhe a estrutura de uma rede.
- Treinamento: ajuste dos parâmetros de uma rede para melhorar seu desempenho em uma tarefa.
- Hiperparâmetro: configuração que controla como o treinamento acontece, como a taxa de aprendizado.
- Pré-treinamento: etapa anterior em que um modelo aprende padrões usando dados antes da tarefa avaliada.
- Peso sináptico: valor que influencia a força de uma conexão entre neurônios.
- Plasticidade: capacidade de uma conexão ou rede mudar com a experiência.
- Semente: variação usada para gerar condições iniciais diferentes em um experimento.
- Neuromodulador: sinal que altera a atividade e a plasticidade de uma rede biológica ou simulada.
- Homeostase: mecanismo que mantém a atividade dentro de um intervalo saudável.
- Efeito Baldwin: contribuição da capacidade de aprendizado individual para a seleção evolutiva.
- Maldição do vencedor: inflação do resultado quando muitos candidatos são escolhidos pelos mesmos dados de seleção.
- Modelo open-weight: modelo cujos pesos treinados estão disponíveis para uso e adaptação.
- Envoltório de agente: camada que organiza entradas, ações e decisões de um modelo em uma tarefa interativa.
- Gradiente: informação sobre como mudar parâmetros para reduzir um erro.
- Parquet: formato colunar usado para armazenar grandes conjuntos de dados.
- Conectoma: mapa das conexões de um sistema nervoso ou de uma rede que o representa.
- Hash: impressão digital calculada a partir de conteúdo, usada para verificar se ele mudou.
- Quórum tolerante a falhas bizantinas: acordo que continua verificável mesmo com participantes defeituosos ou maliciosos.
- Dias-GPU: medida que multiplica o tempo de execução pela quantidade de GPUs usadas.
- Useful Proof of Work: proposta da Qubic de direcionar capacidade computacional de segurança para tarefas de IA.

## Para onde ir depois

A próxima data concreta é 4 de dezembro de 2026, quando a ARC Prize Foundation divulgará os resultados oficiais. Depois disso, o ponto a observar será a posição da submissão da Qubic e a distância para as entradas que usam modelos pré-treinados.

Os experimentos completos do Neuraxon 3.0 serão publicados quando terminarem, qualquer que seja o resultado. Para estudar a série desde o início, comece pelo NIA Vol. 1: Neuraxon Time. Na prática, escolha um jogo público e compare uma busca evolutiva com uma busca aleatória no mesmo orçamento, separando as sementes usadas para escolher e relatar.

- 4 de dezembro de 2026: acompanhar a avaliação privada oficial do Prêmio ARC 2026.
- Experimentos concluídos: ler os resultados completos do Neuraxon 3.0 e verificar o efeito de cada mecanismo.
- Prática: construir uma rede no navegador e testar uma população com sementes de seleção separadas das sementes de relato.

Fonte: <https://arcprize.org/competitions/2026>

## Além do vídeo

- O NAS foi usado para projetar o MobileNetV3, rede de imagens presente em recursos de câmeras de celulares.
- A evolução também encontrou melhorias para o Transformer em The Evolved Transformer, de So, Liang e Le, em 2019.
- O repositório do Neuraxon registrava 533 estrelas em 6 de novembro de 2026.
