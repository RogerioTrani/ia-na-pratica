---
name: eng-deploy-readiness
description: "Verifica ambientes, segredos, migrações e testes antes de publicar, com plano de reversão e observação. Use quando uma versão estiver prestes a ir para produção."
---

# Prontidão para publicar em produção

Verifica ambientes, segredos, migrações e testes antes de publicar, com plano de reversão e observação. Use quando uma versão estiver prestes a ir para produção.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Mudanças incluídas na versão
- Resultado dos testes e do build
- Variáveis, segredos e migrações necessários
- Janela de publicação e responsáveis

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Compare a configuração de produção com a do ambiente de teste e liste variáveis e permissões que faltam, só pelos nomes.
2. Confirme que o artefato a publicar é o mesmo que foi testado.
3. Defina a ordem entre migrações, serviços e interface, garantindo convivência entre versão antiga e nova.
4. Escreva o gatilho, o responsável e os comandos da reversão, incluindo o que não pode ser desfeito.
5. Liste os sinais a observar após a publicação, por quanto tempo e os testes rápidos de fumaça.

## O que entregar

Checklist de publicação e de pós-publicação, com plano de reversão.

## Conferência antes de entregar

- [ ] Cada item está marcado como confirmado, pendente ou não verificável.
- [ ] Existe backup válido antes de mudança em dados.
- [ ] A publicação em si só ocorre com aprovação explícita.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
