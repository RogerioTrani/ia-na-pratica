---
name: traffic-conversion-tracking
description: "Especifica eventos, parâmetros UTM, deduplicação, consentimento e testes para medir o funil. Use quando for implantar a mensuração ou houver conversões divergentes ou duplicadas."
---

# Plano de rastreamento de conversões

Especifica eventos, parâmetros UTM, deduplicação, consentimento e testes para medir o funil. Use quando for implantar a mensuração ou houver conversões divergentes ou duplicadas.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Etapas do funil e ações que contam como conversão
- Site, aplicativo, checkout e ferramentas de medição em uso
- Eventos já enviados e divergências conhecidas
- Política de privacidade e coleta de consentimento
- Ambiente de teste e responsável técnico

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Liste cada evento com gatilho, parâmetros, origem de envio, destino e conversão correspondente.
2. Padronize os valores de UTM em uma convenção única de maiúsculas, separadores e nomes de campanha.
3. Defina um identificador compartilhado para que envios do navegador e do servidor não contem duas vezes.
4. Verifique o que só pode disparar após consentimento e quais dados pessoais não devem ser transmitidos.
5. Escreva um roteiro que percorra do clique no anúncio à conversão e compare os registros em cada sistema.

## O que entregar

Especificação de eventos, convenção de UTMs, regra de deduplicação e checklist de testes de ponta a ponta.

## Conferência antes de entregar

- [ ] Todo evento tem gatilho único e verificável.
- [ ] Consentimento e privacidade foram tratados em cada coleta.
- [ ] O rastreamento só é dito testado se a validação foi executada.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
