---
name: eng-transactional-email
description: "Especifica mensagens disparadas por eventos, com modelos, preferências, falhas e entregabilidade. Use quando o sistema precisar enviar confirmações, avisos ou recuperação de acesso por e-mail."
---

# E-mails transacionais

Especifica mensagens disparadas por eventos, com modelos, preferências, falhas e entregabilidade. Use quando o sistema precisar enviar confirmações, avisos ou recuperação de acesso por e-mail.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Eventos do produto que devem gerar mensagem
- Provedor de envio e domínio remetente
- Idioma, tom e dados que cada mensagem precisa mostrar
- Regras de preferência e privacidade

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Monte um catálogo com evento, destinatário, assunto, variáveis, prazo de envio e se o usuário pode desativar.
2. Redija modelos com versão em texto simples, valores de reserva para variáveis ausentes e apenas os dados indispensáveis.
3. Envie por fila, com chave que impeça duplicidade, nova tentativa em falha temporária e registro do estado.
4. Configure a autenticação do domínio (SPF, DKIM e DMARC) e trate devoluções e denúncias de spam.
5. Teste a renderização e os eventos em modo de teste, com destinatários controlados.

## O que entregar

Especificação dos eventos e das mensagens, modelos e regras de envio e falha.

## Conferência antes de entregar

- [ ] Links com acesso têm validade e uso limitado.
- [ ] Um evento repetido não gera e-mail em dobro.
- [ ] Nenhuma mensagem real é enviada sem autorização.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
