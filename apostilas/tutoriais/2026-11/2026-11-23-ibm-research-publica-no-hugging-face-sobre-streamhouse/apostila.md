# IBM Research publica no Hugging Face sobre Streamhouse

_2026-11-23 · tutorial_

Esta apostila ensina a usar previsão e detecção de anomalias em dados em fluxo contínuo com os modelos de séries temporais da IBM e o Apache Flink na Confluent. Você vai entender o que é um Streamhouse, escolher entre TTM, PatchTST-FM, FlowState e TSPulse, escrever as consultas SQL de previsão e de anomalias, configurar o ambiente próprio e conferir o resultado contra dados que você conhece. Serve para quem trabalha com dados de máquinas, vendas, pagamentos ou operações. Ao final, você terá um caminho claro, com comandos prontos para copiar, e saberá o que conferir antes de confiar.

## O que você terá no fim

Você terá um caminho funcional para usar previsão e detecção de anomalias em dados em fluxo contínuo, com os modelos de séries temporais da IBM rodando junto do Apache Flink na plataforma da Confluent. Serve para quem já trabalha com dados de máquinas, vendas, pagamentos ou operações e quer enxergar o que vem pela frente sem montar tudo do zero.

Tudo parte de um post publicado pela IBM Research no Hugging Face em 18 de novembro de 2026, com vários autores. O post descreve o Streamhouse, os modelos e os casos de uso. A documentação oficial da Confluent e o repositório da IBM completam o caminho com as chamadas SQL e os notebooks.

Você não precisa ser especialista em aprendizado de máquina. Precisa de um navegador, um ambiente Flink na Confluent Cloud ou no Confluent Platform, noção básica de SQL e uma série de dados para testar, como temperatura, vendas ou telemetria.

Fonte: <https://huggingface.co/blog/ibm-research/time-series-powered-streamhouse>

## Como isso funciona

Toda empresa gera um registro contínuo de mudanças: uma leitura de máquina, um pagamento, uma venda, um pedido, uma mudança de estoque. Essas observações formam séries temporais e carregam sinais que ajudam a antecipar o que acontece em seguida. O problema é transformar esses sinais em decisões enquanto ainda importam: uma previsão entregue depois da produção, do desabastecimento ou da autorização de pagamento pode ser precisa, mas chega tarde demais.

A IBM e a Confluent levam modelos de fundação de séries temporais para perto dos dados enquanto eles fluem. Com o Apache Flink, equipes aplicam previsão, detecção de anomalias e inteligência semântica a dados em fluxo usando SQL, e os resultados ficam disponíveis para as aplicações e pessoas responsáveis pela próxima ação.

Modelos de fundação já mudaram o trabalho com texto, imagens e documentos. Os de séries temporais estendem a mesma ideia aos dados numéricos: aprendem padrões gerais a partir de dados históricos diversos e aplicam esse conhecimento a séries novas e a tarefas diferentes. Podem servir de ponto de partida sem exigir um modelo treinado para cada série.

No Streamhouse, o Flink transforma e enriquece os dados enquanto eles se movem, e as Lightning Tables dão acesso de baixa latência ao estado atual. Os modelos da IBM entram nesse fluxo para prever valores e apontar anomalias. Outros modelos, incluindo grandes modelos de linguagem, modelos estatísticos e sistemas de aprendizado de máquina especializados, podem contribuir onde fizer sentido.

A arquitetura ajuda em quatro frentes: escalar o desenvolvimento de modelos, porque um modelo pré-treinado serve de ponto de partida comum para muitas séries; atualizar previsões conforme os dados mudam, incorporando observações recentes; colocar os sinais mais perto da decisão, roteando previsões e anomalias para aplicações operacionais; e rodar modelos compactos em processadores comuns, na nuvem ou no servidor próprio, o que pode reduzir a necessidade de infraestrutura dedicada de GPU.

Fonte: <https://huggingface.co/blog/ibm-research/time-series-powered-streamhouse>

## Os modelos e quando usar cada um

Hoje os modelos rodam nativamente dentro da Confluent como funções embutidas, na nuvem e no servidor próprio. Na Confluent Cloud são totalmente gerenciados, sem nada para implantar. No servidor próprio, rodam na sua infraestrutura com o Confluent Platform para Apache Flink. Todos rodam em CPU, sem GPU.

O post apresenta uma família de modelos compactos da IBM. Um deles, o TTM, é usado para previsão, como a previsão de quatro horas sobre a telemetria de uma fábrica. O PatchTST-FM prevê o volume de negociação nos próximos trinta minutos, com faixa entre o percentil 10 e o 90. O TSPulse gera representações de janelas de dados para buscar padrões parecidos no histórico.

O portfólio tem quatro modelos complementares, todos em acesso antecipado, chamados pelas funções AI_FORECAST e AI_DETECT_ANOMALIES do Flink SQL. Troca-se o modelo com um parâmetro, sem redesenhar o pipeline. O TTM usa redes de mistura minúsculas ao longo do tempo e entre variáveis, e, com cerca de um milhão de parâmetros, cobre cem mil séries por noite em CPU. O PatchTST-FM lê a série em trechos, com cada variável em canal próprio, e devolve uma distribuição completa. O FlowState mantém um resumo contínuo atualizado a cada ponto e lê tanto telemetria de segundos quanto dados de mercado por hora. O TSPulse combina visões de tempo e frequência em um modelo multitarefa para anomalia, classificação, preenchimento de lacunas e busca por similaridade.

Não existe um modelo único melhor. A escolha depende de quantas séries você tem, se é uma variável ou muitas, do horizonte de previsão e se a tarefa é previsão ou detecção de anomalia. O post traz seis casos de uso para guiar essa escolha.

Fonte: <https://huggingface.co/blog/ibm-research/time-series-powered-streamhouse>

## Os números do post

Os números abaixo vêm dos dois posts da IBM Research, da documentação da Confluent e do repositório da IBM. Cada item indica o seu contexto.

- Mais de 50 milhões de downloads dos modelos de séries temporais da IBM, segundo o post principal.
- Mais de 44 milhões de downloads, segundo o segundo post.
- Ganhos de produtividade de 5 a 10 vezes, relatados pela IBM no segundo post.
- Cada ponto de acurácia vale milhões, segundo o mesmo post.
- O TTM, com cerca de um milhão de parâmetros, cobre cem mil séries por noite em CPU, segundo o segundo post.
- Previsão de 28 dias com faixa P10 a P90 no caso de planejamento de estoque.
- Previsão de quatro horas à frente no caso de produção.
- Previsão de volume de negociação para os próximos 30 minutos no caso de negociação.
- Python suportado no repositório granite-tsfm: 3.10, 3.11, 3.12 e 3.13.
- Ordem de exemplo na figura de negociação: 100.000 ações.
- Chamada de exemplo de detecção, com base na documentação da Confluent: mínimo de 15 pontos de histórico e nível de confiança de 95,0%.

Fonte: <https://huggingface.co/blog/ibm-research/time-series-powered-streamhouse>

## Casos de uso do post

Os cenários do post mostram como combinar modelos de séries temporais, dados em fluxo e lógica de aplicação. Eles são ilustrativos, não provas de resultado garantido.

A busca por similaridade ajuda a estreitar a investigação; por si só não estabelece a causa raiz de um problema. Essa aplicação exige pipeline de embeddings, índice e acesso ao contexto relevante.

- Produção: um modelo TTM lê telemetria e medições de qualidade e prevê a fração de produtos dentro da especificação quatro horas à frente, com faixa de valores. Se a previsão cai abaixo da meta, um processo de otimização avalia combinações de temperatura e fluxo de ar antes de qualquer mudança na linha.
- Anomalia em vendas: cada série de vendas recebe uma faixa esperada com base no histórico recente. Cada nova leitura é comparada com essa faixa no nível de confiança escolhido, sem treinar um modelo por produto e loja. Fora da faixa, o sinal se combina com estoque e dados da loja para sugerir a causa e o próximo passo.
- Planejamento de estoque: um modelo pré-treinado prevê demanda em todas as lojas e produtos, gerando previsão de 28 dias com faixa P10 a P90, atualizada conforme chegam novas vendas. O aplicativo de planejamento combina a previsão com estoque, prazo de entrega e nível de serviço para calcular o ponto de reposição; quando o estoque projetado cai abaixo desse ponto, um agente pode rascunhar um pedido de compra para revisão.
- Fraude em cartões: cada pagamento é comparado com a faixa de gasto esperada para aquele cartão, com base no histórico recente. Transações fora da faixa vão para os sistemas de fraude existentes como insumo adicional, ao lado de outras regras. O banco decide aprovar, pedir autenticação adicional ou investigar.
- Negociação: o PatchTST-FM prevê o volume de negociação para os próximos 30 minutos, com faixa P10 a P90. O algoritmo de execução usa essa previsão para distribuir a ordem dentro do limite de participação definido pela mesa. Se a atividade mudar, o algoritmo pode pausar e replanejar.
- Busca por padrões parecidos: o TSPulse produz representações de janelas de séries temporais que permitem busca por similaridade. Um engenheiro pode procurar formas como pico e recuperação, subida gradual ou mudança de nível, e inspecionar registros de manutenção e condições de operação associados.

Fonte: <https://huggingface.co/blog/ibm-research/time-series-powered-streamhouse>

## Antes de começar

Confira os requisitos antes de abrir qualquer documento. Sem eles, os passos não rodam.

- Navegador e conexão com a internet para abrir o post e a documentação.
- Ambiente Flink na Confluent Cloud, totalmente gerenciado, ou o Confluent Platform para Apache Flink instalado no seu servidor. Os modelos rodam em processador comum, sem placa de vídeo, nos dois casos.
- Noção básica de SQL, porque as chamadas de previsão e de anomalia são escritas em SQL do Flink.
- Uma série de dados para testar, como temperatura, vendas, telemetria de máquina ou pagamentos.
- Se for usar o Confluent Platform no servidor próprio, acesso à página de configuração das funções de IA e permissão para subir servidores e registrar funções.

Fonte: <https://huggingface.co/blog/ibm-research/time-series-powered-streamhouse>

## Passo a passo

Siga na ordem. Cada passo diz a ação e o resultado esperado; se o resultado não aparecer, use a dica de erro antes de seguir.

1. Abra o post oficial da IBM Research no Hugging Face, em https://huggingface.co/blog/ibm-research/time-series-powered-streamhouse. Resultado esperado: a página do artigo com título sobre modelos de séries temporais no Streamhouse, nomes dos autores e data de publicação em novembro de 2026. Se a página não abrir, confira se o endereço foi digitado por inteiro, sem espaços.
2. Role até a seção sobre o Streamhouse e leia o primeiro bloco. Resultado esperado: você consegue explicar em uma frase onde o modelo fica no caminho do dado — o Flink transforma os dados em movimento e os modelos da IBM entram para prever e detectar anomalias. Se o texto parecer denso, releia só o primeiro bloco e deixe os casos de uso para depois.
3. Compare TTM, PatchTST-FM e TSPulse na seção de casos de uso e anote o que combina com o seu problema. Resultado esperado: um nome de modelo anotado ao lado do seu caso — previsão com TTM ou PatchTST-FM, busca de padrões parecidos com TSPulse. Se nenhum parecer servir, comece pelo caso de uso mais próximo do seu e compare com os outros.
4. Abra a documentação da função de previsão na Confluent Cloud, em https://docs.confluent.io/cloud/current/ai/builtin-functions/forecast.html. Resultado esperado: a página da função AI_FORECAST, com o que ela recebe (valor, horário e configuração opcional) e o que devolve (média e faixas q10, q50 e q90), mais o aviso de acesso antecipado. Leia as entradas antes de seguir.
5. Se você usa o Confluent Platform no seu próprio ambiente, abra a página de configuração das funções de IA, em https://docs.confluent.io/cp-flink/current/jobs/sql-statements/ai/set-up-ai-functions.html, e prepare o ambiente: suba um servidor por modelo, registre as duas funções com CREATE FUNCTION e aponte o endereço de cada servidor nas configurações do ambiente. Se você usa só a nuvem gerenciada, pule este passo.
6. Escreva a consulta de previsão no SQL do Flink usando a chamada da documentação, trocando os nomes das colunas pelos da sua tabela. Resultado esperado: novas linhas com o valor previsto — média e faixas q10, q50 e q90 para cada horário futuro. Se aparecer erro de função desconhecida, confirme se as funções de IA estão habilitadas e se o nome foi digitado como na consulta de exemplo.
7. Escreva a consulta de detecção de anomalias no SQL do Flink usando a chamada da documentação. Resultado esperado: cada leitura com o campo is_anomaly (verdadeiro ou falso) e os limites inferior e superior da faixa esperada. Se tudo ou nada for marcado, revise a série usada e o nível de confiança.
8. Abra o repositório da IBM com código e notebooks, em https://github.com/ibm-granite/granite-tsfm, e entre na pasta notebooks. Resultado esperado: o repositório granite-tsfm, com notebooks de introdução ao TTM e um exemplo com o PatchTST-FM. Guarde a página nos favoritos.

Fonte: <https://huggingface.co/blog/ibm-research/time-series-powered-streamhouse>

## Consulta de previsão (AI_FORECAST)

Cole no SQL do Flink. Troque cpu_percent e event_time pelos nomes das colunas da sua tabela. O parâmetro horizon define quantos passos à frente prever.

```
AI_FORECAST(cpu_percent, event_time, JSON_OBJECT('model' VALUE 'ttm', 'horizon' VALUE 5)) OVER (ORDER BY event_time RANGE BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)
```

Fonte: <https://docs.confluent.io/cloud/current/ai/builtin-functions/forecast.html>

## Consulta de anomalias (AI_DETECT_ANOMALIES)

Cole no SQL do Flink. Troque temperature e reading_time pelos nomes das colunas da sua tabela. minContextSize define o mínimo de pontos de histórico e confidencePercentage define o nível de confiança da faixa.

```
AI_DETECT_ANOMALIES(temperature, reading_time, JSON_OBJECT('model' VALUE 'ttm', 'minContextSize' VALUE 15, 'confidencePercentage' VALUE 95.0)) OVER (ORDER BY reading_time RANGE BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW)
```

Fonte: <https://docs.confluent.io/cloud/current/ai/builtin-functions/detect-anomalies.html>

## Exemplo completo

Caso concreto: planejamento de estoque. Um modelo pré-treinado prevê demanda em todas as lojas e produtos, gerando uma previsão de 28 dias com faixa P10 a P90, atualizada conforme chegam novas vendas. O aplicativo de planejamento combina essa previsão com estoque, prazo de entrega e nível de serviço escolhido para calcular o ponto de reposição; quando o estoque projetado cai abaixo desse ponto, um agente pode rascunhar um pedido de compra para revisão.

A chamada abaixo, tirada do segundo post, mostra a forma geral com outro tipo de dado, leituras de medidores. Troque load_kw, event_time e meter_readings pelos nomes das suas colunas e da sua tabela e ajuste o modelo e o horizonte.

```
SELECT AI_FORECAST( load_kw, event_time, JSON_OBJECT ( 'model' VALUE 'ttm' , 'horizon' VALUE 12 ) ) OVER ( ORDER BY event_time RANGE BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW ) AS forecast FROM meter_readings;
```

Fonte: <https://huggingface.co/blog/ibm-research/real-time-intelligence>

## Configurar as funções de IA no servidor próprio

Só para quem usa o Confluent Platform no próprio ambiente. Na nuvem gerenciada nada disso é necessário: a Confluent cuida do serviço dos modelos.

No servidor próprio, o ambiente precisa ser preparado antes de qualquer consulta: sobe-se um servidor para cada modelo, registram-se as duas funções e informa-se ao ambiente o endereço de cada servidor.

- Suba um servidor por modelo.
- Registre as duas funções com CREATE FUNCTION.
- Aponte o endereço de cada servidor nas configurações do ambiente.
- Confirme que as funções de IA estão habilitadas antes de rodar as consultas.
- Siga a ordem em que as etapas aparecem na página e não adapte nada por conta própria.

Fonte: <https://docs.confluent.io/cp-flink/current/jobs/sql-statements/ai/set-up-ai-functions.html>

## Notebooks e código da IBM

O repositório granite-tsfm é o ponto de partida para quem quer ir além da leitura e mexer nos modelos de séries temporais da família Granite.

Na pasta notebooks há um tutorial de introdução ao TTM e um exemplo com o PatchTST-FM. O repositório também oferece demos, issues e uma wiki.

- Python suportado: 3.10, 3.11, 3.12 e 3.13.
- Clone com git clone "https://github.com/ibm-granite/granite-tsfm.git" e entre na pasta.
- Instale as dependências dos notebooks com pip install ".[notebooks]".
- Instale as demos com pip install ".[demos]".
- Notebooks disponíveis: introdução ao PatchTSMixer, transfer learning com PatchTSMixer e PatchTST, introdução ao TTM, benchmarking do TTM, FlowState e PatchTST-FM.
- Há um tutorial do TTM no Google Colab.

```
git clone "https://github.com/ibm-granite/granite-tsfm.git"
cd granite-tsfm
```

Fonte: <https://github.com/ibm-granite/granite-tsfm>

## Teste de pronto

Rode sobre um período em que você já sabe o que aconteceu e compare a saída com o que conhece.

- [ ] Na previsão: o valor real cai dentro da faixa P10 a P90.
- [ ] Na detecção: o evento que você já sabia ser estranho aparece marcado como anomalia.
- [ ] Se o valor real vive fora da faixa, revise a série usada e a escolha do modelo.
- [ ] Se tudo ou nada for marcado como anomalia, confira a série passada e o nível de confiança escolhido.
- [ ] Lembre o aviso do post sobre busca por similaridade: padrão parecido não prova a causa de um problema.

Fonte: <https://huggingface.co/blog/ibm-research/time-series-powered-streamhouse>

## Erros comuns e cuidados

O recurso está em acesso antecipado na Confluent Cloud. Vale para avaliação e testes. Confirme as condições antes de usar em produção.

Os modelos rodam em CPU, sem GPU, tanto na nuvem quanto no servidor próprio. Isso simplifica a implantação, mas confira a documentação para limites de escala.

- Acesso antecipado: confirme o status do recurso na documentação antes de depender dele.
- Disponível em acesso antecipado na Confluent Cloud na AWS; o Confluent Platform segue para ambientes próprios e híbridos.
- Previsão e detecção são stateful: o próximo valor só faz sentido contra o histórico recente, e a anomalia só existe contra um senso corrente do normal. O Flink gerencia esse estado por série, com tolerância a falhas.
- Similaridade ajuda a estreitar a investigação; não estabelece causa raiz por si só.
- Os cenários do post são ilustrativos: mostram como as organizações poderiam combinar modelos, dados em fluxo e lógica de aplicação.
- Os modelos foram rodados pela IBM em seus próprios produtos e operações antes de serem oferecidos, e com parceiros de design em cimento, aço, celulose e papel, alimentos e telecomunicações. Isso é evidência de uso, não garantia de resultado no seu caso.
- Não adapte por conta própria etapas que você não reconhece na página de configuração; siga a ordem em que aparecem.

Fonte: <https://huggingface.co/blog/ibm-research/time-series-powered-streamhouse>

## Glossário

- Série temporal: sequência de observações numéricas coletadas ao longo do tempo, como leituras de máquina, vendas ou pagamentos.
- Modelo de fundação de séries temporais (TSFM): modelo pré-treinado em padrões gerais de dados históricos diversos, que se aplica a séries novas sem treino específico para cada uma.
- Streamhouse: arquitetura que captura, processa, governa e serve contexto de negócio atual de forma contínua.
- Apache Flink: motor de processamento de dados em fluxo que transforma e enriquece dados enquanto eles se movem.
- Lightning Tables: acesso de baixa latência ao estado atual dos dados no Streamhouse.
- Confluent Cloud: plataforma gerenciada de streaming de dados da Confluent.
- Confluent Platform: versão para instalação no servidor próprio ou ambiente híbrido.
- AI_FORECAST: função do Flink que pede uma previsão, recebendo valor, horário e configuração opcional, e devolvendo média e faixas q10, q50 e q90.
- AI_DETECT_ANOMALIES: função do Flink que compara cada leitura com a faixa esperada e devolve is_anomaly e os limites inferior e superior.
- Faixa P10 a P90: intervalo entre o percentil 10 e o percentil 90 da distribuição prevista.
- Percentil: valor abaixo do qual cai determinada fração das observações.
- Horizonte (horizon): quantos passos à frente a previsão deve ir.
- minContextSize: mínimo de pontos de histórico exigido para a detecção de anomalias.
- confidencePercentage: nível de confiança da faixa esperada na detecção de anomalias.
- TTM (TinyTimeMixer): modelo compacto da IBM para previsão, que usa redes de mistura minúsculas.
- PatchTST-FM: modelo que lê a série em trechos e devolve uma distribuição completa de previsão.
- FlowState: modelo que mantém um resumo contínuo atualizado a cada ponto.
- TSPulse: modelo multitarefa para anomalia, classificação, preenchimento de lacunas e similaridade.
- SCADA: sistema de supervisão e aquisição de dados em plantas industriais.
- Similaridade (busca por padrões parecidos): comparação de formas de séries temporais para encontrar casos históricos semelhantes.
- CPU: processador comum, sem necessidade de placa de vídeo.
- Acesso antecipado: recurso disponível para avaliação e testes, com condições específicas.
- Notebook: arquivo interativo com código e explicações, usado para testar modelos.
- Repositório: pasta de código versionada, no caso o granite-tsfm no GitHub.
- Granite: família de modelos da IBM, incluindo os de séries temporais.

## Plano de 7 dias

- Dia 1: abrir e ler o post da IBM Research no Hugging Face e anotar os casos de uso mais próximos do seu problema.
- Dia 2: entender o papel do Streamhouse e escrever em uma frase onde o modelo entra no caminho do dado.
- Dia 3: comparar TTM, PatchTST-FM e TSPulse e escolher um modelo para o seu caso.
- Dia 4: abrir a documentação da função AI_FORECAST e ler as entradas e saídas.
- Dia 5: se usar o Confluent Platform no servidor próprio, abrir a página de configuração das funções de IA e preparar o ambiente; se usar só a nuvem, pular para o dia 6.
- Dia 6: escrever e rodar a consulta de previsão e a de anomalias no SQL do Flink.
- Dia 7: conferir o resultado contra um período que você conhece e abrir o repositório granite-tsfm para ver os notebooks.

## Para onde ir depois

- Ler o post completo da IBM Research: https://huggingface.co/blog/ibm-research/time-series-powered-streamhouse
- Abrir a documentação da função AI_FORECAST: https://docs.confluent.io/cloud/current/ai/builtin-functions/forecast.html
- Abrir a documentação da função AI_DETECT_ANOMALIES: https://docs.confluent.io/cloud/current/ai/builtin-functions/detect-anomalies.html
- Se usar servidor próprio, abrir a configuração das funções de IA: https://docs.confluent.io/cp-flink/current/jobs/sql-statements/ai/set-up-ai-functions.html
- Explorar o repositório granite-tsfm e seus notebooks: https://github.com/ibm-granite/granite-tsfm
- Verificar o programa de acesso antecipado às funções de Flink da Confluent: https://events.confluent.io/early-access-flink-features
- Ler o segundo post, 'Real-Time Intelligence with IBM Time Series Models on Confluent', para aprofundar a economia e o portfólio: https://huggingface.co/blog/ibm-research/real-time-intelligence
- Testar com uma série real sua, trocando os nomes das colunas nas consultas e conferindo o resultado contra o que você conhece.

## Além do vídeo

- Segundo o segundo post da IBM Research, as margens de segurança, o estoque extra e a folga de capacidade são o custo, pago a cada ciclo, de decisões que ninguém conseguia prever.
- O mesmo post dá o exemplo de uma linha de temperagem de chocolate: o modelo prevê a produção ao longo do turno da noite, compara a rodada do dia com o comportamento normal da linha em chocolate amargo e busca o caso mais parecido no histórico da fábrica.
- Quem roda em infraestrutura própria pode usar os pesos abertos disponíveis no Hugging Face Hub, em CPU. Os modelos de séries temporais da família Granite estão reunidos em uma coleção em https://huggingface.co/collections/ibm-granite/granite-time-series-models.
- A inferência nativa na Confluent Cloud, segundo o segundo post, dispensa servir os modelos em infraestrutura dedicada, mantém os dados dentro da plataforma e segue os mesmos esquemas, linhagem e controles de acesso.
- O repositório granite-tsfm avisa que o código foi publicado pela IBM como projeto de código aberto, sem obrigação de suporte ou atualização, e que não será mantido daqui em diante.
