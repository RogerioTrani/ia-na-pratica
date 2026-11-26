---
name: eng-project-cli-design
description: "Especifica comandos internos com argumentos, validação, ajuda, saídas e códigos de erro consistentes. Use quando tarefas do projeto estiverem espalhadas em scripts soltos."
---

# Interface de linha de comando do projeto

Especifica comandos internos com argumentos, validação, ajuda, saídas e códigos de erro consistentes. Use quando tarefas do projeto estiverem espalhadas em scripts soltos.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Operações frequentes e scripts existentes
- Quem usa e se há uso em automação
- Linguagem e bibliotecas do repositório
- Operações com risco

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Reúna as operações repetidas e agrupe-as em comandos e subcomandos com nomes previsíveis.
2. Defina para cada um argumentos obrigatórios, opções, padrões e mensagens para valor inválido.
3. Separe o resultado na saída padrão das mensagens na saída de erro e preveja formato legível por máquina quando houver automação.
4. Padronize códigos de término, texto de ajuda e confirmação ou simulação para ações perigosas.
5. Escreva exemplos de uso correto e incorreto que sirvam de casos de teste.

## O que entregar

Especificação dos comandos, texto de ajuda e exemplos.

## Conferência antes de entregar

- [ ] Todo comando funciona sem pergunta interativa quando chamado por automação.
- [ ] Opções com o mesmo nome se comportam igual em todos os comandos.
- [ ] Falhas retornam código diferente de zero.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
