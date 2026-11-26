# Anthropic lança /ship no Claude Code para levar PRs ao merge

_2026-11-24 · noticia_

O /ship é o novo comando do Claude Code que revisa o código, corrige falhas e acompanha o pull request até ele ficar pronto para merge. Ele lida com checks que falham, comentários de revisão e conflitos na junção do código, mas o merge final continua com você. Esta apostila explica os requisitos, o fluxo de uso, os modos de permissão e as condições para o acompanhamento de até 7 dias. Depois da leitura, você saberá preparar a branch, conferir mudanças pendentes e distinguir o /ship do Claude Ship do plano Team.

## O fato

A Anthropic lançou o /ship no Claude Code para preparar pull requests para merge. O anúncio informa que o recurso está sendo distribuído no aplicativo desktop.

O comando roda /code-review, corrige os bugs que considera reais e acompanha o PR enquanto trabalha em checks que falham, comentários de revisão e conflitos de merge. Quando o PR fica pronto, ele avisa e deixa a junção do código com você.

O mesmo anúncio apresenta o Claude Ship, em beta, para o plano Team. Nesse recorte, a ferramenta revisa e corrige PRs em todo um repositório do GitHub e aprova aqueles que a política da equipe permite.

Fonte: <https://code.claude.com/docs/en/ship-command.md>

## Por que isso importa

Escrever código costuma ser a parte rápida. A aprovação ainda pode travar o trabalho: um teste falha, um colega pede outra alteração ou surge um conflito ao juntar as mudanças. Cada situação traz você de volta para um PR que já parecia concluído.

Um pull request reúne as alterações de uma branch para revisão e junção ao código principal. Os checks automatizados procuram falhas, e os revisores avaliam se a mudança atende ao que o projeto precisa. Essas etapas existem para reduzir problemas antes que o código entre no fluxo principal.

O /ship cuida do retrabalho que aparece durante essa aprovação. Ele pode corrigir uma falha, responder a um comentário e pedir uma nova revisão. Você acompanha o resultado e mantém as regras do repositório, incluindo as revisões e os checks obrigatórios.

Fonte: <https://code.claude.com/docs/en/ship-command.md>

## Revisão do código e correção de bugs

O /ship começa executando /code-review. Depois da revisão, ele corrige os problemas que considera falhas reais. A expressão considera reais é importante: a ferramenta aplica um julgamento sobre o que encontrou, e você ainda pode examinar as alterações antes do merge.

Na versão 2.1.328, o /code-review passou a relatar, na maioria dos modelos, apenas bugs e violações de CLAUDE.md. Os achados recebem os rótulos Important, para problema importante, Pre-existing, para problema preexistente, e Nit, para detalhe menor. O anúncio indica /simplify quando se busca sugestões de limpeza do código.

Esse recorte concentra a revisão em defeitos e descumprimentos das orientações do projeto. Para quem recebe o PR, isso ajuda a separar uma correção necessária de uma preferência pessoal de estilo. As correções continuam sujeitas às verificações e à revisão exigidas pelo repositório.

Fonte: <https://code.claude.com/docs/en/ship-command.md>

## Como o acompanhamento do PR funciona

Depois da revisão inicial, o /ship monitora o pull request e trabalha nos obstáculos que aparecem. Aparecem três situações: um check que falha, um comentário que pede mudança e um conflito de merge. Cada uma exige uma resposta diferente para o PR avançar.

No fluxo apresentado, o Claude envia correções, responde ao revisor como autor, resolve a thread de conversa e pede outra revisão. Quando um colega solicita uma alteração, ele faz a mudança e retoma o diálogo. Essas ações formam o ciclo de acompanhamento até a aprovação.

O monitoramento pode durar até 7 dias, com a sessão local aberta e o computador ligado e acordado. Mantenha também a sessão em primeiro plano e a branch aberta. Ao ficar pronto, o Claude informa o estado do PR e deixa o merge para você.

Fonte: <https://code.claude.com/docs/en/ship-command.md>

## Mudanças pendentes e abertura do PR

O /ship também pode fazer commit e push das mudanças que ainda não foram registradas ou enviadas. A exceção é o repositório público. Se você ainda não tiver um pull request aberto, o comando pode criar um.

Por isso, vale conferir o git status antes de começar. O status mostra o que está pendente e ajuda a decidir se aquele trabalho deve entrar no fluxo. Em um repositório público, a orientação é fazer commit das mudanças em uma branch antes do envio.

Commit registra um conjunto de alterações no histórico local, e push envia esse registro para o repositório remoto. Como o /ship pode executar essas ações, o ponto de partida do comando pode incluir trabalho que você ainda não tinha registrado ou enviado.

Fonte: <https://code.claude.com/docs/en/ship-command.md>

## Claude Ship no plano Team

O Claude Ship é a oferta em beta voltada ao plano Team. Ele pode revisar e corrigir pull requests em todo um repositório do GitHub, ampliando o trabalho para além do PR que você está preparando no momento.

Nesse recorte, o Claude Ship também pode aprovar os PRs que a política da equipe permite. A autorização de aprovação e a revisão de todo o repositório pertencem ao Claude Ship do plano Team. O /ship individual prepara o PR e deixa o merge com você.

Beta indica um recurso em fase de teste. Essa condição faz parte da apresentação do Claude Ship e deve acompanhar a leitura das capacidades de revisão e aprovação, sem transferir essas condições para outro plano ou variante.

Fonte: <https://code.claude.com/docs/en/claude-ship.md>

## Antes de começar

O fluxo usa três ferramentas: Claude Code, CLI do GitHub e git. Cada uma tem uma versão mínima para o uso descrito. O sinal de mais nas versões significa que a versão indicada ou uma posterior atende ao requisito.

Também é preciso estar no projeto e na branch que receberá as mudanças. As regras do repositório continuam valendo durante todo o processo, inclusive as que exigem revisão ou checks antes do merge.

- Atualize o Claude Code para a versão v2.1.330 ou posterior; o resultado esperado é ter uma versão que inclua o fluxo do /ship.
- Tenha a CLI do GitHub na versão 2.63 ou posterior; ela será usada para autenticar o acesso ao GitHub.
- Tenha o git na versão 2.38 ou posterior; ele será usado para branch, status, commit e push.
- Abra a branch que receberá as alterações; o resultado esperado é executar o comando no contexto correto do projeto.

Fonte: <https://code.claude.com/docs/en/ship-command.md>

## Entre no GitHub pela CLI

A CLI do GitHub conecta o terminal ao GitHub. O login é a etapa que autoriza a ferramenta a trabalhar com o repositório durante o fluxo do PR.

Execute o comando no terminal em que você usa o Claude Code e conclua o login. O resultado esperado é ter a conta autenticada antes de rodar o /ship.

```
gh auth login
```

Fonte: <https://code.claude.com/docs/en/ship-command.md>

## Confira a branch e as pendências

O git status mostra as alterações pendentes no projeto. Leia a saída antes de iniciar o /ship, porque o comando pode registrar e enviar esse trabalho.

Se o repositório for público, faça commit das mudanças em uma branch antes do envio. O resultado esperado é você saber exatamente o que está na branch e evitar que trabalho pendente entre no fluxo sem uma decisão consciente.

```
git status
```

Fonte: <https://code.claude.com/docs/en/ship-command.md>

## Passo a passo para rodar o /ship

O fluxo começa com a preparação do ambiente e termina com a sua decisão sobre o merge. O acompanhamento automático depende das permissões e das condições da sessão explicadas nas próximas seções.

1. No terminal do Claude Code, dentro do projeto, confirme as versões mínimas do Claude Code, da CLI do GitHub e do git; o resultado esperado é um ambiente compatível com o /ship.
2. Na mesma sessão, entre no GitHub com o comando de autenticação mostrado antes; o resultado esperado é concluir o login da conta que usará o repositório.
3. Na branch escolhida, consulte as pendências com o comando de status mostrado antes; o resultado esperado é saber quais alterações podem ser registradas e enviadas.
4. Se o repositório for público, faça commit das mudanças nessa branch antes do envio; o resultado esperado é deixar o trabalho pendente na branch usada pelo comando.
5. Execute o /ship no terminal; o resultado esperado é iniciar a revisão do código e abrir um PR ou trabalhar no PR que já existe.
6. Mantenha a sessão local aberta, em primeiro plano, com a branch aberta e o computador ligado e acordado; o resultado esperado é reunir as condições para o acompanhamento.
7. Quando o Claude indicar que o PR está pronto, examine o resultado e faça o merge se as revisões e os checks exigidos tiverem passado; a decisão final continua com você.

```
/ship
```

Fonte: <https://code.claude.com/docs/en/ship-command.md>

## Exemplo completo

Imagine que você terminou uma alteração e já está na branch que será enviada. Depois de conferir o git status e fazer o login no GitHub, você roda o /ship. Ele faz a revisão inicial, corrige os bugs que considera reais e abre um PR ou usa o PR já existente.

Durante o acompanhamento, um check falha. O Claude trabalha na correção e envia a alteração. Em seguida, um colega pede uma mudança em um comentário. O Claude faz o ajuste, responde como autor, resolve a thread e solicita uma nova revisão.

Se surgir um conflito de merge, ele também trata desse obstáculo. Depois que a revisão necessária é concluída e o PR fica pronto, o Claude avisa. Você confere o resultado e decide se faz o merge.

Fonte: <https://code.claude.com/docs/en/ship-command.md>

## Os números

Os números definem o tempo máximo de acompanhamento e os requisitos das ferramentas. Eles não medem quanto tempo o comando economiza nem garantem que um PR será aprovado.

- O acompanhamento pode durar até 7 dias, com a sessão local aberta e o computador ligado e acordado; é um limite máximo condicionado, não uma promessa de conclusão do PR.
- Claude Code v2.1.330+ é a versão mínima para o fluxo; o sinal + indica que uma versão posterior também atende ao requisito.
- A CLI do GitHub 2.63+ é a versão mínima da ferramenta de linha de comando usada na autenticação; o número não informa a velocidade do PR.
- O git 2.38+ é a versão mínima do sistema de versionamento usado para branch, status, commit e push; o número não altera as regras de aprovação do repositório.

Fonte: <https://code.claude.com/docs/en/ship-command.md>

## Permissões e condições do acompanhamento

Os modos de permissão definem quando o Claude pode agir sem uma nova confirmação sua. O modo auto permite que ele aja sem perguntar. Nos outros modos, o /ship espera a sua intervenção para continuar.

O monitoramento também depende da sessão. Ela precisa permanecer aberta, em primeiro plano, com a branch aberta e o computador ligado e acordado. Essas condições valem para todo o período de acompanhamento.

No Windows nativo, o acompanhamento não roda. Essa restrição se refere ao monitoramento contínuo do PR. As regras do repositório continuam valendo em qualquer ambiente: revisões e checks obrigatórios precisam passar antes do merge.

- Use o modo auto se quiser que o comando aja sem perguntar durante o fluxo.
- Nos outros modos de permissão, fique disponível para responder quando o /ship esperar por você.
- Mantenha a sessão em primeiro plano e a branch aberta para preservar as condições do acompanhamento.
- No Windows nativo, não conte com a etapa de monitoramento descrita para o /ship.

Fonte: <https://code.claude.com/docs/en/ship-command.md>

## O que muda para você

O trabalho passa de atender cada retorno do PR para acompanhar as correções e conferir o resultado. O /ship assume a sequência de ajustes e respostas que aparece após a revisão inicial.

Você continua responsável pela branch, pelas mudanças pendentes, pelos modos de permissão e pela decisão de merge. Também precisa garantir que as exigências do repositório sejam cumpridas antes de juntar o código.

Exemplo: quando um check falha ou um revisor pede uma alteração, o comando pode retomar o PR, corrigir o problema e pedir outra revisão enquanto a sessão atende às condições. Você acompanha esse ciclo e faz a conferência final.

Fonte: <https://code.claude.com/docs/en/ship-command.md>

## O que conferir antes de confiar

A automação muda quem executa as tarefas repetitivas, mas o PR continua sujeito às regras do projeto. Uma correção feita pelo Claude só entra no fluxo principal depois de cumprir essas regras.

A conferência final continua necessária porque o comando corrige o que considera falha real e pode atuar sobre mudanças pendentes. Veja o que foi alterado antes de aprovar a junção.

- Confirme se o Claude Code está na versão v2.1.330 ou posterior, a CLI do GitHub na 2.63 ou posterior e o git na 2.38 ou posterior.
- Leia o git status antes de rodar o comando para saber quais mudanças pendentes podem ser registradas e enviadas.
- Em repositório público, faça commit das mudanças em uma branch antes do envio.
- Confirme se você está na branch e na conta de GitHub que pretende usar no PR.
- Verifique a plataforma, o modo de permissão e as condições da sessão antes de depender do acompanhamento.
- Confirme se as revisões e os checks exigidos pelas regras do repositório passaram antes do merge.
- Se estiver usando o Claude Ship do plano Team, considere o recorte em beta e a política da equipe que autoriza aprovações.
- Examine as correções e o estado final do PR; o merge continua sendo uma decisão sua.

Fonte: <https://code.claude.com/docs/en/ship-command.md>

## Glossário

- /ship: comando do Claude Code que revisa o código, corrige falhas e acompanha o PR até ele ficar pronto para merge.
- Claude Ship: oferta em beta do plano Team que revisa e corrige PRs em um repositório e aprova os que a política da equipe permite.
- Pull request ou PR: proposta que reúne alterações de uma branch para revisão e junção ao código principal.
- Branch: linha de trabalho do repositório onde as alterações são desenvolvidas antes da junção.
- Merge: ação de juntar as alterações de uma branch ao código de destino.
- Commit: registro de um conjunto de alterações no histórico local do git.
- Push: envio dos commits locais para o repositório remoto.
- git status: comando que mostra as alterações pendentes no projeto.
- Check: verificação automatizada usada para validar as alterações antes da junção.
- CI: integração contínua, prática de executar verificações automatizadas sobre as mudanças de código.
- Comentário de revisão: observação de um revisor que pode pedir ajustes ou apontar um problema.
- Thread de revisão: conversa organizada em torno de um comentário ou achado do PR.
- Conflito de merge: situação em que as mudanças precisam ser ajustadas para que a junção possa continuar.
- Sessão local: execução do Claude Code que precisa permanecer aberta para o monitoramento descrito.
- Modo auto: modo de permissão em que o Claude age sem perguntar antes de agir.
- Regras de branch: exigências do repositório, como revisões e checks, que precisam ser atendidas antes do merge.
- CLAUDE.md: arquivo com orientações para o Claude Code; a revisão pode apontar descumprimentos dessas orientações.
- Beta: versão de um recurso disponibilizada para teste e sujeita a mudanças.

Fonte: <https://code.claude.com/docs/en/ship-command.md>

## Para onde ir depois

O próximo passo é preparar uma branch, conferir as pendências e executar o /ship em um projeto em que você possa acompanhar as alterações. Observe como a revisão inicial se transforma no ciclo de checks, comentários e aprovação.

Pratique mantendo a sessão nas condições exigidas e revise o PR antes do merge. Se o seu interesse for a revisão de todo o repositório e a aprovação conforme a política da equipe, leia a documentação específica do Claude Ship do plano Team.

- Atualize as três ferramentas para as versões mínimas e faça o login no GitHub antes do primeiro uso.
- Use o /ship em uma branch e acompanhe o PR desde a revisão inicial até a indicação de que está pronto.
- Leia a documentação oficial do /ship em https://code.claude.com/docs/en/ship-command.md e a do Claude Ship em https://code.claude.com/docs/en/claude-ship.md.
- Consulte os modos de permissão em https://code.claude.com/docs/en/permission-modes.md para escolher como o comando deve pedir confirmações.
- Acesse o repositório oficial do Claude Code em https://github.com/anthropics/claude-code para acompanhar o projeto.

Fonte: <https://code.claude.com/docs/en/ship-command.md>

## Além do vídeo

- Mods do aplicativo desktop passaram a mudar o fundo e o tema, usando $.theme.set e um gancho de renderização Backdrop.
- Mods também podem usar dados da sessão com $.session.usage(); o exemplo do anúncio acumula neve conforme a janela de contexto se enche e derrete depois de /compact.
- O plugin theme-examples reúne exemplos de temas e pode ser instalado em Customize > Plugins pesquisando theme.
- O painel lateral do desktop agora abre Files, Changes, Terminal e outras ferramentas em abas; é possível mover uma aba ou abri-la em outra janela.
- Projects ganhou um coordenador que executa outras sessões, e /btw e /fork também funcionam nele; está em beta pública e sendo distribuído para Pro, Max e Ultra.
- iPhone Duo passou a funcionar no simulador de iOS; está em beta pública no desktop e exige Mac com Xcode 27.1 ou posterior.
- O canal Latest libera atualizações mais cedo no desktop e pode trazer versões menos confiáveis; Stable continua sendo o padrão.
- O anúncio também compartilha práticas de verificação da equipe do Claude Code, com testes, benchmarks e execuções de ponta a ponta mais baratos de pedir ao Claude.
- Code Mode permite que o Claude escreva um script que executa várias chamadas de ferramenta em sequência ou em paralelo; funciona apenas no terminal, exige v2.1.323 ou posterior, está experimental e começa desativado.
- Na versão 2.1.329, /tasks passou a mostrar tarefas agendadas, /loop wakeups, objetivo e forks, além do trabalho em segundo plano; é possível interromper uma tarefa com x e confirmação.
- As versões 2.1.327 adicionaram servidores MCP via stdin, inclusão de arquivos e pastas no chat do VS Code e a indicação de arquivos de configuração quebrados pelo /status.
- Outras mudanças incluem reagendamento de tarefas salvas e correção do /usage na 2.1.329, melhores sinais para hooks e sessões longas na 2.1.326, permissões de comandos em sandbox na 2.1.325 e um limite para loops descontrolados do Code Mode na 2.1.329.
