# LinkedIn reduz modelo de ranking de 7B para 400M parâmetros

_2026-11-20 · noticia_

O LinkedIn reduziu um modelo de ranking de 7 bilhões para 400 milhões de parâmetros e comprimiu a descrição de cada vaga até uma única embedding. A apostila explica como busca, recuperação vetorial e ranking se encaixam e por que usar a probabilidade de match evita gerar texto. Você vai entender destilação multi-professor, pruning, representações offline e os ajustes de inferência que sustentam o caso. Também verá os números com seu recorte e um caminho para aplicar o mesmo raciocínio à sua busca. Ao final, conseguirá mapear o pipeline, escolher uma representação menor e definir o que medir antes de ampliar a infraestrutura.

## O fato

Em uma apresentação na QCon AI, publicada pela InfoQ, a equipe de LLM Inference do LinkedIn detalhou uma mudança no ranking de busca. O modelo usado para ordenar resultados caiu de 7 bilhões para 400 milhões de parâmetros. A redução veio da destilação de um modelo professor para modelos menores, seguida de pruning e de uma nova rodada de destilação e fine-tuning.

A mesma apresentação mostrou a compressão da descrição de cada vaga. Uma representação que podia chegar a 2.000 tokens passou a ser lida do banco como uma única embedding densa, gerada offline. O caso atende uma busca que alcança 1,3 bilhão de membros e ranqueia centenas de candidatos por requisição.

Fonte: <https://www.infoq.com/presentations/scale-llm-ranking-systems-linkedin/>

## Por que isso importa

O trabalho do ranking é ordenar candidatos. A saída que interessa ao sistema é uma nota para cada item, e não um texto para o usuário. Quando um chatbot responde, o modelo primeiro processa o contexto no prefill e depois entra no decode, gerando token após token. No ranking, a equipe pode processar os candidatos em lote no prefill e usar apenas a probabilidade de uma resposta como score.

Isso muda o custo da operação. Cada requisição pode envolver centenas de candidatos, sob um SLA de latência P99 rígido. Nesse cenário, uma melhora na média não basta: o sistema precisa controlar também o tempo das requisições mais lentas. Modelos menores e contextos menores reduzem o trabalho dentro desse limite.

A equipe atacou três frentes ligadas entre si: encolher o modelo, encolher o contexto e otimizar a inferência. A lição prática é escolher a menor representação que ainda entregue a qualidade necessária antes de assumir que o problema será resolvido com mais infraestrutura.

Fonte: <https://www.infoq.com/presentations/scale-llm-ranking-systems-linkedin/>

## As três camadas da busca

A primeira camada é o entendimento da query. Ela transforma uma expressão natural ambígua em algo estruturado. Exemplo: a consulta 'ache vagas de design perto de mim' precisa resolver o que significa 'perto de mim' usando dados do perfil. O resultado dessa etapa orienta a busca que vem depois.

A segunda camada é o retrieval, ou recuperação. O sistema faz uma busca vetorial com KNN contra embeddings pré-computados de milhões de vagas e traz os top-K candidatos. Essa etapa é otimizada para recall, porque precisa trazer uma boa seleção inicial. A precisão da ordem final fica para a próxima camada.

A terceira camada é o ranking, onde entra o LLM. Ele recebe os candidatos recuperados e atribui uma nota a cada um. Separar as etapas evita pedir ao modelo que procure em todo o catálogo e ainda ordene os resultados. O LLM trabalha sobre um conjunto já selecionado, e a qualidade desse conjunto depende do retrieval.

Fonte: <https://www.infoq.com/presentations/scale-llm-ranking-systems-linkedin/>

## Ranking por score, sem decode

Cada candidato recebe um prompt com a query, o perfil do membro, a instrução do sistema e a vaga. Os candidatos compartilham um prefixo longo com as informações comuns. O motor processa esse conjunto em um prefill em lote, sem passar pelo loop de geração de texto.

O modelo calcula a probabilidade de responder yes ou no para aquele item. A probabilidade de yes vira o score usado para ordenar os resultados. Assim, o sistema obtém a nota de relevância diretamente do modelo e não precisa esperar uma explicação ou uma frase gerada.

A mesma ideia pode servir ao ranking binário ou multiclasse. No caso binário, a decisão é match ou não match. Com mais classes, o score pode usar a probabilidade da categoria que interessa ao ordenamento. O princípio continua sendo usar uma probabilidade do modelo como nota.

Fonte: <https://www.infoq.com/presentations/scale-llm-ranking-systems-linkedin/>

## A pergunta feita ao modelo

O prompt de produção descrito na apresentação é direto: dado a query, o perfil do membro e uma vaga, o modelo responde se há match. A pergunta reúne o que a pessoa procura, o contexto que ajuda a interpretar essa busca e o item que precisa ser avaliado.

Essa estrutura também explica por que a compressão do item tem tanto efeito. A query, o perfil e a instrução do sistema formam um prefixo compartilhado, enquanto a descrição da vaga varia para cada candidato. Reduzir a parte variável diminui o contexto processado sem retirar as informações usadas para decidir o match.

Exemplo: uma vaga com texto longo pode ser substituída, no caminho online, pela representação densa que o LinkedIn gera e guarda offline. O ranking continua recebendo query, perfil e vaga, mas a vaga chega ao modelo em uma forma menor.

Fonte: <https://www.infoq.com/presentations/scale-llm-ranking-systems-linkedin/>

## Destilação multi-professor

O processo começou com um modelo professor de 7 bilhões de parâmetros. Ele era capaz de entender políticas de produto e relevância, mas pesado demais para a produção na escala da busca. A equipe usou destilação para transferir esse conhecimento a modelos menores.

Em vez de resumir tudo em um único sinal, a equipe transferiu o conhecimento do professor a dois modelos menores, cada um voltado a uma métrica: relevância e engajamento. Os dois foram depois combinados em um único modelo aluno de 0,6 bilhão de parâmetros. A destilação multi-professor permite preservar critérios diferentes enquanto reduz o tamanho do modelo final.

A vantagem para quem projeta ranking é poder separar objetivos que competem entre si. Um candidato pode ser relevante para a busca e ainda assim ter engajamento diferente. O caso do LinkedIn mostra um caminho para ensinar o modelo menor com os dois sinais, em vez de escolher um e descartar o outro.

Fonte: <https://www.infoq.com/presentations/scale-llm-ranking-systems-linkedin/>

## Pruning e recuperação de qualidade

Depois da destilação, a equipe aplicou pruning. O trabalho consistiu em remover camadas de atenção e MLP por tentativa e erro, medindo a perda de qualidade aceitável. Pruning não significa apagar parâmetros sem critério; neste caso, cada corte foi avaliado pelo efeito no ranking.

A remoção de camadas pode recuperar capacidade de processamento, mas também pode retirar conhecimento útil. Por isso, o processo continuou com uma nova rodada de destilação e fine-tuning para recuperar o que fosse necessário. O ajuste adicional treina o modelo depois que sua estrutura foi reduzida.

O resultado foi um modelo de 400 milhões de parâmetros, pronto para servir em produção. A sequência importa: destilar, combinar sinais, podar, medir e treinar novamente. Cada etapa tem uma finalidade diferente, e a qualidade do modelo final depende da medição feita ao longo do caminho.

Fonte: <https://www.infoq.com/presentations/scale-llm-ranking-systems-linkedin/>

## Comprimir o contexto antes de servir

A descrição de uma vaga pode chegar a 2.000 tokens. Se 100 candidatos chegassem a esse tamanho, uma única requisição de ranking processaria 200 mil tokens. O custo aparece antes de qualquer decisão de infraestrutura: o modelo recebe uma grande quantidade de texto para avaliar uma lista.

A primeira compressão foi um resumo gerado por LLM, com cerca de 150 tokens por item. Isso reduziu o tamanho do prompt por item em 16 vezes e aumentou o throughput em quase 8 vezes. A perda de qualidade ficou abaixo de 2% em relação ao texto completo.

A equipe foi além e passou a usar uma única embedding densa por vaga. A representação caiu para 1 token por item e o throughput chegou a cerca de 22.000 itens por segundo por GPU. A qualidade de ranking ficou igual ou levemente melhor do que com o texto resumido.

As duas representações são geradas offline. O resultado fica salvo em banco e o caminho online apenas o lê. Essa separação tira trabalho repetido da requisição e deixa claro onde a representação precisa ser atualizada quando o item muda.

Fonte: <https://www.infoq.com/presentations/scale-llm-ranking-systems-linkedin/>

## Inferência: o trabalho depois do modelo

A equipe avaliou motores como SGLang, vLLM e TensorRT-LLM e caçou gargalos específicos do workload de ranking. A apresentação aponta máscaras customizadas de flash attention, contornos para o GIL do Python, uso de gc.freeze e cópias de memória CUDA não bloqueantes. Esses ajustes mostram que o runtime também participa do desempenho em produção.

Cada item dessa lista trata de uma parte diferente da execução: atenção, coordenação do Python, coleta de lixo ou movimentação de memória. A escolha depende do gargalo encontrado no sistema real. Uma otimização de runtime não substitui a redução do modelo e do contexto, mas pode melhorar o que sobra depois dessas reduções.

A apresentação também cita a API de scoring do SGLang como caminho para casos de ranking que precisam apenas da probabilidade do próximo token. Quem já usa o projeto pode avaliar essa rota, mantendo o foco no score e na dispensa da geração de texto.

Fonte: <https://www.infoq.com/presentations/scale-llm-ranking-systems-linkedin/>

## Os números

Os valores abaixo pertencem ao caso apresentado pelo LinkedIn. Throughput mede itens processados por segundo por GPU; ele ajuda a comparar representações, mas precisa ser lido junto com a qualidade do ranking e com o SLA de latência.

A perda de qualidade também tem um ponto de comparação. No resumo, ela é medida em relação ao texto completo. Na embedding única, a comparação é com o texto resumido. Esses recortes evitam transformar um resultado de um teste em promessa para qualquer catálogo.

- 1,3 bilhão de membros: alcance da busca apresentado no caso; indica a escala do problema, sem definir o volume de cada produto que reutilize a arquitetura.
- Centenas de candidatos por requisição: quantidade de itens que o ranking precisa avaliar junto; explica por que otimizações por item afetam a operação inteira.
- 7 bilhões de parâmetros: tamanho do modelo professor antes da destilação.
- 0,6 bilhão de parâmetros: tamanho do modelo aluno combinado depois de reunir os modelos de relevância e engajamento.
- 400 milhões de parâmetros: tamanho do modelo final após pruning, nova destilação e fine-tuning.
- Cerca de 2.000 tokens por item: representação em texto completo usada como baseline para a descrição da vaga.
- 200 mil tokens: total processado no exemplo de 100 candidatos quando cada descrição chega a 2.000 tokens.
- Cerca de 150 tokens por item: tamanho do resumo gerado por LLM, com redução de 16 vezes no prompt por item.
- 290 itens/s por GPU: throughput do texto completo, usado como linha de base.
- Cerca de 2.200 itens/s por GPU: throughput do resumo por LLM, com ganho de quase 8 vezes em relação ao texto completo.
- Menos de 2% de perda de qualidade: resultado do resumo comparado ao texto completo; não é uma garantia para outra base de vagas.
- 1 token por item: tamanho da representação com uma única embedding densa.
- Cerca de 22.000 itens/s por GPU: throughput da embedding única, com ganho adicional de 10 vezes sobre o resumo e qualidade igual ou levemente melhor.

Fonte: <https://www.infoq.com/presentations/scale-llm-ranking-systems-linkedin/>

## O que muda para você

O raciocínio vale para marketplace, job board e e-commerce que queira usar um LLM para reordenar resultados. A escala pode ser menor, mas a pergunta continua sendo a mesma: qual é a menor representação do item que preserva a qualidade necessária para ordenar a lista?

Exemplo: imagine um job board com entendimento de query, recuperação vetorial e ranking por LLM. A vaga pode ser representada offline por uma embedding densa. Na requisição, o sistema recupera os candidatos, monta o contexto com query e perfil, calcula a probabilidade de match e ordena os itens pelo score. O leitor desse sistema não recebe texto gerado pelo ranker; recebe a lista ordenada.

Antes de planejar mais capacidade, compare a representação do item e a forma de pontuar. Depois de reduzir esses dois custos, perfile o runtime. Essa ordem ajuda a separar o ganho estrutural de contexto e modelo dos ajustes finos de execução.

Fonte: <https://www.infoq.com/presentations/scale-llm-ranking-systems-linkedin/>

## O que fazer hoje

Use estes passos como um roteiro de análise do seu pipeline. Cada etapa deve terminar com um resultado que você consiga observar ou medir.

1. Mapeie as três camadas da busca: entendimento de query, retrieval e ranking. O resultado esperado é saber quais informações entram em cada etapa e onde o LLM começa a atuar.
2. Defina as métricas do ranking e o SLA P99 no seu caso. O resultado esperado é um alvo explícito de qualidade e latência para orientar as comparações.
3. Separe recuperação de ordenação e avalie o recall do retrieval. O resultado esperado é confirmar que os candidatos importantes chegam ao ranking antes de otimizar o modelo.
4. Substitua a geração de texto pela probabilidade de match no ranker. O resultado esperado é um score por candidato sem o loop de decode.
5. Gere offline um resumo ou uma embedding do item e salve a representação para leitura no caminho online. O resultado esperado é uma versão menor da entrada usada pelo ranking.
6. Compare texto completo, resumo e embedding no mesmo conjunto de candidatos. O resultado esperado é escolher a representação com qualidade aceitável e registrar tokens e throughput por GPU.
7. Se o modelo ainda for grande demais, avalie destilação multi-professor, pruning e fine-tuning. O resultado esperado é um modelo menor com relevância e engajamento medidos separadamente.
8. Perfile o runtime depois de reduzir modelo e contexto. O resultado esperado é identificar se atenção, Python, coleta de lixo ou memória exigem ajustes no seu workload.
9. Se já usar SGLang, avalie a API de scoring para obter a probabilidade do próximo token. O resultado esperado é uma rota de inferência focada no score, sem gerar resposta em texto.

Fonte: <https://www.infoq.com/presentations/scale-llm-ranking-systems-linkedin/>

## O que conferir

Os ganhos do caso do LinkedIn dependem do workload, das métricas e da qualidade aceitável. Antes de transportar a solução, confira estes pontos no seu próprio sistema.

- Recorte dos números: os 290, 2.200 e 22.000 itens/s por GPU são resultados das representações apresentadas, não uma promessa de desempenho para outro hardware ou catálogo.
- Qualidade: defina como medir relevância e engajamento e preserve os dois sinais se ambos forem necessários ao produto.
- Recall do retrieval: um candidato que não chega ao ranking não pode ser recuperado pelo LLM; otimizar o ranker não corrige uma seleção inicial incompleta.
- Representação offline: mudanças na descrição do item precisam de nova geração para que a versão lida no caminho online reflita o conteúdo atual.
- Latência: throughput por GPU não mede sozinho o SLA P99; a avaliação precisa incluir o tempo das requisições no sistema completo.
- Pruning: meça a perda de qualidade ao remover camadas e use a nova destilação e o fine-tuning para recuperar o que for necessário.
- Runtime: confirme o gargalo antes de aplicar contornos de GIL, gc.freeze ou cópias CUDA não bloqueantes; cada ajuste responde a um problema específico de execução.
- API de scoring: confirme se a probabilidade do token usada como score corresponde à decisão de match ou à classe que o seu ranking precisa ordenar.

Fonte: <https://www.infoq.com/presentations/scale-llm-ranking-systems-linkedin/>

## Glossário

- LLM: modelo de linguagem de grande escala treinado para processar e produzir texto.
- Parâmetro: valor interno ajustado durante o treinamento; a quantidade de parâmetros indica o tamanho do modelo.
- Token: unidade de texto processada pelo modelo, usada aqui para medir o contexto de cada candidato.
- Embedding: vetor numérico denso que representa um item e permite compará-lo por similaridade.
- Ranking: ordenação de candidatos segundo um critério ou uma nota.
- Reranking: reordenação de um conjunto de resultados que já passou por uma etapa anterior de recuperação.
- Score: nota numérica usada para ordenar os candidatos.
- Prefill: etapa em que o modelo processa o contexto de entrada antes de gerar uma resposta.
- Decode: etapa de geração que produz um token por vez; no ranking por probabilidade, esse loop é dispensado.
- Destilação: treinamento de um modelo menor para reproduzir o conhecimento ou as saídas de um modelo professor.
- Modelo professor: modelo usado como referência para ensinar outro modelo.
- Modelo aluno: modelo que recebe o conhecimento transferido pelo professor.
- Pruning: remoção de partes do modelo para reduzir seu tamanho ou custo de execução.
- Fine-tuning: treinamento adicional para ajustar um modelo depois da destilação ou da redução de sua estrutura.
- KNN: método de busca por vizinhos mais próximos, usado no retrieval vetorial para encontrar itens semelhantes.
- Top-K: conjunto dos K candidatos mais próximos ou mais bem posicionados trazidos pela recuperação.
- Recall: proporção dos itens relevantes que a recuperação consegue trazer para o conjunto de candidatos.
- Precisão: proporção de itens relevantes entre os resultados apresentados.
- Throughput: quantidade de itens processados por unidade de tempo; no caso apresentado, itens por segundo por GPU.
- Latência: tempo que uma requisição leva para ser respondida.
- SLA: acordo que define o nível de serviço esperado, incluindo limites de desempenho.
- P99: percentil 99; olha para o tempo abaixo do qual ficam 99% das requisições e ajuda a avaliar a cauda da latência.
- GIL: mecanismo do Python que controla o acesso à execução e pode influenciar o paralelismo do processo.
- gc.freeze: recurso do Python que congela a coleta de lixo para reduzir seu trabalho sobre objetos já existentes.
- CUDA: ambiente de computação paralela usado para executar trabalho em GPUs.
- Flash attention: técnica voltada a tornar o processamento de atenção mais eficiente em memória e computação.
- MLP: rede multicamadas de neurônios usada dentro do modelo e citada entre as camadas removidas no pruning.

## Para onde ir depois

Comece pelo desenho do seu pipeline e escolha um conjunto de itens para comparar as representações. Pratique com texto completo, resumo e embedding, medindo qualidade, tokens e throughput. Depois, teste o score de probabilidade no ranking e observe o efeito na latência P99.

A referência do caso é a apresentação oficial Scaling LLM-Based Ranking Systems for Latency-Critical Search & Recommendation Workloads, publicada pela InfoQ. Ela reúne o recorte de modelo, contexto e inferência usado pelo LinkedIn. O próximo passo é aplicar esse recorte ao seu workload e manter as medições que justificam cada redução.

Fonte: <https://www.infoq.com/presentations/scale-llm-ranking-systems-linkedin/>
