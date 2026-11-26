# Calibração do d1.2 define quando um humano revisa

_2026-11-23 · noticia_

A Liquid AI lançou os modelos de decisão d1.2 e d1.2-ultra com probabilidades calibradas e novas formas de responder a partir de texto, imagem e áudio. Nesta apostila, você vai entender como usar a confiança do modelo para separar respostas automáticas de casos que precisam de revisão humana. Também vai conhecer as cinco tarefas novas, os preços por token de entrada e o caminho para testar os modelos na Liquid API. Ao final, terá um roteiro prático para começar e uma lista de cuidados para interpretar pontuação, custo e confiança.

## O fato

Em 16 de novembro de 2026, a Liquid AI lançou os modelos de decisão d1.2 e d1.2-ultra. A empresa os disponibilizou na Liquid API e apresentou os dois como modelos omnimodais, capazes de processar texto, imagens e áudio.

O anúncio reúne cinco tarefas novas, probabilidades calibradas e uma estrutura de cobrança baseada apenas nos tokens de entrada. A proposta é permitir que uma aplicação não apenas obtenha uma resposta, mas também decida o que fazer com ela e quando pedir revisão humana.

Fonte: <https://www.liquid.ai/blog/d1-2>

## Por que isso importa

Uma empresa que usa IA para tomar decisões precisa saber quando confiar na resposta e quando interromper o fluxo. Uma porcentagem de confiança só ajuda se representar alguma coisa na prática. Se o modelo declara 80% de confiança e erra em muitos desses casos, o número não serve para automatizar nada.

Os modelos d1.2 e d1.2-ultra combinam essa leitura da incerteza com tarefas de saída mais específicas. O modelo pode ler um valor, apontar trechos de um texto, marcar objetos em imagens, estimar números com faixas e selecionar opções. Cada formato dá à aplicação uma informação concreta para usar ou conferir.

Fonte: <https://www.liquid.ai/blog/d1-2>

## Dois modelos que processam texto, imagem e áudio

A capacidade de entrada e o formato de saída são partes diferentes do funcionamento desses modelos. O anúncio informa que tanto d1.2 quanto d1.2-ultra processam texto, imagem e áudio. Em seguida, descreve cinco tarefas com resultados próprios, como um valor, um trecho, uma caixa, uma faixa ou uma seleção de opções.

Essa combinação permite tratar a resposta como parte de um processo de decisão. Uma aplicação pode receber a entrada, obter o resultado da tarefa e usar a confiança informada para definir o próximo passo. O conteúdo da resposta e a probabilidade associada a ela têm funções diferentes.

Fonte: <https://www.liquid.ai/blog/d1-2>

## Calibração: transformar confiança em decisão

Calibrar um modelo é fazer sua probabilidade declarada corresponder à realidade. Quando o modelo diz 80%, ele deve acertar cerca de 80% das vezes. Em termos simples, em cerca de oito de cada dez casos dessa faixa de confiança, a resposta precisa estar correta.

Com probabilidades calibradas, você pode estabelecer um limite de confiança. Acima dele, o fluxo segue automaticamente. Abaixo dele, uma pessoa confere. O limite define onde a revisão humana entra e concentra o trabalho das pessoas nos casos em que o modelo hesita.

Fonte: <https://www.liquid.ai/blog/d1-2>

## Ler um valor e mostrar de onde ele veio

A tarefa Read a value from the input (text, number or date) procura um valor na entrada, que pode ser texto, número ou data. O resultado não precisa ficar isolado: o anúncio mostra que o modelo também pode devolver os caracteres dos quais leu a informação.

Exemplo: Imagine uma fatura com a pergunta quanto há a pagar. O modelo devolve o valor correto junto com os caracteres que sustentam essa leitura. Quem recebe a resposta pode comparar o número com o trecho da fatura, o que facilita a conferência antes de usar o dado.

Fonte: <https://www.liquid.ai/blog/d1-2>

## Encontrar todos os trechos de um tipo no texto

A tarefa de spans encontra todas as passagens de um determinado tipo em um texto. Em vez de apresentar somente uma classificação geral, a saída aponta os trechos que correspondem ao critério procurado. Span é justamente esse recorte dentro do texto original.

Exemplo: Imagine que você precisa localizar todas as passagens que tratam de datas em um documento. A tarefa de spans devolve os trechos encontrados, mantendo a ligação com o texto de origem. Isso ajuda a revisar cada ocorrência sem depender de uma releitura inteira do documento.

Fonte: <https://www.liquid.ai/blog/d1-2>

## Localizar objetos em uma imagem

A tarefa de localização usa boxes para indicar onde estão as coisas em uma imagem. Uma box é uma caixa que delimita a área do objeto. Quando a imagem tem uma única ocorrência, o modelo devolve uma caixa; quando há várias ocorrências, devolve uma caixa para cada uma.

Exemplo: Imagine uma imagem com várias ocorrências do mesmo objeto. A saída permite identificar cada área separadamente. Para quem vai conferir, a caixa mostra onde o modelo fez a localização, em vez de exigir que a resposta seja interpretada apenas como um nome de objeto.

Fonte: <https://www.liquid.ai/blog/d1-2>

## Estimar um número com uma faixa

A tarefa Estimate a number (number with a range) devolve uma estimativa numérica acompanhada de uma faixa. A faixa é o intervalo associado à estimativa e ajuda a expressar a incerteza ao redor do número apresentado.

Exemplo: Imagine uma situação em que a entrada permite chegar a uma aproximação, mas não a um valor exato. A resposta reúne o número estimado e o intervalo que o acompanha. Quem utiliza o resultado pode considerar essa amplitude antes de tratar a estimativa como um dado fechado.

Fonte: <https://www.liquid.ai/blog/d1-2>

## Escolher todas as opções que se aplicam

A tarefa choice seleciona todas as opções aplicáveis. Ela é útil quando uma entrada pode se encaixar em mais de uma alternativa e a aplicação precisa receber o conjunto de escolhas, e não apenas uma opção isolada.

Exemplo: Imagine uma lista de opções e um texto que relaciona mais de uma delas. A tarefa choice devolve as opções aplicáveis. O resultado pode alimentar uma classificação múltipla ou uma etapa seguinte do fluxo, mantendo explícitas todas as alternativas atendidas.

Fonte: <https://www.liquid.ai/blog/d1-2>

## Os números

Os números do anúncio têm recortes diferentes. A pontuação do índice pertence ao d1.2-ultra e ao Artificial Analysis Decision Index v2.1. Os preços pertencem a cada modelo e são cobrados por milhão de tokens de entrada. A comparação entre qualidade e custo é a avaliação divulgada pela Liquid AI.

A pontuação de 75 pontos não é uma porcentagem de acerto em todas as tarefas. Ela situa o modelo no índice citado. Da mesma forma, o preço por milhão de tokens é uma tarifa unitária, e não o custo total de uma aplicação.

- 16 de novembro de 2026: data em que a Liquid AI anunciou os modelos d1.2 e d1.2-ultra.
- 75 pontos: pontuação do d1.2-ultra no Artificial Analysis Decision Index v2.1, onde a empresa o apresenta em primeiro lugar entre modelos de decisão.
- US$ 0,02 por milhão de tokens de entrada: preço anunciado para d1.2.
- US$ 0,042 por milhão de tokens de entrada: preço anunciado para d1.2-ultra.
- Menos da metade do preço: recorte da comparação de d1.2 com d1.2-ultra; a Liquid AI atribui a d1.2 a melhor relação entre qualidade e custo nessa comparação.

Fonte: <https://www.liquid.ai/blog/d1-2>

## Custo: a cobrança acontece pela entrada

Token é uma unidade de processamento do texto. Nesse anúncio, a cobrança considera os tokens enviados na entrada. A empresa informa que não há cobrança por tokens de saída. Portanto, o dado a acompanhar para estimar a cobrança é o volume de entrada enviado à API.

A Liquid AI informa que os preços de d1.2 e d1.2-ultra são os mesmos de d1.1 e d1-ultra. Quem já usava as versões anteriores encontra os valores mantidos nas novas opções, com a diferença representada pelas tarefas e capacidades anunciadas.

Fonte: <https://www.liquid.ai/blog/d1-2>

## Onde e como testar

O acesso anunciado acontece pela Liquid API. Para criar uma chave, abra o console da Liquid AI e vá em Dashboard > API Keys. Depois, chame o modelo pelo nome, usando d1.2 ou d1.2-ultra na sua aplicação.

O anúncio colocou OpenRouter e Vercel como próximos canais de acesso. A Liquid AI também informou que pretende abrir os pesos em algum momento. O acesso descrito para o lançamento é pela API da própria empresa; os demais canais e a abertura dos pesos aparecem como planos futuros.

Fonte: <https://console.liquid.ai/>

## O que muda para você

Exemplo: Uma equipe recebe faturas e pergunta ao modelo quanto há a pagar. A resposta reúne o valor lido e os caracteres que comprovam essa leitura. Com um limite de confiança definido, as respostas acima do limite podem seguir automaticamente, enquanto as abaixo dele vão para uma pessoa.

Para quem decide, a pergunta prática é qual limite colocar antes de a revisão humana começar. A calibração torna esse limite utilizável porque dá significado à confiança declarada. A escolha do limite passa a ser a regra que determina quais casos o fluxo resolve sozinho e quais precisam de conferência.

Fonte: <https://www.liquid.ai/blog/d1-2>

## O que fazer hoje

O caminho começa no console da Liquid AI e termina com uma regra de revisão aplicada ao seu fluxo.

1. No console da Liquid AI, abra Dashboard > API Keys e crie uma chave. O resultado é uma credencial para usar a Liquid API.
2. Na aplicação que chama a API, escolha d1.2 ou d1.2-ultra e informe o nome exato do modelo. O resultado é a chamada direcionada à variante escolhida.
3. Envie uma fatura e pergunte quanto há a pagar. O resultado esperado é o valor lido acompanhado dos caracteres que sustentam a resposta.
4. No fluxo de decisão, defina o limite de confiança para seguir automaticamente. O resultado é um critério explícito para a aplicação.
5. Encaminhe à revisão humana as tarefas abaixo desse limite. O resultado é que os casos de pouca confiança chegam a uma pessoa.
6. Na conferência, compare a resposta com os caracteres, trechos, caixas, faixas ou opções devolvidos, conforme a tarefa. O resultado é uma verificação apoiada na saída do modelo.

Fonte: <https://console.liquid.ai/>

## O que conferir

Confiança, índice e preço medem coisas diferentes. Mantenha o recorte de cada um antes de usar o modelo em uma decisão.

- Uma confiança de 80% descreve uma frequência ao longo de casos semelhantes. Ela não garante o acerto de uma resposta específica.
- O limite de confiança define onde a pessoa entra. Acima dele, o fluxo segue sozinho; abaixo dele, a tarefa passa por revisão humana.
- Os 75 pontos pertencem ao d1.2-ultra no Artificial Analysis Decision Index v2.1. O resultado não deve ser lido como taxa de acerto geral do modelo.
- Os preços anunciados são por milhão de tokens de entrada. A cobrança não inclui tokens de saída, e o volume de entrada enviado à API é o dado que pesa nessa conta.
- Use a evidência devolvida para conferir o resultado. Caracteres lidos, trechos encontrados, caixas desenhadas, faixas e opções selecionadas ajudam a verificar a resposta.
- OpenRouter e Vercel foram anunciados como próximos canais. A abertura dos pesos foi apresentada como plano futuro da Liquid AI, enquanto o acesso do lançamento acontece pela Liquid API.

Fonte: <https://www.liquid.ai/blog/d1-2>

## Glossário

- API: interface que permite a uma aplicação enviar solicitações e receber respostas de um serviço.
- Token: unidade em que o texto é dividido para processamento e cobrança.
- Tokens de entrada: unidades enviadas ao modelo; são a base da cobrança anunciada.
- Tokens de saída: unidades geradas na resposta; o anúncio informa que não há cobrança por elas.
- Calibração: ajuste que faz a probabilidade declarada pelo modelo corresponder à frequência real de acertos.
- Limite de confiança ou threshold: valor que separa o fluxo automático da revisão humana.
- Modelo de decisão: modelo usado para produzir resultados que alimentam uma escolha ou uma ação.
- Omnimodal: que processa mais de uma modalidade; aqui, texto, imagem e áudio.
- Span: trecho localizado dentro de um texto.
- Box: caixa que delimita a área de um objeto em uma imagem.
- Faixa de estimativa: intervalo apresentado junto de um número estimado.
- Choice: tarefa de selecionar todas as opções que se aplicam.
- Pesos: parâmetros internos de um modelo, cuja abertura permite seu acesso fora da API.
- Artificial Analysis Decision Index v2.1: índice de decisão citado no anúncio, no qual d1.2-ultra aparece com 75 pontos.
- Revisão humana: conferência feita por uma pessoa antes de a decisão seguir.

Fonte: <https://www.liquid.ai/blog/d1-2>

## Para onde ir depois

Comece pela tarefa que já tem um exemplo concreto e avance para a regra de revisão.

- Pratique com uma fatura: peça o valor a pagar e observe os caracteres devolvidos junto da resposta.
- Crie sua chave em Dashboard > API Keys no console da Liquid AI e teste d1.2 ou d1.2-ultra pela Liquid API.
- Depois de observar as respostas, defina um limite de confiança e pratique o caminho que envia os casos abaixo desse limite para revisão humana.
- Use o anúncio oficial da Liquid AI para acompanhar as novidades sobre OpenRouter, Vercel e a abertura dos pesos.

Fonte: <https://www.liquid.ai/blog/d1-2>
