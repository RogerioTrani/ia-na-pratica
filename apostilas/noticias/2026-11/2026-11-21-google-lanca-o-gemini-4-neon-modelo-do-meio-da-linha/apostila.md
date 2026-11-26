# Google lança o Gemini 4 Neon, modelo do meio da linha

_2026-11-21 · noticia_

O Gemini 4 Neon chegou em 18 de novembro de 2026 como o modelo intermediário da linha Gemini 4, com foco em programação, análise de dados e trabalho profissional complexo. Você vai entender a janela de 1 milhão de tokens, os preços da API, os quatro níveis de pensamento e o significado dos resultados divulgados. Também verá onde o modelo está disponível, como ele foi usado no Antigravity e qual é o alcance do teste de sete pedidos. A leitura explica como avaliar custo por tarefa, benchmarks e proteções de segurança antes de usar o Neon em um fluxo real. Ao final, você terá um caminho para testar um pedido complexo e conferir o resultado.

## O fato

Em 18 de novembro de 2026, o Google apresentou o Gemini 4 Neon, modelo intermediário da nova linha Gemini 4. O anúncio posiciona o Neon em engenharia de software, trabalho de conhecimento e fluxos científicos, com conclusão rápida de tarefas complexas do início ao fim.

O lançamento cobre a Gemini API no Google AI Studio e no Android Studio na faixa paga, o Gemini for business por API e menu de modelos, o Google Antigravity para assinantes pagos Google AI Pro e Ultra e o app Gemini para assinantes Pro e Ultra. A disponibilidade varia conforme a superfície e o plano.

Um teste prático de sete pedidos foi feito no Antigravity e começou por uma landing page. Os resultados desse teste ajudam a entender a experiência de uso, mas têm um recorte diferente dos benchmarks divulgados no anúncio.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## Por que isso importa

Programação e análise costumam exigir várias ações ligadas: ler arquivos, localizar informações, usar ferramentas, corrigir o curso e produzir uma entrega. Um agente executa esse fluxo ao longo de etapas, em vez de devolver apenas uma resposta isolada. O Neon foi apresentado para sustentar esse tipo de trabalho longo.

Na linha Gemini 4, o Carbon trata dos projetos mais difíceis e de longo horizonte, o Hydrogen cuida da execução rápida do cotidiano e o Neon equilibra profundidade e eficiência. A proposta do intermediário é atender fluxos complexos e frequentes com mais velocidade e menor custo por tarefa.

Para quem trabalha com código ou dados, a mudança prática é poder tratar um conjunto de materiais como parte da mesma tarefa. Isso reduz a necessidade de explicar o contexto em pedidos separados e permite acompanhar o modelo enquanto ele avança.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## A janela de contexto de 1 milhão de tokens

Token é uma unidade de texto processada pelo modelo. A janela de contexto é a quantidade de informação que ele consegue considerar junta durante uma tarefa. No Neon, essa janela chega a 1 milhão de tokens.

O Google afirma que o modelo consegue sintetizar planilhas, PDFs, gráficos, áudios e vídeos dentro dessa mesma janela e transformar esses materiais em entregas estruturadas. O benefício aparece quando a resposta depende de cruzar informações que estavam espalhadas por formatos diferentes.

Imagine que uma pessoa recebe uma planilha, um PDF e um gráfico sobre o mesmo assunto. Ela pode reunir os três no pedido e solicitar uma análise que relacione os dados. O modelo trabalha sobre o conjunto enviado, e a pessoa precisa conferir se as conclusões correspondem aos arquivos.

Uma janela maior aumenta o volume que cabe na mesma análise. A conferência do resultado continua necessária, principalmente quando há números, documentos ou decisões envolvidas.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## Preço na API e custo por tarefa

Na API do Gemini, cada milhão de tokens de entrada custa US$ 3 e cada milhão de tokens de saída custa US$ 15. A entrada em cache custa US$ 0,15 por milhão de tokens, um desconto de 95% sobre a entrada normal.

Cache é o reaproveitamento de conteúdo de entrada já processado. Quando esse reaproveitamento se aplica, a cobrança fica menor. Para estimar uma tarefa, é preciso considerar tanto a entrada e a saída quanto a quantidade de passos e de raciocínio que ela exige.

O custo por token e o custo por tarefa são medidas diferentes. No nível high padrão, o Google relata 32% menos custo por tarefa que o Carbon. Em Vals Index e Agent Arena, no nível high, relata cerca de 50% a 80% menos que modelos fronteira concorrentes. No nível xhigh, relata 36% ou mais de economia por tarefa em relação aos concorrentes em sua configuração mais alta.

Esses percentuais descrevem as comparações divulgadas pelo Google. Eles ajudam a dimensionar o uso, mas não definem o preço de toda tarefa: o volume de saída e o esforço escolhido mudam a conta.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## Os quatro níveis de pensamento

O Neon tem quatro níveis que ajustam gradualmente a inteligência aplicada e o gasto de tokens. O high é a configuração padrão. O xhigh acrescenta raciocínio mais profundo e em várias etapas para os trabalhos de engenharia, análise e ciência considerados mais difíceis.

A escolha do nível muda o equilíbrio entre esforço e custo. Uma tarefa com muitas restrições pode exigir mais raciocínio; uma execução mais direta pode começar no padrão. O resultado de uma configuração não deve ser transferido automaticamente para outra.

O Google também destaca o segundo lugar do Neon em steerability no Agent Arena Index. O termo descreve a capacidade de aceitar correções do usuário no meio da tarefa. Na prática, isso importa quando o pedido precisa ser ajustado enquanto o agente ainda está trabalhando.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## Programação, agentes e ciência

O Neon foi projetado para depuração e refatoração em vários arquivos e repositórios, com edições direcionadas. O anúncio descreve fluxos longos com muitas ferramentas, nos quais o modelo mantém o desempenho do início ao fim.

No Antigravity, ele pode atuar sozinho ou como orquestrador de subagentes Hydrogen em paralelo. O Google relata menos leituras redundantes de arquivos, compartilhamento do progresso durante o trabalho e compactação confiável de contexto em sessões longas.

O ambiente influencia o resultado. No SWE-sweep, o Neon marcou 12,8% no harness mini-SWE e 39,0% no Google Antigravity. O anúncio usa essa diferença para mostrar o que o harness do Antigravity acrescenta ao desempenho do modelo.

Na parte científica, o Google relata 70,5% no Terminal-Bench Science, 84,0% no RiemannBench e 71,3% no HLE-Diamond. Cada teste cobre um conjunto próprio de problemas de análise quantitativa, matemática ou pesquisa técnica.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## Análise, pesquisa e automação

No trabalho analítico, o Neon recebe materiais profissionais e os transforma em entregas estruturadas. O Google cita resultados em pesquisa jurídica, tributos, finanças, contabilidade, modelagem de planilhas e cumprimento de restrições complexas.

No app Gemini, o anúncio destaca a leitura de planilhas, PDFs e fotos, a produção de relatórios e resumos e o uso de detalhes do Gmail e do Docs. Também descreve pesquisas na web para comparar preços ou reunir dados recentes em um briefing.

O app foi posicionado para tarefas demoradas, como analisar faturas para entender um aumento de consumo ou cruzar recibos e documentos na tentativa de negociar um reembolso. Esses exemplos mostram o uso de vários documentos em uma mesma solicitação.

A automação aparece em testes com ferramentas e simulações de negócios. O AutomationBench mede tarefas de automação, enquanto o Vending-Bench 2 simula a operação de um negócio por um longo período. Os resultados desses testes têm objetivos diferentes dos de uma conversa comum.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## Os exemplos no Antigravity

O Google mostra o Neon usando Blender MCP para construir uma bancada de laboratório em 3D fotorrealista. A cena associa chamas de Bunsen ao Gemini 4 Carbon e ao Hydrogen, e tubos de descarga de gás de alta tensão ao Argon e ao Neon. Outro exemplo reconstruiu em 3D o estudo de Alan Turing em 1936, no King’s College, em Cambridge, da capela até a Room X.8, com uma Universal Turing Machine funcionando sobre a mesa.

Em um projeto de esqui, o Neon criou do zero um simulador WebGL2 de primeira pessoa com terreno real de Mont Blanc e Chamonix. O trabalho reuniu 10.200 linhas de shaders personalizados, física de esqui a 120 Hz em seis rotas alpinas, rastros de curvas, avalanches de placas e áudio espacial Web Audio, sem recursos prontos.

Com o recurso de enxame, um grupo de agentes do Neon transformou uma imagem em um Google Sheet de 100.000 células. A planilha ficou sem imagens incorporadas e sem Apps Script, usando mais de 500.000 fórmulas ativas para detecção de bordas, profundidade em 3D e reiluminação da cena em seis modos interativos.

Todos esses casos aconteceram no Antigravity e envolveram ferramentas, arquivos ou vários agentes. Ao avaliar um projeto semelhante, vale separar a contribuição do modelo do que o ambiente e os recursos disponíveis acrescentaram.

```
/swarm
```

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## O teste de sete pedidos

O teste prático usou o Antigravity e fez sete pedidos ao Gemini 4 Neon. O primeiro foi uma landing page, seguido por outros projetos. Cada pedido rodou uma única vez, sem segunda tentativa.

Esse formato permite observar como o modelo se comportou na primeira execução daquelas solicitações específicas. O conjunto de sete pedidos serve como relato de experiência e não substitui uma avaliação com muitos casos, repositórios e critérios diferentes.

## Segurança e comportamento

Prompt injection é um ataque em que instruções maliciosas aparecem em páginas, e-mails, documentos ou código que o modelo acessa. O Google afirma que o Neon mantém proteções comparáveis às do Carbon contra uso indevido grave e prompt injection.

No benchmark IPI da Gray Swan, com salvaguardas em tempo real e no nível mais alto de pensamento, o Neon resistiu a todos os ataques avaliados, com 0% de sucesso de ataque. O anúncio diz que esse patamar também foi alcançado apenas por outros modelos Gemini. O resultado se refere àquele benchmark e àquela configuração.

Nos testes internos de comportamento, o Google relata 0,0% de trapaça no Terminal-Bench 4.0 e atalhos em 2,45% das tarefas na avaliação interna de trapaça em código. Também relata, em relação ao Carbon, redução do subatendimento em 43% a 56% e da extrapolação em 13% a 35%, conforme o nível de esforço.

Com as salvaguardas contra uso indevido em cibersegurança e biossegurança, as taxas de recusa foram de 1,98% das tarefas no Terminal-Bench 4.0 e 0% no Terminal-Bench-Science. O Google ainda afirma ter registrado sua menor taxa de fabricação até agora nos testes internos do Antigravity. Esses resultados orientam a avaliação de risco; a revisão humana continua necessária em código, dados e ações com consequências reais.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## Gemini 4 Neon for cyber

O Gemini 4 Neon for cyber é uma variante voltada à defesa cibernética. O anúncio de 18 de novembro informou que ela seria liberada nos dias seguintes, primeiro para defensores confiáveis no Fairwind Program. As condições dessa variante não devem ser transferidas para o Neon comum.

Na geração de código seguro, o Google atribui ao Gemini 4 Neon desempenho superior ao Carbon nos desafios fáceis, médios e difíceis do AutoBaxBench, com 76% no nível difícil. No WebExploitBench v1.2, relata 51,26% e metade do custo de modelos grandes concorrentes.

O ciclo de defesa inclui encontrar vulnerabilidades, validar o risco por exploração e corrigir a causa. Ao apresentar o Neon for cyber, o Google diz que ele entrega desempenho de fronteira nesse ciclo. Nos testes citados em seguida, atribuídos ao Neon, o modelo marcou 90,5% no SEC-bench Pro, com cerca de metade do custo por desafio; alcançou desempenho de fronteira no ExploitGym usando metade dos tokens do Carbon; e chegou a 70,7% no CWE-bench v2, da Collinear, uma alta de 3,4% sobre o Carbon.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## Como funciona o Fairwind Program

O Fairwind Program oferece acesso antecipado a modelos de defesa cibernética para parceiros confiáveis. A prioridade inclui governos, operadores de infraestrutura crítica e plataformas de tecnologia, com foco em proteger serviços essenciais. Parceiros selecionados podem usar os modelos Gemini for cyber sozinhos ou com o CodeMender, um agente de segurança de código para pesquisa e correção de vulnerabilidades.

O uso permitido abrange simulação autorizada de ameaças, engenharia reversa e análise de malware para defesa e pesquisa acadêmica. A criação de malware não é permitida. As organizações passam por due diligence e concordam com autenticação por usuário, MFA resistente a phishing e controles de acesso aplicáveis.

O acesso ao Gemini for cyber fica restrito a equipes internas de segurança cibernética, resposta a incidentes ou testes de intrusão, e o uso dos funcionários precisa ser rastreado. Parceiros aprovados não podem compartilhar, redistribuir ou vender o acesso. Para solicitar entrada, a orientação é falar com a equipe da conta Google Cloud. Organizações fora do programa podem usar o CodeMender com modelos publicamente disponíveis e outras soluções do Google AI Threat Defense.

Fonte: <https://deepmind.google/fairwind-program/>

## Os números

- 1 milhão de tokens é a janela de contexto máxima informada para reunir os materiais de uma tarefa; ela não define a quantidade de páginas nem o tamanho da saída.
- US$ 3 por milhão de tokens de entrada, US$ 15 por milhão de saída e US$ 0,15 por milhão de entrada em cache são os preços divulgados para a API; o cache representa 95% de desconto sobre a entrada normal.
- 65,2% no Terminal-Bench 4.1 e 46,2% no FrontierCode 2.0 são resultados de testes de código diferentes; o segundo foi obtido na configuração high padrão.
- 58,6 pontos no Artificial Analysis Coding Agent Index colocaram o Neon em primeiro lugar nessa avaliação de agentes de programação.
- 70,9% no Vals Index corresponderam ao segundo lugar nesse ranking.
- 70,5% no Terminal-Bench Science, 84,0% no RiemannBench e 71,3% no HLE-Diamond são resultados de avaliações científicas e matemáticas com problemas próprios.
- 73,5% no Chartography medem leitura de gráficos profissionais densos; 75,8% no Agents' Last Exam v1.1 ficaram em nível equiparado ao de modelos líderes.
- O Neon ficou em primeiro lugar no Legal Research Bench e no Tax Agent Bench, além de liderar a maioria dos benchmarks da Surge AI em finanças, contabilidade, modelagem de planilhas e cumprimento de restrições complexas.
- 56,3% no AutomationBench, da Zapier, deram o primeiro lugar em automação; US$ 16.843 no Vending-Bench 2, da Andon Labs, deram o primeiro geral em uma simulação de operação de negócio.
- 12,8% no harness mini-SWE e 39,0% no Google Antigravity mostram a diferença entre executar o SWE-sweep em ambientes diferentes.
- A economia divulgada por tarefa foi de 32% em relação ao Carbon no high padrão, cerca de 50% a 80% em relação a concorrentes fronteira no high, no Vals Index e no Agent Arena, e 36% ou mais no xhigh em relação à configuração mais alta dos concorrentes.
- Sete pedidos executados uma única vez no Antigravity descrevem o teste prático; não formam uma amostra para prever o resultado de outras tarefas.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## O que muda para você

Quem desenvolve ou analisa dados pode reunir mais contexto em um pedido, escolher o nível de pensamento e acompanhar o custo da tarefa. O Neon também foi posicionado para trabalho frequente e complexo, em que profundidade e eficiência precisam coexistir.

Imagine que você precisa produzir um relatório a partir de uma planilha, um PDF e um gráfico. O pedido pode reunir os arquivos, explicar a pergunta e definir a estrutura da entrega. O modelo trabalha sobre esse conjunto e produz um resultado para revisão.

Se a tarefa se repetir com conteúdo semelhante, o cache pode reduzir a cobrança da entrada na API. Antes de adotar o fluxo, compare o resultado com os documentos e acompanhe os tokens usados para entender o custo real do seu caso.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## O que fazer hoje

1. Escolha o acesso adequado: assinantes Google AI Pro e Ultra podem usar o app Gemini ou o Antigravity; quem vai usar a API paga pode abrir o Google AI Studio ou o Android Studio. O resultado esperado é encontrar o Gemini 4 Neon na superfície correspondente ao seu plano.
2. Defina uma tarefa complexa no ambiente escolhido, com um objetivo claro e uma entrega reconhecível. O resultado esperado é saber o que você vai conferir quando o modelo terminar.
3. Reúna os materiais necessários, como planilhas, PDFs, gráficos, áudios ou vídeos, e organize-os para o mesmo pedido. O resultado esperado é fornecer o contexto sem dividir a tarefa em solicitações desconectadas.
4. Escreva o pedido com objetivo, materiais, etapas desejadas e formato final. O resultado esperado é dar ao modelo uma direção que permita produzir uma entrega estruturada.
5. Execute o pedido uma vez e registre o que aconteceu, incluindo correções e ferramentas usadas. O resultado esperado é formar um caso comparável ao teste prático de primeira execução.
6. Confira fatos, números, arquivos alterados e código antes de usar a entrega. O resultado esperado é identificar o que está correto e o que ainda precisa de revisão humana.
7. Se estiver usando a API, acompanhe entrada, saída e entrada em cache da tarefa. O resultado esperado é conseguir estimar o custo por tarefa, além do preço por milhão de tokens.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## O que conferir

- Confira o plano e a superfície antes de procurar o modelo: o acesso ao Antigravity é para assinantes pagos Google AI Pro e Ultra, e a API paga aparece no Google AI Studio e no Android Studio.
- Trate a janela de 1 milhão de tokens como capacidade de contexto, não como promessa de número de arquivos, páginas ou tamanho de resposta.
- Separe preço por token de custo por tarefa: níveis de pensamento, quantidade de saída e passos mudam a cobrança final.
- Ao usar cache, verifique se a entrada da sua tarefa se enquadra no uso de cached input tokens antes de aplicar o preço reduzido à estimativa.
- Compare benchmarks pelo teste, configuração e comparação indicados; percentuais de avaliações diferentes não medem a mesma capacidade.
- Mantenha o recorte do teste de sete pedidos: ele relata a primeira execução daquelas solicitações no Antigravity e não garante o mesmo resultado em outro projeto.
- Separe modelo e harness ao interpretar o SWE-sweep, porque o resultado mudou entre o mini-SWE e o Google Antigravity.
- Use os resultados internos de segurança como evidência daquele teste; eles não substituem revisão humana em código, dados sensíveis ou ações externas.
- Considere prompt injection quando o modelo ler páginas, e-mails, documentos ou código, mesmo com as salvaguardas descritas no anúncio.
- Mantenha o Gemini 4 Neon for cyber separado do Neon comum: a variante tem foco defensivo e distribuição controlada.
- Para atividades cibernéticas no Fairwind Program, confira autorização, finalidade defensiva, autenticação, MFA e rastreamento de acesso; a criação de malware não é permitida.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## Glossário

- Token: unidade de texto processada e contabilizada pelo modelo.
- Janela de contexto: quantidade de informação que o modelo consegue considerar junta durante uma tarefa.
- API: interface que permite usar o modelo dentro de um programa ou serviço.
- Cached input tokens: tokens de entrada reaproveitados de processamento anterior e cobrados com tarifa reduzida quando o cache se aplica.
- Benchmark: teste padronizado usado para medir um tipo específico de desempenho.
- Fronteira de Pareto: conjunto de opções em que melhorar uma medida exige abrir mão de outra; no caso, ajuda a comparar capacidade e custo.
- Nível de pensamento: configuração que ajusta a profundidade do raciocínio e o gasto de tokens.
- Agente: modelo que executa uma tarefa em etapas, usando ferramentas e ajustando o trabalho conforme avança.
- Harness: ambiente que organiza ferramentas, arquivos, execução e controle ao redor do modelo.
- Orquestrador: agente que distribui e coordena o trabalho de outros agentes.
- Compactação de contexto: redução do histórico mantido para continuar uma sessão longa sem perder o necessário para a tarefa.
- Prompt injection: tentativa de inserir instruções maliciosas em conteúdo que o modelo vai ler ou usar.
- Alinhamento: comportamento do modelo de acordo com instruções, limites e objetivos pretendidos.
- Steerability: capacidade de seguir correções do usuário durante a execução.
- Subatendimento: situação em que o agente deixa de fazer parte necessária do trabalho solicitado.
- Extrapolação: situação em que o agente ultrapassa o escopo autorizado pelo usuário.
- Fabricação: apresentação de informação como verdadeira sem sustentação.
- MFA resistente a phishing: autenticação em vários fatores projetada para dificultar ataques que roubam credenciais.
- Uso dual: atividade que pode servir à defesa e também causar dano, por isso exige autorização e finalidade clara.
- MCP: protocolo que permite conectar modelos a ferramentas e fontes de dados.
- Shader: programa que controla como imagens e cenas são renderizadas.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## Para onde ir depois

- Para testar pela API paga, abra https://aistudio.google.com/prompts/new_chat?model=gemini-4-neon e trabalhe em uma tarefa real com materiais e entrega definidos.
- Se você assina Google AI Pro ou Ultra, pratique no app Gemini ou abra https://antigravity.google/ para testar o Neon no ambiente usado nos exemplos.
- Para conhecer a integração com o Antigravity, leia https://antigravity.google/blog/gemini-4-neon-in-google-antigravity/ e observe como o harness participa do fluxo.
- Antes de usar o modelo em produção, leia o model card e o relatório de segurança citados no anúncio oficial e pratique a revisão do resultado.
- Se sua organização atua com defesa cibernética, consulte https://deepmind.google/fairwind-program/ e, sendo elegível, fale com a equipe da conta Google Cloud.

Fonte: <https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/>

## Além do vídeo

- O Neon marcou 61 pontos e ficou em terceiro lugar no Artificial Analysis Intelligence Index no nível xhigh.
- O Neon estreou em segundo lugar no Agent Arena Index, com 1.336 pontos em mais de 4.200 sessões reais de agentes.
- A taxa de ação desalinhada foi de 0,09% na suíte interna de segurança de agentes, e a aprovação na avaliação interna de honestidade de agentes foi de 99,2%.
- Quando acessado diretamente como modelo gerenciado no Gemini for business, o Gemini for cyber do Fairwind Program oferece retenção zero de dados.
