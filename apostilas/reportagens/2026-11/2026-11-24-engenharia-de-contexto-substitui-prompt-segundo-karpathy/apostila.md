# Engenharia de contexto substitui prompt segundo Karpathy

_2026-11-24 · reportagem_

Andrej Karpathy propõe substituir a engenharia de prompt pela engenharia de contexto. A ideia desloca a atenção para os arquivos, as instruções, as referências e os scripts que participam do caminho entre a entrada e a saída da IA. Esta apostila explica essa mudança e usa o Claude Code para mostrar como a organização do ambiente pode importar mais do que uma instrução longa. Você vai aprender a mapear o contexto de um projeto, reconhecer suas partes e testar essa lógica na prática.

## O contexto

Andrej Karpathy propôs substituir a engenharia de prompt pela engenharia de contexto. A proposta muda o foco da pergunta. Em vez de concentrar o trabalho apenas na instrução enviada à IA, passa a considerar tudo que participa do processo até a resposta.

Essa mudança acompanha a evolução dos modelos. Na adoção em massa do ChatGPT, os modelos ainda eram limitados e exigiam comandos muito específicos. Com o avanço rápido desses sistemas, o peso relativo da instrução diminuiu, enquanto o ambiente preparado para ela ganhou importância.

O prompt continua sendo parte do trabalho. A engenharia de contexto amplia a análise para incluir a maneira como arquivos, configurações, skills e scripts estão organizados no projeto. O resultado deixa de depender só do texto digitado e passa a depender também do que já está disponível no caminho.

## Quem é Andrej Karpathy

Andrej Karpathy foi um dos fundadores da OpenAI em 2015. Depois, passou cinco anos à frente da divisão de inteligência artificial da Tesla.

Em 2023, ele voltou à OpenAI. Posteriormente, saiu novamente para fundar uma empresa de educação e inteligência artificial. Essa trajetória, com passagens pela OpenAI e pela Tesla, ajuda a situar a proposta.

O tweet sobre vibe coding, publicado em fevereiro de 2025, ganhou mais visibilidade que seus trabalhos em direção autônoma e na construção da OpenAI. A proposta de engenharia de contexto aparece como um passo seguinte dessa reflexão sobre programação com IA.

Fonte: <https://karpathy.ai/>

## Vibe coding: o tweet que batizou a prática

Em fevereiro de 2025, Karpathy publicou o conceito de vibe coding. O tweet foi visto por mais de 5,2 milhões de pessoas. A prática consiste em descrever o que se quer em linguagem natural e deixar a IA escrever o código.

A expressão também carrega uma maneira de trabalhar: entregar-se ao fluxo e esquecer que o código sequer existe. Karpathy relatou que já programava quase sem tocar no teclado, usando principalmente comandos de voz.

O conceito resumiu um momento da programação com IA. A interface deixa de ser apenas um editor de texto e passa a incluir a conversa em linguagem natural. Isso ajuda a entender a ligação com a engenharia de contexto: quando a IA produz o código, a preparação do ambiente em que ela trabalha ganha peso.

Fonte: <https://x.com/karpathy/status/1886192184808149383>

## Por que isso importa

Um prompt é uma instrução dada à IA. Ele diz o que deve ser feito, mas não explica sozinho todo o ambiente disponível para a tarefa. Uma instrução pode pedir uma ação sem mencionar os arquivos do projeto, as referências já usadas ou os scripts que podem participar do processo.

Com modelos mais fracos, essa limitação tornava os comandos muito específicos especialmente importantes. O usuário precisava estruturar cada pedido com cuidado para obter o resultado desejado. À medida que os modelos melhoraram, a responsabilidade pela qualidade da saída passou a se distribuir por mais partes do sistema.

Para quem trabalha com agentes e projetos, a consequência é prática. Melhorar apenas o texto do pedido pode deixar de fora a maior oportunidade de ajuste. Organizar o contexto permite preparar o terreno antes da instrução e usar o projeto como parte do trabalho, e não apenas como destino do código gerado.

## O que é engenharia de contexto

Engenharia de contexto é o trabalho de organizar tudo que a IA pode usar entre receber uma entrada e produzir uma saída. Isso inclui texto, arquivos, instruções, referências e scripts. A expressão descreve uma arquitetura de informação e de execução, não uma fórmula para escrever uma frase melhor.

O contexto funciona como o conjunto de materiais e condições disponíveis para a tarefa. Uma instrução curta pode ser suficiente quando o projeto já reúne o que é necessário. O agente encontra no ambiente parte da orientação que, em outro arranjo, precisaria ser repetida a cada pedido.

A proposta também aproxima o trabalho com IA da organização de projetos. Pastas, arquivos e configurações passam a ser vistos como componentes do processo. Quem entende essa lógica consegue aplicar a ideia ao projeto atual e preparar os próximos com uma estrutura pensada para o trabalho com agentes.

## O caminho entre entrada e saída

A entrada, ou input, é o pedido enviado à IA. A saída, ou output, é o resultado produzido. Entre os dois extremos existe um percurso em que o sistema pode encontrar arquivos, ler instruções, usar referências e executar scripts. A engenharia de contexto se concentra nesse percurso.

O texto do prompt é apenas uma parte do que chega ao processo. Um projeto pode trazer informações que não aparecem na mensagem enviada naquele momento. Essas informações ajudam a delimitar a tarefa, o formato do trabalho e os recursos disponíveis.

Pensar nesse caminho muda a forma de investigar um resultado insatisfatório. A pergunta passa a incluir o que estava organizado no projeto, quais instruções estavam presentes e quais scripts podiam participar. O ajuste pode acontecer no input, mas também pode acontecer na estrutura que o rodeia.

## CLAUDE.md e settings.json

No Claude Code, CLAUDE.md e settings.json são partes do contexto que podem importar mais do que o prompt enviado. A grafia correta do primeiro nome é CLAUDE.md, com letras maiúsculas. Copiar o nome exatamente evita procurar ou referenciar um arquivo que não existe com a grafia adotada.

CLAUDE.md aparece como um arquivo do ambiente do projeto. settings.json aparece como um arquivo de configuração. Em termos práticos, os dois devem ser observados ao mapear o contexto, porque fazem parte do que está organizado antes do input e pode participar do trabalho do agente.

A lição não está em decorar uma lista de arquivos. Está em reconhecer que o projeto tem uma camada de instruções e configurações que precisa ser compreendida. O prompt enviado em seguida dialoga com essa camada.

Fonte: <https://code.claude.com/docs/en/claude-directory>

## Skills, pastas e scripts

As skills são outro componente citado no Claude Code. Em linguagem simples, uma skill reúne orientação especializada para determinada tarefa. Ela representa uma forma de colocar conhecimento de trabalho no contexto, para que o agente não dependa apenas de uma explicação criada do zero a cada pedido.

A estrutura de pastas determina como os arquivos e recursos do projeto estão organizados. Os scripts acrescentam outra camada, porque podem conter comandos ou instruções que serão executados durante o processo. Arquivos, skills e scripts formam um ambiente que o agente pode percorrer.

Essas peças explicam por que um input simples pode produzir um resultado forte em um projeto bem preparado. A instrução não carrega sozinha toda a informação. Ela aciona um conjunto de recursos que já foi organizado no projeto ou no agente.

Fonte: <https://code.claude.com/docs>

## Como funciona na prática

Imagine que você tem um projeto no Claude Code com CLAUDE.md, settings.json, skills e uma estrutura de pastas preparada. Dentro desse ambiente também existem referências e scripts relacionados ao trabalho. Nenhum desses elementos precisa aparecer inteiro na mensagem que você envia.

Ao dar uma instrução curta, o agente trabalha com o input e com o contexto disponível no projeto. As orientações ajudam a direcionar a tarefa, as configurações participam do ambiente e os scripts podem entrar no processo. A saída é construída a partir dessa combinação.

Esse exemplo mostra onde agir. Se o resultado não corresponde ao esperado, vale examinar a instrução e também os arquivos que cercam a tarefa. Uma skill incompleta, uma referência mal posicionada ou uma estrutura confusa pode fazer parte da explicação. O trabalho de melhoria alcança o projeto inteiro.

Fonte: <https://code.claude.com/docs>

## Os números

- 2015: ano em que Karpathy foi um dos fundadores da OpenAI. O número situa o início de sua passagem pela OpenAI.
- 5 anos: período em que ele dirigiu a divisão de inteligência artificial da Tesla. É uma duração, não uma medida de desempenho.
- 2023: ano em que Karpathy voltou à OpenAI. O retorno aconteceu antes do tweet sobre vibe coding.
- Fevereiro de 2025: mês de publicação do tweet que descreveu o vibe coding. A data posiciona o conceito na evolução da programação em linguagem natural.
- Mais de 5,2 milhões de visualizações: alcance do tweet. O número mede visualizações da publicação, não a qualidade do código produzido por quem adotou a prática.

## Linha do tempo

- 2015: Karpathy foi um dos fundadores da OpenAI.
- Durante 5 anos: ele dirigiu a divisão de inteligência artificial da Tesla.
- 2023: ele voltou à OpenAI.
- Depois do retorno: saiu novamente para fundar uma empresa de educação e inteligência artificial.
- Fevereiro de 2025: publicou o tweet sobre vibe coding, visto por mais de 5,2 milhões de pessoas.
- Posteriormente: propôs substituir a engenharia de prompt pela engenharia de contexto.

## Quem ganha e quem perde

Quem trabalha com agentes, projetos ou repositórios ganha uma nova forma de avaliar o próprio trabalho. O esforço pode se concentrar em preparar arquivos, skills, configurações e scripts para que o input encontre um ambiente útil. Essa abordagem ajuda a reutilizar a organização em projetos atuais e futuros.

Quem concentra toda a atenção na frase enviada à IA perde a chance de examinar o restante do processo. Um prompt pode ser bem escrito e ainda assim dialogar com um contexto desorganizado. Nesse caso, ajustar o comando resolve apenas uma camada do problema.

A vantagem descrita aqui é de método. Ela depende de entender e manter a estrutura usada pela ferramenta. O nome do arquivo, a função de cada configuração e a relação entre pastas e scripts fazem parte desse trabalho.

## O que ainda não se sabe

O alcance do tweet não mede a eficácia do vibe coding. As visualizações mostram quantas pessoas viram a publicação, mas não dizem quantos projetos funcionaram nem qual foi a qualidade do código gerado. O número serve para dimensionar a repercussão do conceito.

A engenharia de contexto também não transforma qualquer organização de arquivos em garantia de bom resultado. O contexto é uma variável central na proposta, e sua utilidade depende de como as peças se relacionam com a tarefa. Uma estrutura preparada para um projeto pode não atender a outro da mesma forma.

O Claude Code é o exemplo concreto apresentado. Ele ajuda a visualizar a lógica, mas não estabelece uma lista universal de componentes para toda ferramenta de IA. Antes de generalizar, observe como o ambiente do seu projeto realmente funciona.

- Confira a grafia de CLAUDE.md e mantenha o nome exatamente como aparece na documentação.
- Separe instruções, configurações, referências e scripts ao mapear o projeto, para entender o papel de cada parte.
- Observe o resultado depois de mudar o contexto e compare com a expectativa da tarefa.
- Trate números de alcance como repercussão da publicação, não como prova de desempenho técnico.

Fonte: <https://code.claude.com/docs>

## O que você pode fazer

Comece pelo ambiente que você já usa. O objetivo é enxergar o contexto antes de tentar melhorar o prompt.

1. Abra a pasta principal do seu agente, projeto ou repositório e identifique os arquivos e as pastas disponíveis. O resultado é um mapa inicial do contexto atual.
2. Se você usa Claude Code, procure CLAUDE.md, settings.json, skills e scripts. O resultado é saber quais peças citadas pela proposta existem no seu ambiente.
3. Leia as instruções, as referências e as configurações relacionadas à tarefa. O resultado é entender o que já está definido antes do envio do input.
4. Organize as pastas e os arquivos de acordo com o trabalho, mantendo skills e scripts ligados às funções que exercem. O resultado é uma estrutura mais fácil de percorrer pelo agente.
5. Envie uma instrução que aproveite esse contexto e observe a saída. O resultado é uma verificação prática de como o input e o ambiente estão colaborando.

Fonte: <https://code.claude.com/docs>

## Glossário

- Prompt: instrução ou comando enviado à IA para orientar uma tarefa.
- Input: entrada recebida pelo sistema, como o pedido feito pelo usuário.
- Output: saída produzida pelo sistema depois de processar a entrada e o contexto.
- Engenharia de prompt: trabalho de formular e ajustar as instruções dadas à IA.
- Engenharia de contexto: organização de tudo que participa do caminho entre a entrada e a saída.
- Contexto: conjunto de informações e recursos disponíveis para a IA durante a tarefa.
- Agente: sistema que usa IA para executar tarefas com base nas instruções e no contexto disponível.
- Repositório: conjunto organizado dos arquivos de um projeto.
- Arquivo de configuração: arquivo que reúne definições usadas para ajustar o funcionamento de uma ferramenta ou projeto.
- Skill: orientação especializada usada para conduzir determinada tarefa.
- Script: arquivo com comandos ou instruções que podem ser executados durante o processo.
- Vibe coding: prática de descrever o que se quer em linguagem natural e deixar a IA escrever o código.
- Claude Code: ferramenta usada aqui como exemplo de organização de contexto em agentes e projetos.
- CLAUDE.md: arquivo citado como parte do contexto no Claude Code, com essa grafia exata.
- settings.json: arquivo de configuração citado como parte do contexto no Claude Code.

## Para onde ir depois

O próximo passo é aplicar a lógica a um projeto real e observar o que muda quando o contexto fica mais explícito. A prática ajuda a perceber quais arquivos e recursos realmente participam do trabalho.

- Escolha um projeto atual e mapeie seus arquivos, instruções, referências, skills e scripts antes de alterar o prompt.
- Use a documentação oficial do Claude Code para entender os componentes do ambiente citados nesta apostila.
- Releia o tweet original sobre vibe coding para situar a prática que antecedeu a proposta de engenharia de contexto.
- Faça um teste com uma instrução simples em um projeto organizado e registre o que estava disponível no contexto antes de avaliar a saída.

Fonte: <https://code.claude.com/docs>
