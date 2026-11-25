# Meta usa agentes para 60% da propagação desde março 2026

_2026-11-23 · reportagem_

Desde março de 2026, agentes de IA tocam mais de 60% da propagação de técnicas entre os modelos de ranking de anúncios da Meta, segundo estimativa da própria empresa. Os primeiros resultados apontam 3x mais produtividade por engenheiro e redução mediana de 4x no compute de treino em combinações selecionadas.

## O contexto

Propagar é adaptar uma técnica já provada em um modelo para o resto da frota, cada modelo com arquitetura e dados próprios. A técnica quase nunca funciona por copiar e colar.

Antes dos agentes, a Meta padronizou o desenho dos modelos em blocos reutilizáveis, os Standard Model Templates (SMT). Uma técnica validada uma vez no template se propaga para todo modelo construído a partir dele.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/>

## Linha do tempo

- Março de 2026: os agentes passam a conduzir a execução da propagação.
- 18 de novembro de 2026: publicação do post oficial da Meta.

## Quem ganha e quem perde

Os agentes têm três frentes: discovery, que gera a lista de candidatos ordenada por impacto esperado; generalization, que adapta a técnica para modelos novos; e adoption, que transforma adaptações validadas em modelos em produção.

Sobrou para os engenheiros o que exige juízo: qual técnica vale para qual modelo, quão ampla deve ser a busca de hiperparâmetros e como detectar e resolver falhas.

## O que ainda não se sabe

Os números são da própria Meta: 3x mais produtividade de engenharia, mediana de 4x menos compute em combinações selecionadas e US$ 45 milhões ou mais de economia estimada em compute até o fim do ano.

Os 60% são uma estimativa da empresa. Os resultados são comparados ao mesmo trabalho antes dos agentes, e valem para as combinações selecionadas.
