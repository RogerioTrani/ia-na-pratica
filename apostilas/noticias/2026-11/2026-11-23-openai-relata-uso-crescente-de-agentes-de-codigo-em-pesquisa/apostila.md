# OpenAI relata uso crescente de agentes de código em pesquisa

_2026-11-23 · noticia_

A OpenAI divulgou um retrato interno de como agentes de código vêm mudando a pesquisa em IA da empresa. Em tarefas estimadas de duas a quatro horas, a taxa de conclusão sem intervenção humana subiu de 23% em março para 46% em outubro de 2026. O avanço varia conforme o tipo de trabalho, e os pesquisadores que mais usam agentes ampliaram sua vantagem de uso. Ao ler esta apostila, você saberá interpretar essas taxas, comparar diferentes tarefas e aplicar as mesmas lentes de medição no seu fluxo, mantendo as pessoas na supervisão e na definição das prioridades de segurança.

## O fato

Em 18 de novembro de 2026, a OpenAI publicou Research acceleration: The jagged frontier, uma atualização sobre a aceleração da pesquisa em IA dentro da própria empresa. O relatório usa medições internas para mostrar como agentes de código vêm alterando o ciclo de desenvolvimento de IA.

O resultado principal é que agentes concluem quase metade das tarefas estimadas em duas a quatro horas sem intervenção humana. De março a outubro de 2026, essa taxa passou de 23% para 46%. A empresa também afirma que as pessoas continuam centrais no desenvolvimento de IA.

O recorte importa: são dados da OpenAI sobre a operação dela. O relatório oferece uma visão detalhada, ainda parcial, desse processo, e não funciona como um teste independente de todos os agentes disponíveis.

Fonte: <https://openai.com/index/research-acceleration-jagged-frontier/>

## Por que isso importa

Pesquisa em IA combina dados, ferramentas como agentes de código, trabalho humano e compute. O agente atua como um insumo: recebe tarefas e pode executar parte do trabalho de desenvolvimento. Quando essas tarefas avançam, o ciclo de pesquisa pode mudar, mas a velocidade de uma tarefa não mede sozinha a melhoria do modelo final.

O título fala em uma fronteira irregular porque o avanço não aparece igual em toda função. Monitorar uma execução de treinamento e escrever código para a infraestrutura de inferência exigem capacidades diferentes. Uma taxa média precisa ser lida junto com o tipo de trabalho.

O assunto também envolve governança. A OpenAI define autoaperfeiçoamento recursivo, ou RSI, como o processo pelo qual a IA acelera o desenvolvimento de futuros sistemas de IA. Ela defende que laboratórios de IA sejam obrigados a acompanhar e divulgar publicamente indicadores desse processo, diz que manter a supervisão humana exigirá resolver novas questões técnicas e de governança e afirma que o relatório não expressa intenção de buscar RSI completo.

Fonte: <https://openai.com/index/research-acceleration-jagged-frontier/>

## Como ler o relatório

O texto organiza a pesquisa em três lentes. Insumos são o que entra no trabalho, como dados, agentes, pessoas e compute. Processo é a maneira como pesquisadores transformam esses insumos em capacidades de modelo. Resultados são as melhorias observadas nessas capacidades. Separar as três lentes ajuda a entender onde cada número atua.

A primeira parte mede intensidade de uso, inclusive gasto equivalente em API, dias de trabalho de agente e uso simultâneo. A segunda observa tarefas delegadas, taxas de sucesso e participação humana. A terceira trata das capacidades produzidas. Como o foco do relatório são agentes de código, as conclusões não cobrem sozinhas todos os insumos da pesquisa.

Ao comparar períodos, vale preservar o recorte de cada medida. Gasto em API reflete atividade e escolhas de modelos; tempo de agente reflete tempo de execução; sucesso sem intervenção mede conclusão autônoma. São sinais diferentes, e um não substitui o outro.

Fonte: <https://openai.com/index/research-acceleration-jagged-frontier/>

## Autonomia cresce, mas varia com a duração

Uma tarefa estimada em duas a quatro horas tinha taxa de sucesso sem intervenção humana de 23% em março e 46% em outubro de 2026. Para tarefas estimadas em quatro a oito horas, a taxa passou de 13% para 35% no mesmo período. Os 46% representam quase metade daquele grupo específico de tarefas, e não quase metade de qualquer trabalho de pesquisa.

Sucesso sem intervenção humana significa que o agente chegou ao fim da tarefa sem ajuda humana naquela execução. A estimativa de duração vem do trabalho humano que a tarefa exigiria. Ela organiza a comparação, mas não garante que o conjunto de tarefas seja idêntico entre março e outubro.

A própria OpenAI alerta para essa mudança de composição. Pesquisadores podem ter passado a delegar tarefas diferentes dentro da mesma faixa de duração. O aumento da taxa pode refletir agentes mais capazes, escolhas diferentes de tarefas ou os dois fatores juntos.

Fonte: <https://openai.com/index/research-acceleration-jagged-frontier/>

## O tipo de tarefa muda o resultado

De 1º de agosto a 18 de outubro de 2026, a taxa estimada de sucesso sem intervenção humana foi de 69% em Communicate, 58% em Analyze e 43% em Build. A divisão usa a taxonomia O*NET AI R&D. Em português, as categorias cobrem comunicação, análise e construção, mas os números pertencem a essa classificação específica.

No nível das tarefas, monitorar execuções de treinamento para encontrar problemas alcançou 79%, e responder perguntas técnicas chegou a 72%. Lançar execuções de treinamento ficou em 35%. Escrever código para as pilhas de inferência e de serviço de modelos (serving) teve 25%, enquanto construir ambientes de avaliação, aprendizado por reforço e agentes teve 29%.

Esses resultados explicam a ideia de fronteira irregular. Um agente pode ter desempenho alto em uma rotina de observação e enfrentar mais dificuldade em outra que envolve construir ou alterar infraestrutura. Na hora de delegar, o tipo de trabalho é tão importante quanto a duração estimada.

Fonte: <https://openai.com/index/research-acceleration-jagged-frontier/>

## O uso de agentes disparou

Em outubro de 2026, o pesquisador mediano da OpenAI usava cerca de US$ 2.400 por dia em ferramentas de IA agentic, considerando preços de tabela da API. Em setembro, o valor era US$ 1.500, com aumento informado de 62%. No percentil 90, o uso diário chegou a US$ 23.000, ante US$ 11.000 em setembro, um aumento de 105%.

O percentil 90 reúne o grupo de maior uso: 90% dos pesquisadores incluídos ficam abaixo dessa marca. A diferença entre o mediano e esse grupo mostra que a adoção cresceu de forma desigual. Os usuários mais intensos ampliaram sua vantagem de uso.

Esse gasto é uma medida aproximada de intensidade, e não um total fechado de custos. A OpenAI diz que a variação pode combinar mais atividade, modelos mais caros e mudanças no comportamento dos modelos e nos agentic harnesses, a estrutura que organiza a execução dos agentes. O aumento do valor não pode ser lido apenas como mais tarefas concluídas.

Fonte: <https://openai.com/index/research-acceleration-jagged-frontier/>

## Tempo de agente e execução simultânea

Para medir o tempo de trabalho, a OpenAI define um dia de trabalho de agente como oito horas de uso. A média passou de 0,5 para 5,7 dias de trabalho de agente por pesquisador, um aumento de onze vezes. O maior aumento ocorreu nas equipes de pré-treinamento e pós-treinamento, onde o tempo médio ficou em cerca de oito dias de trabalho de agente por pesquisador por dia calendário. Em escalonamento e infraestrutura, a média ficou em cerca de quatro.

Esse indicador captura melhor o tempo decorrido em que os agentes trabalham do que o valor gasto. Ele não separa mudanças de capacidade nem de preço. A empresa também observa que a medida inclui, em geral, apenas uso interativo, então pode deixar de fora automações.

Em meados de outubro, mais de dois terços dos pesquisadores incluídos atingiram um pico médio diário de pelo menos quatro agentes simultâneos. Mais de 10% atingiram pelo menos dezesseis. O uso de vários agentes passa a ser parte da operação, e a coordenação humana continua presente no processo descrito.

Fonte: <https://openai.com/index/research-acceleration-jagged-frontier/>

## Pessoas seguem no centro

O relatório não apresenta os agentes como substitutos automáticos das equipes. A produtividade depende de reorganizar o trabalho: os pesquisadores escolhem o que delegar, supervisionam e coordenam os agentes e decidem quais projetos seguir. Essas decisões humanas também podem mudar as tarefas que entram em cada medição.

Uma pesquisa reforça o valor atribuído às ferramentas. Perguntados sobre o que trocariam para manter agentes de código de fronteira por três meses, os respondentes deram como mediana 30% do compute da equipe ou, em uma pergunta separada, 40% do número de pessoas da equipe. O resultado é uma declaração de preferência em um cenário hipotético, e não uma redução efetiva de custos ou de equipes.

Em setembro de 2026, o valor equivalente em API do uso de agentes na organização de pesquisa era cerca de duas vezes a compensação sem ações dos pesquisadores. A proporção exclui equity, que geralmente representa de 70% a 80% da compensação-alvo. Ainda assim, o uso interno, que combina Codex, ChatGPT e API, respondeu por apenas 2% do compute total de pesquisa. Os números mostram uma mudança na alocação de recursos sem apagar a participação humana.

Fonte: <https://openai.com/index/research-acceleration-jagged-frontier/>

## Segurança e alinhamento ganharam mais esforço

Segurança e Alinhamento teve o maior aumento absoluto de esforço documentado entre as grandes áreas de pesquisa da OpenAI. As semanas de trabalho documentadas cresceram 77% de janeiro a setembro de 2026. O crescimento veio de novas contratações e de pesquisadores existentes que passaram a dedicar mais atenção a esses projetos.

A área inclui trabalhos como avaliações de alinhamento, monitorabilidade e pesquisa sobre reward hacking. O relatório identifica uma inflexão após o incidente com o Hugging Face em julho de 2026 e o trabalho da OpenAI para desenvolver e melhorar casos de segurança para treinamentos de IA de fronteira.

A medição usa contribuições dos pesquisadores em publicações no Slack abertas a toda a empresa, pull requests e documentos internos de janeiro a setembro. Classificadores agrupam as contribuições por área, e cada semana de um pesquisador é dividida igualmente entre seus projetos verificados. Isso cria uma aproximação da atenção dedicada, sem equivaler às linhas formais de equipe. A distinção entre pós-treinamento e segurança e alinhamento é complexa, e a empresa pode ajustar a definição.

Fonte: <https://openai.com/index/research-acceleration-jagged-frontier/>

## Os números

Todos os valores abaixo foram divulgados pela OpenAI. Cada um mantém o grupo, o período e a medida que lhe dão sentido.

- 23% para 46%: taxa estimada de sucesso sem intervenção humana em tarefas de duas a quatro horas, de março a outubro de 2026.
- 13% para 35%: mesma medida para tarefas de quatro a oito horas.
- 69%, 58% e 43%: sucesso estimado sem intervenção em Communicate, Analyze e Build, de 1º de agosto a 18 de outubro de 2026.
- 79% e 72%: sucesso estimado ao monitorar execuções e responder perguntas técnicas; 35% para lançar execuções.
- 25% e 29%: sucesso estimado ao escrever código de inferência e de serviço de modelos e ao construir ambientes de avaliação, aprendizado por reforço e agentes.
- US$ 2.400 por dia: uso mediano em outubro de 2026, a preços de tabela da API; alta de 62% sobre US$ 1.500 em setembro.
- US$ 23.000 por dia: uso no percentil 90 em outubro; alta de 105% sobre US$ 11.000 em setembro.
- 0,5 para 5,7: dias de trabalho de agente por pesquisador, com oito horas de uso por dia de agente.
- Cerca de oito e quatro: média de dias de trabalho de agente por pesquisador por dia calendário em pré-treinamento e pós-treinamento e em escalonamento e infraestrutura, respectivamente.
- Mais de dois terços e mais de 10%: pesquisadores com pico médio diário de pelo menos quatro e dezesseis agentes simultâneos em meados de outubro.
- Cerca de duas vezes: valor equivalente em API do uso de agentes em relação à compensação sem ações em setembro de 2026.
- 2%: participação do uso interno com Codex, ChatGPT e API no compute total de pesquisa.
- 77%: crescimento das semanas de trabalho documentadas em Segurança e Alinhamento de janeiro a setembro de 2026.
- 30% ou 40%: mediana do compute ou do número de pessoas que pesquisadores trocariam para manter agentes de código de fronteira por três meses, em perguntas separadas.

Fonte: <https://openai.com/index/research-acceleration-jagged-frontier/>

## O que muda para você

Exemplo: imagine que uma equipe precise monitorar execuções de treinamento e também escrever código para a infraestrutura de inferência. O relatório registra 79% de sucesso sem intervenção para a primeira atividade e 25% para a segunda. Uma decisão útil é medir e delegar os dois fluxos separadamente, em vez de tratar a pesquisa como um bloco único.

Para o leitor, a mudança prática é olhar a tarefa antes do agente. Duração estimada, categoria e necessidade de intervenção ajudam a formar uma expectativa realista. O aumento do uso também pede acompanhar quanto tempo os agentes trabalham, quantos operam ao mesmo tempo e qual é o gasto equivalente em API.

A supervisão humana aparece na definição do trabalho, na coordenação das execuções e nas prioridades de segurança. Cada equipe pode usar essas perguntas e medidas para avaliar o próprio fluxo, preservando o contexto de cada resultado.

Fonte: <https://openai.com/index/research-acceleration-jagged-frontier/>

## O que fazer hoje

Use as lentes do relatório para montar um registro simples do seu fluxo. O objetivo é comparar trabalho semelhante e enxergar onde a intervenção humana ainda acontece.

1. Em uma planilha, liste as tarefas de pesquisa ou desenvolvimento de IA e estime quais exigiriam de duas a quatro horas ou de quatro a oito horas de trabalho humano. O resultado é uma primeira divisão por duração.
2. Na mesma planilha, marque a categoria de cada tarefa, como comunicação, análise ou construção, e o tipo específico, como monitorar uma execução, responder a uma pergunta técnica ou escrever código de inferência. O resultado é um grupo de comparação mais preciso.
3. No registro de cada tarefa delegada a um agente de código, anote se ela terminou sem intervenção humana e em que ponto uma pessoa precisou atuar. O resultado é uma taxa de conclusão autônoma ligada ao tipo de trabalho.
4. No campo de tempo desse registro, anote as horas de uso do agente e converta cada oito horas em um dia de trabalho de agente. O resultado é uma medida de tempo de execução separada do custo.
5. No acompanhamento diário, registre o pico de agentes simultâneos e o gasto equivalente em API. O resultado mostra a intensidade de uso e ajuda a identificar mudanças de modelo ou de estrutura de execução.
6. Na comparação entre períodos, use a mesma faixa de duração e categoria, e anote se o conjunto de tarefas mudou. O resultado evita atribuir toda a melhora à capacidade do agente.
7. No desenho do fluxo, defina onde as pessoas supervisionam, coordenam e revisam o trabalho, incluindo as prioridades de segurança e alinhamento. O resultado é um processo que mantém a decisão humana explícita.

Fonte: <https://openai.com/index/research-acceleration-jagged-frontier/>

## O que conferir

Antes de usar os números para tomar uma decisão, confira o recorte que sustenta cada conclusão.

- Confira a origem: as medidas são internas da OpenAI e descrevem o ciclo de pesquisa da empresa. Elas não representam um resultado médio de todas as equipes que usam agentes.
- Confira duração, categoria, tarefa e período antes de comparar taxas. A melhora dentro de uma faixa pode incluir mudança no tipo de tarefa delegada.
- Separe sucesso sem intervenção de produtividade total. Uma tarefa concluída sozinha não mede, por si só, a capacidade final do modelo.
- Não trate gasto em API como custo total de pesquisa. A medida usa preços de tabela e pode mudar com atividade, preço de modelo e estrutura de execução do agente.
- Não trate dia de trabalho de agente como medida de inteligência. O indicador mede tempo e pode deixar de fora automações.
- Ao comparar agentes e pessoas, lembre que a compensação sem ações exclui equity e que a proporção de gasto não é uma taxa de substituição de pessoal.
- Leia as áreas de pesquisa como aproximação da atenção, e não como organograma. A classificação pode separar pós-treinamento e segurança de maneiras que a empresa ainda pode ajustar.
- Mantenha supervisão humana e requisitos de segurança no fluxo. A própria OpenAI liga a aceleração de pesquisa a questões técnicas e de governança, e diz que o relatório não expressa intenção de buscar RSI completo.

Fonte: <https://openai.com/index/research-acceleration-jagged-frontier/>

## Glossário

Os termos abaixo aparecem no relatório e ajudam a interpretar as medidas sem confundir uma coisa com outra.

- Agente de código: ferramenta de IA que executa tarefas de desenvolvimento, como escrever ou alterar código, dentro de um fluxo de trabalho.
- Agentic harness: estrutura que organiza como o agente executa tarefas e interage com o ambiente.
- API: interface de programação usada para acessar serviços; no relatório, os preços de tabela servem para valorar o uso das ferramentas.
- Sucesso sem intervenção humana: tarefa concluída pelo agente sem ajuda humana na execução medida.
- Dia de trabalho de agente: oito horas de uso do agente.
- Percentil 90: marca em que 90% dos valores ficam abaixo e 10% ficam acima.
- Compute: capacidade de processamento usada na pesquisa e no treinamento de IA.
- Pré-treinamento: fase em que o modelo aprende padrões iniciais a partir de dados.
- Pós-treinamento: ajustes realizados após o treinamento inicial para mudar o comportamento ou o desempenho do modelo.
- Inferência: uso de um modelo treinado para produzir respostas ou resultados.
- Aprendizado por reforço: método de treinamento em que o comportamento é ajustado a partir de recompensas.
- Alinhamento: trabalho voltado a fazer sistemas de IA seguirem objetivos e limites pretendidos.
- Monitorabilidade: capacidade de acompanhar e compreender o que um sistema está fazendo.
- Reward hacking: comportamento que obtém recompensa sem cumprir a intenção da tarefa.
- Autoaperfeiçoamento recursivo (RSI): processo pelo qual a IA acelera o desenvolvimento de futuros sistemas de IA.
- Equity: participação acionária; no relatório, sua exclusão limita a comparação com a compensação total.

Fonte: <https://openai.com/index/research-acceleration-jagged-frontier/>

## Para onde ir depois

Leia o relatório oficial Research acceleration: The jagged frontier para acompanhar os métodos e os recortes por trás dos números. Depois, escolha uma categoria de tarefa do seu trabalho e aplique o registro descrito na seção de passos.

Pratique comparar execuções semelhantes, anotando duração estimada, intervenção humana, tempo de agente e agentes simultâneos. Use o resultado para decidir o próximo ajuste de delegação ou supervisão, preservando o contexto de cada medida.

Inclua segurança e alinhamento na prática. Acompanhe o esforço dedicado a avaliações, monitorabilidade e reward hacking, e reserve espaço para as pessoas definirem prioridades e limites.

Fonte: <https://openai.com/index/research-acceleration-jagged-frontier/>

## Além do vídeo

- A atualização amplia um post de setembro da OpenAI com novas medidas quantitativas e qualitativas.
- A taxonomia O*NET AI R&D usada nas categorias foi desenvolvida pela Epoch AI.
- A OpenAI registra que outras organizações também contribuíram para as normas de medição da aceleração de P&D em IA.
- A compensação sem ações considerada no relatório inclui salário, horas extras, bônus, benefícios e impostos do empregador.
