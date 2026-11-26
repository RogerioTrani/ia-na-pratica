# OpenAI foi de 30 ferramentas a uma fábrica de agentes

_2026-11-24 · reportagem_

A Performance Factory é o sistema com que a OpenAI automatiza a investigação e a correção de regressões de desempenho no ChatGPT usando agentes do Codex. A apostila percorre os seis passos da evolução da equipe de desempenho, desde investigações manuais até a fábrica de agentes, e mostra as quatro peças que sustentam o sistema, o Fluxo de Regressão em operação e as lições para equipes que querem adotar fluxos com agentes de IA. Ao final, você saberá como estruturar tarefas com estado, revisão adversarial e verificação de recuperação para manter serviços rápidos enquanto o desenvolvimento acelera.

## Como usar esta lista

Esta apostila apresenta os seis passos pelos quais a equipe de desempenho da OpenAI passou ao adotar o Codex, do trabalho manual até a Performance Factory, um sistema autônomo que usa agentes de IA para encontrar e corrigir regressões. Cada passo é uma etapa da evolução, não uma escolha isolada: a equipe passou por elas nessa ordem.

Este conteúdo serve a engenheiros e líderes de equipes de serviço que querem entender como fluxos de trabalho com agentes de IA funcionam em produção. O caso concreto é a manutenção do desempenho do ChatGPT, mas o padrão — tarefas com estado, agentes que assumem etapas prontas, revisão adversarial e verificação de recuperação — se aplica a outros domínios.

Comece pelo passo que corresponde ao estágio atual do seu time. Se você ainda investiga lentidões à mão, o passo 1 mostra quais ferramentas criar. Se já usa o Codex como parceiro, o passo 3 explica como transformar o método em habilidade reutilizável. Se já sente que é intermediário entre alertas e o Codex, o passo 6 descreve a fábrica completa.

1. Antes do Codex — tudo manual: comece criando profilers de CPU e de alocação para os problemas que se repetem.
2. Codex como parceiro — pergunte «por que isso ficou mais lento?» e investigue junto, mesmo sem conhecer o sistema.
3. Habilidade compartilhada perf-forensics — registre o método de investigação em uma habilidade que o Codex lê.
4. O humano vira intermediário — quando você só copia alertas e cola resultados, é hora de automatizar.
5. Alerta inicia a sessão do Codex — leve as investigações para a nuvem.
6. A fábrica: tarefas com estado — construa o sistema completo com os quatro componentes.

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Antes do Codex: tudo manual

Antes do Codex, os engenheiros examinavam métricas e logs manualmente, comparavam traces, depuravam máquinas em operação e liam código para investigar uma lentidão. Esse trabalho consumia muito tempo, e saber onde procurar frequentemente exigia um conhecimento profundo do serviço. Era fácil deixar sinais relevantes passarem despercebidos.

Quando a equipe encontrava os mesmos tipos de problemas repetidamente — como regressões na latência do primeiro token do ChatGPT —, criava ferramentas avançadas, como profilers de CPU e de alocação, para facilitar essas investigações. Com o tempo, acumulou mais de 30 ferramentas de desempenho.

Esse passo vale para qualquer equipe que ainda investiga regressões à mão: o ponto de partida é identificar os problemas que se repetem e criar ferramentas específicas para eles. O limite é que cada nova ferramenta resolve um caso, e a equipe segue dependendo de quem conhece o serviço para saber onde olhar.

- Tecnologia: profilers de CPU e de alocação, métricas, logs, traces.
- Como começar: liste os três problemas de desempenho mais recorrentes e crie uma ferramenta para o mais frequente.

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Codex como parceiro

Com o Codex como parceiro, os engenheiros podiam perguntar «por que isso ficou mais lento?» e trabalhar com o Codex para investigar, mesmo em um sistema que não conheciam. O Codex podia pesquisar grandes bases de código, encontrar métricas e traces relevantes, acompanhar interações entre serviços e realizar análises de perfil adequadas para reconstruir o que havia acontecido.

O ganho era que mais pessoas conseguiam avançar em investigações difíceis, com menos tempo e conhecimento especializado. O limite era que os engenheiros ainda precisavam conduzir o processo, sabendo quais ferramentas de desempenho usar e como orientar a investigação.

Esse passo se aplica quando a equipe já tem ferramentas e método, mas a investigação depende de quem conhece o sistema. O Codex amplia quem consegue investigar, mas não elimina a necessidade de orientação humana.

- Tecnologia: Codex (chatgpt.com/codex), métricas, traces, análise de perfil.
- Como começar: use o Codex para investigar uma lentidão em um serviço que você não conhece bem, fornecendo as métricas e traces relevantes.

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Habilidade compartilhada perf-forensics

Para ampliar a automação, a equipe registrou o processo de investigação em uma habilidade compartilhada chamada perf-forensics. Ela informa ao Codex quais ferramentas estão disponíveis, quando usá-las e como investigar uma lentidão, para que ele possa tentar resolver o problema por diferentes ângulos: descobrir quando a lentidão começou, identificar as requisições afetadas e investigar se implantações ou mudanças de configuração poderiam explicá-la.

A habilidade foi testada e refinada usando avaliações baseadas em regressões anteriores. Para os tipos de regressão em que a equipe se concentrou — aumentos de latência e quedas de disponibilidade do ChatGPT —, já era possível fornecer um alerta ao Codex e receber um diagnóstico em uma única execução, sem orientá-lo em cada etapa.

Esse passo se aplica quando o método de investigação da equipe está maduro o suficiente para ser documentado. A habilidade transforma conhecimento tácito em instruções que o Codex pode seguir sozinho, e as avaliações com regressões passadas ajudam a verificar se as mudanças na habilidade melhoram ou pioram o diagnóstico.

- Tecnologia: habilidade perf-forensics, avaliações baseadas em regressões anteriores.
- Como começar: documente o método de investigação da sua equipe em um arquivo de instruções que o Codex possa ler, e teste com casos de regressão já resolvidos.

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## O humano vira intermediário

À medida que adicionavam e refinavam habilidades de desempenho do Codex, como perf-forensics, os engenheiros começaram a se sentir intermediários entre os alertas e o Codex. Um alerta era disparado, e um engenheiro simplesmente o copiava e colava no Codex com a habilidade certa, depois colava os resultados no Slack.

Esse padrão — humano como intermediário — é o sinal de que a automação pode avançar. Quando a única ação humana é repassar informação entre sistemas, essa etapa pode ser automatizada.

Esse passo se aplica quando as habilidades já funcionam bem e o gargalo é a intervenção humana para mover dados entre ferramentas. É o gatilho para levar as investigações para a nuvem.

- Tecnologia: Codex, Slack, habilidades de desempenho.
- Como começar: identifique quais etapas do seu fluxo atual são puramente mecânicas — copiar, colar, repassar — e liste-as para automação.

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Alerta inicia a sessão do Codex

Em seguida, a equipe levou as investigações para a nuvem, para que um alerta pudesse iniciar uma sessão do Codex automaticamente. O Codex investigava a lentidão e publicava suas descobertas na conversa do Slack, mas a automação terminava nessa resposta. Um engenheiro ainda precisava analisar o diagnóstico, desenvolver uma correção e verificar se ela havia funcionado após a implantação.

Conforme os alertas se acumulavam, até descobrir quais regressões precisavam de atenção exigia vasculhar conversas no Slack. A automação parava no diagnóstico: alguém ainda precisava criar a correção e conferir o resultado.

Esse passo se aplica quando o diagnóstico já é confiável o suficiente para ser automatizado, mas a correção e a verificação ainda dependem de pessoas. É um avanço real, mas revela que o gargalo se moveu do diagnóstico para a ação.

- Tecnologia: Codex na nuvem, Slack, alertas de desempenho.
- Como começar: configure um alerta para abrir uma sessão do Codex automaticamente e publicar o diagnóstico no canal da equipe.

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## A fábrica: tarefas com estado

A Performance Factory foi criada para executar fluxos de engenharia de desempenho com agentes de IA de ponta a ponta. Ela acompanha o que cada tarefa ativa precisa fazer a seguir e atribui um agente quando essa etapa está pronta para começar. Cada tarefa mantém seu estado e suas descobertas, permitindo que o trabalho passe entre agentes e engenheiros e seja retomado após uma revisão de código ou implantação.

No caso de uma regressão, o trabalho começa com a investigação de um alerta e termina com a verificação da recuperação em produção. A equipe pode transformar otimizações comuns em fluxos de trabalho executados regularmente em seus serviços. Um fluxo que identifica uma possível otimização pode abrir uma tarefa em outro fluxo para testá-la e implementá-la.

Esse passo se aplica quando a equipe já automatizou o diagnóstico e quer fechar o ciclo completo: investigação, correção, revisão e verificação. A fábrica é o estágio em que o trabalho flui entre agentes e engenheiros sem perder o fio.

- Tecnologia: serviço de tarefas, loop de distribuição, Codex na nuvem, assinaturas de eventos.
- Como começar: defina um fluxo com estados explícitos (detectada, causa raiz, correção proposta, resolvida) e crie tarefas que mantenham estado entre etapas.

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Os números

Em pouco mais de três meses, o Fluxo de Regressão acompanhou mais de 1.700 investigações e identificou a causa raiz de mais de 600 casos. São 17 investigações automatizadas por dia.

O que não dá para concluir: os números não dizem quantas correções foram efetivamente implantadas nem qual foi a taxa de acerto das correções propostas. O artigo menciona que acertar nas correções tem sido mais difícil do que encontrar a causa.

- Investigações acompanhadas: mais de 1.700 (em pouco mais de três meses).
- Causas raiz identificadas: mais de 600.
- Investigações automatizadas por dia: 17.
- Período: pouco mais de três meses.

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Quatro peças sustentam a fábrica

A Performance Factory é composta por quatro componentes: um gerenciador de tarefas com fluxos configuráveis, um loop de distribuição que atribui trabalho pronto aos agentes, uma API que executa o Codex na nuvem e assinaturas de eventos que reativam agentes quando algo muda.

Juntos, esses quatro componentes resolvem o problema central: como fazer agentes de IA trabalharem em tarefas de longa duração que passam por estados, aguardam pessoas e implantações, e precisam ser retomadas sem perder o contexto.

As seções seguintes detalham cada componente. A ordem segue a do artigo: serviço de tarefas, loop de distribuição, Codex na nuvem e assinaturas de eventos.

1. Serviço de tarefas com fluxos configuráveis.
2. Loop de distribuição que atribui trabalho.
3. Codex na nuvem.
4. Assinaturas de eventos que reativam o agente.

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Serviço de tarefas com fluxos configuráveis

O serviço de tarefas é onde os engenheiros definem fluxos de trabalho, adicionando arquivos de configuração e prompts escritos em Markdown para os agentes seguirem. A configuração lista os estados pelos quais uma tarefa pode passar, as transições permitidas e quais etapas precisam de um engenheiro. Prompts separados informam aos agentes o que fazer em cada etapa.

Cada unidade de trabalho se torna uma tarefa em um fluxo, e todos os fluxos ficam visíveis em uma interface. Os engenheiros podem ver o que está em aberto, acompanhar o progresso e compartilhar uma tarefa com um colega que tenha mais contexto ou possa ajudar na próxima etapa.

A estrutura de arquivos é simples: um diretório por tipo de tarefa, com um arquivo de configuração e um subdiretório com os prompts para cada estado.

- Tecnologia: arquivos TOML de configuração, prompts em Markdown.
- Como começar: crie um diretório para o tipo de tarefa, com um config.toml listando estados e transições, e um subdiretório work/ com um arquivo .md por estado.

```
code-change/
├── config.toml
└── work/
    ├── implementing.md
    └── reviewing.md
```

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Loop de distribuição

O loop de distribuição verifica periodicamente quais tarefas estão prontas para a próxima etapa. Ele atribui um agente a cada tarefa, iniciando um turno do Codex com as instruções para o estado atual da tarefa. O agente registra seu progresso na tarefa e a move para o próximo estado se concluir a etapa.

Esse componente resolve o problema de coordenação: em vez de um agente tentar fazer tudo de uma vez, o loop garante que cada tarefa avance apenas quando está pronta, e que um agente seja atribuído no momento certo.

O padrão é verificar periodicamente, atribuir agentes a tarefas prontas e deixar que o agente mova a tarefa para o próximo estado. Isso permite que o trabalho flua sem que alguém precise monitorar cada tarefa individualmente.

- Tecnologia: loop de distribuição, turnos do Codex.
- Como começar: implemente uma verificação periódica que identifique tarefas prontas e atribua um agente com as instruções do estado atual.

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Codex na nuvem

Após receber uma tarefa, o agente precisa de um lugar para trabalhar, com acesso às mesmas ferramentas que um engenheiro usaria. A equipe criou uma API interna para invocar programaticamente um turno do Codex na nuvem. O turno do Codex é executado em um ambiente dentro da rede interna, com acesso aos repositórios de código e às ferramentas de observabilidade usadas pelos engenheiros, como métricas, logs, traces, perfis de CPU e snapshots de memória.

O agente opera com uma identidade de serviço, o que permite delimitar suas permissões e identificar quais ações vieram dos agentes de desempenho.

Levar o trabalho com agentes de IA para a nuvem permite executá-lo em paralelo, sem depender de os laptops dos engenheiros estarem abertos nem de gerenciar manualmente máquinas individuais de desenvolvimento na nuvem. O Codex pode ser acessado em chatgpt.com/codex.

- Tecnologia: API interna do Codex, ambiente na rede interna, identidade de serviço.
- Como começar: crie uma API para invocar o Codex programaticamente em um ambiente com acesso aos seus repositórios e ferramentas de observabilidade.

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Assinaturas de eventos

Alguns trabalhos precisam aguardar uma pessoa ou uma implantação; um agente não deveria precisar continuar em execução durante essa espera. Quando uma tarefa precisa aguardar, ela pode assinar eventos, como comentários de revisão ou falhas nas verificações de CI em um pull request do GitHub, para receber uma notificação quando for hora de retomar o trabalho.

Quando um evento recebido corresponde à assinatura, a tarefa fica pronta novamente, e o loop de distribuição pode atribuir um agente para continuar o trabalho. Isso evita que agentes fiquem rodando e consumindo recursos enquanto esperam por ações humanas ou sistemas externos.

Esse componente atende tarefas de longa duração: o agente trabalha, a tarefa espera e o trabalho é retomado quando algo muda, sem perder o estado da tarefa.

- Tecnologia: assinaturas de eventos, notificações de CI/revisão.
- Como começar: identifique os eventos que sinalizam que uma tarefa pode avançar (comentário de revisão, deploy concluído, CI passou) e configure assinaturas para eles.

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Fluxo de Regressão: do alerta à recuperação

O Fluxo de Regressão é o primeiro fluxo de trabalho criado na Performance Factory. Uma regressão de desempenho passa por várias etapas: precisa de investigação, causa raiz identificada, correção proposta e resolvida. O fluxo automatizado reflete essas mesmas etapas e conduz a tarefa por elas.

Quando um dos alertas de desempenho configurados é disparado, o Fluxo de Regressão abre uma tarefa que os agentes assumem e conduzem pelas etapas. A tarefa registra seu status e suas principais descobertas fora do contexto de qualquer agente individual, para que outros agentes ou engenheiros possam dar continuidade ao trabalho. Os engenheiros podem acompanhar o trabalho no Slack ou na interface do Fluxo de Regressão, acrescentar contexto e revisar as mudanças propostas.

As etapas são: Detectada, Encontrar a causa raiz, Propor correção, Revisar e implantar, Verificar recuperação e Resolvida. Um agente encontra a causa raiz, outro propõe a correção, um engenheiro revisa e implanta, e outro agente verifica se o desempenho voltou ao nível de referência antes de marcar a tarefa como resolvida.

- Detectada: alerta de desempenho é disparado.
- Encontrar a causa raiz: agente investiga métricas, implantações e código.
- Propor correção: agente implementa correção e abre pull request.
- Revisar e implantar: engenheiro revisa e decide sobre a integração.
- Verificar recuperação: agente verifica se o desempenho voltou ao nível de referência.
- Resolvida: se recuperou, tarefa é marcada como resolvida; se recuperou só parcialmente, marca a regressão original como resolvida e abre nova tarefa para a lentidão restante; se não melhorou, registra e reencaminha para investigação.

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Revisão adversarial do diagnóstico

No início, os agentes às vezes paravam na primeira explicação plausível que encontravam, e alguns desses diagnósticos se mostravam incorretos. Para detectar esses erros, a equipe adicionou uma revisão adversarial: uma sessão separada do Codex que tenta refutar o diagnóstico proposto.

O revisor verifica novamente as premissas e testa cenários contrafactuais. Se uma implantação causou a lentidão, requisições semelhantes que não foram expostas à mudança continuaram funcionando normalmente? Se a mudança suspeita foi revertida, a métrica afetada se recuperou?

Em uma investigação, um agente rastreou falhas nas conversas do ChatGPT até erros no download de imagens e marcou a causa como identificada. O revisor do Codex percebeu que o serviço interno responsável por localizar arquivos já havia se recuperado, enquanto as requisições de imagens continuavam falhando. O diagnóstico não explicava a continuidade das falhas, então o revisor de IA reabriu a investigação e registrou o que ainda precisava ser esclarecido.

Em uma revisão manual de 100 sugestões de causa raiz, a equipe classificou 70% como corretas; os outros 30% precisavam de mais refinamento ou não estabeleciam plenamente a relação de causalidade. Turnos diferentes investigam regressões, questionam diagnósticos e propõem correções para aumentar a precisão por meio de verificações e contrapesos.

- Tecnologia: sessão separada do Codex para revisão adversarial.
- Como começar: adicione uma etapa de revisão onde um agente separado tenta refutar o diagnóstico proposto, testando cenários contrafactuais.

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Corrigir a regressão é a parte difícil

Depois que o diagnóstico passa pela revisão adversarial, o fluxo pede ao Codex que implemente uma correção e abra um pull request. Um engenheiro revisa o PR e decide se deve integrá-lo. Cada tarefa tem um relatório com um resumo gerado automaticamente da regressão, seu impacto, a causa raiz e a correção proposta.

A equipe ajustou esses resumos para facilitar a leitura rápida, incluindo séries temporais de métricas, gráficos de chama de CPU e traces para ajudar os engenheiros a entender rapidamente as descobertas e inspecionar as evidências. Os engenheiros podem editar o PR diretamente ou usar o diagnóstico para escrever sua própria correção. Se deixarem comentários no PR, o fluxo reativa um agente para atendê-los.

Acertar nas correções tem sido mais difícil do que encontrar a causa. As mudanças propostas pelos agentes às vezes são mais complicadas do que o necessário ou introduzem novos problemas. Assim como na etapa de causa raiz, a equipe adicionou uma revisão adversarial de cada correção proposta para verificar se ela trata a causa raiz e ajudar a detectar bugs ou consequências não intencionais.

Algumas correções também exigem decisões de arquitetura em um nível mais amplo. Adicionar um cache pode melhorar o desempenho, mas introduzir dados desatualizados. Mudanças como essas se beneficiam da orientação de um engenheiro que conheça o serviço e possa ponderar as vantagens e desvantagens.

- Tecnologia: pull request, relatório de tarefa com resumo, revisão adversarial de correção.
- Como começar: configure o fluxo para abrir PRs automaticamente com relatório de regressão, e adicione uma etapa de revisão adversarial da correção proposta.

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Preserve a atenção dos engenheiros

A saída bruta de uma investigação do Codex pode ser um bloco enorme de texto difícil de interpretar. É preciso esforço para entender o que o agente está afirmando e localizar os gráficos para verificar se os dados sustentam suas conclusões. A equipe quer que os engenheiros concentrem sua atenção nas decisões, em vez de reconstruir o trabalho do agente.

Os agentes conseguem investigar mais regressões do que uma equipe tem tempo de analisar. A primeira versão oferecia aos engenheiros uma interface cheia de descobertas, mas alguém ainda precisava decidir quais informações importavam. Uma única regressão também pode aparecer como vários incidentes em diferentes alertas, monitores e canais.

Agora, o fluxo vincula incidentes relacionados, agrupa-os pelas métricas importantes para as equipes e os ordena pelo impacto estimado. Os engenheiros podem se concentrar em acrescentar contexto, ponderar vantagens e desvantagens e decidir o que colocar em produção.

- Tecnologia: vinculação de incidentes, agrupamento por métricas, ordenação por impacto.
- Como começar: agrupe incidentes relacionados e ordene-os por impacto estimado antes de apresentar aos engenheiros.

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Avalie as mudanças nos seus agentes

Atualizar uma habilidade de investigação ou o modelo pode melhorar o diagnóstico do agente em alguns casos e piorá-lo em outros. Por isso, é preciso testar o impacto dessas mudanças antes de aplicá-las. A equipe testa duas coisas separadamente: a qualidade da investigação do agente e a utilidade dos seus resumos para os engenheiros.

Para avaliar as investigações, a equipe faz testes retrospectivos com incidentes anteriores de produção. Transforma esses incidentes em um conjunto de casos de teste que pode ser executado novamente quando a habilidade muda. Um agente do Codex tenta investigar e resolver o incidente, e o comportamento dele é comparado com os dados da resolução real ocorrida no passado. Cada caso começa com um novo investigador do Codex e o sinal original, sem detalhes que possam revelar a resposta. Testes com dados históricos exigem cuidado: métricas e traces expiram, enquanto evidências coletadas após a recuperação podem revelar a causa. Um teste só é útil se entendermos quais evidências estavam disponíveis para o investigador, que pode inspecionar código e consultar a telemetria de produção dentro de limites definidos, mas não pode usar memórias salvas, ler o relatório do incidente nem ver resultados de execuções anteriores.

Avaliam o acerto sobre quando o problema começou, qual era sua dimensão e quais requisições foram afetadas, e como o agente usa as evidências para ordenar as possíveis causas por probabilidade e explicar o que ainda é incerto. Um agente pode acertar o momento de início e ainda atribuir o problema à implantação errada, por isso esses aspectos são avaliados separadamente. Para avaliar os resumos das tarefas, a equipe usa snapshots de tarefas salvas, especialmente adequados para testes retrospectivos porque a criação de resumos não depende de métricas externas nem de traces que expiram. Um avaliador separado verifica se um engenheiro que não conhece o sistema consegue entender o que aconteceu e por que isso importa, se gráficos úteis foram mantidos e se as evidências sustentam a próxima etapa proposta.

- Tecnologia: testes retrospectivos, snapshots de tarefas, avaliador separado.
- Como começar: crie um conjunto de casos de teste a partir de incidentes já resolvidos e execute-os novamente ao alterar a habilidade ou o modelo.

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Transforme falhas recorrentes em autorreparo

Os agentes precisam de monitoramento tanto quanto os serviços que investigam. Um profiler com defeito ou uma permissão ausente pode impedir que um agente verifique o que causou uma lentidão. Essas falhas podem ser difíceis de identificar no relatório final.

A equipe executa um agente todos os dias para examinar mensagens e logs de execuções recentes em busca de falhas nas ferramentas e erros de acesso. Usa a Performance Factory para se autorreparar e corrigir os problemas descobertos por essa verificação. Quando o mesmo erro de ferramenta bloqueia várias investigações, o agente cria uma tarefa para corrigi-lo. Se a causa estiver clara, um agente propõe uma correção, e um engenheiro revisa a mudança e decide se deve integrá-la.

Depois de integrar mudanças como essa, também se usam avaliações para verificar se os agentes conseguem superar a etapa que antes os bloqueava.

- Tecnologia: agente de monitoramento diário, tarefas de correção, avaliações de regressão.
- Como começar: configure um agente para examinar logs de execuções recentes em busca de falhas de ferramenta e crie tarefas para corrigi-las.

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Próximos passos: aplicações mais amplas

O Fluxo de Regressão é apenas uma aplicação do padrão de fábrica de agentes que conduz tarefas por estados explícitos. Os agentes fazem a tarefa avançar quando há mais trabalho pronto; revisores separados questionam as conclusões; engenheiros intervêm quando a próxima decisão exige discernimento. Outros fluxos de trabalho podem reutilizar a mesma estrutura com estados, instruções e eventos diferentes.

A Performance Factory pode coordenar agentes entre fluxos, com agentes de um fluxo criando tarefas para outro. Atualmente, o Fluxo de Regressão começa quando um alerta é disparado. A equipe está desenvolvendo formas mais proativas de a Performance Factory encontrar lentidões e oportunidades de otimização mesmo quando nenhum alerta é disparado, usando o grande volume de dados detalhados de desempenho já coletados para identificar regressões que os alertas deixam passar.

Ao comparar diferentes tipos de dados — lotes de perfis de CPU e memória, dumps de heap e traces de requisições entre versões —, um agente pode perceber um pequeno aumento no uso de CPU para uma determinada requisição e abrir uma tarefa no Fluxo de Regressão. A equipe também está trabalhando em testes sintéticos de desempenho para que os agentes possam medir os resultados das correções propostas e ajustá-las antes de pedir a revisão de um engenheiro, e explorando como os agentes poderiam usar outras ferramentas de revisão com agentes de IA para identificar mudanças de baixo risco e, futuramente, implantar essas correções sem intervenção humana.

- Tecnologia: coordenação entre fluxos, análise proativa de dados de desempenho, testes sintéticos.
- Como começar: identifique um fluxo que já funciona e replique a estrutura para outro tipo de tarefa, mudando apenas estados e instruções.

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Cuidados

- Em uma revisão manual de 100 sugestões de causa raiz, a equipe classificou 70% como corretas; os outros 30% precisavam de mais refinamento ou não estabeleciam plenamente a causalidade. Não trate o diagnóstico do agente como definitivo.
- Acertar nas correções tem sido mais difícil do que encontrar a causa: mudanças propostas pelos agentes às vezes são mais complicadas do que o necessário ou introduzem novos problemas.
- Algumas correções exigem decisões de arquitetura em nível mais amplo (por exemplo, adicionar um cache pode introduzir dados desatualizados). Essas decisões se beneficiam da orientação de um engenheiro que conheça o serviço.
- Testes com dados históricos exigem cuidado: métricas e traces expiram, e evidências coletadas após a recuperação podem revelar a causa. Entenda quais evidências estavam disponíveis para o investigador antes de confiar no resultado.
- Na avaliação feita pela equipe, o agente não pode usar memórias salvas, ler o relatório do incidente nem ver resultados de execuções anteriores. A transcrição também é inspecionada depois, em busca de informações que possam ter comprometido o teste.
- Um profiler com defeito ou uma permissão ausente pode impedir que um agente verifique o que causou uma lentidão. Monitore as ferramentas dos agentes, não só os serviços que eles investigam.

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Glossário

- Agente: programa de IA que executa tarefas de forma autônoma, seguindo instruções e usando ferramentas.
- Codex: ferramenta de IA da OpenAI para desenvolvimento de software, acessível em chatgpt.com/codex.
- Fluxo de Regressão: fluxo de trabalho da Performance Factory que conduz uma regressão de desempenho da detecção à verificação de recuperação.
- Habilidade (skill): conjunto de instruções que informa ao Codex quais ferramentas existem, quando usá-las e como investigar. Exemplo: perf-forensics.
- Performance Factory: sistema da OpenAI que usa agentes do Codex para encontrar e corrigir regressões de desempenho de ponta a ponta.
- Profiler: ferramenta que analisa o desempenho de um programa, identificando onde o tempo de CPU ou a memória são mais consumidos.
- Regressão: piora no desempenho de um serviço que antes funcionava melhor, geralmente causada por uma mudança recente.
- Revisão adversarial: sessão separada do Codex que tenta refutar o diagnóstico ou a correção proposta, testando cenários contrafactuais.
- Serviço de tarefas: componente da Performance Factory onde engenheiros definem fluxos de trabalho com arquivos de configuração e prompts em Markdown.
- Tarefa com estado: unidade de trabalho que mantém seu status e descobertas entre etapas, permitindo retomada após revisão ou implantação.
- Trace: registro detalhado do caminho de uma requisição através de vários serviços, usado para diagnosticar lentidão.

## Para onde ir depois

- Identifique os três problemas de desempenho mais recorrentes no seu serviço e crie uma ferramenta para o mais frequente, como a equipe fez com profilers de CPU e de alocação.
- Documente o método de investigação da sua equipe em uma habilidade que o Codex possa ler, e teste com regressões já resolvidas.
- Configure um alerta para abrir uma sessão do Codex automaticamente e publicar o diagnóstico no canal da equipe.
- Defina um fluxo com estados explícitos e crie tarefas que mantenham estado entre etapas.
- Adicione uma etapa de revisão adversarial onde um agente separado tenta refutar o diagnóstico proposto.
- Crie um conjunto de casos de teste a partir de incidentes já resolvidos para avaliar mudanças na habilidade ou no modelo.
- Leia o artigo completo da OpenAI sobre a Performance Factory: https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Além do vídeo

- O artigo menciona que a equipe espera que outras equipes de serviços aprendam com seu processo ao adotar fluxos de trabalho com agentes de IA em outras áreas.
- O artigo lista outros textos relacionados da OpenAI: «Por dentro do sandbox do Codex», «Escalando o Git na OpenAI» e «Escalando o armazenamento online para mais de 1 bilhão de usuários do ChatGPT (Parte II)».
