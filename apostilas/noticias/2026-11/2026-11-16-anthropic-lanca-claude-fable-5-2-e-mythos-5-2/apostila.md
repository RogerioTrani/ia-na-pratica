# Anthropic lança Claude Fable 5.2 e Mythos 5.2

_2026-11-16 · noticia_

Em 9 de novembro de 2026 a Anthropic lançou o Claude Fable 5.2 e o Claude Mythos 5.2, dois modelos voltados para desafios técnicos complexos em programação, ciência, raciocínio, visão computacional e robótica. Os dois compartilham a mesma base, mas o Fable 5.2 está disponível nos planos pagos e na API, enquanto o Mythos 5.2 é restrito a organizações verificadas. Os novos modelos geram saídas até 30% mais rápidas que a geração 5.1 e custam US$ 8 por milhão de tokens de entrada e US$ 40 por milhão de saída. Nos benchmarks publicados, o Fable 5.2 supera o Opus 5.5 em programação, engenharia de software e uso de computador. A apostila explica o que mudou, mostra os números com o que eles significam, traz o comando para chamar a API e lista o que conferir antes de confiar.

## O fato

Em 9 de novembro de 2026 a Anthropic lançou dois novos modelos de inteligência artificial: o Claude Fable 5.2 e o Claude Mythos 5.2. Segundo o anúncio oficial da empresa, eles foram criados para acelerar a resolução de tarefas técnicas complexas em programação, ciência, raciocínio, visão computacional, finanças e robótica.

Os dois modelos compartilham exatamente o mesmo modelo subjacente. A diferença não está na inteligência, mas nas salvaguardas: o Fable 5.2 tem proteções reforçadas de cibersegurança e biologia para evitar uso indevido, enquanto o Mythos 5.2 tem menos restrições nessas áreas e é liberado apenas para organizações verificadas.

Os modelos operam com janela de contexto de 1 milhão de tokens e modo de pensamento adaptativo sempre ativado. A Anthropic os apresenta como a opção para o trabalho técnico mais ambicioso e aberto, acima do Claude Opus 5.5, que continua sendo o modelo recomendado para a maioria das tarefas de código e conhecimento.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Por que isso importa

A Anthropic já tinha o Claude Opus 5.5 como modelo principal para uso diário. Com o Fable 5.2 e o Mythos 5.2 ela adiciona um degrau acima, voltado para problemas que exigem mais raciocínio, mais autonomia e mais tempo de execução. A empresa relata que mais de 90% das mudanças mescladas em seu próprio código base são escritas pelo Claude, com orientação humana.

O ponto central é a combinação de três coisas ao mesmo tempo: velocidade maior, preço menor que a geração anterior e resultados melhores em testes. Saídas até 30% mais rápidas, US$ 8 por milhão de tokens de entrada contra US$ 10 da geração 5.1, e pontuações acima do Opus 5.5 em programação e uso de computador. Isso muda a conta para quem roda agentes por muitas horas ou processa grandes volumes.

Os modelos também foram usados internamente em tarefas que antes eram inviáveis: formalizar a prova do Último Teorema de Fermat, resolver problemas abertos sobre buracos negros, projetar dispositivos eletrônicos do zero e até escrever um sistema operacional que inicializa em um laptop. São demonstrações de capacidade, não garantias de resultado para qualquer projeto.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Fable 5.2 e Mythos 5.2 compartilham a mesma base

Fable e Mythos são o mesmo modelo subjacente. A diferença está nas políticas de acesso e nas salvaguardas. O Fable 5.2 recebe proteções reforçadas de cibersegurança e biologia, o que permite que a Anthropic o libere para todos os usuários. O Mythos 5.2 tem menos restrições nessas áreas e por isso é liberado apenas para organizações verificadas que conduzem pesquisas benéficas.

Com a base em comum, o que muda é o que cada um pode fazer em áreas sensíveis, como análise de vulnerabilidades e pesquisa biomédica. Testadores também relataram que Fable 5.2 e Mythos 5.2 se comunicam de forma mais clara que as versões anteriores.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Velocidade: até 30% mais rápidas que a geração 5.1

Os modelos geram saídas até 30% mais rápidas que o Claude Fable 5.1 e o Claude Mythos 5.1. A comparação é com a geração anterior da mesma família, não com o Opus 5.5. Isso importa para fluxos longos: agentes que rodam por horas, migrações de código e revisões extensas terminam antes.

Em esforço médio, que é o padrão nos aplicativos Claude e no Claude Code, o Fable 5.2 pode realizar tarefas desafiadoras usando menos tokens que o Fable 5.1. Em testes iniciais no benchmark de programação FrontierCode 2.0, em esforço alto, ele marcou aproximadamente o mesmo que o Opus 5.5 em esforço máximo, por cerca de metade do custo por tarefa. No mesmo teste, em esforço muito alto (Xhigh), o Fable 5.2 alcançou a maior pontuação entre todos os modelos lançados testados.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Preço: US$ 8 por milhão de tokens de entrada e US$ 40 de saída

O preço padrão é de US$ 8 por milhão de tokens de entrada e US$ 40 por milhão de tokens de saída. A leitura de cache custa US$ 0,20 por milhão de tokens. Comparado à geração 5.1, que custava US$ 10 e US$ 50, é uma redução de 20%.

Os novos modelos são mais baratos que a geração 5.1, mas pertencem a uma categoria superior e mais cara que a linha Opus 5. A Anthropic recomenda começar com o Opus 5.5 para a maioria das tarefas de código e conhecimento, e escalar para Fable ou Mythos apenas quando a complexidade exigir.

- US$ 8 por milhão de tokens de entrada (padrão)
- US$ 40 por milhão de tokens de saída (padrão)
- US$ 0,20 por milhão de tokens de leitura de cache
- US$ 10 / US$ 50 eram os preços da geração 5.1, ou seja, redução de 20%

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Fast mode: até 2,5x mais rápido por US$ 16 / US$ 80

Os modelos oferecem um modo rápido opcional, o fast mode, que acelera a geração de tokens em até 2,5 vezes. O preço desse modo é de US$ 16 por milhão de tokens de entrada e US$ 80 por milhão de tokens de saída, o dobro do modo padrão.

O fast mode é útil quando o tempo de resposta importa mais que o custo, por exemplo em fluxos interativos ou demonstrações. Para processamento em lote ou tarefas de longa duração, o modo padrão costuma ser a escolha mais econômica.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Fable 5.2: disponível nos planos pagos e na API

O Claude Fable 5.2 está disponível para todos os usuários nos planos pagos do Claude e para desenvolvedores pela API. Ele tem salvaguardas reforçadas de cibersegurança e biologia para evitar uso indevido, e registrou 55% menos bloqueios desnecessários em comparação com a geração anterior.

Os bloqueios desnecessários são recusas de pedidos legítimos. Menos bloqueios significa menos interrupções no fluxo de trabalho, mantendo a proteção contra uso indevido. As salvaguardas são tão robustas quanto as do Fable 5.1, mas com menos atrito para o usuário.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Mythos 5.2: restrito a organizações verificadas

O Claude Mythos 5.2 é restrito a organizações verificadas que conduzem pesquisas benéficas nos programas oficiais da Anthropic: o Cyber Verification Program e o Life Sciences Verification Program. Clientes Enterprise também podem acessá-lo pelo Claude Security. A razão é que o Mythos tem menos restrições em áreas sensíveis, como cibersegurança e biologia.

Organizações interessadas precisam se candidatar e ser aprovadas. O modelo não está disponível para uso geral, nem nos planos pagos comuns do Claude. Quem não for aprovado usa o Fable 5.2, que compartilha a mesma base.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Benchmarks: Fable 5.2 acima do Opus 5.5

Nos testes publicados no anúncio da Anthropic, o Fable 5.2 supera o Claude Opus 5.5 em programação agêntica, engenharia de software e uso de computador. Os resultados abaixo são três dos benchmarks destacados; a tabela completa do anúncio inclui mais benchmarks.

FrontierCode 2.0 (programação agêntica): 49,1% para o Fable 5.2 contra 45,5% do Opus 5.5 e 32,4% do Fable 5.1. Esse benchmark mede se as mudanças de código propostas pelo modelo seriam mescladas pelos mantenedores de repositórios de código aberto.

FrontierSWE v2 (engenharia de software): 69,9% contra 62,3% do Opus 5.5 e 56,3% do Fable 5.1.

OSWorld 2.1 (uso de computador, conjunto offline parcial): 89,3% contra 87,2% do Opus 5.5 e 83,5% do Fable 5.1.

Em esforço alto, o Fable 5.2 marcou aproximadamente 45,3% no FrontierCode 2.0, quase empatado com o melhor do Opus 5.5 (45,5%), por cerca de metade do custo por tarefa. Em esforço muito alto, atingiu 49,1%, a maior pontuação de qualquer modelo lançado testado.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Os números

Cada número abaixo vem do anúncio oficial da Anthropic de 9 de novembro de 2026. O recorte importa: as pontuações são as maiores disponíveis para cada modelo no esforço mais alto, com salvaguardas ativadas, salvo indicação em contrário.

- 49,1% no FrontierCode 2.0 (Fable 5.2) contra 45,5% do Opus 5.5 e 32,4% do Fable 5.1: programação agêntica
- 69,9% no FrontierSWE v2 (Fable 5.2) contra 62,3% do Opus 5.5 e 56,3% do Fable 5.1: engenharia de software
- 89,3% no OSWorld 2.1 (Fable 5.2) contra 87,2% do Opus 5.5 e 83,5% do Fable 5.1: uso de computador
- 74,6% no Terminal-Bench-Science 0.1 (Fable 5.2) e 75,3% (Mythos 5.2) contra 58,7% do Opus 5.5: pesquisa científica agêntica
- 89,6% no CVE Rediscovery (Mythos 5.2) contra 81,3% do Opus 5.5 sem salvaguardas: cibersegurança
- 64,9% no RoboDojo Sim (Fable 5.2) contra 39,4% do Opus 5.5: robótica
- 74,2% no Humanity's Last Exam com ferramentas (Fable 5.2) contra 67,7% do Opus 5.5: raciocínio multidisciplinar
- 82,1% no WANDR (Fable 5.2) contra 72,3% do Opus 5.5: busca agêntica
- 30% mais rápidas as saídas em relação à geração 5.1
- US$ 8 / US$ 40 por milhão de tokens de entrada / saída no modo padrão
- US$ 16 / US$ 80 por milhão de tokens no fast mode, até 2,5x mais rápido
- 1 milhão de tokens de janela de contexto
- 55% menos bloqueios desnecessários que a geração anterior
- 90% a 99% de redução nos dados coletados por destiladores ilícitos
- cerca de 1.000 agentes formalizaram a prova do Último Teorema de Fermat em 30 horas

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Evidências: Fermat, buracos negros e dispositivos eletrônicos

Durante os testes internos anteriores ao lançamento, a Anthropic documentou três marcos. Uma equipe coordenada de cerca de 1.000 agentes do Fable 5.2 formalizou por completo a demonstração do Último Teorema de Fermat em 30 horas, com intervenção humana mínima. Uma tentativa anterior com um modelo interno havia levado 11 dias; a nova prova ficou 7 vezes mais curta e usou um terço dos tokens de ação.

Os modelos também resolveram dois problemas em aberto na física de buracos negros.

E projetaram três dispositivos eletrônicos funcionais do zero, com placas de circuito impresso. No benchmark de robótica RoboDojo Sim, o Fable 5.2 marcou 64,9% contra 39,4% do Opus 5.5.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Segurança, alignment e defesas antidestilação

A Anthropic rodou testes de segurança extensivos antes do lançamento, incluindo avaliações novas para comportamentos preocupantes como escape de sandbox. A empresa afirma que os riscos de alto impacto por desalinhamento permanecem baixos e que o modelo teve desempenho igual ou melhor que modelos recentes na maioria das medidas de alignment.

As salvaguardas de cibersegurança e biologia do Fable 5.2 são tão robustas quanto as do Fable 5.1, mas produzem menos bloqueios desnecessários. A empresa também implementou suas proteções mais fortes até hoje contra ataques de destilação, reduzindo em 90% a 99% o volume de dados coletados por destiladores ilícitos.

Detalhes completos estão no System Card do Claude Fable 5.2 e Mythos 5.2, referenciado no anúncio oficial.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Quando usar Fable, Mythos, Opus, Sonnet ou Haiku

A Anthropic recomenda que, para a maioria das tarefas de código e conhecimento, o usuário comece com o Claude Opus 5.5, o modelo mais forte para uso diário, e só então mude de modelo conforme a complexidade do trabalho: para cima, para Fable ou Mythos, ou para baixo, para Claude Sonnet 5.5 ou Claude Haiku 5.5.

Fable e Mythos são indicados para o trabalho técnico mais ambicioso e aberto: migrações grandes, auditorias de segurança longas, pesquisa científica agêntica, projetos de hardware e tarefas que exigem coordenação de muitos agentes. Para tarefas rotineiras, o Opus 5.5 costuma ser mais econômico e suficiente.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Fable 5.2 como Advisor ou Orchestrator

O Fable 5.2 pode assumir dois papéis além de responder diretamente. Como Advisor, modelos menores como Haiku, Sonnet ou Opus o consultam para resolver problemas mais difíceis. Como Orchestrator, o Fable 5.2 delega tarefas mais simples a modelos menores e coordena o trabalho.

Esses padrões permitem combinar custo e capacidade: o modelo mais forte entra apenas onde o raciocínio é crítico, e modelos mais baratos executam as partes mecânicas. Isso é especialmente útil em fluxos com muitos agentes rodando por horas.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Disponibilidade: planos pagos, API e nuvens parceiras

O Fable 5.2 está disponível nos planos pagos do Claude e pela API nativa da Anthropic. O Mythos 5.2 está disponível apenas para organizações aprovadas nos programas de verificação. Além disso, a Anthropic informa disponibilidade em serviços de nuvem parceiros: Amazon Web Services (Amazon Bedrock), Google Cloud (Claude Models on Google Cloud) e Microsoft Azure (Microsoft Foundry).

Os identificadores e guias de implantação para essas nuvens estão documentados na documentação da Claude Platform. O exemplo desta apostila usa a chamada direta pela API da Anthropic, sem comandos de implantação em nuvem.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Chamada à API: exemplo completo

Para chamar o Fable 5.2 pela API de mensagens, gere uma chave em platform.claude.com/docs/en/get-api-key, exporte-a na variável de ambiente e envie uma requisição POST para o endpoint oficial. O endpoint é https://api.anthropic.com/v1/messages. Os cabeçalhos obrigatórios são Authorization: Bearer $ANTHROPIC_API_KEY, anthropic-version: 2026-10-21 e content-type: application/json.

Para contas aprovadas no Mythos 5.2, troque apenas o identificador do modelo para claude-mythos-5-2. A estrutura da requisição é a mesma.

```
curl -X POST "https://api.anthropic.com/v1/messages" \
  -H "Authorization: Bearer $ANTHROPIC_API_KEY" \
  -H "anthropic-version: 2026-10-21" \
  -H "content-type: application/json" \
  -d '{
    "model": "claude-fable-5-2",
    "max_tokens": 1024,
    "messages": [
      {"role": "user", "content": "Olá, Claude"}
    ]
  }'
```

Fonte: <https://platform.claude.com/docs/en/api/overview>

## O que muda para você

Se você já usava o Opus 5.5 para tarefas longas de programação, vale testar o Fable 5.2: no FrontierCode 2.0, em esforço alto, ele empatou aproximadamente com o melhor resultado do Opus 5.5 por cerca de metade do custo por tarefa, e em esforço muito alto pontuou mais. Para fluxos com muitos agentes rodando por horas, a combinação de velocidade maior e preço menor muda a viabilidade de projetos que antes eram caros demais.

Um exemplo: a Anthropic relata que uma equipe de agentes rodando uma versão anterior do Fable 5.2 migrou um serviço crítico de produção de Python para Rust, resultando em serviço mais eficiente, mais confiável e que inicia cerca de 26 vezes mais rápido. Esse é um caso documentado pela empresa, não uma promessa para qualquer migração.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## O que fazer hoje

1. Gere uma chave de API em platform.claude.com/docs/en/get-api-key e exporte-a com export ANTHROPIC_API_KEY="SUA_CHAVE". Resultado esperado: a variável fica disponível no shell para as próximas chamadas.
2. Execute o comando de exemplo da seção 'Chamada à API: exemplo completo' trocando o conteúdo da mensagem pelo seu caso. Resultado esperado: uma resposta JSON com a resposta do modelo claude-fable-5-2.
3. Se sua conta for aprovada nos programas de verificação, troque o identificador do modelo para claude-mythos-5-2 e repita a chamada. Resultado esperado: resposta do Mythos 5.2.
4. Avalie se sua tarefa justifica o Fable 5.2 ou se o Opus 5.5 já resolve. Comece pelo Opus 5.5 e escale apenas se a complexidade exigir. Resultado esperado: custo menor nas tarefas em que o Opus 5.5 der conta.
5. Se o tempo de resposta for crítico, teste o fast mode (US$ 16 / US$ 80 por milhão de tokens) e compare com o modo padrão. Resultado esperado: até 2,5x mais rápido na geração de tokens.

Fonte: <https://platform.claude.com/docs/en/get-api-key>

## O que conferir

- Confirme o endpoint: a API de mensagens da Anthropic usa https://api.anthropic.com/v1/messages.
- Confirme o identificador do modelo: claude-fable-5-2 para o Fable e claude-mythos-5-2 para o Mythos.
- Confirme os cabeçalhos: anthropic-version: 2026-10-21, content-type: application/json e autenticação via Authorization: Bearer $ANTHROPIC_API_KEY (x-api-key é aceito como fallback legado).
- O Mythos 5.2 não está disponível para todos: exige aprovação nos programas Cyber Verification ou Life Sciences Verification.
- As pontuações de benchmark são as maiores disponíveis para cada modelo no esforço mais alto, com salvaguardas ativadas. Não assuma que uma tarefa sua terá o mesmo resultado.
- As demonstrações científicas e de engenharia (Fermat, buracos negros, dispositivos) são casos documentados pela Anthropic em testes internos. São evidências de capacidade, não garantias para projetos arbitrários.
- O fast mode custa o dobro do modo padrão. Use quando o tempo importar mais que o custo.
- Disponibilidade nas nuvens parceiras (AWS, Google Cloud, Microsoft Azure) é informada pela Anthropic. Para implantar, consulte a documentação da Claude Platform para cada nuvem.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Glossário

- Token: unidade de texto processada pelo modelo. Preços são cobrados por milhão de tokens de entrada e de saída.
- Janela de contexto: quantidade máxima de texto que o modelo consegue considerar de uma vez. Nos novos modelos é de 1 milhão de tokens.
- Modo de pensamento adaptativo: capacidade do modelo de ajustar o raciocínio interno conforme a complexidade da tarefa, sempre ativado nesses modelos.
- Fast mode: modo opcional que acelera a geração de tokens em até 2,5x, com preço dobrado.
- Salvaguardas: proteções para evitar uso indevido em áreas sensíveis como cibersegurança e biologia.
- Bloqueios desnecessários (over-refusals): recusas de pedidos legítimos pelo modelo. O Fable 5.2 teve 55% menos que a geração anterior.
- Benchmark: teste padronizado usado para comparar modelos. Os citados medem programação, engenharia, uso de computador, raciocínio e robótica.
- Destilação ilícita: tentativa de extrair o raciocínio de um modelo para treinar outro. As defesas do Fable 5.2 reduziram em 90% a 99% os dados coletados por destiladores.
- Advisor: papel em que modelos menores consultam o Fable 5.2 para resolver problemas mais difíceis.
- Orchestrator: papel em que o Fable 5.2 delega tarefas simples a modelos menores e coordena o trabalho.
- API de mensagens: endpoint POST https://api.anthropic.com/v1/messages usado para enviar prompts e receber respostas.
- System Card: documento técnico com detalhes de segurança, alignment e avaliação do modelo.

## Para onde ir depois

- Ler o anúncio oficial em anthropic.com/claude-fable-and-mythos-5-2 para a tabela completa de benchmarks e os casos de uso relatados por empresas.
- Consultar a documentação da Claude Platform em platform.claude.com/docs/en/get-api-key para gerar a chave e em platform.claude.com/docs/en/api/overview para os detalhes da API.
- Testar o Fable 5.2 em uma tarefa longa de programação ou migração e comparar custo e qualidade com o Opus 5.5.
- Se atuar em cibersegurança ou ciências da vida, avaliar a candidatura aos programas de verificação para acessar o Mythos 5.2.
- Acompanhar o System Card do modelo para detalhes de segurança e alignment.
- Explorar os papéis de Advisor e Orchestrator em fluxos com vários agentes.

## Outros pontos do lançamento

- A tabela completa de benchmarks do anúncio, incluindo Humanity's Last Exam, Chartography, WANDR, RoboDojo Sim, BenchCAD 2.1, AA-Briefcase, Remote Labor Index, AutomationBench, CyScenarioBench e CVE Rediscovery.
- A comparação com GPT-6 Astra e Gemini 4 Carbon em vários benchmarks.
- A tentativa anterior de formalizar o Último Teorema de Fermat com modelo interno, que levou 11 dias, com prova 7 vezes mais longa e três vezes mais tokens de ação.
- O protótipo de sistema operacional escrito pelo Fable 5.2 com mais de 1.000 subagentes em 8 dias, que inicializa em um laptop.
- A migração de um serviço crítico de produção de Python para Rust, com inicialização cerca de 26 vezes mais rápida.
- O hypervisor com mais de 3.500 provas verificadas por máquina.
- A auditoria de segurança de 10 a 12 horas com cerca de 170 agentes revisores, write-up, pull requests de correção e proposta de política.
- Os relatos de empresas como Vercel, Shopify, Datadog, Unity, Uber, Oracle, iGent, Snowflake e Cognition sobre o uso do Fable 5.2.
- O fast mode com preço dobrado e aceleração de até 2,5x.
- A leitura de cache a US$ 0,20 por milhão de tokens e a redução de 20% em relação à geração 5.1.
- Os papéis de Advisor e Orchestrator e a recomendação de começar com o Opus 5.5.
- A disponibilidade em Amazon Bedrock, Google Cloud Vertex AI e Microsoft Foundry, além da API nativa.
