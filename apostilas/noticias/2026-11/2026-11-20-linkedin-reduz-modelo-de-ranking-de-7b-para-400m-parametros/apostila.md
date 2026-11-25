# LinkedIn reduz modelo de ranking de 7B para 400M parâmetros

_2026-11-20 · noticia_

O LinkedIn ranqueia vagas com um modelo de linguagem para 1,3 bilhão de membros. O time reduziu o modelo de 7 bilhões para 400 milhões de parâmetros e comprimiu cada vaga de cerca de 2.000 tokens para 1 embedding. O ranking usa a probabilidade de 'yes' como nota, sem gerar texto.

## O fato

O LinkedIn ranqueia vagas com um modelo de linguagem para 1,3 bilhão de membros, sob limite de latência P99 e sem estourar o custo de GPU.

Sundara Raman Ramachandran, lead engineer do time de LLM Inference do LinkedIn, detalhou a solução na QCon AI, em apresentação publicada pela InfoQ.

Fonte: <https://www.infoq.com/presentations/scale-llm-ranking-systems-linkedin/>

## Os números

- 1,3 bilhão de membros atendidos pela busca.
- De 7 bilhões para 400 milhões de parâmetros no modelo.
- De cerca de 2.000 tokens para 1 embedding por vaga.
- Prompt por item reduzido em 16x, com ganho de quase 8x em throughput com o resumo.
- A embedding única multiplicou o throughput por outros 10x.

## O que muda para você

No ranking não há decode. Monta-se um prompt por item candidato, todos com o mesmo prefixo, e tudo passa num prefill em lote. A probabilidade do token 'yes' vira a nota que ordena os resultados.

Uma descrição de vaga pode chegar a 2.000 tokens. Com 100 candidatos por requisição, seriam 200 mil tokens processados de uma vez, inviável nessa escala. A vaga é comprimida offline e o resultado fica salvo em banco.

## O que fazer hoje

1. Use a probabilidade do token ('yes' ou 'no') como nota em vez de gerar texto. Resultado: o loop de decode some e a latência cai.
2. Destile com vários professores, um por métrica, como relevância e engajamento. Resultado: um modelo menor mantém sinais de qualidade.
3. Comprima o item, com resumo ou embedding única gerados offline, antes de mexer na infraestrutura. Resultado: mais throughput do que otimizar a infra isolada.
4. Quem já serve modelos com SGLang ou vLLM pode olhar a API de scoring do SGLang. Resultado: o ranking usa só a probabilidade do próximo token.

Fonte: <https://www.infoq.com/presentations/scale-llm-ranking-systems-linkedin/>

## O que conferir

Os números de throughput vêm da apresentação, feita num contexto de escala do LinkedIn. Eles não se transferem direto para outro marketplace.

O resumo gerado por LLM teve perda de qualidade menor que 2%, segundo a apresentação. A embedding única ficou com qualidade igual ou levemente melhor.
