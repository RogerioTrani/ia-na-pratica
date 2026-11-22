# 29 MCPs para facilitar seu dia

_2026-11-22 · noticia_

29 servidores MCP em seis categorias, mais dois diretórios para explorar. Para cada um você tem o repositório ou a documentação e, quando existe, o servidor remoto ou o comando de conexão, copiado como está. Comece com poucos servidores, com permissão de leitura e dados que não sejam de produção.

## Uso geral

O GitHub roda em Docker ou como servidor remoto. Context7, Playwright, Filesystem e Brave Search sobem com um comando npx.

- GitHub: github.com/github/github-mcp-server · remoto: api.githubcopilot.com/mcp/
- Context7: github.com/upstash/context7 · remoto: mcp.context7.com/mcp
- Playwright: github.com/microsoft/playwright-mcp
- Filesystem: github.com/modelcontextprotocol/servers/tree/main/src/filesystem (troque /caminho/permitido pela pasta que o servidor pode acessar)
- Brave Search: github.com/brave/brave-search-mcp-server

## Desenvolvimento e bancos de dados

O repositório oficial do PostgreSQL está arquivado. Use a alternativa mantida antes de levar qualquer coisa para produção. Supabase, Neon e Sentry têm servidor remoto, e Neon e Sentry também têm comando de instalação local.

- PostgreSQL (repositório arquivado): github.com/modelcontextprotocol/servers-archived/tree/main/src/postgres
- Supabase: github.com/supabase-community/supabase-mcp · remoto: mcp.supabase.com/mcp
- Neon: github.com/neondatabase/mcp-server-neon · remoto: mcp.neon.tech/mcp
- Sentry: github.com/getsentry/sentry-mcp · remoto: mcp.sentry.dev/mcp
- Docker MCP Catalog: hub.docker.com/mcp
- Kubernetes (repositório da comunidade): github.com/containers/kubernetes-mcp-server

## Equipes e negócios

Linear, Notion e Atlassian oferecem servidor remoto. Slack tem documentação do servidor MCP. Google Calendar e Gmail têm servidor MCP do Google, ainda em Developer Preview.

- Slack: docs.slack.dev/ai/mcp-server
- Linear: linear.app/docs/mcp · remoto: mcp.linear.app/mcp
- Notion: developers.notion.com/guides/mcp/get-started-with-mcp · remoto: mcp.notion.com/mcp
- Atlassian Rovo MCP: github.com/atlassian/atlassian-mcp-server · remoto: mcp.atlassian.com/v2/mcp
- Google Calendar (Developer Preview): developers.google.com/workspace/calendar/api/guides/configure-mcp-server · remoto: calendarmcp.googleapis.com/mcp/v1
- Gmail (Developer Preview): developers.google.com/workspace/guides/configure-mcp-servers · remoto: gmailmcp.googleapis.com/mcp/v1

## Criação de conteúdo

O Higgsfield entra como conector personalizado e o ElevenLabs tem servidor hospedado com login OAuth. O Figma conecta ao Claude Code com um comando. DaVinci Resolve e YouTube são repositórios da comunidade.

- Higgsfield: higgsfield.ai/mcp · conector personalizado: mcp.higgsfield.ai/mcp
- DaVinci Resolve: github.com/samuelgursky/davinci-resolve-mcp
- Figma: developers.figma.com/docs/figma-mcp-server/ · remoto: mcp.figma.com/mcp
- ElevenLabs (servidor hospedado, OAuth): elevenlabs.io/docs/eleven-agents/operate/hosted-mcp
- YouTube: github.com/anaisbetts/mcp-youtube

## Pagamentos e finanças

Esses servidores podem mexer com dinheiro e dados bancários. Use credenciais de teste primeiro.

O QuickBooks tem repositório oficial da Intuit e roda na sua máquina, via stdio.

- Stripe: docs.stripe.com/mcp · remoto: mcp.stripe.com
- Plaid: plaid.com/docs/resources/mcp/ · remoto (Dashboard): api.dashboard.plaid.com/mcp/
- QuickBooks: github.com/intuit/quickbooks-online-mcp-server

## Negociação e mercados

O Polygon.io agora se chama Massive. O CoinGecko tem um comando pronto para o Claude Code, o CCXT roda local com npx e o TradingView usa login OAuth.

- Polygon.io (agora Massive): github.com/massive-com/mcp_massive · remoto: mcp.massive.com
- CoinGecko: remoto: mcp.api.coingecko.com/mcp
- CCXT: github.com/ccxt/ccxt/tree/master/mcp
- TradingView: tradingview.com/mcp/docs · remoto (OAuth): mcp.tradingview.com/mcp

## Dois diretórios para explorar mais

Para achar outros servidores, comece pelo repositório oficial de servidores MCP e pela lista curada Awesome MCP Servers.

- Official MCP Servers Repository: github.com/modelcontextprotocol/servers
- Awesome MCP Servers: github.com/punkpeye/awesome-mcp-servers

## Antes de instalar

Trate cada servidor como código que lê seus dados e age em seu nome. Nem todo link da lista é um servidor oficial mantido pelo fabricante, então verifique de onde ele vem.

- Confirme que o link é um servidor de verdade e não um resultado de busca ou documentação geral.
- Veja se o projeto é mantido ativamente.
- Revise o código-fonte, as permissões, as dependências e o acesso a dados.
- Comece com poucos servidores que sirvam ao seu fluxo.
- Use permissão só de leitura sempre que der.
- Fixe versões em que você confia.
- Teste com dados que não sejam de produção.

## Além do vídeo

- A lista original distingue o tipo de cada link: repositório, documentação, busca ou endpoint. Nem todo link é um servidor oficial do fabricante.
- O checklist completo de segurança: confirmar que o link é um servidor real, checar a manutenção, revisar código, permissões, dependências e acesso a dados, e fixar versões confiáveis.
- Disponibilidade, instruções de configuração e recursos suportados podem mudar com o tempo.
