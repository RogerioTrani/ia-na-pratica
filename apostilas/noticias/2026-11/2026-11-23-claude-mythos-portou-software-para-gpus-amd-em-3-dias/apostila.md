# Claude Mythos portou software para GPUs AMD em 3 dias

_2026-11-23 · noticia_

A Anthropic disse a investidores que o Claude Mythos Preview levou cerca de três dias para preparar o processamento de prompt de um modelo em GPUs AMD MI355X, com desempenho útil e quase 100% dos kernels portados ou escritos pelo modelo. O prazo cobre uma etapa específica do trabalho e contrasta com uma estimativa histórica de 6 a 12 meses para preparar novos aceleradores com engenharia tradicional. Esta apostila explica o que são kernels, como CUDA e ROCm organizam essa camada de software e por que a redução do prazo pode baratear a troca de fornecedor de chips. Você também vai aprender a separar o resultado anunciado das perguntas que ainda exigem medição, incluindo desempenho, escopo do teste e necessidade de hardware para validação. Ao final, terá critérios para ler o anúncio sem confundir portabilidade com desempenho equivalente.

## O fato

Em 10 de novembro de 2026, às vésperas do IPO, a Anthropic apresentou a investidores um resultado obtido com o Claude Mythos Preview. Segundo a empresa, o modelo levou cerca de três dias para colocar o processamento de prompt de um modelo da Anthropic em GPUs AMD MI355X, alcançando um nível de desempenho considerado útil.

Nesse trabalho, o Mythos portou ou escreveu quase 100% dos kernels com, nas palavras da empresa, basicamente nenhuma intervenção humana. Tom Brown, cofundador e diretor de computação da Anthropic, apresentou esse prazo como uma redução diante de um trabalho que antes consumia meses e exigia dezenas de engenheiros.

O anúncio tem importância porque vem da própria Anthropic, que compra os chips e usa a infraestrutura para executar seus modelos. A empresa não está vendendo GPUs: está mostrando como pretende preparar novas plataformas para sua própria operação.

Fonte: <https://www.anthropic.com>

## Por que isso importa

Um modelo de IA depende de software escrito para o chip que o executa. Essa camada precisa organizar o trabalho de cálculo de maneira que o hardware consiga processar o modelo. Quando esse software é adaptado para um fornecedor, o custo e o tempo de adaptação influenciam a escolha do chip.

A CUDA, plataforma de programação da Nvidia, acumulou ao longo de quase duas décadas um conjunto de ferramentas, código e conhecimento de engenharia. Parte da vantagem da Nvidia está nessa trajetória. A expressão 'fosso do CUDA' descreve a dificuldade de reproduzir esse ecossistema ao mudar para outro fornecedor.

Se uma IA consegue escrever ou adaptar boa parte do código de baixo nível em dias, a barreira para testar outro chip diminui. A escolha pode passar a depender mais de preço, disponibilidade e desempenho medido. O anúncio da Anthropic aponta nessa direção, mas não prova que todas as vantagens da CUDA desapareceram.

Fonte: <https://developer.nvidia.com/cuda-zone>

## Kernels: a camada que liga o modelo ao chip

Kernel é um trecho de código de baixo nível que executa uma parte específica do trabalho no processador. No contexto de modelos de IA, os kernels ligam as operações do modelo aos recursos da GPU. Eles determinam como o cálculo é organizado para aquele hardware.

Cada plataforma tem arquitetura e formas próprias de executar esse trabalho. Por isso, adaptar um modelo para um chip novo pode exigir a revisão de kernels escritos para outra plataforma. A Anthropic baseia a estimativa de 6 a 12 meses em sua experiência histórica com engenharia tradicional, em que ajustar o código a cada plataforma era um desafio.

Imagine que um modelo já funciona em um conjunto de GPUs, mas a equipe quer avaliar outro fornecedor. O modelo continua sendo o mesmo, enquanto a camada que conversa com o chip precisa ser adaptada. O trabalho do Mythos descrito no anúncio está nessa camada. Portar software significa fazer essa adaptação; escrever um kernel significa criar o código necessário para executar uma operação específica.

## O que os três dias realmente medem

O processamento de prompt, também chamado de prefill, é a etapa em que o modelo lê e processa o que recebeu antes de começar a responder. A resposta é gerada em outra etapa, chamada de decode. Separar as duas ajuda a entender o alcance do resultado.

A nota do slide limita os cerca de três dias ao prefill de um modelo da Anthropic em GPUs AMD MI355X, com desempenho útil. A empresa não informou se a etapa de resposta entrou na conta. Portanto, o prazo não deve ser lido como uma medida de todo o processo de atendimento do modelo.

A expressão 'desempenho útil' indica que o resultado tinha uma qualidade de execução considerada aproveitável, mas o anúncio não apresenta uma velocidade de comparação com as GPUs da Nvidia. O gráfico da Anthropic mostra duas linhas chegando à mesma marca de aproximadamente 100%, sem explicar 100% de quê. Isso impede transformar o gráfico em uma medida de desempenho ou de conclusão de todo o sistema.

Fonte: <https://www.anthropic.com>

## A comparação com a engenharia tradicional

Tom Brown disse que o trabalho original exigia dezenas de engenheiros durante meses. Já a estimativa de 6 a 12 meses é atribuída à Anthropic, com base em sua experiência histórica ao preparar novos aceleradores com métodos tradicionais de engenharia.

Os cerca de três dias do Mythos se aplicam ao recorte divulgado no slide: processamento de prompt de um modelo, em MI355X, com desempenho útil. A comparação mostra uma mudança grande no esforço de software dentro desse recorte. Ela não estabelece uma comparação direta entre duas execuções completas e idênticas.

O prospectus da Anthropic também afirma que suas equipes de engenharia, usando o Claude, conseguem levar novas plataformas de chips à produção mais rápido. O documento não associa essa frase a um número específico nem nomeia um chip. A afirmação reforça a direção da mudança, enquanto o exemplo do MI355X fornece o recorte concreto.

Fonte: <https://www.anthropic.com>

## O caminho da AMD: de ROCm à geração de kernels por IA

A AMD tem o ROCm como plataforma de programação e a HIP como camada de programação. Código escrito para CUDA precisa ser transformado para funcionar nesse ambiente, e a própria AMD criou o HIPify para ajudar na conversão. O Mythos entra nesse processo como uma ferramenta capaz de analisar e gerar código, em vez de apenas aplicar uma conversão mecânica.

Em 1º de agosto de 2025, pesquisadores da AMD publicaram o GEAK, um agente de IA que escreve kernels de GPU. Em uma comparação com 30 kernels escritos por especialistas, o GEAK acertou 19 e alcançou, em média, 0,92 vez a velocidade das versões dos especialistas. O resultado pertence ao GEAK e não deve ser atribuído ao Mythos.

Em 24 de setembro de 2025, Lisa Su, presidente do conselho e CEO da AMD, disse que grande parte do software escrito em CUDA podia ser traduzida para a AMD por software. Em 1º de abril de 2026, Anush Elangovan, vice-presidente de software de IA da AMD, comparou o Claude ao HIPify e afirmou que o Claude era melhor porque tinha busca na web integrada.

Em julho de 2026, Vamsi Boppana, vice-presidente sênior de IA da AMD, disse que engenheiros da empresa usavam modelos de IA para gerar kernels de GPU. Segundo ele, em alguns casos os kernels gerados ficaram melhores que as versões ajustadas manualmente. Pelo acordo firmado com a Anthropic em julho, a AMD também usa o Claude para otimizar cargas de trabalho das GPUs Instinct e acelerar o desenvolvimento do ROCm.

## O acordo com a AMD e o teste do rack MI355X

A Anthropic começou a trabalhar com GPUs AMD em 2026 e tem um acordo para até 2 gigawatts. Esse valor expressa o limite previsto no acordo; ele não é uma medida do resultado obtido pelo Mythos. A parceria também aproxima uma empresa que desenvolve modelos de uma fornecedora de chips que disputa espaço com a Nvidia.

Em 23 de julho de 2026, Tom Brown relatou no evento Advancing AI da AMD que um engenheiro pediu ao Claude para preparar um rack MI355X e deixou o trabalho rodando durante o fim de semana. Brown descreveu a tarefa como um grande esforço e disse que o desempenho foi aumentando. O relato de julho não informa um prazo fechado para esse teste.

O anúncio de novembro é mais específico: cerca de três dias, Claude Mythos Preview, quase 100% dos kernels portados ou escritos e basicamente nenhuma intervenção humana. A nota do slide acrescenta o limite ao processamento de prompt de um modelo. Os dois relatos mostram uma evolução do uso do Claude, mas têm recortes diferentes.

## A aposta da Anthropic em vários tipos de chip

A Anthropic já executa seus modelos em GPUs da Nvidia e da AMD, nos TPUs do Google e no Trainium da AWS. A empresa administra esse conjunto como um pool de computação fungível. Brown chamou a decisão inicial de trabalhar com vários chips de aposta incomum.

A estratégia reduz a dependência de um único fornecedor e permite que a empresa prepare diferentes plataformas para sua operação. Além disso, os TPUs do Google já podem executar nativamente modelos de IA construídos em PyTorch e que a Meta usa esses chips em produção. Isso mostra que a alternativa à GPU da Nvidia não se resume a um único tipo de hardware.

Ainda assim, fungível não significa que todos os chips sejam idênticos. Os TPUs do Google estão cada vez mais especializados, e aproveitar o máximo de cada plataforma continua exigindo hardware para testes. O pool dá flexibilidade à operação, mas a adaptação e a validação de cada plataforma continuam necessárias.

Fonte: <https://www.anthropic.com>

## A resposta da Nvidia

Em 15 de abril de 2026, Jensen Huang, CEO da Nvidia, disse em entrevista a Dwarkesh Patel que a empresa já usa muita IA para criar seus próprios kernels. Ele afirmou que ninguém conhece a arquitetura da Nvidia melhor que a própria empresa e que isso permite extrair o máximo dos chips.

Huang chamou a Anthropic de caso único, e não de tendência. A resposta da Nvidia separa a capacidade de gerar código do conhecimento acumulado sobre a arquitetura e da otimização do hardware. Para a Nvidia, escrever kernels com IA não elimina a vantagem de dominar a plataforma em que eles serão executados.

Existe também uma ligação financeira: Nvidia e AMD estão entre as sete empresas que compram 26 bilhões de dólares em ações da Anthropic no preço do IPO. A Nvidia participa do investimento na mesma empresa que Huang classificou como exceção.

## Os números

Cada número do anúncio responde a uma pergunta diferente. Manter o recorte evita transformar uma medida de prazo em prova de desempenho ou um resultado de um agente em resultado de outro.

- Cerca de três dias: prazo atribuído ao Claude Mythos Preview para o processamento de prompt de um modelo da Anthropic em GPUs AMD MI355X, com desempenho útil. O valor não inclui uma confirmação sobre a etapa de resposta.
- 6 a 12 meses: estimativa histórica da Anthropic para preparar novos aceleradores com engenharia tradicional. É a referência usada pela empresa, não uma medição do mesmo teste com outro método.
- Quase 100% dos kernels: parcela dos kernels que o Mythos portou ou escreveu no trabalho descrito. O número não significa 100% de todo o sistema, nem explica a marca de aproximadamente 100% do gráfico.
- Dezenas de engenheiros: tamanho da equipe que, segundo Tom Brown, era necessária no trabalho tradicional. O número descreve o esforço anterior e não a equipe usada no teste do Mythos.
- 19 de 30 kernels: quantidade acertada pelo GEAK em uma comparação da AMD com kernels escritos por especialistas, publicada em 1º de agosto de 2025.
- 0,92 vez a velocidade: resultado médio do GEAK frente aos kernels dos especialistas nesse mesmo teste. O valor indica 92% da velocidade média deles e pertence ao GEAK.
- Até 2 gigawatts: limite do acordo da Anthropic com a AMD. O valor descreve a escala prevista da parceria, não a velocidade do modelo nem o consumo medido no teste.
- 26 bilhões de dólares: valor das ações da Anthropic compradas por sete empresas no preço do IPO, incluindo Nvidia e AMD. A participação financeira não serve como prova de desempenho técnico.
- Primeiro semestre de 2027: previsão para os primeiros chips AMD MI450 da Anthropic em racks Helios. A nova geração permitirá observar se o resultado de três dias se repete.

## O que muda para você

A principal mudança está no custo de experimentar outra plataforma. Se adaptar o software para um chip novo exigia meses e uma grande equipe, a empresa podia ficar presa ao fornecedor já estabelecido. Um prazo menor torna a avaliação de outra opção mais acessível e desloca parte da decisão para preço, disponibilidade e desempenho.

O desempenho continua sendo a prova decisiva. Colocar o modelo para rodar não demonstra que o chip alternativo atende à mesma carga com a mesma eficiência. A Anthropic não divulgou a velocidade do modelo nas GPUs AMD em comparação com as GPUs Nvidia, então a equivalência de desempenho permanece uma questão aberta.

Exemplo: uma equipe avalia mover uma carga de IA para GPUs AMD. O primeiro resultado do Mythos pode mostrar que o software foi adaptado. A equipe ainda precisa medir como a plataforma executa o trabalho, separar prefill de decode e reservar hardware para testar o código gerado. Assim, a redução do prazo ajuda na avaliação sem substituir a medição.

## Linha do tempo

O anúncio da Anthropic reúne resultados produzidos em etapas diferentes. As datas ajudam a distinguir o trabalho da AMD, os relatos sobre o Claude e a apresentação feita aos investidores.

- 1º de agosto de 2025: pesquisadores da AMD publicam o GEAK, agente que escreve kernels de GPU, com 19 acertos em 30 kernels de especialistas e velocidade média de 0,92 vez a deles.
- 24 de setembro de 2025: Lisa Su diz que grande parte do código escrito para CUDA pode ser traduzida para a AMD por software.
- 1º de abril de 2026: Anush Elangovan compara o Claude ao HIPify e destaca a busca na web integrada ao Claude.
- 15 de abril de 2026: Jensen Huang afirma que a Nvidia usa IA para criar kernels e chama a Anthropic de caso único.
- 23 de julho de 2026: Tom Brown relata o trabalho de um engenheiro com o Claude em um rack MI355X; Vamsi Boppana fala sobre kernels gerados por IA; Andrew Dieckman diz ter quase nenhuma conversa com clientes da AMD sobre CUDA; Philippe Tillet, da OpenAI, afirma que um único engenheiro confirmou o funcionamento de racks Helios em poucos dias.
- 10 de novembro de 2026: a Anthropic apresenta o resultado do Mythos a investidores e atualiza o prospectus com a afirmação de que novas plataformas de chips entram em produção mais rápido.
- Primeiro semestre de 2027: chegada prevista dos primeiros chips AMD MI450 da Anthropic em racks Helios.

## O que fazer hoje

O anúncio oferece um critério prático para avaliar portabilidade sem cair em conclusões amplas demais. Use o recorte do teste como ponto de partida.

1. Defina a etapa medida: registre se o resultado se refere ao processamento de prompt, à geração da resposta ou ao conjunto. O resultado esperado é uma descrição que impeça aplicar o prazo de três dias a todo o atendimento do modelo.
2. Identifique o caso concreto: anote o modelo, a GPU e o nível de desempenho usados como referência. No anúncio da Anthropic, são um modelo da empresa, GPUs AMD MI355X e desempenho útil.
3. Separe adaptação de desempenho: trate a portabilidade dos kernels e a velocidade de execução como duas provas distintas. O resultado esperado é uma avaliação que não conclua equivalência apenas porque o modelo começou a rodar.
4. Mapeie a camada de software: verifique quais kernels precisam ser adaptados e quais ferramentas de conversão entram no caminho, como ROCm, HIP e HIPify. O resultado esperado é uma lista clara do trabalho de software envolvido.
5. Reserve hardware para teste: agentes que escrevem código de GPU precisam de GPUs para validar esse código. O resultado esperado é um ambiente de teste compatível com a plataforma avaliada.
6. Acompanhe a repetição do resultado: observe a chegada dos chips MI450 em Helios, prevista para o primeiro semestre de 2027, e os relatórios da Anthropic depois do IPO. O próximo dado deve mostrar se o prazo e o desempenho se mantêm em outra geração.

## O que conferir

O anúncio muda a percepção sobre o custo de adaptar modelos a novos chips. A leitura correta depende de conferir o escopo, a origem dos números e as condições de teste.

- Escopo do prazo: os cerca de três dias cobrem o processamento de prompt de um modelo em MI355X. A empresa não informou se a geração da resposta entrou na conta.
- Escopo do código: quase 100% dos kernels portados ou escritos não equivale a 100% de todo o software necessário para operar o sistema.
- Significado do desempenho: 'desempenho útil' não vem acompanhado de uma comparação de velocidade entre AMD e Nvidia.
- Leitura do gráfico: as duas linhas chegam a aproximadamente 100%, mas o eixo não explica 100% de quê. A marca não pode ser usada como medida isolada.
- Base da comparação: os 6 a 12 meses vêm da experiência histórica com engenharia tradicional. O anúncio não apresenta um controle experimental com o mesmo escopo dos dois lados.
- Necessidade de hardware: cada agente precisa de GPUs para testar o código. A falta constante de GPUs na AMD para esse tipo de desenvolvimento foi apontada como um possível novo gargalo.
- Troca de plataforma: os chips do pool da Anthropic não são totalmente intercambiáveis. Os TPUs do Google estão cada vez mais especializados, e extrair o máximo de cada plataforma exige teste no hardware correspondente.
- Revisão humana: antes de usar o caso para uma decisão de compra, confira separadamente portabilidade, desempenho, custo de validação e adequação da plataforma à carga de trabalho.

## Glossário

- Kernel: trecho de código de baixo nível que executa uma parte específica do trabalho no processador.
- CUDA: plataforma de programação da Nvidia usada para desenvolver software que executa em suas GPUs.
- ROCm: plataforma de programação da AMD para seu ambiente de GPUs.
- HIP: camada de programação do ROCm usada para adaptar código ao ambiente da AMD.
- HIPify: ferramenta criada pela AMD para ajudar na conversão de código escrito para CUDA.
- GPU: processador especializado em executar muitas operações de cálculo em paralelo, amplamente usado em IA.
- TPU: chip especializado desenvolvido pelo Google para cargas de trabalho de aprendizado de máquina.
- Trainium: chip da AWS usado pela Anthropic em sua infraestrutura de computação.
- Prefill: etapa em que o modelo lê e processa o prompt antes de começar a resposta.
- Decode: etapa em que o modelo gera a resposta depois do processamento do prompt.
- Porte de software: adaptação de um programa para funcionar em outra plataforma ou arquitetura.
- Fosso de software: vantagem construída por ferramentas, código e conhecimento que dificultam a troca para um concorrente.
- Pool de computação fungível: conjunto de diferentes recursos de computação administrado como uma capacidade comum, embora cada plataforma mantenha suas particularidades.
- Desempenho útil: nível de execução considerado suficiente para uma finalidade prática, sem indicar, por si só, uma velocidade específica.
- Agente de IA: sistema que recebe uma tarefa e executa ações para produzi-la, como escrever ou adaptar código.
- IPO: primeira oferta pública de ações de uma empresa, quando ela passa a negociar no mercado de capitais.

## Para onde ir depois

O próximo ponto de observação é a chegada dos primeiros chips AMD MI450 da Anthropic em racks Helios, prevista para o primeiro semestre de 2027. Uma nova geração permitirá verificar se o trabalho de preparação em cerca de três dias se repete e em qual escopo.

Depois do IPO, a Anthropic também passa a publicar resultados como empresa aberta. Para praticar a leitura desse tipo de anúncio, separe sempre três informações: qual etapa foi medida, qual hardware foi usado e qual comparação de desempenho foi apresentada. No caso do Mythos, a redução do prazo é o fato central; a equivalência entre AMD e Nvidia depende de uma medição que ainda precisa aparecer.
