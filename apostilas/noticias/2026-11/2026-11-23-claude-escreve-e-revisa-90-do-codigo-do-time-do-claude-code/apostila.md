# Claude escreve e revisa 90% do código do time do Claude Code

_2026-11-23 · noticia_

A Anthropic diz que o Claude escreve e revisa cerca de 90% do código da equipe do Claude Code. A conferência fica por conta de checagens automáticas: o Claude roda o app com a skill verify e passa por uma lista de 39 itens de confiabilidade. Se uma checagem falha por três rodadas, ele chama uma pessoa. O trabalho do engenheiro passa a ser definir o que é "pronto" e revisar as evidências.

## O número: cerca de 90%

A própria equipe do Claude Code descreve o número como "~90%". Ele vale para as duas pontas do fluxo: o Claude propõe a alteração e também a revisa.

A pergunta que importa é como esse trabalho é conferido.

Fonte: <https://claude.dev/blog/how-the-claude-code-team-thinks-about-verification/>

## Como o Claude confere o próprio trabalho

Antes de gravar a mudança, o Claude roda o aplicativo de verdade. Ele usa a skill verify, que fica dentro do repositório.

Fonte: <https://claude.dev/blog/how-the-claude-code-team-thinks-about-verification/>

## A lista de 39 itens e a regra das três rodadas

Depois de rodar o app, o Claude confere uma lista de 39 itens de confiabilidade. Ele aplica só os que combinam com a mudança, normalmente de 3 a 10.

- Lista: 39 itens de confiabilidade.
- Aplicados por mudança: normalmente de 3 a 10.
- Se uma checagem continua falhando depois de três rodadas, o Claude para e chama uma pessoa.

Fonte: <https://claude.dev/blog/how-the-claude-code-team-thinks-about-verification/>

## O que muda para o engenheiro

O trabalho deixa de ser ler cada alteração. Passa a ser definir o que é "pronto" e revisar as evidências que o Claude apresenta.

Fonte: <https://code.claude.com/docs/en/code-review-customize>

## Quem julga a mudança não é a mudança

A alteração não muda a regra que a julga: o REVIEW.md vem da branch base. Uma mudança não consegue reescrever os critérios pelos quais será avaliada.

A documentação do Claude Code explica como personalizar o Code Review com o REVIEW.md.

Fonte: <https://code.claude.com/docs/en/code-review-customize>

## Perguntas para levar à sua equipe

Se o Claude escreve e revisa, a qualidade depende de como o resultado é checado.

- Quem define as checagens na sua equipe?
- Elas pegariam um erro do Claude?

## Links oficiais

- Post da equipe do Claude Code sobre como ela pensa a verificação: https://claude.dev/blog/how-the-claude-code-team-thinks-about-verification/
- Documentação do Claude Code, personalizar o Code Review (REVIEW.md): https://code.claude.com/docs/en/code-review-customize
