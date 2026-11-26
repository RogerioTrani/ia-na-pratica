# Vercel abre o eve Software Factory, fábrica de agentes no GitHub

_2026-11-23 · reportagem_

A Vercel abriu o eve Software Factory, um modelo de fábrica de software em que agentes de IA acompanham uma tarefa da entrada até a entrega de um pull request em rascunho. O Foreman organiza a fila, enquanto outros agentes classificam, planejam, escrevem o código e participam da verificação. O critério de pronto e os testes acompanham o trabalho desde o ticket, e a revisão usa um modelo da OpenAI para conferir o código produzido por um modelo da Anthropic. Depois de ler, você vai entender o fluxo, reconhecer os pontos de conferência e saber por onde começar a ajustar o seu próprio processo.

## O contexto

Uma fábrica de software organiza o desenvolvimento como um fluxo de produção. A demanda entra num formato comum, percorre etapas definidas e chega ao final com um critério de pronto. Essa estrutura dá um papel a cada agente e uma referência para saber quando a tarefa pode seguir.

Usar IA apenas para escrever código cobre uma etapa desse caminho. O modelo da Vercel reúne entrada, orquestração e verificação no mesmo processo. A pessoa continua responsável pela decisão final sobre a alteração.

Fonte: <https://github.com/vercel-labs/eve-software-factory-template>

## O fato: a Vercel abre o eve Software Factory

A Vercel abriu no GitHub o modelo eve Software Factory. O agente chefe desse modelo se chama Foreman. Para colocar uma tarefa no fluxo, você põe a etiqueta factory numa issue do GitHub.

Um agente classifica, outro planeja e outro escreve o código. O resultado chega como um pull request em rascunho, depois de passar pela verificação. A aprovação e o merge ficam com você.

Fonte: <https://github.com/vercel-labs/eve-software-factory-template>

## A entrada: tudo vira ticket

O ticket é a peça que anda pela fábrica. Ele padroniza a demanda antes da execução, seja um pedido de cliente, um bug reclamado no Discord ou uma ideia sua. A origem muda, mas o trabalho passa a ter um registro comum.

O critério de pronto já faz parte dessa entrada. Ele diz o que precisa ser atendido para a tarefa ser considerada concluída. Assim, quem executa e quem confere trabalham com a mesma referência desde o começo.

Fonte: <https://github.com/vercel-labs/eve-software-factory-template>

## O orquestrador: Foreman coordena a fila

Foreman é o agente chefe, ou orquestrador, do modelo da Vercel. Ele recebe os tickets, enxerga as dependências e decide o que pode avançar ao mesmo tempo e o que precisa esperar. O trabalho é entregue aos agentes que executam cada etapa.

Dependência é a relação em que uma tarefa precisa da conclusão de outra. O orquestrador segura o que precisa esperar e libera o que pode andar em paralelo. A distribuição deixa de ser feita tarefa por tarefa por você e passa pelo agente chefe.

Fonte: <https://github.com/vercel-labs/eve-software-factory-template>

## A verificação começa no ticket

O critério de pronto nasce no ticket e orienta a verificação ao longo do processo. Os agentes escrevem os testes, e o código passa por eles antes de chegar a você. A conferência acompanha a produção.

Um teste é uma verificação do comportamento esperado do código. Ele permite conferir durante o fluxo se o trabalho corresponde ao que foi pedido. Quando o critério de pronto só aparece no final, a descoberta de um desencontro chega tarde; defini-lo no ticket ajuda a identificar isso antes da entrega.

Fonte: <https://github.com/vercel-labs/eve-software-factory-template>

## O fluxo no GitHub

O fluxo começa na issue do GitHub com a etiqueta factory. A partir daí, a classificação organiza a tarefa, o planejamento prepara o caminho e a programação produz o código. O Foreman coordena essas etapas de acordo com a fila e as dependências.

A verificação inclui os testes escritos pelos agentes e a revisão do código produzido. O resultado chega a você como um pull request em rascunho. Antes disso, classificar, planejar, programar e revisar já aconteceu dentro da fábrica.

Fonte: <https://github.com/vercel-labs/eve-software-factory-template>

## A revisão independente

O código sai de um modelo da Anthropic. O revisor usa um modelo da OpenAI e confere o diff real, que é o conjunto das alterações feitas no código. Ele não vê o raciocínio de quem escreveu.

A conferência parte das alterações produzidas. Isso permite ao revisor examinar o resultado sem depender da explicação de quem programou. A revisão é independente nesse fluxo, e a decisão de aceitar a alteração continua humana.

Fonte: <https://vercel.com/kb/guide/eve-software-factory>

## A entrega: um pull request em rascunho

Um pull request é uma proposta de alteração de código aberta para revisão. No modelo da Vercel, ele chega em rascunho. Esse estado separa o trabalho produzido pelos agentes da aprovação final.

Você revisa o resultado, marca o pull request como pronto e faz o merge. O merge integra a alteração aceita ao código principal. A fábrica executou o percurso, e a decisão final fica com você.

Fonte: <https://github.com/vercel-labs/eve-software-factory-template>

## Como funciona na prática

Imagine que um cliente relata um bug. A reclamação vira um ticket, e o critério de pronto fica definido nessa entrada. Quando a tarefa é representada por uma issue no GitHub, você põe a etiqueta factory para iniciar o fluxo.

O Foreman organiza a fila e olha as dependências. Um agente classifica, outro planeja e outro escreve o código. Os agentes também escrevem os testes, e o código passa pela verificação antes da entrega.

O revisor usa um modelo da OpenAI para examinar o diff do código produzido por um modelo da Anthropic, sem ver o raciocínio de quem escreveu. Você recebe um pull request em rascunho, confere o resultado e decide se marca como pronto e faz o merge.

Fonte: <https://github.com/vercel-labs/eve-software-factory-template>

## Código aberto e instalação com um clique

O Foreman tem licença MIT e é de código aberto. A Vercel oferece instalação com um clique em vercel.fyi/eve-software-factory. Também há uma página oficial do modelo para essa implantação.

Código aberto permite consultar e adaptar o código conforme a licença. Ainda assim, uma fábrica de software se constrói aos poucos. A instalação é o ponto de partida; os ajustes do fluxo acontecem com o tempo.

- Repositório oficial do modelo: https://github.com/vercel-labs/eve-software-factory-template
- Instalação com um clique: vercel.fyi/eve-software-factory
- Página oficial do modelo na Vercel: https://vercel.com/templates/eve/eve-software-factory

Fonte: <https://vercel.com/kb/guide/eve-software-factory>

## O que você pode fazer

O primeiro uso pode seguir o caminho que o modelo já propõe. Cada ação abaixo tem um ponto de conferência para você saber se a etapa foi concluída.

1. No repositório oficial do eve Software Factory, reconheça o modelo e o nome do agente chefe, Foreman. O resultado é usar a referência correta antes de instalar.
2. Na página oficial de instalação da Vercel, use a opção com um clique. O resultado esperado é instalar o Foreman pela Vercel.
3. Na entrada do seu fluxo de trabalho, transforme a demanda num ticket com o critério de pronto definido. O resultado é uma tarefa com a condição de conclusão estabelecida antes da execução.
4. Na issue do GitHub que representa a tarefa, ponha a etiqueta factory. O resultado esperado é acionar a classificação, o planejamento e a programação pelos agentes.
5. Na revisão do resultado, confira o critério do ticket, a passagem do código pelos testes e o diff real. O resultado é uma conferência baseada no que foi definido na entrada e no que foi entregue.
6. Se aprovar, marque o pull request como pronto e faça o merge. O resultado é integrar a alteração depois da sua revisão.

Fonte: <https://vercel.com/kb/guide/eve-software-factory>

## O que conferir

O modelo é aberto e tem instalação com um clique, mas uma fábrica de software continua exigindo ajustes. O ponto central é manter o critério de pronto, os testes e a revisão humana conectados ao longo do fluxo.

- Confira o nome do produto e do agente: o modelo é eve Software Factory, e o agente chefe é Foreman.
- Confira a marca de entrada: o fluxo começa com a etiqueta factory numa issue do GitHub.
- Confira o critério de pronto no ticket e a passagem do código pelos testes antes da entrega.
- Mantenha separados os papéis dos modelos: o código sai de um modelo da Anthropic, e o revisor usa um modelo da OpenAI.
- Trate o pull request em rascunho como trabalho para revisão. A marcação como pronto e o merge continuam sendo decisões suas.
- Ajuste o processo com o tempo. Código aberto e instalação com um clique são o ponto de partida da fábrica.

Fonte: <https://vercel.com/kb/guide/eve-software-factory>

## Glossário

- Fábrica de software: organização do desenvolvimento em etapas coordenadas, com entrada, verificação e entrega.
- Agente de IA: parte do sistema que recebe uma tarefa e age para executá-la dentro do fluxo.
- Modelo de IA: sistema usado para produzir respostas ou executar tarefas; no fluxo, modelos da Anthropic e da OpenAI têm papéis diferentes.
- Ticket: registro padronizado de uma demanda que percorre as etapas da fábrica.
- Issue do GitHub: item de acompanhamento no GitHub que, neste modelo, recebe a etiqueta factory para iniciar uma tarefa.
- Etiqueta factory: marca posta na issue do GitHub para dar entrada ao fluxo.
- Orquestrador: agente que organiza a fila e distribui o trabalho entre os agentes.
- Foreman: nome do agente chefe, ou orquestrador, no modelo da Vercel.
- Dependência: relação em que uma tarefa precisa da conclusão de outra antes de seguir.
- Critério de pronto: condição definida no ticket para considerar a tarefa concluída.
- Teste: verificação usada para comparar o comportamento do código com o esperado.
- Diff: conjunto das alterações feitas no código que o revisor examina.
- Pull request: proposta de alteração de código submetida à revisão.
- Rascunho: estado de um pull request que ainda está em preparação para aprovação.
- Merge: ação de integrar ao código principal uma alteração que foi aprovada.
- Código aberto: disponibilização do código para consulta e adaptação conforme a licença.
- Licença MIT: licença de código aberto usada pelo Foreman.

Fonte: <https://vercel.com/kb/guide/eve-software-factory>

## Para onde ir depois

Comece pelos endereços oficiais e pratique o fluxo com uma tarefa. O objetivo é acompanhar cada etapa e entender onde entra a sua revisão.

- Abra o repositório oficial do modelo: https://github.com/vercel-labs/eve-software-factory-template
- Use o guia oficial para montar uma fábrica de software com eve: https://vercel.com/kb/guide/eve-software-factory
- Use a página oficial do modelo para a instalação com um clique: https://vercel.com/templates/eve/eve-software-factory
- Consulte a documentação de Software Factories da Vercel: https://vercel.com/docs/agent-resources/software-factory
- Pratique com uma tarefa: defina o critério de pronto no ticket, ponha a etiqueta factory na issue e revise o pull request em rascunho antes de decidir pelo merge.

Fonte: <https://vercel.com/docs/agent-resources/software-factory>
