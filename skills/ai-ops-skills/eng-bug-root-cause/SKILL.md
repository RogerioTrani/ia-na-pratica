---
name: eng-bug-root-cause
description: "Investiga uma falha reproduzível até a causa raiz, corrige e protege com teste de regressão. Use quando houver erro, resultado incorreto ou comportamento inesperado no software."
---

# Caça à causa raiz de bugs

Investiga uma falha reproduzível até a causa raiz, corrige e protege com teste de regressão. Use quando houver erro, resultado incorreto ou comportamento inesperado no software.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Sintoma observado e comportamento esperado
- Passos para reproduzir, ambiente e versão
- Mensagens de erro, rastros e logs disponíveis
- Mudanças recentes no código, configuração ou dados

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Reproduza a falha e anote as condições em que ela acontece e em que deixa de acontecer.
2. Reduza o cenário ao menor caso que ainda quebra, retirando dados e componentes irrelevantes.
3. Liste hipóteses em ordem de probabilidade e teste uma de cada vez com logs, depurador ou verificações pontuais.
4. Depois de achar a origem, escreva um teste que falhe por causa dela e aplique a correção no ponto compartilhado pelos chamadores.
5. Confirme que o teste passa, procure o mesmo erro em outros trechos e retire a instrumentação temporária.

## O que entregar

Explicação da causa raiz com a evidência, correção em código e teste de regressão.

## Conferência antes de entregar

- [ ] A causa explica todos os sintomas relatados.
- [ ] O teste falha sem a correção e passa com ela, ou está registrado que isso não foi executado.
- [ ] Se não houve reprodução, o relatório diz isso e apresenta a causa apenas como provável.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
