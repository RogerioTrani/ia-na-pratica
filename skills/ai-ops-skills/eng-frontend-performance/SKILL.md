---
name: eng-frontend-performance
description: "Investiga lentidão em páginas e aplicações e prioriza correções em carregamento, imagens, fontes e scripts. Use quando a interface demorar a aparecer ou a responder."
---

# Desempenho do frontend

Investiga lentidão em páginas e aplicações e prioriza correções em carregamento, imagens, fontes e scripts. Use quando a interface demorar a aparecer ou a responder.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Páginas ou telas lentas e relato do problema
- Dispositivos e conexões do público
- Stack, processo de build e hospedagem
- Medições já coletadas

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Meça as telas prioritárias em condições fixas de aparelho e rede, separando tempo para exibir, para interagir e estabilidade visual.
2. Examine a cascata de requisições para achar imagens pesadas, fontes que bloqueiam texto, scripts grandes e chamadas em sequência.
3. Entregue primeiro o necessário para a primeira tela e adie, divida ou remova o restante.
4. Investigue renderizações repetidas e tarefas longas que travam cliques e digitação.
5. Ordene as correções por ganho esperado e esforço e repita a medição após cada grupo.

## O que entregar

Backlog de desempenho priorizado, com medição de partida e critério de melhoria para cada item.

## Conferência antes de entregar

- [ ] Antes e depois são comparados nas mesmas condições.
- [ ] As mudanças não quebram funcionalidade, layout nem acessibilidade.
- [ ] Ganhos previstos e ganhos medidos estão diferenciados.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
