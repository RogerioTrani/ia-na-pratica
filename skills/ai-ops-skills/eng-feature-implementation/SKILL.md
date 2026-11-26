---
name: eng-feature-implementation
description: "Escreve o código de uma funcionalidade seguindo os padrões do repositório, com validação, tratamento de erros e testes. Use quando houver um requisito definido pronto para virar código."
---

# Implementação de funcionalidade

Escreve o código de uma funcionalidade seguindo os padrões do repositório, com validação, tratamento de erros e testes. Use quando houver um requisito definido pronto para virar código.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Requisito e critérios de aceite
- Acesso ao repositório e comandos de teste e build
- Arquivo de instruções do projeto, se houver
- Partes do sistema afetadas e restrições de compatibilidade

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Leia código parecido já existente e copie a forma de organizar, nomear, validar e testar usada ali.
2. Confirme as ambiguidades que mudariam o comportamento e anote as suposições feitas nas demais.
3. Escreva um teste que expresse o critério de aceite e veja-o falhar antes de implementar.
4. Faça a menor alteração que atende ao requisito, validando entradas nas fronteiras e tratando os erros que podem realmente ocorrer.
5. Rode a suíte do projeto, revise o diff para tirar mudanças alheias ao pedido e escreva como usar a novidade.

## O que entregar

Código da funcionalidade, testes correspondentes e notas curtas de uso e configuração.

## Conferência antes de entregar

- [ ] Os critérios de aceite foram comprovados por teste, com o resultado da execução informado ou declarado como não executado.
- [ ] O diff não traz refatoração nem formatação fora do escopo.
- [ ] Nenhum segredo ou dado real foi colocado no código ou nos testes.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
