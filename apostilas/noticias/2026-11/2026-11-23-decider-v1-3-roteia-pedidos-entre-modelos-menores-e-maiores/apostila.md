# Decider v1.3 roteia pedidos entre modelos menores e maiores

_2026-11-23 · noticia_

A Perplexity lançou o Decider v1.3 e o Decider Flash v1.3, modelos de decisão que recebem um texto e uma lista de perguntas e devolvem a probabilidade de cada resposta em uma única passada, sem gerar texto token a token. A versão 1.3 traz a extração de trechos (locate), que devolve o texto exato com posições de início e fim, útil para nomes, dados pessoais e respostas extrativas. Você vai entender o que é um modelo de decisão, como ele se situa entre LLMs generativos e classificadores específicos, como treiná-lo e avaliá-lo, e como integrá-lo ao seu pipeline com código, limites e cuidados.

## O fato

A Perplexity lançou o Decider v1.3 e o Decider Flash v1.3, sucessores dos modelos de decisão anteriores da empresa (v1, v1.1, v1.2 e Flash v1.2). O anúncio foi publicado em 12 de novembro de 2026 no blog da Perplexity.

O Decider Flash v1.3 é uma versão menor, destilada do Decider v1.3. Ambos estão disponíveis no Hugging Face sob licença Apache, via OpenRouter e na Perplexity Decisions API.

Os pesos estão na coleção Decider v1.3 do Hugging Face, com repositórios individuais para cada variante, além de entradas no OpenRouter e documentação da API de Decisões.

Fonte: <https://www.perplexity.ai/hub/blog/perplexity-decider>

## Por que isso importa

Muitas tarefas de pipeline não precisam de texto livre. Julgar a qualidade de uma saída, encaminhar pedidos fáceis para modelos menores e difíceis para maiores, moderar conteúdo, detectar prompt injection e reordenar resultados de busca são decisões estruturadas, mas costumam ser feitas por LLMs generativos que escrevem a resposta token a token.

Um modelo de decisão devolve probabilidades para várias perguntas sobre a mesma entrada em uma única passada, compartilhando o cálculo entre as perguntas e evitando a geração token a token. Isso reduz custo e latência e dá um número ajustável por limiar, em vez de um texto que precisa ser interpretado.

A diferença prática é que você pode calibrar thresholds em um conjunto de desenvolvimento rotulado e trocar de modelo (v1.3 para casos nuançados, Flash para alto volume) sem mudar a lógica do pipeline.

Fonte: <https://www.perplexity.ai/hub/blog/perplexity-decider>

## O que é um modelo de decisão

Um modelo de decisão é um classificador general-purpose. Você entrega uma entrada (o estado) e um conjunto de perguntas, cada uma com suas respostas possíveis. Para cada pergunta, ele devolve uma distribuição de probabilidade sobre as respostas.

A inspiração declarada pela Perplexity é o Jev, modelo da TypeSafe AI conhecido como System One Model. A proposta é cobrir classificação e pontuação com um único modelo reutilizável.

Diferente de um classificador específico, que faz uma tarefa só e exige treino para cada nova tarefa, o Decider aceita tarefas novas por instrução em linguagem natural no próprio pedido, flexibilidade aprendida ao treinar em diversas tarefas no formato compartilhado de pergunta e resposta.

Fonte: <https://www.perplexity.ai/hub/blog/perplexity-decider>

## Como funciona em uma única passada

Um pedido consiste em um estado compartilhado (o contexto) e várias perguntas. O estado é reutilizado por todas as perguntas. Por exemplo, dado um documento e seu resumo, um único pedido pode perguntar se o resumo representa fielmente o documento e se é voltado a especialista ou público geral.

Depois do estado, cada bloco de pergunta contém a pergunta e suas respostas possíveis, cada uma com um token de rótulo predefinido como A, B ou C. Um token especial, o marcador de leitura, indica onde a predição é lida. Nessa posição, uma camada linear aprendida (a cabeça de decisão) transforma o estado oculto em pontuações para as opções, convertidas em probabilidades.

A camada de saída é inicializada a partir do modelo base, que normalmente pontua o próximo token em todo o vocabulário, mantendo apenas as linhas correspondentes aos tokens de opção. Essa camada podada é treinada para transformar o estado oculto do marcador em pontuações de resposta.

Como todas as perguntas sobre a mesma entrada saem de uma única passada, o cálculo do texto é compartilhado entre elas, sem escrever resposta token a token. O resultado é uma resposta por pergunta, com probabilidades que a aplicação usa para classificar, rotear, ranquear e avaliar entradas.

Fonte: <https://www.perplexity.ai/hub/blog/perplexity-decider>

## Os três tipos de pergunta

O Decider cobre todas as perguntas de classificação porque podem ser formuladas como múltipla escolha. São três tipos de pergunta.

- Yes/No: decisão binária. Retorna P(true).
- Multiple choice: rótulos multi-classe personalizados, de 1 a 255 opções. Retorna a escolha e probabilidades por opção.
- Score: níveis ordenados, de 2 a 255 descrições de nível do mais baixo ao mais alto. Retorna o índice de nível esperado, probabilidades, legenda e confiança.

Fonte: <https://huggingface.co/perplexity-ai/pplx-decider-v1.3>

## Onde ele se situa

O Decider fica entre LLMs generativos e classificadores específicos. Um classificador específico faz uma tarefa só. Um LLM generativo escreve texto livre, o que é caro quando a tarefa é só decidir.

O Decider aceita tarefas novas por instrução em linguagem natural no próprio pedido, sem treinar um classificador para cada uma, e retorna probabilidades para múltiplas perguntas sobre a mesma entrada em uma única passada.

Tarefas típicas: julgar saídas (fidelidade, qualidade, segurança); rotear pedidos para modelos menores ou maiores conforme a dificuldade; moderar e proteger (conteúdo nocivo, phishing, prompt injection em saídas de ferramentas); filtrar e etiquetar grandes coleções; recuperar e reordenar resultados por relevância.

Fonte: <https://www.perplexity.ai/hub/blog/perplexity-decider>

## A novidade da v1.3: extração de trechos (locate)

A versão 1.3 introduz o locate, que extrai trechos do texto em vez de selecionar entre opções predefinidas. Serve para reconhecimento de entidades nomeadas, identificação de dados pessoais e perguntas extrativas.

Uma pergunta locate descreve o que encontrar, com rótulo curto (como "location") ou instrução (como "Extraia o nome da cidade onde a vaga está"). O modelo retorna o texto exato do estado, com posições de início e fim em caracteres. Se não encontrar correspondência, retorna lista vazia.

Por causa do estado compartilhado, um único pedido pode combinar perguntas locate, de classificação e de pontuação sobre a mesma entrada. Exemplo: perguntar se uma vaga exige experiência sênior e, na mesma passada, extrair as habilidades exigidas.

Fonte: <https://www.perplexity.ai/hub/blog/perplexity-decider>

## Bidirectional attention e padrões de atenção

Os modelos partem de backbones generativos fortes, cuja atenção causal permite que cada token atenda apenas a si e aos tokens anteriores. Estudos de ablação mostraram que tornar as camadas de atenção completa do backbone bidirecionais melhora o desempenho, então a Perplexity adotou esse desenho para que cada token incorpore contexto de toda a entrada.

A atenção bidirecional traz uma escolha de projeto: como estado e perguntas interagem. Três padrões foram considerados.

No padrão "tudo vê tudo" (v1.2), estado e todas as perguntas são processados juntos com atenção bidirecional completa: o cálculo sobre o estado é compartilhado, mas a resposta a uma pergunta pode mudar conforme as outras perguntadas. No padrão "perguntas isoladas" (v1.3), o estado atende a todas as perguntas, enquanto cada pergunta atende apenas ao estado e a seus próprios tokens: as perguntas ainda podem influenciar umas às outras indiretamente pelo estado compartilhado, mas os resultados são mais estáveis. No padrão "totalmente cacheável", o estado só atende a si mesmo e cada pergunta atende ao estado e a si mesma: o estado fica independente da pergunta e reutilizável entre pedidos para aproveitar cache de prompt, mas não é o padrão porque deixar o estado ver as perguntas importa muito em várias tarefas.

A Perplexity escolheu perguntas isoladas pelo desempenho forte e estabilidade. A versão totalmente cacheável pode ser ativada com um pequeno fine-tuning.

Fonte: <https://www.perplexity.ai/hub/blog/perplexity-decider>

## Treinamento em três estágios

O treinamento ocorre em três estágios para ambos os tamanhos. Primeiro treina-se o modelo maior, baseado no Qwen3.8-27B, com entropia cruzada em grandes conjuntos de dados; depois destila-se para o modelo menor, Qwen3.5-4B.

O primeiro estágio é o treinamento generalista, com fine-tuning completo em corpora de larga escala. Nesse estágio só se aceitam dados que ajudam o modelo de forma geral e não são específicos de nenhum benchmark; por isso se excluem splits de treino de benchmarks. Para mitigar contaminação treino-teste, removem-se amostras de treino que possam se sobrepor a qualquer avaliação usada, e realizam-se auditorias e remoções de viés.

O segundo estágio é mais fino, com LoRA, voltado a domínios e tarefas específicas. Dados são adicionados nesse estágio em vez do primeiro quando se observam ganhos estreitos ou regressões em outras tarefas. LoRA evita afastar demais o modelo do generalista. Um peso é usado ao fundir o LoRA de volta ao modelo base, para controlar o afastamento e favorecer métricas em dados não vistos.

O terceiro estágio é específico de visão, tratado como outra especialização fina com adapter LoRA fundido com peso. Como capacidades de visão podem custar desempenho em texto, e o uso é muito maior em texto, as métricas de texto são priorizadas.

Para ambos os estágios de texto, usam-se as médias dos pesos de três execuções com sementes aleatórias diferentes, o que melhora desempenho e robustez do modelo agregado.

Fonte: <https://www.perplexity.ai/hub/blog/perplexity-decider>

## Destilação do modelo maior para o menor

Uma vez obtido o modelo grande final, aplica-se o mesmo procedimento de três estágios ao modelo menor. O modelo grande atua como professor: sua distribuição de saída prevista substitui os rótulos de ouro, e o modelo menor é treinado para minimizar a divergência KL entre suas predições e as do professor.

O objetivo de destilação supera a entropia cruzada nos mesmos dados de treino. Embora a entropia cruzada seja melhor em benchmarks com dados de treino dedicados, generaliza menos bem para dados não vistos. A hipótese é que a destilação transfere melhor a distribuição de saída do professor, incluindo a confiança sobre alternativas não-ouro, enquanto a entropia cruzada incentiva overfitting à distribuição de treino específica do benchmark.

Fonte: <https://www.perplexity.ai/hub/blog/perplexity-decider>

## Como a extração locate é treinada

O locate ensina uma tarefa estruturalmente diferente, e a Perplexity quer adicioná-la sem perder o que o modelo já faz bem. Para isso introduz-se um estágio adicional: adiciona-se um novo token especial, uma cabeça de span e um adapter LoRA ao Decider.

A embedding do novo token é inicializada a partir do marcador aprendido nos estágios anteriores. Treina-se apenas essa embedding, a cabeça de span e os adapters LoRA, mantendo congelados os pesos originais do backbone e da cabeça de decisão. Cada campo solicitado ganha seu próprio token de locate.

A cabeça de span usa a representação do token de locate junto com as representações dos tokens do estado para pontuar onde os spans correspondentes começam e terminam, e quais pares início-fim pertencem juntos. Também usa a representação do token de locate para prever limiares específicos por campo para essas pontuações. Os spans selecionados são retornados como posições de caracteres no texto original.

A cabeça é treinada com uma perda InfoNCE adaptada que empurra todo span de ouro acima do limiar e o limiar acima de todo outro span. O primeiro termo empurra as pontuações dos spans corretos acima do limiar e dos spans errados; o segundo empurra o limiar acima das pontuações dos spans errados. Campos sem resposta recebem apenas o segundo termo, o que ensina o modelo a retornar lista vazia.

O treino cobre tarefas de extração de span, incluindo reconhecimento de entidades nomeadas, detecção de dados pessoais e perguntas extrativas. As descrições de campo variam de rótulos curtos a instruções detalhadas, para que o modelo aprenda a seguir o pedido em vez de memorizar um conjunto fixo de rótulos.

Mesclar os adapters de locate no backbone causa alguma regressão em pedidos de decisão. Para limitar isso, a Perplexity investiga mais dados de replay dos estágios anteriores e objetivos auxiliares que mantenham as saídas do modelo em pedidos de decisão próximas às do modelo original. Como a fusão ainda não é sem perdas, os adapters são mantidos não fundidos e ativados apenas para pedidos locate.

Fonte: <https://www.perplexity.ai/hub/blog/perplexity-decider>

## Avaliação em benchmarks externos

O Decider v1.3 e o Decider Flash v1.3 são avaliados em benchmarks externos do Hugging Face Decision Index, do ClaimBench da Vals AI e do Artificial Analysis Decision Index. Todos os resultados são zero-shot, sem fine-tuning específico por tarefa.

Para complementar esses leaderboards, que podem ser jogados por submissões repetidas e ajuste iterativo, a Perplexity avalia em uma suíte interna que combina tarefas de produção privadas com avaliações não vistas extraídas de conjuntos de dados públicos não-benchmark. Internamente, a suíte tem mais de 200 tarefas em domínios e tipos variados: classificação, pontuação, reordenação e extração de entidades.

- Classificação de consultas: 63 tarefas, 91,6% de acurácia média para o v1.3, 6,54 pontos percentuais acima dos classificadores de produção. O Flash também supera a linha de base, e o v1.3 supera o Jev 1.14.
- Classificação por domínio: 7 domínios (verificação de claims 6 tarefas, saúde 7, cibersegurança 8, programação 16, governo 7, direito 9, finanças 9). O v1.3 lidera em todos, superando o Jev 1.14 em até 12,9 pontos em finanças e 9,3 em direito. O Flash fica atrás do Jev em finanças, programação e direito, e é similar nos demais.
- Recuperação e reordenação: 72 tarefas, nDCG@10 de 83,99 para o v1.3, 1,81 ponto acima do Qwen3-Reranker-8B e 2,24 acima do Jev 1.14. No BEIR, ambos superam o Qwen3-Reranker-8B em 8,78 e 7,05 nDCG@10; contra o Jev, o v1.3 é 1,33 ponto maior e o Flash 0,4 menor.
- Classificação multilíngue: 19 tarefas em 8 línguas (alemão, espanhol, francês, italiano, russo, japonês, coreano, chinês), 46.484 exemplos. Acurácia média de 88,16% para o v1.3 e 86,50% para o Flash, contra 85,41% do Jev 1.14. O v1.3 supera o Jev em todas as 8 línguas; o Flash em 6.
- NER, PII e QA extrativa: 17 tarefas fora do domínio. F1 de span exato para NER e PII, F1 em nível de caractere para QA extrativa, acurácia de campo para extração estruturada. O v1.3 atinge média de 69,0 e o Flash 63,6, contra 43,3 do Liquid d1, 41,5 do Clairic e 33,6 do GLiNER large v2.5. Ambos lideram em todas as categorias.
- Classificação de imagens: 5 tarefas (documentos como faturas, cartas e currículos, além de satélite, textura, raça de pet e contagem de animais). O v1.3 atinge 76,99% de acurácia média, 1,47 ponto acima do Jev 1.14. O Flash atinge 72,77%.

Fonte: <https://www.perplexity.ai/hub/blog/perplexity-decider>

## Resultados em tarefas internas

A Perplexity amostrou um milhão de pedidos deduplicados e com dados pessoais mascarados, submetidos à Perplexity Decisions API nos primeiros 18 dias de disponibilidade. Como cada pedido pode conter várias perguntas sobre o mesmo estado, a amostra compreende 2.318.887 perguntas individuais. Todos os pedidos foram incluídos com permissão explícita do usuário para pesquisa.

Como pedidos de produção não vêm com rótulos de verdade, usam-se juízes LLM de fronteira para gerar respostas de referência e medir a concordância de cada modelo com eles. Os pedidos são agrupados em 10 categorias de tarefa: extração de informação, classificação de domínio, análise de sentimento, intenção e roteamento, ranqueamento de relevância, moderação de conteúdo, revisão de qualidade e conformidade, matching de entidades, análise de negócio e "Outros".

A mistura de tarefas é desigual: extração de informação responde por 425.402 perguntas, classificação de domínio por 409.564 e análise de sentimento por 344.158. Juntas, essas três categorias representam 50,8% das perguntas amostradas.

O v1.3 alcança a maior concordância com os juízes, 93,98%, contra 93,68% do v1.2 e 93,35% do Jev 1.14. O v1.3 e o Jev 1.14 estão quase empatados em classificação de domínio e análise de sentimento, com diferenças de 0,34 e 0,07 ponto percentual. O Jev lidera em ranqueamento de relevância por 0,69 ponto, enquanto o v1.3 lidera em extração de informação (a tarefa mais comum da amostra) por 0,93 ponto e em intenção e roteamento por 1,21 ponto.

Fonte: <https://www.perplexity.ai/hub/blog/perplexity-decider>

## Robustez a mudanças de rótulo e serving

A sensibilidade a rótulos foi avaliada em 372 perguntas de múltipla escolha, gerando 4.788 pedidos por modelo. Reordenaram-se opções, reatribuíram-se rótulos aos textos de resposta e renomearam-se rótulos preservando o significado de cada pergunta, verificando se a resposta semântica do modelo mudava. Taxas de inversão menores indicam maior estabilidade.

O v1.3 mudou sua resposta em apenas 0,27% das perguntas sob cada transformação, contra 2,69% a 4,84% do Jev 1.14. Repetindo entradas idênticas para medir variabilidade de serving, o v1.3 não mudou, enquanto o Jev 1.14 mudou em 1,88% das perguntas.

Fonte: <https://www.perplexity.ai/hub/blog/perplexity-decider>

## Usos internos na Perplexity

Regras de segurança autoaperfeiçoadas: a atividade dos agentes é registrada e checagens baseadas em regras identificam comportamento problemático em tempo real, com latência desprezível. Offline, o Decider examina amostras dos logs. Quando nenhum comportamento problemático foi sinalizado, o Decider verifica se as regras perderam algo; quando um alarme foi disparado, verifica se foi falso positivo. Registros em que o conjunto de regras falha nos dois casos vão para triagem por um agente e uma correção é proposta, a ser aprovada pela equipe de segurança. Em um dia, o Decider leu 1 bilhão de tokens em 7.000 sessões de agente e identificou falhas que levaram a 14 correções de regras, 6 aprovadas e publicadas em dois dias. Reproduzido em uma semana de logs, as correções cortaram o volume da regra mais ocupada em 52%, e as regras ampliadas capturaram cerca de 40% mais ações legítimas para investigar.

Monitoramento de rollouts de RL: ao pós-treinar modelos com aprendizado por reforço, métricas agregadas como recompensa terminal não explicam por que um rollout individual teve sucesso ou falhou. Pode perder recompensa injustamente porque um serviço de ferramenta ou o sandbox falhou, ou receber recompensa indevida se o avaliador ignora uma afirmação não suportada, como um valor inventado que nenhuma ferramenta retornou. O Decider monitora rollouts para esses casos: código identifica partes que merecem inspeção mais próxima (chamada de ferramenta falha e raciocínio ao redor, código que rodou sem erros, resposta final), e o Decider responde perguntas de múltipla escolha sobre cada parte, como o que falhou em um passo (serviço de ferramenta, site externo, sandbox, harness ou código do próprio agente) e se o agente interpretou o resultado corretamente. Todas as perguntas sobre uma parte são agrupadas em um único pedido, e armazenam-se as probabilidades em vez de um veredito, para ajustar limiares depois sem consultar o Decider de novo. O monitor apenas observa e diagnostica: nunca muda uma recompensa nem para uma execução.

Filtragem de qualidade de página: ao rastrear páginas web para indexar e servir, muitas são de baixa qualidade demais para ser úteis, incluindo paredes anti-bot, CAPTCHAs e páginas de erro, além de páginas corretamente carregadas que não contêm informação útil, como spam, enchimento de SEO ou páginas só de navegação. Com o Decider, julga-se a qualidade das páginas enquanto são rastreadas. Na mesma passada, realizam-se outras tarefas de classificação, como identificar o domínio e a audiência pretendida do conteúdo e se contém material nocivo, ilegal ou informação pessoal identificável. Comparado a um juiz LLM, o Decider é consideravelmente mais rápido e mais barato.

Fonte: <https://www.perplexity.ai/hub/blog/perplexity-decider>

## Outros usos sugeridos

Além dos usos internos, o Decider se encaixa em fluxos como os seguintes.

QA visual: como lê imagens, funciona como verificador visual, revisando mudanças de estilo em páginas ou apps e identificando falhas. Pode revisar capturas de tela em busca de texto cortado, elementos sobrepostos e layouts quebrados antes de uma mudança ir ao ar, ou sinalizar gráficos cujo desenho pode enganar o leitor ou quebrar um guia de marca.

Navegação em navegador: agentes podem usar o Decider para decisões pequenas dentro de tarefas maiores. Um agente de navegador pode enviar uma captura de tela a cada passo e receber informação detalhada sobre o estado da página e o resultado esperado de cada ação possível.

Planejamento de tarefas de pesquisa: perguntas dos usuários variam muito em complexidade, assim como a profundidade de busca necessária para responder. O Decider pode estimar isso antes de a busca começar, permitindo gastar menos recursos em perguntas simples.

Fonte: <https://www.perplexity.ai/hub/blog/perplexity-decider>

## Os números

Cada número abaixo vem da Perplexity e deve ser lido com seu contexto: em qual teste, comparado a quê, para quem vale.

- 91,6%: acurácia média do v1.3 em 63 tarefas de classificação de consultas, 6,54 pontos acima dos classificadores de produção.
- 12,9 e 9,3 pontos percentuais: vantagem do v1.3 sobre o Jev 1.14 em finanças e direito, nos domínios avaliados.
- 83,99: nDCG@10 médio do v1.3 em 72 tarefas de recuperação, 1,81 ponto acima do Qwen3-Reranker-8B.
- 88,16% e 86,50%: acurácia média do v1.3 e do Flash em classificação multilíngue, contra 85,41% do Jev 1.14.
- 69,0 e 63,6: pontuação média do v1.3 e do Flash em NER, PII e QA extrativa, contra 43,3 (Liquid d1), 41,5 (Clairic) e 33,6 (GLiNER large v2.5).
- 76,99% e 72,77%: acurácia média do v1.3 e do Flash em 5 tarefas de classificação de imagens.
- 93,98%, 93,68% e 93,35%: concordância com juízes LLM em um milhão de pedidos de produção para v1.3, v1.2 e Jev 1.14.
- 425.402, 409.564 e 344.158: perguntas nas categorias extração de informação, classificação de domínio e análise de sentimento; juntas, 50,8% da amostra.
- 2.318.887: perguntas individuais na amostra de um milhão de pedidos.
- 0,27%: taxa de inversão do v1.3 sob transformações de rótulo, contra 2,69% a 4,84% do Jev 1.14.
- 1,88%: taxa de mudança do Jev 1.14 em entradas idênticas repetidas; o v1.3 não mudou.
- 1 bilhão de tokens lidos em um dia em 7.000 sessões de agente; 14 correções de regras propostas, 6 aprovadas em dois dias.
- 52% de corte no volume da regra mais ocupada e cerca de 40% mais ações legítimas capturadas após as correções.
- 26B e 5B: parâmetros do v1.3 e do Flash.
- Cerca de 49 GiB e 8,5 GiB: memória para pesos BF16 do v1.3 e do Flash, mais memória de trabalho.
- 1.638.400 pixels (1,6 MP): tamanho máximo de imagem; uma imagem desse tamanho usa cerca de 1.600 posições de sequência.
- 32.768 tokens: max_length padrão; treinamento usou sequências de até 30.720 tokens.
- 1 a 255 opções por pergunta (2 a 255 para score); até 128 perguntas locate por pedido.

Fonte: <https://www.perplexity.ai/hub/blog/perplexity-decider>

## O que muda para você

Se o seu pipeline usa um LLM generativo só para classificar, julgar ou filtrar, vale testar se um modelo de decisão resolve com perguntas e probabilidades. O ganho esperado é custo e latência menores, além de um número ajustável por limiar em vez de texto a ser interpretado.

Para julgamentos nuançados, rubricas detalhadas e fluxos em que erros são custosos, use o Decider v1.3. Para roteamento, rotulagem e filtragem de alto volume, onde latência e custo são a restrição principal, use o Decider Flash v1.3. Avalie ambos em exemplos representativos da sua carga de trabalho antes de escolher.

Exemplo: em vez de pedir a um LLM "classifique este ticket como billing, support ou sales e diga se é urgente", você monta um pedido com estado igual ao texto do ticket e duas perguntas (team como choice com as três opções, urgent como noul). O modelo retorna a escolha e P(true) em uma passada, e você aplica seus próprios limiares.

Fonte: <https://www.perplexity.ai/hub/blog/perplexity-decider>

## O que fazer hoje

1. confirme se sua tarefa é decisão estruturada (classificar, julgar, rotear, moderar, reordenar, extrair trechos). Se precisar de texto livre, o Decider não é a ferramenta.
2. obtenha acesso aos pesos no Hugging Face (os repositórios são privados; é preciso token com acesso) ou use o OpenRouter ou a Perplexity Decisions API.
3. instale as dependências (torch, transformers, safetensors, pillow, torchvision, huggingface-hub) e baixe o checkpoint com snapshot_download.
4. carregue o modelo com Decider.from_pretrained(checkpoint, device="cuda") e faça uma chamada decide() com um estado e uma ou mais perguntas.
5. calibre os limiares em um conjunto de desenvolvimento rotulado representativo, em vez de assumir um corte fixo. Se a aplicação depende de valores de probabilidade, calibre em amostra do seu próprio tráfego.
6. avalie o v1.3 e o Flash em exemplos representativos da sua carga e escolha conforme qualidade, latência e orçamento. Use o v1.3 para julgamentos nuançados e o Flash para alto volume.
7. se precisar de extração de trechos, use perguntas do tipo locate e trate spans vazios como "sem correspondência". Misturar locate e decisão em um mesmo pedido exige passadas separadas e adiciona latência.

Fonte: <https://huggingface.co/perplexity-ai/pplx-decider-v1.3>

## O que conferir

- Os repositórios no Hugging Face são privados: é preciso autenticar com token que tenha acesso. Sem isso, o download falha.
- Requisitos de hardware: cerca de 49 GiB de pesos BF16 mais memória de trabalho para o v1.3 e cerca de 8,5 GiB para o Flash, em GPU CUDA, com Python 3.12 ou superior.
- Probabilidades variam levemente entre composições de lote por causa de BF16. Para resultados bit-estáveis, use uma request por chamada.
- LengthError ocorre quando uma pergunta com o estado e as imagens excede o max_length (padrão 32.768 tokens). Encurte o estado ou reduza max_pixels. Entradas nunca são truncadas; valide entradas longas por conta própria.
- Out of memory: reduza batch_tokens.
- Não reutilize construtores de prompt das versões 1.1 ou 1.2: o modelo espera o formato v1.3 construído por pplx_decider.
- Locate exige estado de texto não vazio, sem imagens e no máximo 128 perguntas por pedido. Cada span tem offsets start e end (exclusivo), texto e pontuação; state[start:end] == text. Sem correspondência retorna lista vazia.
- Misturar perguntas locate e de decisão em um mesmo pedido exige passadas separadas para cada tipo, adicionando latência. Dividir o mesmo trabalho em duas chamadas decide() não remove essas passadas.
- Se uma pergunta mais o estado não couber, LengthError é levantado. fast=True com locate=False desabilita locate.
- Chamadas a decide(), logits(), reference_logits() e warmup() na mesma instância são serializadas por um lock interno, incluindo carregamento de adapter. Chamadores concorrentes são seguros por esses métodos; use instâncias separadas para inferência paralela.
- O fast path (fast=True, requer requirements-fast.txt) empacota várias sequências por passada e compila o decoder com torch.compile. O modo separate também reproduz grafos CUDA. Chame warmup() na inicialização para compilar com antecedência.
- O custo reportado para rodar um milhão de pedidos de produção é específico da carga de trabalho, com contabilização de hardware local não especificada e sem comparação de latência. Decider rodou localmente; GLM e DeepSeek usaram llm-api; Jev usou OpenRouter.
- Thresholds dependem da aplicação: frequências de rótulo e custos relativos de falsos positivos e negativos variam. Tune em conjunto de desenvolvimento rotulado representativo.

Fonte: <https://huggingface.co/perplexity-ai/pplx-decider-v1.3>

## Requisitos e instalação

O v1.3 tem 26 bilhões de parâmetros, baseado no Qwen3.8-27B; o Flash tem 5 bilhões, baseado no Qwen3.5-4B. Ambos exigem Python 3.12 ou superior e GPU CUDA com espaço para os pesos BF16 (cerca de 49 GiB para o v1.3, cerca de 8,5 GiB para o Flash) mais memória de trabalho.

Os repositórios são privados: é preciso autenticar com token do Hugging Face que tenha acesso. Baixe o repositório e instale o requirements.txt (torch, transformers, safetensors, pillow, torchvision, huggingface-hub). O código-fonte também pode ser instalado como pacote com pip install ./source.

O fast path (fast=True) requer requirements-fast.txt e empacota várias sequências por passada, compilando o decoder com torch.compile. No modo separate também reproduz grafos CUDA. No modo separate, é cerca de 1,7 a 1,9 vez mais rápido que os lotes padrão, com concordância de resposta principal de 99,6% a 99,7%. No modo isolated é 9 a 18 vezes mais rápido que o caminho isolated de referência. Chame warmup() na inicialização.

```
import sys
from pathlib import Path
from huggingface_hub import snapshot_download
checkpoint = Path(snapshot_download(
    "perplexity-ai/pplx-decider-v1.3"
))
sys.path.insert(0, str(checkpoint / "source" / "src"))
from pplx_decider import Decider
decider = Decider.from_pretrained(checkpoint, device="cuda")
```

Fonte: <https://huggingface.co/perplexity-ai/pplx-decider-v1.3>

## Como montar uma request

Um pedido tem um estado (contexto a classificar; não-strings são serializadas como JSON) e um ou mais perguntas. Imagens são opcionais e vão no campo images.

Cada pergunta tem type (choice, noul, score ou locate), instructions opcional (para locate, refina ou substitui a chave da pergunta) e criteria conforme o tipo. As opções são mostradas ao modelo na ordem dada, sob os códigos de resposta A, B, ...

Um exemplo de pedido: o estado é a mensagem de um cliente que diz receber erro 401 na integração desde a troca da chave de API. As perguntas são team (choice, com as opções billing, support e sales e uma descrição para cada uma), urgent (noul, para saber se o cliente está bloqueado agora) e frustration (score, com níveis de calm a angry). A chamada é decider.decide() com esse pedido; a escolha fica em response["answers"]["team"]["choice"] e a probabilidade de urgência em response["answers"]["urgent"]["noul"]. decide() aceita um pedido e devolve uma resposta; com uma lista de pedidos, devolve uma lista na mesma ordem.

A resposta tem a forma {"answers": {"<id>": {...}}, "usage": {"input_tokens": int, "output_tokens": 0, "sequences": int}}. Pedidos que não seguem o esquema levantam pplx_decider.RequestError antes de qualquer computação.

Imagens vão em images, são colocadas antes do texto do pedido e todas as perguntas podem vê-las. Cada imagem é redimensionada (proporção mantida) para no máximo max_pixels pixels: 1.638.400 (1,6 MP), conforme salvo em decision_config.json. Imagens menores mantêm o tamanho. Uma imagem de 1,6 MP usa cerca de 1.600 posições de sequência, então várias imagens grandes contam para o limite de comprimento.

- choice: criteria traz cada opção com uma descrição (ou nenhuma), de 1 a 255 opções; a resposta traz choice, probabilities e confidence.
- noul: criteria é opcional, com descrições para true e false; a resposta traz noul, que é P(true).
- score: criteria é uma lista de 2 a 255 descrições de nível, da mais baixa à mais alta; a resposta traz score, probabilities, legend e confidence.
- locate: não usa criteria; a chave da pergunta é o rótulo, que instructions pode substituir; a resposta traz spans com start, end, text e score.

Fonte: <https://huggingface.co/perplexity-ai/pplx-decider-v1.3>

## Modes: separate e isolated

Para perguntas de decisão, um pedido pode carregar qualquer número de perguntas sobre o mesmo estado. Por padrão (mode="separate") cada pergunta é respondida em sua própria sequência, formada pelo estado (e imagens) e aquela pergunta apenas: as perguntas não se veem, e uma resposta não muda quando você adiciona, remove ou reordena as outras. É a computação usada para medir as pontuações publicadas no cartão do modelo. Coloque tudo o que uma pergunta precisa no estado, não em outra pergunta.

Decider.from_pretrained(..., mode="isolated") em vez disso codifica o pedido inteiro como uma sequência com o layout de treino: o estado é lido uma vez e cada pergunta atende ao estado e a si mesma. É mais barato quando muitas perguntas compartilham um estado longo, mas o estado também atende às perguntas, então respostas podem mudar levemente com o conjunto de perguntas (em amostras da Perplexity, 1,5% a 2,2% das respostas principais diferem do modo separate). Use separate a menos que o custo de reler o estado importe.

Fonte: <https://huggingface.co/perplexity-ai/pplx-decider-v1.3>

## Temperature e calibração

O arquivo decision_config.json armazena a temperatura ajustada em dados de calibração reservados. O método decide aplica-a exatamente uma vez e depois normaliza um softmax sobre as opções válidas de cada pergunta. decide(..., temperature=t) sobrescreve esse valor.

Ao usar logits diretamente, divida pela temperatura salva antes do softmax e não inclua os códigos não usados. Se a aplicação depende de valores de probabilidade (e não apenas de rankings ou da resposta principal), calibre em amostra do seu próprio tráfego: uma única temperatura não pode estar certa para toda tarefa, e limiares por tarefa costumam ser melhores.

O método logits(requests) retorna os logits brutos de leitura de cada pergunta, antes da temperatura. Para ranqueamento, use a margem de logit true - false de uma pergunta noul: diferentemente das probabilidades, não satura em empates.

Fonte: <https://huggingface.co/perplexity-ai/pplx-decider-v1.3>

## Locate: limites e comportamento

Locate exige estado de texto não vazio, sem imagens e no máximo 128 perguntas por pedido. Cada span tem offsets de caractere start e end (exclusivo), seu texto e uma pontuação; vale state[start:end] == text. Sem correspondência retorna lista vazia de spans.

O adapter de locate é carregado automaticamente no primeiro pedido com esse tipo de pergunta.

Perguntas locate rodam juntas, separadamente das perguntas de decisão, e podem influenciar umas às outras pelo estado compartilhado. Pedidos que misturam locate e decisão exigem passadas separadas para cada tipo, adicionando latência em comparação com pedidos que contêm apenas um tipo. Dividir o mesmo trabalho em duas chamadas decide() não remove essas passadas.

Usam o mesmo max_length (padrão 32.768 tokens): perguntas são divididas apenas quando necessário, preservando o estado completo. Se uma única pergunta mais o estado não couber, LengthError é levantado. fast=True com locate=False desabilita locate.

As chamadas a decide(), logits(), reference_logits() e warmup() na mesma instância de Decider são serializadas por um lock interno, incluindo carregamento de adapter. Chamadores concorrentes são seguros por esses métodos; use instâncias separadas para inferência paralela.

Fonte: <https://huggingface.co/perplexity-ai/pplx-decider-v1.3>

## Formato do checkpoint e serving

Este é o layout nativo de checkpoint de decisão: o backbone mais readout.safetensors, uma cabeça de decisão BF16 [255, hidden_size]. O arquivo joint_config.json declara o protocolo do pedido (version: 4, joint-chunked-readout-v1, marcador <|fim_suffix|>, separador <|fim_middle|>).

As camadas de atenção completa são não causais sobre a sequência (o estado e a pergunta sendo respondida); as camadas de atenção linear mantêm comportamento causal. Inferência causal padrão não reproduz este checkpoint. A leitura é aplicada em cada marcador <|fim_suffix|>, uma por pergunta, e não no último token. Tokens especiais literais no conteúdo do usuário são neutralizados antes da tokenização, então texto do usuário não pode criar marcadores.

Este artefato tem uma leitura separada, não uma cabeça lm de vocabulário completo. A linha i da leitura corresponde à linha i do vocabulário em decision_config.json["token_ids"]. O arquivo release-manifest.json registra checksums dos arquivos.

Limites: 1 a 255 opções por pergunta (2 a 255 para score). Os códigos de resposta são tokens únicos e a cabeça de leitura tem 255 linhas. Comprimento: treinamento usou sequências de até 30.720 tokens. Entradas nunca são truncadas; valide entradas mais longas na sua tarefa. Perguntas por pedido: sem teto fixo; o limite de comprimento é a única restrição.

Fonte: <https://huggingface.co/perplexity-ai/pplx-decider-v1.3>

## Troubleshooting

Probabilidades diferem levemente entre composições de lote: esperado em BF16. Use uma request por chamada para resultados bit-estáveis.

LengthError: uma pergunta com o estado e as imagens excede o max_length. Encurte o estado ou reduza max_pixels.

Out of memory: reduza batch_tokens.

Respostas diferentes de prompts no estilo v1.1 ou v1.2: este modelo espera o formato v1.3 construído por pplx_decider. Não reutilize construtores de prompt anteriores.

Fonte: <https://huggingface.co/perplexity-ai/pplx-decider-v1.3>

## Glossário

- Modelo de decisão: classificador general-purpose que recebe uma entrada e perguntas com respostas possíveis e devolve a probabilidade de cada resposta.
- Estado (state): o contexto compartilhado que todas as perguntas de um pedido usam.
- Cabeça de decisão (decision head): camada linear aprendida que transforma o estado oculto do marcador em pontuações para as opções de resposta.
- Marcador de leitura: token especial que indica onde a predição é lida.
- Locate: recurso que extrai trechos verbatim do estado com posições de início e fim em caracteres.
- Span: trecho extraído, com start, end (exclusivo), text e score.
- noul: tipo de pergunta binária que retorna P(true).
- Score: tipo de pergunta com níveis ordenados do mais baixo ao mais alto.
- Choice: tipo de pergunta de múltipla escolha com 1 a 255 opções.
- Bidirectional attention: atenção em que tokens podem atender em ambas as direções, em vez de apenas aos anteriores.
- Mode separate: cada pergunta em sua própria sequência; perguntas não se veem.
- Mode isolated: pedido inteiro como uma sequência; estado lido uma vez.
- Fast path: modo de inferência que empacota várias sequências por passada e compila o decoder.
- LoRA: técnica de fine-tuning por adaptadores de baixo posto (low-rank) usada nos estágios finos de treino.
- Destilação: treino do modelo menor para imitar a distribuição de saída do modelo maior via divergência KL.
- nDCG@10: métrica de qualidade de ranqueamento nos 10 primeiros resultados.
- F1 de span exato: métrica que exige que spans previstos coincidam exatamente com as fronteiras de referência.
- BEIR: benchmark de recuperação de informação.
- tasksource: conjunto de dados de tarefas de NLP citado como contribuinte importante para os ganhos.

## Links citados

- https://docs.perplexity.ai/docs/decisions/quickstart
- https://huggingface.co/collections/perplexity-ai/decider-v13
- https://huggingface.co/perplexity-ai/pplx-decider-flash-v1.3
- https://openrouter.ai/perplexity/pplx-decider-flash-v1.3:free
- https://openrouter.ai/perplexity/pplx-decider-v1.3:free

## Outros pontos

- A Perplexity se inspirou no Jev, modelo da TypeSafe AI conhecido como System One Model.
- Os repositórios no Hugging Face são privados e exigem token com acesso.
- O modelo base do v1.3 é o Qwen3.8-27B; o do Flash é o Qwen3.5-4B.
- O Decider tem suporte a imagens (visão) desde a v1.
- A v1.3 melhora desempenho e robustez por atenção bidirecional, dados de treino melhor curados e receita de treino refinada.
- O treinamento remove amostras que possam se sobrepor a avaliações e realiza auditorias e remoções de viés.
- Os adapters de locate são mantidos não fundidos porque fundi-los causa regressão em pedidos de decisão.
- Entradas nunca são truncadas; a validação de entradas longas fica por conta do usuário.
- O caminho padrão com uma request por chamada reproduz a implementação de avaliação com diferença de até 3e-7.
- O post inclui uma citação BibTeX com autores e data de 12 de novembro de 2026.
- Os ganhos são atribuídos em parte aos dados do tasksource.
- A licença dos modelos é Apache.
