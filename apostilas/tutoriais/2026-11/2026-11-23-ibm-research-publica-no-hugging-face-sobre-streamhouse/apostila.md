# IBM Research publica no Hugging Face sobre Streamhouse

_2026-11-23 · tutorial_

A IBM Research publicou no Hugging Face um post sobre modelos de séries temporais no Streamhouse. Ele mostra como rodar previsão e detecção de anomalias em dados em fluxo contínuo, com modelos da IBM no Apache Flink da Confluent. Esta apostila reúne o caminho do vídeo: o post, a escolha do modelo, a documentação, as duas consultas SQL e os notebooks de exemplo.

## O que você terá no fim

Ao final, você terá uma consulta de previsão e uma de detecção de anomalias em SQL no Flink, rodando sobre uma série de dados sua. Os modelos rodam em processador comum, sem placa de vídeo, tanto na nuvem gerenciada quanto no Confluent Platform. Fonte: https://huggingface.co/blog/ibm-research/time-series-powered-streamhouse

- Navegador e conexão com a internet.
- Flink na Confluent Cloud ou no Confluent Platform.
- Noção básica de SQL.
- Uma série de dados para testar, como temperatura ou vendas.

Fonte: <https://huggingface.co/blog/ibm-research/time-series-powered-streamhouse>

## Passo a passo

Siga os passos na ordem. As consultas SQL ficam em seções próprias. O post é a base de todo o caminho, e a documentação da função de previsão é a referência oficial.

1. leia o post e entenda o Streamhouse. O post descreve o Streamhouse, os modelos e os casos de uso. A Confluent usa o Apache Flink para transformar e enriquecer dados enquanto eles se movem. Resultado esperado: você entende onde os modelos entram no fluxo.
2. escolha o modelo do seu caso. Anote o nome do modelo ao lado do seu caso de uso: TTM para previsão, PatchTST-FM para previsão do volume de negociação com faixa entre o percentil 10 e o 90, e TSPulse para buscar padrões parecidos no histórico. Resultado esperado: o modelo do seu caso está anotado.
3. leia a documentação na Confluent Cloud. A página da função de previsão é a referência oficial de como pedir uma previsão no Flink. A função recebe o valor, o horário e uma configuração opcional, e devolve a média e as faixas q10, q50 e q90. Resultado esperado: você sabe os parâmetros da função.
4. prepare o Confluent Platform, só se usar servidor próprio. Suba um servidor por modelo, registre as duas funções com CREATE FUNCTION e aponte o endereço de cada servidor nas configurações do ambiente. Quem usa a nuvem gerenciada pode pular. Guia: https://docs.confluent.io/cp-flink/current/jobs/sql-statements/ai/set-up-ai-functions.html. Resultado esperado: as funções de IA estão registradas.
5. rode a consulta de previsão. Troque os nomes das colunas pelos da sua tabela. Resultado esperado: a saída traz novas linhas com o valor previsto, média e faixas q10, q50 e q90 para cada horário futuro.
6. rode a consulta de anomalias. Cada leitura é comparada com a faixa esperada. Resultado esperado: cada leitura vem com o campo is_anomaly e com os limites inferior e superior.

Fonte: <https://docs.confluent.io/cloud/current/ai/builtin-functions/forecast.html>

## Consulta de previsão

No SQL do Flink, a chamada recebe a coluna do valor, a coluna do horário e uma configuração com o modelo e o horizonte (quantos passos à frente prever). Troque os nomes das colunas pelos da sua tabela. Se aparecer erro de função desconhecida, confirme se as funções de IA estão habilitadas e se o nome está igual ao da documentação. Fonte: https://docs.confluent.io/cloud/current/ai/builtin-functions/forecast.html

```
AI_FORECAST(cpu_percent, event_time, JSON_OBJECT('model' VALUE 'ttm', 'horizon' VALUE 5)) OVER (ORDER BY event_time RANGE BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)
```

Fonte: <https://docs.confluent.io/cloud/current/ai/builtin-functions/forecast.html>

## Consulta de anomalias

Em vez de um limite fixo, cada leitura é comparada com a faixa esperada. A configuração escolhe o modelo, o mínimo de pontos de histórico e o nível de confiança. Se tudo ou nada for marcado, revise a série e o nível de confiança. Fonte: https://docs.confluent.io/cloud/current/ai/builtin-functions/detect-anomalies.html

```
AI_DETECT_ANOMALIES(temperature, reading_time, JSON_OBJECT('model' VALUE 'ttm', 'minContextSize' VALUE 15, 'confidencePercentage' VALUE 95.0)) OVER (ORDER BY reading_time RANGE BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)
```

Fonte: <https://docs.confluent.io/cloud/current/ai/builtin-functions/detect-anomalies.html>

## Teste de pronto

Como saber que funcionou. Cada item é verificável.

- [ ] A consulta de previsão devolve linhas com média e faixas q10, q50 e q90 para horários futuros.
- [ ] A consulta de anomalias devolve o campo is_anomaly e os limites inferior e superior em cada leitura.
- [ ] Se tudo ou nada aparecer como anomalia, a série e o nível de confiança foram revisados.

Fonte: <https://huggingface.co/blog/ibm-research/time-series-powered-streamhouse>

## Cuidados e notebooks

O recurso de previsão está em acesso antecipado, então serve para avaliação e testes. Notebooks de exemplo: o repositório granite-tsfm reúne código e notebooks dos modelos Granite de séries temporais. Na pasta notebooks há um tutorial de introdução ao TTM e um exemplo com o PatchTST-FM. Fonte: https://github.com/ibm-granite/granite-tsfm

Link para pedir acesso antecipado aos recursos de Flink da Confluent: https://events.confluent.io/early-access-flink-features. Outro post da IBM Research no Hugging Face: https://huggingface.co/blog/ibm-research/real-time-intelligence

Fonte: <https://github.com/ibm-granite/granite-tsfm>
