---
name: eng-error-handling
description: "Organiza as falhas do sistema com categorias, mensagens, registro e regras de nova tentativa. Use quando os erros chegam confusos ao usuário ou cada parte do código reage de um jeito."
---

# Padrão de tratamento de erros

Organiza as falhas do sistema com categorias, mensagens, registro e regras de nova tentativa. Use quando os erros chegam confusos ao usuário ou cada parte do código reage de um jeito.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Pontos onde o sistema falha hoje e exemplos de mensagens
- Linguagem, framework e formato de erro já adotado
- Públicos que leem os erros, como usuário final, suporte e desenvolvedor
- Operações que não podem ser executadas duas vezes

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Agrupe as falhas em corrigíveis pelo usuário, temporárias e defeitos que exigem intervenção.
2. Atribua a cada tipo um código estável, uma mensagem que diga ao usuário o próximo passo e um detalhe técnico só para os logs.
3. Defina em qual camada cada erro é capturado e convertido, evitando capturas que engolem a falha.
4. Permita nova tentativa apenas em falhas temporárias e operações idempotentes, com espera crescente e limite.
5. Aplique o padrão a um fluxo real e teste cada categoria.

## O que entregar

Tabela de erros com código, resposta, registro e ação, mais exemplos de implementação.

## Conferência antes de entregar

- [ ] Mensagens públicas não mostram rastros, consultas nem dados internos.
- [ ] Todo erro inesperado fica registrado com contexto suficiente para investigar.
- [ ] Nenhuma repetição automática pode duplicar cobrança, envio ou gravação.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
