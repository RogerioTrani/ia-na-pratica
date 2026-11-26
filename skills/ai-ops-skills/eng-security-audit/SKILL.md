---
name: eng-security-audit
description: "Examina um código autorizado em busca de falhas de permissão, validação de entrada e segredos, e prioriza correções. Use quando for preciso avaliar riscos antes de publicar ou após mudanças sensíveis."
---

# Auditoria defensiva de segurança

Examina um código autorizado em busca de falhas de permissão, validação de entrada e segredos, e prioriza correções. Use quando for preciso avaliar riscos antes de publicar ou após mudanças sensíveis.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Confirmação de que há autorização para analisar o sistema e o escopo
- Código, configuração e arquitetura
- Dados sensíveis e perfis de acesso
- Resultados de verificações anteriores

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Mapeie as portas de entrada, os limites de confiança e onde ficam os dados valiosos.
2. Confira em cada operação a autenticação e a autorização sobre o registro específico.
3. Siga os dados externos até consultas, comandos, arquivos, páginas e chamadas de rede, procurando falta de validação ou de codificação.
4. Procure segredos no código e no histórico, configurações permissivas e dependências com falhas conhecidas, sem executar exploração destrutiva.
5. Classifique cada achado por impacto e facilidade de abuso, com evidência, correção e forma de revalidar.

## O que entregar

Relatório de achados priorizados e plano de correção.

## Conferência antes de entregar

- [ ] Segredos encontrados são citados apenas por local e tipo, sem o valor.
- [ ] Suspeitas não confirmadas estão separadas de falhas comprovadas.
- [ ] O relatório declara o que ficou fora da análise.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
