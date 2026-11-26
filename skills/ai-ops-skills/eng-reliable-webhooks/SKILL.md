---
name: eng-reliable-webhooks
description: "Constrói o recebimento de eventos externos com verificação de assinatura, proteção contra duplicidade e controle de ordem. Use quando outro serviço for notificar o sistema por webhook."
---

# Recepção confiável de webhooks

Constrói o recebimento de eventos externos com verificação de assinatura, proteção contra duplicidade e controle de ordem. Use quando outro serviço for notificar o sistema por webhook.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Documentação dos eventos e do método de assinatura do emissor
- Ação que cada evento dispara no sistema
- Política de reenvio e tempo de resposta exigidos pelo emissor
- Banco ou fila disponíveis para guardar eventos

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Valide a assinatura sobre o corpo bruto, junto com o horário do envio quando existir, e rejeite o que não conferir.
2. Grave o identificador do evento com restrição de unicidade antes de produzir qualquer efeito.
3. Responda rapidamente e processe o trabalho pesado fora da requisição, com novas tentativas limitadas.
4. Lide com eventos atrasados ou fora de ordem comparando versão ou consultando o estado atual na origem.
5. Teste assinatura inválida, repetição, ordem trocada, formato desconhecido e queda no meio do processamento.

## O que entregar

Contrato do webhook, código ou desenho do receptor e casos de teste.

## Conferência antes de entregar

- [ ] O mesmo evento recebido duas vezes causa um único efeito.
- [ ] O segredo de assinatura fica protegido e fora dos logs.
- [ ] Eventos que falham definitivamente podem ser localizados e reprocessados.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
