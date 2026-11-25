# Git Guardrails já tem mais de 560 mil instalações

_2026-11-23 · noticia_

Git Guardrails é uma skill com mais de 560 mil instalações que instala um gancho no Claude Code e bloqueia comandos perigosos de Git antes de rodarem. Ela vive no repositório mattpocock/skills, que passa de 300 mil estrelas no GitHub.

## O fato

Git Guardrails é uma skill com mais de 560 mil instalações. Ela instala um gancho no Claude Code que vigia cada comando de Git que a IA tenta rodar.

Se o comando for perigoso, ele é bloqueado antes de executar e a IA recebe a resposta de que não tem autorização.

Fonte: <https://github.com/mattpocock/skills>

## Os números

- Mais de 560 mil instalações da skill.
- Mais de 300 mil estrelas no repositório mattpocock/skills, no GitHub.
- Seis comandos de Git bloqueados na lista principal.

## O que muda para você

São bloqueados git push em todas as variantes, git reset --hard, git clean -f, git branch -D, git checkout . e git restore .

Na configuração, você escolhe se a trava vale só para este projeto ou para todos. Se escolher um só, os outros ficam sem proteção.

Fonte: <https://raw.githubusercontent.com/mattpocock/skills/main/skills/misc/git-guardrails-claude-code/SKILL.md>

## O que fazer hoje

1. Rode o comando de instalação no terminal. Resultado: a skill git-guardrails-claude-code é instalada a partir do repositório oficial.
2. Instale em todos os projetos em que a IA mexe no seu código. Resultado: a trava vale em cada um deles.

```
npx skills add https://github.com/mattpocock/skills --skill git-guardrails-claude-code
```

Fonte: <https://skills.sh/mattpocock/skills/git-guardrails-claude-code>

## O que conferir

Em cada projeto sem a instalação, a trava não existe.

Confira as instruções da skill no SKILL.md do repositório oficial antes de instalar.

Fonte: <https://github.com/mattpocock/skills/blob/main/skills/misc/git-guardrails-claude-code/SKILL.md>

## Além do vídeo

- Matt Pocock já apareceu no canal com outras duas skills; este é o terceiro pacote dele da série.
