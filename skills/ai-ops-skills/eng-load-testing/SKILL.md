---
name: eng-load-testing
description: "Planeja e interpreta testes de capacidade com aumento gradual de demanda em ambiente autorizado. Use quando for preciso saber quanto o sistema aguenta antes de um pico ou lançamento."
---

# Testes de carga

Planeja e interpreta testes de capacidade com aumento gradual de demanda em ambiente autorizado. Use quando for preciso saber quanto o sistema aguenta antes de um pico ou lançamento.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Ambiente autorizado e semelhança com produção
- Fluxos mais usados e demanda esperada
- Metas de tempo de resposta e taxa de erro
- Ferramenta de carga e monitoramento disponíveis

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Defina métricas, metas e critérios de interrupção antes de gerar tráfego.
2. Monte cenários com a proporção real de operações, dados de teste e serviços externos simulados.
3. Estabeleça uma linha de base e suba a carga em degraus, mantendo cada um tempo suficiente para estabilizar.
4. Cruze latência por percentil, erros e vazão com uso de processador, memória, banco e filas para localizar o gargalo.
5. Corrija ou recomende uma mudança por vez e repita o cenário.

## O que entregar

Plano de carga, limites observados, gargalos e interpretação dos resultados.

## Conferência antes de entregar

- [ ] Há autorização para o alvo e aviso a quem opera o ambiente.
- [ ] Diferenças em relação à produção acompanham as conclusões.
- [ ] Números apresentados vêm de execução real ou são ditos como estimativa.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
