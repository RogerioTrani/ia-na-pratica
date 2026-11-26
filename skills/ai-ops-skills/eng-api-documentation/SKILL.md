---
name: eng-api-documentation
description: "Produz referência de endpoints com autenticação, exemplos, erros e histórico de versões. Use quando outros desenvolvedores precisarem consumir a API sem depender de explicação oral."
---

# Documentação de API

Produz referência de endpoints com autenticação, exemplos, erros e histórico de versões. Use quando outros desenvolvedores precisarem consumir a API sem depender de explicação oral.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Código das rotas ou especificação existente
- Público consumidor e forma de obter acesso
- Política de versão e mudanças recentes
- Ambiente em que os exemplos possam ser testados

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Extraia do código as rotas, parâmetros, tipos e permissões reais, apontando diferenças em relação ao que já estava escrito.
2. Abra com um guia de primeira chamada, da obtenção da credencial até uma resposta bem-sucedida.
3. Documente cada rota com finalidade, campos obrigatórios, limites, exemplo de chamada e de resposta.
4. Liste os erros possíveis com a causa e o que o consumidor deve fazer.
5. Registre a versão e as mudanças, destacando as que quebram compatibilidade.

## O que entregar

Referência dos endpoints, guia de início, exemplos de chamadas e registro de mudanças.

## Conferência antes de entregar

- [ ] Os exemplos batem com o comportamento do código ou estão marcados como não testados.
- [ ] As credenciais mostradas são fictícias.
- [ ] Nenhuma rota interna foi publicada na documentação externa.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
