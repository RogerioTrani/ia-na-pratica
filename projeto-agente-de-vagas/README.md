# Projeto: agente de vagas

O projeto final da série [Agente de vagas](../serie-agente-de-vagas/README.md): três agentes de IA que trabalham juntos.

| Agente | O que faz | Arquivos |
| --- | --- | --- |
| **Regente** | Conversa com você, aplica o quiz, guarda o perfil e delega o trabalho | [`personas/regente.md`](personas/regente.md), [`skills/regente-quiz.md`](skills/regente-quiz.md), [`skills/regente-delegar-trabalho.md`](skills/regente-delegar-trabalho.md) |
| **Faro** | Busca vagas reais, com link, nos sites de vagas | [`personas/faro.md`](personas/faro.md), [`skills/faro-buscar-vagas.md`](skills/faro-buscar-vagas.md) |
| **Prumo** | Ranqueia as vagas com nota de 0 a 100, pontos fortes, lacunas e motivo | [`personas/prumo.md`](personas/prumo.md), [`skills/prumo-ranquear-vagas.md`](skills/prumo-ranquear-vagas.md) |

Não há código de programação aqui: o sistema inteiro é Markdown. As **personas** dizem quem cada agente é, as **habilidades** (skills) ensinam o que ele sabe fazer e os **planos** são a fonte de verdade de tudo.

## Como usar

1. Faça o ambiente da [Aula 1, parte 1](../serie-agente-de-vagas/aula-1-parte-1/README.md): Zed, OpenRouter e um modelo gratuito.
2. Copie esta pasta para o seu computador e abra-a no Zed.
3. Para a busca, instale o Node e o Firecrawl como na [Aula 2, parte 2](../serie-agente-de-vagas/aula-2-parte-2/README.md).
4. Abra uma conversa nova no painel do agente e escreva: `Leia e siga o @AGENTS.md`.
5. O Regente se apresenta, faz o quiz e mostra o menu.

## Estrutura

```text
projeto-agente-de-vagas/
├── AGENTS.md                  instrui a IA a adotar a persona do Regente
├── plano.md                   plano do Regente (orquestrador)
├── plano-aula-2.md            plano do Faro
├── plano-aula-3.md            plano do Prumo
├── personas/                  um arquivo por agente
├── skills/                    uma habilidade por arquivo
└── data/                      o que os agentes gravam (perfil, resultados, ranking)
```

## Cuidados

- Os arquivos de `data/` têm informações da sua busca e ficam fora do repositório. Não publique o seu perfil com dados pessoais.
- Use a sua própria chave do OpenRouter e do Firecrawl. Nunca coloque chaves nestes arquivos.
- O modelo pode se comportar de forma um pouco diferente a cada execução. Se algo sair estranho, ajuste o plano ou a habilidade e teste de novo: é o ciclo do projeto.
