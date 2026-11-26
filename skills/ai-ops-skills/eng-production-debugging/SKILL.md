---
name: eng-production-debugging
description: "Conduz a apuração de um problema em produção, estancando o impacto antes de buscar causa e prevenção. Use quando usuários reais estiverem sendo afetados por falha, lentidão ou dado errado."
---

# Investigação de incidente em produção

Conduz a apuração de um problema em produção, estancando o impacto antes de buscar causa e prevenção. Use quando usuários reais estiverem sendo afetados por falha, lentidão ou dado errado.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Sintoma, horário de início e quem foi afetado
- Logs, métricas e acessos que podem ser consultados
- Publicações e mudanças de configuração recentes
- Quem tem autoridade para agir no ambiente

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Dimensione o impacto e abra uma linha do tempo com horários e fontes.
2. Proponha a mitigação mais reversível, como voltar a versão ou desligar a função, e peça autorização antes de aplicar.
3. Investigue em modo de leitura, correlacionando erros com mudanças e preservando evidências.
4. Confirme a causa com dados, corrija e acompanhe os indicadores até a normalização.
5. Redija o pós-incidente sem culpar pessoas, com fatores contribuintes e ações preventivas com dono.

## O que entregar

Linha do tempo, correção ou mitigação e relatório pós-incidente.

## Conferência antes de entregar

- [ ] Nenhuma ação em produção foi feita sem permissão.
- [ ] Fatos e hipóteses estão separados no relatório.
- [ ] Cada ação preventiva tem responsável e forma de verificação.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
