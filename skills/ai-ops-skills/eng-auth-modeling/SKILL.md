---
name: eng-auth-modeling
description: "Planeja login, sessões, perfis e regras de acesso, com expiração, recuperação e revogação. Use quando um sistema for ganhar contas de usuário ou revisar quem pode fazer o quê."
---

# Modelagem de autenticação e permissões

Planeja login, sessões, perfis e regras de acesso, com expiração, recuperação e revogação. Use quando um sistema for ganhar contas de usuário ou revisar quem pode fazer o quê.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Tipos de usuário e ações sensíveis do sistema
- Provedor ou biblioteca de autenticação em uso
- Clientes que acessam, como navegador, aplicativo ou outro serviço
- Exigências de segurança e privacidade

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Trate separadamente como a identidade é comprovada e como cada permissão é decidida.
2. Monte uma matriz de perfil, recurso e ação, negando por padrão o que não estiver concedido e indicando regras de posse do registro.
3. Defina como a sessão ou o token é criado, armazenado, renovado, expirado e invalidado.
4. Desenhe cadastro, entrada, recuperação de acesso, troca de perfil e saída, considerando tentativas abusivas e mensagens que não revelem se a conta existe.
5. Indique onde o servidor aplica cada verificação e prefira mecanismos consolidados a criptografia própria.

## O que entregar

Matriz de permissões, diagramas em texto dos fluxos de acesso e casos de teste de autorização.

## Conferência antes de entregar

- [ ] Toda ação sensível é verificada no servidor.
- [ ] Está definido o que acontece com sessões ativas após troca de senha ou remoção de acesso.
- [ ] Há teste de um usuário tentando acessar dados de outro.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
