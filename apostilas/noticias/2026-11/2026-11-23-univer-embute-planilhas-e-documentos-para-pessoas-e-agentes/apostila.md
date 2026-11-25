# Univer embute planilhas e documentos para pessoas e agentes

_2026-11-23 · noticia_

O Univer, da dream-num, é um Office SDK para embutir edição, cálculo, colaboração e processamento de arquivos no seu produto, para pessoas e agentes de IA. O núcleo com Sheets, Docs, motor de fórmulas e Facade APIs é aberto sob Apache-2.0. Server SDK, plugins comerciais e extensões de IA são distribuídos e licenciados à parte.

## O fato

O Univer, da dream-num, é um Office SDK para embutir edição, cálculo, colaboração e processamento de arquivos no seu produto, para pessoas e agentes de IA, com seus dados e permissões. O núcleo com Sheets, Docs, motor de fórmulas e Facade APIs é aberto sob Apache-2.0. Server SDK, plugins comerciais e extensões de IA são distribuídos e licenciados à parte.

Repositório: https://github.com/dream-num/univer

Fonte: <https://github.com/dream-num/univer>

## O que é o Univer

O Univer Office SDK leva edição, cálculo, colaboração e processamento de arquivos para dentro do seu produto. O mesmo recurso atende quem edita na tela e agentes que operam planilhas e documentos por código. A família cobre planilhas, documentos, apresentações, tabelas relacionais, canvas e PDFs.

Fonte: <https://github.com/dream-num/univer>

## As três partes do SDK

O pacote tem três partes.

- Web SDK: a base. Traz modelos de conteúdo, edição, renderização, cálculo de fórmulas e Facade APIs (as APIs voltadas ao aplicativo). Também roda sem editor, em modo headless, reaproveitando modelos, comandos e cálculo.
- Server SDK: serviços de backend para colaboração em tempo real, histórico de edições e importação e exportação de arquivos Office.
- AI SDK: liga os recursos de Office a agentes e fluxos existentes, com ferramentas de conteúdo, execução e revisão.

Fonte: <https://github.com/dream-num/univer>

## O que é aberto e o que é comercial

O repositório traz sob Apache-2.0 a arquitetura central do Web SDK: modelos de conteúdo e formatos de snapshot, gestão de plugins e dependências, sistema de comandos, motores de fórmula e renderização, Facade APIs, base de interface e a edição de Sheets e Docs.

Plugins comerciais do Web SDK, o Server SDK e as extensões comerciais do AI SDK são distribuídos e licenciados separadamente. Agentes também podem usar as mesmas APIs abertas: o seu aplicativo entrega o modelo e a orquestração das ferramentas.

Fonte: <https://github.com/dream-num/univer>

## Recursos abertos de Sheets e Docs

Importar e exportar XLSX usa a conversão de arquivos, distribuída separadamente.

- Sheets, edição e layout: estilos de célula, células mescladas, texto rico na célula, painéis congelados, imagens flutuantes e desfazer/refazer.
- Sheets, dados e cálculo: fórmulas, nomes definidos, filtros, ordenação, validação de dados, formatação condicional, hiperlinks, comentários e localizar e substituir.
- Docs: edição de texto rico, formatação de parágrafo, listas, hiperlinks, comentários e integração de desenhos.

Fonte: <https://github.com/dream-num/univer>

## Comece: editor de planilha em poucas linhas

Num aplicativo de navegador com bundler, como o Vite, instale os pacotes. Depois, crie o contêiner antes de inicializar o Univer, inicialize com o preset Sheets Core e chame univerAPI.createWorkbook para ter o editor na página. Use o univerAPI retornado para trabalhar com o conteúdo. Esse exemplo usa só pacotes abertos, sem licença comercial nem Server SDK. Em frameworks de componentes, guarde a instância retornada por createUniver e chame univer.dispose() quando o componente for desmontado. Documentação: https://docs.univer.ai/

1. instale os pacotes com o comando abaixo. Resultado: os pacotes do editor ficam no projeto.
2. crie o contêiner e inicialize com o preset Sheets Core. Resultado: o editor aparece na página.

```
pnpm add @univerjs/presets @univerjs/preset-sheets-core
```

Fonte: <https://github.com/dream-num/univer>

## Salvar e restaurar a planilha

workbook.save() devolve um snapshot em JSON com a planilha e os dados dos plugins registrados. A persistência fica com o seu aplicativo; o exemplo usa o armazenamento do navegador. Na próxima carga da página, restaure o snapshot em vez de criar uma planilha em branco:

```
const saved = localStorage.getItem('quotation')
if (saved) {
  univerAPI.createWorkbook(JSON.parse(saved))
}
```

Fonte: <https://github.com/dream-num/univer>

## Links oficiais e o que conferir

Fato: o núcleo é Apache-2.0, e os plugins comerciais, o Server SDK e as extensões de IA são licenciados à parte.

Repositório: https://github.com/dream-num/univer. Documentação: https://docs.univer.ai/. Site: https://univer.ai/

Fonte: <https://univer.ai/>
