# Busca, leitura de URL e título de chat em 1 requisição

_2026-11-24 · tutorial_

Este vídeo mostra como montar uma única requisição à API da DeepSeek que pesquisa na web, lê links, revisa a segurança e gera um título para a conversa. Você usa o endpoint Messages com o modelo deepseek-flash, raciocínio ativo e duas ferramentas declaradas. A resposta chega em blocos: pensamento, buscas, página lida, texto com citações, recusa e título.

## O que você terá no fim

Ao final, você terá uma chamada POST ao endpoint Messages da DeepSeek que pesquisa, lê links, revisa a segurança e gera o título, com a resposta chegando em blocos no seu chat. Uma única chamada já liga busca na web, leitura de URL, revisão de segurança e geração de título. O serviço executa tudo isso: pesquisa, abre páginas e decide quando usar cada ferramenta. Seu chat só precisa exibir os blocos que chegam e devolvê-los intactos na próxima rodada. Fonte: https://api-docs.deepseek.com/guides/build_a_chatbot

O guia oficial está em api-docs.deepseek.com/guides/build_a_chatbot e a demo de código aberto em github.com/deepseek-ai/chat-demo.

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Passo a passo

Siga os passos na ordem. Os blocos de código ficam em seções próprias.

1. guarde a chave. Crie a variável de ambiente DEEPSEEK_API_KEY com a sua chave da plataforma, no mesmo terminal da chamada. Resultado esperado: a variável existe na sessão.
2. aponte para o endpoint Messages. Inicie um POST para https://api.deepseek.com/anthropic/v1/messages com os cabeçalhos Content-Type e x-api-key. Na API Messages a chave vai no cabeçalho x-api-key. Resultado esperado: o endpoint recebe a requisição.
3. defina o modelo e o raciocínio. No corpo JSON, indique o modelo deepseek-flash e ative o raciocínio com thinking.type: enabled. Resultado esperado: o primeiro bloco da resposta será o de pensamento.
4. declare as ferramentas de busca e leitura. Adicione um array tools com deepseek_web_search e deepseek_read_url, cada uma com type e name. Resultado esperado: o serviço decide quando pesquisar páginas ou abrir links citados.
5. ligue a segurança e o título. Ligue a revisão de segurança com level: high e o título com enabled: true. Resultado esperado: a resposta traz a marca de recusa quando há risco e o bloco de título.
6. envie a pergunta em streaming. Feche o corpo com messages e stream: true, e rode o comando completo. Resultado esperado: os eventos chegam em sequência, começando por message_start.
7. exiba raciocínio e buscas. O pensamento vira um painel recolhível; as buscas viram cartões; a leitura de página aparece como uma página aberta. Resultado esperado: cada bloco aparece no formato certo.

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Guardar a chave

Os comandos seguintes leem essa variável, então ela precisa existir na mesma sessão do terminal. Troque o texto de exemplo pela sua chave real. Chave da plataforma: https://www.deepseek.com/en/platform/

```
export DEEPSEEK_API_KEY="sua-chave"
```

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Endpoint Messages

Endpoint: https://api.deepseek.com/anthropic/v1/messages. Método: POST. Cabeçalho 1: Content-Type: application/json. Cabeçalho 2: x-api-key com a chave lida da variável DEEPSEEK_API_KEY. Nos protocolos Responses e Chat Completions o formato é diferente: Authorization: Bearer.

```
curl https://api.deepseek.com/anthropic/v1/messages \
  -H "Content-Type: application/json" \
  -H "x-api-key: ${DEEPSEEK_API_KEY}"
```

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Modelo e raciocínio

Com as ferramentas ligadas, o parâmetro thinking.budget_tokens é ignorado: o serviço decide o limite. Ativado o raciocínio, o primeiro bloco da resposta será o de pensamento. Na Messages cada ferramenta leva type e name; nos protocolos Responses e Chat Completions basta o type.

- model: deepseek-flash.
- thinking: {"type": "enabled"}.

```
"model": "deepseek-flash",
"thinking": {"type": "enabled"},
```

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Segurança e título

A revisão avalia entrada e saída do modelo e devolve uma marca de recusa quando encontra risco. Se você expõe um serviço ao público, cumpra também as obrigações de provedor (revisão de conteúdo, registro do modelo e rotulagem de IA). Com essas opções ativadas, temperature, top_p e outros parâmetros de amostragem são ignorados pelo serviço.

- safety_check: {"level": "high"}.
- title: {"enabled": true}.

```
"safety_check": {"level": "high"},
"title": {"enabled": true},
```

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Teste de pronto

Rode a chamada e confira os blocos que chegam. A resposta chega em blocos: pensamento, buscas, página lida, texto com citações, recusa e título.

- [ ] Os eventos chegam em streaming e o primeiro é message_start.
- [ ] O bloco de pensamento aparece antes das buscas.
- [ ] Na rodada seguinte, os blocos são devolvidos exatamente como chegaram, sem reescrever.

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Cuidados e outros links

Na rodada seguinte, devolva os blocos exatamente como chegaram, sem reescrever. Lista de parâmetros ignorados por protocolo (Messages, Responses e Chat Completions) no guia oficial.

Exemplo de Web Tools (segunda rodada): https://api-docs.deepseek.com/guides/web_tools/. Chat demo em código aberto: https://github.com/deepseek-ai/chat-demo e versão online https://cdn.deepseek.com/chat-demo. Plataforma da API DeepSeek para obter a chave: https://www.deepseek.com/en/platform/

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>
