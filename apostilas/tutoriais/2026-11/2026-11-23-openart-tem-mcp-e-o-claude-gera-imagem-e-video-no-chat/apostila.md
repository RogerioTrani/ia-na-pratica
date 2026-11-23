# OpenArt tem MCP e o Claude gera imagem e vídeo no chat

_2026-11-23 · tutorial_

Este guia liga o OpenArt ao Claude por um servidor MCP. Depois de conectado, você pede imagens e vídeos na conversa e o resultado volta ali mesmo, sem abrir o site. O Claude também lista os modelos, envia imagens de referência, organiza projetos e consulta o saldo de créditos. Os passos vão do cadastro do conector até o primeiro teste.

## O que muda no seu fluxo

O OpenArt reúne modelos como Nano Banana Pro, GPT Image 2, Seedream e Kling numa assinatura só. Com o conector ativo, o Claude gera imagens e vídeos no OpenArt e devolve o resultado na própria conversa.

O mesmo assistente que escreve o roteiro de um carrossel escreve o prompt de cada imagem, então imagem e texto saem coerentes. Crédito é a moeda da plataforma: cada imagem ou vídeo gerado desconta um valor do saldo, o mesmo que no site.

O Cursor também conecta por MCP, e o Codex usa a CLI do OpenArt.

Fonte: <https://openart.ai/mcp/>

## Antes de começar

- Uma conta no Claude, com acesso às configurações e à área de conectores.
- Uma conta no OpenArt, com a assinatura que você pretende usar.
- Créditos na conta do OpenArt, porque cada geração desconta do saldo.
- Um navegador, já que o login do OpenArt acontece numa página da web.

## Passo 1: abra os conectores do Claude

No app do Claude ou em claude.ai, abra Settings, depois Customize e clique em Connectors. É nessa tela que o Claude guarda as ferramentas externas ligadas a ele. Se o OpenArt já estiver na lista, pule para o teste.

Atalho direto para a tela: https://claude.ai/new#settings/customize-connectors

Fonte: <https://openart.ai/mcp/>

## Passos 2 e 3: conector customizado e nome

Na tela de conectores, clique em + Add e escolha Add custom connector. Abre uma janela pedindo o nome e o endereço do servidor.

No campo de nome, escreva OpenArt. O nome ajuda a reconhecer a ferramenta quando a lista tiver vários conectores.

Fonte: <https://openart.ai/mcp/claude-ai-image-generator/>

## Passo 4: cole o endereço do servidor MCP

No campo de URL, cole o endereço abaixo e deixe as configurações avançadas vazias. Copie e cole em vez de digitar: uma letra faltando impede a conexão. Cole só o endereço, sem texto antes ou depois.

```
https://mcp.openart.ai/mcp
```

Fonte: <https://openart.ai/mcp/claude-ai-image-generator/>

## Passos 5 e 6: adicione e entre na conta

Clique em Add. O Claude confere o endereço e salva o conector, que entra na lista com o botão Connect. Se aparecer erro, confira se o endereço foi colado inteiro, sem espaço sobrando.

Clique em Connect e faça login com a conta do OpenArt. Use a conta onde estão a assinatura e os créditos: outra conta liga o Claude a um saldo e a projetos que não são os seus.

Fonte: <https://openart.ai/mcp/claude-ai-image-generator/>

## Passo 7: autorize com Always Allow

Nas permissões do conector, escolha Always Allow. Assim o Claude usa o OpenArt sem pedir confirmação a cada ação: gera imagens e vídeos, lista modelos, envia referências, organiza projetos e consulta o saldo. O OpenArt deve aparecer conectado na lista de conectores. Se não aparecer, repita o passo de conectar.

Com essa permissão, cada geração que você pedir desconta créditos da sua conta.

```
Always Allow
```

Fonte: <https://openart.ai/mcp/claude-ai-image-generator/>

## Teste: modelos, saldo e uma imagem

Abra uma conversa nova no Claude e envie o pedido abaixo. Se ele responder com a lista de modelos e o saldo, a conexão está ativa. Depois peça uma imagem, descrevendo o que quer. O resultado volta na própria conversa.

Se o Claude disser que não tem acesso, volte à lista de conectores e confira se o OpenArt está ativo. Comece com um pedido simples e veja quanto saldo ele consumiu antes de pedir vídeos.

Fonte: <https://openart.ai/mcp/>

## Além do vídeo

- Com o conector ativo, o Claude também pode ser usado para gerar um carrossel inteiro, com texto e imagens saindo da mesma conversa.
- O guia oficial do OpenArt cobre o MCP e a CLI: https://openart.ai/mcp/
