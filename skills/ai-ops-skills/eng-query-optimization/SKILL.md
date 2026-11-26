---
name: eng-query-optimization
description: "Diagnostica consultas lentas e melhora o desempenho mantendo os mesmos resultados, com medição antes e depois. Use quando uma consulta ou tela estiver demorando por causa do banco."
---

# Otimização de consultas

Diagnostica consultas lentas e melhora o desempenho mantendo os mesmos resultados, com medição antes e depois. Use quando uma consulta ou tela estiver demorando por causa do banco.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Texto da consulta e frequência de execução
- Esquema, índices existentes e tamanho das tabelas
- Plano de execução, se for possível obtê-lo
- Tempo atual e meta desejada

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Registre a medição de partida com parâmetros representativos e guarde o resultado para comparação.
2. Leia o plano de execução em busca de varreduras desnecessárias, junções custosas, ordenações e estimativas distantes do real.
3. Corrija primeiro a própria consulta, como colunas sobrando, funções sobre campos indexados e chamadas repetidas em laço.
4. Proponha índices alinhados aos filtros, junções e ordenação, informando o custo extra em escrita e espaço.
5. Meça de novo nas mesmas condições e compare as linhas devolvidas com as originais.

## O que entregar

Plano de otimização com a consulta revisada, índices propostos e métricas comparadas.

## Conferência antes de entregar

- [ ] O resultado é equivalente, inclusive em nulos, duplicatas e ordem.
- [ ] Ganhos não medidos aparecem como estimativa.
- [ ] A criação de índices em produção está prevista sem bloqueio indevido e com aprovação.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
