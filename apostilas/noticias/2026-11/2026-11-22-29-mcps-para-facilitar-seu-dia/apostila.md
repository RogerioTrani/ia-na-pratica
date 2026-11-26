# 29 MCPs para facilitar seu dia

_2026-11-22 · noticia_

A coleção reúne 29 servidores e recursos MCP em seis categorias, mais dois diretórios para encontrar outras opções. Você vai entender o que é um servidor MCP, como ele conecta um assistente a ferramentas e dados e qual é a diferença entre instalação local e servidor remoto. Também vai conhecer os endereços e comandos de GitHub, Context7, Playwright, Filesystem, Brave Search, Supabase, Neon, Stripe, Figma, CoinGecko e demais itens. No fim, saberá escolher um servidor para o seu fluxo, conferir origem e permissões e testar com dados que não sejam de produção.

## O fato

A coleção MCP Servers Complete Link Collection, datada de 3 de novembro de 2026, reúne 29 entradas em seis categorias: uso geral, desenvolvimento e bancos de dados, equipes e negócios, criação de conteúdo, pagamentos e finanças, negociação e mercados. A seleção termina com dois diretórios: o repositório oficial de servidores MCP e a lista Awesome MCP Servers.

Cada entrada pode ser um repositório, uma documentação, uma busca, uma página de produto ou um endpoint. Essa distinção muda o próximo passo: o repositório permite examinar o código, a documentação orienta a configuração e o endpoint identifica para onde a conexão remota aponta.

A lista mistura projetos oficiais, iniciativas da comunidade, implementações arquivadas e recursos em versão prévia. O nome do serviço ajuda a reconhecer a entrada, mas o tipo e o estado de manutenção indicam como ela deve ser avaliada.

## Por que isso importa

Um servidor MCP é o elo entre um assistente de IA e uma ferramenta ou fonte de dados. O assistente envia uma solicitação pelo protocolo MCP; o servidor recebe, considera o que está autorizado e executa a ação disponível. A conexão pode rodar na sua máquina ou apontar para um serviço remoto.

Isso amplia o trabalho do assistente. Ele passa a atuar nos sistemas que você liberou, com o alcance definido pelas permissões. Um acesso maior permite mais ações e também aumenta a necessidade de revisar o que será lido ou alterado.

Imagine que você libera uma pasta do projeto para o Filesystem. O argumento /caminho/permitido indica a área recebida pelo servidor no comando. Teste primeiro com uma pasta de trabalho e observe se o assistente respeita esse limite antes de ampliar o acesso.

Começar com poucos servidores mantém o conjunto de credenciais e permissões sob controle. A lista serve para montar conexões que combinem com tarefas reais, em vez de instalar todas as opções de uma vez.

Fonte: <https://github.com/modelcontextprotocol/servers>

## Uso geral: GitHub, Context7, Playwright, Filesystem e Brave Search

Estas cinco opções cobrem trabalho com código, documentação, navegação, arquivos e busca. GitHub oferece conexão por Docker ou servidor remoto; Context7 oferece npx ou servidor remoto. Playwright, Filesystem e Brave Search aparecem com comandos locais.

A configuração mostra parte do comportamento de cada servidor. O Filesystem recebe um caminho explícito, o Brave Search usa stdio e o Playwright é iniciado por npx com @latest. Esses detalhes ajudam a entender onde o processo roda e qual versão está sendo chamada.

- GitHub: repositório em https://github.com/github/github-mcp-server, servidor remoto em api.githubcopilot.com/mcp/ e comando Docker no bloco abaixo. O comando passa o token pela variável GITHUB_PERSONAL_ACCESS_TOKEN.
- Context7: repositório em https://github.com/upstash/context7, servidor remoto em mcp.context7.com/mcp e comando npx no bloco abaixo.
- Playwright: repositório em https://github.com/microsoft/playwright-mcp e comando npx no bloco abaixo. O sufixo @latest indica a versão mais recente do pacote.
- Filesystem: repositório em https://github.com/modelcontextprotocol/servers/tree/main/src/filesystem e comando npx no bloco abaixo. O argumento /caminho/permitido representa a pasta que você pretende liberar.
- Brave Search: repositório em https://github.com/brave/brave-search-mcp-server e comando npx no bloco abaixo. A opção --transport stdio configura a comunicação local pela entrada e saída do processo.

```
docker run -i --rm -e GITHUB_PERSONAL_ACCESS_TOKEN ghcr.io/github/github-mcp-server
npx -y @upstash/context7-mcp
npx @playwright/mcp@latest
npx -y @modelcontextprotocol/server-filesystem /caminho/permitido
npx -y @brave/brave-search-mcp-server --transport stdio
```

Fonte: <https://github.com/github/github-mcp-server>

## Desenvolvimento e bancos de dados

Seis entradas cobrem bancos de dados, monitoramento, contêineres e Kubernetes. O PostgreSQL oficial aparece como implementação de referência arquivada. A alternativa mantida indicada é o Postgres MCP Pro, executado pelo comando uvx postgres-mcp.

Supabase, Neon e Sentry têm endpoints remotos. Supabase, Neon e Sentry também registram comandos locais. O Docker MCP Catalog é um catálogo para descobrir servidores, e o Kubernetes aponta para um repositório da comunidade mantido pela equipe Red Hat/Containers, escrito em Go e sem dependência externa de kubectl.

Antes de levar uma conexão de banco para produção, confira manutenção, permissões e dados acessados. O endpoint remoto define o destino da conexão; o comando local determina o código que será executado na sua máquina.

- PostgreSQL arquivado: referência em https://github.com/modelcontextprotocol/servers-archived/tree/main/src/postgres. A alternativa mantida indicada é o Postgres MCP Pro, com uvx postgres-mcp.
- Supabase: repositório em https://github.com/supabase-community/supabase-mcp e servidor remoto em mcp.supabase.com/mcp. A instalação local registrada usa o comando com <PAT> no bloco abaixo, ponto em que entra o token de acesso.
- Neon: repositório em https://github.com/neondatabase/mcp-server-neon, servidor remoto em mcp.neon.tech/mcp e comando npx neon@latest init no bloco abaixo. O servidor remoto aceita OAuth ou API Key.
- Sentry: repositório em https://github.com/getsentry/sentry-mcp, servidor remoto em mcp.sentry.dev/mcp e comando npx @sentry/mcp-server@latest no bloco abaixo.
- Docker MCP Catalog: catálogo em https://hub.docker.com/mcp para descobrir servidores MCP.
- Kubernetes: repositório da comunidade em https://github.com/containers/kubernetes-mcp-server.

```
uvx postgres-mcp
npx -y @supabase/mcp-server-supabase@latest --access-token <PAT>
npx neon@latest init
npx @sentry/mcp-server@latest
```

Fonte: <https://github.com/modelcontextprotocol/servers-archived/tree/main/src/postgres>

## Equipes e negócios

Esta categoria reúne documentação e serviços usados por equipes. Slack tem página oficial de documentação; Linear, Notion e Atlassian oferecem servidor remoto. Google Calendar e Gmail aparecem em Developer Preview, versão prévia para desenvolvedores.

Nos serviços remotos, a autenticação faz parte da configuração. O Notion documenta o endpoint via Streamable HTTP e informa que ele substitui o antigo /sse. Linear e Atlassian têm endpoints próprios. No Google, Calendar e Gmail usam endpoints específicos.

- Slack: documentação oficial do servidor MCP em https://docs.slack.dev/ai/mcp-server.
- Linear: documentação em https://linear.app/docs/mcp e servidor remoto em mcp.linear.app/mcp, via Streamable HTTP.
- Notion: guia de MCP em https://developers.notion.com/guides/mcp/get-started-with-mcp e servidor remoto em mcp.notion.com/mcp, via Streamable HTTP.
- Atlassian Rovo MCP: repositório em https://github.com/atlassian/atlassian-mcp-server e servidor remoto em mcp.atlassian.com/v2/mcp.
- Google Calendar, Developer Preview: guia em https://developers.google.com/workspace/calendar/api/guides/configure-mcp-server e servidor remoto em calendarmcp.googleapis.com/mcp/v1.
- Gmail, Developer Preview: guia em https://developers.google.com/workspace/guides/configure-mcp-servers e servidor remoto em gmailmcp.googleapis.com/mcp/v1.

Fonte: <https://developers.notion.com/guides/mcp/get-started-with-mcp>

## Criação de conteúdo

Higgsfield, DaVinci Resolve, Figma, ElevenLabs e YouTube formam o grupo de criação de conteúdo. A seleção combina conector personalizado, servidor hospedado, servidor remoto e repositórios da comunidade. A origem de cada item ajuda a definir o caminho de instalação.

Figma e Higgsfield têm endpoints remotos. ElevenLabs usa servidor hospedado com OAuth. DaVinci Resolve e YouTube apontam para repositórios da comunidade e têm comandos npx. O comando do Figma registra a conexão HTTP no Claude Code.

- Higgsfield: página em https://higgsfield.ai/mcp e conector personalizado em mcp.higgsfield.ai/mcp.
- DaVinci Resolve: repositório da comunidade em https://github.com/samuelgursky/davinci-resolve-mcp e comando npx davinci-resolve-mcp setup no bloco abaixo.
- Figma: documentação em https://developers.figma.com/docs/figma-mcp-server/, servidor remoto em mcp.figma.com/mcp e comando de conexão para o Claude Code no bloco abaixo.
- ElevenLabs: documentação em https://elevenlabs.io/docs/eleven-agents/operate/hosted-mcp, com servidor hospedado e autenticação OAuth.
- YouTube: repositório da comunidade em https://github.com/anaisbetts/mcp-youtube e comando npx no bloco abaixo.

```
npx davinci-resolve-mcp setup
claude mcp add --transport http figma https://mcp.figma.com/mcp
npx -y @anaisbetts/mcp-youtube
```

Fonte: <https://developers.figma.com/docs/figma-mcp-server/>

## Pagamentos e finanças

Stripe, Plaid e QuickBooks podem alcançar dados financeiros. A coleção recomenda começar com credenciais de teste ou sandbox. Essa precaução vale para qualquer conexão que envolva dinheiro ou dados bancários.

Stripe tem endpoint remoto e comando npx. Plaid tem endpoint remoto do Dashboard e usa OAuth com escopo mcp:dashboard. QuickBooks tem repositório oficial da Intuit e roda localmente via stdio. Cada integração exige sua própria configuração de credenciais e permissões.

- Stripe: documentação em https://docs.stripe.com/mcp, servidor remoto em mcp.stripe.com e comando npx -y @stripe/mcp --tools=all no bloco abaixo.
- Plaid: documentação em https://plaid.com/docs/resources/mcp/ e endpoint remoto do Dashboard em api.dashboard.plaid.com/mcp/, com autenticação OAuth no escopo mcp:dashboard.
- QuickBooks: repositório oficial da Intuit em https://github.com/intuit/quickbooks-online-mcp-server, executado localmente via stdio.

```
npx -y @stripe/mcp --tools=all
```

Fonte: <https://docs.stripe.com/mcp>

## Negociação e mercados

Polygon.io agora se chama Massive. A entrada atual usa o repositório massive-com/mcp_massive e o endpoint mcp.massive.com. CoinGecko, CCXT e TradingView completam a categoria com servidor remoto, execução local e servidor remoto com OAuth, respectivamente.

CoinGecko traz um comando para o Claude Code; CCXT usa npx local e integra o servidor MCP ao monorepo principal; TradingView usa endpoint remoto com OAuth. Massive também tem instalação local registrada na documentação do projeto.

- Massive, antigo Polygon.io: repositório em https://github.com/massive-com/mcp_massive, servidor remoto em mcp.massive.com e comando de instalação local no bloco abaixo.
- CoinGecko: endpoint remoto em mcp.api.coingecko.com/mcp e comando de conexão para o Claude Code no bloco abaixo.
- CCXT: repositório em https://github.com/ccxt/ccxt/tree/master/mcp e comando npx -y ccxt-mcp no bloco abaixo, com execução local.
- TradingView: documentação em https://www.tradingview.com/mcp/docs e servidor remoto com OAuth em mcp.tradingview.com/mcp.

```
uv tool install mcp_massive @ git+https://github.com/massive-com/mcp_massive
claude mcp add --transport http coingecko https://mcp.api.coingecko.com/mcp
npx -y ccxt-mcp
```

Fonte: <https://github.com/massive-com/mcp_massive>

## Os números

A contagem descreve o tamanho da coleção. Ela mostra onde há mais opções e ajuda a escolher por onde começar, sem indicar qualidade ou cobertura de cada servidor.

- 29 entradas: total de servidores e recursos distribuídos nas seis categorias.
- 5 entradas em uso geral: GitHub, Context7, Playwright, Filesystem e Brave Search.
- 6 entradas em desenvolvimento e bancos de dados: PostgreSQL, Supabase, Neon, Sentry, Docker e Kubernetes.
- 6 entradas em equipes e negócios: Slack, Linear, Notion, Atlassian, Google Calendar e Gmail.
- 5 entradas em criação de conteúdo: Higgsfield, DaVinci Resolve, Figma, ElevenLabs e YouTube.
- 3 entradas em pagamentos e finanças: Stripe, Plaid e QuickBooks.
- 4 entradas em negociação e mercados: Massive, CoinGecko, CCXT e TradingView.
- 2 diretórios: Official MCP Servers Repository e Awesome MCP Servers.

## O que muda para você

A lista ajuda a montar um assistente com acesso deliberado. Para trabalho com código, GitHub e Playwright aparecem como caminhos; para arquivos locais, Filesystem; para bancos, Supabase, Neon e a alternativa ao PostgreSQL arquivado. A escolha parte da tarefa que você quer executar.

Exemplo: você quer avaliar uma conexão financeira sem usar dados de produção. Escolha Stripe, abra a documentação oficial e use credenciais de teste. Faça uma operação de leitura permitida e observe quais dados aparecem. Depois de verificar o comportamento, amplie o teste aos poucos, mantendo o mínimo de permissão necessário.

Um servidor remoto usa um endpoint externo. Um servidor local roda na sua máquina e pede atenção ao código, às dependências e ao caminho liberado. Essa diferença deve entrar na decisão junto com a tarefa e o nível de acesso.

Fonte: <https://docs.stripe.com/mcp>

## O que fazer hoje

Siga a sequência para testar um servidor com controle. O objetivo é validar uma conexão antes de ampliar permissões ou adicionar outras integrações.

1. Escolha, na coleção, uma entrada da categoria que resolve uma tarefa real. O resultado é um único servidor para avaliar.
2. Abra o repositório ou a documentação oficial indicada e identifique se a entrada é um servidor, uma busca, uma página de produto ou um endpoint.
3. Verifique no projeto se ele está ativamente mantido e quem o publica. O resultado é a confirmação da origem antes da instalação.
4. Leia o código-fonte, as permissões, as dependências e os dados acessados. Registre o que o servidor poderá ler ou executar.
5. Prefira permissões somente leitura quando a tarefa permitir. O teste fica com alcance reduzido para alterações.
6. Use uma versão confiável e fixe-a quando o projeto permitir. Revise a atualização antes de adotar @latest.
7. Configure o comando ou endpoint exato da seção correspondente. Confirme o destino da conexão e a conta usada na autenticação.
8. Teste com dados que não sejam de produção. Em pagamentos e finanças, use credenciais de teste ou sandbox e amplie o acesso somente após verificar o resultado.

Fonte: <https://github.com/modelcontextprotocol/servers>

## O que conferir

A seleção inclui projetos oficiais, documentação, catálogo, página de produto, endpoint e iniciativas da comunidade. Kubernetes, DaVinci Resolve e YouTube são exemplos de repositórios da comunidade nesta coleção.

O PostgreSQL oficial está arquivado. Google Calendar e Gmail estão em Developer Preview. Disponibilidade, instruções de configuração e recursos suportados podem mudar, então o estado do projeto acompanha a decisão de uso.

- Confirme a origem pelo domínio do projeto, pelo repositório oficial ou pela documentação do fornecedor.
- Uma busca no GitHub ou no catálogo indica um ponto de partida; abra o projeto encontrado para verificar quem mantém.
- Em produção, substitua o PostgreSQL arquivado pela alternativa mantida indicada.
- Considere o status de Developer Preview de Google Calendar e Gmail ao planejar o uso.
- Revise permissões, dependências e acesso a dados antes de instalar.
- Comece com somente leitura e amplie apenas o necessário para a tarefa.
- Use credenciais de teste em Stripe, Plaid e QuickBooks.
- Fixar versões confiáveis e testar dados não produtivos reduz mudanças inesperadas.

Fonte: <https://github.com/modelcontextprotocol/servers-archived/tree/main/src/postgres>

## Glossário

- MCP: protocolo que padroniza a comunicação entre um assistente de IA e ferramentas ou fontes de dados externas.
- Servidor MCP: programa ou serviço que recebe solicitações do cliente e oferece ferramentas ou dados.
- Cliente MCP: aplicativo que se conecta ao servidor, como um assistente ou ambiente de desenvolvimento.
- Endpoint: endereço para onde o cliente envia a conexão com um serviço remoto.
- Servidor local: servidor executado na sua máquina, normalmente iniciado por um comando.
- Servidor remoto: servidor hospedado fora da sua máquina e acessado por um endpoint.
- stdio: canal de comunicação local pela entrada e saída de um processo.
- Streamable HTTP: forma de comunicação com servidor MCP por HTTP, usada nos endpoints remotos do Linear e do Notion.
- OAuth: fluxo de autorização que permite conceder acesso a uma conta sem compartilhar a senha; aparece em Plaid, ElevenLabs e TradingView.
- PAT: token de acesso pessoal. No comando local do Supabase, entra no lugar de <PAT>; no comando Docker do GitHub, o token vai pela variável GITHUB_PERSONAL_ACCESS_TOKEN.
- npx: comando do ecossistema Node.js que executa pacotes e pode obtê-los quando necessário.
- Docker: plataforma de contêineres; no GitHub, o comando inicia o servidor em um contêiner.
- uvx: comando do ecossistema Python usado para executar um pacote em ambiente isolado, como na alternativa ao PostgreSQL.
- Repositório: local onde o código-fonte do projeto é publicado e pode ser examinado.
- Documentação: páginas oficiais com instruções e detalhes de configuração.
- Catálogo ou diretório: lista que ajuda a descobrir projetos; a conexão é configurada no servidor escolhido.
- Somente leitura: permissão que permite consultar dados sem autorizar alterações.
- Sandbox: ambiente de teste separado dos dados reais, recomendado para começar em pagamentos e finanças.
- Developer Preview: versão prévia para desenvolvedores; é o status de Google Calendar e Gmail nesta coleção.
- Versão fixada: escolha explícita de uma versão confiável para reduzir mudanças inesperadas.

Fonte: <https://github.com/modelcontextprotocol/servers>

## Dois diretórios para continuar

Os diretórios ampliam a busca depois da seleção inicial. O Official MCP Servers Repository reúne o repositório oficial de servidores MCP. O Awesome MCP Servers é uma lista curada de opções para explorar.

Use os diretórios para encontrar um projeto específico e depois abrir a fonte dele. A lista ajuda na descoberta; manutenção, permissões e configuração continuam sendo verificadas no projeto escolhido.

- Official MCP Servers Repository: https://github.com/modelcontextprotocol/servers, ponto de partida para os servidores do repositório oficial.
- Awesome MCP Servers: https://github.com/punkpeye/awesome-mcp-servers, lista curada para ampliar a pesquisa.

Fonte: <https://github.com/punkpeye/awesome-mcp-servers>

## Para onde ir depois

O próximo passo é escolher um servidor que resolva uma tarefa real e testá-lo com o menor acesso possível. Comece por uma entrada com documentação clara e uma forma de conexão conhecida, como um endpoint remoto ou um comando local.

Pratique a revisão de segurança: identifique a origem, confira a manutenção, leia as permissões e teste com dados que não sejam de produção. Depois de validar uma integração, use os diretórios para comparar uma segunda opção.

- Hoje: escolha uma categoria e uma entrada que resolva uma tarefa sua.
- Na primeira sessão: abra a fonte oficial e configure com o comando ou endpoint exato.
- No teste: use somente leitura e dados que não sejam de produção.
- Depois: amplie as permissões apenas se a tarefa exigir e explore os dois diretórios para encontrar outra opção.

Fonte: <https://github.com/modelcontextprotocol/servers>
