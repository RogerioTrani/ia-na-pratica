---
name: eng-data-pipeline-design
description: "Planeja coleta, limpeza, versionamento, acesso e validação de dados, com dicionário. Use quando dados de várias origens precisarem virar informação confiável para análise ou produto."
---

# Arquitetura de pipeline de dados

Planeja coleta, limpeza, versionamento, acesso e validação de dados, com dicionário. Use quando dados de várias origens precisarem virar informação confiável para análise ou produto.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Origens, formatos, volume e frequência
- Quem consome os dados e para qual decisão
- Dados pessoais e restrições de acesso
- Infraestrutura disponível e orçamento

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Descreva o contrato de cada origem com campos, tipos, responsável e aviso de mudança.
2. Separe a cópia bruta das camadas tratadas, para permitir reprocessar sem coletar de novo.
3. Especifique transformações, remoção de duplicatas e tratamento de registros atrasados ou inválidos.
4. Crie validações de completude, unicidade, faixa e atualidade, com a reação quando falharem.
5. Defina versionamento, retenção, permissões e o dicionário de dados.

## O que entregar

Mapa do pipeline, regras de validação e dicionário de dados.

## Conferência antes de entregar

- [ ] Rodar o mesmo lote duas vezes não duplica registros.
- [ ] Cada campo final tem origem e significado rastreáveis.
- [ ] Dados pessoais têm finalidade e acesso restrito declarados.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
