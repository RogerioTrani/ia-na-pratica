# Meta corta 92% do tempo por modelo com templates ML

_2026-11-23 · reportagem_

A Meta reduziu em 92% o tempo de engenharia por modelo em dois anos ao padronizar o design dos modelos de ranking de anúncios em templates reutilizáveis (SMT). Em vez de adaptar cada ideia modelo por modelo, a equipe testa técnicas em modelos representativos e propaga o que generaliza. Esta apostila reúne o problema, o método, os números e o papel dos templates em sistemas de agentes de ML.

## O problema: fragmentação em escala

Os sistemas de ranking de anúncios da Meta processam bilhões de requisições por dia, em muitos produtos e objetivos de otimização, atendidos por um grande número de modelos em produção. Com esse volume, o desafio deixou de ser inventar técnicas e passou a ser levá-las a todos os modelos em que se aplicam.

A diversidade de arquiteturas, features, configurações de treino, restrições de serving e lógica específica de plataforma criou três custos:

- Custo de engenharia alto para propagar ideias novas.
- Custo de confiabilidade alto, por causa da explosão de casos extremos.
- Baixa previsibilidade ao estimar o impacto de uma mudança em todo o ecossistema.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/design-once-deploy-at-scale-template-driven-ml-ecosystem/>

## A solução: Standard Model Templates (SMT)

Um template é uma configuração de modelo mínima e opinativa, montada com componentes compartilhados: escolhas de arquitetura, lógica de features, configurações de treino e de serving. A Meta agrupou modelos similares em torno de poucos templates padrão. A lógica específica de cada modelo continua existindo onde é necessária, mas as partes comuns passaram a ser compartilhadas.

Os templates cobrem os principais padrões de ranking e recuperação em diferentes tamanhos de modelo. Eles empacotam componentes reutilizáveis para seleção de features, interação entre features, paralelismo de modelo, configuração de treino e serving adaptado ao hardware.

Na prática, uma ideia nova é avaliada num conjunto pequeno de templates representativos e depois propagada aos grupos de modelos que os usam. A iteração deixa de ser por modelo e passa a ser por template.

- Menos complexidade de propagação: uma implementação serve muitos modelos.
- Mais confiabilidade: com menos setups únicos, validações, guardrails e depuração se tornam viáveis.
- Mais previsibilidade: o desempenho em modelos representativos vira sinal para o resto do grupo.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/design-once-deploy-at-scale-template-driven-ml-ecosystem/>

## Os números de dois anos

Segundo a Meta, nos últimos dois anos a abordagem por templates entregou os resultados abaixo.

- Redução de 92% no tempo de engenharia por modelo.
- Mais de 5000 combinações técnica-modelo entregues.
- 80 técnicas novas de ML entregues pelo fluxo de otimização multi-modelo.
- Qualidade offline 0,63% maior em média, com capacidade de serving neutra.
- Lift online acumulado de 0,86%, cobrindo 70% dos modelos por contagem.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/design-once-deploy-at-scale-template-driven-ml-ecosystem/>

## Como uma técnica entra num template

A otimização multi-modelo torna a iteração dos templates rigorosa. Ela avalia técnicas candidatas em modelos representativos e busca configurações que melhorem o desempenho agregado e limitem regressões. Uma técnica com ganho médio alto, mas regressões frequentes, é difícil de lançar numa frota grande: a consistência pesa tanto quanto o ganho máximo.

Depois da otimização, as candidatas são validadas em modelos retidos, para checar se o ganho se transfere além do conjunto representativo. As que passam entram na próxima versão do template, e todo modelo que adota um template maduro herda o histórico de melhorias generalizadas.

- Avaliar candidatas em modelos representativos.
- Medir ganho agregado e taxa de regressão.
- Validar em modelos retidos.
- Integrar as aprovadas na próxima versão do template.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/design-once-deploy-at-scale-template-driven-ml-ecosystem/>

## Por que isso importa para agentes de ML

Um agente que explora livremente o design de modelos enfrenta um espaço de busca sem restrições. Sem bons pontos de partida, gasta esforço em regiões improdutivas, se recupera de falhas evitáveis ou propõe mudanças difíceis de explicar e de lançar.

Os templates codificam padrões de design já conhecidos como bons. Isso dá aos agentes um ponto de partida estruturado, um espaço de busca limitado e um piso de qualidade. Na Meta, os SMTs são a base da abordagem multiagente para construir modelos: os templates trazem a estrutura e os agentes trazem exploração adaptativa e automação.

No nível do template, os agentes ajudam a construir, avaliar e melhorar os próprios templates. Propõem ideias de otimização com base em técnicas comprovadas, lançam experimentos em modelos representativos, diagnosticam falhas e iteram em várias rodadas. Também assumem trabalhos mais pesados, como migrar modelos para novas plataformas de hardware.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/design-once-deploy-at-scale-template-driven-ml-ecosystem/>

## O que a Meta aprendeu

A automação rende mais quando o sistema por baixo é mais estruturado. O desenvolvimento por templates facilitou a operação para as pessoas e também para sistemas de otimização, fluxos de scaling e agentes.

A padronização só funciona se for opinativa o bastante para remover diversidade desnecessária e preservar a flexibilidade limitada que importa. Um sistema de templates que tenta acomodar todo caso extremo histórico acaba recriando a fragmentação que queria resolver.

Padronizar é uma escolha arquitetural para fazer um ecossistema grande de ML aprender mais rápido.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/design-once-deploy-at-scale-template-driven-ml-ecosystem/>

## Fontes para aprofundar

- Post oficial: Design Once, Deploy at Scale (Engineering at Meta) https://engineering.fb.com/2026/11/18/ml-applications/design-once-deploy-at-scale-template-driven-ml-ecosystem/
- Post complementar: How Meta Uses AI Agents to Scale ML Innovations Across Ads Ranking Models https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/
- Artigo no arXiv: Template-Driven Machine Learning Standardization for Large Model Fleets https://arxiv.org/abs/2603.24963

Fonte: <https://arxiv.org/abs/2603.24963>

## Além do vídeo

- Os templates empacotam componentes para seleção de features, interação entre features, paralelismo de modelo, configuração de treino e serving adaptado ao hardware.
- Como a estrutura padronizada torna as decisões de scaling reutilizáveis, a Meta aprende trade-offs de custo e desempenho no espaço de templates, o que levou a fluxos de otimização baseados em scaling laws.
- A Meta transfere designs completos de modelos fortes para famílias-alvo por uma camada de template compartilhada, porque muitos ganhos vêm da interação entre arquitetura, escala e estratégia de treino.
- Agentes também ajudam a migrar modelos para novas plataformas de hardware, e uma técnica validada num template chega a todos os modelos construídos sobre ele com uma fração do custo de computação.
- Próximos passos citados pela Meta: melhorar a cobertura dos templates, reforçar a otimização baseada em scaling laws e avançar para fluxos agênticos de ponta a ponta, com mais confiabilidade e explicabilidade.
