# Claude Code ganha 79 skills para criar jogos

_2026-11-24 · tutorial_

O repositório Awesome Gamedev Agent Skills instala 79 habilidades de jogos e um roteador no seu agente de código, para que você descreva o jogo e ele carregue as habilidades certas antes de escrever código. A apostila mostra como preparar a pasta, conferir o Node.js, instalar o pacote, abrir o Claude Code, pedir um jogo e testar se o roteador funcionou. Ela também explica o que é uma habilidade, como o roteador escolhe motor e tarefa, quais agentes são compatíveis e onde estão os comandos oficiais. Ao fim, você terá um ambiente pronto para prototipar jogos pequenos e aprender arquitetura de jogos, com a ressalva de revisar tudo antes de publicar.

## O que você terá no fim

Ao final, seu agente de código terá 79 habilidades de desenvolvimento de jogos e um roteador que escolhe as certas para o motor e a tarefa antes de escrever código. Você descreve o jogo em linguagem natural e o agente começa com contexto de motor, gênero e fluxo de trabalho.

O pacote é gratuito, de código aberto, sob licença Apache-2.0, e funciona em 12 motores: Godot, Unity, Unreal, Ebitengine, Phaser, PixiJS, three.js, Bevy, pygame, LÖVE, Defold e Roblox.

O resultado esperado não é um jogo pronto para venda. É um ambiente para prototipar rápido, testar mecânicas e aprender como jogos são montados. Antes de publicar, revise cada linha gerada.

Fonte: <https://github.com/gamedev-skills/awesome-gamedev-agent-skills>

## Como isso funciona

Uma habilidade é um pequeno arquivo de capacidade que o agente carrega só quando precisa. O repositório entrega 79 dessas habilidades mais um roteador.

O roteador faz três coisas: detecta o motor pelos arquivos do projeto, lê o pedido para identificar a tarefa e carrega só as habilidades que combinam. A ordem é motor primeiro, depois conceito, depois cola de gênero. Se você troca de assunto, ele reorganiza.

A detecção é exclusiva para o motor: exatamente um motor. Disciplinas, gêneros e fluxos de trabalho são aditivos. Por exemplo, 'adicionar pulo duplo no jogador Godot' carrega godot-2d-movement e platformer, nada além disso.

O pacote também inclui um fluxo de direção de arte: trava um alvo visual, cria famílias de assets, normaliza saídas de forma determinística e confere dentro do jogo.

Fonte: <https://github.com/gamedev-skills/awesome-gamedev-agent-skills/blob/main/README.md>

## Antes de começar

Separe o básico antes de instalar. Resolver falta agora evita erro no meio do processo.

- Computador com terminal: Windows, macOS ou Linux.
- Claude Code instalado e conta ativa. Documentação de início rápido: code.claude.com/docs/en/quickstart.
- Node.js 22.20 ou mais novo, porque o instalador de habilidades exige essa versão. Download oficial: nodejs.org.
- Conexão com a internet para baixar o pacote.
- Uma pasta vazia para o experimento, para manter habilidades e arquivos do jogo juntos.

Fonte: <https://nodejs.org>

## Passo a passo

Siga na ordem. Cada item traz a ação e o resultado esperado.

1. Abra o terminal em uma pasta nova. Crie uma pasta vazia para o experimento e abra o terminal dentro dela. Resultado esperado: o terminal aberto, com o nome da pasta no caminho exibido. Se o terminal abrir em outro lugar, navegue até a pasta certa antes de seguir.
2. Confira a versão do Node.js. Rode node --version e veja se o número é 22.20 ou maior. Resultado esperado: aparece um número de versão começando com v, igual ou maior que 22.20. Se a versão for menor ou o comando não for encontrado, instale ou atualize o Node.js em nodejs.org, reabra o terminal e repita.
3. Instale o pacote de habilidades. Rode o instalador universal apontando para o repositório oficial. Resultado esperado: o instalador detecta seu agente de código e instala o roteador e as habilidades. Se falhar, confira a versão do Node.js e o nome do repositório; como alternativa, use os dois comandos do plugin do Claude Code.
4. Abra o Claude Code na pasta. Na mesma pasta, digite claude e aperte Enter. Resultado esperado: a tela inicial do Claude Code abre no terminal, pronta para receber sua mensagem. Se o terminal disser que o comando claude não foi encontrado, confirme a instalação do Claude Code e reabra o terminal.
5. Descreva o jogo que você quer. Escreva em linguagem natural o tipo de jogo, onde ele roda e o que o personagem faz. Resultado esperado: o Claude Code começa a trabalhar no pedido, e o roteador escolhe motor e tarefa. Se a resposta vier genérica, refaça o pedido citando o motor, como Godot, Unity ou navegador.
6. Confira se o roteador carregou. Observe a resposta do Claude Code ao seu pedido de jogo. Resultado esperado: antes de escrever código, o Claude Code carrega habilidades de jogos ligadas ao motor e à tarefa. Se nada for carregado, repita a instalação, feche e abra o Claude Code de novo e refaça o pedido.

Fonte: <https://github.com/gamedev-skills/awesome-gamedev-agent-skills/blob/main/README.md>

## Comandos para copiar

Antes de instalar, confira o Node.js com node --version: o número precisa ser 22.20 ou maior. Depois, na pasta do experimento, rode o instalador universal abaixo.

```
npx skills add gamedev-skills/awesome-gamedev-agent-skills
```

Fonte: <https://github.com/gamedev-skills/awesome-gamedev-agent-skills/blob/main/README.md>

## Comandos para copiar (continuação)

Se você usa o Claude Code e prefere instalar como plugin, use estes dois comandos, nesta ordem, no lugar do instalador universal.

```
claude plugin marketplace add gamedev-skills/awesome-gamedev-agent-skills
claude plugin install gamedev@awesome-gamedev-agent-skills
```

Fonte: <https://github.com/gamedev-skills/awesome-gamedev-agent-skills/blob/main/README.md>

## Comandos para um único motor

Para trabalhar em um só motor, com o marketplace já adicionado pelo primeiro comando da alternativa acima, instale o roteador e o pacote do seu motor em vez do pacote completo. O exemplo é para Godot; o comentário no fim da segunda linha lista os outros pacotes que podem entrar no lugar de godot.

```
claude plugin install router@awesome-gamedev-agent-skills
claude plugin install godot@awesome-gamedev-agent-skills    # or: unity · unreal · ebitengine · web-engines · other-engines
```

Fonte: <https://github.com/gamedev-skills/awesome-gamedev-agent-skills/blob/main/README.md>

## Abrir o Claude Code

Com as habilidades instaladas, abra o Claude Code dentro da mesma pasta. Se o terminal disser que o comando não foi encontrado, confirme a instalação e reabra o terminal.

```
claude
```

Fonte: <https://code.claude.com/docs/en/quickstart>

## Exemplo completo

Você pede: 'Quero um jogo de plataforma 2D simples no navegador, com um personagem que anda e pula.'

O esperado é que o roteador identifique o alvo (navegador) e a tarefa (movimento de plataforma) e carregue as habilidades ligadas a eles antes de escrever código. Se não conseguir identificar o motor, ele pergunta.

Você não escolhe habilidade nenhuma. Quanto mais claro o pedido, melhor a escolha. Se a resposta vier genérica, refaça citando o motor, como Godot, Unity ou navegador.

Fonte: <https://github.com/gamedev-skills/awesome-gamedev-agent-skills/blob/main/README.md>

## Prompt pronto

Use como base o pedido "Quero um jogo de plataforma 2D simples no navegador, com um personagem que anda e pula." e troque o tipo de jogo, o lugar onde ele roda e as ações do personagem pelo seu caso.

Fonte: <https://github.com/gamedev-skills/awesome-gamedev-agent-skills/blob/main/README.md>

## Teste de pronto

O teste confirma se a instalação funcionou de verdade, não só se o comando terminou.

- [ ] Antes de escrever código, o Claude Code carrega habilidades de jogos ligadas ao motor e à tarefa.
- [ ] As habilidades vêm ligadas ao motor e à tarefa, não como código solto.
- [ ] Se você viu isso, o roteador está ativo.
- [ ] Se não viu nada sendo carregado, repita a instalação, feche e abra o Claude Code de novo e refaça o pedido.

Fonte: <https://github.com/gamedev-skills/awesome-gamedev-agent-skills>

## Erros comuns e cuidados

A maioria dos problemas vem de versão antiga do Node.js ou de comando digitado de forma diferente.

- A versão do Node.js é o tropeço mais comum. Exija 22.20 ou mais nova; se o comando falhar ou a versão for menor, instale ou atualize em nodejs.org, reabra o terminal e repita.
- Se o terminal disser que o comando claude não foi encontrado, confirme a instalação do Claude Code e reabra o terminal.
- Se a resposta do Claude Code vier genérica, refaça o pedido citando o motor, como Godot, Unity ou navegador.
- O número de acerto do roteador vem dos testes do próprio projeto: 98,7% em 366 pedidos de teste cegos. Trate como referência do projeto, não como garantia.
- Para um jogo de loja, confira cada linha antes de publicar. O pacote serve para prototipar e aprender, não para substituir revisão.
- Se seu agente já tem muitas habilidades, instale só o roteador e o pacote do motor. Agentes listam a descrição de cada habilidade até um limite de tamanho; além dele, algumas descrições são cortadas e a escolha fica mais difícil. No Claude Code o limite é 1% da janela de contexto; aumente com skillListingBudgetFraction, por exemplo 0,02, ou defina caracteres com SLASH_COMMAND_TOOL_CHAR_BUDGET.

Fonte: <https://github.com/gamedev-skills/awesome-gamedev-agent-skills/blob/main/README.md>

## Exemplos do que você pode pedir

Você nunca digita o nome da habilidade. O roteador decide a partir do seu pedido.

- 'Adicionar pulo duplo ao jogador Godot' carrega godot-2d-movement e platformer.
- 'Criar inventário para RPG em Unity' carrega unity-scriptableobjects, rpg e save-systems.
- 'Jogo 2D de quebra-cabeça em Go com Ebitengine' carrega ebitengine-game e puzzle.
- 'Adicionar movimento ao jogador em Defold' carrega defold-core e input-systems.
- 'Roguelike de masmorra procedural em Godot' carrega godot-tilemap, procedural-gen e roguelike.
- 'Fazer personagem, inimigos e tiles em pixel art coesos' carrega create-game-assets e o importador do motor detectado.
- 'Como devo desenhar slots de save?' carrega save-systems.
- 'Publicar meu jogo na itch com butler' carrega itch-publish.

Fonte: <https://github.com/gamedev-skills/awesome-gamedev-agent-skills/blob/main/README.md>

## Agentes compatíveis e instalação alternativa

Os mesmos arquivos SKILL.md carregam nativamente em Claude Code, Cursor, Windsurf, Cline, Codex, Gemini CLI, GitHub Copilot, Kiro e dezenas de outros agentes. A CLI detecta o agente que você já usa.

O instalador universal é npx skills add gamedev-skills/awesome-gamedev-agent-skills. Acrescente --list para pré-visualizar, -g para instalar em todos os projetos ou -a <agente> para mirar uma ferramenta específica.

No Claude Code existe a alternativa de plugin: adicione o marketplace e instale o pacote completo. Se você trabalha em um único motor, instale só o roteador e o pacote desse motor.

Fonte: <https://www.npmjs.com/package/skills>

## O que foi verificado

As habilidades são escritas a partir da documentação oficial dos motores e fixadas em versões atuais: Godot 4.7.2, Unity 6.3 LTS, Unreal 5.8, Phaser 4.2.1, three.js r187, entre outras, verificadas em 11/11/2026.

Exemplos de código foram executados ou compilados nas ferramentas reais para 10 dos 12 motores.

Em 366 pedidos de teste cegos, a habilidade certa carregou em 98,7% dos pedidos que precisavam de uma.

O repositório tinha 9.152 estrelas no GitHub em 16/11/2026.

Fonte: <https://github.com/gamedev-skills/awesome-gamedev-agent-skills/blob/main/README.md>

## Glossário

- Habilidade: pequeno arquivo de capacidade que o agente carrega só quando precisa.
- Roteador: componente que detecta o motor e a tarefa e carrega as habilidades certas.
- Motor de jogo: programa que faz o jogo rodar, como Godot, Unity ou Unreal.
- Agente de código: programa que escreve código com base no seu pedido.
- Node.js: programa que o instalador de habilidades usa para rodar.
- Terminal: janela onde você digita comandos.
- Arquivo SKILL.md: arquivo de habilidade lido pelo agente.
- Estrela no GitHub: marca de favorito dada por usuários ao repositório.

Fonte: <https://github.com/gamedev-skills/awesome-gamedev-agent-skills/blob/main/README.md>

## Plano de 7 dias

- Dia 1: prepare a pasta e confira o Node.js.
- Dia 2: instale o pacote e abra o Claude Code.
- Dia 3: peça um jogo simples e observe o roteador.
- Dia 4: repita com outro motor ou outro gênero.
- Dia 5: teste uma mecânica específica, como pulo duplo.
- Dia 6: revise o código gerado e anote acertos e erros.
- Dia 7: decida o próximo experimento e documente o que aprendeu.

Fonte: <https://github.com/gamedev-skills/awesome-gamedev-agent-skills/blob/main/README.md>

## Para onde ir depois

- Leia o README do repositório para o catálogo completo de 79 habilidades em 9 categorias.
- Consulte docs/INSTALLATION.md para caminhos por ferramenta e instalação manual.
- Consulte docs/COMPATIBILITY.md para a lista de agentes compatíveis.
- Consulte docs/VERSION-SUPPORT.md para as versões de motores suportadas.
- Consulte evals/RESULTS.md para método e limites dos testes de acerto.
- Navegue no catálogo web em gamedev-skills.github.io/awesome-gamedev-agent-skills.
- Teste com um jogo pequeno, veja onde acerta e onde erra, e trate o resultado como começo.

Fonte: <https://github.com/gamedev-skills/awesome-gamedev-agent-skills>

## Links citados

- https://code.claude.com/docs/en/quickstart

## Resumo dos recursos

- A instalação pode ser feita como plugin do Claude Code, com pacote completo ou pacotes menores por motor.
- A CLI aceita --list, -g e -a <agente>.
- A lista de agentes compatíveis inclui Cursor, Windsurf, Cline, Codex, Gemini CLI, GitHub Copilot e Kiro.
- O pacote tem fluxo de direção de arte com alvo visual, famílias de assets e normalização determinística.
- O limite de listagem de habilidades no Claude Code pode ser aumentado com skillListingBudgetFraction ou SLASH_COMMAND_TOOL_CHAR_BUDGET.
- O repositório tem documentação de instalação, compatibilidade, suporte de versões e resultados de avaliação.
- O catálogo completo de 79 habilidades está organizado em 9 categorias e pode ser lido no README ou no site gerado.
