---
name: eng-work-orchestration
description: "Divide uma demanda grande em tarefas por frente, com dependências, interfaces e ordem de execução. Use quando várias pessoas ou agentes vão desenvolver em paralelo e é preciso evitar conflito e retrabalho."
---

# Orquestração de frentes de desenvolvimento

Divide uma demanda grande em tarefas por frente, com dependências, interfaces e ordem de execução. Use quando várias pessoas ou agentes vão desenvolver em paralelo e é preciso evitar conflito e retrabalho.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Requisito ou objetivo a entregar e como saber que está pronto
- Repositório, stack e arquivo de instruções do projeto, se houver
- Quem executa cada frente (pessoas ou agentes) e prazo
- Testes existentes e partes do código que não podem ser mexidas

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Escreva o escopo em itens verificáveis e anote o que fica explicitamente de fora.
2. Fixe antes os contratos entre as partes (assinaturas, formatos de dados, eventos) para que cada frente avance sem esperar a outra.
3. Separe as tarefas que podem correr em paralelo das que dependem de uma anterior, evitando que duas frentes editem os mesmos arquivos.
4. Dê a cada tarefa um responsável, o teste que comprova a conclusão e o ponto em que ela será integrada.
5. Ordene o backlog pelo caminho crítico e marque quais tarefas de risco precisam de aprovação antes de começar.

## O que entregar

Backlog técnico em ordem de execução, com dependências, responsáveis, contratos entre frentes e pontos de integração.

## Conferência antes de entregar

- [ ] Cada tarefa tem critério de pronto que alguém consegue testar.
- [ ] Não há dependência circular nem duas tarefas paralelas disputando o mesmo arquivo.
- [ ] A integração entre as frentes tem dono e teste definidos.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
