# Muse Ember chega à Meta Model API com janela de 1M tokens

_2026-11-22 · noticia_

A Meta apresentou o Muse Ember, seu menor modelo e o mais eficiente da linha, para executar tarefas repetitivas de agentes em escala. Ele reúne janela de 1 milhão de tokens, saída de até 512 mil tokens, entrada multimodal e preços por token que variam conforme o tamanho do prompt. Nesta apostila, você vai entender onde ele faz sentido, como ler os testes e os preços e como começar no Muse Code ou na Meta Model API. Também vai ver os limites dos resultados publicados e a divisão sugerida com o Muse Wonder para os problemas mais difíceis.

## O fato

A Meta apresentou o Muse Ember como seu menor e mais eficiente modelo, voltado à execução de raciocínio complexo e ao trabalho que agentes repetem ao longo do dia. O anúncio destaca chamadas de ferramentas, subtarefas de código, roteamento, extração e leitura de documentos longos.

O modelo está disponível no Muse Code e na Meta Model API com o identificador muse-ember-1.0. Ele suporta a Responses API e tem janela de contexto de 1 milhão de tokens, com saída de até 512 mil tokens.

A proposta da Meta é usar um modelo pequeno e barato nas etapas de maior volume. Para os problemas mais difíceis, a recomendação é combinar o Ember com o Muse Wonder, que faz o planejamento.

Fonte: <https://research.meta.ai/blog/muse-ember>

## Por que isso importa: o custo dos muitos passos

Um agente de IA divide um objetivo em várias ações. Em vez de produzir uma resposta longa de uma vez, ele pode consultar registros, chamar ferramentas, extrair campos e atualizar sistemas. Cada etapa consome tokens, e a soma dessas pequenas etapas costuma responder por grande parte do uso do agente.

O Muse Ember foi desenhado para esse padrão de trabalho. A Meta cita fluxos de negócio de ponta a ponta, nos quais o agente consulta registros, chama ferramentas em sequência e atualiza informações entre aplicativos. Também destaca a leitura de arquivos, a execução de testes e as correções pontuais em código.

Isso muda a decisão de quem constrói um agente. Um modelo maior pode continuar responsável pelo planejamento, enquanto o Ember recebe as subtarefas repetitivas. A economia depende da quantidade de trabalho delegado e da faixa de preço aplicada a cada prompt.

Fonte: <https://research.meta.ai/blog/muse-ember>

## Janela de contexto e limite de saída

A janela de contexto é a quantidade de tokens que o modelo pode considerar em uma chamada. Ela inclui as instruções, o conteúdo fornecido e o histórico da conversa. Com 1 milhão de tokens de contexto, a Meta diz que o Ember pode receber uma base de código inteira ou um conjunto de documentos de uma vez.

Esse tamanho reduz a necessidade de dividir o conteúdo em pedaços antes da análise. O agente pode manter partes relacionadas do documento ou do projeto na mesma chamada, o que ajuda quando a resposta depende de informação espalhada por vários arquivos.

O limite de saída é outro número. O Ember pode gerar até 512 mil tokens de resposta, mas esse valor é um teto. A saída real depende da tarefa e é cobrada separadamente da entrada. A janela de 1 milhão de tokens também não define a faixa de preço: prompts acima de 200 mil tokens entram na tabela mais cara.

Fonte: <https://dev.meta.ai/docs/muse-ember>

## Preços por token: as duas faixas

O preço do Muse Ember é cobrado por milhão de tokens. Entrada e saída têm valores diferentes, e a entrada reaproveitada em cache tem uma tarifa própria. Tokens em cache são porções da entrada já processadas que podem ser reutilizadas, com cobrança menor.

A faixa depende do tamanho do prompt. Um prompt de até 200 mil tokens usa os valores da primeira faixa; acima disso, valem os valores da segunda. A conta de uma chamada depende da quantidade processada em cada categoria, não de um único número isolado.

- Até 200 mil tokens no prompt: US$ 0,10 por milhão de tokens de entrada.
- Até 200 mil tokens no prompt: US$ 0,004 por milhão de tokens de entrada em cache.
- Até 200 mil tokens no prompt: US$ 0,50 por milhão de tokens de saída.
- Acima de 200 mil tokens no prompt: US$ 0,30 por milhão de tokens de entrada.
- Acima de 200 mil tokens no prompt: US$ 0,012 por milhão de tokens de entrada em cache.
- Acima de 200 mil tokens no prompt: US$ 1,50 por milhão de tokens de saída.

Fonte: <https://dev.meta.ai/models/muse-ember>

## Os números: qualidade e custo por tarefa

O custo por tarefa do Artificial Analysis é uma estimativa formada a partir dos resultados brutos do teste e dos preços de lista. Ele não é o valor cobrado por uma chamada. No recorte exibido, os três modelos aparecem no esforço máximo de raciocínio, indicado como max.

A Meta resume a comparação dizendo que o Ember iguala a melhor pontuação do Claude Haiku 5.5 por cerca de um terço do custo e supera todas as configurações do GPT-6 Luna. Os valores exatos do recorte máximo aparecem abaixo. A tabela completa também registra outro ponto do Ember, com custo estimado de US$ 0,116 por tarefa e pontuação 33,9.

Os resultados do Artificial Analysis Intelligence Index v5 foram publicados em 9 de novembro de 2026. A Meta afirma que o Ember fica na fronteira de eficiência do ranking completo, com nenhum modelo pontuando mais por menos por tarefa. O anúncio arredonda o custo do Ember para cerca de US$ 0,14 por tarefa.

- Muse Ember, max: US$ 0,136 por tarefa e pontuação 35,8 no recorte do gráfico.
- GPT-6 Luna, max: US$ 0,152 por tarefa e pontuação 27,8.
- Claude Haiku 5.5, max: US$ 0,411 por tarefa e pontuação 36,2.

Fonte: <https://research.meta.ai/static/muse-ember-evaluation-report>

## Agentes e fluxos de negócio

Os testes de agentes avaliam mais do que responder a uma pergunta. Eles verificam se o modelo consegue conduzir uma tarefa com várias etapas e ferramentas até o fim. O AutomationBench-AA mede fluxos de negócio de ponta a ponta; o Agents' Last Exam reúne tarefas de agente; o Personal Superintelligence Index combina trabalhos pessoais e de conhecimento.

Os resultados destacados usam o esforço máximo. O AutomationBench-AA usa sucesso estrito na primeira tentativa, chamado de pass@1 estrito. O Agents' Last Exam é uma avaliação interna da Meta restrita ao subconjunto Linux. O Personal Superintelligence Index também é interno e reúne oito avaliações: Agents' Last Exam, AutomationBench, FocusBench, JobBench, OfficeQA Pro, GDP.pdf, GDP.xlsx e VBT.

Nos testes iniciais de parceiros, a Box relatou bom desempenho em precisão, velocidade e eficiência de tokens. A empresa descreveu o modelo como capaz de comparar contratos com um manual de negociação cláusula por cláusula e chegar à classificação de risco, além de selecionar candidatos a partir de um briefing detalhado e sinalizar os casos limítrofes como alternativas.

- AutomationBench-AA, max: Muse Ember com 37,8%, GPT-6 Luna com 20,2% e Claude Haiku 5.5 com 13,9%.
- Agents' Last Exam, max: Muse Ember com 61,6%, GPT-6 Luna com 57,1% e Claude Haiku 5.5 com 57,0%.
- Personal Superintelligence Index, max: Muse Ember com 46,8%, GPT-6 Luna com 37,0% e Claude Haiku 5.5 com 36,1%.

Fonte: <https://research.meta.ai/blog/muse-ember>

## Código: resultados por tipo de tarefa

Para código, o anúncio descreve subtarefas que um agente envia muitas vezes durante uma sessão: ler arquivos, executar testes e fazer correções pontuais. O Ember aparece bem em parte desses testes, mas os resultados variam conforme a avaliação.

O Terminal-Bench 4.0 usa o melhor harness publicado de cada modelo. Isso significa que as pontuações foram obtidas com estruturas de execução diferentes: mini-swe-agent para o Muse Ember, Claude Code para o Claude Haiku 5.5 e Codex para o GPT-6 Luna. A comparação mantém o interesse do teste, mas não isola apenas a capacidade do modelo.

Em testes iniciais de parceiros, a Cloudflare relatou que o Ember rodou até 30% mais rápido na cauda de latência do que o modelo comparável testado e lidou bem com investigações amplas em vários repositórios. A You.com informou que o modelo completou todas as tarefas de código do teste com a menor latência entre os modelos testados: p95 de 2,2 segundos, cerca de 4 a 13 vezes mais rápido que modelos de pesos abertos líderes, usando de 36% a 48% menos tokens de saída.

A Cline descreveu o Ember como adequado ao trabalho de subagente em código e análise de documentos. A Oracle relatou capacidade promissora em tarefas complexas de engenharia durante os testes iniciais. Esses relatos de parceiros têm escopo próprio e não substituem a leitura de cada benchmark.

- Terminal-Bench 4.0, max: Muse Ember com 40,9%, Claude Haiku 5.5 com 39,2% e GPT-6 Luna com 16,4%.
- Coding Agent Index-AA, max: Muse Ember com 46, Claude Haiku 5.5 com 37 e GPT-6 Luna com 31.
- FrontierCode 2.0-AA, max: Claude Haiku 5.5 com 34,9%, Muse Ember com 27,2% e GPT-6 Luna com 25,2%.

Fonte: <https://research.meta.ai/blog/muse-ember>

## Multimodal e uso de computador

O Muse Ember entende texto, imagem, áudio e vídeo de forma nativa. Segundo a Meta, o mesmo modelo pode ler capturas de tela, gráficos e documentos digitalizados, além de trabalhar com memorandos de voz, gravações de reuniões e vídeo, sem recorrer a um modelo separado.

A capacidade multimodal também aparece em testes de documentos longos, percepção visual e uso de computador. Cada avaliação mede uma parte diferente: leitura de documentos profissionais, identificação de detalhes visuais ou execução de ações em aplicativos de desktop.

Os resultados precisam ser lidos com o método de cada teste. O GDP.pdf-AA vem do Artificial Analysis. OSWorld 2.1 e PerceptionBench são avaliações internas da Meta; OSWorld usa pontuação parcial e PerceptionBench é executado com ferramentas.

- GDP.pdf-AA, max: Muse Ember e GPT-6 Luna com 22,8%; Claude Haiku 5.5 com 20,8%.
- OSWorld 2.1, max, com pontuação parcial: Muse Ember com 69,5%, Claude Haiku 5.5 com 68,9% e GPT-6 Luna com 50,5%.
- PerceptionBench com ferramentas, max: Muse Ember com 80,6%, Claude Haiku 5.5 com 78,6% e GPT-6 Luna com 62,8%.

Fonte: <https://research.meta.ai/blog/muse-ember>

## Segurança: o que foi avaliado

Antes do lançamento, a Meta avaliou o Muse Ember dentro do Meta Superintelligence Scaling Framework. O comunicado cita riscos químicos e biológicos, de cibersegurança e de perda de controle. A empresa informa que, nas categorias avaliadas, o modelo ficou abaixo dos limiares de alto risco do framework.

A Meta também diz que, embora seja um modelo pequeno, o Ember recebeu o mesmo treinamento central de segurança e os mesmos testes.

Outra parte da avaliação verificou como o modelo age em nome do usuário. Os critérios incluem respeitar a intenção do usuário, tratar informações sensíveis de forma adequada, resistir a instruções ocultas em páginas, documentos ou saídas de ferramentas e pedir intervenção humana antes de ações de alto impacto.

O resultado comunicado se refere às categorias e ao framework citados. Em um fluxo real, a revisão humana continua importante quando a ação pode afetar dados, sistemas ou decisões relevantes.

- Riscos químicos e biológicos: incluídos na avaliação de segurança.
- Riscos de cibersegurança: incluídos na avaliação de segurança.
- Risco de perda de controle: incluído na avaliação de segurança.

Fonte: <https://research.meta.ai/blog/muse-ember>

## Muse Code: instalação e escolha do modelo

O Muse Code oferece o muse-ember-1.0 no modo pré-pago e em todos os planos de assinatura. A instalação por linha de comando é indicada para macOS e Linux. No Windows, o comando exige um shell compatível, como WSL ou Git Bash.

O seletor de modelos da sessão define qual modelo trabalha naquela sessão. Os arquivos de perfil ou de subagentes do projeto permitem delegar apenas as subtarefas repetitivas ao Ember, enquanto modelos como muse-wonder-1.0 ou muse-spark-1.3 cuidam do planejamento.

1. No macOS ou Linux, execute o comando de instalação abaixo. O resultado esperado é ter o Muse Code disponível para abrir.
2. Abra o Muse Code e selecione muse-ember-1.0 no seletor de modelos da sessão. O resultado esperado é direcionar as tarefas daquela sessão ao Ember.
3. Para delegar só o trabalho repetitivo, configure o muse-ember-1.0 nos arquivos de perfil ou de subagentes do projeto. O resultado esperado é separar o volume de execução do planejamento feito por modelos maiores.

```
curl -fsSL https://dev.meta.ai/install.sh | bash
```

Fonte: <https://dev.meta.ai/products/muse-code/>

## Meta Model API: chave e primeira chamada com cURL

A Meta Model API usa o endereço base https://api.meta.ai/v1. O endpoint da Responses API para a chamada do exemplo é POST https://api.meta.ai/v1/responses. A autenticação usa o cabeçalho Authorization com Bearer e a chave guardada em MODEL_API_KEY.

O exemplo abaixo envia uma instrução para resumir um documento e especifica o modelo muse-ember-1.0. Ele pressupõe que a variável de ambiente MODEL_API_KEY já está definida no ambiente em que o comando será executado.

1. Acesse o painel dev.meta.ai, abra a aba API keys e escolha Create API key. Dê um nome à chave e copie-a no momento da criação, porque ela só aparece uma vez.
2. Configure a chave copiada na variável de ambiente MODEL_API_KEY. O resultado esperado é o comando encontrar a credencial em $MODEL_API_KEY.
3. Execute a chamada para POST https://api.meta.ai/v1/responses com o modelo muse-ember-1.0. O resultado esperado é receber pela Responses API a resposta ao texto enviado.

```
curl https://api.meta.ai/v1/responses \
  -H "Authorization: Bearer $MODEL_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "muse-ember-1.0",
    "input": "Resuma os pontos principais deste documento."
  }'
```

Fonte: <https://dev.meta.ai/docs/muse-ember>

## Meta Model API: chamada com Python

Para quem já trabalha com o SDK da OpenAI, há uma chamada equivalente em Python. O cliente aponta para o endereço base https://api.meta.ai/v1 e lê a chave da variável de ambiente MODEL_API_KEY.

A função responses.create envia o modelo muse-ember-1.0 e o texto de entrada. O exemplo pressupõe que a biblioteca openai está instalada e que a variável de ambiente já foi configurada.

```
import os
from openai import OpenAI

client = OpenAI(
    base_url="https://api.meta.ai/v1",
    api_key=os.environ["MODEL_API_KEY"],
)

resp = client.responses.create(
    model="muse-ember-1.0",
    input="Resuma os pontos principais deste documento.",
)
```

Fonte: <https://dev.meta.ai/docs/muse-ember>

## Muse Wonder, Muse Spark e onde cada modelo entra

Para os problemas mais difíceis, a Meta sugere uma divisão de trabalho: o Muse Wonder planeja e o Muse Ember executa o volume. O Ember foi o primeiro modelo treinado usando o Muse Wonder Full, segundo o anúncio.

No portfólio descrito pela Meta, o Muse Wonder cuida dos problemas mais difíceis, o Muse Spark atende fluxos de código e de agentes, e o Muse Ember trata das tarefas repetitivas de código e de agentes em escala. Muse Ember, Muse Spark e Muse Wonder estão disponíveis no Google Cloud e no Oracle Cloud.

A comparação com o Muse Spark 1.3 mostra a troca entre capacidade, custo por tarefa e preço por token. Os valores abaixo vêm do Artificial Analysis no esforço máximo.

- Artificial Analysis Intelligence Index, max: Muse Ember com 36 e Muse Spark 1.3 com 37.
- Custo por tarefa, max: cerca de US$ 0,14 para o Muse Ember e US$ 2,39 para o Muse Spark 1.3.
- Preço por milhão de tokens de entrada e saída: Muse Ember a US$ 0,10 e US$ 0,50; Muse Spark 1.3 a US$ 1,25 e US$ 4,25.

Fonte: <https://research.meta.ai/blog/muse-ember>

## O que muda para você

Exemplo: um agente precisa revisar um conjunto de contratos e comparar cláusulas com um manual de negociação. Em cada documento, ele pode extrair os pontos relevantes e indicar o risco geral. Esse trabalho reúne leitura longa, extração estruturada e várias etapas pequenas, justamente as atividades descritas para o Ember.

A Box relatou esse tipo de uso em teste inicial, incluindo a análise cláusula por cláusula e a classificação de risco. O Ember pode receber o volume de documentos e produzir as análises intermediárias. Se o problema exigir planejamento difícil, o Muse Wonder entra antes da execução.

A responsabilidade pela decisão permanece humana nas ações de alto impacto. O modelo ajuda a organizar e executar o trabalho repetitivo; a revisão define se a classificação ou a ação corresponde ao contexto real.

Fonte: <https://research.meta.ai/blog/muse-ember>

## O que fazer hoje

Escolha primeiro o caminho de uso. O Muse Code serve para trabalhar dentro da ferramenta; a Meta Model API serve para integrar o modelo em um programa ou fluxo próprio.

1. Escolha entre o Muse Code e a Meta Model API conforme a tarefa. O resultado esperado é definir onde a primeira execução acontecerá.
2. No Muse Code, instale a ferramenta e selecione muse-ember-1.0 no seletor da sessão. O resultado esperado é ter o Ember ativo para a tarefa escolhida.
3. Na Meta Model API, crie a chave em dev.meta.ai, guarde-a em MODEL_API_KEY e use o endpoint https://api.meta.ai/v1/responses. O resultado esperado é autenticar a chamada com o modelo correto.
4. Faça uma primeira tarefa de extração, roteamento ou leitura de documento. O resultado esperado é obter uma resposta que você consiga conferir contra o conteúdo enviado.
5. Confira o tamanho do prompt antes de executar. O resultado esperado é saber se a chamada usa a faixa de até 200 mil tokens ou a faixa acima desse limite.
6. Em um fluxo mais difícil, deixe o planejamento com o Muse Wonder e delegue o volume ao Muse Ember. O resultado esperado é separar a decisão complexa da execução repetitiva.

Fonte: <https://dev.meta.ai/docs/muse-ember>

## O que conferir

Os números do anúncio ajudam a escolher o modelo, desde que o teste e a configuração sejam mantidos. Resultados internos, avaliações externas e relatos iniciais de parceiros têm recortes diferentes.

- Preço: confira se o prompt tem até 200 mil tokens. Acima disso, valem US$ 0,30 de entrada, US$ 0,012 de cache e US$ 1,50 de saída por milhão.
- Custo por tarefa: os valores do Artificial Analysis são estimativas baseadas nos resultados do teste e nos preços de lista, não a fatura de uma chamada.
- Configuração: os resultados destacados usam o esforço máximo. Comparar um ponto intermediário com o resultado max muda a conclusão.
- Harness: no Terminal-Bench 4.0, cada modelo usa seu melhor harness publicado, com estruturas de execução diferentes.
- Método: o AutomationBench-AA usa pass@1 estrito, e o OSWorld 2.1 usa pontuação parcial.
- Resultados internos: Agents' Last Exam, Personal Superintelligence Index, OSWorld 2.1 e PerceptionBench são avaliações internas da Meta, cada uma com seu recorte.
- Segurança: a Meta informa que o Ember ficou abaixo dos limiares de alto risco nas categorias avaliadas. Ações de alto impacto ainda pedem intervenção humana.
- Chave de API: copie a chave quando ela for criada, porque só aparece uma vez, e guarde-a em MODEL_API_KEY.

Fonte: <https://research.meta.ai/blog/muse-ember>

## Glossário

- Token: unidade em que o modelo processa e cobra texto; uma palavra pode corresponder a mais de um token.
- Janela de contexto: quantidade máxima de tokens que o modelo considera em uma chamada.
- Tokens de entrada: tokens enviados no prompt, incluindo instruções e material.
- Tokens de saída: tokens gerados na resposta do modelo.
- Cache de entrada: reaproveitamento de parte da entrada já processada, com tarifa menor.
- Prompt: texto de instrução e material enviado ao modelo.
- Agente: sistema que executa uma tarefa em etapas, usando ferramentas e resultados intermediários.
- Chamada de ferramenta: ação em que o modelo solicita o uso de uma função ou serviço para obter dados ou realizar algo.
- Roteamento: escolha do próximo modelo, agente ou caminho para uma tarefa.
- Extração: seleção de informações de um documento ou resposta e organização em campos.
- Multimodal: capacidade de trabalhar com mais de um tipo de conteúdo, aqui texto, imagem, áudio e vídeo.
- Responses API: interface da Meta Model API usada para enviar entrada e receber a resposta do modelo.
- Subagente: agente auxiliar a quem um agente principal delega parte do trabalho.
- SDK: conjunto de bibliotecas que permite chamar um serviço a partir de uma linguagem de programação.
- Harness: estrutura de teste que organiza como o modelo executa a tarefa e como o resultado é avaliado.
- Pass@1 estrito: medida de sucesso na primeira tentativa, com critério estrito.
- Max: configuração de esforço máximo de raciocínio usada nos resultados destacados.
- P95: medida de latência em que 95% das observações ficam abaixo do valor informado.

Fonte: <https://research.meta.ai/blog/muse-ember>

## Para onde ir depois

Depois da primeira chamada, escolha uma tarefa que realmente se repita no seu fluxo. Comece por extração de campos, roteamento ou leitura de documentos e confira a saída contra o documento original.

A documentação do Muse Ember reúne o uso no Muse Code e na Meta Model API. O relatório de avaliação detalha os testes citados. A Meta encerra o anúncio informando que tem modelos ainda mais eficientes em treinamento.

- Pratique com um documento curto: peça um resumo ou extraia campos e verifique se cada campo corresponde ao conteúdo.
- Antes de usar um prompt acima de 200 mil tokens, calcule a faixa de preço aplicada e separe entrada, cache e saída na estimativa.
- Delegue uma subtarefa repetitiva ao Muse Ember e reserve o planejamento para o Muse Wonder.
- Ao comparar código, leia o método do teste e o harness usado antes de transportar a pontuação para outro fluxo.

Fonte: <https://dev.meta.ai/docs/muse-ember>

## Links citados

- https://artificialanalysis.ai/articles/meta-s-muse-ember-is-the-cheapest-model-scoring-36-on-the-intelligence-index
