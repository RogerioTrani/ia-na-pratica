---
name: eng-safe-refactoring
description: "Planeja e conduz melhorias de estrutura em passos pequenos, protegidos por testes de regressão. Use quando o código estiver difícil de manter e o comportamento externo precisar continuar igual."
---

# Refatoração sem mudar comportamento

Planeja e conduz melhorias de estrutura em passos pequenos, protegidos por testes de regressão. Use quando o código estiver difícil de manter e o comportamento externo precisar continuar igual.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Trecho a refatorar e o incômodo concreto que ele causa
- Comportamentos que outros dependem, inclusive os estranhos
- Cobertura de testes atual e como executá-la
- Limites de escopo e prazo

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Liste saídas, efeitos colaterais, mensagens de erro e contratos que precisam permanecer idênticos.
2. Escreva testes que capturem o comportamento atual onde faltar proteção e rode-os antes de tocar no código.
3. Quebre o trabalho em transformações pequenas, cada uma reversível e integrável sozinha.
4. Rode os testes após cada passo e desfaça o passo se algo mudar, em vez de ajustar o teste.
5. Registre à parte os defeitos descobertos, para correção em mudança separada.

## O que entregar

Plano de refatoração em etapas, testes de proteção e critérios que demonstram a equivalência.

## Conferência antes de entregar

- [ ] Os mesmos testes passam antes e depois sem terem sido afrouxados.
- [ ] Nenhuma funcionalidade nova ou correção entrou misturada.
- [ ] Interfaces usadas por terceiros continuam compatíveis ou têm aprovação para mudar.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
