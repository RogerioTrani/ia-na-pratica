# Muse Ember chega à Meta Model API com janela de 1M tokens

_2026-11-22 · noticia_

A Meta lançou o Muse Ember, o menor e mais eficiente modelo da linha Muse, feito para chamadas de ferramentas, subtarefas de código, roteamento, extração e leitura de documentos longos. Custa US$ 0,10 por milhão de tokens de entrada e US$ 0,50 por milhão de saída, com janela de 1M tokens. Segundo o Artificial Analysis, iguala a melhor pontuação do Claude Haiku 5.5 por cerca de um terço do custo por tarefa.

## O fato

O Muse Ember é o menor e mais eficiente modelo da Meta. Agentes gastam a maior parte dos tokens em muitos passos pequenos e estruturados, e é esse volume que o modelo foi feito para absorver: chamadas de ferramentas, subtarefas de código, roteamento, extração e leitura de documentos longos.

Ele consegue conduzir um fluxo de negócio de ponta a ponta: puxar registros, chamar ferramentas em sequência e atualizar sistemas em vários aplicativos. Também entende texto, imagem, áudio e vídeo, então lê capturas de tela, gráficos e documentos escaneados sem outro modelo. Fonte: https://research.meta.ai/blog/muse-ember

Fonte: <https://research.meta.ai/blog/muse-ember>

## Preços e limites

O nome do modelo na plataforma é muse-ember-1.0. Os valores abaixo são por milhão de tokens. Fonte: https://dev.meta.ai/models/muse-ember

- Até 200 mil tokens no prompt: US$ 0,10 de entrada, US$ 0,004 de entrada em cache e US$ 0,50 de saída.
- Acima de 200 mil tokens: US$ 0,30 de entrada, US$ 0,012 em cache e US$ 1,50 de saída.
- Janela de contexto de 1M tokens e até 512K tokens de saída.
- Suporta a Responses API.

Fonte: <https://dev.meta.ai/models/muse-ember>

## Contexto longo em uma chamada só

Com 1M tokens de contexto e até 512K de saída, uma base de código inteira ou um conjunto de documentos cabe em uma única chamada. O agente lê tudo de uma vez, sem picotar o material em pedaços. Fonte: https://research.meta.ai/blog/muse-ember

Fonte: <https://research.meta.ai/blog/muse-ember>

## Custo e desempenho nos testes

O Artificial Analysis mediu a pontuação do Muse Ember contra o custo por tarefa. O modelo iguala a melhor pontuação do Claude Haiku 5.5 gastando cerca de um terço por tarefa e supera todas as configurações do GPT-6 Luna. Os custos do Muse Ember são estimados a preço de lista.

No AutomationBench-AA, que mede fluxos de negócio de ponta a ponta (pass@1 estrito, raciocínio no máximo), a diferença é grande. Fonte: https://artificialanalysis.ai/articles/meta-s-muse-ember-is-the-cheapest-model-scoring-36-on-the-intelligence-index

- Custo por tarefa, em US$: Muse Ember 0,136; GPT-6 Luna 0,152; Claude Haiku 5.5 0,411.
- AutomationBench-AA: Muse Ember 37,8%; GPT-6 Luna 20,2%; Claude Haiku 5.5 13,9%.

Fonte: <https://artificialanalysis.ai/articles/meta-s-muse-ember-is-the-cheapest-model-scoring-36-on-the-intelligence-index>

## Usar no Muse Code

O Muse Ember está disponível no Muse Code em pré-pago e em todos os planos. A instalação é para macOS e Linux. Página do produto: https://dev.meta.ai/products/muse-code/. Script de instalação: https://dev.meta.ai/install.sh

1. rode o comando de instalação abaixo. Resultado: o Muse Code fica instalado.
2. abra uma sessão do Muse Code. Resultado: a sessão fica pronta para escolher o modelo.
3. escolha o Muse Ember no seletor de modelos da sessão. Resultado: a sessão passa a usar o Muse Ember.

```
curl -fsSL https://dev.meta.ai/install.sh | bash
```

Fonte: <https://dev.meta.ai/products/muse-code/>

## Usar na Meta Model API

As chamadas vão para o endereço da Responses API, com o modelo muse-ember-1.0 e a chave no cabeçalho Authorization. Documentação: https://dev.meta.ai/docs/muse-ember

1. entre em dev.meta.ai, abra a aba API keys e clique em Create API key. Resultado: a chave é criada.
2. dê um nome à chave e copie na hora: ela só aparece uma vez. Resultado: você guarda a chave antes de sair da tela.
3. guarde a chave na variável de ambiente MODEL_API_KEY. Resultado: a chave fica fora do código.
4. envie um POST para o endereço da Responses API com o cabeçalho Authorization: Bearer $MODEL_API_KEY e o modelo muse-ember-1.0. Resultado: o modelo responde.

Fonte: <https://dev.meta.ai/docs/muse-ember>

## Para o difícil, combine com o Muse Wonder

Nos problemas mais duros, a Meta sugere dividir o trabalho: o Muse Wonder planeja e o Muse Ember cuida do volume. O Muse Ember foi o primeiro modelo treinado com o Muse Wonder Full. Muse Wonder: https://dev.meta.ai/models/muse-wonder

Fonte: <https://dev.meta.ai/models/muse-wonder>

## O que conferir

Fato: os números de teste vêm do Artificial Analysis e da própria Meta. Os custos do Muse Ember são estimados a preço de lista.

Segurança: antes do lançamento, a Meta avaliou o modelo em riscos químicos e biológicos, de cibersegurança e de perda de controle, e ele ficou abaixo dos limites de alto risco do framework. Também testou se ele resiste a instruções escondidas em páginas, documentos e saídas de ferramentas.

Comparação com o Muse Spark 1.3 no Artificial Analysis: índice 36 contra 37, custo por tarefa de US$ 0,14 contra US$ 2,39, e preço por milhão de tokens de US$ 0,10 de entrada e US$ 0,50 de saída contra US$ 1,25 e US$ 4,25.

Fonte: <https://research.meta.ai/blog/muse-ember>
