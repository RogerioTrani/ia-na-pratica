# Vercel abre o Formidable, fábrica de agentes no GitHub

_2026-11-23 · reportagem_

A Vercel abriu um modelo de fábrica de software em que agentes de IA classificam, planejam, programam e revisam tarefas a partir de uma issue do GitHub. O modelo se chama eve Software Factory, e o agente orquestrador, Foreman. O resultado chega como pull request em rascunho, e a decisão de aprovar e fazer o merge continua com você.

## O contexto

A Vercel abriu um modelo de fábrica de software em que agentes de IA classificam, planejam, programam e revisam tarefas a partir de uma issue do GitHub. O modelo se chama eve Software Factory, e o agente orquestrador, Foreman. O resultado chega como pull request em rascunho, e a decisão de aprovar e fazer o merge continua com você. Fonte: https://vercel.com/kb/guide/eve-software-factory

Fonte: <https://vercel.com/kb/guide/eve-software-factory>

## A ideia: desenvolvimento como linha de produção

Uma fábrica de software tem três partes: entrada, orquestrador e verificação. Quem está na frente trata o desenvolvimento como linha de produção, em que cada pedido passa por etapas definidas e sai com um critério claro de pronto. O assistente de código, que só escreve trechos, fica de fora desse desenho.

- Parte 1: a entrada, onde tudo vira ticket.
- Parte 2: o orquestrador, um agente chefe.
- Parte 3: a verificação, presente desde o começo.

Fonte: <https://vercel.com/kb/guide/eve-software-factory>

## Parte 1: a entrada

A demanda pode vir de qualquer lugar: pedido de cliente, bug reclamado no Discord ou ideia sua. Tudo é padronizado no mesmo formato antes de andar. Cada item vira um ticket, a peça que passa pela fábrica.

Fonte: <https://vercel.com/kb/guide/eve-software-factory>

## Parte 2: o orquestrador

Em vez de você distribuir tarefa por tarefa, um agente chefe cuida da fila. Ele pega cada ticket, decide o que roda junto e o que espera, e entrega o trabalho aos agentes que executam. Como ele enxerga as dependências, libera em paralelo só o que pode andar. No modelo da Vercel, esse agente se chama Foreman. Fonte: https://github.com/vercel-labs/eve-software-factory-template

Fonte: <https://github.com/vercel-labs/eve-software-factory-template>

## Parte 3: a verificação

Se o critério de pronto só aparece no fim, a conferência chega tarde. Na fábrica, ele nasce no ticket. Os agentes escrevem os testes, e o código passa por tudo isso antes de chegar a você.

Fonte: <https://vercel.com/kb/guide/eve-software-factory>

## O caminho de uma tarefa no Foreman

O modelo pronto se chama eve Software Factory. A tarefa começa numa issue do GitHub e termina num pull request. Repositório: https://github.com/vercel-labs/eve-software-factory-template

1. ponha a etiqueta factory numa issue do GitHub. Resultado: a tarefa entra na fábrica.
2. um agente classifica a tarefa. Resultado: a tarefa ganha categoria.
3. outro agente planeja. Resultado: o plano da tarefa fica pronto.
4. outro escreve o código. Resultado: o código da tarefa é escrito.
5. um revisor confere o resultado. Resultado: o código passa pela conferência.
6. a fábrica entrega um pull request em rascunho. Resultado: você recebe o pull request.
7. você revisa, marca como pronto e faz o merge. Resultado: a decisão final fica com você.

Fonte: <https://github.com/vercel-labs/eve-software-factory-template>

## Revisão feita por outra empresa

O revisor usa um modelo da OpenAI, e o código sai de um modelo da Anthropic. Ele confere o diff real sem ver o raciocínio de quem escreveu, então avalia o que de fato foi alterado. Fonte: https://vercel.com/kb/guide/eve-software-factory

Fonte: <https://vercel.com/kb/guide/eve-software-factory>

## Instalar e ajustar

O Foreman tem licença MIT e instala com um clique neste endereço:

Uma fábrica dessas não vem acabada. Você vai ajustando o pipeline com o tempo. O repositório do modelo está em github.com/vercel-labs/eve-software-factory-template. Página do modelo na Vercel, com deploy de um clique: https://vercel.com/templates/eve/eve-software-factory. Documentação sobre Software Factories na Vercel: https://vercel.com/docs/agent-resources/software-factory

```
vercel.fyi/eve-software-factory
```

Fonte: <https://vercel.com/kb/guide/eve-software-factory>
