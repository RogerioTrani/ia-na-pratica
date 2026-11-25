# Knowledge factory fecha loop entre agentes e curador

_2026-11-22 · reportagem_

O gargalo de IA nas empresas é o conhecimento tácito de como a empresa opera, espalhado e implícito. A knowledge factory coleta, cura e mantém esse conhecimento para os agentes, em um loop onde o trabalho revela o que falta. A orientação é começar por um fluxo recorrente.

## O contexto

O que torna seus melhores funcionários eficientes está na cabeça deles: quem procurar, onde responder, por que fazer de um jeito. Esse conhecimento é tácito e espalhado.

Para a IA funcionar na empresa, é preciso coletar, curar e manter uma representação desse conhecimento para passar aos agentes.

Fonte: <https://www.langchain.com/blog/knowledge-factory>

## Linha do tempo

- Passo 1: comece por um fluxo recorrente.
- Passo 2: veja onde o agente trava.
- Passo 3: feche a lacuna e melhore o próximo trabalho.

## Quem ganha e quem perde

A factory mantém três tipos de conhecimento: skills, domain knowledge e data access guidance.

Um dos melhores jeitos de descobrir conhecimento faltante é ter o agente sinalizar enquanto trabalha. Quando não acha ou acha errado, marca a falha e sugere a correção.

Um curator agent roda em background, acessa as fontes brutas e as traces, e cura tudo. Os agentes que usam o conhecimento não devem mantê-lo.

## O que ainda não se sabe

Contexto é o que o agente tem disponível durante a tarefa. Conhecimento é o entendimento reutilizável que mantemos para que ele acerte. Conhecimento é uma forma de contexto, mas geralmente não a única.

O armazenamento é o menos importante. O que importa é o loop entre agentes e curador.
