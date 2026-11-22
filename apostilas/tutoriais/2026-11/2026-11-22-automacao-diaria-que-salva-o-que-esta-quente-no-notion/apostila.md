# Automação diária que salva o que está quente no Notion

_2026-11-22 · tutorial_

Segundo cérebro é uma pasta de arquivos de texto, em geral markdown, e só ajuda a IA se estiver atualizada. Este guia monta uma rotina em que o Claude Code coleta um log bruto todo dia e uma skill com modelo mais barato digere esse log e atualiza a pasta. Você sai com o prompt de coleta e o texto da skill prontos para copiar.

## A ideia

O segundo cérebro é uma pasta de arquivos de texto, em geral markdown. Quanto mais contexto atualizado ela guarda, mais a IA consegue te ajudar.

Parada, a pasta não serve para nada. A automação deste guia faz ela se atualizar sozinha, sem você digitar.

## Passo 1: crie a pasta e o mapa.md

Crie uma pasta no computador e sincronize com o GitHub. Divida em áreas, como empresa e pessoal.

Dentro dela, crie o mapa.md: o índice que o Claude Code lê primeiro para saber o que existe em cada pasta.

- Pasta no computador, sincronizada com o GitHub
- Subpastas por área, como empresa e pessoal
- mapa.md na raiz, descrevendo o conteúdo de cada pasta

Fonte: <https://github.com>

## Passo 2: conecte suas fontes

E-mail, calendário, CRM, Notion e WhatsApp entram no agente por servidores MCP (Model Context Protocol) e por integrações via n8n. A IA lê o que chegou de novo sem você copiar e colar nada.

Fonte: <https://n8n.io>

## Passo 3: peça a automação diária

Peça ao agente uma automação de coleta com o prompt abaixo. Fontes como o Notion entram só para leitura.

```
Acesse minhas tarefas do Notion, eventos de hoje no calendário e mensagens importantes. Crie um log bruto em Markdown na pasta /logs/hoje.md.
```

Fonte: <https://www.notion.com>

## Passo 4: gere um log bruto todo dia

O Claude Code roda essa rotina todo dia e puxa WhatsApp, e-mail e calendário para um log bruto em Markdown. Nesta etapa ninguém interpreta nada, só se coleta.

Fonte: <https://claude.com>

## Passo 5: defina quem pode entrar no cérebro

Crie uma lista de pessoas aprovadas. Só quem está nela cai em people, pendências e hot.

O agente pode te mandar essa lista todo dia para você autorizar quem entra.

## Passo 6: digira o log com uma skill e um modelo mais barato

A digestão lê o log bruto e atualiza os arquivos permanentes. Use um modelo leve: Claude Haiku (Anthropic) ou GPT-4o mini (OpenAI). O texto da skill de digestão:

```
Leia o arquivo /logs/hoje.md, extraia decisões tomadas, tarefas pendentes e insights principais. Atualize os arquivos permanentes do meu segundo cérebro e faça o commit no GitHub.
```

## Checklist final

- Pasta com mapa.md na raiz, sincronizada no GitHub (github.com)
- Fontes conectadas por MCP e n8n (n8n.io)
- Log bruto gerado todo dia pelo Claude Code (claude.com)
- Lista de pessoas aprovadas
- Skill com Claude Haiku ou GPT-4o mini atualizando hot, people, pendências e decisões

## Além do vídeo

- O hot.md guarda o que está vivo no dia a dia: reuniões, mensagens lidas e to-do lists vindas de várias fontes.
- O people funciona como um pequeno CRM das pessoas com quem você interagiu, e só quem você autoriza entra nele.
- A skill de digestão também atualiza o diário, além de hot, people, pendências e decisões.
- No Hermes, a sessão é compactada automaticamente quando chega a 75%. No Claude, dá para criar uma skill chamada salve que guarda a sessão e propaga o que ficou no cérebro.
- Dá para conectar uma leitura de extrato bancário na pasta pessoal e automatizar as finanças.
