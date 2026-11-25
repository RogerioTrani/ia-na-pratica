# Plannotator Inbox reúne mensagens de agentes numa janela

_2026-11-17 · noticia_

O Plannotator Inbox é uma janela local, aberta no navegador, onde agentes de programação deixam mensagens, perguntas e arquivos enquanto continuam trabalhando. Você responde quando puder, e a resposta volta à sessão que perguntou como o próximo turno. O projeto tem código aberto e funciona com dez agentes de programação, além de assistentes pessoais.

## O fato

O Plannotator Inbox é uma janela local, aberta no navegador, onde agentes de programação deixam mensagens, perguntas e arquivos enquanto continuam trabalhando. Você responde quando puder, e a resposta volta à sessão que perguntou como o próximo turno.

O Plannotator é um espaço local, no navegador, para revisar o que agentes de IA de programação produzem. O código é aberto e está no GitHub: https://github.com/backnotprop/plannotator

Fonte: <https://github.com/backnotprop/plannotator>

## Plannotator Inbox

O Inbox é uma janela local onde seus agentes deixam mensagens, perguntas, arquivos e revisões guiadas enquanto continuam trabalhando. Nenhuma sessão fica aberta esperando por você. Documentação: https://plannotator.ai/docs/reference/inbox/

```
plannotator inbox
```

Fonte: <https://plannotator.ai/inbox/>

## Como responder

A resposta que você envia chega à mesma sessão que fez a pergunta, como o próximo turno da conversa.

- Responda uma pergunta com um clique.
- Anote um arquivo, se for o caso.
- Aperte Send quando tiver um momento.

Fonte: <https://github.com/backnotprop/plannotator>

## Agentes compatíveis

Claude Code, Pi e OpenCode se conectam pelos plugins do Plannotator, e as respostas chegam como o próximo turno de cada um. Qualquer outro agente se conecta por MCP. O comando de ajuda é o guia que o agente lê. Fonte: https://plannotator.ai/docs/reference/inbox/

O Inbox também atende assistentes pessoais: Grok Bot, Muse, Hermes e OpenClaw. Os recados de todos podem cair na mesma janela.

- Agentes de programação: Claude Code, Codex, Copilot CLI, Gemini CLI, OpenCode, Kiro, Droid, Amp, DeepSeek Harness e Pi.

Fonte: <https://github.com/backnotprop/plannotator>

## Instalação

Um instalador cobre quase todos os agentes. Ele instala o binário plannotator, detecta os agentes que você já tem e configura hooks, skills e comandos de cada um. Site oficial: https://plannotator.ai/

No macOS, Linux ou WSL, rode o instalador. Para Windows, use o comando PowerShell abaixo. Script do Windows: https://plannotator.ai/install.ps1

1. rode o instalador do seu sistema. Resultado: o binário plannotator é instalado e os agentes encontrados são configurados.

```
curl -fsSL https://plannotator.ai/install.sh | bash

# Windows PowerShell
irm https://plannotator.ai/install.ps1 | iex
```

Fonte: <https://plannotator.ai/>

## Passo final no Claude Code

Depois do instalador, rode os dois comandos de plugin e reinicie o Claude Code. Fonte: https://github.com/backnotprop/plannotator

1. adicione o marketplace. Resultado: o catálogo do plugin fica disponível.
2. instale o plugin. Resultado: o plugin do Plannotator fica ativo no Claude Code.
3. reinicie o Claude Code. Resultado: a conexão passa a valer nas próximas sessões.

Fonte: <https://github.com/backnotprop/plannotator>

## O que conferir

Privacidade: o Plannotator não coleta telemetria; planos, diffs e anotações ficam locais por padrão.

Instalação só do binário, sem skills, hooks nem configuração por agente: acrescente --minimal ao instalador (curl -fsSL https://plannotator.ai/install.sh | bash -s -- --minimal).

Revisão de código: /plannotator-review revisa mudanças locais, um PR do GitHub ou um MR do GitLab. Anotação de arquivos, pastas e URLs com /plannotator-annotate, e da última mensagem do agente com /plannotator-last. Herdr Annotate leva a revisão ao terminal (herdr plugin install plannotator/herdr-annotate).

Fonte: <https://plannotator.ai/>
