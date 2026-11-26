---
name: eng-async-job-queue
description: "Tira tarefas demoradas do caminho da requisição, definindo entrega, tempo máximo, fila de mortos (DLQ) e rastreio. Use quando operações lentas travarem respostas ou precisarem de novas tentativas."
---

# Filas e processamento assíncrono

Tira tarefas demoradas do caminho da requisição, definindo entrega, tempo máximo, fila de mortos (DLQ) e rastreio. Use quando operações lentas travarem respostas ou precisarem de novas tentativas.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Tarefas lentas, duração e frequência
- Impacto de atraso, perda ou execução dupla em cada uma
- Infraestrutura de filas disponível
- Como o usuário acompanha o resultado

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Classifique os trabalhos por urgência, duração, volume e tolerância a repetição.
2. Defina a mensagem de cada trabalho com identificador, versão e apenas os dados necessários.
3. Escolha a garantia de entrega e torne o consumidor idempotente quando a mensagem puder chegar mais de uma vez.
4. Estabeleça tempo máximo, número de tentativas, espera entre elas e envio das falhas persistentes para a fila de mortos.
5. Registre o estado de cada trabalho, acompanhe tamanho e idade da fila e descreva como reprocessar.

## O que entregar

Desenho das filas, formato das mensagens, regras de reprocessamento e métricas.

## Conferência antes de entregar

- [ ] Um consumidor que cai no meio não perde nem duplica efeito.
- [ ] A fila de mortos tem responsável e procedimento.
- [ ] O usuário consegue saber se a tarefa terminou ou falhou.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
