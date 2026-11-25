# Claude escreve e revisa 90% do código do time do Claude Code

_2026-11-23 · noticia_

A Anthropic diz que o Claude escreve e revisa cerca de 90% do código da equipe do Claude Code. A conferência fica por conta de checagens automáticas, com uma lista de 39 itens de confiabilidade. Se uma checagem falha por três rodadas, o Claude chama uma pessoa.

## O fato

A própria equipe do Claude Code descreve o número como cerca de 90%. Ele vale para as duas pontas do fluxo: o Claude propõe a alteração e também a revisa.

A pergunta que importa é como esse trabalho é conferido.

Fonte: <https://claude.dev/blog/how-the-claude-code-team-thinks-about-verification/>

## Os números

- Cerca de 90% do código escrito e revisado pelo Claude.
- 39 itens de confiabilidade na lista de checagem.
- Entre 3 e 10 itens aplicados por mudança, normalmente.
- Três rodadas de falha antes de chamar uma pessoa.

## O que muda para você

Antes de gravar a mudança, o Claude roda o aplicativo de verdade com a skill verify, que fica dentro do repositório.

O trabalho do engenheiro deixa de ser ler cada alteração. Passa a ser definir o que é 'pronto' e revisar as evidências que o Claude apresenta.

A alteração não muda a regra que a julga: o REVIEW.md vem da branch base.

Fonte: <https://code.claude.com/docs/en/code-review-customize>

## O que fazer hoje

1. Pergunte quem define as checagens na sua equipe. Resultado: fica claro quem responde pela definição de pronto.
2. Veja se as checagens pegariam um erro do Claude. Resultado: você sabe se a checagem vale a pena.

Fonte: <https://claude.dev/blog/how-the-claude-code-team-thinks-about-verification/>

## O que conferir

O número de 90% é uma descrição da própria equipe, sem medição independente no texto.

A documentação do Claude Code explica como personalizar o Code Review com o REVIEW.md.

Fonte: <https://code.claude.com/docs/en/code-review-customize>
