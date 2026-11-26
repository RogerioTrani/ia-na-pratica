# Novo modelo de raciocínio gasta 345x menos na inferência

_2026-11-23 · noticia_

Um novo modelo de raciocínio chamado Energy-Based Reasoner (EBR) propõe substituir o raciocínio em loop por uma função de energia que guia o refinamento e diz quando parar. No teste Sudoku-Extreme, ele usa 345 vezes menos computação na inferência que o EqR e chega a 99,9% de acurácia com 1,8 milhão de parâmetros. Depois de ler, você entenderá como a energia guia o raciocínio, o que os números significam e como baixar o código e rodar os experimentos.

## O fato

Em 6 de novembro de 2026, William Xingxu Chen, Alexi Gladstone, Zeyu Michael Li, Heng Ji e Yilun Du submeteram ao arXiv o artigo "Energy-Based Reasoners: Your Recurrent Reasoner Should Be an Energy-Based Model" (arxiv.org/abs/2611.08977).

O artigo propõe o Energy-Based Reasoner (EBR) como alternativa ao raciocínio em loop, também chamado de raciocínio recorrente. O código do projeto está aberto no GitHub, em github.com/wwillchen/ebr, e a página do projeto está em energy-based-reasoners.github.io.

O anúncio central: no teste Sudoku-Extreme, o EBR usa 345 vezes menos computação na inferência que o EqR, o segundo melhor modelo da comparação, e chega a 99,9% de acurácia com 1,8 milhão de parâmetros, com custo de treino comparável.

Fonte: <https://arxiv.org/abs/2611.08977>

## Por que isso importa

Modelos que raciocinam em loop repetem um bloco recorrente várias vezes para aprofundar a resposta em espaço latente. Esse looping é um viés indutivo forte, porque permite escalar a profundidade efetiva e fazer raciocínio em várias etapas.

O problema é que os modelos em loop não têm uma medida explícita de progresso. É difícil saber quando parar de iterar e como melhorar o estado atual. O EBR ataca esse ponto: em vez de iterar às cegas, ele aprende uma função de energia que pontua cada estado de raciocínio, e o gradiente dessa energia indica como refinar a resposta e quando parar.

Se o ganho se confirmar fora do estudo original, raciocinar com muito menos computação pode baratear rodar esses modelos.

Fonte: <https://arxiv.org/abs/2611.08977>

## O que é o Energy-Based Reasoner

O EBR é um modelo que aprende uma função de energia escalar E(z; x) sobre um estado latente z, dado o problema x. Raciocinar vira descida de gradiente nessa energia: a cada passo, o estado se move na direção que diminui a energia.

Essa única função unifica três papéis: avaliar um estado (quão boa é a resposta atual), refinar (como melhorá-la) e verificar (quando parar). O artigo defende que um raciocinador recorrente deve ser, na verdade, um modelo baseado em energia.

Fonte: <https://github.com/wwillchen/ebr>

## Como o raciocínio funciona por energia

Na prática, o loop de raciocínio deixa de ser uma repetição fixa e passa a ser um processo guiado. A energia atribui uma pontuação a cada estado latente; estados melhores têm energia mais baixa. O gradiente da energia diz em que direção mudar o estado para melhorar a resposta, e também fornece um sinal de parada.

Assim, o loop passa a contar com uma medida explícita de progresso.

Fonte: <https://arxiv.org/abs/2611.08977>

## Treinamento por exploração

Para treinar bem, o EBR usa treinamento por exploração, chamado de state-based explorative modeling (SXM). A ideia é explorar várias trajetórias latentes durante o treino e supervisionar a que tem a melhor correspondência com a solução.

O SXM tem duas variantes. O Forward SXM escolhe entre estados candidatos. O Reverse SXM escolhe entre as soluções válidas da entrada. O objetivo é descobrir modos adicionais e modelar melhor a paisagem de energia em um conjunto mais amplo de estados.

Fonte: <https://github.com/wwillchen/ebr>

## Os resultados no Sudoku-Extreme

O teste de destaque é o Sudoku-Extreme. Nele, o EBR usa 345 vezes menos computação na inferência que o EqR, o segundo melhor modelo da comparação. Também atinge 99,9% de acurácia com apenas 1,8 milhão de parâmetros, com custo de treino comparável ao dos outros modelos.

Para igualar a melhor acurácia do EqR, o EBR precisa de 7 vezes menos iterações e 43 vezes menos amostras.

Fonte: <https://energy-based-reasoners.github.io/>

## Cobertura de soluções em benchmarks multi-solução

Em todos os benchmarks com várias soluções válidas, o EBR alcança cobertura de ponta de soluções distintas válidas, mantendo acurácia próxima de 100% com uma única amostra.

Isso importa porque um bom raciocinador não deve apenas acertar uma resposta: deve conseguir gerar respostas diferentes e válidas quando o problema admite mais de uma.

Fonte: <https://arxiv.org/abs/2611.08977>

## Os benchmarks avaliados

O repositório treina e avalia o EBR em quatro benchmarks de raciocínio algorítmico.

- Sudoku-Extreme: 1.000 quebra-cabeças com 1.000 aumentações cada.
- Maze-Hard: labirintos de 30x30.
- N-Queens: tabuleiros de 8x8 e 10x10, na divisão do GRAM.
- Graph Coloring: 8 e 10 vértices, nos dados liberados pelos autores do GRAM.
- Além dos quatro, ARC-AGI-1, ARC-AGI-2 e ConceptARC: scripts de download e build incluídos; configs de treino e checkpoints serão liberados em breve.

Fonte: <https://github.com/wwillchen/ebr>

## Os números

Os números abaixo vêm do artigo, da página e do repositório do projeto. As comparações são com o EqR no Sudoku-Extreme.

- 345x: menos computação na inferência no Sudoku-Extreme, comparado ao EqR, o segundo melhor modelo.
- 99,9%: acurácia no Sudoku-Extreme com 1,8 milhão de parâmetros.
- 1,8 milhão: parâmetros do modelo nesse resultado.
- 7x: menos iterações para igualar a melhor acurácia do EqR.
- 43x: menos amostras para o mesmo objetivo.
- 4: benchmarks algorítmicos avaliados.
- 1.000: quebra-cabeças do Sudoku-Extreme, com 1.000 aumentações cada.
- 30x30: tamanho dos labirintos no Maze-Hard.

Fonte: <https://arxiv.org/abs/2611.08977>

## O que muda para você

O ganho mais concreto está na inferência: usar 345 vezes menos computação para raciocinar significa que rodar esses modelos pode ficar mais barato, se os números se confirmarem em testes de outros grupos.

O treino não fica mais caro: o custo de treino é comparável ao dos outros modelos. E a acurácia alta com 1,8 milhão de parâmetros sugere que o método é eficiente em parâmetros.

Exemplo: se uma equipe hoje gasta muito em inferência para raciocinar em loop em tarefas algorítmicas, um modelo baseado em energia pode reduzir esse custo, mantendo a acurácia. Ainda é preciso validar em tarefas fora do estudo.

Fonte: <https://arxiv.org/abs/2611.08977>

## O que fazer hoje

Se você quer experimentar o método, o repositório oficial traz código, datasets e checkpoints.

1. Instale os requisitos: Python 3.10 ou mais novo, CUDA 12.x e PyTorch 2.6 ou mais novo. Prefira GPU com bf16.
2. Instale as dependências com pip, conforme o README. Escolha a versão do torch compatível com o seu CUDA; o login no wandb é opcional.
3. Baixe datasets e checkpoints com bash scripts/download.sh. Use bash scripts/download.sh datasets ou bash scripts/download.sh checkpoints para baixar só um dos dois.
4. Ou construa os datasets com bash scripts/build_all.sh. Com WITH_ARC=1 também constrói o ARC.
5. Treine em uma tarefa com bash scripts/train.sh <tarefa>. Exemplos: sudoku, maze_hard_fast, nqueens_8, nqueens_10, graph_coloring_8, graph_coloring_10.
6. Avalie um checkpoint com bash scripts/eval.sh <tarefa> <checkpoint> <dir_de_saida>. No eval, N=1 usa a primeira amostra; N maior que 1 mantém a amostra com a menor energia final entre as primeiras N.

```
pip install --upgrade pip wheel setuptools
pip install torch --index-url https://download.pytorch.org/whl/cu124
pip install -r requirements.txt
wandb login YOUR-LOGIN
bash scripts/download.sh
bash scripts/train.sh sudoku
bash scripts/eval.sh sudoku checkpoints/sudoku-extreme/sudoku.pth out/sudoku
```

Fonte: <https://github.com/wwillchen/ebr>

## O que conferir

Antes de confiar nos números, vale checar os pontos abaixo.

- Os ganhos de 345x, 7x e 43x são resultados divulgados pelos autores no artigo, medidos contra o EqR no Sudoku-Extreme. Outros grupos precisam reproduzir para confirmar.
- A comparação de 345x é com o EqR, o segundo melhor modelo, não com todas as bases.
- No Sudoku-Extreme, o resultado informado é de computação de treino comparável; não conte com economia no treino.
- O repositório ainda está em construção; configs e checkpoints do ARC-AGI serão liberados em breve.
- O treino exige GPU com CUDA 12.x e PyTorch 2.6 ou mais novo; as tarefas sudoku e maze_hard_fast usam kernels Triton fundidos e precisam de GPU CUDA em Linux.
- Os checkpoints pré-treinados estão no Hugging Face (wxingxu/ebr) e são baixados com bash scripts/download.sh checkpoints.
- No eval, N maior que 1 mantém a amostra com a menor energia final entre as primeiras N amostras.

Fonte: <https://github.com/wwillchen/ebr>

## Glossário

- Raciocínio em loop: repetir um bloco recorrente várias vezes para aprofundar a resposta em espaço latente.
- Modelo recorrente: modelo que reutiliza o mesmo bloco em várias iterações.
- Função de energia: função que atribui uma pontuação (energia) a um estado; estados melhores têm energia mais baixa.
- Estado latente: representação interna do raciocínio, não o texto final.
- Gradient descent: processo de ajustar um estado na direção que diminui a função.
- Inferência: etapa de usar o modelo para responder, depois do treino.
- Parâmetro: peso aprendido do modelo; 1,8 milhão no resultado do Sudoku-Extreme.
- Benchmark: teste padronizado para comparar modelos.
- Checkpoint: arquivo com pesos do modelo e configuração de treino.
- SXM (state-based explorative modeling): treinamento por exploração de trajetórias latentes.
- EqR: modelo usado como base de comparação no Sudoku-Extreme.
- ARC-AGI: benchmark de raciocínio; suporte em preparação no repositório.

## Para onde ir depois

- Leia o artigo completo: https://arxiv.org/abs/2611.08977
- Explore o código: https://github.com/wwillchen/ebr
- Veja a página do projeto: https://energy-based-reasoners.github.io/
- Baixe os checkpoints pré-treinados no Hugging Face (wxingxu/ebr) e rode o eval em Sudoku-Extreme para ver os números.
- Acompanhe a liberação dos configs e checkpoints do ARC-AGI no repositório.
- Conheça os projetos em que o código se baseia: HRM, TRM e GRAM.

Fonte: <https://github.com/wwillchen/ebr>

## Além do vídeo

- Os autores do artigo são William Xingxu Chen, Alexi Gladstone, Zeyu Michael Li, Heng Ji e Yilun Du.
- O treino do Sudoku-Extreme leva de 3 a 4 horas em uma H200, com 60 mil passos.
- Os checkpoints são salvos a cada 5 mil passos, em outputs/ ou em OUTPUT_ROOT.
- O resume de treino usa load_checkpoint=<dir>/checkpoints/step_<N>_<run_id>.pth.
- NPROC=<n> roda em n GPUs; qualquer chave de config pode ser sobrescrita na linha de comando.
- O código se baseia em HRM, TRM e GRAM.
- A citação BibTeX do artigo está disponível no repositório.
- A estrutura do repositório inclui pretrain.py, evaluate.py, config/, scripts/, dataset/, models/, evaluators/ e utils/.
- As avaliações por tarefa usam amostras e segmentos específicos: Sudoku-Extreme com 8 amostras e 64 segmentos; Maze-Hard com 1.000 labirintos x 5 amostras e 16 segmentos; N-Queens e Graph Coloring com 20 amostras por entrada.
- Os builders de Sudoku, Maze-Hard, Graph Coloring e ARC baixam as fontes em revisões fixas.
