# Plannotator Inbox reúne mensagens de agentes numa janela

_2026-11-17 · noticia_

O Plannotator Inbox é uma janela local, aberta no navegador, onde agentes de programação deixam mensagens, perguntas e arquivos enquanto continuam trabalhando. Você responde quando puder, e a resposta volta à sessão que perguntou como o próximo turno. O projeto tem código aberto e funciona com dez agentes de programação, além de assistentes pessoais. Esta apostila traz os comandos de instalação e de conexão, prontos para copiar.

## O que é o Plannotator

O Plannotator é um espaço local, no navegador, para revisar o que agentes de IA de programação produzem. O código é aberto e está no GitHub.

Fonte: <https://github.com/backnotprop/plannotator>

## Plannotator Inbox

O Inbox é uma janela local onde seus agentes deixam mensagens, perguntas, arquivos e revisões guiadas enquanto continuam trabalhando. Nenhuma sessão fica aberta esperando por você.

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

## Como conectar os agentes

Claude Code, Pi e OpenCode se conectam pelos plugins do Plannotator, e as respostas chegam como o próximo turno de cada um. Qualquer outro agente se conecta por MCP. O comando de ajuda é o guia que o agente lê.

Fonte: <https://plannotator.ai/docs/reference/inbox/>

## Agentes compatíveis

Agentes de programação: Claude Code, Codex, Copilot CLI, Gemini CLI, OpenCode, Kiro, Droid, Amp, DeepSeek Harness e Pi.

O Inbox também atende assistentes pessoais: Grok Bot, Muse, Hermes e OpenClaw. Os recados de todos podem cair na mesma janela.

Fonte: <https://github.com/backnotprop/plannotator>

## Instalação

Um instalador cobre quase todos os agentes. Ele instala o binário plannotator, detecta os agentes que você já tem e configura hooks, skills e comandos de cada um.

No macOS, Linux ou WSL:

```
curl -fsSL https://plannotator.ai/install.sh | bash

# Windows PowerShell
irm https://plannotator.ai/install.ps1 | iex
```

Fonte: <https://plannotator.ai/>

## Passo final no Claude Code

Depois do instalador, rode os dois comandos de plugin e reinicie o Claude Code.

- Adicione o marketplace.
- Instale o plugin.
- Reinicie o Claude Code.

Fonte: <https://github.com/backnotprop/plannotator>

## Além do vídeo

- Instalação só do binário, sem skills, hooks nem configuração por agente: acrescente --minimal ao instalador (curl -fsSL https://plannotator.ai/install.sh | bash -s -- --minimal).
- Revisão de código: /plannotator-review revisa mudanças locais, um PR do GitHub ou um MR do GitLab.
- Anotação de arquivos, pastas e URLs com /plannotator-annotate, e da última mensagem do agente com /plannotator-last.
- Herdr Annotate leva a revisão ao terminal (herdr plugin install plannotator/herdr-annotate).
- Privacidade: o Plannotator não coleta telemetria; planos, diffs e anotações ficam locais por padrão.
