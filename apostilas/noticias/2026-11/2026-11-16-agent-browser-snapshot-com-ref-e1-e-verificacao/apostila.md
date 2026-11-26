# agent-browser: snapshot, ref @e1 e verificação

_2026-11-16 · noticia_

O agent-browser é um CLI nativo em Rust da Vercel Labs que dá a um agente de IA um navegador controlado por snapshots e refs. Quem lê aprende a instalar, rodar o loop de snapshot, ação e verificação, lidar com falhas seguras e integrar o CLI a agentes e provedores de nuvem. Ao fim, saberá automatizar tarefas de navegador com passos curtos e verificáveis, sem scripts frágeis.

## O fato

A Vercel Labs publicou o agent-browser, um CLI nativo em Rust que dá a um agente de IA um navegador que ele controla um comando por vez.

O ponto central é um loop curto: o agente abre uma página, tira um snapshot que lista os elementos interativos com refs como @e1, age sobre um ref e lê a página de novo para conferir o resultado. O navegador fica aberto entre os comandos, então cada passo é uma chamada curta de shell.

A documentação oficial está em agent-browser.dev e o código-fonte em github.com/vercel-labs/agent-browser. A licença é Apache-2.0.

Fonte: <https://github.com/vercel-labs/agent-browser>

## Por que isso importa

Uma automação de navegador pode falhar quando o agente se baseia em uma versão antiga da página. O agent-browser permite trabalhar com uma descrição atualizada: o snapshot devolve a página como texto compacto, com refs que valem para aquele momento.

Isso torna o comportamento previsível. Em vez de um script longo executado de uma só vez, o agente faz uma ação, confere e decide o próximo passo. A verificação é parte do fluxo, não um extra.

O fato de o CLI ser nativo em Rust e enviar comandos a um daemon em background permite que cada chamada seja curta e independente, sem perder o estado do navegador.

Fonte: <https://github.com/vercel-labs/agent-browser>

## Como o agent-browser funciona

Cada comando é enviado a um daemon em background que inicia no primeiro comando e controla o navegador pelo Chrome DevTools Protocol. Cada sessão identificada com --session ganha daemon e navegador próprios.

Por padrão o daemon fecha o navegador headless e encerra após uma hora sem comandos, salvando o estado antes quando a persistência de sessão está configurada.

O navegador padrão é o Chrome for Testing. É possível anexar a um Chrome já aberto com --cdp ou --auto-connect, escolher o motor Lightpanda ou Obscura com --engine, controlar o Mobile Safari no simulador de iOS ou usar um provedor de navegador em nuvem como Browserbase, Browserless, Browser Use, Kernel ou AgentCore. Há também um guia para o motor Firefox.

Fonte: <https://github.com/vercel-labs/agent-browser>

## Instalação

1. Rode npm install -g agent-browser para instalar o CLI globalmente.
2. Rode agent-browser install para baixar o Chrome for Testing. Esse passo acontece só na primeira vez.
3. No Homebrew, rode brew install agent-browser e depois agent-browser install.
4. No Linux, rode agent-browser install --with-deps para instalar também as bibliotecas de sistema do navegador.
5. Sem instalar, rode npx agent-browser open example.com para experimentar.
6. Para instalação em projeto, build a partir do código, upgrade e doctor, consulte a documentação de instalação em agent-browser.dev.

```
npm install -g agent-browser
agent-browser install
```

Fonte: <https://github.com/vercel-labs/agent-browser>

## O loop central: snapshot, ação, verificação

O exemplo de início rápido tem cinco comandos. Abra a página, tire o snapshot interativo, aja sobre um ref, confira o resultado e feche.

O snapshot para example.com devolve uma linha como `- link "Learn more" [ref=e1]`. Esse ref descreve a página no momento do snapshot.

Após a ação, leia a página de novo com snapshot ou com agent-browser get url antes de seguir. Ao terminar a tarefa, agent-browser close encerra a sessão.

```
agent-browser open example.com
agent-browser snapshot -i
agent-browser click @e1
agent-browser get url
agent-browser close
```

Fonte: <https://github.com/vercel-labs/agent-browser>

## Refs e quando tirar um novo snapshot

- Refs descrevem a página no momento do snapshot. Após navegação ou mudança no DOM, tire um novo snapshot antes de reusar refs.
- Seletores CSS, texto, XPath e localizadores semânticos também funcionam, por exemplo agent-browser find role button click --name "Submit".
- Não confie em um ref antigo depois de clicar em algo que muda a página.

Fonte: <https://github.com/vercel-labs/agent-browser>

## O que acontece quando um click falha

- Um click falha em vez de reportar sucesso quando o alvo está oculto, desabilitado, fora da área visível ou coberto por outro elemento, como um banner de consentimento.
- Quando um elemento cobre o alvo, a resposta é fechar esse elemento, tirar um novo snapshot e tentar de novo.
- Esse comportamento evita que o agente aja sobre o elemento errado e pense que deu certo.

Fonte: <https://github.com/vercel-labs/agent-browser>

## Encaixes no ecossistema: sessões, motores e provedores

Cada --session tem daemon e navegador próprios, o que permite rodar fluxos isolados ao mesmo tempo.

Além do Chrome for Testing, o CLI anexa a um Chrome em execução, escolhe motores alternativos e controla o Mobile Safari no simulador de iOS.

Provedores em nuvem suportados incluem Browserbase, Browserless, Browser Use, Kernel e AgentCore. Há guia específico para o motor Firefox.

Fonte: <https://github.com/vercel-labs/agent-browser>

## Skills, MCP e integração com agentes

O CLI entrega skills que acompanham a versão instalada. Comandos como agent-browser skills get core carregam o loop central, refs, espera e fluxos comuns. As variantes --ref commands e --full adicionam referência de comandos e templates.

agent-browser skills list mostra skills especializadas, como electron, slack e dogfood.

Para instalar a skill de descoberta em um harness de agente, rode npx skills add vercel-labs/agent-browser. A skill instalada é um stub fino que manda o agente carregar agent-browser skills get core, então as instruções sempre batem com o CLI instalado.

Alternativa: adicione ao AGENTS.md a instrução para usar agent-browser e rodar agent-browser skills get core antes do primeiro uso.

Para clientes MCP, agent-browser mcp inicia um servidor MCP sobre stdio.

```
agent-browser skills get core
agent-browser skills get core --ref commands
agent-browser skills get core --full
agent-browser skills list
npx skills add vercel-labs/agent-browser
agent-browser mcp
```

Fonte: <https://github.com/vercel-labs/agent-browser>

## Comandos disponíveis

Rode agent-browser --help para a lista completa ou agent-browser <comando> --help para um comando. Os comandos se agrupam por função.

- Navegar e ler: open, back, forward, reload, read, snapshot, get, is.
- Interagir: click, dblclick, fill, type, press, keyboard, hover, focus, select, check, uncheck, scroll, drag, upload, mouse, find.
- Esperar: wait.
- Capturar: screenshot, pdf, record, download, diff.
- Estado de página e rede: cookies, storage, network, set, clipboard, eval, pushstate.
- Abas, frames e diálogos: tab, frame, dialog.
- Depuração e desempenho: console, errors, highlight, inspect, trace, profiler, vitals, react, a11y.
- Sessões e autenticação: session, state, auth, profiles, confirm, deny.
- Agentes e integrações: skills, mcp, webmcp, flow, chat, batch, plugin.
- Observar: stream, dashboard.
- Configuração: install, upgrade, doctor, connect, close.
- Flags, variáveis de ambiente e agent-browser.json estão documentados em Configuration.

Fonte: <https://github.com/vercel-labs/agent-browser>

## Plataformas e requisitos

- Binários nativos existem para macOS (ARM64, x64), Linux (ARM64, x64, glibc e musl) e Windows (x64). O pacote npm escolhe o binário certo para o host.
- Para build a partir do código: Node.js 24 ou superior, pnpm 11 ou superior e Rust.
- Comandos de verificação do Rust, a partir de cli/: cargo fmt -- --check, cargo clippy, cargo test e cargo test e2e -- --ignored --test-threads=1.

Fonte: <https://github.com/vercel-labs/agent-browser>

## Os números

- 47,5 mil estrelas no GitHub: número exibido na página do repositório.
- 105 pessoas acompanhando o repositório.
- Uma hora sem comandos: tempo padrão para o daemon fechar o navegador headless e encerrar, salvando estado quando persistência está configurada.
- Chrome for Testing: navegador padrão baixado na primeira instalação.

Fonte: <https://github.com/vercel-labs/agent-browser>

## O que muda para você

Imagine um agente que precisa preencher um formulário em um site. Em vez de escrever um script frágil com seletores, ele abre a página, tira snapshot -i, vê o campo de e-mail com um ref como @e3, preenche o campo com o comando fill usando esse ref, tira um novo snapshot para conferir e só então clica em enviar.

Se um banner de consentimento cobrir o botão, o click falha em vez de fingir sucesso. O agente fecha o banner, tira um novo snapshot e tenta de novo. O resultado é um fluxo auditável passo a passo.

Fonte: <https://github.com/vercel-labs/agent-browser>

## O que fazer hoje

1. Instale com npm install -g agent-browser e rode agent-browser install.
2. Abra uma página de teste com agent-browser open example.com.
3. Rode agent-browser snapshot -i e observe os refs gerados.
4. Execute uma ação simples, como agent-browser click @e1, e confira com agent-browser get url.
5. Encerre com agent-browser close.
6. Leia a documentação em agent-browser.dev para flags, variáveis de ambiente e configuração.
7. Se você usa um harness de agente, instale a skill de descoberta com npx skills add vercel-labs/agent-browser.

Fonte: <https://github.com/vercel-labs/agent-browser>

## O que conferir

- Refs expiram depois de navegação ou mudança no DOM. Sempre tire um novo snapshot antes de reusar.
- Click falha em alvo oculto, desabilitado, fora da área visível ou coberto. Trate a falha como informação, não como erro.
- O daemon encerra após uma hora sem comandos por padrão. Configure persistência de sessão se precisar manter estado.
- O build a partir do código exige Node.js 24+, pnpm 11+ e Rust. Verifique as versões antes de compilar.
- A licença é Apache-2.0. Confira os termos antes de redistribuir.
- Não confie em links ou comandos fora do repositório oficial ou da documentação oficial.

Fonte: <https://github.com/vercel-labs/agent-browser>

## Glossário

- CLI: interface de linha de comando, programa usado no terminal.
- Daemon: processo em background que recebe comandos e controla o navegador.
- CDP: Chrome DevTools Protocol, protocolo usado para controlar o Chrome.
- Snapshot: captura da página como texto, com refs para elementos interativos.
- Ref: identificador como @e1 que aponta para um elemento no momento do snapshot.
- DOM: estrutura da página HTML que pode mudar após ações.
- MCP: Model Context Protocol, interface para conectar o CLI a clientes de IA.
- Headless: navegador sem interface gráfica, rodando em segundo plano.
- Chrome for Testing: build do Chrome usado por padrão pelo CLI.

Fonte: <https://github.com/vercel-labs/agent-browser>

## Desenvolvimento a partir do código

Quem quiser contribuir ou rodar a partir do código precisa de Node.js 24 ou superior, pnpm 11 ou superior e Rust.

- Build a partir do código: pnpm install, pnpm build:source, pnpm link --global e agent-browser install.
- Verificações Rust a partir de cli/: cargo fmt -- --check, cargo clippy, cargo test e cargo test e2e -- --ignored --test-threads=1.

```
pnpm install
pnpm build:source
pnpm link --global
agent-browser install
cargo fmt -- --check
cargo clippy
cargo test
cargo test e2e -- --ignored --test-threads=1
```

Fonte: <https://github.com/vercel-labs/agent-browser>

## Para onde ir depois

- Leia a documentação em agent-browser.dev, começando por quick start e commands.
- Explore as skills com agent-browser skills get core e agent-browser skills list.
- Teste fluxos reais em sites próprios antes de automatizar produção.
- Configure sessões e persistência para tarefas longas.
- Acompanhe o changelog no repositório para novidades.

Fonte: <https://github.com/vercel-labs/agent-browser>

## Além do vídeo

- O repositório inclui pastas de exemplos, benchmarks, evals, docker e pacotes.
- Existe um arquivo AGENTS.md que lista arquivos a atualizar a cada mudança, checagens de documentação e processo de release.
- A documentação inclui guias de segurança com auth vault, listas de domínios permitidos, políticas de ação e limites de conteúdo.
- Há guias específicos para rodar o agent-browser no Vercel Sandbox e em agentes eve.
- O CLI oferece comandos de observação como stream e dashboard, além de webmcp, flow, chat, batch e plugin.
- A documentação inclui páginas de Next.js e Vercel, além de changelog no repositório.
- As skills do CLI acompanham a versão instalada; a skill de descoberta, instalada via skills.sh, é um stub fino que redireciona para agent-browser skills get core.
