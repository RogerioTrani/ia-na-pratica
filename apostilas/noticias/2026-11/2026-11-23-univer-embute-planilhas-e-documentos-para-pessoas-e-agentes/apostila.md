# Univer embute planilhas e documentos para pessoas e agentes

_2026-11-23 · noticia_

Univer é um Office SDK da DreamNum para montar aplicativos de escritório dentro do seu próprio produto, com edição, cálculo, colaboração e processamento de arquivos para pessoas e agentes de IA. O núcleo aberto, sob Apache-2.0, cobre Sheets e Docs; colaboração em tempo real, conversão de arquivos e recursos de IA são camadas comerciais distribuídas à parte. Depois de ler, você sabe o que cada um dos três SDKs faz, como embutir um editor de planilha em poucas linhas, como integrar sua aplicação via Facade APIs e o que conferir antes de usar em produção.

## O fato

Univer é um Office SDK para montar aplicativos de escritório dentro do seu próprio produto. A DreamNum Co., Ltd. mantém o repositório dream-num/univer no GitHub, que traz a base aberta.

A proposta é embutir um escritório completo no seu aplicativo. O mesmo recurso atende quem edita na tela e agentes que operam planilhas e documentos por código, usando seus dados e permissões.

A família de produtos cobre planilhas, documentos, apresentações, tabelas relacionais, telas (canvases) e PDFs. Edição, cálculo, colaboração e processamento de arquivos ficam disponíveis para pessoas e agentes de IA.

Fonte: <https://github.com/dream-num/univer>

## Por que isso importa

Em vez de enviar o usuário para um editor pronto ou depender de um serviço externo, você coloca o editor dentro do seu produto: seus dados, suas permissões, sua interface.

Isso vale para dois casos: embutir uma superfície de edição (Sheets ou Docs) em um aplicativo ou agente, e processar conteúdo sem editor, em modo headless, em Node.js para tarefas automatizadas.

A base é aberta (Apache-2.0) para Sheets e Docs. Colaboração em tempo real, conversão de arquivos e recursos de IA são camadas comerciais que estendem a mesma arquitetura.

## Web SDK: a fundação

Web SDK é a fundação: modelos de conteúdo, edição, renderização, cálculo de fórmulas e Facade APIs (APIs voltadas para a aplicação).

Componha seus plugins em um editor embutido ou em um aplicativo de escritório próprio. Reutilize modelos, comandos e cálculo para processamento headless sem editor interativo.

Este repositório fornece a arquitetura central e as implementações de motor sob Apache-2.0: modelos de conteúdo e formatos de snapshot, gerenciamento de plugins e dependências, sistema de comandos, motores de fórmula e renderização, Facade APIs, base de UI e capacidades de edição de Sheets e Docs.

## Server SDK: colaboração, histórico e arquivos

Server SDK adiciona serviços de backend para colaboração em tempo real, histórico de edições e importação/exportação de arquivos Office.

Entra quando o produto precisa de várias pessoas no mesmo arquivo, ou de abrir e salvar formatos do Office (XLSX, DOCX, PPTX). Distribuído e licenciado separadamente.

Colaboração empacota mutações em changesets, aplica transformação operacional (OT) a mudanças concorrentes e gerencia revisões confirmadas e snapshots. O histórico pode reconstruir uma revisão a partir de um snapshot e dos changesets seguintes.

## AI SDK: agentes e fluxos

AI SDK liga as capacidades de Office a agentes e fluxos existentes, com ferramentas de conteúdo, execução e revisão.

Agentes usam as mesmas APIs abertas; sua aplicação fornece o modelo e a orquestração das ferramentas. O AI SDK constrói sobre os modelos headless, comandos, cálculo e Facade APIs do Web SDK.

Expõe APIs TypeScript estruturadas e presets opcionais de Commander para compor seu próprio CLI ou ferramentas de agente. Sua aplicação é dona do CLI raiz, dos alvos, da autorização e da saída.

## Capacidades abertas do núcleo

A base aberta cobre planilhas e documentos. Recursos são compostos por plugins e presets; o início rápido usa só o preset Sheets Core. Imagens usam os plugins de desenho correspondentes.

Veja a comparação de recursos no site para cobertura detalhada entre código aberto e comercial.

- Sheets · Edição e layout: estilos de célula, células mescladas, texto rico em célula, painéis congelados, imagens flutuantes e desfazer/refazer.
- Sheets · Dados e cálculo: fórmulas, nomes definidos, filtragem, ordenação, validação de dados, formatação condicional, hiperlinks, comentários e localizar/substituir.
- Docs: edição de texto rico, formatação de parágrafo, listas, hiperlinks, comentários e integração com desenhos.

Fonte: <https://github.com/dream-num/univer>

## Licenciamento: núcleo aberto, extensões comerciais

Apache-2.0 vale para Sheets, Docs, motor de fórmulas e Facade APIs. Plugins comerciais do Web SDK, Server SDK e extensões de IA são distribuídos e licenciados separadamente.

Avaliação freemium inclui marcas d'água e limites de recursos. Aplicativos de referência de código aberto, como o Univer Workspace, têm suas próprias licenças; suas dependências de SDK mantêm as respectivas licenças.

O núcleo pode ser usado em aplicações comerciais sob Apache-2.0. Capacidades comerciais (gráficos, formas, tabelas dinâmicas, SmartArt e outras) seguem os padrões de plugin, injeção de dependência, comando/mutação e extensão de Facade do núcleo.

## Os números

- 6.050 commits: desenvolvimento ativo.
- 578 observadores: pessoas acompanhando mudanças.
- Node.js >= 18.17.0 para Univer headless; desenvolvimento do monorepo exige Node.js >= 22.18.
- Navegadores: Edge >= 88, Firefox >= 90, Chrome >= 88, Safari >= 14.1, Electron >= 12. Alvo de compilação Chrome 88.
- React: camada de visão construída em React 18, suporta 18 e 19, compatibilidade mínima com 16.9+ e 17.
- Polyfill: Univer depende de Intl.Segmenter; adicione um polyfill como @formatjs/intl-segmenter se o alvo não fornecer.

## O que muda para você

Você pode embutir um editor de planilha ou documento no seu produto e deixar que a aplicação e o editor operem sobre a mesma pasta de trabalho. Fórmulas recalculam automaticamente. Você persiste um snapshot JSON e restaura em carga posterior.

Agentes podem usar as mesmas APIs abertas para inspecionar, editar e checar conteúdo. Sua aplicação fornece o modelo e a orquestração.

Exemplo: montar uma cotação onde a aplicação altera uma quantidade e o total recalcula sozinho, depois salvar o snapshot no armazenamento do navegador.

## Início rápido: editor de planilha em poucas linhas

Instale os pacotes abertos, crie o contêiner e inicialize com o preset Sheets Core. Este exemplo usa só pacotes abertos e não exige licença comercial nem Server SDK.

1. instale os pacotes com pnpm add @univerjs/presets @univerjs/preset-sheets-core.
2. crie o contêiner antes de inicializar: <div id="app" style="height: 100vh"></div>.
3. importe o preset, os locales e o CSS; crie a instância com createUniver, locale EN_US e o preset Sheets Core apontando para o contêiner 'app'.
4. chame univerAPI.createWorkbook({}) para criar a pasta de trabalho; o editor aparece na página.
5. use univerAPI para trabalhar com o conteúdo.
6. em frameworks de componentes, mantenha a instância univer retornada por createUniver e chame univer.dispose() ao desmontar o componente.
7. mantenha os pacotes @univerjs/* coordenados na mesma versão.

```
pnpm add @univerjs/presets @univerjs/preset-sheets-core
<div id="app" style="height: 100vh"></div>
import { UniverSheetsCorePreset } from '@univerjs/preset-sheets-core'
import UniverPresetSheetsCoreEnUS from '@univerjs/preset-sheets-core/locales/en-US'
import { createUniver, LocaleType, mergeLocales } from '@univerjs/presets'
import '@univerjs/preset-sheets-core/lib/index.css'
const { univerAPI } = createUniver({
  locale: LocaleType.EN_US,
  locales: {
    [LocaleType.EN_US]: mergeLocales(UniverPresetSheetsCoreEnUS),
  },
  presets: [
    UniverSheetsCorePreset({
      container: 'app',
    }),
  ],
})
univerAPI.createWorkbook({})
```

Fonte: <https://github.com/dream-num/univer>

## Facade APIs: aplicação e editor na mesma pasta de trabalho

Facade APIs são a interface voltada para a aplicação, sobre pastas de trabalho, planilhas e intervalos. O editor e sua aplicação operam sobre a mesma pasta de trabalho; mudanças de fórmula recalculam automaticamente.

univerAPI.getActiveWorkbook() retorna a pasta de trabalho ativa; workbook.getActiveSheet() a planilha ativa; sheet.getRange('A1:D4').setValues(...) preenche células; sheet.getRange('B2').setValue(4) altera uma célula e recalcula o total.

workbook.save() retorna um snapshot JSON com a pasta de trabalho e os dados dos plugins registrados. Sua aplicação é dona da persistência. Em carga posterior, após a inicialização, restaure o snapshot em vez de criar uma pasta em branco.

Snapshot de persistência é separado da importação/exportação XLSX, que usa as capacidades de conversão de arquivos distribuídas separadamente. Use as Facade APIs públicas para integração e consulte a política de estabilidade de API antes de depender de um ponto de extensão.

```
// Wait for formula controllers before editing a newly created workbook.
await new Promise<void>((resolve) => {
  if (univerAPI.getCurrentLifecycleStage() >= univerAPI.Enum.LifecycleStages.Steady) {
    resolve()
    return
  }
  const listener = univerAPI.addEvent(univerAPI.Event.LifeCycleChanged, ({ stage }) => {
    if (stage === univerAPI.Enum.LifecycleStages.Steady) {
      listener.dispose()
      resolve()
    }
  })
})
const workbook = univerAPI.getActiveWorkbook()!
const sheet = workbook.getActiveSheet()
sheet.getRange('A1:D4').setValues([
  ['Item', 'Quantity', 'Unit price', 'Amount'],
  ['Seats', 2, 25, '=B2*C2'],
  ['Support', 1, 100, '=B3*C3'],
  ['Total', '', '', '=SUM(D2:D3)'],
])
// An application control or agent can make the same edit.
sheet.getRange('B2').setValue(4)
univerAPI.getFormula().onCalculationResultApplied().then(() => {
  console.log(sheet.getRange('D4').getValue()) // 200
  localStorage.setItem('quotation', JSON.stringify(workbook.save()))
}).catch(console.error)
```

Fonte: <https://github.com/dream-num/univer>

## Facade APIs: aplicação e editor na mesma pasta de trabalho (continuação)

Em uma carga posterior da página, depois da inicialização, use o trecho abaixo no lugar de criar uma pasta de trabalho em branco.

```
const saved = localStorage.getItem('quotation')
if (saved) {
  univerAPI.createWorkbook(JSON.parse(saved))
}
```

Fonte: <https://github.com/dream-num/univer>

## Modo Plugin: controle manual

Use o Modo Plugin quando precisar de controle preciso sobre seleção de plugins, dependências ou carregamento. O preset cuida dessa composição automaticamente.

Essa inicialização alternativa substitui a do preset: usa o mesmo contêiner 'app' e o conjunto de plugins de navegador do preset Sheets Core, sem Worker. Você instala os pacotes @univerjs/* um a um, cria a instância com new Univer, registra cada plugin com univer.registerPlugin e obtém a API com FUniver.newAPI(univer). Depois disso, o exemplo da cotação roda com o univerAPI retornado.

Descarte a instância univer quando o contêiner for desmontado. Presets compõem plugins e registram suas Facade APIs.

O registro dos plugins segue a ordem abaixo. Os plugins de Docs dão suporte à edição de texto rico na planilha. Ao adicionar um recurso, inclua as extensões Facade, os pacotes de locale e os estilos de UI correspondentes. O código completo, com comandos de instalação e imports, está no README do repositório.

- UniverNetworkPlugin, UniverDocsPlugin e UniverRenderEnginePlugin.
- UniverUIPlugin (com o contêiner 'app') e UniverDocsUIPlugin.
- UniverFormulaEnginePlugin, UniverSheetsPlugin e UniverSheetsUIPlugin.
- UniverSheetsNumfmtPlugin e UniverSheetsNumfmtUIPlugin.
- UniverSheetsFormulaPlugin e UniverSheetsFormulaUIPlugin.

Fonte: <https://github.com/dream-num/univer>

## Arquitetura: três camadas e comandos

Univer organiza lógica de conteúdo e interação de UI em plugins separados. Plugins de recurso gerenciam regras e mudanças de conteúdo; plugins de UI fornecem a interface e as interações.

Três camadas: plugins de recurso (ex.: filtro) constroem sobre plugins de produto (ex.: Sheets), que reutilizam o framework central (UI, motor de fórmula, motor de renderização, core).

Dentro de um recurso: Model, Controller, Service, Command/Mutation e Facade API; na UI: View, UI Controller e UI Service. A base de UI usa @univerjs/design (componentes e estilos), @univerjs/ui (menus, atalhos, painéis, registro de componentes) e @univerjs/icons.

Sistema de comandos: Command orquestra uma ação de negócio e as mudanças necessárias; Mutation altera conteúdo salvo no snapshot, com parâmetros serializáveis; Operation altera estado transitório, como painel aberto ou posição de rolagem.

Para uma edição desfazível, a implementação fornece as mutações diretas e as inversas, e o Command as registra via IUndoRedoService. Uma ação que afeta vários recursos combina suas mudanças e dados de desfazer em um único registro.

Facade APIs envolvem as capacidades em objetos de aplicação (FWorkbook, FWorksheet, FRange). Cada plugin contribui suas extensões de Facade, eventos tipados via univerAPI.Event e enums via univerAPI.Enum. BeforeCommandExecute pode inspecionar e cancelar uma execução; CommandExecuted notifica ouvintes.

## Padrões de aplicação

Univer Workspace é um aplicativo de referência: mostra como compor editores, colaboração, capacidades de arquivo, agentes existentes e revisão humana em um workspace auto-hospedável.

Web App × Sheet (experimental): vincule controles a células; o aplicativo escreve na planilha e mudanças na planilha atualizam o aplicativo.

Agentes e conteúdo de escritório editável: conversas, edição de planilha e conteúdo Office em um só workspace. Com as capacidades de colaboração e web correspondentes, o Worktree permite que agentes editem e verifiquem um rascunho isolado ao longo de várias rodadas, depois entreguem a uma pessoa para revisar, mesclar ou reabrir.

## Compatibilidade, requisitos e desenvolvimento local

Compatibilidade de runtime, requisitos de desenvolvimento e estrutura do repositório.

- Navegadores: Edge >= 88, Firefox >= 90, Chrome >= 88, Safari >= 14.1, Electron >= 12. Alvo de compilação Chrome 88.
- Polyfill: Univer depende de Intl.Segmenter; adicione @formatjs/intl-segmenter se o alvo não fornecer.
- Ferramentas de build: recomenda-se Vite, esbuild ou Webpack 5. Webpack 4 pode exigir mapeamento de caminhos extra (sem suporte ao campo exports).
- React: camada de visão em React 18; suporta 18 e 19; compatibilidade mínima com 16.9+ e 17.
- Node.js: headless suporta >= 18.17.0; desenvolvimento do monorepo exige >= 22.18.
- Desenvolvimento local: git clone https://github.com/dream-num/univer.git; cd univer; pnpm install; pnpm dev. Comandos: pnpm dev, pnpm build, pnpm test, pnpm typecheck, pnpm lint, pnpm storybook:dev.
- Layout do repositório: packages/ (pacotes centrais, motores, tipos de documento, plugins de UI e recurso), examples/ (workbench Vite), common/ (ferramentas internas), tests/ (integração), docs/ (notas de arquitetura).

## O que fazer hoje

1. abra o repositório oficial (github.com/dream-num/univer) e leia o README para confirmar versões e requisitos.
2. confira a licença do que você vai usar: núcleo Apache-2.0; colaboração, conversão de arquivos e IA são comerciais.
3. rode o início rápido (pnpm add @univerjs/presets @univerjs/preset-sheets-core) em um projeto com bundler (Vite) e veja o editor aparecer.
4. teste a integração via Facade APIs: crie uma pasta de trabalho, preencha células, altere um valor e leia o total recalculado.
5. se precisar de persistência, salve o snapshot com workbook.save() e restaure em carga posterior.
6. se precisar de colaboração ou XLSX, avalie o Server SDK (comercial) e a conversão de arquivos.
7. leia a documentação (docs.univer.ai) e a política de estabilidade de API antes de depender de pontos de extensão.

## O que conferir

- Licença: o núcleo é Apache-2.0, mas plugins comerciais, Server SDK e extensões de IA são pagos e distribuídos à parte. Avaliação freemium tem marcas d'água e limites.
- Versões: mantenha os pacotes @univerjs/* coordenados na mesma versão; pacotes comerciais devem usar a linha de release correspondente; ícones seguem compatibilidade declarada.
- Polyfill Intl.Segmenter: se o navegador ou runtime alvo não fornecer, adicione @formatjs/intl-segmenter.
- Persistência vs XLSX: snapshot JSON (workbook.save()) é persistência própria; importar/exportar XLSX usa conversão de arquivos distribuída separadamente.
- Compatibilidade de navegador: alvo Chrome 88; verifique Edge >= 88, Firefox >= 90, Chrome >= 88, Safari >= 14.1, Electron >= 12.
- Node.js: headless exige >= 18.17.0; desenvolvimento do monorepo exige >= 22.18.
- Slides e Boards (telas): capacidades atuais são produtos comerciais distribuídos separadamente, não estão no núcleo aberto.
- React: camada de visão em React 18; suporte mínimo a 16.9+ e 17.
- APIs internas: use Facade APIs públicas para integração; consulte a política de estabilidade antes de depender de pontos de extensão.

## Glossário

- Office SDK: kit de desenvolvimento para montar aplicativos de escritório dentro do seu próprio produto.
- Web SDK: fundação com modelos de conteúdo, edição, renderização, cálculo de fórmulas e Facade APIs.
- Server SDK: serviços de backend para colaboração em tempo real, histórico de edições e importação/exportação de arquivos Office.
- AI SDK: conecta capacidades de Office a agentes e fluxos, com ferramentas de conteúdo, execução e revisão.
- Facade API: interface voltada para a aplicação sobre pastas de trabalho, planilhas e intervalos.
- Headless: processamento sem editor interativo, reutilizando modelos, comandos e cálculo.
- Plugin: módulo que adiciona um recurso; separa lógica de conteúdo e interação de UI.
- Preset: composição de plugins que registra suas Facade APIs (ex.: Sheets Core).
- Snapshot: representação serializável de uma pasta de trabalho (ex.: IWorkbookData) com dados de plugins.
- Mutation: mudança de conteúdo salva no snapshot, com parâmetros serializáveis.
- Command: orquestra uma ação de negócio e as mudanças necessárias.
- Operation: mudança de estado transitório, como painel aberto ou posição de rolagem.
- Unit: convenção de snapshot compartilhada entre editor, backend e agentes.
- OT (transformação operacional): técnica para aplicar mudanças concorrentes em colaboração.
- Changeset: pacote de mutações em colaboração.
- Worktree: rascunho isolado para agentes editarem e verificarem antes da revisão humana.
- Apache-2.0: licença de código aberto do núcleo.

## Para onde ir depois

- Repositório oficial: github.com/dream-num/univer (código, issues, releases).
- Documentação oficial: docs.univer.ai (guias, referência de API, showcase, blog).
- Site oficial: univer.ai (comparação de recursos, demos).
- Univer Workspace: github.com/dream-num/univer-workspace (aplicativo de referência).
- Discord: discord.gg/z3NKNT6D2f (comunidade).
- X: @univerhq.
- Open Collective: opencollective.com/univer (apoio).
- API Reference: docs.univer.ai/reference/classes/univer.
- Showcase: docs.univer.ai/showcase.
- Blog: docs.univer.ai/blog.
- Leia a política de estabilidade de API e o guia de contribuição antes de depender de pontos de extensão.

## Links citados

- https://docs.univer.ai/
- https://univer.ai/

## Além do vídeo

- A lista de integrações de agente: Univer CLI, Univer Office para DeepSeek, WorkBuddy, OpenClaw e Univer SDK Skills.
- Os diagramas de arquitetura (três camadas de plugins e organização de código de um recurso) e o fluxograma do comando de inserção de linha.
- O código completo do Modo Plugin, com o registro manual dos plugins e as extensões Facade.
- A lista completa de pacotes do monorepo e a estrutura detalhada de packages/, examples/, common/, tests/, docs/.
- A tabela completa de escopo e licenciamento (open-source core, plugins comerciais do Web SDK, Server SDK, extensões de IA).
- Os demos do showcase (Sheets, Docs, Web App, Universe, Slides, tabelas relacionais, canvases, PDF).
- Políticas de segurança, código de conduta, patrocinadores e canais de contribuição.
- O guia headless para processamento em Node.js e a arquitetura isomórfica.
