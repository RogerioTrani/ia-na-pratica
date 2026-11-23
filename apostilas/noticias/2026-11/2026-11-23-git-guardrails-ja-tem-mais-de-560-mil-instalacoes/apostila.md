# Git Guardrails já tem mais de 560 mil instalações

_2026-11-23 · noticia_

Git Guardrails é uma skill com mais de 560 mil instalações que instala um gancho no Claude Code e bloqueia comandos perigosos de Git antes de rodarem. Ela vive no repositório mattpocock/skills, que passa de 300 mil estrelas no GitHub. Esta apostila mostra o que ela barra, o comando de instalação e a escolha que decide se a trava vale em um projeto ou em todos.

## O risco

Você pede para a IA organizar o projeto e ela decide sozinha apagar um branch antigo. Sem pergunta e sem aviso. Um comando destrutivo de Git assim pode fazer o seu código sumir.

## O que a Git Guardrails faz

A skill instala um gancho no Claude Code que vigia cada comando de Git que a IA tenta rodar. Se o comando for perigoso, ele é bloqueado antes de executar e a IA recebe a resposta de que não tem autorização.

Mais de 560 mil pessoas já instalaram a skill. Ela faz parte do repositório de skills de Matt Pocock, que passa de 300 mil estrelas no GitHub.

Fonte: <https://github.com/mattpocock/skills>

## Comandos que ficam bloqueados

São os comandos que mais machucam. Todos param antes de executar.

- git push (todas as variantes)
- git reset --hard
- git clean -f
- git branch -D
- git checkout .
- git restore .

Fonte: <https://raw.githubusercontent.com/mattpocock/skills/main/skills/misc/git-guardrails-claude-code/SKILL.md>

## Como instalar

Rode o comando abaixo no terminal. Ele instala a skill git-guardrails-claude-code a partir do repositório oficial.

```
npx skills add https://github.com/mattpocock/skills --skill git-guardrails-claude-code
```

Fonte: <https://skills.sh/mattpocock/skills/git-guardrails-claude-code>

## Escolha onde a trava vale

Na configuração, você escolhe se a trava vale só para este projeto ou para todos. Se escolher um só, os outros ficam sem proteção e a IA roda qualquer comando de Git sem perguntar.

- Instale em todos os projetos em que a IA mexe no seu código.
- Em cada projeto sem a instalação, a trava não existe.

Fonte: <https://skills.sh/mattpocock/skills/git-guardrails-claude-code>

## Links oficiais

- Repositório oficial (mattpocock/skills): https://github.com/mattpocock/skills
- Skill no skills.sh: https://skills.sh/mattpocock/skills/git-guardrails-claude-code
- Instruções da skill (SKILL.md): https://github.com/mattpocock/skills/blob/main/skills/misc/git-guardrails-claude-code/SKILL.md

## Além do vídeo

- Matt Pocock já apareceu no canal com outras duas skills; este é o terceiro pacote dele da série.
