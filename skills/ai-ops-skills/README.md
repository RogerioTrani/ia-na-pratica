# ai-ops-skills

209 skills de agente de IA, em português, com nomes em inglês no formato `time-função`. Cada uma é um roteiro
de trabalho em texto (`SKILL.md`): o que reunir, os passos, o que entregar e como conferir. Sem código executável.

| Time | Skills | Prefixo |
| --- | --- | --- |
| Conteúdo | 15 | `content-` |
| Copy | 56 | `copy-` |
| Tráfego | 16 | `traffic-` |
| Design | 26 | `design-` |
| Engenharia | 46 | `eng-` |
| Negócio | 50 | `biz-` |

O catálogo completo, com quando usar cada uma, está em [AGENTS.md](AGENTS.md).

## Instalar

O jeito mais fácil é pedir ao seu agente: "instale a skill copy-method-router de RogerioTrani/ia-na-pratica/skills/ai-ops-skills com
npx skills". Ou rode você mesmo (precisa do Node.js; o comando detecta os agentes instalados):

```bash
npx skills add RogerioTrani/ia-na-pratica/skills/ai-ops-skills --list
```

```bash
npx skills add RogerioTrani/ia-na-pratica/skills/ai-ops-skills --skill copy-method-router
```

```bash
npx skills add RogerioTrani/ia-na-pratica/skills/ai-ops-skills --skill '*'
```

`-g` instala para todos os projetos e `-a <agente>` escolhe o agente. Instale só o que for usar: muitas skills de uma
vez ocupam contexto do agente.

## Agentes que usam outro formato

Se o seu agente não lê `SKILL.md`, copie esta pasta para o projeto e acrescente ao arquivo de instruções dele
(`AGENTS.md`, `GEMINI.md`, `CLAUDE.md`, regras do Cursor, `CONVENTIONS.md` ou o equivalente):

```text
Antes de uma tarefa, consulte skills/ai-ops-skills/AGENTS.md. Se houver uma skill para ela, abra o SKILL.md indicado e siga.
```

Em um chat sem acesso a arquivos, cole o conteúdo do `SKILL.md` da tarefa junto com o seu pedido.

## Contexto do projeto

As skills trabalham melhor quando o arquivo de instruções do projeto diz: quem é a marca, o que vende e para quem; o
objetivo atual e como ele é medido; o tom de voz; onde estão preços, provas e políticas; e o que exige aprovação antes
de executar.
