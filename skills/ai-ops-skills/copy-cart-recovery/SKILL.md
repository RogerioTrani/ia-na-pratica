---
name: copy-cart-recovery
description: "Cria mensagens para retomar compras interrompidas conforme o motivo provável. Use quando houver carrinhos abandonados ou pagamentos que falham e a empresa puder contatar essas pessoas."
---

# Recuperação de carrinho

Cria mensagens para retomar compras interrompidas conforme o motivo provável. Use quando houver carrinhos abandonados ou pagamentos que falham e a empresa puder contatar essas pessoas.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Eventos disponíveis, como abandono, recusa de pagamento ou boleto pendente
- Meios de pagamento, entrega, acesso e suporte
- Canal autorizado para contato e intervalo permitido
- Condições da oferta e se existe prazo ou estoque limitado de verdade

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Separe os casos de falha técnica dos casos de hesitação usando os eventos registrados, sem adivinhar o que não foi medido.
2. Para falhas, explique o que ocorreu em termos simples e como concluir por outro caminho.
3. Para hesitação, esclareça dúvidas de pagamento, acesso e suporte e ofereça ajuda de uma pessoa.
4. Escreva no máximo três mensagens, com momento de envio e interrupção automática quando houver compra ou pedido para parar.
5. Retire qualquer alerta de vaga, estoque ou tempo que não esteja confirmado.

## O que entregar

Sequência de até três mensagens por cenário, com gatilho, intervalo e condição de parada.

## Conferência antes de entregar

- [ ] Quem já pagou não é abordado como devedor ou desistente.
- [ ] Não há cupom ou urgência criada sem aprovação.
- [ ] A mensagem não expõe dados de pagamento do comprador.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
