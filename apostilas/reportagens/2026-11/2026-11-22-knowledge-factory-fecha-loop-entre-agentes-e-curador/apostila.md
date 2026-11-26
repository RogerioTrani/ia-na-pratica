# Knowledge factory fecha loop entre agentes e curador

_2026-11-22 · reportagem_

Uma knowledge factory reúne e mantém o conhecimento que os agentes precisam para executar tarefas do jeito que a empresa espera. Ela transforma documentos, experiência e falhas de uso em orientações reutilizáveis, reduzindo a dependência da memória dos melhores funcionários. Nesta apostila, você vai separar contexto de conhecimento, conhecer os três tipos de conhecimento e entender o loop entre agentes, curador e armazenamento. O exemplo de um relatório de receita mostra como uma falha e uma correção humana atualizam o trabalho seguinte. Ao final, você terá um caminho para começar por um fluxo recorrente e fechar a primeira lacuna.

## O fato

Em 21 de novembro de 2026, a LangChain divulgou um artigo sobre como construir uma knowledge factory. O termo designa o sistema usado para coletar, curar e manter conhecimento para agentes. A proposta responde a um problema prático: modelos e contexto não resolvem sozinhos a forma como uma empresa trabalha.

A LangChain relata aplicação interna em agentes de go-to-market (GTM) e de conteúdo. Também descreve o LangSmith Engine, agente que analisa traces e sugere correções, como responsável por manter uma knowledge factory para cada agente.

Fonte: <https://www.langchain.com/blog/knowledge-factory>

## Por que isso importa

Os funcionários mais eficientes carregam decisões que não aparecem em um manual. Eles sabem com quem falar, onde buscar uma resposta e por que seguir determinado procedimento. Esse conhecimento costuma ser tácito, implícito e espalhado. Pode existir apenas na memória de uma pessoa ou estar dividido entre vários documentos.

Quando essa experiência não chega ao agente, ele recebe dados, mas falta parte do entendimento necessário para agir corretamente. A knowledge factory organiza esse saber para que ele seja reutilizado. O objetivo é transformar o trabalho realizado em aprendizado para o trabalho seguinte.

A proposta acompanha a ideia de software factories. Nesse modelo, engenheiros especializados constroem sistemas que ajudam toda a empresa a produzir software, enquanto agentes executam a construção. O trabalho de conhecimento segue uma lógica parecida. O artigo cita apresentações, vídeos de lançamento e ações de prospecção outbound como tarefas que agentes já conseguem realizar; o investimento recomendado está no conhecimento que essas tarefas exigem.

Fonte: <https://www.langchain.com/blog/knowledge-factory>

## Contexto e conhecimento

Contexto é o conjunto de informações disponíveis para o agente durante uma tarefa. Ele pode incluir dados da solicitação, resultados de ferramentas e conhecimentos previamente armazenados. É o contexto que o agente tem à mão no momento de agir.

Conhecimento é o entendimento reutilizável que a empresa mantém para que a tarefa seja executada corretamente. Ele responde a perguntas como o que uma métrica significa, qual fonte merece confiança e como tratar uma situação específica. Pode estar escrito, mas muitas vezes depende da experiência de quem já realizou o trabalho.

A knowledge factory transforma documentos e experiência em conhecimento que poderá virar contexto em tarefas futuras. O conhecimento é uma forma de contexto, sem esgotar tudo o que o agente precisa receber. Dados que mudam rapidamente podem ser fornecidos diretamente durante a execução, enquanto procedimentos e definições são mantidos para reutilização.

Fonte: <https://www.langchain.com/blog/knowledge-factory>

## Skills

Skills registram como realizar tarefas do jeito que a empresa espera. Elas reúnem procedimentos, instruções e scripts. Muitas dessas orientações eram passadas de colega para colega e nunca foram escritas. Escrevê-las permite que o agente siga o mesmo padrão sem depender da disponibilidade de uma pessoa específica.

Uma skill útil descreve a sequência esperada e os cuidados do processo. No exemplo do artigo, uma skill ensina a produzir relatórios no estilo da LangChain. Depois de uma correção de formato, essa mesma skill pode incorporar o novo cabeçalho e passar a valer para os próximos relatórios.

- Use skills para registrar procedimentos repetidos e padrões de execução.
- Inclua as instruções e os scripts necessários para cumprir a tarefa.
- Comece pelos procedimentos que hoje dependem de orientação entre colegas.

Fonte: <https://www.langchain.com/blog/knowledge-factory>

## Domain knowledge

Domain knowledge reúne definições, políticas e fatos sobre o funcionamento do negócio. Abrange informações centrais sobre pessoas, produtos, clientes, concorrentes e organização. É o conhecimento que muda com menos frequência e dá base para interpretar o que o agente encontra.

Esse conteúdo costuma estar escrito, mas pode ficar incompleto ou incorreto por causa do volume de informação. A curadoria serve para preencher lacunas, corrigir contradições e manter uma representação utilizável. No exemplo do relatório de receita, a forma de calcular ARR fica no wiki da empresa como conhecimento de longa duração.

- Inclua definições, políticas e fatos necessários para entender o negócio.
- Priorize informações centrais sobre pessoas, produtos, clientes, concorrentes e organização.
- Use a curadoria para corrigir lacunas e contradições.

Fonte: <https://www.langchain.com/blog/knowledge-factory>

## Data access guidance

Data access guidance orienta quais fontes usar, onde os dados ficam e como consultá-los. Uma estratégia de dados com ferramentas como Snowflake ou Databricks é a base desse trabalho. Quando a fonte de verdade já está completa e atualizada, não é necessário manter uma cópia separada. O conhecimento a manter é a instrução de acesso.

Essa separação evita transformar dados voláteis em documentação duplicada. O agente recebe a orientação para chegar à informação atual e consulta a fonte no momento da tarefa. No exemplo do artigo, instruções no Context Hub explicam como acessar os dados de receita em BigQuery e Salesforce.

- Identifique a fonte de verdade de cada dado.
- Explique onde as informações ficam armazenadas.
- Registre como consultar as fontes.
- Atualize a orientação quando o caminho de acesso mudar.

Fonte: <https://www.langchain.com/blog/knowledge-factory>

## Os números do modelo

A estrutura apresentada no artigo pode ser contada em três tipos de conhecimento, três peças da factory e um fluxo recorrente para começar. Esses números organizam o modelo; não representam metas de desempenho.

- Três tipos de conhecimento: skills, domain knowledge e data access guidance. Eles separam o procedimento, o funcionamento do negócio e o acesso aos dados atuais.
- Três peças da factory: sinalização pelos agentes, curator agent e armazenamento. Juntas, elas formam o caminho da lacuna até a atualização.
- Um fluxo recorrente para começar: o artigo recomenda escolher uma tarefa repetida para descobrir onde os agentes têm dificuldade e fechar o loop.

Fonte: <https://www.langchain.com/blog/knowledge-factory>

## Agentes sinalizam lacunas

Uma das melhores formas de descobrir conhecimento faltante é observar o agente durante o trabalho. Quando ele não encontra uma informação ou percebe que ela está errada, deve sinalizar o problema. A ferramenta precisa permitir, no mínimo, relatar o que está errado. Ela também pode aceitar uma sugestão de correção.

A sinalização transforma uma dificuldade da tarefa em entrada para a curadoria. O agente que está executando o trabalho reconhece o ponto de falha; o curador investiga as fontes e decide como atualizar o conhecimento.

- Informe quando uma informação não foi encontrada ou está errada.
- Descreva o problema no contexto da tarefa executada.
- Sugira a correção quando houver base para isso.
- Envie a sinalização para o fluxo de curadoria.

Fonte: <https://www.langchain.com/blog/knowledge-factory>

## Curator agent

Manter todo o conhecimento manualmente exigiria um esforço muito grande. Também é arriscado deixar a atualização apenas com os agentes que usam esse conhecimento. Eles estão concentrados em cumprir a própria tarefa, e corrigir a base exige entender as fontes e as relações entre as informações. Se cada agente alterar o que bem entender, o conhecimento pode ficar confuso e contraditório.

O curator agent roda em segundo plano, em uma cadência, e reúne o que precisa para manter a base organizada. Ele deve acessar as fontes brutas, como Notion e Slack, os traces dos agentes e as sinalizações de erro. Com esse conjunto, ele atualiza skills, definições e instruções de acesso.

O LangSmith Engine ilustra esse papel na LangChain. Ele analisa traces, sugere correções e mantém uma knowledge factory para cada agente.

- Receba as sinalizações de informações erradas ou ausentes.
- Acesse as fontes brutas onde o conhecimento está espalhado.
- Examine os traces para entender como os agentes usam o conhecimento.
- Atualize a base em uma cadência definida.

Fonte: <https://www.langchain.com/blog/knowledge-factory>

## Traces: do uso ao aprendizado

Trace é o registro da execução de um agente. Ele permite acompanhar tentativas, consultas e correções. O curador usa esse registro para entender como as pessoas estão tentando usar os agentes e transformar padrões observados em skills.

As correções humanas também deixam marcas nesse caminho. No exemplo do relatório, a liderança de finanças trabalha com o agente para ajustar a formatação e informar um novo cabeçalho. O curador encontra essa troca nos traces e incorpora o padrão ao conhecimento reutilizável.

- Use traces para identificar padrões de uso.
- Compare a tentativa do agente com a correção humana.
- Transforme o procedimento ajustado em uma skill reutilizável.

Fonte: <https://www.langchain.com/blog/knowledge-factory>

## Armazenamento: GitHub, Notion, Context Hub e Neo4j

Em alguns aspectos, o armazenamento é a parte menos importante da factory. O conhecimento pode ficar em skills no GitHub, em um arquivo único no Notion, em formato OKF no LangSmith Context Hub ou em um grafo de conhecimento no Neo4j. O curador deve saber interagir com esses formatos.

A representação da memória ainda é um campo pouco explorado. O artigo observa que a indústria convergiu para skills na memória procedural. Para a memória semântica, menciona OKF como possibilidade e reconhece que ainda não existe um padrão consolidado. Por isso, escolher um formato excessivamente rígido no início pode complicar mais do que ajudar.

Antes de decidir onde guardar, é mais útil garantir que o agente sinalize lacunas, que o curador receba as informações certas e que a atualização chegue ao próximo trabalho.

- GitHub: skills no formato padrão, com endereço oficial em https://github.com.
- Notion: arquivo único, com endereço oficial em https://www.notion.so.
- LangSmith Context Hub: formato OKF, com documentação oficial em https://docs.langchain.com/langsmith/use-the-context-hub.
- Neo4j: grafo de conhecimento, com endereço oficial em https://neo4j.com.

Fonte: <https://www.langchain.com/blog/knowledge-factory>

## Exemplo completo: relatório de receita

O exemplo da LangChain reúne contexto imediato e conhecimento reutilizável na mesma tarefa. Os números de receita são o contexto bruto. As instruções de acesso, a forma de calcular ARR e o padrão de relatório são o conhecimento que orienta a execução.

A atualização acontece depois que o agente trabalha e revela uma lacuna. Uma correção humana entra nos traces, o curador identifica o padrão e a knowledge factory incorpora a mudança.

- O agente começa com os números de receita armazenados em BigQuery e Salesforce, que formam o contexto bruto da tarefa.
- Ele consulta uma skill no GitHub para produzir relatórios no estilo da LangChain, a definição de ARR no wiki da empresa e instruções no Context Hub para acessar BigQuery e Salesforce.
- Ao perceber que uma coluna do BigQuery foi renomeada, ele encontra a coluna correta, sinaliza o problema e sugere o nome adequado.
- Depois de gerar o relatório, a liderança de finanças corrige a formatação com o agente e informa um novo cabeçalho para todos os documentos da LangChain.
- Naquela noite, o curador lê a sinalização e os traces, então atualiza as skills para usar a nova coluna e o novo cabeçalho.

Fonte: <https://www.langchain.com/blog/knowledge-factory>

## O que muda para você

A knowledge factory muda o ponto de partida. Você não precisa documentar tudo antes de colocar os agentes para trabalhar. O próprio trabalho revela o que falta, e a curadoria transforma essa descoberta em conhecimento para as próximas tarefas.

O ciclo começa com a execução do agente. Uma falha produz uma sinalização, o curador investiga as fontes e os traces, e o armazenamento recebe a atualização. Na tarefa seguinte, o agente usa essa versão corrigida. O valor está na reutilização do aprendizado, não no volume de documentos acumulados.

Fonte: <https://www.langchain.com/blog/knowledge-factory>

## O que fazer hoje

O artigo recomenda começar por um fluxo recorrente. A sequência abaixo mantém o foco em descobrir uma lacuna real, tratá-la com o curador e verificar o resultado na próxima execução.

1. No fluxo de trabalho que você quer melhorar, escolha uma tarefa recorrente executada por um agente. O resultado será um limite claro para observar o loop.
2. Na execução dessa tarefa, deixe o agente usar o contexto e o conhecimento disponíveis. O resultado será um registro de onde ele acerta, trava ou encontra informação errada.
3. Na ferramenta de sinalização do agente, registre cada lacuna e a correção sugerida quando houver base. O resultado será uma fila de problemas para o curador.
4. No processo de curadoria, configure o agente responsável para ler fontes brutas, traces e sinalizações em uma cadência definida. O resultado será a atualização das skills, definições ou instruções de acesso afetadas.
5. Na próxima execução da mesma tarefa, use o conhecimento atualizado. O resultado será uma nova verificação de se a lacuna foi fechada e de se outra surgiu.

Fonte: <https://www.langchain.com/blog/knowledge-factory>

## O que conferir

Antes de confiar na factory, confira se o loop tem todas as peças. O agente precisa conseguir sinalizar, o curador precisa ter acesso às evidências e o conhecimento atualizado precisa chegar à tarefa seguinte.

Algumas decisões exigem atenção humana. No exemplo, a liderança de finanças participa da correção de formatação e do novo cabeçalho. O curador usa essa interação para atualizar a skill, mas a validação do padrão vem do trabalho com uma pessoa responsável pelo resultado.

- Fonte de verdade: quando ela já estiver completa e atualizada, mantenha instruções de acesso no lugar de uma cópia separada dos dados.
- Papel dos agentes: use os agentes de tarefa para sinalizar problemas e reservar a manutenção do conhecimento ao curador.
- Acesso do curador: verifique se ele consegue ler fontes brutas, traces e sinalizações.
- Revisão humana: mantenha validação humana para correções de padrão, formato e regras de negócio.
- Formato: trate a escolha do armazenamento como uma decisão aberta, principalmente para memória semântica.
- Cadência: defina com que frequência o curador roda para que as sinalizações não fiquem sem tratamento.
- Recorte: use o exemplo da LangChain para entender o mecanismo, sem convertê-lo em promessa de resultado para outro contexto.

Fonte: <https://www.langchain.com/blog/knowledge-factory>

## Glossário

- Agente: programa de IA que executa tarefas e pode consultar fontes ou usar ferramentas.
- Conhecimento tácito: entendimento que uma pessoa usa no trabalho, mas que costuma ficar implícito ou apenas na memória.
- Contexto: informações disponíveis para o agente durante uma tarefa.
- Conhecimento: entendimento reutilizável mantido para que o agente realize a tarefa corretamente.
- Knowledge factory: sistema que coleta, cura e mantém o conhecimento usado pelos agentes.
- Skills: procedimentos, instruções e scripts que registram a forma esperada de executar tarefas.
- Domain knowledge: definições, políticas e fatos sobre o negócio, produtos, clientes, pessoas, concorrentes e organização.
- Data access guidance: orientação sobre quais fontes usar, onde ficam os dados e como consultá-los.
- Fonte de verdade: base de dados considerada completa e atualizada para determinada informação.
- Trace: registro da execução de um agente, usado para entender tentativas, ferramentas e correções.
- Curator agent: agente que atualiza e mantém o conhecimento em segundo plano, com acesso a fontes, traces e sinalizações.
- Memória procedural: conhecimento de como executar procedimentos, representado no modelo por skills.
- Memória semântica: conhecimento sobre conceitos e fatos, para o qual o artigo menciona OKF como possível padrão.
- OKF: formato de conhecimento mencionado para representação no LangSmith Context Hub.
- Grafo de conhecimento: estrutura que representa informações como entidades e relações entre elas.
- ARR: métrica de receita recorrente anual usada no exemplo do relatório.
- LangSmith Engine: agente da LangChain que analisa traces, sugere correções e mantém uma knowledge factory por agente.

Fonte: <https://www.langchain.com/blog/knowledge-factory>

## Para onde ir depois

O próximo passo é escolher um fluxo recorrente e tratar a primeira dificuldade do agente como uma oportunidade de aprendizado. Pratique a separação entre contexto imediato e conhecimento reutilizável antes de ampliar a documentação.

- Separe, em uma tarefa real, os dados da execução, o procedimento, as definições e as instruções de acesso.
- Liste as lacunas encontradas durante o trabalho do agente.
- Envie as lacunas para o curador e acompanhe a atualização do conhecimento.
- Repita a tarefa para verificar o efeito da correção e identificar o próximo aprendizado.

Fonte: <https://www.langchain.com/blog/knowledge-factory>

## Além do vídeo

- A LangChain afirma trabalhar com alguns clientes para levar a knowledge factory a agentes internos e externos.
