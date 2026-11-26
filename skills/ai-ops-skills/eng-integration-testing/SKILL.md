---
name: eng-integration-testing
description: "Planeja e escreve testes das interfaces entre serviços, banco e integrações, cobrindo sucesso, falha e repetição. Use quando partes que funcionam sozinhas precisarem ser validadas juntas."
---

# Testes de integração entre componentes

Planeja e escreve testes das interfaces entre serviços, banco e integrações, cobrindo sucesso, falha e repetição. Use quando partes que funcionam sozinhas precisarem ser validadas juntas.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Componentes envolvidos e contratos entre eles
- Ambiente de teste isolado e como subir as dependências
- Dados necessários para cada cenário
- Falhas de integração já conhecidas

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Desenhe quem chama quem e anote o formato, a ordem e as garantias esperadas em cada fronteira.
2. Decida quais dependências rodam de verdade no ambiente de teste e quais serão simuladas.
3. Prepare dados controlados que cada teste cria e limpa, sem depender de sobras de execuções anteriores.
4. Cubra o caminho de sucesso, a resposta de erro, a demora, a interrupção no meio e a mesma mensagem enviada duas vezes.
5. Confira o estado final nos dois lados da fronteira, e não apenas o código de resposta.

## O que entregar

Lista de cenários e testes de integração com preparação de dados e instruções de execução.

## Conferência antes de entregar

- [ ] Nenhum teste usa banco ou serviço de produção.
- [ ] Há cenário de falha para cada dependência importante.
- [ ] A suíte pode ser executada duas vezes seguidas com o mesmo resultado.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
