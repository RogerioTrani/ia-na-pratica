# Modelos de IA já controlam um braço robótico de 6 eixos

_2026-11-24 · filme_

A Artificial Analysis mediu modelos de linguagem controlando um braço robótico de 6 eixos em oito tarefas de mesa. O GPT-6 Astra lidera com 69,4 pontos de 100. Os modelos acertam tarefas simples, mas levam cerca de meia hora por tarefa, contra 20 segundos de uma pessoa.

## O contexto

A Artificial Analysis lançou o AA-Robotics v0.1, uma prévia de pesquisa. Ela mede quão bem modelos de linguagem operam um braço robótico de 6 eixos (5 juntas e uma garra) em oito tarefas de mesa.

Cada modelo roda num contêiner isolado e enxerga a mesa por quatro câmeras, três ao redor da mesa e uma no pulso do braço. Ele escreve e executa código para planejar e enviar os movimentos. Toda tentativa é zero-shot.

Aprovação vale 100 pontos; tarefa incompleta recebe pontos parciais pelo progresso.

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## Quem ganha e quem perde

A nota é a média por tarefa, de 0 a 100. Os modelos GPT rodaram no Codex, os Claude no Claude Code e o Gemini 4 Argon no Antigravity, todos no esforço alto.

Em média, o GPT-6 Astra gastou 30 minutos e US$ 16,36 por tarefa. O GPT-6.1 Sol é o mais barato, com US$ 1,93 por tarefa, e ficou menos de cinco pontos abaixo na nota (69,4 contra 64,6).

Os modelos levam cerca de meia hora por tarefa. Um humano leva em média 20 segundos. O Gemini 4 Argon é o mais lento, com 52 minutos.

- GPT-6 Astra: 69,4
- GPT-6.1 Sol: 64,6
- Gemini 4 Argon: 55,3
- Claude Opus 5.5: 48,8
- Claude Fable 5.1: 46,3

Fonte: <https://artificialanalysis.ai/articles/aa-robotics>

## O que ainda não se sabe

Os modelos continuam refinando a tentativa muito depois de chegar a um estado aprovado. O GPT-6.1 Sol montou uma torre válida em cerca de 17 minutos e, ao seguir mexendo, falhou na tarefa.

Ainda não se sabe como os modelos vão melhorar o julgamento sobre quando uma tarefa física está terminada.

Os tempos de atividade do Gemini 4 Argon são estimativas, porque o Antigravity não registra horário de cada passo.
