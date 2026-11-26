# Revolut corta 90% do custo de IA ao adotar GLM

_2026-11-23 · noticia_

O Revolut levou o GLM 5.1, da Z.ai, para a geração de código de cerca de 2.000 engenheiros e hospedou o modelo nos próprios servidores. Segundo a reportagem do The Register, a US$ 0,30 por milhão de tokens, esse custo é cerca de um décimo do custo de usar Codex ou Claude Code. O banco mantém GPT e Claude em usos específicos e usa um roteador para enviar tarefas visuais, como UI, a modelos como Gemini ou GPT Luna. Ao longo desta apostila, você vai entender a conta, o papel da hospedagem própria e como separar tarefas de texto, visão e uso excepcional de modelos de ponta.

## O fato

Em reportagem publicada em 3 de novembro de 2026, o The Register descreve a adoção do GLM 5.1 pelo Revolut. O modelo da chinesa Z.ai gera código para cerca de 2.000 engenheiros e roda nos servidores do próprio banco.

A mudança reduziu aproximadamente 90% do custo de IA nesse cenário. A comparação usa Codex ou Claude Code como referência e apresenta o GLM 5.1 hospedado a US$ 0,30 por milhão de tokens, cerca de um décimo daquele custo.

A operação mantém GPT e Claude em parte do fluxo. Tarefas visuais, como trabalho de interface, passam por um roteador para modelos como Gemini ou GPT Luna. A geração de código permanece no GLM.

Fonte: <https://www.theregister.com/ai-and-ml/2026/11/03/british-fintech-revolut-slashes-ai-coding-costs-10x-by-cutting-out-claude-and-going-self-hosted/5307345>

## Por que isso importa

Uma equipe de programação usa IA em tarefas diferentes. Gerar código a partir de texto e interpretar uma interface exigem capacidades diferentes. O caso do Revolut mostra uma distribuição dessas tarefas por tipo de modelo, em vez de enviar tudo ao mesmo serviço.

A conta depende do volume de uso e do preço por unidade. O GLM 5.1 aparece na comparação com custo de cerca de um décimo da referência formada por Codex e Claude Code. O número precisa ser lido dentro dessa comparação.

A hospedagem própria completa a estratégia. Rodar o modelo nos servidores do banco coloca a execução da infraestrutura sob o controle do Revolut. A reportagem descreve o código aberto como prioridade e o modelo de ponta como exceção.

Fonte: <https://www.theregister.com/ai-and-ml/2026/11/03/british-fintech-revolut-slashes-ai-coding-costs-10x-by-cutting-out-claude-and-going-self-hosted/5307345>

## O GLM 5.1 e a família GLM-5

O GLM 5.1 é o modelo citado no caso do Revolut. Ele pertence à família GLM-5, desenvolvida pela Z.ai. O repositório oficial reúne a família e é identificado como repositório de pesos abertos, com licença Apache-2.0.

Pesos abertos são os parâmetros que o modelo aprende durante o treinamento e que ficam disponíveis para uso. Isso permite que uma organização avalie o modelo e considere executá-lo em infraestrutura própria. No caso descrito, o Revolut hospeda o GLM 5.1 nos seus servidores.

A distinção entre família e versão ajuda a ler os materiais oficiais. O endereço do repositório usa o nome GLM-5, enquanto a comparação de custo do caso usa GLM 5.1. O número da versão não deve ser trocado na hora de reproduzir a comparação.

Fonte: <https://github.com/zai-org/GLM-5>

## O que muda quando o modelo roda no próprio banco

Hospedar um modelo significa executá-lo em servidores. Quando isso acontece dentro da própria empresa, a empresa controla a infraestrutura em que o modelo roda. No Revolut, o GLM 5.1 hospedado é quem gera o código dos engenheiros.

Essa escolha se liga ao custo por tokens citado na reportagem. O valor de US$ 0,30 por milhão de tokens é apresentado para o GLM 5.1 hospedado. A base 100 da comparação representa o uso de Codex ou Claude Code, e o GLM aparece perto de 10.

O preço por token e a hospedagem são partes relacionadas, mas medidas diferentes. O caso informa o custo comparado e o local de execução. O total de uso acompanha o volume de tokens, já que a unidade da comparação é um milhão de tokens.

Fonte: <https://www.theregister.com/ai-and-ml/2026/11/03/british-fintech-revolut-slashes-ai-coding-costs-10x-by-cutting-out-claude-and-going-self-hosted/5307345>

## Como ler a conta do custo

US$ 0,30 por milhão de tokens é o valor atribuído ao GLM 5.1 hospedado na comparação. Token é uma unidade de processamento de texto usada para medir entrada e saída do modelo. Um milhão de tokens é a unidade do preço; não é uma quantidade de engenheiros, tarefas ou respostas.

A escala do gráfico é relativa. Codex ou Claude Code recebe a base 100. O GLM 5.1 hospedado fica em cerca de 10. Assim, o custo restante é aproximadamente um décimo da referência, o que corresponde a um corte aproximado de 90%.

Essa comparação não transforma 100 em US$ 100 nem 10 em US$ 10. Os índices mostram proporção. O valor em dólares que aparece no caso é US$ 0,30 por milhão de tokens.

Fonte: <https://www.theregister.com/ai-and-ml/2026/11/03/british-fintech-revolut-slashes-ai-coding-costs-10x-by-cutting-out-claude-and-going-self-hosted/5307345>

## Por que o GLM só texto leva a um roteador

O GLM 5.1 usado pelo Revolut trabalha só com texto. Isso serve para a geração de código descrita no caso. Tarefas de visão computacional, como interpretar uma interface, precisam de outro caminho.

O banco usa um roteador de modelos para direcionar essas consultas visuais a modelos como Gemini ou GPT Luna. O roteador recebe a consulta e a encaminha ao modelo escolhido para aquele tipo de tarefa.

A estratégia mantém a geração de código no GLM e usa modelos de ponta como exceção. GPT e Claude continuam presentes em usos específicos. No relato, Codex e Claude Code aparecem como referência de custo.

Fonte: <https://www.theregister.com/ai-and-ml/2026/11/03/british-fintech-revolut-slashes-ai-coding-costs-10x-by-cutting-out-claude-and-going-self-hosted/5307345>

## Codex e Claude Code entram na comparação

Codex e Claude Code são as ferramentas usadas como referência de custo no caso. A reportagem compara o custo de usar OpenAI Codex ou Anthropic Claude Code com o de hospedar o GLM 5.1. A base 100 pertence a essa referência.

O Codex CLI está no repositório oficial da OpenAI. O Claude Code tem página oficial da Anthropic. No caso do Revolut, a função dessas ferramentas no relato é servir de referência de custo.

Fonte: <https://www.theregister.com/ai-and-ml/2026/11/03/british-fintech-revolut-slashes-ai-coding-costs-10x-by-cutting-out-claude-and-going-self-hosted/5307345>

## Os números

Os números do caso precisam ser lidos com suas unidades e seus pontos de comparação. Eles descrevem o alcance das ferramentas de programação, a redução de custo e a proporção entre as opções.

- Cerca de 2.000 engenheiros: é o alcance citado para as ferramentas de IA de programação; o GLM gera código para esse grupo.
- Aproximadamente 90%: é a redução de custo relatada; indica que restou cerca de 10% do custo de referência.
- Base 100 para Codex ou Claude Code: é um índice relativo da comparação, não um preço em dólares.
- Cerca de 10 para o GLM 5.1 hospedado: mostra que o custo ficou perto de um décimo da referência.
- US$ 0,30 por milhão de tokens: é o valor usado para o GLM 5.1 hospedado na comparação de custo.

Fonte: <https://www.theregister.com/ai-and-ml/2026/11/03/british-fintech-revolut-slashes-ai-coding-costs-10x-by-cutting-out-claude-and-going-self-hosted/5307345>

## O que muda para você

Exemplo: imagine uma equipe que usa IA para escrever código e também para trabalhar com interfaces visuais. O caso do Revolut sugere separar esses dois fluxos antes de escolher um único modelo para tudo.

No fluxo de texto, a geração de código pode ficar com um modelo como o GLM 5.1, com a hospedagem avaliada pela equipe. No fluxo visual, um roteador pode enviar as tarefas a modelos como Gemini ou GPT Luna. O modelo de ponta entra nas situações específicas previstas pela equipe.

Para aplicar a ideia, identifique quais tarefas exigem texto e quais exigem visão. Depois, compare os custos na mesma unidade e decida onde cada tarefa vai rodar. O resultado esperado é uma divisão clara de responsabilidades, mantendo o custo por milhão de tokens como base da comparação.

Fonte: <https://www.theregister.com/ai-and-ml/2026/11/03/british-fintech-revolut-slashes-ai-coding-costs-10x-by-cutting-out-claude-and-going-self-hosted/5307345>

## O que fazer hoje

Comece pelo mapa de tarefas. A divisão entre texto e visão define quais atividades podem seguir no fluxo de código e quais precisam de outro modelo.

1. Liste as tarefas de programação da equipe e marque as que usam só texto e as que envolvem visão ou interface. O resultado é um mapa que mostra quais atividades podem seguir no fluxo de código e quais precisam de roteamento.
2. Abra o repositório oficial do GLM-5 e identifique a versão GLM 5.1, os pesos abertos e a licença Apache-2.0. O resultado é a confirmação do modelo e das condições apresentadas pelo projeto.
3. Compare as opções usando a mesma unidade, tokens por milhão. No caso do Revolut, a referência é Codex ou Claude Code na base 100, e o GLM 5.1 hospedado fica em cerca de 10. O resultado é uma comparação proporcional.
4. Decida se a geração de código será executada em infraestrutura própria. No exemplo do banco, o GLM 5.1 roda nos servidores do Revolut. O resultado é uma escolha explícita de hospedagem para essa etapa.
5. Defina um roteador para as tarefas visuais e estabeleça quais situações usarão modelos de ponta. O exemplo do banco encaminha visão e UI a modelos como Gemini ou GPT Luna, mantendo o modelo de ponta como exceção. O resultado é um destino definido para cada tipo de tarefa.

Fonte: <https://www.theregister.com/ai-and-ml/2026/11/03/british-fintech-revolut-slashes-ai-coding-costs-10x-by-cutting-out-claude-and-going-self-hosted/5307345>

## O que conferir

Antes de transportar o caso para outra equipe, preserve o recorte de cada número e de cada função. A comparação do Revolut junta custo, capacidade do modelo e distribuição de tarefas.

- Recorte do número: o corte de aproximadamente 90% pertence ao caso do Revolut e à comparação apresentada. Ele não estabelece o mesmo resultado para outra equipe.
- Unidade do preço: US$ 0,30 é o valor por milhão de tokens do GLM 5.1 hospedado. A base 100 e o valor 10 são índices relativos.
- Capacidade do modelo: o GLM 5.1 do caso é só texto. Tarefas de visão e UI seguem por outro caminho.
- Papel das ferramentas: Codex e Claude Code aparecem como referência de custo. GPT e Claude permanecem em usos específicos, com o modelo de ponta como exceção.
- Roteamento: cada tarefa visual precisa de um destino definido, como Gemini ou GPT Luna no caso relatado, antes de aplicar a mesma divisão.

Fonte: <https://www.theregister.com/ai-and-ml/2026/11/03/british-fintech-revolut-slashes-ai-coding-costs-10x-by-cutting-out-claude-and-going-self-hosted/5307345>

## Glossário

- GLM 5.1: versão do modelo da Z.ai usada na comparação de custo e na geração de código do caso.
- GLM-5: família de modelos da Z.ai e nome do repositório oficial de pesos abertos.
- Z.ai: empresa desenvolvedora da família GLM-5.
- Token: unidade de processamento de texto usada para medir o uso do modelo.
- Modelo só texto: modelo que processa texto, sem tratar das tarefas visuais descritas no caso.
- Visão computacional: capacidade de interpretar informações visuais, como uma imagem de interface.
- UI: interface de usuário, a parte visual com que a pessoa interage.
- Roteador de modelos: componente que encaminha uma consulta ao modelo escolhido para aquele tipo de tarefa.
- Modelo de ponta: modelo de capacidade avançada que, na estratégia descrita, é usado como exceção.
- Hospedagem própria: execução do modelo em servidores da própria organização.
- Pesos abertos: parâmetros do modelo disponibilizados pelo projeto, conforme o repositório oficial.
- Apache-2.0: licença indicada no repositório oficial dos pesos abertos do GLM-5.
- Codex CLI: agente de programação da OpenAI, usado como referência de custo na comparação.
- Claude Code: produto de programação da Anthropic, usado como referência de custo na comparação.

Fonte: <https://www.theregister.com/ai-and-ml/2026/11/03/british-fintech-revolut-slashes-ai-coding-costs-10x-by-cutting-out-claude-and-going-self-hosted/5307345>

## Para onde ir depois

O próximo passo é transformar a divisão do caso em um exercício prático. Separe as tarefas da sua equipe entre geração de código, visão ou UI e usos excepcionais de modelos de ponta.

- Leia a reportagem do The Register para acompanhar a comparação de custo e o roteamento descrito: https://www.theregister.com/ai-and-ml/2026/11/03/british-fintech-revolut-slashes-ai-coding-costs-10x-by-cutting-out-claude-and-going-self-hosted/5307345
- Conheça a Z.ai no site oficial: https://z.ai
- Examine a família GLM-5 no repositório oficial: https://github.com/zai-org/GLM-5
- Localize o Codex CLI no repositório oficial da OpenAI: https://github.com/openai/codex
- Localize o Claude Code na página oficial da Anthropic: https://claude.com/product/claude-code
- Pratique a classificação das tarefas da sua equipe e use a mesma divisão para discutir hospedagem e custo por milhão de tokens.

Fonte: <https://www.theregister.com/ai-and-ml/2026/11/03/british-fintech-revolut-slashes-ai-coding-costs-10x-by-cutting-out-claude-and-going-self-hosted/5307345>
