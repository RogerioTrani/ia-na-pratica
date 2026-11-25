# Anthropic lança /ship no Claude Code para levar PRs ao merge

_2026-11-24 · noticia_

A Anthropic lançou o /ship no Claude Code para levar pull requests até o merge. O comando revisa o código, corrige as falhas que considera reais e acompanha o PR por até 7 dias. Quem aperta o botão de merge ainda é você.

## O fato

A Anthropic lançou o /ship no Claude Code para levar pull requests até o merge.

Ele roda a revisão do código e corrige os bugs que considera reais. No plano Team, a revisão também vale para o repositório inteiro, com o Claude Ship em beta.

Fonte: <https://code.claude.com/docs/en/ship-command.md>

## Os números

- Até 7 dias de acompanhamento do PR.
- Claude Code v2.1.330 ou mais, CLI do GitHub 2.63 ou mais e git 2.38 ou mais.

## O que muda para você

O comando atua em checks que falham, comentários de revisão e conflitos na junção do código. Ele responde ao revisor como autor e pede outra revisão.

O acompanhamento só continua enquanto a sessão local fica aberta e o computador ligado.

No Windows nativo, o acompanhamento não roda.

## O que fazer hoje

Antes de rodar, veja o git status, porque o comando pode enviar mudanças pendentes por conta própria, menos em repositório público.

1. Atualize o Claude Code para a versão mínima e entre no GitHub com gh auth login. Resultado: o ambiente fica pronto para o comando.
2. Rode /ship no terminal. Resultado: o PR é revisado e acompanhado até a aprovação.

Fonte: <https://code.claude.com/docs/en/ship-command.md>

## O que conferir

As regras do repositório continuam valendo: revisão e check exigidos ainda precisam passar.

Mantenha a sessão em primeiro plano, com a branch aberta e o computador ligado. Use o modo auto para o comando agir sem perguntar.
