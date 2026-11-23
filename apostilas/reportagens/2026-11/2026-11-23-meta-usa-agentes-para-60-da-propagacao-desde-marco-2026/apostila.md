# Meta usa agentes para 60% da propagação desde março 2026

_2026-11-23 · reportagem_

Desde março de 2026, agentes de IA tocam mais de 60% da propagação de técnicas entre os modelos de ranking de anúncios da Meta, segundo estimativa da própria empresa. Propagar é adaptar uma técnica já provada em um modelo para o resto da frota, cada modelo com arquitetura e dados próprios. Os primeiros resultados apontam 3x mais produtividade por engenheiro e redução mediana de 4x no compute de treino em combinações selecionadas.

## O número central

Desde que os agentes passaram a conduzir a execução, em março de 2026, a Meta estima que eles cuidem de mais de 60% de toda a propagação de técnicas. Os demais 40% ficam abaixo desse patamar, segundo a fonte.

A comparação é feita contra o mesmo trabalho antes dos agentes.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/>

## O que é propagação de técnicas

Uma técnica é qualquer coisa que melhora um modelo de ranking: avanço de arquitetura, representação de dados mais rica, otimização de treino ou ganho de eficiência em treino e inferência.

Propagar é adaptar uma técnica provada em um modelo para o resto da frota. Cada modelo tem arquitetura, dados de treino e restrições de serviço próprios, então a técnica quase nunca funciona por copiar e colar.

Há pressa: técnicas têm prazo de validade e podem ser superadas em poucos ciclos de desenvolvimento. Quanto antes uma técnica provada chega a toda a frota, mais valor ela entrega.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/>

## Os dois gargalos

O primeiro é a banca de engenharia. O método tradicional coloca um especialista para estudar como a técnica interage com a arquitetura de um modelo, generalizá-la e ajustá-la. Dá o melhor resultado e continua sendo o processo dos modelos de maior receita, mas não escala para todos.

O segundo é o compute. Cada tentativa de adaptação exige uma rodada de treino, e o orçamento é finito. A pergunta é quais técnicas testar e como percorrer o espaço de configurações sem gastar o orçamento em tentativas de ganho baixo.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/>

## A base: templates padronizados

Antes dos agentes, a Meta padronizou o desenho dos modelos em blocos reutilizáveis (Standard Model Templates, SMT). Uma técnica validada uma vez no template se propaga automaticamente para todo modelo construído a partir dele.

Em 2 anos, a padronização e a automação entregaram 5.000+ combinações técnica-modelo e reduziram em 92% o tempo de engenharia por modelo.

Sobrou o que exige juízo: qual técnica vale para qual modelo, quão ampla deve ser a busca de hiperparâmetros, por que um modelo não mostra ganho e como detectar e resolver falhas.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/>

## As três frentes dos agentes

Os agentes cobrem o caminho do candidato priorizado ao modelo em produção.

- Discovery: mantém uma visão atualizada das técnicas provadas, estima o quanto cada uma pode transferir e gera uma lista de candidatos técnica-modelo ordenada por impacto esperado. Os agentes avaliam a frota inteira de uma vez, e o engenheiro revisa e decide.
- Generalization: adapta uma técnica para modelos para os quais ela não foi desenhada. Em modelos de templates compartilhados, a técnica é generalizada uma vez por template. Nos modelos de maior receita, o agente aprende com as decisões do engenheiro nas primeiras aplicações e propõe e testa adaptações para os demais, com o engenheiro revisando e orientando.
- Adoption: transforma adaptações validadas em modelos em produção, vários ao mesmo tempo. Lança experimentos, gerencia treinos assíncronos de vários dias, monitora convergência, diagnostica e recupera falhas e monta as propostas.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/>

## Como os agentes decidem

Os agentes combinam raciocínio de LLM com ferramentas especializadas de ML para decidir quais adaptações tentar, diagnosticar falhas e mitigá-las automaticamente e navegar os espaços de busca de hiperparâmetros.

Todos compartilham uma base de conhecimento: o registro acumulado de rodadas de treino anteriores, arquiteturas de modelo e resultados de técnicas. Assim partem do que já foi aprendido. Com milhões de rodadas anteriores como referência, começam pelas configurações com mais chance de funcionar, usam cada rodada para estreitar a busca da seguinte e decidem quais experimentos interromper cedo.

Quando há falha, seja de infraestrutura, divergência de treino ou erro no pipeline de dados, a depuração integrada identifica a causa raiz e aplica correções ou novas tentativas.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/>

## Resultados medidos

Comparado ao mesmo trabalho antes dos agentes, os primeiros resultados mostram:

- 3x mais produtividade de engenharia. Antes, cada engenheiro acompanhava rodadas, tratava falhas à mão e reiniciava, o que limitava cada um a poucos modelos. Agora a supervisão fica nos pontos de decisão: aprovar planos e definir prioridades.
- Redução mediana de 4x no compute de treino, em combinações técnica-modelo selecionadas.
- US$45M+ de economia estimada em compute até o fim do ano.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/ai-agents-to-scale-ml-innovations-across-ads-ranking-models/>

## Além do vídeo

- Exemplos de técnicas propagadas: camadas de fatoração Wukong e redes de interação Interformer.
- Nos modelos de templates, os agentes propõem hipóteses de otimização do template, lançam experimentos em conjuntos representativos de modelos e iteram em várias rodadas. Validar no template custa uma fração do compute de adaptar cada modelo.
- Na adoção, um loop de auto-research busca sobre o template para ajustar cada modelo, e nas técnicas aplicadas individualmente os agentes buscam a melhor combinação de pacotes de técnicas.
- Gestão de capacidade: com centenas de fluxos rodando ao mesmo tempo, os agentes ordenam os jobs por importância de receita, potencial da técnica e proximidade do prazo, e recuperam capacidade de execuções paradas ou de baixo valor. Esse é o foco atual de investimento da Meta.
- O texto de origem é o post oficial da Meta, com autoria de uma equipe de engenharia, que dá continuidade a uma série sobre o Ranking Engineer Agent (REA).
