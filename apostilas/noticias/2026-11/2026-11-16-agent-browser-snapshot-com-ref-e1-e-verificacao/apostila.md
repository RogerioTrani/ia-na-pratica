# agent-browser snapshot com ref @e1 e verificação

_2026-11-16 · noticia_

agent-browser é um CLI nativo em Rust que dá a um agente de IA um navegador controlado por snapshots e refs. O fluxo básico é abrir a página, gerar refs com snapshot -i, agir com o ref capturado e verificar o resultado antes de seguir. O repositório vercel-labs/agent-browser acumula 47,5 mil estrelas no GitHub.

## O fato

agent-browser é um CLI nativo em Rust que dá a um agente de IA um navegador controlado por snapshots e refs. O fluxo básico é abrir a página, gerar refs com snapshot -i, agir com o ref capturado e verificar o resultado antes de seguir.

O repositório vercel-labs/agent-browser acumula 47,5 mil estrelas no GitHub. Repositório: https://github.com/vercel-labs/agent-browser. A documentação oficial está em agent-browser.dev.

Fonte: <https://github.com/vercel-labs/agent-browser>

## O que é o agent-browser

CLI nativo em Rust que envia cada comando a um daemon em background, que controla o Chrome via Chrome DevTools Protocol. O navegador permanece aberto entre comandos, e cada passo é uma chamada curta de shell.

O snapshot devolve a página como texto compacto, com um ref como @e1 para cada elemento. O agente age sobre o ref e lê a página de novo para conferir o resultado.

- Repositório vercel-labs/agent-browser: 47,5 mil estrelas no GitHub.

Fonte: <https://github.com/vercel-labs/agent-browser>

## Instalação

Instale o CLI e baixe o Chrome for Testing na primeira execução.

1. rode npm install -g agent-browser. Resultado: o CLI fica instalado.
2. rode agent-browser install. Resultado: o Chrome for Testing é baixado na primeira execução.

```
npm install -g agent-browser
agent-browser install
```

Fonte: <https://github.com/vercel-labs/agent-browser>

## Loop de uso

Abra a página, gere refs dos elementos interativos, aja sobre um ref e verifique o resultado.

1. agent-browser open example.com. Resultado: a página é aberta.
2. agent-browser snapshot -i. Resultado: os elementos interativos recebem refs, como @e1.
3. agent-browser click @e1. Resultado: a ação é feita sobre o ref capturado.
4. agent-browser get url. Resultado: você confere onde a página está.
5. agent-browser close. Resultado: a sessão é encerrada.

Fonte: <https://github.com/vercel-labs/agent-browser>

## Refs e seletores

Refs descrevem a página no momento do snapshot. Após navegação ou mudança de DOM, tire uma nova snapshot antes de reusar refs.

CSS selectors, text, XPath e semantic locators também funcionam. Exemplo com localizador semântico:

```
agent-browser find role button click --name "Submit"
```

Fonte: <https://github.com/vercel-labs/agent-browser>

## Falha segura

Um click falha, em vez de reportar sucesso, quando o alvo está oculto, desabilitado, fora do viewport ou coberto por outro elemento, como um banner de consentimento. Descarte o elemento cobridor, tire nova snapshot e tente de novo.

Fonte: <https://github.com/vercel-labs/agent-browser>

## Verificação e encerramento

Após a ação, leia a página de novo com snapshot ou com agent-browser get url para verificar o resultado antes de seguir. Ao terminar, agent-browser close encerra a sessão.

Fonte: <https://github.com/vercel-labs/agent-browser>

## O que conferir

Instalação por Homebrew: brew install agent-browser e depois agent-browser install.

No Linux, agent-browser install --with-deps também instala as bibliotecas de sistema do navegador. Uso sem instalar: npx agent-browser open example.com.

Cada --session tem daemon e navegador próprios; por padrão, o daemon fecha o navegador headless e sai após uma hora sem comandos. Anexar Chrome em execução: --cdp ou --auto-connect. Motores alternativos: --engine com Lightpanda ou Obscura.

Fonte: <https://github.com/vercel-labs/agent-browser>
