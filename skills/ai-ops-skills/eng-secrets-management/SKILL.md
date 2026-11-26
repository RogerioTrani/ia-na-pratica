---
name: eng-secrets-management
description: "Localiza chaves e tokens expostos, move-os para armazenamento adequado e planeja a rotação. Use quando houver risco de credencial no código, em logs ou em configuração compartilhada."
---

# Gestão de segredos do projeto

Localiza chaves e tokens expostos, move-os para armazenamento adequado e planeja a rotação. Use quando houver risco de credencial no código, em logs ou em configuração compartilhada.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Repositório, scripts, pipelines e arquivos de ambiente
- Serviços que usam credenciais e quem as administra
- Cofre ou mecanismo de segredos disponível
- Suspeitas de vazamento já ocorridas

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Inventarie cada credencial por nome, uso, local, dono e permissões, sem copiar valores.
2. Verifique código, histórico de versões, logs, imagens e pacotes de publicação.
3. Substitua valores fixos por leitura do cofre ou de variáveis protegidas e mantenha no repositório só um exemplo vazio.
4. Trate como comprometido tudo que foi exposto, rotacionando com criação da nova chave, troca nos consumidores e revogação da antiga.
5. Acrescente bloqueios que impeçam novos segredos de entrar no versionamento e defina a periodicidade de revisão.

## O que entregar

Checklist de proteção, lista de mudanças no código e plano de rotação.

## Conferência antes de entregar

- [ ] Nenhum valor secreto aparece no relatório ou nos exemplos.
- [ ] Apagar do arquivo atual não é tratado como suficiente quando o segredo está no histórico.
- [ ] Revogações e reescrita de histórico aguardam aprovação.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
