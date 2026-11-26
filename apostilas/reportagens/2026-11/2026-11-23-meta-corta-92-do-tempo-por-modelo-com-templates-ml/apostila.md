# Meta corta 92% do tempo por modelo com templates ML

_2026-11-23 · reportagem_

A Meta reduziu em 92% o tempo de engenharia por modelo em dois anos ao organizar designs independentes em um pequeno conjunto de Standard Model Templates (SMT). Esta apostila explica como templates compartilhados reduzem o custo de propagar técnicas, como a otimização multi-modelo separa ganhos consistentes de regressões e por que essa estrutura ajuda agentes de ML. Você vai entender os números anunciados, os recortes de cada resultado e os limites do que eles permitem concluir. Ao final, terá um fluxo para agrupar modelos semelhantes, avaliar técnicas em modelos representativos e retidos e planejar a adoção de melhorias.

## O fato

Em 18 de novembro de 2026, a Meta publicou Design Once, Deploy at Scale: Building a Template-Driven ML Ecosystem. A empresa descreve uma mudança no desenvolvimento de modelos de ranking de anúncios. Modelos semelhantes passaram a ser organizados em poucos templates reutilizáveis, com arquitetura, features, treinamento e serving compartilhados.

Em dois anos, a Meta relatou uma redução de 92% no tempo de engenharia por modelo. Também relatou mais de 5.000 combinações técnica-modelo e 80 técnicas novas de ML no fluxo de otimização. O anúncio apresenta a padronização como uma escolha arquitetural para fazer um ecossistema grande de ML aprender mais rápido.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/design-once-deploy-at-scale-template-driven-ml-ecosystem/>

## O contexto: por que a propagação virou o gargalo

Os sistemas de ranking de anúncios da Meta processam bilhões de requisições por dia. Eles atendem produtos diferentes e objetivos de otimização variados. Os modelos de recomendação estimam respostas como cliques, conversões e outros eventos que orientam a operação da plataforma.

Cada produto ou objetivo pode exigir ajustes próprios. Com o crescimento da frota, aumentaram as diferenças de arquitetura, features, configurações de treinamento, restrições de serving e lógica específica de plataforma. Uma técnica que funciona em um modelo precisa ser adaptada e testada nos demais antes de gerar impacto em larga escala.

Nesse cenário, o desafário passou a ser levar ideias comprovadas para todos os modelos aos quais elas se aplicam. Uma arquitetura nova pode começar em um modelo e demorar anos para alcançar o restante do ecossistema. Uma migração de plataforma pode funcionar em uma família de modelos e falhar em configurações especializadas. O custo de propagação pode superar o custo da própria inovação.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/design-once-deploy-at-scale-template-driven-ml-ecosystem/>

## Por que a fragmentação custa caro

A diversidade de modelos dá flexibilidade, mas cria três problemas sistêmicos. O primeiro é o alto custo de engenharia para espalhar uma ideia por muitos modelos. O segundo é o custo de confiabilidade causado pela multiplicação de casos extremos. O terceiro é a baixa previsibilidade do impacto de uma mudança em todo o ecossistema.

Quando cada modelo tem uma estrutura diferente, um ajuste de treinamento não oferece muitas pistas sobre o próximo modelo. Uma falha de serving também precisa ser investigada em um contexto novo. A equipe precisa conhecer cada combinação de componentes antes de decidir se uma melhoria pode ser propagada.

A fragmentação ainda enfraquece a automação. Sistemas de AutoML e otimização trabalham melhor em espaços estruturados. Se cada modelo tem uma forma própria, as técnicas de maior potencial alcançam apenas uma parte da frota. A Meta começou reduzindo a complexidade antes de acrescentar outra camada de automação.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/design-once-deploy-at-scale-template-driven-ml-ecosystem/>

## Standard Model Templates: a unidade compartilhada

Um Standard Model Template, ou SMT, é uma configuração mínima e opinativa de modelo construída com componentes compartilhados. Opinativo significa que o template já traz escolhas consideradas adequadas para um padrão de modelo. Ele reduz a liberdade desnecessária e oferece um ponto de partida consistente.

Modelos semelhantes são agrupados em torno de um número menor de templates. As partes comuns ficam explícitas e compartilhadas. A lógica específica de cada modelo continua existindo onde é necessária, mas ela deixa de definir tudo o que pode ser reutilizado.

O template funciona como uma camada comum entre a pesquisa de técnicas e os modelos de produção. Uma melhoria incorporada a ele pode alcançar todos os modelos construídos sobre aquela estrutura. A unidade de trabalho passa do modelo isolado para o grupo de modelos que compartilha o template.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/design-once-deploy-at-scale-template-driven-ml-ecosystem/>

## O que existe dentro de um template

Os templates da Meta cobrem padrões importantes de ranking e recuperação, com diferentes tamanhos de modelo. Eles reúnem componentes para seleção de features, interação entre features, paralelismo de modelo, configuração de treinamento e serving consciente do hardware. Também incluem escolhas de arquitetura e configurações de infraestrutura usadas para servir os modelos.

Cada componente resolve uma parte do problema. A seleção de features define quais informações entram no modelo. A interação entre features permite combinar sinais. O paralelismo distribui o trabalho do modelo entre recursos. O serving consciente do hardware ajusta a operação ao ambiente onde o modelo será executado.

Compartilhar esses componentes permite concentrar validações, proteções e fluxos de depuração. Uma instabilidade de treinamento ou uma regressão de serving passa a acontecer dentro de uma estrutura conhecida. A equipe pode reutilizar o diagnóstico e aplicar a correção em vários modelos.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/design-once-deploy-at-scale-template-driven-ml-ecosystem/>

## A mudança da otimização por modelo para a otimização por template

Antes dos SMTs, uma técnica era ajustada manualmente em cada modelo. Com os templates, a avaliação acontece em um conjunto menor de modelos representativos. A ideia é descobrir se a melhoria funciona no padrão compartilhado e depois levá-la aos grupos de modelos que usam esse template.

O estudo descreve a redução da complexidade de propagação de O(n·k) para O(n+k). Na expressão, n é o número de modelos e k é o número de técnicas. A notação mostra como o trabalho cresce com o tamanho do problema. Ela não mede horas, qualidade ou custo financeiro.

Uma implementação compartilhada reduz o esforço para distribuir uma ideia. Menos configurações únicas também tornam as validações e a depuração mais previsíveis. Quando os modelos de um grupo compartilham a mesma base, o desempenho dos representativos oferece um sinal mais útil para planejar o impacto no restante do grupo.

Fonte: <https://arxiv.org/abs/2603.24963>

## Transferência de designs e decisões de escala

Muitos ganhos em ML vêm da combinação entre arquitetura, decisões de escala e estratégias de treinamento. Aplicar componentes isolados pode deixar parte desse efeito de fora. A Meta passou a transferir designs completos de modelos fonte fortes para famílias de modelos de destino por meio da camada compartilhada de templates.

Essa transferência muda o objeto da otimização. O fluxo procura um conjunto de escolhas que funcione bem em modelos representativos. Depois da validação, o design aprovado entra na próxima versão do template e chega aos modelos construídos sobre ele.

A estrutura padronizada também tornou as decisões de escala mais reutilizáveis. Em vez de redescobrir compensações entre custo e desempenho para cada modelo, a equipe aprende essas relações no espaço dos templates. Isso apoia fluxos baseados em leis de escala e uma alocação de recursos menos improvisada.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/design-once-deploy-at-scale-template-driven-ml-ecosystem/>

## Otimização multi-modelo: do candidato à próxima versão

A otimização multi-modelo avalia técnicas candidatas em modelos representativos. O objetivo é encontrar configurações que melhorem o desempenho agregado e limitem regressões. O resultado médio importa, mas a frequência de modelos que pioram também entra na decisão.

Uma técnica com ganho médio alto e regressões frequentes é difícil de distribuir em uma frota grande. Consistência pesa tanto quanto o melhor resultado individual. O fluxo considera o conjunto de modelos avaliados para decidir se o candidato está pronto para integração.

Depois da otimização, a técnica passa pela validação em modelos retidos, que ficaram fora do conjunto representativo. Esse passo verifica se o ganho ultrapassa os representativos. As técnicas aprovadas entram na próxima versão do template. Em dois anos, a Meta enviou 80 técnicas novas por esse fluxo.

O efeito se acumula porque cada modelo que adota um template maduro herda um histórico de melhorias generalizadas. Ele não parte de uma base isolada sempre que uma nova ideia aparece.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/design-once-deploy-at-scale-template-driven-ml-ecosystem/>

## Como funciona na prática

Imagine que um grupo de modelos de ranking tenha objetivos de otimização diferentes, mas compartilhe padrões de arquitetura, features e serving. Esses modelos podem usar um template comum. A lógica específica de cada objetivo permanece no modelo, enquanto as partes repetidas ficam na camada compartilhada.

Uma técnica candidata é avaliada nos modelos representativos desse grupo. O fluxo mede o ganho agregado e a taxa de regressão. Se a técnica mantiver um resultado consistente, ela segue para os modelos retidos. A validação nesse segundo conjunto verifica se a melhoria se transfere para além dos modelos usados na busca.

Com a aprovação, a técnica é incorporada à próxima versão do template. Os modelos do grupo passam a poder herdar essa mudança sem exigir uma adaptação completa e isolada para cada um. O exemplo termina no ponto em que a melhoria deixa de ser uma descoberta local e se torna uma atualização compartilhada.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/design-once-deploy-at-scale-template-driven-ml-ecosystem/>

## Os números anunciados pela Meta

A Meta resume os resultados de dois anos de trabalho no ecossistema de ranking de anúncios. Os números descrevem esforço de engenharia, volume de adoção, qualidade offline, resultado online e cobertura da frota. Cada um mede uma parte diferente do sistema.

- 92%: redução do tempo de engenharia por modelo ao longo de dois anos. É um resultado de esforço de engenharia e não mede qualidade, receita ou custo total.
- Mais de 5.000 combinações técnica-modelo: total de pares enviados pelo fluxo. Uma técnica aplicada a vários modelos gera várias combinações, portanto esse valor não representa 5.000 técnicas diferentes.
- 80 técnicas novas de ML: quantidade de técnicas incorporadas pelo fluxo em dois anos. É uma contagem de técnicas, distinta da contagem de pares técnica-modelo.
- 0,63%: melhoria média da qualidade offline com capacidade de serving neutra. É uma média do recorte anunciado e não um ganho garantido para cada modelo nem pontos percentuais de acerto.
- 0,86%: lift online acumulado. É um ganho em métrica online no recorte da Meta, associado a uma cobertura de 70% dos modelos por contagem; o post não o apresenta como receita nem como resultado idêntico em todos os produtos.
- 70%: cobertura dos modelos por contagem, informada junto do lift online acumulado de 0,86%. O valor não indica 70% do tráfego, da receita ou do impacto total.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/design-once-deploy-at-scale-template-driven-ml-ecosystem/>

## Os números do estudo no arXiv

O estudo Template-Driven Machine Learning Standardization for Large Model Fleets traz outro recorte. O resumo do artigo relata resultados de cinco ciclos globais de desenvolvimento no ecossistema de produção de ranking de anúncios da Meta.

Os valores do artigo e os do post oficial pertencem a métricas e recortes próprios. Eles não devem ser somados nem tratados como se fossem a mesma medida.

- Cinco ciclos globais de desenvolvimento: período de avaliação descrito no estudo. É o recorte usado para os resultados relatados no resumo.
- 0,77%: melhoria média em cross-entropy com capacidade de serving neutra. Como cross-entropy mede erro de previsão, a melhoria indica redução desse erro. O valor não é 0,77 ponto percentual de acerto.
- 1,52%: lift acumulado em métrica online no estudo. O resultado tem fonte e recorte próprios e não deve ser substituído pelo 0,86% anunciado no post da Meta.
- 92%: redução do tempo de engenharia de iteração por modelo. O estudo também reporta esse percentual dentro de sua avaliação.
- 6,3 vezes: fator de aumento reportado na vazão de adoção de pares técnica-modelo. Ele descreve throughput de adoções e não é um multiplicador de qualidade ou receita.

Fonte: <https://arxiv.org/abs/2603.24963>

## Linha do tempo

O estudo passou por atualizações antes da publicação do post oficial da Meta. As datas abaixo situam o artigo e o período de resultados sem misturar os dois recortes.

- 26 de março de 2026: a primeira versão do estudo foi submetida ao arXiv.
- Ao longo de dois anos: a Meta desenvolveu e aplicou o fluxo de templates que resultou na redução de 92% do tempo de engenharia por modelo e no envio de mais de 5.000 combinações técnica-modelo.
- 15 de novembro de 2026: o estudo teve a versão v4 revisada.
- Cinco ciclos globais de desenvolvimento: recorte da avaliação descrita no resumo do artigo no arXiv.

Fonte: <https://arxiv.org/abs/2603.24963>

## Templates como base para agentes de ML

Um agente de ML pode receber ferramentas, pipelines de treinamento e resultados de avaliação para explorar um espaço grande de designs. Sem um conhecimento prévio forte, ele pode gastar esforço em regiões improdutivas, recuperar-se de falhas evitáveis ou propor mudanças difíceis de explicar e colocar em produção.

Os SMTs armazenam padrões de design já validados. Eles dão ao agente um ponto de partida estruturado, limitam o espaço de busca e estabelecem um piso de qualidade. A construção do modelo deixa de ser uma busca totalmente livre e passa a ser dividida em subproblemas mais específicos.

Na Meta, os agentes atuam no nível dos templates. Eles propõem ideias baseadas em técnicas comprovadas, executam experimentos em modelos representativos, diagnosticam falhas e iteram por várias rodadas. Também podem assumir tarefas mais difíceis, como migrar modelos para novas plataformas de hardware.

Uma técnica validada nesse fluxo alcança todos os modelos construídos sobre o template. Segundo a Meta, isso exige uma fração do compute que seria necessário para adaptar cada modelo separadamente.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/design-once-deploy-at-scale-template-driven-ml-ecosystem/>

## Quem ganha e quem perde

Os modelos construídos sobre um template maduro herdam melhorias que já passaram pelo fluxo de avaliação. Os times ganham uma forma compartilhada de propagar técnicas e depurar falhas. Os agentes ganham um espaço de busca menor e padrões conhecidos para começar o trabalho.

A contrapartida aparece para os designs independentes. Eles exigem adaptação e validação próprias a cada mudança. A padronização também reduz a liberdade irrestrita de arquitetura, mas preserva a flexibilidade necessária para a lógica específica do modelo.

Esse equilíbrio define o sucesso do template. Um sistema que tenta acomodar todos os casos extremos históricos acaba recriando a fragmentação que deveria eliminar. O template precisa remover diversidade desnecessária e manter apenas as diferenças que importam.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/design-once-deploy-at-scale-template-driven-ml-ecosystem/>

## O que ainda não se sabe

A Meta aponta trabalho pela frente na cobertura dos templates e no fortalecimento da otimização baseada em leis de escala. O plano de desenvolvimento também inclui fluxos mais completos com agentes para construção de templates, geração de modelos, avaliação online e otimização contínua a partir de sinais online.

Confiabilidade e capacidade de explicação seguem como objetivos desse trabalho. Um resultado médio forte não elimina a necessidade de observar regressões. Um espaço de busca limitado também precisa preservar a flexibilidade que realmente afeta o modelo.

Os resultados publicados pertencem ao ecossistema de ranking de anúncios da Meta e aos recortes descritos. Aplicar a mesma conclusão a outro contexto exige avaliação própria. A leitura correta dos números depende de identificar a fonte, a métrica, o período e a unidade de cobertura.

- Fonte do número: identifique se ele vem do post da Meta ou do estudo no arXiv antes de comparar resultados.
- Momento da medição: qualidade offline e lift online descrevem estágios diferentes e não devem ser tratados como a mesma métrica.
- Unidade do percentual: confira se o valor é uma melhoria percentual da métrica ou pontos percentuais antes de interpretar o tamanho do efeito.
- Cobertura: o indicador de 70% é por contagem de modelos e não representa participação de tráfego ou receita.
- Validação: verifique se a técnica passou pelos modelos representativos e pelos modelos retidos antes de considerá-la pronta para propagação.
- Flexibilidade do template: observe se ele acomoda apenas as diferenças necessárias ou começa a reconstruir a fragmentação com casos extremos.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/design-once-deploy-at-scale-template-driven-ml-ecosystem/>

## O que você pode fazer

A lógica dos SMTs pode orientar a organização de um ecossistema com vários modelos. O fluxo abaixo usa as etapas descritas pela Meta e termina com a propagação de uma técnica aprovada.

1. No inventário de modelos, registre arquitetura, features, treinamento, serving e lógica específica de plataforma. O resultado será um mapa das semelhanças e diferenças que justificam cada configuração.
2. No agrupamento, reúna modelos semelhantes por padrões de ranking e recuperação. O resultado será um conjunto de grupos candidatos a compartilhar templates.
3. No desenho do template, defina uma configuração mínima e opinativa com os componentes comuns explícitos. O resultado será uma base reutilizável para o grupo.
4. Na revisão do escopo, preserve a lógica específica que realmente muda o comportamento do modelo. O resultado será um template que reduz diversidade sem forçar todos os modelos a uma estrutura idêntica.
5. Na preparação da avaliação, escolha modelos representativos e reserve modelos retidos fora do conjunto representativo. O resultado será uma forma de medir desempenho e verificar transferência.
6. Na avaliação do candidato, meça o ganho agregado e a taxa de regressão nos representativos. O resultado será uma decisão baseada na consistência do grupo, além do melhor resultado individual.
7. Na validação, aplique a técnica aos modelos retidos. O resultado será a evidência de que o ganho ultrapassa o conjunto usado na busca.
8. Na próxima versão do template, incorpore as técnicas aprovadas e propague a atualização ao grupo. O resultado será uma melhoria compartilhada que os modelos do template podem herdar.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/design-once-deploy-at-scale-template-driven-ml-ecosystem/>

## Glossário

- ML: aprendizado de máquina, área que treina modelos para reconhecer padrões e fazer previsões a partir de dados.
- Ranking de anúncios: processo que ordena anúncios ou itens para uma requisição usando previsões e objetivos de otimização.
- Recuperação: etapa que seleciona um conjunto de candidatos antes da ordenação final.
- Template e SMT: configuração reutilizável de modelo. SMT significa Standard Model Template, o nome do padrão usado pela Meta.
- Arquitetura de modelo: organização dos componentes e das conexões que definem como o modelo processa informações.
- Feature: característica ou variável de entrada usada pelo modelo para fazer uma previsão.
- Interação de features: combinação de sinais de entrada para que o modelo considere relações entre eles.
- Treinamento: processo de ajuste do modelo usando dados e um objetivo de aprendizado.
- Serving: etapa em que o modelo treinado recebe requisições e produz respostas em operação.
- Paralelismo de modelo: divisão do trabalho do modelo entre recursos de computação.
- Serving consciente do hardware: configuração da operação que considera as características do hardware disponível.
- Modelo representativo: modelo escolhido para avaliar uma técnica em nome de um grupo com características compartilhadas.
- Modelo retido: modelo reservado para validar se um resultado encontrado no conjunto representativo se transfere para outros modelos.
- Ganho agregado: resultado combinado da avaliação de uma técnica em vários modelos.
- Taxa de regressão: frequência com que uma mudança piora o desempenho nos casos avaliados.
- Qualidade offline: desempenho do modelo medido fora da operação online, usando dados e métricas de avaliação.
- Lift online: melhoria medida por uma métrica de produção durante a operação online.
- Capacidade de serving neutra: comparação feita com a capacidade de servir modelos mantida como referência comum.
- Cross-entropy: medida de erro usada em previsões probabilísticas. Valores menores indicam melhor ajuste.
- Combinação técnica-modelo: par formado por uma técnica e um modelo no qual ela foi adotada.
- Propagação de técnicas: processo de levar uma melhoria validada para os modelos aos quais ela se aplica.
- Otimização multi-modelo: avaliação de candidatos em vários modelos para buscar ganho agregado e controlar regressões.
- AutoML: automação de partes do processo de construção e ajuste de modelos de ML.
- Lei de escala: relação entre o aumento de recursos ou dimensões e o desempenho ou custo do modelo.
- Notação Big O: forma matemática de descrever como um trabalho cresce com o tamanho da entrada.
- Agente de ML: sistema de IA que usa ferramentas e resultados para propor, executar e revisar tarefas de desenvolvimento de modelos.
- Espaço de busca: conjunto de escolhas e configurações que um processo de otimização pode explorar.
- Piso de qualidade: nível mínimo de desempenho oferecido por padrões já validados.
- Throughput: quantidade de trabalho processada em um intervalo de tempo.
- Caso extremo: configuração especial ou incomum que pode exigir tratamento próprio.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/design-once-deploy-at-scale-template-driven-ml-ecosystem/>

## Para onde ir depois

O próximo passo é aplicar o mapeamento a um grupo de modelos que você já conhece. Identifique as partes repetidas, escolha representantes e separe modelos para validação antes de propor uma propagação.

- Leia o post oficial Design Once, Deploy at Scale: Building a Template-Driven ML Ecosystem para revisar o fluxo dos SMTs.
- Leia o estudo Template-Driven Machine Learning Standardization for Large Model Fleets no arXiv para acompanhar o recorte de cinco ciclos e as métricas do artigo.
- Leia How Meta Uses AI Agents to Scale ML Innovations Across Ads Ranking Models para entender o uso de agentes no desenvolvimento dos templates.
- Pratique o desenho de um template para um grupo de modelos semelhantes, registrando quais componentes podem ser compartilhados e quais diferenças precisam permanecer.
- Antes da próxima propagação, escreva quais modelos serão representativos, quais ficarão retidos e como você medirá ganho agregado e regressões.
- Ao revisar um resultado, anote a fonte, a métrica, o período e a unidade de cobertura para evitar comparações entre recortes diferentes.

Fonte: <https://engineering.fb.com/2026/11/18/ml-applications/design-once-deploy-at-scale-template-driven-ml-ecosystem/>
