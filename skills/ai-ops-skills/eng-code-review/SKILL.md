---
name: eng-code-review
description: "Analisa um conjunto de mudanças em busca de defeitos, falhas de segurança, lentidão e complexidade sobrando. Use quando houver um diff ou pedido de integração aguardando aprovação."
---

# Revisão de código por severidade

Analisa um conjunto de mudanças em busca de defeitos, falhas de segurança, lentidão e complexidade sobrando. Use quando houver um diff ou pedido de integração aguardando aprovação.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Diff ou lista de arquivos alterados
- Objetivo da mudança e requisito de origem
- Padrões de código e arquivo de instruções do projeto, se houver
- Resultado dos testes e da verificação automática

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Entenda a intenção da mudança e leia também os chamadores e contratos que o diff não mostra.
2. Verifique a correção em casos limite, valores vazios, concorrência, erros ignorados e diferença entre o pedido e o implementado.
3. Procure entrada não validada, falha de autorização, segredo exposto, consulta repetida em laço e trabalho desnecessário.
4. Aponte abstrações, duplicações ou código sem uso que possam ser removidos sem perder função.
5. Classifique cada achado como bloqueante, importante ou sugestão, com arquivo, linha, cenário que causa o problema e correção proposta.

## O que entregar

Relatório de achados ordenados por severidade, com referência ao código e parecer de aprovar ou pedir ajustes.

## Conferência antes de entregar

- [ ] Cada achado aponta um local e explica como o problema se manifesta.
- [ ] Preferências de estilo estão separadas de defeitos reais.
- [ ] Está dito o que não foi possível verificar.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
