# OpenArt tem MCP e o Claude gera imagem e vídeo no chat

_2026-11-23 · tutorial_

Este guia liga o OpenArt ao Claude por um servidor MCP. Depois de conectado, você pede imagens e vídeos na conversa e o resultado volta ali mesmo, sem abrir o site. O Claude também lista os modelos, envia imagens de referência, organiza projetos e consulta o saldo de créditos. Os passos vão do cadastro do conector até o primeiro teste.

## O que você terá no fim

Ao final, o OpenArt estará conectado ao Claude por um servidor MCP, e você pedirá imagens e vídeos na conversa. O OpenArt reúne modelos como Nano Banana Pro, GPT Image 2, Seedream e Kling numa assinatura só. Cada imagem ou vídeo gerado desconta um valor do saldo de créditos. Fonte: https://openart.ai/mcp/

Antes de começar, você precisa de: uma conta no Claude, com acesso às configurações e à área de conectores; uma conta no OpenArt, com a assinatura que pretende usar; créditos na conta do OpenArt; e um navegador, já que o login do OpenArt acontece numa página da web.

Fonte: <https://openart.ai/mcp/>

## Passo a passo

Siga os passos na ordem. O endereço do servidor e a permissão ficam em seções próprias.

1. abra os conectores do Claude. No app do Claude ou em claude.ai, abra Settings, depois Customize e clique em Connectors. Se o OpenArt já estiver na lista, pule para o teste. Atalho direto: https://claude.ai/new#settings/customize-connectors. Resultado esperado: a tela de conectores está aberta.
2. Passos 2 e 3: adicione um conector customizado e dê o nome. Na tela de conectores, clique em + Add e escolha Add custom connector. No campo de nome, escreva OpenArt. Resultado esperado: a janela pede o endereço do servidor.
3. cole o endereço do servidor MCP, https://mcp.openart.ai/mcp. No campo de URL, cole o endereço abaixo e deixe as configurações avançadas vazias. Copie e cole em vez de digitar. Resultado esperado: o campo de URL tem só o endereço.
4. Passos 5 e 6: adicione e entre na conta. Clique em Add. O conector entra na lista com o botão Connect. Clique em Connect e faça login com a conta do OpenArt, a que tem a assinatura e os créditos. Resultado esperado: o conector está conectado.
5. autorize com Always Allow. Nas permissões do conector, escolha Always Allow. O OpenArt deve aparecer conectado na lista de conectores. Resultado esperado: o Claude usa o OpenArt sem pedir confirmação a cada ação.

Fonte: <https://openart.ai/mcp/claude-ai-image-generator/>

## Endereço do servidor MCP

Cole só o endereço, sem texto antes ou depois. Uma letra faltando impede a conexão. Se aparecer erro ao adicionar, confira se o endereço foi colado inteiro, sem espaço sobrando. Fonte: https://openart.ai/mcp/claude-ai-image-generator/

```
https://mcp.openart.ai/mcp
```

Fonte: <https://openart.ai/mcp/claude-ai-image-generator/>

## Permissão Always Allow

Com essa permissão, cada geração que você pedir desconta créditos da sua conta. Assim o Claude gera imagens e vídeos, lista modelos, envia referências, organiza projetos e consulta o saldo. Se o OpenArt não aparecer conectado, repita o passo de conectar. Fonte: https://openart.ai/mcp/claude-ai-image-generator/

```
Always Allow
```

Fonte: <https://openart.ai/mcp/claude-ai-image-generator/>

## Teste de pronto

Abra uma conversa nova no Claude e envie o pedido de teste. Se ele responder com a lista de modelos e o saldo, a conexão está ativa. Depois peça uma imagem, descrevendo o que quer. O resultado volta na própria conversa. Comece com um pedido simples e veja quanto saldo ele consumiu antes de pedir vídeos. Fonte: https://openart.ai/mcp/

- [ ] O Claude responde com a lista de modelos e o saldo.
- [ ] Uma imagem volta na própria conversa.

Fonte: <https://openart.ai/mcp/>

## Cuidados e outras opções

Se o Claude disser que não tem acesso, volte à lista de conectores e confira se o OpenArt está ativo. Use a conta onde estão a assinatura e os créditos: outra conta liga o Claude a um saldo e a projetos que não são os seus.

O mesmo assistente que escreve o roteiro de um carrossel escreve o prompt de cada imagem, então imagem e texto saem coerentes. O Cursor também conecta por MCP, e o Codex usa a CLI do OpenArt. O guia oficial do OpenArt cobre o MCP e a CLI: https://openart.ai/mcp/

Fonte: <https://openart.ai/mcp/>
