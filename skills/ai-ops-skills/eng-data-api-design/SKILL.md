---
name: eng-data-api-design
description: "Desenha tabelas ou coleções, relacionamentos, endpoints, autenticação, erros, índices e migrações. Use quando uma funcionalidade nova precisar de dados persistidos ou de uma API para outros consumirem."
---

# Modelo de dados e contratos de API

Desenha tabelas ou coleções, relacionamentos, endpoints, autenticação, erros, índices e migrações. Use quando uma funcionalidade nova precisar de dados persistidos ou de uma API para outros consumirem.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Funcionalidade e consultas que o sistema precisará fazer
- Banco de dados e padrão de API já usados no projeto
- Consumidores da API e como se identificam
- Volume estimado e dados sensíveis envolvidos

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Levante entidades, atributos, chaves e cardinalidades, definindo onde valem unicidade, obrigatoriedade e exclusão em cascata.
2. Liste as consultas mais frequentes e crie apenas os índices que elas justificam.
3. Especifique cada endpoint com método, caminho, parâmetros, corpo, resposta de sucesso, códigos de erro e regra de autorização.
4. Padronize paginação, formato de erro e tratamento de requisições repetidas nas operações que criam ou cobram algo.
5. Planeje a migração sobre os dados atuais e aponte os riscos de compatibilidade com quem já consome a API.

## O que entregar

Esquema de dados, contratos de API com exemplos de requisição e resposta, plano de migração e lista de riscos.

## Conferência antes de entregar

- [ ] Cada endpoint informa quem pode chamá-lo e o que acontece quando não pode.
- [ ] Os nomes e formatos seguem o padrão já existente no repositório.
- [ ] Mudanças que quebram clientes atuais estão sinalizadas para aprovação.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
