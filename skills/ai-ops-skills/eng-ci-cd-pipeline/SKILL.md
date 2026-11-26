---
name: eng-ci-cd-pipeline
description: "Projeta as etapas de verificação, build e publicação, com ambientes, segredos, travas e reversão. Use quando as entregas forem manuais, imprevisíveis ou chegarem quebradas à produção."
---

# Pipeline de integração e entrega

Projeta as etapas de verificação, build e publicação, com ambientes, segredos, travas e reversão. Use quando as entregas forem manuais, imprevisíveis ou chegarem quebradas à produção.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Repositório, stack e comandos de verificação, teste e build
- Plataforma de automação e destino da publicação
- Ambientes existentes e quem aprova cada um
- Segredos necessários e onde ficam guardados

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Encadeie análise estática, testes e build, deixando as checagens rápidas primeiro para falhar cedo.
2. Gere o artefato uma única vez e promova o mesmo entre os ambientes.
3. Separe credenciais por ambiente, com o menor acesso possível e fora do repositório e dos logs.
4. Estabeleça as travas de promoção, incluindo aprovação humana antes da produção.
5. Defina como voltar à versão anterior, inclusive quando houver migração de dados, e teste esse caminho.

## O que entregar

Proposta de pipeline em configuração ou pseudocódigo e política de publicação e reversão.

## Conferência antes de entregar

- [ ] Uma falha em qualquer verificação impede a publicação.
- [ ] Contribuições não confiáveis não têm acesso a segredos.
- [ ] Nada é publicado de verdade sem autorização.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
