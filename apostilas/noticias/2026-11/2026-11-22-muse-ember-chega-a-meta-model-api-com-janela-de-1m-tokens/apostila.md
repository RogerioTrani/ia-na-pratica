# Muse Ember chega à Meta Model API com janela de 1M tokens

_2026-11-22 · noticia_

A Meta lançou o Muse Ember, o menor e mais eficiente modelo da linha Muse, feito para o trabalho que agentes repetem o dia todo: chamadas de ferramentas, subtarefas de código, roteamento, extração e leitura de documentos longos. Custa US$ 0,10 por milhão de tokens de entrada e US$ 0,50 por milhão de saída, tem janela de 1M tokens e já está no Muse Code e na Meta Model API. Segundo o Artificial Analysis, iguala a melhor pontuação do Claude Haiku 5.5 por cerca de um terço do custo por tarefa. Esta apostila traz preços, números dos testes e os passos para usar o modelo.

## O que é o Muse Ember

O Muse Ember é o menor e mais eficiente modelo da Meta. Agentes gastam a maior parte dos tokens em muitos passos pequenos e estruturados, e é esse volume que o modelo foi feito para absorver: chamadas de ferramentas, subtarefas de código, roteamento, extração e leitura de documentos longos.

Ele consegue conduzir um fluxo de negócio de ponta a ponta: puxar registros, chamar ferramentas em sequência e atualizar sistemas em vários aplicativos. Também entende texto, imagem, áudio e vídeo, então lê capturas de tela, gráficos e documentos escaneados sem outro modelo.

Fonte: <https://research.meta.ai/blog/muse-ember>

## Preços e limites

O nome do modelo na plataforma é muse-ember-1.0. Os valores abaixo são por milhão de tokens.

- Até 200 mil tokens no prompt: US$ 0,10 de entrada, US$ 0,004 de entrada em cache e US$ 0,50 de saída.
- Acima de 200 mil tokens: US$ 0,30 de entrada, US$ 0,012 em cache e US$ 1,50 de saída.
- Janela de contexto de 1M tokens e até 512K tokens de saída.
- Suporta a Responses API.

Fonte: <https://dev.meta.ai/models/muse-ember>

## Contexto longo em uma chamada só

Com 1M tokens de contexto e até 512K de saída, uma base de código inteira ou um conjunto de documentos cabe em uma única chamada. O agente lê tudo de uma vez, sem picotar o material em pedaços.

Fonte: <https://research.meta.ai/blog/muse-ember>

## Custo e desempenho nos testes

O Artificial Analysis mediu a pontuação do Muse Ember contra o custo por tarefa. O modelo iguala a melhor pontuação do Claude Haiku 5.5 gastando cerca de um terço por tarefa e supera todas as configurações do GPT-6 Luna. Os custos do Muse Ember são estimados a preço de lista.

No AutomationBench-AA, que mede fluxos de negócio de ponta a ponta (pass@1 estrito, raciocínio no máximo), a diferença é grande.

- Custo por tarefa, em US$: Muse Ember 0,136; GPT-6 Luna 0,152; Claude Haiku 5.5 0,411.
- AutomationBench-AA: Muse Ember 37,8%; GPT-6 Luna 20,2%; Claude Haiku 5.5 13,9%.

Fonte: <https://artificialanalysis.ai/articles/meta-s-muse-ember-is-the-cheapest-model-scoring-36-on-the-intelligence-index>

## Usar no Muse Code

O Muse Ember está disponível no Muse Code em pré-pago e em todos os planos. A instalação é para macOS e Linux.

- Rode o comando de instalação abaixo.
- Abra uma sessão do Muse Code.
- Escolha o Muse Ember no seletor de modelos da sessão.

```
curl -fsSL https://dev.meta.ai/install.sh | bash
```

Fonte: <https://dev.meta.ai/products/muse-code/>

## Usar na Meta Model API

As chamadas vão para o endereço da Responses API, com o modelo muse-ember-1.0 e a chave no cabeçalho Authorization.

- Entre em dev.meta.ai, abra a aba API keys e clique em Create API key.
- Dê um nome à chave e copie na hora: ela só aparece uma vez.
- Guarde a chave na variável de ambiente MODEL_API_KEY.
- Envie um POST para o endereço abaixo com o cabeçalho Authorization: Bearer $MODEL_API_KEY e o modelo muse-ember-1.0.

Fonte: <https://dev.meta.ai/docs/muse-ember>

## Para o difícil, combine com o Muse Wonder

Nos problemas mais duros, a Meta sugere dividir o trabalho: o Muse Wonder planeja e o Muse Ember cuida do volume. O Muse Ember foi o primeiro modelo treinado com o Muse Wonder Full.

- Muse Wonder: dev.meta.ai/models/muse-wonder
- Documentação do Muse Ember: dev.meta.ai/docs/muse-ember

Fonte: <https://dev.meta.ai/models/muse-wonder>

## Além do vídeo

- Outros resultados no máximo de raciocínio, Muse Ember contra Luna e Haiku: Agents' Last Exam 61,6% (Luna 57,1%, Haiku 57,0%); Terminal-Bench 4.0 40,9% (Haiku 39,2%, Luna 16,4%); Coding Agent Index-AA 46 (Haiku 37, Luna 31); PerceptionBench 80,6% (Haiku 78,6%, Luna 62,8%).
- No FrontierCode 2.0-AA o Haiku 5.5 vai melhor: 34,9%, contra 27,2% do Muse Ember e 25,2% do Luna.
- Comparação com o Muse Spark 1.3 no Artificial Analysis: índice 36 contra 37, custo por tarefa de US$ 0,14 contra US$ 2,39, e preço por milhão de tokens de US$ 0,10 de entrada e US$ 0,50 de saída contra US$ 1,25 e US$ 4,25.
- Depoimentos de parceiros em testes iniciais: Box, Cline, Oracle, Cloudflare e You.com. A Cloudflare relatou até 30% mais velocidade na cauda; a You.com, p95 de 2,2 segundos e 36% a 48% menos tokens de saída.
- Segurança: antes do lançamento, a Meta avaliou o modelo em riscos químicos e biológicos, de cibersegurança e de perda de controle, e ele ficou abaixo dos limites de alto risco do framework. Também testou se ele resiste a instruções escondidas em páginas, documentos e saídas de ferramentas.
