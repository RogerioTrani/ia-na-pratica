# OpenArt tem MCP e o Claude gera imagem e vídeo no chat

_2026-11-23 · tutorial_

O OpenArt reúne vários modelos de imagem e vídeo numa única conta e possui MCP, o que permite conectá-lo ao Claude para gerar imagens e vídeos direto na conversa. Com esta apostila, você aprende a ligar o OpenArt ao Claude passo a passo, desde abrir os conectores até autorizar e testar, e sai pronto para pedir imagens e vídeos sem abrir o site. Você também entende como funcionam os créditos, quais modelos estão disponíveis e quais cuidados tomar para não perder saldo nem ligar a conta errada.

## O que você terá no fim

No fim da leitura, você terá o OpenArt ligado ao Claude por MCP. A partir daí, você pede uma imagem ou um vídeo numa conversa e o resultado volta ali mesmo, sem abrir o site do OpenArt.

O Claude também passa a listar os modelos de imagem e vídeo disponíveis, enviar imagens de referência, organizar projetos e consultar quantos créditos restam. Crédito é a moeda da plataforma: cada imagem ou vídeo gerado desconta um valor do saldo.

O ganho está no contexto. O assistente que escreve o texto do carrossel é o mesmo que escreve o prompt de cada slide, então a imagem sai coerente com o texto. Você para de copiar prompt de uma aba para outra.

Fonte: <https://openart.ai/mcp/>

## Como isso funciona

O OpenArt é uma plataforma que reúne vários modelos de imagem e vídeo numa única conta. Com uma única assinatura, você tem acesso a modelos como Nano Banana Pro, GPT Image 2, Seedream, Kling e Seedance, entre outros.

MCP (Model Context Protocol) é o protocolo que permite ao Claude conversar com ferramentas externas. No caso do OpenArt, ele expõe um servidor MCP num endereço fixo. Ao registrar esse endereço nos conectores do Claude, o assistente passa a chamar as ferramentas do OpenArt como se fossem nativas.

Via MCP fica tudo mais simplificado. Você não precisa usar o Playwright MCP, que acaba ficando mais pesado, mais caro e consumindo mais créditos. O Claude cuida do texto e da estratégia, o OpenArt cuida da imagem e do vídeo.

O mesmo fluxo funciona em outros agentes. O Cursor também conecta ao OpenArt por MCP. O Codex usa a CLI do OpenArt.

Fonte: <https://openart.ai/mcp/>

## Antes de começar

Separe quatro coisas antes de começar. Sem elas, a conexão não funciona ou liga o Claude a uma conta errada.

- Uma conta no Claude, em que você consiga abrir as configurações e a área de conectores.
- Uma conta no OpenArt, com a assinatura que você pretende usar.
- Créditos disponíveis na conta do OpenArt, porque cada geração desconta do saldo.
- Um navegador, já que o login do OpenArt acontece numa página da web.

Fonte: <https://openart.ai/mcp/>

## Passo a passo

Os passos abaixo seguem a ordem da conexão. Cada item diz a ação e o resultado esperado, para você saber se deu certo.

1. Abra os conectores do Claude. Resultado esperado: a lista de conectores da sua conta aparece na tela, mesmo que esteja vazia.
2. Escolha adicionar conector customizado. Resultado esperado: abre uma janela pedindo o nome e o endereço do servidor.
3. Digite o nome do conector. Resultado esperado: o nome OpenArt fica escrito no primeiro campo da janela.
4. Cole o endereço do servidor MCP. Resultado esperado: o endereço aparece inteiro no campo de URL.
5. Clique em adicionar. Resultado esperado: o conector OpenArt entra na lista, com o botão Connect.
6. Entre na conta do OpenArt. Resultado esperado: a conta do OpenArt fica ligada ao Claude e as permissões do conector aparecem.
7. Autorize com permissão total. Resultado esperado: o OpenArt aparece conectado na lista de conectores.
8. Teste. Peça modelos, saldo e uma imagem. Resultado esperado: o Claude responde com os modelos e o saldo, e a imagem gerada aparece na própria conversa.

Fonte: <https://openart.ai/mcp/>

## Passo 1: Abra os conectores do Claude

Entre na sua conta do Claude, no app ou no site. Abra as configurações (Settings), vá em Customize e depois em Connectors. Atalho direto: https://claude.ai/new#settings/customize-connectors

Esse passo existe porque é nessa tela que o Claude guarda todas as ferramentas externas ligadas a ele. Se o OpenArt já estiver conectado, ele aparece na lista e você pode pular para o teste.

Se a opção não aparecer, confira se você está na área de conectores e não em outra página das configurações.

Fonte: <https://openart.ai/mcp/>

## Passo 2: Escolha adicionar conector customizado

Na tela de conectores, clique no botão de adicionar e escolha a opção de conector personalizado.

Esse tipo de conector liga ao Claude um servidor MCP que não vem pronto na lista. É o caso do OpenArt.

Uma janela vai abrir pedindo um nome e um endereço. Preencha os dois campos nos próximos passos.

```
+ Add > Add custom connector
```

Fonte: <https://openart.ai/mcp/>

## Passo 3: Digite o nome do conector

No primeiro campo, escreva o nome do conector. Use OpenArt.

O nome ajuda você a reconhecer a ferramenta depois, quando tiver vários conectores na lista.

Se errar a escrita, apague e digite de novo. Com o nome preenchido, o próximo campo é o do endereço do servidor.

```
OpenArt
```

Fonte: <https://openart.ai/mcp/claude-ai-image-generator/>

## Passo 4: Cole o endereço do servidor MCP

No campo da URL, cole o endereço do servidor MCP do OpenArt, exatamente como está.

Ele diz ao Claude onde o OpenArt está. Sem ele, o Claude não sabe com quem conversar.

Deixe as configurações avançadas vazias. Copie e cole em vez de digitar, porque uma letra faltando impede a conexão. Cole só o endereço, sem texto antes ou depois.

```
https://mcp.openart.ai/mcp
```

Fonte: <https://openart.ai/mcp/claude-ai-image-generator/>

## Passo 5: Clique em adicionar

Clique em Add. O Claude confere o endereço antes de salvar o conector.

Esse clique registra o OpenArt na sua conta.

Se aparecer erro, volte e confira se o endereço foi colado inteiro, sem espaço sobrando. A autorização acontece no próximo passo.

```
Add
```

Fonte: <https://openart.ai/mcp/claude-ai-image-generator/>

## Passo 6: Entre na conta do OpenArt

Clique em Connect e entre na sua conta do OpenArt, se ela pedir.

O Claude precisa saber de qual conta usar os créditos e os modelos, por isso o login aparece.

Se o login falhar, confira se você está usando a conta onde tem a assinatura e os créditos. Entrar em outra conta liga o Claude a um saldo e a projetos que não são os que você quer.

```
Connect > login no OpenArt
```

Fonte: <https://openart.ai/mcp/>

## Passo 7: Autorize com permissão total

Nas permissões do conector, escolha Always Allow. Isso libera o Claude para usar o OpenArt sem pedir confirmação a cada ação.

Com isso ele gera imagens e vídeos, lista modelos, envia referências, organiza projetos e consulta o saldo.

Com essa permissão, cada geração que você pedir desconta créditos da sua conta.

```
Always Allow
```

Fonte: <https://openart.ai/mcp/claude-ai-image-generator/>

## Exemplo completo

Imagine que você está escrevendo o roteiro de um carrossel no Claude. Em vez de abrir o site do OpenArt, copiar o prompt e voltar, você pede a imagem na mesma conversa.

Exemplo: você pede ao Claude uma imagem num estilo visual que chamou sua atenção. O resultado volta na própria conversa, com o texto e a imagem no mesmo lugar. O mesmo assistente gera o texto e o prompt de imagem de cada slide, por isso a imagem sai coerente com o texto.

Comece com um pedido simples para ver quanto saldo ele consumiu. Assim você tem uma noção de custo antes de pedir vídeos.

Fonte: <https://openart.ai/mcp/>

## Pedido de teste

Abra uma conversa nova no Claude para conferir se a conexão ficou ativa. Peça, com suas palavras, que ele liste os modelos de imagem e vídeo do OpenArt e diga quantos créditos você tem.

Se o Claude responder com a lista e o saldo, a conexão está funcionando. Depois, peça uma imagem descrevendo o que você quer.

Fonte: <https://openart.ai/mcp/>

## Teste de pronto

Confira os pontos abaixo para saber se a conexão realmente ficou ativa.

- [ ] O Claude responde com a lista de modelos de imagem e vídeo do OpenArt.
- [ ] O Claude informa quantos créditos restam na sua conta.
- [ ] A imagem gerada aparece na própria conversa, sem você entrar no site do OpenArt.
- [ ] Se o Claude disser que não tem acesso, volte à lista de conectores e confira se o OpenArt está ativo.

Fonte: <https://openart.ai/mcp/>

## Erros comuns e cuidados

Confira os pontos abaixo antes de confiar na conexão ou no saldo.

- Endereço colado com espaço sobrando ou letra faltando impede a conexão. Copie e cole o endereço inteiro.
- Se a opção de conector personalizado não aparecer, confira se você está na área de conectores e não em outra página das configurações.
- Entrar com outra conta do OpenArt liga o Claude a um saldo e a projetos que não são os seus. Use a conta onde estão a assinatura e os créditos.
- Always Allow libera o Claude a usar o OpenArt sem pedir confirmação a cada ação. Revise as permissões se não quiser gerações automáticas.
- Cada geração desconta créditos. Comece com um pedido simples para ter noção de custo antes de pedir vídeos.
- O custo real de cada geração depende da sua conta e da assinatura.

Fonte: <https://openart.ai/mcp/claude-ai-image-generator/>

## Glossário

- MCP (Model Context Protocol): protocolo que permite ao Claude conversar com ferramentas externas, como o OpenArt.
- Conector: ferramenta externa ligada à conta do Claude.
- Conector customizado: conector que você mesmo adiciona, apontando para um servidor MCP.
- Servidor MCP: endereço onde o OpenArt expõe suas ferramentas para o Claude.
- Crédito: moeda da plataforma OpenArt. Cada imagem ou vídeo gerado desconta um valor do saldo.
- Always Allow: permissão que libera o Claude a usar o OpenArt sem pedir confirmação a cada ação.
- Playwright MCP: alternativa mais pesada, que consome mais créditos. O MCP do OpenArt evita esse custo.
- Nano Banana Pro, GPT Image 2, Seedream, Kling, Seedance: modelos de imagem e vídeo disponíveis no OpenArt.

## Plano de 7 dias

- Dia 1: crie ou confirme sua conta no Claude e sua conta no OpenArt com assinatura e créditos.
- Dia 2: abra os conectores do Claude e adicione o conector customizado com o nome OpenArt.
- Dia 3: cole o endereço https://mcp.openart.ai/mcp, clique em Add e entre na conta do OpenArt.
- Dia 4: autorize com Always Allow e confira se o OpenArt aparece conectado na lista.
- Dia 5: abra uma conversa nova e peça a lista de modelos e o saldo de créditos.
- Dia 6: peça uma imagem simples e veja quanto saldo ela consumiu.
- Dia 7: peça um carrossel inteiro, com texto e imagens saindo da mesma conversa, e avalie o custo total.

## Para onde ir depois

Depois de conectar, pratique e aprofunde com os recursos abaixo.

- Guia oficial do OpenArt MCP e CLI: https://openart.ai/mcp/
- Passo a passo oficial no Claude: https://openart.ai/mcp/claude-ai-image-generator/
- Endereço do servidor MCP: https://mcp.openart.ai/mcp
- Atalho para os conectores do Claude: https://claude.ai/new#settings/customize-connectors
- Se você usa o Cursor, conecte o OpenArt por MCP. Se usa o Codex, use a CLI do OpenArt.
- Salve esta apostila para repetir o passo a passo com a tela ao lado.
- Teste primeiro com uma imagem simples para ter noção de custo antes de pedir vídeos.

Fonte: <https://openart.ai/mcp/>

## Links úteis

- Guia oficial do OpenArt MCP e CLI: https://openart.ai/mcp/
- Passo a passo oficial do OpenArt no Claude: https://openart.ai/mcp/claude-ai-image-generator/
- Endereço do servidor MCP do OpenArt: https://mcp.openart.ai/mcp
- Atalho direto para os conectores do Claude: https://claude.ai/new#settings/customize-connectors
