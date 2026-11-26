---
name: eng-git-workflow
description: "Define uso de branches, mensagens de commit, revisão, releases e reversão no Git. Use quando o time tiver histórico confuso, conflitos frequentes ou publicações sem rastreio."
---

# Fluxo de versionamento e revisão

Define uso de branches, mensagens de commit, revisão, releases e reversão no Git. Use quando o time tiver histórico confuso, conflitos frequentes ou publicações sem rastreio.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Tamanho do time e ritmo de entrega
- Fluxo atual e problemas percebidos
- Plataforma do repositório e verificações automáticas
- Versões que precisam de suporte simultâneo

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Escolha o modelo de branches mais simples que atenda ao ritmo e às versões mantidas.
2. Estabeleça uma convenção de commits e nomes de branch com exemplos do próprio projeto.
3. Defina o que um pedido de integração precisa descrever, quem revisa e quais checagens bloqueiam a fusão.
4. Descreva como marcar versões, publicar correção urgente e reverter sem reescrever histórico compartilhado.

## O que entregar

Fluxo Git documentado e checklist para pedidos de integração.

## Conferência antes de entregar

- [ ] Há procedimento claro de correção urgente e de reversão.
- [ ] As regras cabem no arquivo de instruções ou no guia do projeto.
- [ ] Comandos que reescrevem ou apagam histórico exigem confirmação.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
