# Harness Leaderboard compara 9 harnesses com 28.849 testes

_2026-11-24 · reportagem_

O Harness Leaderboard compara nove harnesses de agentes de código usando modelos abertos, com 28.849 testes rodados. Cada comparação mantém o modelo igual e altera apenas o harness, o que permite isolar a contribuição dessa camada. Esta apostila explica o conceito, o método e os cuidados para usar o ranking na escolha de um harness. Depois da leitura, você saberá conferir se uma comparação está avaliando o harness ou misturando modelos.

## O fato

Joël Niklaus criou o Harness Leaderboard, um ranking que compara nove harnesses de agentes de código executados com modelos abertos. Foram rodados 28.849 testes para montar a comparação.

O anúncio parte de uma pergunta prática: em qual harness rodar um modelo aberto? A proposta é responder com medição. A página oficial apresenta o ranking em um Hugging Face Space.

Fonte: <https://huggingface.co/spaces/joelniklaus/harness-leaderboard>

## Por que isso importa

Quem programa com modelos abertos escolhe o modelo e o harness. O modelo participa da geração das respostas, enquanto o harness organiza o trabalho do agente. Quando a decisão considera apenas o modelo, a camada que conduz a execução fica fora da análise.

O Harness Leaderboard trata essa escolha com medição. A pessoa pode consultar uma comparação que manteve o modelo aberto e variou o harness. Isso ajuda a separar o efeito da camada organizadora da influência de modelos diferentes.

Fonte: <https://huggingface.co/spaces/joelniklaus/harness-leaderboard>

## O que é um harness de agente de código

Harness é a camada que envolve o modelo e organiza o trabalho do agente. O modelo produz a resposta, e o harness estrutura o trabalho que cerca essa resposta durante a programação.

Essa distinção explica por que o mesmo modelo aberto pode ser avaliado em harnesses diferentes. A comparação mantém o componente que gera as respostas e troca a camada que organiza a atuação do agente.

## A regra da comparação

Em cada comparação do ranking, só o harness muda. O modelo aberto permanece o mesmo. Esse desenho é uma comparação controlada: o fator observado é o harness, enquanto os demais elementos são mantidos constantes.

Quando os resultados variam entre harnesses, a diferença pode ser atribuída à camada que foi alterada. Comparar dois harnesses com modelos diferentes responde a outra pergunta, porque a variação envolve o modelo e o harness.

O valor do método está em reduzir explicações concorrentes. O ranking avalia a camada que organiza o agente dentro do recorte de modelos abertos.

Fonte: <https://huggingface.co/spaces/joelniklaus/harness-leaderboard>

## O escopo da comparação

O ranking abrange nove harnesses de agentes de código. Todos são testados com modelos abertos e comparados lado a lado.

O recorte orienta a leitura. O objeto medido é o harness, e o modelo aberto funciona como ponto fixo da comparação. Uma conclusão sobre esses harnesses deve permanecer dentro desse contexto.

Fonte: <https://huggingface.co/spaces/joelniklaus/harness-leaderboard>

## Os números

Os números mostram a escala do trabalho e o tamanho do recorte. Eles precisam ser lidos com o que representam, sem tratar volume como resultado.

- 28.849 testes: quantidade de testes rodados para construir o ranking. O número representa o esforço de computação dedicado à comparação e não declara, sozinho, um vencedor.
- Nove harnesses: quantidade de camadas de agentes de código comparadas. Esse total define a amplitude do ranking.
- Modelos abertos: categoria de modelo usada nas comparações. É o recorte dentro do qual os resultados devem ser interpretados.
- Variável alterada: o harness. O modelo permanece igual para que a comparação foque na camada que organiza o trabalho do agente.

Fonte: <https://huggingface.co/spaces/joelniklaus/harness-leaderboard>

## Como funciona na prática

Exemplo: imagine que você quer comparar dois harnesses. Escolha um único modelo aberto e mantenha-o nas duas execuções. Depois, altere apenas o harness. A leitura do resultado fica centrada na camada que organiza o agente.

Se você trocar o modelo no meio da comparação, a diferença observada também poderá vir do modelo. O princípio é manter constante aquilo que não se quer testar. O ranking aplica essa lógica ao variar o harness.

## O que fazer hoje

A consulta ao ranking fica mais útil quando você já sabe qual modelo aberto pretende usar. Siga estes passos para manter a leitura dentro da regra da comparação.

1. Abra a página oficial do Harness Leaderboard em https://huggingface.co/spaces/joelniklaus/harness-leaderboard. O resultado esperado é localizar o ranking dos nove harnesses.
2. Defina o modelo aberto que você pretende usar. O resultado esperado é estabelecer o ponto fixo para ler as comparações.
3. Ao comparar dois harnesses, confira se o modelo aberto é o mesmo. O resultado esperado é manter a avaliação centrada no harness.
4. Escolha um dos nove harnesses como referência para o seu fluxo de programação. O resultado esperado é ter uma opção concreta para observar na prática.
5. Pratique com o harness escolhido em uma tarefa de programação que você já saiba verificar. O resultado esperado é observar como essa camada organiza o trabalho do agente com o modelo aberto.

Fonte: <https://huggingface.co/spaces/joelniklaus/harness-leaderboard>

## O que conferir

Uma boa leitura começa pelo que está sendo comparado. Antes de usar o ranking para decidir, confira o modelo, o recorte e o significado dos números.

- Modelo: verifique se as comparações que você está lendo usam o mesmo modelo aberto. Essa condição permite isolar o harness.
- Escala: leia 28.849 como quantidade de testes rodados. O número expressa o volume do trabalho de comparação e não indica, por si só, superioridade.
- Recorte: mantenha a conclusão dentro do universo de modelos abertos e dos nove harnesses comparados.
- Aplicação: use o ranking para orientar a escolha e observe o harness no seu próprio fluxo de programação.
- Fonte: consulte a página oficial do Harness Leaderboard para acessar o ranking.

Fonte: <https://huggingface.co/spaces/joelniklaus/harness-leaderboard>

## Glossário

- Harness: camada que envolve o modelo e organiza o trabalho do agente.
- Agente de código: sistema que usa um modelo para realizar tarefas de programação.
- Modelo aberto: modelo disponibilizado para uso aberto, conforme seus termos. No ranking, é o tipo de modelo empregado nas comparações.
- Leaderboard: ranking que ordena os resultados de uma comparação.
- Teste: execução usada para comparar os harnesses.
- Comparação controlada: comparação em que apenas o fator de interesse muda.
- Hugging Face Space: espaço hospedado na plataforma Hugging Face que apresenta o Harness Leaderboard.

## Para onde ir depois

O próximo passo é consultar o ranking oficial e escolher um harness para acompanhar no seu trabalho com modelos abertos. Depois, repita o exercício de leitura: identifique o modelo, confira se ele permaneceu igual e observe apenas a mudança do harness.

Para praticar, use uma tarefa de programação que você já conhece e observe o trabalho do agente ao testar outro harness. O objetivo é aplicar a mesma disciplina da comparação no seu uso diário.

Fonte: <https://huggingface.co/spaces/joelniklaus/harness-leaderboard>
