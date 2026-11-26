# Git Guardrails já tem mais de 560 mil instalações

_2026-11-23 · noticia_

A Git Guardrails é uma skill que instala um gancho no Claude Code e bloqueia comandos perigosos de Git antes da execução. Ela cobre `git push`, `git reset --hard`, `git clean -f`, `git branch -D`, `git checkout .` e `git restore .`. Depois de ler esta apostila, você vai entender por que o bloqueio prévio importa, como a skill atua e como definir seu alcance. Também vai saber instalar a ferramenta com o comando oficial e reconhecer quais projetos estão protegidos pela configuração escolhida.

## O fato

A Git Guardrails, identificada no repositório como `git-guardrails-claude-code`, passa de 560 mil instalações. O pacote fica no repositório oficial `mattpocock/skills` e tem uma função específica: impedir que a IA execute comandos perigosos de Git sem aviso.

Quando instalada, a skill coloca um gancho no Claude Code. Se a IA tenta rodar um comando da lista bloqueada, o gancho impede a execução. A IA recebe a resposta de que não tem autorização para aquele comando.

Fonte: <https://skills.sh/mattpocock/skills/git-guardrails-claude-code>

## Por que isso importa

Trabalhar com IA de programação permite delegar tarefas que envolvem vários comandos. Uma instrução ampla, como organizar o projeto, dá espaço para a ferramenta escolher os passos. Entre esses passos podem aparecer ações que mudam ou removem partes do trabalho.

Git tem comandos capazes de descartar alterações, apagar branches e enviar mudanças para o repositório remoto. O problema aparece quando um desses comandos é executado sem uma intervenção anterior. A Git Guardrails atua nesse intervalo: ela verifica a tentativa e barra o comando perigoso antes que ele rode.

Fonte: <https://github.com/mattpocock/skills/blob/main/skills/misc/git-guardrails-claude-code/SKILL.md>

## O risco de uma decisão automática

O perigo começa quando a IA transforma um objetivo geral em uma ação concreta sem perguntar. Quando o pedido é organizar o projeto, ela pode decidir excluir um branch antigo por conta própria. A intenção pode parecer adequada, mas o comando escolhido tem poder de destruição.

Um branch antigo ainda pode conter trabalho importante para o projeto. Por isso, uma decisão de limpeza merece proteção no ponto de execução. A skill muda esse ponto: a tentativa de exclusão passa pelo gancho, e o comando bloqueado não chega a ser executado.

Fonte: <https://github.com/mattpocock/skills/blob/main/skills/misc/git-guardrails-claude-code/SKILL.md>

## O que é a Git Guardrails

Uma skill é um pacote de instruções que orienta uma ferramenta de IA. No caso da Git Guardrails, o pacote realiza uma tarefa concreta: instala um gancho no Claude Code para vigiar comandos de Git.

A proteção tem escopo definido. Ela cobre os comandos de Git que a skill reconhece como perigosos e atua no Claude Code. A função da ferramenta é barrar tentativas de execução dentro da lista definida.

Fonte: <https://github.com/mattpocock/skills/blob/main/skills/misc/git-guardrails-claude-code/SKILL.md>

## Como o gancho bloqueia o comando

O fluxo tem três momentos. Primeiro, a IA decide tentar um comando de Git. Depois, o gancho verifica essa tentativa. Se o comando estiver na lista de bloqueio, a execução não acontece.

Nesse caso, a IA recebe uma resposta de falta de autorização. A tentativa termina antes de o comando rodar, que é o ponto central da proteção. A skill separa a decisão da IA da permissão para executar a ação.

Fonte: <https://github.com/mattpocock/skills/blob/main/skills/misc/git-guardrails-claude-code/SKILL.md>

## Os comandos travados

A lista inclui `git push` em todas as variantes, inclusive com força. Também bloqueia `git reset --hard`, `git clean -f`, `git branch -D`, `git checkout .` e `git restore .`.

Os nomes precisam ser lidos literalmente. O ponto final em `git checkout .` e `git restore .` faz parte do comando e indica o diretório atual. Argumentos como `--hard`, `-f` e `-D` também identificam os comandos bloqueados. Já `git push` aparece sem sufixo porque o bloqueio vale para todas as suas variantes.

- `git push`: envia alterações para o repositório remoto; o bloqueio vale para todas as variantes, inclusive com força.
- `git reset --hard`: faz um reset forçado que reposiciona o branch e descarta alterações locais.
- `git clean -f`: remove arquivos não rastreados do diretório de trabalho.
- `git branch -D`: força a exclusão de um branch.
- `git checkout .`: descarta alterações de arquivos no diretório atual.
- `git restore .`: restaura arquivos no diretório atual, descartando alterações.

Fonte: <https://github.com/mattpocock/skills/blob/main/skills/misc/git-guardrails-claude-code/SKILL.md>

## Onde a proteção vale

Na configuração, você escolhe entre proteger só este projeto ou todos. Essa decisão determina onde a trava existe. Se você escolher um único projeto, os outros ficam sem essa proteção.

O alcance precisa ficar explícito antes de você contar com o bloqueio. Um projeto sem a skill ou fora do escopo escolhido fica sem a proteção descrita para a Git Guardrails.

Fonte: <https://skills.sh/mattpocock/skills/git-guardrails-claude-code>

## Os números

A marca de 560 mil instalações mostra a adoção da skill entre quem programa com IA. Ela indica volume de instalações, não uma taxa de sucesso nem uma garantia de proteção em qualquer situação.

O repositório `mattpocock/skills` passa de 300 mil estrelas no GitHub. Esse número pertence ao repositório inteiro e supera o da maioria dos frameworks mais usados. Estrelas e instalações medem coisas diferentes: uma indica atenção ao repositório, e a outra, uso da skill.

- 560 mil+: instalações da Git Guardrails.
- 300 mil+: estrelas do repositório `mattpocock/skills` no GitHub.

Fonte: <https://github.com/mattpocock/skills>

## O que muda para você

Com a skill instalada no escopo correto, a IA não consegue executar os comandos bloqueados. A barreira é automática e aparece no momento em que a ferramenta tenta rodar a ação. Isso protege o projeto de uma decisão destrutiva tomada a partir de uma instrução ampla.

Imagine que você pede à IA para organizar um projeto e ela decide excluir um branch antigo. Se a tentativa for `git branch -D`, o gancho verifica o comando. Como ele está na lista, a execução é bloqueada antes da exclusão, e a IA recebe a resposta de que não tem autorização.

Para você, a diferença aparece no fluxo de trabalho: a proteção acontece na tentativa de execução. O projeto protegido ganha uma trava para os comandos listados, e o alcance escolhido na configuração define onde ela vale.

Fonte: <https://github.com/mattpocock/skills/blob/main/skills/misc/git-guardrails-claude-code/SKILL.md>

## O que fazer hoje

A instalação usa um comando que aponta para o repositório oficial e seleciona a skill pelo nome `git-guardrails-claude-code`. Execute o comando completo no terminal do seu ambiente de desenvolvimento, preservando o endereço e os argumentos.

O comando adiciona a skill; é ela que instala o gancho no Claude Code. Use a configuração para escolher o alcance da proteção e saber onde ela vale.

1. Execute o comando de instalação no terminal do seu ambiente de desenvolvimento. O resultado esperado é adicionar a skill `git-guardrails-claude-code` ao Claude Code.
2. Abra a configuração da skill. O resultado esperado é encontrar a escolha entre só este projeto e todos.
3. Selecione o alcance desejado. O resultado esperado é definir onde a proteção da Git Guardrails vai atuar.
4. Confira o ambiente e o escopo escolhido. O resultado esperado é identificar se o projeto em que você está está coberto pela trava.

```
npx skills add https://github.com/mattpocock/skills --skill git-guardrails-claude-code
```

Fonte: <https://skills.sh/mattpocock/skills/git-guardrails-claude-code>

## O que conferir

A proteção depende do ambiente e do escopo. A skill instala o gancho no Claude Code, e a configuração decide se ele vale para um projeto ou para todos. Fora do escopo escolhido, a trava não existe.

Confira também os comandos literalmente. O bloqueio de `git push` inclui todas as variantes. Nos outros itens, argumentos como `--hard`, `-f`, `-D` e o ponto final fazem parte do comando identificado. A função descrita é barrar essa lista de comandos de Git.

- Ambiente: confirme que você está usando o Claude Code, que é onde a skill instala o gancho.
- Escopo: confira se a opção escolhida cobre só este projeto ou todos.
- Projeto sem proteção: se ele não estiver no escopo, a trava não existe ali.
- Comandos: reconheça `git push`, `git reset --hard`, `git clean -f`, `git branch -D`, `git checkout .` e `git restore .` como os bloqueados.
- Resposta à IA: quando um comando perigoso é barrado, ela recebe a informação de que não tem autorização para executar.

Fonte: <https://github.com/mattpocock/skills/blob/main/skills/misc/git-guardrails-claude-code/SKILL.md>

## Glossário

- Git: sistema de controle de versão usado para acompanhar alterações no projeto.
- Branch: linha separada de desenvolvimento no Git.
- Skill: pacote de instruções que orienta uma ferramenta de IA; nesta apostila, é o pacote que instala o gancho de proteção.
- Gancho (hook): mecanismo acionado durante um evento do Claude Code; aqui, verifica a tentativa de executar comandos de Git.
- Claude Code: ambiente de programação com IA onde a skill instala o gancho.
- Comando destrutivo: comando que pode apagar ou descartar trabalho; neste caso, é a categoria usada para os comandos de Git bloqueados pela skill.
- `git push`: comando que envia alterações para o repositório remoto; todas as variantes ficam bloqueadas.
- `git reset --hard`: comando de reset forçado que reposiciona o branch e descarta alterações locais.
- `git clean -f`: comando que remove arquivos não rastreados do diretório de trabalho.
- `git branch -D`: comando que força a exclusão de um branch.
- `git checkout .`: comando que descarta alterações de arquivos no diretório atual.
- `git restore .`: comando que restaura arquivos no diretório atual, descartando alterações.

Fonte: <https://github.com/mattpocock/skills/blob/main/skills/misc/git-guardrails-claude-code/SKILL.md>

## Para onde ir depois

O próximo passo é instalar a skill e definir o alcance que você quer usar. Depois, pratique reconhecer os comandos bloqueados e observe o retorno quando a IA tentar executar um deles.

Consulte o repositório oficial e a página da skill para acompanhar as instruções. Ao delegar uma tarefa à IA, use a lista como referência para identificar ações que merecem proteção antes da execução.

- Instale a Git Guardrails pelo comando oficial.
- Escolha entre proteger só este projeto ou todos.
- Pratique identificar `git push`, `git reset --hard`, `git clean -f`, `git branch -D`, `git checkout .` e `git restore .`.
- Quando ocorrer um bloqueio, use a resposta da IA para reconhecer qual comando foi barrado.

Fonte: <https://skills.sh/mattpocock/skills/git-guardrails-claude-code>

## Links citados

- https://raw.githubusercontent.com/mattpocock/skills/main/skills/misc/git-guardrails-claude-code/SKILL.md

## Além do vídeo

- Em seis meses, o repositório ultrapassou o React em estrelas no GitHub, segundo comparação do star-history.com consultada em 14/11/2026.
