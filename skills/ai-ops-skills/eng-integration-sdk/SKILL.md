---
name: eng-integration-sdk
description: "Encapsula uma API em biblioteca simples, com autenticação e erros padronizados, exemplos e testes. Use quando vários consumidores repetirem o mesmo código para chamar o serviço."
---

# SDK para uma API

Encapsula uma API em biblioteca simples, com autenticação e erros padronizados, exemplos e testes. Use quando vários consumidores repetirem o mesmo código para chamar o serviço.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Contrato da API e versão
- Linguagens dos consumidores
- Operações mais usadas
- Forma de distribuição pretendida

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Escolha poucas operações principais e escreva primeiro como o consumidor gostaria de chamá-las.
2. Centralize endereço base, credenciais, tempo máximo e novas tentativas seguras em um único cliente.
3. Converta respostas e falhas em tipos e erros próprios, preservando o identificador da requisição.
4. Teste com respostas simuladas e, se houver, no ambiente de testes da API.
5. Documente instalação, exemplo mínimo, configuração e política de versões.

## O que entregar

Esqueleto do SDK com operações principais, testes e documentação de uso.

## Conferência antes de entregar

- [ ] O exemplo mínimo corresponde à interface realmente implementada.
- [ ] Credenciais não aparecem em erros nem em logs.
- [ ] Publicar o pacote fica pendente de aprovação.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
