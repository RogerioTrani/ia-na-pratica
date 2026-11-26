---
name: eng-app-architecture
description: "Define componentes, fronteiras e fluxos críticos de um sistema, pesando custo e complexidade. Use quando for iniciar uma aplicação ou reorganizar uma que está com responsabilidades misturadas."
---

# Arquitetura da aplicação

Define componentes, fronteiras e fluxos críticos de um sistema, pesando custo e complexidade. Use quando for iniciar uma aplicação ou reorganizar uma que está com responsabilidades misturadas.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- O que o sistema faz e quais fluxos não podem falhar
- Stack atual, ambiente de execução e arquivo de instruções do projeto, se houver
- Tamanho do time e orçamento de infraestrutura
- Integrações externas e carga esperada

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Divida o sistema em interface, regras de domínio, persistência e integrações, dizendo o que cada parte pode e não pode conhecer das outras.
2. Percorra os fluxos críticos componente por componente, indicando onde há chamada síncrona, fila, transação e ponto de falha.
3. Compare a opção mais simples com a alternativa mais elaborada em custo, operação e dificuldade de mudar depois.
4. Registre cada decisão com o motivo, as opções descartadas e o sinal que justificaria revê-la.

## O que entregar

Diagrama em texto dos componentes e fluxos, acompanhado do registro das decisões arquiteturais.

## Conferência antes de entregar

- [ ] Cada componente tem uma responsabilidade que cabe em uma frase.
- [ ] Nenhuma camada ou serviço foi incluído sem um requisito que o exija.
- [ ] Os fluxos críticos dizem o que acontece quando uma dependência falha.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
