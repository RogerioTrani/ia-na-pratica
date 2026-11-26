# Fable 5.2 amplia acesso, mas premia quem sabe pedir

_2026-11-15 · noticia_

Em 9 de novembro de 2026, a Anthropic apresentou o Claude Fable 5.2 e o Claude Mythos 5.2 com avanços em programação, raciocínio e visão. O Fable 5.2 ficou aberto a todos os usuários no Claude, no Claude Code e na Claude Platform, enquanto o Mythos 5.2 mantém acesso restrito a programas de verificação e a clientes Claude Enterprise. Esta apostila explica os preços, os níveis de esforço e os exemplos de sistema operacional, hardware, jogos e robótica divulgados pela empresa. Você também vai aprender a separar resultados de benchmark de promessas de uso e a escolher o modelo conforme a tarefa. Depois da leitura, terá um caminho para formular objetivos, limites e critérios de sucesso, além de avaliar a entrega.

## O fato

Em 9 de novembro de 2026, a Anthropic anunciou o Claude Fable 5.2 e o Claude Mythos 5.2. A empresa descreve melhorias em programação, raciocínio e visão e posiciona os modelos para desafios técnicos abertos e ambiciosos.

O Claude Fable 5.2 está disponível para todos os usuários no Claude, no Claude Code e na Claude Platform. O Claude Mythos 5.2 segue restrito a aprovados nos programas Cyber e Life Sciences Verification e a clientes Claude Enterprise.

A recomendação de uso da Anthropic começa pelo Claude Opus 5.5 nas tarefas cotidianas de programação e conhecimento. A empresa orienta migrar para o Fable 5.2 quando o escopo e a complexidade exigirem mais capacidade.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Por que isso importa

Os exemplos do anúncio envolvem trabalho coordenado por muitos agentes, projetos de longa duração e entregas que exigem teste e revisão. O acesso mais amplo reduz uma barreira de entrada, mas deixa outra para quem quer usar o modelo: explicar o que precisa ser feito.

Um prompt é a instrução que orienta o modelo. Um texto curto pode transmitir a intenção principal, mas o trabalho ainda depende de objetivos claros, limites conhecidos e critérios de sucesso. A Anthropic afirma que o Fable 5.2 produz resultados de qualidade mesmo com pedidos ambíguos; os relatos publicados também incluem orientação humana.

A hipótese apresentada é que o gargalo passe da execução técnica para a formulação e a avaliação. Quem consegue traduzir uma ideia em instruções verificáveis ganha autonomia. Quem não consegue pode depender de outra pessoa para orientar a IA e revisar o resultado.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Fable e Mythos: dois nomes, um modelo

A Anthropic informa que Claude Fable e Claude Mythos usam o mesmo modelo subjacente. A diferença anunciada está no acesso e nas salvaguardas, não em uma arquitetura separada.

O Fable 5.2 tem salvaguardas fortes de cibersegurança e biologia para reduzir o risco de uso indevido. Essas proteções permitem que a empresa o ofereça a todos os usuários.

O Mythos 5.2 destina-se a aplicações benéficas nessas áreas. Organizações interessadas em pesquisa de cibersegurança ou biomédica podem solicitar acesso pelos programas Life Sciences e Cyber Verification. O produto também é oferecido a clientes Claude Enterprise.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Onde usar o Claude Fable 5.2

O acesso direto está disponível em https://claude.ai, no Claude Code e na Claude Platform, em https://claude.com. A informação de lançamento também inclui AWS, Google Cloud e Azure.

O identificador de modelo informado é claude-fable-5-2. Ao usar uma integração que peça esse identificador, copie o valor exatamente para selecionar o Fable 5.2.

Nos planos Pro e Team, o lançamento contempla até 50% dos limites semanais e até 3 resets extras na semana de lançamento. O benefício dos resets extras pertence especificamente à semana de lançamento.

```
claude-fable-5-2
```

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Preço, tokens e velocidade

Na API, o Fable 5.2 custa US$ 8 por milhão de tokens de entrada e US$ 40 por milhão de tokens de saída. O Fast Mode custa US$ 16 e US$ 80, respectivamente, e acelera a geração de tokens em até 2,5 vezes.

Token é uma unidade de texto processada pelo modelo. A entrada é o conteúdo enviado para ele; a saída é o conteúdo gerado. Como as duas direções têm preços diferentes, o custo depende da quantidade usada em cada uma.

Um milhão de tokens de entrada custa US$ 8 no modo padrão, e um milhão de tokens de saída custa US$ 40. O Fast Mode dobra o preço por milhão de tokens nas duas direções. Esses valores não representam o preço fixo de uma resposta ou de um projeto.

O anúncio também informa geração de saída até 30% mais rápida que a do Fable 5.1 e do Mythos 5.1. Essa comparação é diferente da aceleração de até 2,5 vezes do Fast Mode, que se refere à geração de tokens.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Esforço, Advisor e Orchestrator

Medium é o nível de esforço padrão no Claude e no Claude Code. O usuário pode ajustar para High, Xhigh ou Max. A Anthropic relata que, em Medium, o Fable 5.2 conclui tarefas desafiadoras com menos tokens que o Fable 5.1.

O Fable 5.2 também pode atuar como Advisor. Nessa função, modelos Haiku, Sonnet ou Opus o consultam para resolver problemas mais difíceis.

Como Orchestrator, o Fable 5.2 delega tarefas mais simples a modelos menores. A escolha entre consultar e delegar organiza o trabalho entre modelos com capacidades diferentes.

Para a maioria das tarefas, a recomendação oficial continua sendo começar com Opus 5.5. O usuário pode subir para Fable ou Mythos em trabalhos complexos ou descer para Sonnet 5.5 e Haiku 5.5 quando a tarefa permitir.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Um sistema operacional feito por mais de 1.000 subagentes

Em um experimento interno, um engenheiro da Anthropic pediu ao Fable 5.2 que projetasse um protótipo de sistema operacional. O trabalho começou em uma pasta vazia. O modelo coordenou mais de 1.000 subagentes, que escreveram, testaram e revisaram código por oito dias.

O sistema produzido inicializa em um laptop. Ele tem um núcleo que executa a máquina, drivers para disco, teclado e rede, armazenamento permanente de arquivos, janelas, tela de login, instalador e funcionalidades integradas do Claude.

Subagentes são agentes que recebem partes do trabalho e podem executá-las em paralelo. Esse caso mostra a escala da coordenação relatada pela empresa. Oito dias e mais de 1.000 subagentes descrevem esse experimento específico e servem como demonstração de alto nível, não como expectativa para qualquer projeto.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Três placas eletrônicas a partir de um parágrafo

O exemplo da Diode relata a criação de três placas eletrônicas a partir de um prompt de um parágrafo. É o caso mais direto do anúncio para ligar uma intenção curta a um resultado de hardware.

Uma placa eletrônica é uma entrega física. O projeto precisa transformar a intenção em uma definição verificável, e o resultado precisa ser avaliado como hardware. Por isso, um parágrafo pode resumir o objetivo sem substituir as etapas de projeto, construção e validação.

O valor didático desse exemplo está na formulação: o ponto de partida foi enxuto. A execução relatada não deve ser lida como prova de que qualquer pedido curto leva ao mesmo resultado.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Jogos, cenas 3D e robótica

A Unity relata que o Fable 5.2 se destacou na criação de cenas 3D do zero e na reconstrução de experiências a partir de referências visuais. O relato também destaca a iteração em tarefas difíceis de desenvolvimento de jogos.

O anúncio mostra robôs físicos controlados em vídeo e registra 64,9% no RoboDojo Sim. A execução desse benchmark foi interna e usou o maior esforço disponível.

Os 64,9% são uma pontuação no RoboDojo Sim. Eles não representam uma taxa de acerto universal em robôs físicos. A demonstração em vídeo e o resultado de benchmark são evidências diferentes, cada uma com seu próprio escopo.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Outros resultados relatados

A Anthropic afirma que mais de 90% das alterações incorporadas à sua base principal de código são escritas pelo Claude, com orientação humana. A empresa também relata correção de bugs persistentes em minutos e otimização de desempenho em seus serviços.

Uma equipe de agentes usando uma versão anterior do Fable 5.2 migrou um serviço crítico de produção de Python para Rust. O serviço ficou mais eficiente e confiável, e passou a iniciar cerca de 26 vezes mais rápido. O resultado pertence a esse serviço e a essa migração.

Os relatos publicados no anúncio incluem projetos que estavam em andamento há semanas e foram concluídos em dias, refinamento de ideias abertas e coordenação de modelos menores. Em um teste de SQL da Oracle, o SQL gerado pelo modelo retornou os resultados esperados; o SQL de dois outros modelos também rodou, mas somou valores incorretamente e produziu números de 5 a 8 vezes os valores esperados.

A Uber relata uma auditoria de segurança de 10 a 12 horas com cerca de 170 agentes revisores, que resultou em um relatório, pedidos de correção e uma proposta de política. Outro depoimento publicado no anúncio relata a criação de um hipervisor em uma única sessão, com mais de 3.500 provas verificadas por máquina. A Anthropic também registra a solução de dois problemas abertos da física de buracos negros e a formalização da prova do Último Teorema de Fermat em 30 horas. Esses são resultados relatados pela empresa e por clientes, sem garantia de repetição em outras tarefas.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Os números

Cada porcentagem ou nota abaixo pertence a um benchmark específico. O valor precisa ser lido com o esforço usado, as ferramentas disponíveis e o objeto do teste. Uma pontuação alta em programação não permite concluir desempenho equivalente em robótica ou conhecimento.

A Anthropic informa que os resultados de Fable 5.2, Fable 5.1 e Opus 5.5 usam salvaguardas, salvo indicação contrária. A tabela também registra o maior esforço disponível de cada modelo, a menos que o teste especifique outro nível.

- FrontierCode 2.0: o Fable 5.2 marcou 49,1% com Xhigh effort. O benchmark mede se as alterações de código seriam aceitas pelos mantenedores de repositórios abertos; não mede a qualidade de todo software.
- Custo no FrontierCode 2.0: em High effort, o Fable 5.2 marcou 45,3% contra 45,5% do Opus 5.5 em Max effort, por cerca de metade do custo por tarefa, segundo a Anthropic.
- WANDR: em Medium effort, o Fable 5.2 igualou a melhor pontuação do Opus 5.5 por cerca de 40% do custo por tarefa. O benchmark avalia agentes em tarefas de coleta de dados em larga escala.
- BenchCAD 2.1: o Fable 5.2 marcou 83,5 em Max effort, contra 65,3 do Opus 5.5 e 44,4 do Fable 5.1. A nota vai de 0 a 100 e avalia a proximidade de projetos de hardware com geometrias e circuitos de referência.
- Humanity's Last Exam: em Low effort, o Fable 5.2 igualou a melhor pontuação do Opus 5.5 por menos de um décimo do custo por tarefa. O teste cobre conhecimento acadêmico e raciocínio de nível especializado, com ferramentas.
- Chartography: em Medium effort, o Fable 5.2 marcou 66,4% contra 64,4% do Opus 5.5 em Max effort, por menos de um décimo do custo por tarefa. O teste avalia leitura de gráficos e figuras sem ferramentas.
- RoboDojo Sim: o Fable 5.2 marcou 64,9%, contra 39,4% do Opus 5.5 e 27,6% do Fable 5.1. O resultado usa o maior esforço disponível e veio de uma execução interna.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## O que muda para você

Imagine que você precisa reorganizar um serviço de software e quer delegar a parte técnica à IA. O primeiro movimento é definir o objetivo, os limites da mudança e os critérios que a entrega precisa cumprir.

Você pode começar pelo Opus 5.5, como recomenda a Anthropic para tarefas diárias. Se o trabalho se mostrar aberto e complexo, passe para o Fable 5.2 e ajuste o nível de esforço. Ao receber a entrega, compare o resultado com os critérios definidos e revise os pontos que não correspondem ao objetivo.

Esse exemplo transforma a escolha do modelo em parte de um processo. A pergunta prática passa a ser quais objetivos, limites e critérios de sucesso precisam ficar claros e como você vai verificar a entrega. A autonomia depende tanto da formulação quanto da revisão.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## O que fazer hoje

1. No Claude, comece a tarefa diária com o Claude Opus 5.5. Você terá o ponto de partida recomendado pela Anthropic para a maioria das tarefas de programação e conhecimento.
2. Antes de enviar o pedido, escreva o objetivo, os limites e os critérios de sucesso. O resultado esperado é uma intenção que você consiga comparar com a entrega.
3. Se a tarefa for aberta e complexa, mude para o Claude Fable 5.2 no Claude, no Claude Code ou na Claude Platform. Você passa a usar o modelo indicado para desafios técnicos mais ambiciosos.
4. Ajuste o nível de esforço conforme a necessidade. Medium é o padrão no Claude e no Claude Code; High, Xhigh e Max permitem elevar o esforço. Você controla esse ajuste sem precisar trocar de modelo.
5. Ao usar vários modelos, decida se o Fable atuará como Advisor ou Orchestrator. No primeiro caso, modelos menores o consultam; no segundo, ele delega tarefas simples a eles. O resultado esperado é uma divisão explícita do trabalho.
6. Ao receber a resposta, compare-a com os critérios de sucesso e revise os pontos que não correspondem ao objetivo. Você obtém uma verificação concreta antes de aceitar a entrega.
7. Se for usar a API, acompanhe separadamente os tokens de entrada e de saída e o modo padrão ou Fast Mode. Você consegue estimar o custo pela tabela de preços por milhão de tokens.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## O que conferir

Os vídeos e as descrições oficiais são demonstrações de alto nível. Use-os para entender o tipo de resultado e o contexto do teste, sem tratá-los como uma receita completa de reprodução.

A segurança também tem escopo. A Anthropic relata testes pré-release que incluem avaliações de fugas de sandbox e afirma acreditar que riscos de desalinhamento de alto impacto continuam baixos. A empresa diz que o Fable 5.2 mantém as salvaguardas de cibersegurança e biologia do Fable 5.1, com menos bloqueios desnecessários, e aplica sua maior proteção contra ataques de destilação.

- Modelo e acesso: verifique se está usando Fable 5.2 ou Mythos 5.2. O primeiro está aberto a todos; o segundo exige aprovação nos programas Cyber e Life Sciences Verification ou acesso como cliente Claude Enterprise.
- Preço: separe tokens de entrada e de saída. O modo padrão custa US$ 8 e US$ 40 por milhão, respectivamente; o Fast Mode custa US$ 16 e US$ 80.
- Velocidade: trate até 30% e até 2,5 vezes como limites relatados em condições específicas. A segunda cifra se refere à geração de tokens no Fast Mode.
- Benchmarks: observe o esforço, o uso de ferramentas e as salvaguardas de cada resultado. A tabela usa o maior esforço disponível, salvo indicação, e o RoboDojo Sim foi executado internamente.
- Exemplos: diferencie demonstrações em vídeo, relatos de clientes e resultados de benchmark. Cada um desses formatos sustenta um tipo de conclusão diferente.
- Robótica: os 64,9% são uma pontuação no RoboDojo Sim. Eles não representam desempenho garantido em todos os robôs físicos.
- Segurança: as avaliações de risco e alinhamento são relatos da desenvolvedora do modelo. Trabalhos de alto impacto continuam exigindo revisão humana.
- Limites de uso: os até 3 resets extras pertencem à semana de lançamento. Não os trate como uma condição permanente dos planos.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Glossário

- Token: unidade de texto processada pelo modelo, usada também para calcular o consumo e o preço na API.
- Prompt: instrução enviada ao modelo para orientar uma tarefa.
- API: interface que permite usar o modelo por meio de integrações de software.
- Modelo subjacente: sistema de IA que sustenta as variantes oferecidas ao usuário.
- Subagente: agente que recebe uma parte do trabalho e pode executá-la em paralelo com outros.
- Nível de esforço: configuração que define quanto trabalho o modelo dedica à tarefa; Medium é o padrão no Claude e no Claude Code.
- Benchmark: teste padronizado usado para medir uma capacidade em condições definidas.
- Programação agêntica: uso de agentes para planejar e executar tarefas de programação, incluindo escrever, testar e revisar código.
- Advisor: função em que o Fable 5.2 é consultado por modelos menores para ajudar em problemas difíceis.
- Orchestrator: função em que o Fable 5.2 delega tarefas simples a modelos menores.
- Fast Mode: modo opcional que acelera a geração de tokens e tem preço por milhão de tokens maior que o modo padrão.
- Salvaguarda: proteção aplicada ao modelo para reduzir usos indevidos ou resultados prejudiciais.
- Alinhamento: correspondência entre o comportamento do modelo e os objetivos e limites definidos para ele.
- Sandbox: ambiente isolado usado para conter a execução de um sistema.
- Fuga de sandbox: situação em que um sistema ultrapassa o isolamento do ambiente em que deveria executar.
- Ataque de destilação: tentativa de extrair comportamento ou conhecimento de um modelo para reproduzi-lo em outro.
- Hipervisor: software que separa máquinas virtuais que compartilham uma mesma máquina física.
- RoboDojo Sim: benchmark de robótica mencionado no anúncio do Fable 5.2.

## Para onde ir depois

O próximo passo é aplicar o método a uma tarefa real. Escolha um objetivo, registre os limites e os critérios de sucesso, comece pelo Opus 5.5 e só aumente a complexidade do modelo quando o trabalho justificar.

Para aprofundar a leitura, use o anúncio oficial e a metodologia descrita no Claude Fable 5.2 and Claude Mythos 5.2 System Card. Eles ajudam a entender as condições dos testes e os resultados de segurança.

- Pratique a formulação em uma tarefa pequena e verifique se outra pessoa consegue entender o objetivo e os limites apenas pela sua descrição.
- Compare o resultado do Opus 5.5 com o do Fable 5.2 em um trabalho complexo e observe o que muda na entrega.
- Registre os pontos que precisaram de revisão humana para melhorar os próximos pedidos.
- Ao usar a API, acompanhe os tokens de entrada e de saída para relacionar o custo ao trabalho realizado.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Outros pontos

Para quem quiser se aprofundar, o anúncio oficial e o System Card trazem ainda:

- A tabela integral de benchmarks, incluindo linhas como AutomationBench, CyScenarioBench, CVE Rediscovery, desenho de proteínas, AA-Briefcase e Remote Labor Index.
- Os detalhes completos das avaliações de segurança e da metodologia de cada benchmark.
- A íntegra dos depoimentos de clientes publicados no anúncio oficial.
