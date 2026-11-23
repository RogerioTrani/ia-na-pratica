# IBM Research publica no Hugging Face sobre Streamhouse

_2026-11-23 · tutorial_

A IBM Research publicou no Hugging Face um post sobre modelos de séries temporais no Streamhouse. Ele mostra como rodar previsão e detecção de anomalias em dados em fluxo contínuo, com modelos da IBM no Apache Flink da Confluent. Esta apostila reúne o caminho do vídeo: o post, a escolha do modelo, a documentação, as duas consultas SQL e os notebooks de exemplo.

## O que você precisa

Os modelos rodam em processador comum, sem placa de vídeo, tanto na nuvem gerenciada quanto no Confluent Platform.

- Navegador e conexão com a internet
- Flink na Confluent Cloud ou no Confluent Platform
- Noção básica de SQL
- Uma série de dados para testar, como temperatura ou vendas

Fonte: <https://huggingface.co/blog/ibm-research/time-series-powered-streamhouse>

## O post e o Streamhouse

O post "Time-Series Models in the Streamhouse: A New Frontier and Use Cases" é a base de todo o caminho. Ele descreve o Streamhouse, os modelos e os casos de uso.

A Confluent usa o Apache Flink para transformar e enriquecer dados enquanto eles se movem. Os modelos da IBM entram nesse fluxo para prever valores e apontar anomalias.

Fonte: <https://huggingface.co/blog/ibm-research/time-series-powered-streamhouse>

## Escolha o modelo do seu caso

O post apresenta uma família de modelos compactos da IBM. Anote o nome do modelo ao lado do seu caso de uso.

- TTM: previsão, como a de quatro horas sobre a telemetria de uma fábrica
- PatchTST-FM: previsão do volume de negociação nos próximos trinta minutos, com faixa entre o percentil 10 e o 90
- TSPulse: gera representações de janelas de dados para buscar padrões parecidos no histórico

Fonte: <https://huggingface.co/blog/ibm-research/time-series-powered-streamhouse>

## Documentação na Confluent Cloud

A página da função de previsão é a referência oficial de como pedir uma previsão no Flink. O recurso está em acesso antecipado, então serve para avaliação e testes.

A função recebe o valor, o horário e uma configuração opcional. Devolve a média e as faixas q10, q50 e q90.

Fonte: <https://docs.confluent.io/cloud/current/ai/builtin-functions/forecast.html>

## Preparar o Confluent Platform (servidor próprio)

Este passo é só para quem usa o Confluent Platform. Quem usa a nuvem gerenciada pode pular.

- Subir um servidor por modelo
- Registrar as duas funções com CREATE FUNCTION
- Apontar o endereço de cada servidor nas configurações do ambiente

Fonte: <https://docs.confluent.io/cp-flink/current/jobs/sql-statements/ai/set-up-ai-functions.html>

## Consulta de previsão

No SQL do Flink, a chamada recebe a coluna do valor, a coluna do horário e uma configuração com o modelo e o horizonte (quantos passos à frente prever). Troque os nomes das colunas pelos da sua tabela.

A saída traz novas linhas com o valor previsto: média e faixas q10, q50 e q90 para cada horário futuro. Se aparecer erro de função desconhecida, confirme se as funções de IA estão habilitadas e se o nome está igual ao da documentação.

```
AI_FORECAST(cpu_percent, event_time, JSON_OBJECT('model' VALUE 'ttm', 'horizon' VALUE 5)) OVER (ORDER BY event_time RANGE BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)
```

Fonte: <https://docs.confluent.io/cloud/current/ai/builtin-functions/forecast.html>

## Consulta de anomalias

Em vez de um limite fixo, cada leitura é comparada com a faixa esperada. A configuração escolhe o modelo, o mínimo de pontos de histórico e o nível de confiança.

Cada leitura vem com o campo is_anomaly e com os limites inferior e superior. Se tudo ou nada for marcado, revise a série e o nível de confiança.

```
AI_DETECT_ANOMALIES(temperature, reading_time, JSON_OBJECT('model' VALUE 'ttm', 'minContextSize' VALUE 15, 'confidencePercentage' VALUE 95.0)) OVER (ORDER BY reading_time RANGE BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)
```

Fonte: <https://docs.confluent.io/cloud/current/ai/builtin-functions/detect-anomalies.html>

## Notebooks de exemplo

O repositório granite-tsfm reúne código e notebooks dos modelos Granite de séries temporais. Na pasta notebooks há um tutorial de introdução ao TTM e um exemplo com o PatchTST-FM.

Fonte: <https://github.com/ibm-granite/granite-tsfm>

## Além do vídeo

- Link para pedir acesso antecipado aos recursos de Flink da Confluent: https://events.confluent.io/early-access-flink-features
- Outro post da IBM Research no Hugging Face, "Real-Time Intelligence with IBM Time Series Models on Confluent": https://huggingface.co/blog/ibm-research/real-time-intelligence
