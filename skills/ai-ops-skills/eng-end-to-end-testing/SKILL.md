---
name: eng-end-to-end-testing
description: "Automatiza as jornadas mais importantes do usuário, incluindo erros, permissões e retomada. Use quando for preciso comprovar que o sistema completo funciona antes de entregar uma mudança."
---

# Testes ponta a ponta das jornadas

Automatiza as jornadas mais importantes do usuário, incluindo erros, permissões e retomada. Use quando for preciso comprovar que o sistema completo funciona antes de entregar uma mudança.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Jornadas que sustentam o produto e perfis de usuário
- Endereço do ambiente de teste e contas de teste
- Ferramenta de automação já adotada, se houver
- Critérios de aceite de cada jornada

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Escolha poucas jornadas pelo estrago que a quebra causaria e descreva cada uma do ponto de vista do usuário.
2. Automatize usando seletores por papel, rótulo ou identificador próprio para teste, evitando posição e aparência.
3. Espere por condições observáveis em vez de pausas fixas e verifique o resultado final de cada jornada.
4. Inclua entrada errada, acesso negado, sessão expirada, perda de conexão e retorno ao fluxo.
5. Execute no ambiente de teste e guarde o registro do que passou, falhou ou ficou instável.

## O que entregar

Roteiros ponta a ponta automatizados e evidências da execução, como logs e capturas.

## Conferência antes de entregar

- [ ] Só é relatado como aprovado o que de fato foi executado.
- [ ] Os testes criam os próprios dados e não afetam usuários reais.
- [ ] Falhas intermitentes estão investigadas ou sinalizadas, sem serem escondidas por novas tentativas.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
