# Automação diária que salva o que está quente no Notion

_2026-11-22 · tutorial_

Segundo cérebro é uma pasta de arquivos de texto, em geral markdown, e só ajuda a IA se estiver atualizada. Este guia monta uma rotina em que o Claude Code coleta um log bruto todo dia e uma skill com modelo mais barato digere esse log e atualiza a pasta. Você sai com o prompt de coleta e o texto da skill prontos para copiar.

## O que você terá no fim

Ao final, sua pasta de segundo cérebro se atualiza sozinha todo dia: o Claude Code coleta um log bruto e uma skill com modelo mais barato digere esse log e atualiza os arquivos permanentes. O segundo cérebro é uma pasta de arquivos de texto, em geral markdown. Quanto mais contexto atualizado ela guarda, mais a IA consegue te ajudar. Fonte: https://github.com

Fonte: <https://github.com>

## Antes de começar

Requisitos para seguir o guia.

- Uma pasta no computador, sincronizada com o GitHub: github.com.
- Fontes de dados: e-mail, calendário, CRM, Notion e WhatsApp, conectados por servidores MCP (Model Context Protocol) e por integrações via n8n: n8n.io.
- Claude Code para coletar o log e um modelo leve para a digestão: Claude Haiku (Anthropic) ou GPT-4o mini (OpenAI).

Fonte: <https://n8n.io>

## Passo a passo

Siga os passos na ordem. Os prompts ficam em seções próprias.

1. crie a pasta e o mapa.md. Crie uma pasta no computador e sincronize com o GitHub. Divida em áreas, como empresa e pessoal. Dentro dela, crie o mapa.md, o índice que o Claude Code lê primeiro. Resultado esperado: a pasta tem o mapa.md na raiz.
2. conecte suas fontes. E-mail, calendário, CRM, Notion e WhatsApp entram no agente por servidores MCP e por integrações via n8n. Resultado esperado: a IA lê o que chegou de novo sem você copiar e colar nada.
3. peça a automação diária com o prompt de coleta. Fontes como o Notion entram só para leitura. Resultado esperado: a automação de coleta fica criada no agente.
4. gere um log bruto todo dia. O Claude Code roda essa rotina todo dia e puxa WhatsApp, e-mail e calendário para um log bruto em Markdown. Nesta etapa ninguém interpreta nada, só se coleta. Resultado esperado: o log bruto do dia aparece em Markdown.
5. defina quem pode entrar no cérebro. Crie uma lista de pessoas aprovadas. Só quem está nela cai em people, pendências e hot. Resultado esperado: a lista de aprovados fica pronta.
6. digira o log com uma skill e um modelo mais barato. A digestão lê o log bruto e atualiza os arquivos permanentes, com o texto da skill de digestão. Resultado esperado: os arquivos permanentes são atualizados.

Fonte: <https://claude.com>

## Prompt de coleta

Cole este prompt no agente para criar a automação diária de coleta.

```
Acesse minhas tarefas do Notion, eventos de hoje no calendário e mensagens importantes. Crie um log bruto em Markdown na pasta /logs/hoje.md.
```

Fonte: <https://www.notion.com>

## Prompt da skill de digestão

Use este texto como a skill de digestão, rodada com o modelo mais barato.

```
Leia o arquivo /logs/hoje.md, extraia decisões tomadas, tarefas pendentes e insights principais. Atualize os arquivos permanentes do meu segundo cérebro e faça o commit no GitHub.
```

Fonte: <https://github.com>

## Teste de pronto

Como saber que funcionou. Cada item é verificável.

- [ ] A pasta tem o mapa.md na raiz, sincronizada no GitHub.
- [ ] Fontes conectadas por MCP e n8n.
- [ ] O log bruto do dia aparece em /logs/hoje.md, gerado pelo Claude Code.
- [ ] A lista de pessoas aprovadas existe e só quem está nela entra em people, pendências e hot.
- [ ] Os arquivos permanentes foram atualizados pela skill com Claude Haiku ou GPT-4o mini.

Fonte: <https://claude.com>

## Cuidados

O hot.md guarda o que está vivo no dia a dia: reuniões, mensagens lidas e to-do lists vindas de várias fontes. O people funciona como um pequeno CRM das pessoas com quem você interagiu, e só quem você autoriza entra nele.

No Hermes, a sessão é compactada automaticamente quando chega a 75%. Dá para conectar uma leitura de extrato bancário na pasta pessoal e automatizar as finanças. Fonte: https://claude.com

Fonte: <https://claude.com>
