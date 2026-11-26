---
name: eng-database-migration
description: "Planeja mudanças de esquema e de dados em etapas compatíveis, com backup e reversão. Use quando for alterar tabelas ou formatos de um banco que já guarda dados em uso."
---

# Migração de banco com segurança

Planeja mudanças de esquema e de dados em etapas compatíveis, com backup e reversão. Use quando for alterar tabelas ou formatos de um banco que já guarda dados em uso.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Esquema atual e esquema desejado
- Banco utilizado, volume das tabelas e horários de pico
- Versões da aplicação que lerão e escreverão durante a transição
- Rotina de backup e tolerância a indisponibilidade

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Avalie quais operações bloqueiam tabelas ou quebram a versão da aplicação que ainda estará no ar.
2. Primeiro expanda o esquema com estruturas novas que não afetam o código antigo.
3. Copie os dados em lotes que possam ser retomados e compare contagens e amostras entre origem e destino.
4. Passe a aplicação para a estrutura nova e só remova a antiga depois de um período de observação.
5. Ensaie backup, restauração e reversão em uma cópia, anotando o ponto a partir do qual voltar atrás perde dados.

## O que entregar

Roteiro de migração em SQL ou pseudocódigo, com verificações por etapa e plano de reversão.

## Conferência antes de entregar

- [ ] Cada etapa informa como confirmar o sucesso e como desfazer.
- [ ] Passos destrutivos estão separados e exigem aprovação explícita.
- [ ] Nada é aplicado em produção sem ensaio e backup restaurável.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
