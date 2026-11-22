# LinkedIn reduz modelo de ranking de 7B para 400M parâmetros

_2026-11-20 · noticia_

O LinkedIn ranqueia vagas com um modelo de linguagem para 1,3 bilhão de membros, sob limite de latência P99 e sem estourar o custo de GPU. Para isso, o time reduziu o modelo de 7 bilhões para 400 milhões de parâmetros e comprimiu cada vaga de cerca de 2.000 tokens para 1 embedding. O ranking usa a probabilidade de "yes" como nota, sem gerar texto. A apostila reúne os números e os três passos que qualquer marketplace pode copiar.

## O problema: ranquear com LLM em tempo real

A busca do LinkedIn atende 1,3 bilhão de membros e ranqueia centenas de candidatos a cada requisição. O limite é a latência P99 e o custo de GPU. Sundara Raman Ramachandran, lead engineer do time de LLM Inference do LinkedIn, detalhou a solução na QCon AI, em apresentação publicada pela InfoQ.

O time atacou três frentes ao mesmo tempo: encolher o modelo, encolher o contexto e otimizar a inferência.

Fonte: <https://www.infoq.com/presentations/scale-llm-ranking-systems-linkedin/>

## Ranking sem gerar texto

Num chatbot, o modelo faz prefill (entende o contexto) e depois um loop de decode, gerando token a token. No ranking não há decode. Monta-se um prompt por item candidato, todos com o mesmo prefixo (busca, perfil do membro, instrução do sistema), e tudo passa num prefill em lote.

O prompt de produção pergunta, dados a busca, o perfil e uma vaga, se há match. A probabilidade do token "yes" vira a nota que ordena os resultados. Sem o loop de decode, a latência cai.

Fonte: <https://www.infoq.com/presentations/scale-llm-ranking-systems-linkedin/>

## Modelo: de 7B para 400M de parâmetros

O ponto de partida foi um modelo professor de 7 bilhões de parâmetros. Ele entendia políticas de produto e relevância, mas era pesado demais para produção.

- Destilação multi-professor: o conhecimento foi transferido para dois modelos menores, um para relevância e outro para engajamento.
- Os dois foram combinados num único modelo aluno de 0,6 bilhão de parâmetros.
- Pruning: o time removeu camadas de atenção e MLP por tentativa e erro, medindo a perda de qualidade aceitável.
- Nova rodada de destilação e fine-tuning para recuperar a qualidade.
- Resultado: um modelo de 400 milhões de parâmetros, pronto para produção.

Fonte: <https://www.infoq.com/presentations/scale-llm-ranking-systems-linkedin/>

## Contexto: cada vaga vira uma embedding

Uma descrição de vaga pode chegar a 2.000 tokens. Com 100 candidatos por requisição, são 200 mil tokens processados de uma vez, inviável nessa escala.

A solução foi comprimir a vaga sempre offline: o resultado fica salvo em banco e é só lido no caminho online.

- Texto completo: cerca de 2.000 tokens por item, 290 itens/s por GPU, qualidade de referência.
- Resumo gerado por LLM: cerca de 150 tokens, cerca de 2.200 itens/s por GPU, perda de qualidade menor que 2%.
- Embedding única: 1 token, cerca de 22.000 itens/s por GPU, qualidade igual ou levemente melhor.
- O resumo reduziu o prompt por item em 16x e deu ganho de quase 8x em throughput. A embedding única multiplicou o throughput por outros 10x.

Fonte: <https://www.infoq.com/presentations/scale-llm-ranking-systems-linkedin/>

## Como aplicar no seu marketplace

Nenhuma empresa brasileira opera com 1,3 bilhão de membros, mas o raciocínio serve a qualquer marketplace, job board ou e-commerce que queira rerankear resultados com LLM sem estourar GPU nem latência de página.

- Use a probabilidade do token ("yes" ou "no") como nota em vez de gerar texto. Isso elimina o loop de decode e serve para ranking binário ou multi-classe.
- Destile com vários professores, um por métrica (relevância, engajamento), para treinar um modelo menor sem perder sinais de qualidade.
- Comprima o item (resumo ou embedding única, gerados offline) antes de mexer na infraestrutura. Costuma render mais throughput que qualquer otimização de infra isolada e deve vir antes do capacity planning.
- Quem já serve modelos com SGLang ou vLLM pode olhar a API de scoring do SGLang, pensada para ranking que só precisa da probabilidade do próximo token.

Fonte: <https://www.infoq.com/presentations/scale-llm-ranking-systems-linkedin/>

## A regra que resume tudo

Nas palavras de Ramachandran: "The best representation for your workload is not necessarily the longest one. It's the smallest one that can give you the acceptable quality your use case needs."

Em português: a melhor representação para o seu caso não é a mais longa, e sim a menor que ainda entrega a qualidade de que você precisa.

Fonte: <https://www.infoq.com/presentations/scale-llm-ranking-systems-linkedin/>

## Além do vídeo

- O pipeline de busca tem três camadas: entendimento de query, retrieval por busca vetorial (KNN) contra embeddings pré-computados de milhões de vagas, e ranking com o LLM.
- Na inferência, o time não tratou SGLang, vLLM e TensorRT-LLM como solução pronta. Segundo o resumo oficial da palestra, foram atacados gargalos do workload de ranking: máscaras customizadas de flash attention, contornos para o GIL do Python, gc.freeze e cópias de memória CUDA não bloqueantes.
- Ramachandran contribui com o SGLang, projeto open source com foco na API de scoring usada para ranking com LLMs.
- O modelo professor de 7B entendia políticas de produto e relevância, mas era pesado demais para produção.
