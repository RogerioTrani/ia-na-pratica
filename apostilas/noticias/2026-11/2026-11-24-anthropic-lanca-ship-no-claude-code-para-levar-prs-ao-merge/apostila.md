# Anthropic lança /ship no Claude Code para levar PRs ao merge

_2026-11-24 · noticia_

A Anthropic lançou o /ship no Claude Code para levar pull requests até o merge. O comando revisa o código, corrige as falhas que considera reais e acompanha o PR por até 7 dias, tratando checks que falham e comentários de revisão. Ele prepara o caminho até a aprovação; quem aperta o botão de merge ainda é você.

## O que o /ship faz

A Anthropic lançou o /ship no Claude Code para levar PRs até o merge. Ele roda a revisão do código e corrige os bugs que considera reais. No plano Team, a revisão também vale para o repositório inteiro: o Claude Ship, em beta, revisa e corrige PRs no GitHub e aprova os que a regra do time permite.

- Roda /code-review e conserta o que parece falha de verdade.
- Acompanha o PR e atua em checks que falham, comentários de revisão e conflitos na junção do código.
- Responde ao revisor como autor e pede outra revisão.
- Deixa o merge para você.

Fonte: <https://code.claude.com/docs/en/ship-command.md>

## O problema que ele ataca

Escrever código virou a parte rápida. A revisão e o merge ainda prendem o resultado: um check falha, um colega pede mudança, e você volta a um PR que já tinha terminado.

## Acompanhamento por até 7 dias

O comando acompanha o PR por até 7 dias, desde que a sessão local fique aberta e o computador ligado. Nesse tempo, ele lida com testes que falham, comentários e conflitos na junção do código.

Fonte: <https://code.claude.com/docs/en/ship-command.md>

## Como usar

Atualize o Claude Code para a versão mínima e entre no GitHub com o comando de login. Antes de rodar, veja o git status: o comando pode enviar mudanças pendentes por conta própria, menos em repositório público. Guia: code.claude.com/docs/en/ship-command. Código: github.com/anthropics/claude-code.

- Claude Code v2.1.330+
- CLI do GitHub 2.63+ com gh auth login
- git 2.38+
- Rode /ship no terminal

Fonte: <https://code.claude.com/docs/en/ship-command.md>

## Limites na prática

No Windows nativo, o acompanhamento não roda. Use o modo auto para o comando agir sem perguntar; nos outros modos, ele espera você. Mantenha a sessão em primeiro plano, com a branch aberta e o computador ligado. As regras do repositório continuam valendo: revisão e check exigidos ainda precisam passar.

Fonte: <https://code.claude.com/docs/en/ship-command.md>

## Além do vídeo

- Em repositório público, faça commit em uma branch antes de rodar /ship.
- Mods no desktop podem mudar o tema de fundo com $.theme.set e um hook Backdrop; exemplos no plugin theme-examples (Customize > Plugins, /custom-theme).
- O painel lateral do desktop abre arquivos, mudanças e terminal como abas em um painel só; dá para mover uma aba ou destacá-la em outra janela.
- Code Mode, experimental, deixa o Claude escrever um script que faz várias chamadas de ferramenta de uma vez: CLAUDE_CODE_EXPERIMENTAL_CODE_MODE=1 claude, só no terminal (v2.1.323 ou posterior).
- Projects foi redesenhado: você fala com um coordenador que roda as outras sessões, com /btw e /fork funcionando; está em beta pública.
