# Hassabis propõe o teste de Einstein para medir a AGI

_2026-11-18 · reportagem_

O teste de Einstein propõe medir a AGI pela capacidade de um modelo, com conhecimento limitado a 1911, chegar à relatividade geral. A discussão se estende à escolha das perguntas que tornam esse salto possível. Esta apostila explica o corte de conhecimento em 1911, o experimento Machina Mirabilis e o risco de entregar a resposta dentro da própria pergunta. Você vai entender por que uma anomalia pode importar mais que uma conclusão pronta e como uma nova representação muda o problema. Ao final, conseguirá separar o que um modelo produziu da seleção humana que tornou aquele resultado possível.

## O contexto

Uma IA pode acertar uma prova e ainda enfrentar dificuldade para resolver um problema que exige mudar a forma de pensar. O debate sobre AGI trata dessa distância. No recorte desta discussão, a AGI é a inteligência artificial geral capaz de fazer tudo o que um humano especialista consegue. Demis Hassabis propõe avaliar essa ambição pela criação de conhecimento científico.

A discussão sobre IA científica encontra um paralelo em A Chegada e no conto Story of Your Life. As obras ajudam a levantar uma hipótese: a linguagem usada para descrever o mundo também limita ou amplia as perguntas que conseguimos fazer. Essa ideia serve para entender o que uma IA científica precisaria fazer antes de apresentar uma teoria.

## O fato

Demis Hassabis, CEO da Google DeepMind, propôs o teste de Einstein como régua para a AGI. A proposta congela o conhecimento científico em 1911. O modelo estudaria apenas o disponível até aquele corte, sem conhecimento explícito de Einstein, relatividade, mecânica quântica e física moderna. A tarefa seria trabalhar com os problemas da época e tentar propor a relatividade geral.

Einstein formulou a relatividade geral em 1915, quatro anos depois do corte. O período importa porque a comparação procura reproduzir o ponto de partida do cientista, com as contradições e os dados que ele tinha. O teste pergunta se uma máquina seria capaz de construir uma nova forma de entender o problema.

## Por que isso importa

Benchmarks avaliam desempenho em tarefas delimitadas. Um modelo pode acertar questões de múltipla escolha, resolver quebra-cabeças, passar em exames como a OAB e, ainda assim, tropeçar em uma conta que uma criança faria com um ábaco. Esses resultados continuam úteis, mas medem uma parte do problema. Acertar provas e agir no mundo são exigências diferentes.

Uma descoberta científica começa antes da resposta. Alguém precisa perceber uma contradição, decidir que ela importa, escolher uma observação e abandonar hipóteses que não funcionam. O teste de Einstein desloca a avaliação para esse processo. Ele procura medir a produção de uma explicação nova a partir das condições históricas disponíveis.

## O que estava em jogo em 1911

Einstein não tinha um documento final da relatividade geral para consultar. Ele tinha contradições conceituais, dados experimentais, matemática e intuição física. Uma das contradições citadas é a órbita de Mercúrio, que não fechava. Em linguagem simples, a explicação disponível não conseguia acomodar tudo o que a observação mostrava.

Uma anomalia desse tipo abre mais de um caminho. O pesquisador pode ajustar um detalhe da teoria, mudar uma hipótese ou reformular o problema inteiro. Einstein acabou colocando o espaço e o tempo como a própria dinâmica do problema. O desafio do teste está em chegar a esse tipo de mudança sem receber a teoria pronta.

## O gargalo: saber qual pergunta fazer

Se o enunciado aponta qual suposição deve ser abandonada, o modelo recebeu parte do raciocínio do pesquisador. Encontrar a saída pode continuar difícil, mas a descoberta da pergunta já foi conduzida por alguém. Esse é o risco do raciocínio circular: a resposta aparece escondida nas pistas do enunciado.

No experimento de Michael Hla, os lampejos surgiram quando o modelo recebeu a observação certa. A escolha humana não elimina a reação do modelo, mas muda o que o resultado demonstra. Para avaliar uma IA científica, é preciso registrar quem escolheu o experimento e quais pistas foram fornecidas.

Fonte: <https://michaelhla.com/blog/machina-mirabilis.html>

## Machina Mirabilis: um modelo treinado antes de 1900

Michael Hla treinou um modelo do zero no projeto Machina Mirabilis. O treinamento usou somente texto publicado antes de 1900, com cerca de 22 bilhões de tokens limpos. Tokens são unidades em que o texto é dividido para processamento. O volume indica a escala do material de treinamento e, por si só, não comprova capacidade de raciocínio.

Depois, o modelo recebeu observações experimentais que causavam dúvidas entre os cientistas da época. Hla afirma que ele é pequeno demais para raciocinar de verdade, mas teve lampejos de intuição. O projeto disponibiliza seu código em https://github.com/michaelhla/gpt1900. Esse experimento usa um corte anterior a 1900 e não equivale ao teste de Einstein, que propõe conhecimento até 1911.

Fonte: <https://michaelhla.com/blog/machina-mirabilis.html>

## O efeito fotoelétrico: o lampejo do modelo

Diante dos dados do efeito fotoelétrico, o modelo insistia que a luz não podia ser contínua e deveria ser feita de partes separadas de frequências variadas. O efeito fotoelétrico é um fenômeno em que a luz provoca a emissão de elétrons de um material. As observações desafiavam a ideia de tratar a luz apenas como um fluxo contínuo.

A fala do modelo se aproxima da ideia de pacotes de energia. Por volta de 1900, Planck percebeu que a energia precisava chegar em pedaços para que a conta fechasse. Em 1905, Einstein levou essa ideia adiante e usou pacotes de luz para explicar o efeito fotoelétrico, trabalho pelo qual recebeu o Prêmio Nobel. O modelo treinado com texto anterior a 1900 tropeçou na fronteira em que essa mudança começava a se formar.

O limite do exemplo é importante. O modelo apontou para uma representação descontínua da luz, mas não formulou a explicação completa de Einstein em 1905. Além disso, um humano já havia selecionado os dados do efeito fotoelétrico. O resultado é um sinal de intuição diante de um problema escolhido.

Fonte: <https://michaelhla.com/blog/machina-mirabilis.html>

## Como funciona na prática

Imagine que um pesquisador reúne as observações disponíveis em 1911 e entrega tudo a um modelo sem conhecimento posterior. Se o pesquisador também escreve que a órbita de Mercúrio não fecha e que é preciso abandonar a física clássica, a pista já contém a direção da resposta. O modelo pode concluir, mas parte do enquadramento veio pronta.

Agora imagine que o pesquisador entrega apenas dados e contradições, sem apontar qual merece atenção. O modelo precisa notar a anomalia, formular uma pergunta sobre ela e propor uma mudança de representação. A qualidade dessa pergunta determina o problema que a resposta tenta resolver.

Esse exemplo é hipotético e ajuda a ler o experimento de Hla. Quando o texto registra um lampejo diante do efeito fotoelétrico, o humano já havia selecionado a observação. A reação mostra como o modelo tratou aquele problema. Ela ainda não mostra que ele encontrou sozinho o problema no conjunto.

## A resposta é 42 e o problema da pergunta

Em O Guia do Mochileiro das Galáxias, uma civilização constrói um supercomputador para descobrir a resposta para a pergunta fundamental sobre a vida, o universo e tudo mais. Depois de 7,5 milhões de anos, ele responde: 42. O problema é que ninguém sabia qual era a pergunta. O número pertence à ficção e representa uma conclusão sem problema definido.

A piada alcança um ponto importante da avaliação de IA. Uma conclusão grandiosa pode surgir sem que o sistema entenda o que deveria investigar. O raciocínio de um LLM pode produzir uma sequência longa de passos, mas a qualidade do resultado depende da formulação que orientou essa sequência. Um benchmark que entrega a pergunta certa pode medir a resposta e deixar de medir a descoberta da pergunta.

## A linguagem que muda o pensamento

Em Story of Your Life e A Chegada, a linguagem dos heptápodes organiza a experiência de outra forma. Depois de aprendê-la, a protagonista passa a perceber passado, presente e futuro simultaneamente. Na obra, isso é ficção científica. A ideia que interessa à discussão é que uma estrutura de linguagem pode mudar o tipo de pensamento possível.

A analogia tem uma aplicação técnica. Representações e abstrações determinam quais padrões ficam visíveis, quais relações podem ser comprimidas e quais perguntas conseguem ser formuladas. Em 1915, Einstein não apenas respondeu a uma pergunta que já estava na lousa. Ele mudou o modo de formular o problema ao colocar o espaço e o tempo como a própria dinâmica do problema.

Para a AGI, isso amplia a pergunta do teste. Um sistema treinado até 1911 precisaria perceber que a forma de enxergar espaço, tempo e gravidade estava inadequada. Essa percepção é uma reformulação. A derivação da relatividade geral seria a resposta construída depois dela.

## Formular bons problemas na matemática

Hassabis comentou que resolver um problema famoso, como a hipótese de Riemann, seria espetacular. Segundo ele, seria ainda melhor conseguir propor um problema matemático de ponta. A formulação define quais estruturas merecem investigação, que tipo de explicação será aceito e quais caminhos de pesquisa fazem sentido.

Na ciência, escolher uma anomalia promissora tem um papel semelhante. Uma IA científica propositiva poderia participar da etapa anterior à solução, apontando que uma hipótese está mal formulada ou que a pergunta principal está no lugar errado.

- "Essa hipótese parece mal formulada."
- "Esses dados sugerem que a pergunta principal talvez não seja essa."
- "Você está tentando explicar X, mas a anomalia relevante está em Y."
- "Esse problema parece exigir uma nova variável ou representação."
- "Essa literatura está presa em uma dicotomia falsa."

## As capacidades de uma IA científica

Uma IA que participa da descoberta científica precisa de mais do que produção de respostas. O processo envolve agência científica, modelos de mundo capazes de prever causalidade, interação com experimentos físicos, memória de longo prazo e capacidade de descartar hipóteses. Também envolve uma relação propositiva com a informação disponível, seja nos pesos do modelo, seja por meio de um harness que busca conteúdo na internet.

Um modelo de mundo representa relações entre fenômenos e permite antecipar consequências. A causalidade acrescenta a explicação de por que uma mudança produz outra. A memória mantém o fio de uma investigação ao longo do tempo. O harness organiza ferramentas e informações ao redor do modelo. Cada peça pode falhar separadamente, mesmo quando o sistema escreve uma resposta convincente.

Entre as muitas capacidades que esses sistemas precisam ter, algumas já estão próximas do que os LLMs atuais conseguem fazer. Outras, como as citadas acima, exigem um salto mais profundo. O teste de Einstein reúne essas exigências em um desafio, mas acertar uma resposta não estabelece que todas elas estejam presentes.

## Linha do tempo

Os marcos ajudam a separar o experimento de Hla da proposta de Hassabis. O primeiro usa um corte anterior a 1900. O segundo propõe conhecimento até 1911.

- Antes de 1900: período de publicação dos textos que Michael Hla usou no treinamento do modelo gpt1900; o recorte exclui trabalhos publicados a partir de 1900.
- Por volta de 1900: Planck percebeu que a energia precisava chegar em pedaços para que a conta fechasse.
- 1905: Einstein usou a ideia de pacotes de luz para explicar o efeito fotoelétrico, trabalho pelo qual recebeu o Prêmio Nobel.
- 1911: corte de conhecimento proposto no teste de Einstein; o modelo teria apenas o que se sabia até ali.
- 1915: Einstein formulou a relatividade geral, quatro anos após o corte.

## Quem ganha e quem perde

Pesquisadores podem ganhar um critério que observa a descoberta, e não apenas o acerto em tarefas conhecidas. A ciência pode ganhar sistemas capazes de identificar anomalias e propor enquadramentos diferentes. Para quem acompanha IA, o teste oferece uma pergunta mais exigente: o sistema encontrou um caminho novo ou apenas repetiu um caminho que o enunciado já indicava?

Sistemas cujo desempenho depende de respostas conhecidas ou de muitas orientações humanas tendem a sair enfraquecidos dessa avaliação. Equipes que medem um produto apenas por provas e benchmarks também perdem uma verificação importante. O teste não torna os benchmarks antigos inúteis. Ele acrescenta uma exigência que eles não cobrem.

## O que ainda não se sabe

O experimento de Hla e a proposta de Hassabis respondem a perguntas diferentes. O primeiro relata lampejos de intuição em um modelo pequeno. O segundo é uma régua proposta para avaliar a AGI.

- Tamanho do modelo: Hla afirma que ele é pequeno demais para raciocinar de verdade; o volume de texto usado no treinamento não comprova raciocínio.
- Seleção humana: os lampejos apareceram depois que um humano escolheu o experimento e apontou os dados.
- Escopo do resultado: a resposta sobre a luz se aproxima da ideia de pacotes de energia, mas não equivale à formulação completa da teoria de Einstein em 1905.
- Recorte temporal: o gpt1900 usou texto anterior a 1900; o teste de Einstein propõe conhecimento até 1911.
- Conclusão sobre AGI: um lampejo em um problema selecionado não demonstra que um sistema descobriu sozinho uma teoria.
- Interpretação dos links: o post, o repositório, a demo e os modelos documentam o projeto; a existência dessas páginas não comprova o resultado científico.

Fonte: <https://michaelhla.com/blog/machina-mirabilis.html>

## O que você pode fazer

Ao encontrar uma notícia ou uma demonstração que promete descoberta científica, aplique o mesmo exame. O objetivo é identificar qual capacidade foi demonstrada e qual parte do caminho veio pronta.

1. Localize o corte de conhecimento na descrição do experimento e verifique até que ano vão os textos e quais conhecimentos posteriores foram excluídos. Você saberá se a comparação histórica corresponde ao caso que está avaliando.
2. Separe observações e respostas ao ler a demonstração. Anote quais dados foram entregues ao modelo e qual teoria você espera que ele construa. Você distinguirá a evidência disponível do conhecimento posterior.
3. Procure a escolha da pergunta no relato do experimento. Veja se um humano selecionou a anomalia, indicou uma direção ou escreveu pistas no enunciado. Você poderá medir a intervenção humana.
4. Compare o resultado com o marco histórico. No caso do efeito fotoelétrico, situe a fala do modelo entre a ideia de Planck, por volta de 1900, e a explicação de Einstein em 1905. Você evitará tratar uma aproximação como descoberta completa.
5. Termine a avaliação reformulando o problema. Pergunte se o sistema apenas respondeu ou também apontou que a hipótese, a variável ou a pergunta precisava mudar. Você decidirá qual capacidade ficou demonstrada.

Fonte: <https://michaelhla.com/blog/machina-mirabilis.html>

## Glossário

- AGI: inteligência artificial geral; no recorte desta discussão, uma IA capaz de fazer tudo o que um humano especialista consegue.
- Agência científica: capacidade de conduzir uma investigação, escolhendo hipóteses, experimentos e próximos passos.
- Anomalia: observação ou resultado que não se encaixa na explicação disponível.
- Benchmark: teste usado para avaliar e comparar o desempenho de sistemas.
- Causalidade: relação pela qual um fenômeno produz outro; permite explicar consequências, e não apenas reconhecer padrões.
- Corte de conhecimento: data limite que separa os dados disponíveis do conhecimento posterior.
- Efeito fotoelétrico: fenômeno em que a luz provoca a emissão de elétrons de um material.
- Harness: ambiente que organiza o acesso do modelo a ferramentas e informações, incluindo buscas na internet.
- Hipótese: explicação proposta que pode ser confrontada com dados.
- Mecânica quântica: área da física que estuda o comportamento da matéria e da luz em escalas muito pequenas.
- Modelo de mundo: representação interna de como o mundo funciona, usada para antecipar resultados.
- Pacote de luz: nome simplificado para a ideia de que a luz transporta energia em porções discretas.
- Pesos: valores aprendidos durante o treinamento que guardam parte do conhecimento e dos padrões do modelo.
- Raciocínio circular: argumento que pressupõe, escondida ou abertamente, a conclusão que deveria descobrir.
- Relatividade geral: teoria formulada por Einstein em 1915 que reformulou a compreensão de espaço, tempo e gravidade.
- Representação: forma de organizar informações e conceitos para descrever um fenômeno.
- Token: unidade em que um modelo divide o texto para processá-lo; pode corresponder a partes de palavras.

## Para onde ir depois

O próximo passo é acompanhar o experimento de Hla e aplicar a distinção entre responder e formular. Comece pelo post, depois examine o código e a demo para ver o que cada parte documenta.

- Leia o post do Machina Mirabilis: https://michaelhla.com/blog/machina-mirabilis.html
- Consulte o repositório oficial gpt1900: https://github.com/michaelhla/gpt1900
- Abra a demo do modelo gpt1900: http://gpt1900.com
- Veja a coleção de modelos no Hugging Face: https://huggingface.co/collections/mhla/gpt-1900
- Pratique com um caso: escreva separadamente a observação, a pergunta feita ao modelo e a reformulação que uma descoberta exigiria. Depois, marque quais partes vieram de uma escolha humana.

## Além do vídeo

- No conto, Gary percebe que os heptápodes respondem quando os humanos apresentam equações físicas ou matemáticas, mas não respondem a perguntas abertas sobre novas leis da física.
- Uma das interpretações da obra é que os heptápodes evitam fornecer conhecimento novo para não alterar a evolução da humanidade.
- Os 7,5 milhões de anos que o supercomputador de O Guia do Mochileiro das Galáxias passa pensando permitem uma associação com o reasoning dos LLMs.
- Os exemplos de possíveis fronteiras científicas incluem matéria escura, energia escura e a cura do câncer.
