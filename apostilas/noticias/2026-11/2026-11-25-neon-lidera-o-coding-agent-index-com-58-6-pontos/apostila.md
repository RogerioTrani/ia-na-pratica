# Neon lidera o Coding Agent Index com 58,6 pontos

_2026-11-25 · noticia_

O Google apresentou o Gemini 4 Neon em 18 de novembro de 2026 como um modelo para fluxos longos de programação, análise e trabalho científico. O anúncio destaca o primeiro lugar no Coding Agent Index da Artificial Analysis, com 58,6 pontos, e um salto no SWE-sweep quando o mesmo modelo roda no Google Antigravity. Ao longo desta apostila, você vai entender o que o índice mede, como o harness e os subagentes mudam o resultado e quais são os preços e caminhos de acesso. Também vai ver os limites dos benchmarks, os cuidados com segurança e um roteiro prático para testar o modelo no seu próprio fluxo.

## O fato

Em 18 de novembro de 2026, o Google apresentou o Gemini 4 Neon. O modelo foi anunciado para fluxos complexos de engenharia de software, trabalho de conhecimento e ciência, com foco em concluir tarefas de ponta a ponta. O anúncio oficial informa que o Neon ficou em primeiro lugar no Coding Agent Index da Artificial Analysis, com 58,6 pontos.

O lançamento também ampliou o acesso. Desenvolvedores podem usar a API paga do Gemini no Google AI Studio e no Android Studio. Assinantes pagos do Google AI Pro e Ultra têm acesso no Google Antigravity, e assinantes Pro e Ultra podem selecionar o modelo no app Gemini. Empresas têm acesso pelo Gemini for business, via API ou menu de modelos.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## Por que isso importa

Um modelo de linguagem gera respostas a partir das instruções e do contexto que recebe. Um agente de código usa esse modelo dentro de um fluxo de trabalho: lê arquivos, executa comandos, edita código e verifica o resultado das ações. Por isso, avaliar um agente exige observar mais do que a capacidade do modelo isolado.

O harness é o ambiente que organiza esse fluxo. Ele define como o agente recebe ferramentas, acessa o repositório, executa comandos e retoma o trabalho ao longo de uma tarefa. A Artificial Analysis compara agentes, modelos e configurações de execução justamente porque esses elementos podem produzir resultados diferentes.

Os 58,6 pontos do Neon são uma nota composta do Coding Agent Index. Eles não representam 58,6% de acerto em uma única prova. O índice resume o desempenho em três testes diferentes e serve para comparação rápida, desde que seja lido junto com o resultado de cada componente.

Fonte: <https://artificialanalysis.ai/agents/coding-agents#coding-agents-index>

## Como o Coding Agent Index chega a 58,6

O Coding Agent Index v2.1 combina três benchmarks com pesos iguais. Cada tarefa é avaliada em três tentativas, e a média dessas tentativas entra no cálculo. Depois, os resultados das tarefas são combinados para que cada uma tenha o mesmo peso na nota final.

Os componentes medem partes distintas do trabalho de um agente. Entender essa divisão ajuda a interpretar o primeiro lugar do Neon e a identificar onde ele pode ser mais forte ou mais fraco em um projeto real.

- FrontierCode-AA 2.0 reúne 132 tarefas de engenharia de software, criadas pela Cognition e implementadas pela Artificial Analysis.
- Terminal-Bench 4.1 reúne 66 tarefas de uso agêntico do terminal, responsabilidade da Laude Institute.
- SWE-Atlas-QnA-AA reúne 124 tarefas de perguntas técnicas, criadas pela Scale AI e com correção ajustada pela Artificial Analysis.

Fonte: <https://artificialanalysis.ai/agents/coding-agents#coding-agents-index>

## O mesmo modelo, dois resultados no SWE-sweep

No SWE-sweep, o Gemini 4 Neon alcançou 12,8% no harness mini-SWE e 39,0% no Google Antigravity. O Google descreve a segunda marca como estado da arte e afirma que o resultado mais que triplicou quando o ambiente de execução mudou.

A comparação isola uma variável importante: o modelo permaneceu o mesmo, enquanto o harness mudou. O ambiente pode alterar a maneira como o agente lê arquivos, executa comandos, recebe ferramentas e organiza o trabalho. O resultado de 39,0% pertence ao Antigravity; os 12,8% pertencem ao mini-SWE.

Para avaliar um agente no seu fluxo, vale repetir a mesma tarefa com o mesmo modelo e registrar o harness usado. Assim, a comparação fica mais próxima da pergunta que interessa: qual combinação de modelo e ambiente resolve melhor o seu problema.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## Orquestração com subagentes Hydrogen

No Google Antigravity, o Neon pode trabalhar sozinho ou atuar como orquestrador. Nessa função, ele dirige vários subagentes Hydrogen em paralelo. O anúncio associa essa configuração a fluxos longos e com muitas ferramentas.

Um orquestrador divide uma tarefa maior em partes, distribui essas partes e reúne os resultados. Um subagente executa uma parte com seu próprio contexto de trabalho. A paralelização pode ajudar quando existem atividades independentes, como investigar arquivos diferentes ou produzir componentes separados da mesma entrega.

Os exemplos do anúncio usam /swarm no Google Antigravity. O comando aparece associado à criação de trabalho por um enxame de agentes. A divisão do trabalho precisa respeitar dependências: se duas partes mexem no mesmo trecho de código, o risco de conflito aumenta.

```
/swarm
```

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## Sessões longas: leitura, progresso e compactação

Em uma sessão longa, o agente pode precisar consultar os mesmos arquivos várias vezes. Cada leitura consome tempo e tokens, além de ocupar espaço no contexto. O anúncio diz que o Neon reduz leituras redundantes, compartilha o progresso enquanto trabalha e lida com a compactação de contexto.

Compactação de contexto é o processo de reorganizar ou resumir o histórico para liberar espaço na janela, preservando as informações necessárias para continuar a tarefa. Em um trabalho com muitos passos, isso ajuda a manter o foco sem tratar todo o histórico como se tivesse a mesma importância.

Os avisos de andamento ajudam o usuário a acompanhar o que está sendo feito e a corrigir o rumo no meio da execução. Para quem usa agentes em tarefas demoradas, esse acompanhamento reduz a sensação de uma caixa-preta e permite intervir antes que um desvio se espalhe.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## Os níveis de pensamento e o lugar na família Gemini 4

Na família Gemini 4, o Carbon é apresentado para os projetos mais difíceis e de longa duração, o Hydrogen para a execução rápida do dia a dia e o Neon para equilibrar profundidade e eficiência. O Neon tem quatro níveis de pensamento, que permitem ajustar o esforço de raciocínio e o gasto de tokens conforme a tarefa.

O nível padrão é chamado de high. O nível xhigh adiciona raciocínio mais profundo e em várias etapas para os trabalhos mais difíceis. O Google informa que, no nível high, o Neon teve 32% menos custo por tarefa que o Carbon em benchmarks de terceiros. Também relata reduções de aproximadamente 50% a 80% no custo por tarefa diante dos principais modelos concorrentes nas comparações em que ele aparece na fronteira de Pareto.

No nível xhigh, o Google afirma que o Neon ainda custa mais de 36% menos por tarefa do que modelos concorrentes em sua configuração mais alta. Esses números descrevem custo por tarefa em avaliações específicas. Eles não equivalem ao preço por token, ao valor de uma assinatura nem ao custo total de operação de um sistema em produção.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## Além do código: análise, documentos e ciência

O anúncio também cobre trabalho analítico e científico. O Neon pode reunir planilhas, PDFs, gráficos, áudio e vídeo em uma única janela de 1 milhão de tokens e transformar esses materiais em entregas estruturadas. Essa capacidade interessa a quem precisa cruzar informações espalhadas por vários formatos antes de produzir um relatório ou uma análise.

Os resultados divulgados pelo Google mostram desempenho em diferentes tipos de tarefa. Cada percentual pertence ao benchmark indicado e não deve ser transferido para outra atividade.

- No Vals Index, o Neon ficou em segundo lugar, com 70,9%.
- No Chartography, voltado à leitura de gráficos profissionais densos, o Neon marcou 73,5%.
- No Agents' Last Exam v1.1, o resultado foi 75,8%, descrito pelo Google como comparável ao de modelos líderes.
- No Terminal-Bench Science, o Neon marcou 70,5%; no RiemannBench, 84,0%; e no HLE-Diamond, 71,3%. Esses testes cobrem raciocínio científico e matemático.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## Exemplos de uso no Google Antigravity

O anúncio reúne demonstrações de tarefas longas executadas no Google Antigravity. Os casos abaixo mostram a variedade de trabalhos apresentados pelo Google, incluindo programação gráfica, reconstrução histórica e manipulação de planilhas.

Esses exemplos são demonstrações relatadas pelo fornecedor. Eles ajudam a entender o tipo de fluxo pretendido, mas não garantem o mesmo resultado em outro repositório, conjunto de dados ou configuração de harness.

- Blender MCP: usando /swarm, o Neon construiu uma bancada de laboratório 3D fotorrealista para visualizar nomes de modelos com elementos visuais associados a cada nome.
- WebGL2: o Neon escreveu um simulador de esqui em primeira pessoa usando terreno real de Mont Blanc e Chamonix, com 10.200 linhas de shaders personalizados, física de esqui a 120 Hz, seis linhas alpinas e nenhum recurso pronto.
- Reconstrução 3D: com /swarm, o Neon usou fotos de arquivo para recriar em 3D interativo a sala de estudos de Alan Turing em 1936 no King's College, Cambridge, incluindo uma Universal Turing Machine funcional sobre a mesa.
- Google Sheets: um enxame de agentes transformou uma imagem em uma planilha de 100.000 células, sem imagens incorporadas e sem Apps Script, usando mais de 500.000 fórmulas ativas para seis modos interativos.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## Cibersegurança defensiva

O anúncio trata a cibersegurança como um ciclo que inclui gerar código seguro, encontrar vulnerabilidades, validar riscos e corrigir a causa do problema. O Gemini 4 Neon for cyber foi apresentado para esse fluxo defensivo, com resultados em testes específicos e acesso controlado.

Os números a seguir mantêm o recorte de cada avaliação. Eles indicam desempenho nas condições descritas pelo Google e não substituem uma auditoria de segurança nem autorizam o uso ofensivo das ferramentas.

- No AutoBaxBench, o Neon produziu código mais seguro que o Carbon nos desafios fáceis, médios e difíceis, chegando a 76% no nível difícil, descrito como estado da arte.
- No WebExploitBench v1.2, o Neon marcou 51,26% e foi descrito como estado da arte, com metade do custo de modelos grandes concorrentes.
- No SEC-bench Pro, o Neon marcou 90,5% na busca por vulnerabilidades, com aproximadamente metade do custo por desafio.
- No ExploitGym, o Neon teve desempenho de ponta usando metade dos tokens do Carbon para validar riscos por exploração.
- No CWE-bench v2, o Neon marcou 70,7% na correção de vulnerabilidades, com elevação de 3,4% sobre o Carbon.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## Segurança e prompt injection

O Google diz que o Neon mantém proteções equivalentes às do Carbon contra uso indevido severo e prompt injection, além de avançar no alinhamento e no comportamento agêntico. Prompt injection ocorre quando instruções maliciosas aparecem em páginas, e-mails, documentos ou código que o agente consulta.

No benchmark IPI da Gray Swan, com salvaguardas em tempo real e no nível mais alto de pensamento, o Neon resistiu a todos os ataques daquele teste. A taxa de sucesso dos ataques foi de 0,0% nessa configuração específica. O resultado se restringe ao benchmark e às condições descritas.

Para uso em produção, a proteção do modelo precisa ser combinada com limites de ferramentas, revisão das ações e controle do escopo. Um resultado de benchmark não elimina a necessidade de tratar páginas e arquivos externos como entradas não confiáveis.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## Preço, contexto e onde usar

O preço do Gemini 4 Neon é cobrado por milhão de tokens. Tokens de entrada são as informações enviadas ao modelo, incluindo instruções e contexto. Tokens de saída são o conteúdo gerado. Tokens de entrada em cache têm um preço reduzido quando o provedor reutiliza informações já processadas.

O anúncio informa uma janela de contexto de 1 milhão de tokens. Esse limite não define a qualidade da resposta nem o custo final de uma tarefa: uma sessão pode consumir mais tokens ao longo de várias interações, e o resultado depende do problema e do fluxo de execução.

- Entrada sem cache: US$ 3 por milhão de tokens.
- Entrada em cache: US$ 0,15 por milhão de tokens, com desconto de 95% sobre o preço da entrada sem cache.
- Saída: US$ 15 por milhão de tokens.
- Janela de contexto: 1 milhão de tokens.
- Para desenvolvedores, o acesso anunciado inclui a API paga do Gemini no Google AI Studio e no Android Studio.
- No Google Antigravity, o Neon está disponível para assinantes pagos do Google AI Pro e Ultra.
- No app Gemini, assinantes Pro e Ultra podem selecionar o Neon no menu de modelos.
- Empresas podem usar o modelo pelo Gemini for business, via API ou menu de modelos.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## Os números

Os principais números do anúncio respondem a perguntas diferentes. A nota do índice resume três benchmarks, os percentuais mostram resultados em testes específicos e os valores em dólares descrevem o preço por milhão de tokens. Comparar esses formatos como se fossem a mesma medida leva a conclusões erradas.

- 58,6 pontos: nota composta do Neon no Coding Agent Index, com primeiro lugar geral. Não é uma porcentagem de acerto.
- 65,2%: resultado do Neon no Terminal-Bench 4.1, voltado a fluxos agênticos no terminal.
- 46,2%: resultado no FrontierCode 2.0 no nível padrão de pensamento, chamado high. Não é a nota do índice composto.
- 12,8%: resultado do mesmo modelo no SWE-sweep usando o harness mini-SWE.
- 39,0%: resultado do mesmo modelo no SWE-sweep usando o Google Antigravity. A diferença em relação ao mini-SWE mostra o peso do harness nesse teste.
- 61 pontos: nota na Artificial Analysis Intelligence Index no nível xhigh, com terceiro lugar geral. É um índice de inteligência, distinto do Coding Agent Index.
- US$ 3 por milhão: preço dos tokens de entrada sem cache.
- US$ 0,15 por milhão: preço dos tokens de entrada em cache.
- US$ 15 por milhão: preço dos tokens de saída.
- 1 milhão de tokens: tamanho da janela de contexto, e não uma garantia de acerto nem o custo de uma tarefa.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## O que muda para você

Exemplo: Imagine que você precisa corrigir um bug que atravessa vários arquivos de um repositório. O Neon foi anunciado para depuração e refatoração em vários arquivos, com edições direcionadas. Você pode descrever o problema, os arquivos envolvidos e o comportamento esperado, deixando claro onde a tarefa termina.

Execute a tarefa no harness que você já usa e registre o modelo, o nível de pensamento, as ferramentas disponíveis e o tempo de trabalho. Se tiver acesso ao Google Antigravity, repita a mesma tarefa nesse ambiente. Compare a correção, os testes, os arquivos alterados, o consumo de tokens e o custo por tarefa.

O objetivo é descobrir se a combinação entre o Neon e aquele harness funciona no seu projeto. O resultado de 39,0% no SWE-sweep indica o que aconteceu naquele teste; a decisão prática depende do seu repositório, das suas verificações e do custo que você observa.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## O que fazer hoje

1. Escolha o canal de acesso. Use a API paga do Gemini no Google AI Studio ou no Android Studio; no Google Antigravity, verifique se sua assinatura Google AI Pro ou Ultra inclui o Neon. O resultado esperado é encontrar o modelo disponível no canal escolhido.
2. Defina uma tarefa com escopo e critério de conclusão. Para código, descreva o problema, os arquivos relevantes e a verificação esperada. O resultado esperado é uma instrução que permita distinguir uma entrega correta de uma resposta apenas plausível.
3. Execute a tarefa e registre o modelo, o harness, o nível de pensamento e as ferramentas usadas. O resultado esperado é uma execução reproduzível, que possa ser comparada com outra tentativa.
4. No Google Antigravity, experimente a orquestração com subagentes Hydrogen em uma tarefa que possa ser dividida em partes independentes. O resultado esperado é acompanhar a distribuição do trabalho e verificar como as partes são reunidas.
5. Repita a mesma tarefa em outra configuração disponível e compare correção, tempo, tokens e custo por tarefa. O resultado esperado é identificar o efeito do harness e do nível de pensamento sobre o seu fluxo.
6. Revise o resultado antes de aceitar. Confira o código, os testes, o escopo das alterações e qualquer afirmação apresentada como fato. O resultado esperado é uma entrega verificada por você, e não apenas um texto gerado pelo agente.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## O que conferir

- Índice composto: leia o resultado de cada benchmark junto com a nota geral. Dois agentes com pontuações próximas podem ter forças diferentes em implementação, terminal e compreensão de repositório.
- Harness: compare o mesmo modelo nas mesmas condições. Os 12,8% no mini-SWE e os 39,0% no Antigravity mostram que o ambiente altera o resultado do SWE-sweep.
- Custo: diferencie preço por token, custo por tarefa e preço de assinatura. O desconto de entrada em cache não se aplica automaticamente a todos os tokens enviados.
- Nível de pensamento: registre se o teste usou high ou xhigh. Resultados de níveis diferentes não devem ser tratados como uma comparação direta.
- Fonte da avaliação: separe resultados internos do Google de avaliações independentes e mantenha o recorte de cada benchmark.
- Limitações do modelo: o model card lista alucinações como limitação conhecida, indica corte de conhecimento em março de 2026 e registra trabalho contínuo na resistência a jailbreaks.
- Segurança: trate páginas, documentos e código externos como entradas que podem conter instruções maliciosas. O resultado de 0,0% no benchmark IPI vale para a configuração testada.
- Acesso: confirme o canal e o plano. No Google Antigravity, o Neon foi anunciado para assinantes pagos Google AI Pro e Ultra; a API do Gemini tem cobrança por uso.
- Cibersegurança: o acesso ao Gemini 4 Neon for cyber foi anunciado para defensores confiáveis no Fairwind Program. Os resultados dos testes não substituem revisão de segurança humana.
- Exemplos do fornecedor: use as demonstrações do Antigravity para entender o fluxo pretendido e teste o resultado no seu próprio projeto antes de adotá-lo.

Fonte: <https://deepmind.google/models/model-cards/gemini-4-neon/>

## Glossário

- Agente de código: fluxo que usa um modelo para executar tarefas de programação com ferramentas, como ler arquivos, rodar comandos e editar código.
- Modelo: componente que gera respostas e decisões a partir do contexto recebido.
- Harness: ambiente que organiza a execução do agente, suas ferramentas e o andamento da tarefa.
- Orquestrador: agente responsável por dividir o trabalho, distribuir tarefas e reunir os resultados.
- Subagente: agente que executa uma parte específica da tarefa sob a coordenação de outro agente.
- Benchmark: teste padronizado usado para medir um desempenho em condições definidas.
- SWE-sweep: benchmark citado no anúncio para comparar o resultado do mesmo modelo em diferentes harnesses.
- Terminal-Bench 4.1: benchmark de tarefas agênticas executadas em ambiente de terminal.
- FrontierCode 2.0: benchmark de engenharia de software citado no resultado do Neon no nível high.
- Token: unidade de texto processada pelo modelo, usada também para calcular consumo e preço.
- Janela de contexto: quantidade de tokens que o modelo pode considerar em uma interação, incluindo entradas e saídas dentro do limite informado.
- Compactação de contexto: reorganização ou resumo do histórico para liberar espaço e permitir a continuidade de sessões longas.
- Token em cache: token de entrada reaproveitado pelo provedor e cobrado com um preço reduzido.
- Nível de pensamento: configuração que ajusta a profundidade do raciocínio e o consumo de tokens, como high e xhigh.
- Prompt injection: tentativa de inserir instruções maliciosas em páginas, documentos, e-mails ou código consultados pelo agente.
- Alucinação: informação gerada pelo modelo que não corresponde à realidade ou às fontes disponíveis.
- Fronteira de Pareto: conjunto de opções em que melhorar uma medida, como desempenho, exige abrir mão de outra, como custo.

Fonte: <https://artificialanalysis.ai/agents/coding-agents#coding-agents-index>

## Para onde ir depois

O próximo passo é repetir uma tarefa real com o Neon e registrar o resultado. Comece com um problema delimitado, avalie a entrega e só então aumente a complexidade. Use o model card para conhecer as limitações e a página da Artificial Analysis para comparar o índice com os resultados individuais de cada benchmark.

Para praticar, escolha uma correção em vários arquivos, uma tarefa de análise de documentos ou um fluxo de terminal. O aprendizado está em observar como o modelo, o harness e o nível de pensamento mudam a execução, e em criar o hábito de revisar o resultado antes de usá-lo.

- Pratique com um bug de escopo claro e registre os arquivos alterados, os testes executados e o consumo de tokens.
- Amplie a prática para uma tarefa com partes independentes e avalie se a orquestração com subagentes ajuda no seu fluxo.
- Teste uma tarefa de análise com planilhas, PDFs ou gráficos e verifique se a entrega estruturada corresponde ao pedido.
- Consulte o model card e a metodologia dos benchmarks para manter os resultados dentro do escopo em que foram medidos.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## Links citados

- https://aistudio.google.com/prompts/new_chat?model=gemini-4-neon
- https://antigravity.google/
- https://cognition.com/blog/frontier-code-2.0
- https://storage.googleapis.com/deepmind-media/Model-Cards/Gemini-4-Neon-Model-Card.pdf
- https://www.tbench.ai/

## Além do vídeo

- O Neon ficou em primeiro lugar no Legal Research Bench e no Tax Agent Bench.
- O Google relata que o Neon ficou em primeiro na maioria dos benchmarks da Surge AI em finanças, contabilidade, modelagem de planilhas e cumprimento de restrições complexas.
- No Agent Arena Index, o Neon estreou em segundo lugar, com 1.336 pontos, em mais de 4.200 sessões reais de agentes; o anúncio também o coloca em segundo em steerability, que mede a adaptação a correções do usuário durante a tarefa.
- O Neon marcou 56,3% no AutomationBench, com primeiro lugar, e US$ 16.843 no Vending-Bench 2, também com primeiro lugar, em uma simulação de longa duração de administração de um negócio.
- O model card informa até 64 mil tokens de saída síncrona por padrão e até 1 milhão de tokens via decodificação longa em segundo plano.
- O model card registra 56,5% no MKA Climb WSR, 89,0% no LVBench e 95,2% no GraphWalks para contexto de 256 mil a 1 milhão de tokens.
- O Google relata recusa de 1,98% das tarefas no Terminal-Bench 4.0 e de 0% no Terminal-Bench-Science.
- A avaliação interna de comportamento agêntico apontou, em relação ao Carbon, redução de 43% a 56% em subatendimento e de 13% a 35% em excesso de escopo, conforme o nível de esforço.
- O Google relata 0,09% de ação desalinhada na suíte de segurança agêntica e 99,2% de aprovação na avaliação interna de honestidade.
- No app Gemini, o anúncio destaca a leitura de envios como planilhas, PDFs e fotos, além da integração com informações do Gmail e do Docs.
- O model card informa que o Gemini 4 Neon é adaptado do Gemini 4 Carbon e que arquitetura, dados de treinamento, hardware e software seguem as referências do modelo Carbon.
