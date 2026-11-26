---
name: eng-external-api-integration
description: "Projeta o cliente de um serviço externo com autenticação, limites, tempo máximo, novas tentativas e registro seguro. Use quando o sistema precisar consumir uma API que pode falhar ou mudar."
---

# Integração com API de terceiros

Projeta o cliente de um serviço externo com autenticação, limites, tempo máximo, novas tentativas e registro seguro. Use quando o sistema precisar consumir uma API que pode falhar ou mudar.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Documentação oficial da API e versão a usar
- Operações necessárias e volume previsto
- Ambiente de testes do fornecedor e forma de guardar credenciais
- Impacto no usuário se o serviço ficar indisponível

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Confirme na documentação o método de autenticação, a validade das credenciais, os limites de uso e a paginação.
2. Isole as chamadas em um módulo próprio que converta as respostas externas para os tipos do sistema.
3. Monte a matriz de falhas, definindo para tempo esgotado, limite excedido, erro do cliente e erro do servidor se há nova tentativa, com qual espera e quando desistir.
4. Só repita operações com efeito quando houver chave de idempotência ou outra garantia contra duplicidade.
5. Registre identificador, duração e resultado de cada chamada, mascarando tokens e dados pessoais, e teste as falhas com respostas simuladas.

## O que entregar

Cliente da API, matriz de falhas com a reação a cada uma e testes para sucesso e erro.

## Conferência antes de entregar

- [ ] Toda chamada tem tempo máximo definido.
- [ ] Credenciais vêm de configuração protegida e não aparecem nos logs.
- [ ] Nada foi disparado contra o ambiente de produção do fornecedor sem autorização.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
