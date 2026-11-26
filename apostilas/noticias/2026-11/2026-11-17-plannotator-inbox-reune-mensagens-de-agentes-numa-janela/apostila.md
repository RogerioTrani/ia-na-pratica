# Plannotator Inbox reúne mensagens de agentes numa janela

_2026-11-17 · noticia_

O Plannotator Inbox é uma janela local onde agentes de programação deixam mensagens, perguntas e arquivos enquanto continuam trabalhando. Você responde quando tiver um momento, e a resposta volta à mesma sessão que perguntou. O Plannotator roda no navegador, tem código aberto no GitHub e conecta dez agentes de programação mais assistentes pessoais. Esta apostila explica o que é, como funciona, quais agentes conectam, como instalar e o que conferir antes de confiar. Ao final você saberá abrir o Inbox, responder um agente e manter o fluxo de trabalho sem sessões travadas.

## O fato

O Plannotator é um espaço local, aberto no navegador, para revisar o que agentes de IA de programação produzem. O código é aberto e fica no GitHub, em github.com/backnotprop/plannotator. O site oficial é plannotator.ai.

A novidade é o Plannotator Inbox: uma janela local onde agentes deixam recados, perguntas e arquivos enquanto continuam trabalhando. Você responde quando tiver um momento.

O projeto é mantido por backnotprop e licenciado sob Apache 2.0 ou MIT, à escolha.

Fonte: <https://github.com/backnotprop/plannotator>

## Por que isso importa

Quem usa vários agentes de programação ao mesmo tempo conhece o problema: perguntas se perdem em terminais diferentes, sessões ficam paradas esperando resposta e o trabalho para.

O Inbox tenta juntar tudo isso em um só lugar. Ele é a camada de revisão entre você e o trabalho com vários agentes: decisões, protótipos, variações, planos e o que mais precisar para se manter a par.

Nenhuma sessão de agente fica presa esperando por você. Ao enviar, a resposta chega à mesma sessão que perguntou, como a próxima mensagem da conversa.

Fonte: <https://github.com/backnotprop/plannotator>

## Plannotator Inbox: o que é

O Inbox é uma janela local onde seus agentes deixam mensagens, perguntas, arquivos e revisões guiadas enquanto seguem trabalhando. Você responde uma pergunta com um clique, anota um arquivo e aperta Send quando puder.

A página oficial do Inbox é plannotator.ai/inbox/ e a documentação de referência está em plannotator.ai/docs/reference/inbox/.

```
plannotator inbox
```

Fonte: <https://plannotator.ai/inbox/>

## Como responder

1. Abra o Inbox com o comando acima. A janela abre no navegador, no endereço local.
2. Leia a mensagem ou pergunta que o agente deixou.
3. Responda uma pergunta com um clique na opção desejada.
4. Se precisar, anote o arquivo anexado antes de enviar.
5. Aperte Send. A resposta volta à sessão que perguntou, como o próximo turno da conversa.
6. Confira se a sessão do agente recebeu a resposta e seguiu trabalhando.

Fonte: <https://plannotator.ai/inbox/>

## Conexão com agentes

Claude Code, Pi e OpenCode se conectam ao Inbox pelos plugins do Plannotator. As respostas chegam como o próximo turno dessas sessões.

Qualquer outro agente alcança o Inbox pelo protocolo MCP, com o comando abaixo. O comando `plannotator inbox --help` é o guia que o próprio agente lê para se conectar.

```
plannotator inbox mcp
```

Fonte: <https://github.com/backnotprop/plannotator>

## Agentes compatíveis

O Plannotator funciona com dez agentes de programação. O Inbox também atende assistentes pessoais, e os recados de todos podem cair na mesma janela.

- Agentes de programação: Claude Code, Codex, Copilot CLI, Gemini CLI, OpenCode, Kiro, Droid, Amp, DeepSeek Harness e Pi.
- Assistentes pessoais: Grok Bot, Muse, Hermes e OpenClaw.
- A detecção é automática no instalador: ele reconhece os agentes que você já tem e configura cada um.

Fonte: <https://github.com/backnotprop/plannotator>

## Instalação

1. macOS, Linux ou WSL: rode o comando do bloco abaixo.
2. Windows PowerShell: rode a segunda linha do bloco.
3. O instalador baixa o binário do GitHub Releases, detecta os agentes instalados e configura hooks, skills e comandos de cada um.
4. No Claude Code, depois do instalador, rode `/plugin marketplace add backnotprop/plannotator` e `/plugin install plannotator@plannotator`, e reinicie o Claude Code.
5. Para instalar só o binário, sem skills nem configuração por agente: `curl -fsSL https://plannotator.ai/install.sh | bash -s -- --minimal` (ou defina `PLANNOTATOR_MINIMAL=1`).
6. Para fixar uma versão: `curl -fsSL https://plannotator.ai/install.sh | bash -s -- --version vX.Y.Z`.

```
curl -fsSL https://plannotator.ai/install.sh | bash
irm https://plannotator.ai/install.ps1 | iex
```

Fonte: <https://github.com/backnotprop/plannotator>

## Os números

- 843 forks: cópias do repositório criadas no GitHub.
- 27 watchers: quem acompanha a atividade do repositório.
- 8.817 commits: volume de histórico de desenvolvimento.
- Licença Apache 2.0 ou MIT, à escolha: o uso segue as condições da licença escolhida.
- Sem telemetria nem análise de uso: planos, diffs, anotações, rascunhos, histórico e configuração ficam locais por padrão.
- Cada superfície do app verifica o GitHub em busca da versão mais recente ao carregar. Isso envia apenas uma requisição comum, sem conteúdo de plano ou revisão, e não há configuração para desligar essa verificação.

Fonte: <https://github.com/backnotprop/plannotator>

## O que muda para você

Antes do Inbox, perguntas de agentes diferentes se perdem em terminais diferentes e sessões ficam paradas. Com o Inbox, tudo cai na mesma janela e você responde quando puder.

Exemplo: você roda um agente em Codex e outro em Claude Code. Os dois deixam perguntas no Inbox. Você responde a do Codex com um clique, anota o arquivo do Claude Code e aperta Send. Cada resposta volta à sessão que perguntou, como a próxima mensagem da conversa, e nenhuma sessão ficou travada esperando.

O Inbox também atende assistentes pessoais como Grok Bot, Muse, Hermes e OpenClaw, então recados de todos podem cair na mesma janela.

Fonte: <https://github.com/backnotprop/plannotator>

## O que fazer hoje

1. Instale o Plannotator com o comando do seu sistema.
2. Se você usa Claude Code, rode os dois comandos de plugin e reinicie.
3. Abra o Inbox com `plannotator inbox` e confira se a janela abre no navegador.
4. Conecte um agente: se for Claude Code, Pi ou OpenCode, o plugin já cuida; para os demais, use `plannotator inbox mcp` no agente.
5. Peça ao agente que deixe uma pergunta no Inbox e responda com um clique para testar o fluxo de ida e volta.
6. Leia `plannotator inbox --help` se o agente precisar de instruções de conexão.

```
plannotator inbox
```

Fonte: <https://github.com/backnotprop/plannotator>

## O que conferir

- O armazenamento é local por padrão: planos, diffs, anotações e configuração ficam na sua máquina, normalmente em `~/.plannotator`. Compartilhamento e Workspaces têm regras próprias.
- Não há telemetria nem análise de uso, mas há acesso à rede: verificação de versão no GitHub ao carregar as telas de revisão e, no code review local, consulta ao origin com `git ls-remote` para detectar o branch padrão e uma base desatualizada.
- Conteúdo sai do fluxo local quando um recurso de rede precisa: anotar uma URL (por padrão via Jina Reader em páginas públicas), revisar PRs ou MRs, usar Ask AI ou agentes de revisão (a pergunta e o contexto relevante vão ao provedor configurado) e compartilhar.
- Em modo remoto (SSH, devcontainer, Docker) o servidor escuta em todas as interfaces (`0.0.0.0`) sem login. Mantenha a porta fechada para redes que você não confia.
- O compartilhamento por link aberto é legado e está a caminho de suporte descontinuado; Workspaces é o caminho principal para times. Compartilhamentos pequenos em Markdown vão no fragmento da URL sem criptografia: quem tiver o link completo pode ler.
- Dados locais não são recuperáveis se você os apagar: `plannotator uninstall --purge` desinstala, remove os dados locais conhecidos e pede que você digite `purge` para confirmar. Faça backup antes.
- Compartilhamento pode ser desligado por completo com `PLANNOTATOR_SHARE=disabled`.

Fonte: <https://github.com/backnotprop/plannotator>

## Glossário

- Inbox: janela local onde agentes deixam mensagens, perguntas, arquivos e revisões guiadas.
- Agente de programação: ferramenta de IA que escreve ou revisa código, como Claude Code, Codex ou OpenCode.
- MCP: protocolo que permite a um agente se conectar a ferramentas externas, usado pelo Inbox para agentes sem plugin próprio.
- Plugin: extensão instalada no agente que conecta o Inbox diretamente.
- Sessão: uma conversa em andamento com um agente; a resposta do Inbox volta a ela como próximo turno.
- Hook: gatilho que abre o Plannotator automaticamente quando o agente cria um plano.
- Workspaces: produto hospedado do Plannotator para colaboração em equipe, separado do app local de código aberto.

Fonte: <https://github.com/backnotprop/plannotator>

## Para onde ir depois

- Repositório oficial: https://github.com/backnotprop/plannotator
- Site oficial: https://plannotator.ai/
- Página do Inbox: https://plannotator.ai/inbox/
- Documentação do Inbox: https://plannotator.ai/docs/reference/inbox/
- Instale o Plannotator e rode `plannotator inbox` para ver a janela funcionando.
- Teste com dois agentes diferentes para sentir o fluxo de respostas voltando a cada sessão.

Fonte: <https://github.com/backnotprop/plannotator>

## Comandos e blocos para copiar

```
curl -fsSL https://plannotator.ai/install.sh | bash

# Windows PowerShell
irm https://plannotator.ai/install.ps1 | iex
```

## Além do vídeo

- Comandos de anotação: /plannotator-annotate para arquivos, pastas e URLs, /plannotator-last para a última resposta do agente.
- Code review no Plannotator: /plannotator-review para diffs locais ou URLs de PR/MR do GitHub e GitLab.
- Plan mode: abre o Plannotator automaticamente quando o agente cria um plano, via hooks.
- CLI de sessões: plannotator sessions, plannotator sessions --open 1 e plannotator archive.
- Integrações: VS Code, Obsidian, Bear e Notion para salvar planos aprovados.
- Herdr Annotate e Plannotator TUI para revisão no terminal.
- Controles Vim opcionais em Settings para navegação por teclado.
- Modo remoto por SSH, devcontainer ou Docker com PLANNOTATOR_REMOTE e PLANNOTATOR_PORT.
- Verificação de atestação com --verify-attestation e configuração verifyAttestation.
- Desinstalação com plannotator uninstall, --purge, --dry-run e --yes.
- Variáveis de ambiente: PLANNOTATOR_BROWSER, PLANNOTATOR_AI, PLANNOTATOR_ORIGIN, PLANNOTATOR_JINA, PLANNOTATOR_DATA_DIR e outras.
- Pin de versão e instalação mínima com --minimal.
