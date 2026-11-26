# Anthropic lança Sheets, Data e Whiteboards no Claude

_2026-11-22 · reportagem_

A Anthropic anunciou, na terça-feira, dia 10, três novidades para o Claude: Sheets, Data e Whiteboards. Elas reúnem planilha, painel de dados e quadro branco no mesmo ambiente dos artefatos Docs, Slides e Design. Ao ler esta apostila, você vai entender como criar uma tabela por conversa, transformar um CSV em painel, acompanhar dados por conectores e montar um organograma. Também vai conhecer a liberação por plano, os cuidados antes de conectar dados e o fluxo prático para testar cada ferramenta.

## O fato

A Anthropic anunciou um conjunto de ferramentas de escritório dentro do Claude. O anúncio aconteceu na terça-feira, dia 10, e soma três novidades aos artefatos Docs, Slides e Design, que já existiam. As novas ferramentas são Claude Sheets, Claude Data e Claude Whiteboards.

Claude Sheets é uma planilha com fórmulas familiares para quem usa Excel ou Google Sheets. Claude Data transforma dados em painéis e visualizações, a partir de um arquivo CSV ou de conectores. Claude Whiteboards oferece um quadro em branco para cards, desenhos e estruturas visuais.

O Claude Data já existia com o nome Dashboards. A Central de ajuda também detalha em quais planos Sheets e Whiteboards estão disponíveis, em beta.

Fonte: <https://claude.com/resources/articles/more-ways-to-work-with-claude-sheets-whiteboards-and-interactive-connectors>

## Por que isso importa

O anúncio aproxima o Claude do trabalho de escritório. Até aqui, a conversa com o assistente podia levar à criação de documentos e apresentações. Com a planilha, o painel e o quadro branco, o Claude passa a reunir etapas diferentes de produção no mesmo ambiente.

Isso importa porque uma tarefa costuma atravessar vários formatos. Uma tabela de clientes pode virar um arquivo CSV. Esse arquivo pode alimentar um painel com métricas. Um quadro branco pode organizar a estrutura de uma empresa. No exemplo apresentado adiante, uma tabela criada no Sheets é exportada como CSV e vira um painel no Data.

O movimento também aumenta a concorrência no mercado corporativo. Google e Microsoft já ocupam esse território com pacotes de escritório e ferramentas de dados. A Anthropic entra nessa disputa com artefatos que nascem da conversa e podem se ligar a fontes externas por conectores.

Fonte: <https://claude.com/resources/articles/more-ways-to-work-with-claude-sheets-whiteboards-and-interactive-connectors>

## Claude Sheets

Claude Sheets abre como um artefato em forma de planilha. A experiência lembra Google Sheets e oferece as fórmulas conhecidas por quem trabalha com planilhas. Você pode editar a tabela diretamente ou descrever o que precisa em linguagem natural.

No modo conversacional, o Claude começa a montar a estrutura. Ele pode criar as categorias, preencher as colunas e inserir os dados enquanto você acompanha o trabalho. Isso muda o ponto de partida: em vez de abrir uma grade vazia e construir cada parte, você explica o objetivo da tabela.

Exemplo: uma hamburgueria fictícia pode pedir uma tabela de clientes. O Claude cria as categorias e preenche os registros. Como o exemplo usa dados fictícios, ele serve para entender o fluxo sem expor informações reais. Depois de gerar a planilha, confira as colunas, os valores e as fórmulas antes de usar o arquivo em um trabalho real.

```
quero que você crie uma tabela de clientes da minha hamburgueria fictícios.
```

Fonte: <https://claude.com/resources/articles/more-ways-to-work-with-claude-sheets-whiteboards-and-interactive-connectors>

## Claude Data a partir de CSV

CSV é um formato de arquivo que organiza dados em linhas e colunas. No Claude Data, ele funciona como ponte entre a planilha e o painel. Você exporta a tabela, importa o arquivo e pede as visualizações que fizerem sentido para aquele conjunto de dados.

O painel do exemplo usou uma tabela fictícia de clientes. A partir dela, o Claude sugeriu frequência, ticket médio, os dez maiores clientes por total gasto e dias desde o último pedido. Essas medidas ajudam a enxergar comportamentos que não aparecem com clareza na planilha bruta.

1. Na planilha criada no Sheets, use a opção de exportar e escolha CSV. O resultado esperado é um arquivo com os dados da tabela para importar no Data.
2. Volte a Artefatos, abra Claude Data e escolha importar de um CSV. O resultado esperado é a abertura da seleção de arquivo.
3. Selecione o arquivo exportado e envie o pedido de visualizações. O Claude usa as colunas disponíveis para sugerir métricas e gráficos.
4. Clique para permitir a criação quando a solicitação aparecer. O resultado esperado é um dashboard com as visualizações geradas.

```
Crie para mim diversas visualizações em um dashboard com dados que você acha que possa fazer sentido para os dados que eu estou te enviando.
```

Fonte: <https://claude.com/resources/articles/more-ways-to-work-with-claude-sheets-whiteboards-and-interactive-connectors>

## Claude Data com conectores

O Claude Data também pode receber dados de um conector. Com um arquivo CSV, o painel parte de um conteúdo exportado em um momento específico. Com o conector de e-mail, ele pode acompanhar as mensagens que chegam e atualizar os indicadores conforme novos dados aparecem.

O exemplo usa a caixa de entrada para mostrar o mecanismo. O painel pode mostrar o total de e-mails recebidos, separar as mensagens não lidas e incluir um contador de spam. O leitor escolhe o que quer medir, e o conector fornece a origem dos dados.

A mesma estrutura pode ser aplicada a outras fontes conectadas, como sistemas de uma empresa. Antes de ligar uma fonte real, defina quais informações serão acessadas e quem está autorizado a usar esses dados. O painel só consegue acompanhar o que a conexão disponibiliza.

Fonte: <https://claude.com/resources/articles/more-ways-to-work-with-claude-sheets-whiteboards-and-interactive-connectors>

## Claude Whiteboards

Claude Whiteboards é um espaço visual em branco, com uma proposta parecida com a do Miro. Você pode colocar cards e desenhar. Também pode pedir ao Claude uma estrutura pronta, como um organograma, e acompanhar a montagem.

O quadro ajuda a organizar relações hierárquicas, fluxos e ideias sem começar do zero. No exemplo, o pedido foi um organograma de uma empresa fictícia com três camadas. O Claude cria a distribuição visual dos níveis e dos cargos.

Exemplo: uma pessoa que precisa explicar uma estrutura de empresa pode começar pelo texto e receber um organograma no quadro. As três camadas do exemplo mostram a profundidade pedida naquele caso. Depois, vale revisar nomes, cargos e linhas de reporte para confirmar se a estrutura corresponde à organização real.

```
crie para mim o organograma de uma empresa fictícia com três camadas.
```

Fonte: <https://claude.com/resources/articles/more-ways-to-work-with-claude-sheets-whiteboards-and-interactive-connectors>

## Chamadas de vídeo com um agente do Claude

O pacote de novidades também inclui chamadas de vídeo com uma proposta semelhante à de Zoom ou Google Meet. O diferencial descrito é a presença de um agente do Claude dentro da chamada. Ele aparece como mais um participante, acompanha o que é dito e aceita sugestões durante a reunião.

Na versão do aplicativo testada, esse recurso ainda não estava disponível. Por isso, o primeiro cuidado é confirmar se ele aparece na sua conta. Antes de colocar o agente em uma reunião, verifique se os participantes autorizam a presença dele e se o áudio contém informação interna que não deva ser compartilhada.

## Conectores interativos

Conectores são pontes que permitem ao Claude trocar informações com outras aplicações. Essa troca pode envolver dados ou ações. Esses conectores também são chamados de MCPs.

A novidade interativa torna o trabalho da conexão visível. Ao pedir uma interação com um conector, como o Gmail, o Claude pode abrir o site da aplicação dentro da experiência. A pessoa acompanha o processo e consegue observar se a ação corresponde ao pedido.

Esse acompanhamento ajuda a fiscalizar uma conexão que mexe em dados externos. A liberação dos conectores interativos no Brasil é gradual, então a disponibilidade precisa ser observada na própria conta.

Fonte: <https://claude.com/resources/articles/more-ways-to-work-with-claude-sheets-whiteboards-and-interactive-connectors>

## Como funciona na prática

Imagine uma hamburgueria que quer entender melhor o comportamento dos clientes. O trabalho começa no Claude Sheets com um pedido de tabela. O Claude cria as categorias e preenche registros fictícios, o que permite testar o processo sem usar dados reais.

Em seguida, a planilha é exportada como CSV. O arquivo é importado no Claude Data, e um prompt pede visualizações adequadas aos dados enviados. O painel resultante reúne indicadores como frequência, ticket médio e clientes com maior total gasto.

O leitor passa por quatro pontos de controle: a estrutura da tabela, o conteúdo do CSV, a escolha das métricas e o sentido dos gráficos. Se algum indicador não fizer sentido, o painel pode ser ajustado. Para criar um organograma, o fluxo é mais direto: abra Whiteboards e peça a estrutura desejada.

Fonte: <https://claude.com/resources/articles/more-ways-to-work-with-claude-sheets-whiteboards-and-interactive-connectors>

## Linha do tempo

A disponibilidade das ferramentas não acontece toda no mesmo instante. O anúncio define o pacote, e a Central de ajuda detalha regras específicas de ativação.

- Terça-feira, dia 10: a Anthropic anunciou Claude Sheets, Claude Data e Claude Whiteboards, além de conectores interativos e chamadas de vídeo com agente.
- 20 de novembro de 2026: o Claude Data fica ativado por padrão no plano Enterprise, conforme a Central de ajuda.
- Quando as ferramentas aparecerem na conta: Sheets e Whiteboards seguem a disponibilidade em beta e, no Enterprise, dependem da ativação de um administrador.

Fonte: <https://support.claude.com/en/articles/18324300-get-started-with-claude-sheets>

## Os números

Os números abaixo ajudam a entender o tamanho do pacote e o recorte dos exemplos. Eles não medem, sozinhos, a qualidade ou a substituição de ferramentas existentes.

- Três novidades centrais: Sheets, Data e Whiteboards se somam a Docs, Slides e Design. A contagem descreve o pacote anunciado e não inclui todos os recursos internos de cada ferramenta.
- Top 10 clientes por total gasto: é uma visualização do painel criado com dados fictícios. Ela ordena os dez clientes com maior soma de gastos naquele exemplo e não representa uma base real.
- Três camadas: é a profundidade do organograma fictício solicitado no Whiteboards. O número pertence ao exemplo e não funciona como limite informado para outros quadros.
- 20 de novembro de 2026: é a data de ativação padrão do Claude Data no Enterprise. Ela não indica a data de lançamento geral do Data.
- Pro, Max, Ultra, Team e Enterprise: são os planos listados para Sheets e Whiteboards em beta. O plano gratuito não aparece nessa lista.
- No plano Team, as três ferramentas vêm ativadas por padrão. No Enterprise, Sheets e Whiteboards começam desativados até um administrador ligá-los, enquanto o Data tem regra própria de ativação.

Fonte: <https://support.claude.com/en/articles/18324300-get-started-with-claude-sheets>

## O que muda para você

Para quem já monta planilhas e relatórios, a mudança está na ordem do trabalho. Você pode começar pela descrição do que precisa, deixar o Claude estruturar a tabela e pedir a análise em seguida. A exportação para CSV e a importação no Data mantêm esse fluxo dentro do ambiente dos artefatos.

Exemplo: em vez de escolher cada gráfico de um painel do zero, você explica que quer visualizações para os dados de clientes. O Claude sugere métricas. Ainda assim, cabe ao leitor decidir se frequência, ticket médio e recência respondem à pergunta do negócio.

Para trabalhos visuais, Whiteboards oferece outro ponto de partida. Uma estrutura hierárquica pode nascer de um pedido por texto e depois ser ajustada no quadro. O benefício prático é ter um primeiro rascunho rapidamente, com possibilidade de revisão.

Fonte: <https://claude.com/resources/articles/more-ways-to-work-with-claude-sheets-whiteboards-and-interactive-connectors>

## Quem ganha e quem perde

Profissionais que trabalham com documentos, planilhas, indicadores e diagramas encontram mais opções dentro do Claude. Empresas também podem avaliar como essas ferramentas se encaixam nos sistemas já usados e quais conectores seriam necessários.

Google e Microsoft passam a enfrentar concorrência em um território que já dominam com ferramentas de escritório e dados. As comparações com Office, Power BI e Miro ajudam a entender a proposta, mas a disputa depende de adoção, integração e uso real. Uma entrada nova no mercado não basta para declarar um vencedor ou uma perda de usuários.

Fonte: <https://claude.com/resources/articles/more-ways-to-work-with-claude-sheets-whiteboards-and-interactive-connectors>

## O que fazer hoje

O caminho mais simples para aprender é repetir o fluxo com dados fictícios. Comece pela disponibilidade da conta e depois avance uma ferramenta por vez.

1. Atualize o aplicativo do Claude. Se as novidades não aparecerem depois da atualização, verifique a liberação e o plano da conta.
2. Confirme o plano: Sheets e Whiteboards estão em beta em Pro, Max, Ultra, Team e Enterprise. No Team, as três ferramentas vêm ativadas por padrão; no Enterprise, um administrador precisa ligar Sheets e Whiteboards. O resultado esperado é identificar se você já pode abrir os artefatos.
3. Abra Artefatos e entre em Claude Sheets. Envie o pedido de uma tabela de clientes fictícios. O resultado esperado é uma planilha com categorias e registros preenchidos pelo Claude.
4. Exporte a planilha como CSV. O resultado esperado é um arquivo que preserve as colunas e os dados criados.
5. Abra Claude Data, escolha importar de um CSV e selecione o arquivo. Envie o pedido de visualizações e permita a criação quando solicitado. O resultado esperado é um painel com métricas e gráficos.
6. Abra Claude Whiteboards e peça um organograma de empresa fictícia com três camadas. O resultado esperado é um quadro com a estrutura hierárquica montada.
7. Se quiser testar conectores, escolha uma fonte com dados que você pode compartilhar e defina os indicadores antes da conexão. O resultado esperado é um painel alimentado pela origem escolhida, com atualização conforme os dados chegarem.

Fonte: <https://support.claude.com/en/articles/18324300-get-started-with-claude-sheets>

## O que conferir

As ferramentas automatizam a criação de uma primeira versão. A revisão continua necessária para confirmar se o resultado serve ao objetivo.

- Confira o plano e o estado beta antes de esperar acesso imediato. Sheets e Whiteboards aparecem na lista de Pro, Max, Ultra, Team e Enterprise; o plano gratuito não aparece nessa lista.
- No Enterprise, verifique se um administrador ativou Sheets e Whiteboards. O Claude Data tem ativação padrão prevista para 20 de novembro de 2026 nesse plano.
- Se um artefato não aparecer, atualize o aplicativo e observe a liberação gradual. A ausência momentânea não deve ser interpretada como falha na criação do arquivo.
- Revise fórmulas, categorias e valores da planilha. O preenchimento automático pode produzir uma base fictícia ou inadequada se o pedido não descrever bem a estrutura desejada.
- Confira se cada métrica do painel responde a uma pergunta real. Frequência, ticket médio e total gasto medem coisas diferentes e não devem ser lidas como sinônimos.
- Antes de conectar e-mail ou sistemas da empresa, verifique autorização, escopo de acesso e sensibilidade dos dados. Um conector amplia o alcance das ações dentro do Claude.
- Use dados fictícios no primeiro teste. Eles permitem aprender o fluxo sem colocar informações reais em uma demonstração.
- Confira a disponibilidade das chamadas de vídeo com agente e dos conectores interativos na sua conta. As chamadas ainda não estavam disponíveis na versão testada, e os conectores interativos têm liberação gradual no Brasil.

Fonte: <https://support.claude.com/en/articles/18324300-get-started-with-claude-sheets>

## Glossário

- Artefato: objeto de trabalho criado dentro do Claude, como documento, apresentação, planilha, painel ou quadro branco.
- Beta: versão disponível para teste antes de uma liberação ampla, podendo ter regras próprias de acesso.
- CSV: formato de arquivo que organiza informações em linhas e colunas e permite exportar ou importar dados de uma planilha.
- Dashboard: painel que reúne indicadores e visualizações para acompanhar um conjunto de dados.
- Fórmula: instrução usada em uma célula da planilha para calcular ou obter um resultado a partir de outros valores.
- Métrica: medida usada para acompanhar um aspecto dos dados, como frequência ou ticket médio.
- Ticket médio: média dos valores de compra ou pedido, usada para entender o gasto característico daquele conjunto de clientes.
- Visualização: representação gráfica de dados, como um gráfico que ajuda a comparar ou acompanhar valores.
- Conector: ligação que permite ao Claude trocar dados ou executar ações com outra aplicação.
- MCP: padrão de conexão usado para ligar o Claude a ferramentas e fontes de dados externas.
- Whiteboard: quadro visual em branco onde é possível organizar cards, desenhos e estruturas.
- Organograma: representação visual da hierarquia de uma empresa, com níveis e relações de reporte.
- Spam: mensagem indesejada que pode ser identificada e contada separadamente em um painel de e-mail.

## Para onde ir depois

O próximo passo é executar o fluxo completo com dados fictícios e observar onde a automação ajuda. Depois, repita o exercício com uma pergunta que você realmente precisa responder.

Pratique a revisão tanto quanto a criação. Uma planilha bem preenchida, um painel com métricas coerentes e um organograma correto dependem de você conferir o resultado gerado.

- Crie uma tabela no Sheets e confira se as categorias permitem responder à pergunta que você tinha em mente.
- Exporte a tabela como CSV e monte um painel no Data com visualizações adequadas aos dados.
- Peça um organograma no Whiteboards e revise cargos, níveis e relações de reporte.
- Se a conexão estiver disponível e autorizada, teste um conector com indicadores simples antes de levar o painel para dados de trabalho.
