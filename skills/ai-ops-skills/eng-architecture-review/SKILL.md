---
name: eng-architecture-review
description: "Avalia decisões técnicas contra os requisitos, expondo concessões, pontos únicos de falha e prioridades em um registro de decisão (ADR). Use quando uma arquitetura existente ou proposta precisar de segunda análise."
---

# Revisão de arquitetura

Avalia decisões técnicas contra os requisitos, expondo concessões, pontos únicos de falha e prioridades em um registro de decisão (ADR). Use quando uma arquitetura existente ou proposta precisar de segunda análise.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Diagrama ou descrição da arquitetura
- Requisitos de carga, disponibilidade, segurança e prazo
- Custos atuais e capacidade do time
- Incidentes e dores conhecidos

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Confronte cada decisão com o requisito que ela deveria atender e destaque as que não atendem a nenhum.
2. Procure componentes cuja queda para o sistema, acoplamentos fortes e dados sem recuperação.
3. Compare alternativas, incluindo manter como está, em custo, risco, operação e esforço de migração.
4. Priorize as mudanças pelo risco reduzido e defina passos incrementais.
5. Escreva o ADR com contexto, opções, decisão recomendada, consequências e condições para rever.

## O que entregar

ADR com riscos, alternativas avaliadas e recomendação priorizada.

## Conferência antes de entregar

- [ ] Cada crítica indica o requisito ou cenário afetado.
- [ ] As desvantagens da recomendação também estão descritas.
- [ ] Premissas sobre carga e custo estão visíveis.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
