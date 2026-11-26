---
name: eng-payments-integration
description: "Modela estados de cobrança, notificações do provedor e reconciliação sem expor dados sensíveis. Use quando o produto for cobrar assinaturas ou compras por um provedor de pagamento."
---

# Integração de pagamentos

Modela estados de cobrança, notificações do provedor e reconciliação sem expor dados sensíveis. Use quando o produto for cobrar assinaturas ou compras por um provedor de pagamento.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Tipo de cobrança, meios de pagamento e moeda
- Documentação e ambiente de testes do provedor
- O que é liberado ao pagar e o que acontece em atraso ou estorno
- Necessidades do financeiro para conferência

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Desenhe a máquina de estados com pendente, aprovado, recusado, cancelado, estornado e contestado, definindo transições válidas.
2. Use a coleta de cartão do próprio provedor, guardando apenas referências, sem número completo nem código de segurança.
3. Valide a assinatura das notificações, trate repetições e ordem trocada e envie chave de idempotência ao criar cobranças.
4. Libere o produto somente após confirmação do servidor e represente valores em unidade inteira ou decimal exato.
5. Planeje a reconciliação periódica entre registros internos e extrato do provedor, com tratamento das divergências.

## O que entregar

Fluxo de pagamentos, matriz de estados e transições, rotina de reconciliação e casos de teste.

## Conferência antes de entregar

- [ ] Repetir uma requisição ou notificação não cobra nem libera duas vezes.
- [ ] Testes usam somente o ambiente de testes do provedor.
- [ ] Ativar chaves reais ou movimentar dinheiro depende de aprovação.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
