---
name: eng-multi-tenant-isolation
description: "Planeja a separação de dados, permissões e uso entre clientes que compartilham o sistema, com testes de isolamento. Use quando uma aplicação passar a atender várias organizações."
---

# Isolamento em aplicação multi-tenant

Planeja a separação de dados, permissões e uso entre clientes que compartilham o sistema, com testes de isolamento. Use quando uma aplicação passar a atender várias organizações.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- O que caracteriza um cliente e como usuários se vinculam a ele
- Exigências de isolamento, residência de dados e plano de cobrança
- Banco, armazenamento, filas e cache utilizados
- Operações administrativas que cruzam clientes

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Compare banco separado, esquema separado e tabelas compartilhadas e escolha conforme isolamento exigido e custo de operação.
2. Derive o identificador do cliente da sessão autenticada, nunca de um valor livre enviado pelo navegador.
3. Aplique o filtro e a autorização em consultas, arquivos, cache, filas, buscas, logs e relatórios.
4. Defina como o consumo de cada cliente é medido, limitado e cobrado.
5. Crie testes com dois clientes em que um tenta ler, alterar e exportar dados do outro.

## O que entregar

Arquitetura de multi-tenancy, regras de autorização por camada e testes de isolamento.

## Conferência antes de entregar

- [ ] Não existe caminho de acesso a dados sem o filtro do cliente.
- [ ] Acessos administrativos entre clientes são restritos e registrados.
- [ ] Tarefas em segundo plano mantêm o contexto do cliente correto.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
