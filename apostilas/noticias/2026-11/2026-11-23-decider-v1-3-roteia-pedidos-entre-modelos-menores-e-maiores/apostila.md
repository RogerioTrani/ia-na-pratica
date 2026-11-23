# Decider v1.3 roteia pedidos entre modelos menores e maiores

_2026-11-23 · noticia_

A Perplexity lançou o Decider v1.3 e o Decider Flash v1.3, modelos de decisão que funcionam como classificadores gerais guiados por perguntas. Você envia um texto e perguntas com respostas possíveis, e recebe a probabilidade de cada resposta em uma única passada, sem geração token a token. A versão 1.3 acrescenta o locate, que extrai trechos do texto com as posições de início e fim. Os pesos têm licença Apache e estão no Hugging Face, no OpenRouter e na Perplexity Decisions API.

## O que é um modelo de decisão

Um modelo de decisão é um classificador geral. Você entrega uma entrada e um conjunto de perguntas, cada uma com suas respostas possíveis. Para cada pergunta, ele devolve uma distribuição de probabilidade sobre as respostas.

Os três tipos de pergunta aceitos são sim/não (decisões binárias), múltipla escolha (rótulos personalizados) e nota (níveis ordenados). As probabilidades servem para classificar, rotear, ordenar e avaliar entradas.

## Como ele responde várias perguntas de uma vez

Um pedido tem um contexto compartilhado (o estado) e uma ou mais perguntas. Um mesmo pedido pode, por exemplo, checar se um resumo representa fielmente um documento e se ele se destina a especialistas ou ao público geral.

O modelo lê todas as perguntas sobre a mesma entrada em uma única passada. O cálculo do texto é compartilhado entre elas, e a resposta não é escrita token a token.

- Cada pergunta traz as opções de resposta, identificadas por rótulos como A, B ou C.
- Na versão 1.3, cada pergunta enxerga o estado e os próprios tokens, o que deixa as respostas mais estáveis quando você muda as outras perguntas do pedido.

## Tarefas que ele assume

Várias dessas tarefas iam para LLMs generativos, embora não exijam texto livre como resposta.

- Julgar saídas: fidelidade, qualidade e segurança.
- Rotear pedidos entre modelos menores e maiores, conforme a dificuldade.
- Moderar conteúdo e detectar phishing e prompt injection em saídas de ferramentas.
- Filtrar e etiquetar grandes coleções de conteúdo.
- Reordenar resultados de busca por relevância.

## Onde ele se encaixa

O Decider fica entre os LLMs e os classificadores específicos. Um classificador específico faz uma tarefa só. O Decider aprendeu a partir de tarefas variadas em um formato único de perguntas e respostas, e por isso aceita tarefas novas por instrução em linguagem natural no próprio pedido, sem treinar um classificador para cada uma.

## Novidade da v1.3: locate

O locate extrai texto da entrada em vez de escolher entre opções prontas. Serve para reconhecimento de entidades nomeadas, identificação de dados pessoais e perguntas com resposta extrativa.

Você descreve o que procurar com um rótulo curto, como "location", ou com uma instrução, como "Extract the city name where the job is located." O modelo devolve o texto exato encontrado, com as posições de início e fim em caracteres. Se não achar nada, devolve uma lista vazia.

Um único pedido pode combinar locate, classificação e nota sobre a mesma entrada. Exemplo: perguntar se uma vaga exige experiência sênior e extrair as habilidades pedidas.

## Duas versões, licença Apache

O Decider v1.3 é o modelo maior. O Decider Flash v1.3 é menor e foi destilado do primeiro. As duas versões têm licença Apache.

- Coleção Decider v1.3 no Hugging Face: https://huggingface.co/collections/perplexity-ai/decider-v13
- Decider v1.3 (Hugging Face): https://huggingface.co/perplexity-ai/pplx-decider-v1.3
- Decider Flash v1.3 (Hugging Face): https://huggingface.co/perplexity-ai/pplx-decider-flash-v1.3
- Decider v1.3 no OpenRouter: https://openrouter.ai/perplexity/pplx-decider-v1.3:free
- Decider Flash v1.3 no OpenRouter: https://openrouter.ai/perplexity/pplx-decider-flash-v1.3:free
- Perplexity Decisions API (documentação): https://docs.perplexity.ai/docs/decisions/quickstart

Fonte: <https://huggingface.co/collections/perplexity-ai/decider-v13>

## Como testar no seu pipeline

Procure no pipeline os pontos em que um LLM só classifica, julga ou filtra. Esses são os candidatos.

- Liste as decisões que o LLM toma hoje e reescreva cada uma como pergunta com respostas possíveis (sim/não, múltipla escolha ou nota).
- Agrupe as perguntas que usam a mesma entrada em um só pedido.
- Rode o modelo pela Decisions API ou pelo OpenRouter e use as probabilidades devolvidas para decidir, por exemplo, qual modelo recebe o pedido.
- Para extrair nomes ou dados pessoais, use perguntas do tipo locate.

Fonte: <https://docs.perplexity.ai/docs/decisions/quickstart>

## Além do vídeo

- O Decider foi inspirado no Jev, o System One Model da TypeSafe AI.
- As versões anteriores eram v1, v1.1, v1.2 e Flash v1.2.
- A v1.3 usa atenção bidirecional e dados de treino mais bem selecionados, com ganhos em tarefas de texto e de visão.
- O modelo Flash é treinado para reproduzir a distribuição de saída do modelo maior, e a Perplexity diz que isso generaliza melhor para dados fora do treino do que o treino direto com rótulos.
- Os adaptadores do locate ficam sem fusão com o modelo base e só são ativados em pedidos de locate, porque a fusão ainda causa perda nos pedidos de decisão.
