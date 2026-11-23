# Vercel abre o Formidable, fábrica de agentes no GitHub

_2026-11-23 · reportagem_

A Vercel abriu um modelo de fábrica de software em que agentes de IA classificam, planejam, programam e revisam tarefas a partir de uma issue do GitHub. O modelo se chama eve Software Factory, e o agente orquestrador, Foreman. O resultado chega como pull request em rascunho, e a decisão de aprovar e fazer o merge continua com você. Esta apostila mostra as três partes da fábrica, o caminho de uma tarefa e onde pegar o modelo.

## A ideia: desenvolvimento como linha de produção

Uma fábrica de software tem três partes: entrada, orquestrador e verificação. Quem está na frente trata o desenvolvimento como linha de produção, em que cada pedido passa por etapas definidas e sai com um critério claro de pronto. O assistente de código, que só escreve trechos, fica de fora desse desenho.

- Parte 1: a entrada, onde tudo vira ticket
- Parte 2: o orquestrador, um agente chefe
- Parte 3: a verificação, presente desde o começo

## Parte 1: a entrada

A demanda pode vir de qualquer lugar: pedido de cliente, bug reclamado no Discord ou ideia sua. Tudo é padronizado no mesmo formato antes de andar. Cada item vira um ticket, a peça que passa pela fábrica.

## Parte 2: o orquestrador

Em vez de você distribuir tarefa por tarefa, um agente chefe cuida da fila. Ele pega cada ticket, decide o que roda junto e o que espera, e entrega o trabalho aos agentes que executam. Como ele enxerga as dependências, libera em paralelo só o que pode andar. No modelo da Vercel, esse agente se chama Foreman.

Fonte: <https://github.com/vercel-labs/eve-software-factory-template>

## Parte 3: a verificação

Se o critério de pronto só aparece no fim, a conferência chega tarde. Na fábrica, ele nasce no ticket. Os agentes escrevem os testes, e o código passa por tudo isso antes de chegar a você.

## O caminho de uma tarefa no Foreman

O modelo pronto se chama eve Software Factory. A tarefa começa numa issue do GitHub e termina num pull request.

- Ponha a etiqueta factory numa issue do GitHub.
- Um agente classifica a tarefa.
- Outro agente planeja.
- Outro escreve o código.
- Um revisor confere o resultado.
- A fábrica entrega um pull request em rascunho.
- Você revisa, marca como pronto e faz o merge.

Fonte: <https://github.com/vercel-labs/eve-software-factory-template>

## Revisão feita por outra empresa

O revisor usa um modelo da OpenAI, e o código sai de um modelo da Anthropic. Ele confere o diff real sem ver o raciocínio de quem escreveu, então avalia o que de fato foi alterado.

Fonte: <https://vercel.com/kb/guide/eve-software-factory>

## Instalar e ajustar

O Foreman tem licença MIT e instala com um clique neste endereço:

Uma fábrica dessas não vem acabada. Você vai ajustando o pipeline com o tempo. O repositório do modelo está em github.com/vercel-labs/eve-software-factory-template.

```
vercel.fyi/eve-software-factory
```

Fonte: <https://vercel.com/kb/guide/eve-software-factory>

## Além do vídeo

- Página do modelo na Vercel, com deploy de um clique: https://vercel.com/templates/eve/eve-software-factory
- Guia oficial para montar uma fábrica de software com eve: https://vercel.com/kb/guide/eve-software-factory
- Documentação sobre Software Factories na Vercel: https://vercel.com/docs/agent-resources/software-factory
