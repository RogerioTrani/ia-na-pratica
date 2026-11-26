---
name: eng-task-automation-script
description: "Cria um script que automatiza um trabalho manual, com simulação, tratamento de erros e registro legível. Use quando a mesma sequência de passos for repetida com frequência."
---

# Script para tarefa repetitiva

Cria um script que automatiza um trabalho manual, com simulação, tratamento de erros e registro legível. Use quando a mesma sequência de passos for repetida com frequência.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Passo a passo manual atual
- Exemplos de entrada e resultado esperado
- Sistema operacional e linguagens disponíveis
- O que pode ser apagado, sobrescrito ou enviado

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Defina entradas, saídas, pré-condições e o que o script não deve tocar.
2. Escreva a solução mais simples usando o que já existe no ambiente.
3. Torne a repetição segura, reconhecendo o que já foi feito e evitando resultado parcial.
4. Ofereça modo de simulação que mostre as ações sem executá-las e exija confirmação para as destrutivas.
5. Encerre com código de erro claro, registre o que aconteceu e teste com dados de amostra.

## O que entregar

Script comentado no essencial e instruções de instalação, uso e simulação.

## Conferência antes de entregar

- [ ] A simulação não altera nada.
- [ ] Uma segunda execução não duplica nem corrompe o resultado.
- [ ] Credenciais são lidas de configuração protegida.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
