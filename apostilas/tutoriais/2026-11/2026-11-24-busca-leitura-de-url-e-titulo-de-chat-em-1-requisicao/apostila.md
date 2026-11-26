# Busca, leitura de URL e título de chat em 1 requisição

_2026-11-24 · tutorial_

Esta apostila ensina a montar uma única chamada à API da DeepSeek que pesquisa na web, lê links, revisa a segurança do conteúdo e gera um título para a conversa, tudo em fluxo. Você aprende a guardar a chave, montar a requisição com modelo, raciocínio, ferramentas, segurança e título, enviar a pergunta e exibir cada bloco da resposta no seu chat. Também aprende a devolver os blocos intactos na rodada seguinte e a confirmar o título gerado. Serve para quem desenvolve um chat próprio e quer esses recursos sem montar o backend de busca.

## O que você terá no fim

Ao final, você terá uma única chamada à API da DeepSeek que, ao mesmo tempo, pesquisa na web, lê links, revisa a segurança do conteúdo e gera um título curto para a conversa. Seu chat exibe cada pedaço da resposta no lugar certo: raciocínio, buscas, texto com fontes e, se houver risco, uma recusa. Tudo em uma requisição, em fluxo.

O serviço da DeepSeek executa as buscas e a leitura de páginas. Seu código só mostra os blocos que chegam e os devolve sem alterar na rodada seguinte. Esta apostila serve para quem desenvolve um chat próprio e quer esses recursos sem montar o backend de busca.

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Como isso funciona

A API da DeepSeek oferece os mesmos recursos do chat da web e do aplicativo: busca na web, busca com raciocínio (busca profunda), entrada de arquivos, leitura de URL, controle de risco para segurança de conteúdo, marcador de metadados do usuário, título da conversa, leitura em voz alta e entrada por voz.

Nesta apostila você liga quatro deles numa requisição: busca na web com raciocínio, leitura de URL, revisão de segurança e título. O modelo decide quando pesquisar e quando abrir uma página, com base na pergunta da pessoa.

Cada resposta chega como uma sequência de blocos: raciocínio (thinking), uso de ferramenta no servidor (server_tool_use), resultado da busca (web_search_tool_result), resultado da leitura (web_fetch_tool_result), texto (text) com citações (citations_delta) e, no final, um evento de fim de mensagem (message_delta) com o motivo de parada e o título.

Seu cliente lê o tipo de cada bloco e decide o que mostrar. O serviço executa; você exibe. Na rodada seguinte, você envia de volta a pergunta anterior, a resposta do assistente com os blocos exatamente como chegaram e a nova pergunta.

Modelo usado: deepseek-flash. A página da plataforma lista preços por 1 milhão de tokens para DeepSeek-V4-Flash e DeepSeek-V4-Pro; confira qual deles vale para o deepseek-flash. O DeepSeek-V4-Flash cobra US$ 0,0028 de entrada com cache hit, US$ 0,14 de entrada sem cache e US$ 0,28 de saída; DeepSeek-V4-Pro cobra US$ 0,003625, US$ 0,435 e US$ 0,87, respectivamente. A API faz cache automático e suporta até 1 milhão de tokens de contexto. Preços podem mudar; confira na plataforma.

- DeepSeek-V4-Flash: entrada com cache hit US$ 0,0028, entrada sem cache US$ 0,14, saída US$ 0,28 (por 1 milhão de tokens)
- DeepSeek-V4-Pro: entrada com cache hit US$ 0,003625, entrada sem cache US$ 0,435, saída US$ 0,87 (por 1 milhão de tokens)
- Contexto: até 1 milhão de tokens; cache automático

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Antes de começar

Confirme que você tem tudo abaixo antes de rodar a primeira chamada.

- Chave de API da DeepSeek, obtida em deepseek.com/en/platform.
- Terminal com o programa de requisições HTTP usado nos exemplos (curl), para a primeira chamada.
- Um chat seu, em qualquer linguagem, onde os blocos serão exibidos.
- Saber criar uma variável de ambiente no seu sistema, pois a chave ficará nela.
- Nada para instalar além disso.
- Cumprimento dos termos de serviço da Open Platform.

Fonte: <https://www.deepseek.com/en/platform/>

## Passo a passo

1. Guarde a chave numa variável: crie a variável de ambiente DEEPSEEK_API_KEY com a sua chave no terminal onde rodará a chamada. Resultado: a variável existe naquela sessão e as próximas chamadas a leem.
2. Aponte para o endpoint Messages: inicie um POST para https://api.deepseek.com/anthropic/v1/messages com os cabeçalhos Content-Type: application/json e x-api-key lido da variável. Resultado: a rota e os cabeçalhos ficam prontos; a resposta vem nos próximos passos.
3. Escolha o modelo e ative o raciocínio: no corpo JSON, indique model deepseek-flash e thinking com type enabled. Resultado: quando a resposta chegar, o primeiro bloco será o de raciocínio.
4. Declare as duas ferramentas: adicione tools com deepseek_web_search e deepseek_read_url, cada uma com type e name. Resultado: a resposta passará a trazer blocos de busca e de leitura de página.
5. Ligue a revisão de segurança e o título: adicione safety_check no nível high e title com enabled true. Resultado: no fim do fluxo chega o título; se houver risco, a resposta termina com stop_reason igual a refusal.
6. Envie a pergunta em streaming: feche o corpo com messages e stream true e rode o comando completo. Resultado: eventos chegam em sequência, começando por message_start.
7. Exiba o raciocínio e as buscas: no chat, escolha o que mostrar pelo tipo de cada bloco. Resultado: painel de raciocínio recolhível e cartões de busca com título, nome do site e ícone.
8. Mostre texto, citações, recusa e título: o bloco text traz a resposta com marcadores de citação; se stop_reason for refusal, troque a resposta pela sua mensagem; o title chega no message_delta. Resultado: resposta com marcadores que levam às fontes e o título da conversa ao final.
9. Devolva os blocos intactos na rodada seguinte: envie em messages a pergunta anterior, a resposta do assistente com os blocos exatamente como chegaram e a nova pergunta. Resultado: a nova rodada segue a conversa sem que você reescreva nenhum bloco.

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Comando: variável de ambiente

Crie a variável no terminal onde rodará a chamada, trocando o texto de exemplo pela sua chave. Este passo existe para que a chave nunca fique escrita dentro do comando nem do código do chat.

```
export DEEPSEEK_API_KEY="sua-chave"
```

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Comando: endpoint Messages

Use o endereço da API Messages, compatível com o formato da Anthropic, e envie com POST. Coloque os dois cabeçalhos: um avisa que o corpo é JSON, o outro leva a chave lida da variável. Ainda sem resposta: o corpo da requisição vem nos próximos passos.

```
curl https://api.deepseek.com/anthropic/v1/messages \
  -H "Content-Type: application/json" \
  -H "x-api-key: ${DEEPSEEK_API_KEY}" \
```

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Comando: modelo e raciocínio

Abra o corpo da requisição indicando o modelo Flash e ligando o raciocínio. Com o raciocínio ativo, o modelo pensa em várias etapas, pesquisa na web e lê links por conta própria, e cada etapa volta como um bloco que o seu chat poderá mostrar.

```
"model": "deepseek-flash",
"thinking": {"type": "enabled"},
```

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Comando: ferramentas

Declare as duas ferramentas do serviço: a de busca na web e a de leitura de URL. Com a busca ligada, ele decide quando pesquisar páginas ou imagens e responde com citações; com a leitura ligada, ele percebe links na mensagem da pessoa e abre as páginas. Quem executa tudo isso é o serviço da DeepSeek, não o seu código.

```
"tools": [
  {"type": "deepseek_web_search", "name": "deepseek_web_search"},
  {"type": "deepseek_read_url", "name": "deepseek_read_url"}
],
```

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Comando: segurança e título

Acrescente a revisão de segurança no nível alto e a geração de título. A revisão avalia a entrada e a saída do modelo e devolve uma marca de recusa quando encontra risco. O título é uma frase curta gerada quando a resposta termina.

```
"safety_check": {"level": "high"},
"title": {"enabled": true},
```

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Comando: requisição completa

Feche o corpo com a pergunta e com o envio em fluxo, e rode o comando completo no terminal. O envio em fluxo existe para o seu chat mostrar a resposta aos poucos, bloco a bloco, em vez de esperar tudo terminar.

```
curl https://api.deepseek.com/anthropic/v1/messages \
  -H "Content-Type: application/json" \
  -H "x-api-key: ${DEEPSEEK_API_KEY}" \
  -d '{
    "model": "deepseek-flash",
    "thinking": {"type": "enabled"},
    "tools": [
      {"type": "deepseek_web_search", "name": "deepseek_web_search"},
      {"type": "deepseek_read_url", "name": "deepseek_read_url"}
    ],
    "safety_check": {"level": "high"},
    "title": {"enabled": true},
    "messages": [{"role": "user", "content": "What is new in DeepSeek V4.1?"}],
    "stream": true
  }'
```

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Protocolos e parâmetros ignorados

Os mesmos recursos estão nos três protocolos: Messages, Responses e Chat Completions, cada um com endereço próprio. Na Messages a chave vai no cabeçalho x-api-key; em Responses e Chat Completions usa-se Authorization: Bearer. Na Messages cada ferramenta leva type e name; nos outros dois protocolos basta o type.

Com deepseek_web_search ou deepseek_read_url declarados, safety_check em high ou title habilitado, o serviço decide vários parâmetros e ignora os valores enviados. O max_tokens (max_output_tokens na Responses) funciona normalmente: limita a saída de cada etapa de inferência numa rodada, não o total da rodada.

- Messages: POST https://api.deepseek.com/anthropic/v1/messages
- Responses: POST https://api.deepseek.com/responses
- Chat Completions: POST https://api.deepseek.com/chat/completions
- Ignorados na Messages: temperature, top_p, top_k, stop_sequences, thinking.budget_tokens, preserve_thinking, tool_choice.disable_parallel_tool_use, metadata (exceto user_id)
- Ignorados na Responses: temperature, top_p, reasoning.summary, text.verbosity, include, max_tool_calls, truncation, metadata, parallel_tool_calls, store
- Ignorados na Chat Completions: temperature, top_p, frequency_penalty, presence_penalty, stop, seed, n, preserve_thinking, parallel_tool_calls

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Mostrando os blocos no chat

O serviço executa tudo e só devolve o que aconteceu; mostrar é com você. Leia o fluxo e decida pelo tipo de cada bloco, conforme o mapa abaixo.

- thinking: painel de raciocínio recolhível
- server_tool_use + web_search_tool_result: etapa de busca com cartões (título, nome do site, ícone)
- server_tool_use + web_fetch_tool_result: página aberta ou link lido
- text com citations: resposta com marcadores de citação que levam às fontes
- stop_reason: refusal: substitua a resposta pela sua mensagem de recusa, não exiba o que veio

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Devolver os blocos intactos

Na rodada seguinte, monte a requisição com três mensagens: a pergunta anterior da pessoa, a resposta do assistente com a lista de blocos exatamente como chegou (com os campos de tipo e de assinatura), e a nova pergunta. O serviço espera receber de volta o que ele mesmo gerou. Não corte, não reordene e não reescreva nenhum bloco.

```
curl https://api.deepseek.com/anthropic/v1/messages \
  -H "Content-Type: application/json" \
  -H "x-api-key: ${DEEPSEEK_API_KEY}" \
  -d '{
    "model": "deepseek-flash",
    "tools": [
      {"type": "deepseek_web_search", "name": "deepseek_web_search"},
      {"type": "deepseek_read_url", "name": "deepseek_read_url"}
    ],
    "messages": [
      {"role": "user", "content": "Summarize https://example.com/ in one sentence."},
      {
        "role": "assistant",
        "content": [
          {
            "type": "server_tool_use",
            "id": "srvtoolu_rl_00_0efde247...",
            "name": "deepseek_read_url",
            "input": {"action": "read_link", "url": "https://example.com"},
            "caller": {"type": "direct"},
            "kind": "read_link"
          },
          {
            "type": "web_fetch_tool_result",
            "tool_use_id": "srvtoolu_rl_00_0efde247...",
            "content": {
              "type": "web_fetch_result",
              "url": "https://example.com",
              "content": {
                "type": "document",
                "source": {"type": "text", "media_type": "text/plain", "data": ""},
                "title": "Example Domain"
              },
              "published_at": null
            },
            "kind": "read_link",
            "signature": "tQU8k+8Ko7MY5XDAvJd0..."
          },
          {"type": "text", "text": "The example.com domain is reserved for use in documentation examples."}
        ]
      },
      {"role": "user", "content": "Quote the first sentence of that page."}
    ]
  }'
```

Fonte: <https://api-docs.deepseek.com/guides/web_tools/>

## Exemplo completo: segunda rodada

Exemplo da documentação: o usuário pede um resumo de https://example.com/ em uma frase; o assistente responde com os blocos de leitura de URL e o texto; o usuário pede a primeira frase da página.

Os valores terminados em reticências são abreviações da própria documentação: no uso real, copie o id e a signature completos da resposta recebida.

- A pergunta anterior do usuário vem primeiro.
- Depois, uma mensagem com role assistant, cujo content é a lista de blocos exatamente como chegaram, com os campos kind e signature.
- Por último, a nova mensagem do usuário.
- Os valores terminados em ... são abreviações: use o identificador e a assinatura completos da resposta que você recebeu.

Fonte: <https://api-docs.deepseek.com/guides/web_tools/>

## Teste de pronto

- [ ] Rode de novo o comando completo do passo 6 e acompanhe o fluxo.
- [ ] Aparecem, em ordem, blocos thinking, server_tool_use, web_search_tool_result e text.
- [ ] Depois chega um message_delta com o title e o message_stop.
- [ ] Se stop_reason for refusal no fim, a revisão bloqueou a resposta.
- [ ] Se esses blocos aparecem no seu chat, tudo funcionou.

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Erros comuns e cuidados

- Na Messages a chave vai no cabeçalho x-api-key; em Responses e Chat Completions usa-se Authorization: Bearer.
- Na Messages cada ferramenta leva type e name; nos outros protocolos basta o type.
- Com as ferramentas ligadas, thinking.budget_tokens é ignorado: o serviço decide o limite de tokens do raciocínio.
- Com as ferramentas da web, o safety_check em high ou o título ligados, temperature e top_p são ignorados: o serviço escolhe os valores.
- Em caso de recusa (stop_reason refusal), não exiba o texto que veio: substitua pela sua mensagem de recusa.
- Se o título não aparecer, verifique se você leu o evento de fim da mensagem (message_delta).
- Se o contexto parecer perdido na rodada seguinte, compare o que você guardou com o que chegou; copie o id e a signature completos.
- Se o serviço for aberto ao público, habilite o safety_check, cumpra por conta própria obrigações como revisão de conteúdo, registro do modelo e rotulagem de IA e respeite os termos de serviço.
- Preços podem mudar; confira na plataforma antes de estimar custo.

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Glossário

- API Messages: endpoint da DeepSeek compatível com o formato da Anthropic, em https://api.deepseek.com/anthropic/v1/messages.
- deepseek-flash: modelo usado nas chamadas de exemplo.
- deepseek_web_search: ferramenta do serviço que pesquisa na web ou em imagens e responde com citações.
- deepseek_read_url: ferramenta do serviço que detecta links na mensagem, busca as páginas e as coloca no contexto.
- thinking: raciocínio em várias etapas; quando ativo, o modelo pesquisa e lê links por conta própria.
- safety_check: revisão de segurança da entrada e da saída do modelo; devolve marca de recusa em caso de risco.
- title: geração de um título curto para a conversa quando a resposta termina.
- stream: envio em fluxo, para exibir a resposta aos poucos.
- server_tool_use: bloco que indica uso de ferramenta no servidor.
- web_search_tool_result: bloco com os resultados da busca.
- web_fetch_tool_result: bloco com o resultado da leitura de uma página.
- citations_delta: atualização do fluxo, dentro do bloco de texto, com as citações que apontam para as fontes.
- message_delta: evento de fim da mensagem, que traz stop_reason e title.
- stop_reason: motivo de parada da mensagem; refusal indica bloqueio pela revisão.
- refusal: marca de recusa retornada quando a revisão encontra risco.
- signature: campo de assinatura dos blocos, que deve ser devolvido intacto.
- kind: campo que indica o tipo de operação do bloco (por exemplo, read_link ou deep_search).

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Plano de 7 dias

- Dia 1: obtenha a chave de API e crie a variável de ambiente; rode o passo 1 e confira.
- Dia 2: monte o endpoint e os cabeçalhos do passo 2; a resposta só vem depois que o corpo estiver completo.
- Dia 3: adicione modelo e raciocínio; envie a pergunta e veja o bloco thinking chegar.
- Dia 4: declare as duas ferramentas; confira os blocos de busca e leitura de página.
- Dia 5: ligue segurança e título; confira o title no message_delta e teste uma recusa.
- Dia 6: implemente a exibição dos blocos no seu chat (painel, cartões, citações).
- Dia 7: implemente a devolução dos blocos intactos e rode o teste de pronto.

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Para onde ir depois

- Guia oficial Build a Chatbot: https://api-docs.deepseek.com/guides/build_a_chatbot
- Guia oficial Web Tools (exemplo da segunda rodada): https://api-docs.deepseek.com/guides/web_tools/
- Chat de demonstração de código aberto: https://github.com/deepseek-ai/chat-demo
- Demo online do chat: https://cdn.deepseek.com/chat-demo
- Plataforma da API DeepSeek (chave de API): https://www.deepseek.com/en/platform/
- Demo de referência: clone o repositório, instale Node.js 22.12+ e pnpm, rode pnpm install e pnpm dev (porta 8090), ou gere o build estático com pnpm build (saída em dist/).
- Estude os outros recursos do mapa: entrada de arquivos, marcador de metadados do usuário, leitura em voz alta e entrada por voz.
- Considere os termos de serviço da Open Platform ao publicar um serviço.

Fonte: <https://github.com/deepseek-ai/chat-demo>

## Além do vídeo

- A demo também permite enviar, colar ou arrastar anexos, usar entrada por voz e leitura em voz alta, editar perguntas, regenerar respostas e alternar entre ramos da conversa.
- A interface da demo mostra Markdown, destaque de sintaxe, matemática com KaTeX e diagramas Mermaid, em chinês simplificado ou inglês, com temas claro e escuro.
- Na demo, a chave e as configurações ficam no localStorage do navegador e as conversas e anexos no IndexedDB; ao enviar mensagens, anexos ou usar voz, esse conteúdo vai para o serviço de API configurado.
- Importar um histórico em ZIP substitui todas as conversas e anexos locais, após confirmação e validação.
- O projeto traz os comandos pnpm type, pnpm lint e pnpm format, e o arquivo rspack.config.ts permite trocar a origem da API.
- A plataforma em chinês lista preços em yuans por 1 milhão de tokens (cache hit, sem cache e saída): V4-Flash 0,02, 1 e 2; V4-Pro 0,025, 3 e 6. A mesma página previa preço de pico, o dobro do normal, a partir de meados de julho.
