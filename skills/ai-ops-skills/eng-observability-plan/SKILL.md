---
name: eng-observability-plan
description: "Define logs, métricas e alertas ligados às falhas e jornadas que importam, sem expor dados pessoais. Use quando o sistema falhar sem aviso ou for difícil descobrir o motivo."
---

# Plano de observabilidade

Define logs, métricas e alertas ligados às falhas e jornadas que importam, sem expor dados pessoais. Use quando o sistema falhar sem aviso ou for difícil descobrir o motivo.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Jornadas críticas e incidentes anteriores
- Ferramentas de log e monitoramento disponíveis
- Quem atende alertas e em que horários
- Dados que não podem ser registrados

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Para cada jornada importante, escreva o que pode dar errado e como o time ficaria sabendo.
2. Escolha métricas de volume, erro e duração e eventos estruturados com um identificador que ligue uma requisição entre serviços.
3. Liste os campos permitidos em cada evento e mascare ou exclua dados pessoais e segredos.
4. Crie alertas apenas para situações que pedem ação, com limite, janela, responsável e primeiro procedimento.
5. Provoque uma falha em ambiente de teste para comprovar que o sinal aparece e o alerta dispara.

## O que entregar

Plano de monitoramento com catálogo de eventos, métricas, alertas e responsáveis.

## Conferência antes de entregar

- [ ] Todo alerta diz quem age e o que fazer primeiro.
- [ ] Limites sem histórico estão marcados como iniciais, a calibrar.
- [ ] Nenhum evento carrega senha, token ou dado pessoal desnecessário.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
