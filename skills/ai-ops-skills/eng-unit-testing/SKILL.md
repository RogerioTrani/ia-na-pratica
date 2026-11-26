---
name: eng-unit-testing
description: "Cria testes unitários para casos comuns, limites e entradas inválidas, verificando o que o código entrega. Use quando uma função ou módulo precisar de proteção contra regressões."
---

# Testes unitários de funções e módulos

Cria testes unitários para casos comuns, limites e entradas inválidas, verificando o que o código entrega. Use quando uma função ou módulo precisar de proteção contra regressões.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Código a testar e regras que ele deve cumprir
- Framework de testes e convenções do repositório
- Dependências externas chamadas pelo módulo
- Falhas já ocorridas nessa parte

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Monte uma lista de casos cobrindo uso normal, bordas, vazios, valores inválidos e erros esperados.
2. Substitua somente o que torna o teste lento ou imprevisível, como rede, relógio, aleatoriedade e armazenamento.
3. Escreva um teste por comportamento, com nome que descreva a situação e o resultado.
4. Verifique retornos, estado e efeitos visíveis, sem amarrar o teste à forma interna da implementação.
5. Execute a suíte repetidas vezes e anote os comportamentos que ficaram sem cobertura e o motivo.

## O que entregar

Suíte de testes unitários no padrão do projeto e relatório das lacunas restantes.

## Conferência antes de entregar

- [ ] Alterar de propósito uma regra importante faz algum teste falhar.
- [ ] Os testes não dependem de ordem, rede ou horário da máquina.
- [ ] Divergências entre o código e a regra foram relatadas, não fixadas como comportamento correto.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
