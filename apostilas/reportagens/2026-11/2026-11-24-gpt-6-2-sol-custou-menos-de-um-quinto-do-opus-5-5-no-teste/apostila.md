# GPT-6.2 Sol custou menos de um quinto do Opus 5.5 no teste

_2026-11-24 · reportagem_

O GPT-6.2 Sol chega como opção eficiente para o trabalho diário, enquanto o Claude Opus 5.5 é apresentado para trabalho complexo e agentes. Os gráficos da OpenAI favorecem o Sol, mas um teste direto encontrou o Opus 5.5 um pouco mais preciso. Nesse teste, o Sol custou menos de um quinto do Opus 5.5 e terminou em cerca de metade do tempo. Ao ler, você vai entender a diferença entre preço por token e custo por tarefa, conferir os resultados de cada teste e escolher qual modelo usar conforme o risco do trabalho.

## O fato

Em 17 de novembro de 2026, a OpenAI lançou o GPT-6.2 Sol e o GPT-6.2 Astra. O anúncio oficial apresenta o Sol como um modelo eficiente e versátil para tarefas cotidianas. A Astra é voltada aos projetos mais difíceis, com ênfase em trabalho profissional complexo.

O Claude Opus 5.5, da Anthropic, já havia sido lançado em setembro de 2026. Ele é apresentado como um modelo para programação complexa, agentes e trabalho de conhecimento. A comparação com o Sol surgiu porque os gráficos de lançamento da OpenAI colocam o novo modelo à frente do Opus em alguns resultados e com custo menor.

Um teste direto publicado em 21 de novembro de 2026 chegou a um resultado diferente na precisão. O Opus 5.5 acertou um pouco mais, enquanto o Sol teve custo e tempo bem menores. Os dois conjuntos de números podem coexistir porque medem tarefas, configurações e métodos diferentes.

## O contexto

A página oficial da Anthropic registra o lançamento do Claude Opus 5.5 em 22 de setembro de 2026. A empresa o descreve como seu modelo Opus mais capaz, com foco em agentes de longa duração, programação e fluxos profissionais. O modelo tem janela de contexto de 1 milhão de tokens.

A OpenAI lançou Sol e Astra no mesmo dia. A proposta da empresa é dividir o trabalho entre eficiência no uso cotidiano e qualidade máxima em projetos difíceis. Essa distinção importa porque um resultado atribuído à Astra não pode ser usado como prova de desempenho do Sol.

Para o leitor, a comparação envolve mais do que escolher um nome. É preciso observar a qualidade exigida pela tarefa, o custo total de tokens, o tempo de resposta e o impacto de um erro.

Fonte: <https://www.anthropic.com/claude/opus>

## Por que preço por token e custo por tarefa são diferentes

Token é uma unidade de texto processada pelo modelo. A entrada reúne o conteúdo enviado, como instruções e documentos. A saída reúne a resposta gerada, incluindo os tokens de raciocínio registrados no teste. A API cobra separadamente pela entrada e pela saída, com valores por milhão de tokens.

O preço por token é uma tarifa unitária. O custo por tarefa depende da tarifa e da quantidade de tokens usada para concluir o trabalho. Um modelo pode cobrar mais por token e ainda sair mais barato se precisar de muito menos tokens. Na metodologia da Artificial Analysis, o custo por tarefa também considera cache de leitura, cache de escrita, raciocínio e resposta, ponderados pelas avaliações do índice.

O tempo por tarefa também tem duas leituras possíveis. No teste direto, ele foi medido em segundos decorridos. Na Artificial Analysis, corresponde aos tokens de saída divididos pela velocidade de produção, ponderados pelas avaliações. Já a precisão precisa ser interpretada dentro das regras de cada teste. Comparar apenas um desses números esconde o desempenho completo.

Fonte: <https://artificialanalysis.ai/models/comparisons/gpt-6-2-sol-vs-claude-opus-5-5>

## O que a OpenAI anunciou

A OpenAI chama o GPT-6.2 Sol de seu modelo para o trabalho diário. Segundo o anúncio, ele é mais inteligente e eficiente que o GPT-6.1 Sol, permite concluir mais tarefas no mesmo plano pago e funciona em fluxos agenticos de várias etapas. A empresa também destaca escrita clara e colaboração intuitiva.

O Sol mantém os preços de tokens da API do GPT-6.1 Sol. A OpenAI afirma que Sol e Astra produzem melhores resultados em tarefas exigentes usando menos tokens de saída. Essa é a base econômica da proposta: reduzir o consumo ajuda a ampliar a quantidade de trabalho possível dentro de um limite de uso.

Os gráficos de lançamento mostram o Sol ligeiramente à frente do Opus 5.5 em trabalho de agente e programação científica. O Opus permanece ligeiramente à frente no FrontierCode 2.0. O texto do anúncio não menciona Opus 5.5 pelo nome, mas os gráficos incluem essa comparação.

A Astra tem posição diferente. A OpenAI a apresenta para os projetos mais difíceis e atribui a ela avanços em documentos, planilhas, código, design e uso de computador. Esses resultados pertencem à Astra e não devem ser transferidos para o Sol.

Fonte: <https://openai.com/index/introducing-gpt-6-2-astra-sol>

## O que a Anthropic apresenta

O Claude Opus 5.5 é descrito como um modelo híbrido de raciocínio para programação séria e agentes de IA. A Anthropic destaca tarefas de longa duração, bases de código grandes, revisão de código, análise financeira e interpretação de documentos e imagens. A janela de contexto anunciada é de 1 milhão de tokens.

Os preços padrão são US$ 4 por milhão de tokens de entrada e US$ 20 por milhão de tokens de saída. A leitura de cache custa US$ 0,20 por milhão de tokens. A empresa estima que o modelo custe 40% menos para executar que o Opus 5 em cargas típicas cobradas por token. Essa referência é o Opus 5.

O modo rápido do Opus 5.5 oferece velocidade até 2,5 vezes maior e custa US$ 8 por milhão de tokens de entrada e US$ 40 por milhão de tokens de saída. O teste direto entre Sol e Opus 5.5 usou as configurações padrão, então seus tempos não descrevem o modo rápido.

Fonte: <https://www.anthropic.com/claude/opus>

## Como o teste direto foi montado

O teste usou três tarefas: fechamento de mês, biblioteca de cobrança e análise de dados laboratoriais. Foram avaliados GPT-6.2 Sol, GPT-6.2 Astra, Claude Opus 5.5 e Claude Fable 5.2. Cada modelo rodou uma vez por teste, pela API de seu fabricante, nas configurações padrão.

Um script comparou as respostas com um gabarito. As tarefas tinham regras escritas e uma resposta correta por verificação, o que as torna mais estruturadas que os benchmarks dos gráficos da OpenAI. Assim, as pontuações mostram o desempenho em trabalhos detalhados e realistas, mas não validam os números daqueles gráficos.

Para aumentar a dificuldade, as tarefas passaram pelo GPT-5 e foram reforçadas quando ele ficou perto da pontuação máxima. Como referência, o GPT-5 marcou 130 de 173 pontos no fechamento de mês, 41 de 110 na biblioteca de cobrança e 57 de 76 na análise laboratorial.

Cada tarefa tem seu próprio total de pontos. Por isso, uma pontuação de 169 de 173 no fechamento não pode ser lida como a mesma medida de uma pontuação de 76 de 76 no laboratório. O valor indica acerto dentro daquela tarefa específica.

## Fechamento de mês: a única falha do Sol

A tarefa simulou uma empresa de software com sistema de cobrança, contratos, pagamentos, histórico de indisponibilidade e conversas da equipe de 40 clientes. O modelo precisava encontrar faturas incompatíveis com os contratos, calcular créditos por indisponibilidade, aplicar 30 pagamentos e recusar pedidos de colegas que violavam a política da empresa.

O Opus 5.5 marcou 173 de 173 pontos. O Sol marcou 169 de 173. Os quatro pontos perdidos pelo Sol vieram de um único cliente: ele não concedeu um crédito de cerca de US$ 2.400 por uma indisponibilidade ocorrida em outubro. Com isso, os totais do relatório de fechamento também ficaram errados.

O Sol acertou as faturas com preço incorreto e as solicitações que deveriam ser recusadas, como fez o Opus. Ainda assim, o erro omitido teria consequência comercial e contábil em um trabalho real. A pequena diferença na pontuação esconde um problema grande.

Nessa tarefa, o Opus custou US$ 1,24 e levou 238 segundos. O Sol custou US$ 0,20 e levou 106 segundos. A economia foi relevante, mas o teste mostrou que confiança integral exige verificação do crédito e dos totais.

## Biblioteca de cobrança: empate com contas diferentes

A biblioteca de cobrança continha 20 bugs e uma funcionalidade inacabada. A especificação deixava várias regras sem escrever, então o modelo precisava deduzi-las com cerca de 100 registros do sistema antigo. Também precisava evitar a reprodução dos bugs conhecidos desse sistema.

Três testes da própria biblioteca estavam errados. A tarefa exigia que o modelo identificasse esses testes sem editá-los. Os dois modelos alcançaram 110 de 110 pontos: corrigiram os 20 bugs, concluíram a funcionalidade e sinalizaram os três testes incorretos.

O Sol ainda encontrou uma regra que havia derrubado o GPT-6.2 Astra nessa mesma tarefa. O resultado mostra que o nível de esforço e o raciocínio adicional do Opus não acrescentaram acerto neste caso.

O Opus custou US$ 0,97 e levou 211 segundos. O Sol custou US$ 0,16 e levou 94 segundos. Com a mesma pontuação, a diferença ficou na conta e no tempo, dentro do recorte dessa tarefa de programação.

## Dados laboratoriais: empate e vantagem menor de custo

A análise envolveu um estudo de enzimas com 30 amostras e dados bagunçados. Os arquivos de um instrumento usavam um formato que o script de leitura do laboratório não interpretava corretamente. Uma placa de amostras foi inserida girada, um relógio estava sete minutos adiantado e um freezer aquecido estragou parte das amostras.

Opus 5.5 e Sol marcaram 76 de 76 pontos. Foi o teste em que os dois modelos chegaram mais perto em custo e tempo. O Opus custou US$ 0,58 e levou 137 segundos; o Sol custou US$ 0,15 e levou 90 segundos.

O Opus levou cerca de 50% mais tempo nessa tarefa. A vantagem de custo do Sol ficou um pouco abaixo de quatro vezes, contra cerca de seis vezes no fechamento de mês. O motivo é que o Opus usou bem menos tokens no laboratório do que nas outras duas tarefas.

## A comparação independente da Artificial Analysis

A Artificial Analysis compara dez modelos, sendo cinco versões de cada lançamento, com diferentes níveis de esforço e características de inteligência, velocidade e preço. O Intelligence Index v5.0.2 reúne nove avaliações, incluindo trabalho de conhecimento, automação, programação em terminal, engenharia de software, ciência, documentos profissionais e raciocínio.

Na configuração max, o Claude Opus 5.5 alcançou 59 pontos no índice, contra 57 do GPT-6.2 Sol. A diferença de dois pontos não representa dois pontos percentuais de acerto em qualquer tarefa. O índice resume várias avaliações e não substitui o resultado de um trabalho específico.

As avaliações individuais variam. No nível max, o Sol marcou 67,6% no Terminal-Bench-Science 0.1, contra 59,0% do Opus. No FrontierCode-AA 2.0, o Opus marcou 46,9%, contra 44,4% do Sol. Cada porcentagem pertence ao benchmark em que foi medida.

No nível low, a Artificial Analysis registra 1,7 minuto por tarefa para o Sol e 3,0 minutos para o Opus 5.5. O custo por tarefa fica em US$ 0,18 para o Sol e US$ 0,98 para o Opus. Esses valores de custo e tempo usam configurações low, enquanto o resultado de 59 contra 57 foi obtido na configuração max.

Fonte: <https://artificialanalysis.ai/models/comparisons/gpt-6-2-sol-vs-claude-opus-5-5>

## Os números

Os preços de tokens são unitários. Os custos e tempos do teste direto são estimativas ou medições das três tarefas. Nas contagens de saída, os tokens de raciocínio fazem parte do total e não devem ser somados novamente.

- O Sol custa US$ 2 por milhão de tokens de entrada e US$ 10 por milhão de tokens de saída. O Opus 5.5 custa US$ 4 e US$ 20, respectivamente. Na leitura de cache, os valores são US$ 0,10 para o Sol e US$ 0,20 para o Opus, por milhão de tokens.
- Nos gráficos da OpenAI, uma tarefa de agente fica em cerca de US$ 1,30 com o Sol e US$ 17 com o Opus 5.5. A diferença é de cerca de 1.200% mais para o Opus por tarefa. São estimativas do lançamento, não os valores do teste direto.
- No conjunto dos três testes diretos, o custo estimado foi de US$ 0,51 para o Sol e US$ 2,79 para o Opus 5.5. O Sol ficou abaixo de um quinto do custo do Opus nesse conjunto. O valor estimado não representa uma assinatura ou uma fatura de plano pago.
- O tempo total foi de 290 segundos para o Sol e 586 segundos para o Opus 5.5. O Sol terminou em aproximadamente metade do tempo somado. Isso não garante metade do tempo em toda tarefa futura.
- Foram 713.857 tokens de entrada e 21.489 de saída para o Sol, contra 1.752.477 de entrada e 67.205 de saída para o Opus. São quantidades somadas nos três testes e ajudam a explicar custo e tempo, mas não medem qualidade sozinhas.
- No fechamento de mês, o Opus usou 20 turnos, 844.011 tokens de entrada e 28.983 de saída, incluindo 11.038 de raciocínio. O Sol usou 10 turnos, 270.002 de entrada e 8.205 de saída, incluindo 1.506 de raciocínio.
- Na biblioteca de cobrança, o Opus usou 18 turnos, 616.008 tokens de entrada e 22.797 de saída, incluindo 11.944 de raciocínio. O Sol usou 14 turnos, 218.317 de entrada e 6.844 de saída, incluindo 1.655 de raciocínio.
- No laboratório, o Opus usou 17 turnos, 292.458 tokens de entrada e 15.425 de saída, incluindo 3.755 de raciocínio. O Sol usou 14 turnos, 225.538 de entrada e 6.440 de saída, incluindo 373 de raciocínio.

## Linha do tempo

As datas situam o anúncio, o concorrente e o teste que mudou a leitura dos gráficos de lançamento.

- 22 de setembro de 2026: a Anthropic apresentou o Claude Opus 5.5, voltado a programação, agentes e trabalho de conhecimento.
- 17 de novembro de 2026: a OpenAI lançou o GPT-6.2 Astra e o GPT-6.2 Sol, com posições distintas para projetos difíceis e trabalho cotidiano.
- 21 de novembro de 2026: foi publicado o teste direto que comparou os modelos em fechamento de mês, biblioteca de cobrança e análise de dados laboratoriais.

## Como funciona na prática

Exemplo: imagine que uma equipe usa IA para revisar cobranças e produzir relatórios. Esse trabalho pode começar com o Sol quando os resultados passam por revisão e um erro não causa dano imediato. O modelo empatou com o Opus na biblioteca de cobrança e na análise laboratorial, com custo e tempo menores nesses testes.

Se a mesma tarefa envolve crédito a cliente, conciliação de valores ou decisão com grande efeito posterior, o Opus 5.5 pode atuar como checagem final. No fechamento de mês, ele evitou a omissão de um crédito que deixou o relatório do Sol desbalanceado.

Repetir a tarefa com o Sol ajuda a observar consistência. O teste original executou cada modelo uma única vez por tarefa; por isso, a orientação de rodar o mesmo trabalho duas vezes acrescenta uma verificação que não estava na primeira medição.

## Quem ganha e quem perde

O Sol ganha em economia e velocidade no conjunto dos três testes. Ele também preservou a pontuação máxima em dois trabalhos. Para uso frequente, esse perfil favorece tarefas rotineiras de programação e análise, desde que o resultado possa ser verificado.

O Opus 5.5 ganha em precisão no fechamento de mês, a única tarefa em que houve diferença de pontuação. Esse modelo pode ser preferível quando a revisão final precisa pegar uma omissão com consequência financeira ou operacional. Ele perde em custo e tempo nos três testes realizados.

O empate nos outros dois testes impede uma conclusão geral de superioridade. A escolha depende da frequência de uso, do valor do tempo economizado e do custo de corrigir um erro. Uma pequena vantagem de precisão pode valer mais em trabalho sensível; uma grande economia pode pesar mais em tarefas repetíveis.

## O que você pode fazer

A comparação útil acontece no seu trabalho. O procedimento abaixo reaproveita os critérios do teste: mesma tarefa, condições controladas e registro de acerto, tokens, custo e tempo.

1. No seu fluxo de trabalho, escolha uma tarefa com regras escritas e resultado verificável. O resultado esperado é uma referência clara para dizer se cada modelo acertou.
2. No mesmo ambiente e nas mesmas condições, execute a tarefa com Sol e Opus 5.5. Registre precisão, quantidade de tokens, custo e tempo para obter uma comparação equivalente.
3. Na mesma tarefa de baixo impacto, rode o Sol duas vezes. Compare as respostas para verificar se o resultado se mantém antes de ampliar o uso.
4. Na revisão final de um trabalho em que um erro causa grande impacto, use o Opus 5.5 como checagem. O resultado esperado é encontrar omissões antes da entrega.

## O que conferir antes de escolher

Os números respondem a perguntas específicas. Preserve o contexto de cada medição para não transformar um teste em uma promessa geral.

- Cada modelo rodou apenas uma vez por tarefa no teste direto. Os resultados mostram aquelas execuções e não medem a variação entre tentativas.
- As tarefas diretas tinham regras escritas e respostas verificáveis. Elas são mais estruturadas que os benchmarks de lançamento, então não confirmam nem refutam diretamente os gráficos da OpenAI.
- O teste usou configurações padrão. Níveis de esforço diferentes, cache e o modo rápido do Opus 5.5 mudam as condições de custo e tempo.
- Os quatro pontos perdidos pelo Sol estavam concentrados em um crédito omitido. Uma pontuação alta não elimina a necessidade de revisar valores e consequências comerciais.
- Os custos são estimativas baseadas nos preços e no consumo de tokens. Eles não incluem uma comparação completa entre planos de assinatura.
- O tempo medido no teste direto foi o tempo decorrido das execuções. Na Artificial Analysis, velocidade e latência são médias de endpoints nos últimos cinco dias, com benchmarks executados a cada seis horas.
- Os gráficos da OpenAI são materiais de lançamento. A comparação da Artificial Analysis e o teste direto usam métodos próprios e podem chegar a resultados diferentes.
- As avaliações por capacidade variam entre ciência, engenharia, finanças e outras áreas. O vencedor do índice geral pode perder em um benchmark específico.

## Glossário

- Token: unidade de texto processada pelo modelo, usada para medir entrada, saída e cobrança.
- Token de entrada: parte da tarefa enviada ao modelo, como instrução, documento ou registro.
- Token de saída: texto gerado na resposta, incluindo os tokens de raciocínio registrados.
- Token de raciocínio: parte da saída usada para elaborar a resposta antes da apresentação final.
- Custo por tarefa: valor estimado para executar uma tarefa, considerando preços e consumo de tokens.
- Tempo por tarefa: duração atribuída à execução, medida em segundos no teste direto e calculada por velocidade de saída na Artificial Analysis.
- API: interface usada por programas para enviar tarefas ao modelo e receber respostas.
- Turno: uma rodada de interação entre o agente ou modelo e o ambiente da tarefa.
- Agente: sistema que executa trabalho em várias etapas e pode usar ferramentas para concluir uma tarefa.
- Benchmark: teste de referência com regras definidas para comparar capacidades dos modelos.
- Intelligence Index: índice da Artificial Analysis que combina nove avaliações em uma medida agregada de inteligência.
- Nível de esforço: configuração que altera a quantidade de trabalho dedicada à resposta e pode mudar precisão, custo e tempo.
- Fallback: modelo reserva acionado pelo provedor em determinadas condições; o rótulo do resultado precisa ser preservado na comparação.
- Precisão: desempenho diante dos critérios de uma tarefa específica, sem representar garantia de ausência de erros.

## Para onde ir depois

O próximo passo é aplicar a comparação ao trabalho que você realmente executa. O objetivo é formar um critério de escolha baseado em resultado, risco, custo e tempo.

- Comece pelo Sol em uma tarefa de baixo impacto e execute a mesma tarefa duas vezes para observar consistência.
- Reserve o Opus 5.5 para a revisão final de trabalhos em que um erro tem grande consequência.
- Registre precisão, tokens, custo e tempo nas duas execuções para comparar o seu uso com os números desta apostila.
- Amplie a prática para outra tarefa da sua rotina e mantenha a escolha do modelo vinculada ao impacto do erro, sem transformar um resultado isolado em regra universal.

## Além do vídeo

- No Agents' Last Exam, o GPT-6.2 Astra ficou 5,2 pontos acima do GPT-6 Astra por menos de um terço do custo e 5,5 pontos acima do Claude Fable 5.2 a 5% do custo.
- No Terminal-Bench-Science 0.1, o GPT-6.2 Astra superou o GPT-6 Astra em 9 pontos percentuais, com menos de um terço do custo.
- No Harvey LAB-AA v1.1, o GPT-6.2 Astra mais que dobrou a taxa de aprovação do Claude Fable 5.2 a cerca de um sexto do custo.
- No AA-3D, o GPT-6.2 Astra somou 1.318 pontos Elo, seguido pelo Claude Fable 5.2 com 1.271 e pelo GPT-6.2 Sol com 1.259.
- Na avaliação LifeVal, o GPT-6.2 Sol superou o GPT-6 Astra a cerca de um sétimo do custo.
- O Claude Opus 5.5 está disponível para usuários Pro, Max, Ultra, Team e Enterprise do Claude, além de desenvolvedores no Claude Platform, Amazon Web Services, Google Cloud e Microsoft Foundry.
- A inferência exclusiva nos Estados Unidos para o Opus 5.5 custa 1,1 vez os preços de entrada e saída.
- A OpenAI informa que GPT-6.2 Astra e Sol atingem o limite Critical de cibersegurança de seu Preparedness Framework e foram lançados com salvaguardas mais rígidas para assistência de maior risco.
- Na comparação da Artificial Analysis, os dez modelos têm janela de contexto de 1 milhão de tokens, aceitam texto e imagem e produzem texto.
- O histórico apresentado inclui vitórias do Opus 5.5 sobre Qwen4-Max e Claude Fable 5.2, além de derrota para GPT-6.1 Terra em três testes.
- No GDPval v2 interno, o GPT-6.2 Astra avançou 6,2 pontos percentuais em relação ao GPT-6 Astra usando 22% menos tokens de saída; o GPT-6.2 Sol avançou 5,3 pontos em relação ao GPT-6.1 Sol.
- Os preços da API do GPT-6.2 Astra são US$ 8 por milhão de tokens de entrada, US$ 0,40 para entrada em cache e US$ 40 por milhão de tokens de saída.
