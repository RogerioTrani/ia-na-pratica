# Busca, leitura de URL e título de chat em 1 requisição

_2026-11-24 · tutorial_

Este vídeo mostra como montar uma única requisição à API da DeepSeek que pesquisa na web, lê links, revisa a segurança e gera um título para a conversa. Você usa o endpoint Messages com o modelo deepseek-flash, raciocínio ativo e duas ferramentas declaradas. A resposta chega em blocos: pensamento, buscas, página lida, texto com citações, recusa e título. Na rodada seguinte, devolva os blocos exatamente como chegaram, sem reescrever.

## Visão geral da requisição

Uma única chamada POST para o endpoint Messages da DeepSeek já liga busca na web, leitura de URL, revisão de segurança e geração de título. O serviço executa tudo isso: pesquisa, abre páginas e decide quando usar cada ferramenta. Seu chat só precisa exibir os blocos que chegam e devolvê-los intactos na próxima rodada.

O guia oficial está em api-docs.deepseek.com/guides/build_a_chatbot e a demo de código aberto em github.com/deepseek-ai/chat-demo.

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Passo 1 — Guarde a chave

Crie uma variável de ambiente com o nome DEEPSEEK_API_KEY e coloque nela sua chave da plataforma. Os comandos seguintes leem essa variável, então ela precisa existir na mesma sessão do terminal.

O comando é: export DEEPSEEK_API_KEY="sua-chave". Troque o texto de exemplo pela sua chave real.

- Criar a variável no terminal onde você vai rodar a chamada

```
export DEEPSEEK_API_KEY="sua-chave"
```

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Passo 2 — Aponte para o endpoint Messages

Inicie um POST para https://api.deepseek.com/anthropic/v1/messages com os dois cabeçalhos obrigatórios. Um informa que o corpo é JSON; o outro leva a chave lida da variável DEEPSEEK_API_KEY.

Na API Messages a chave vai no cabeçalho x-api-key. Nos protocolos Responses e Chat Completions o formato é diferente: Authorization: Bearer.

- Endpoint: https://api.deepseek.com/anthropic/v1/messages
- Método: POST
- Cabeçalho 1: Content-Type: application/json
- Cabeçalho 2: x-api-key: ${DEEPSEEK_API_KEY}

```
curl https://api.deepseek.com/anthropic/v1/messages \
  -H "Content-Type: application/json" \
  -H "x-api-key: ${DEEPSEEK_API_KEY}"
```

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Passo 3 — Modelo e raciocínio

No corpo JSON, indique o modelo deepseek-flash e ative o raciocínio com thinking.type: enabled. Com as ferramentas ligadas, o parâmetro thinking.budget_tokens é ignorado: o serviço decide o limite.

Ativado o raciocínio, o primeiro bloco da resposta será o de pensamento.

- model: deepseek-flash
- thinking: {"type": "enabled"}

```
"model": "deepseek-flash",
"thinking": {"type": "enabled"},
```

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Passo 4 — Declare as ferramentas de busca e leitura

Adicione um array tools com deepseek_web_search e deepseek_read_url, cada uma com type e name. É o serviço que decide quando pesquisar páginas ou abrir links citados na mensagem.

Na Messages cada ferramenta leva type e name; nos protocolos Responses e Chat Completions basta o type.

- type: deepseek_web_search
- name: deepseek_web_search
- type: deepseek_read_url
- name: deepseek_read_url

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Passo 5 — Segurança e título

Ligue a revisão de segurança com level: high e o título com enabled: true. A revisão avalia entrada e saída do modelo e devolve uma marca de recusa quando encontra risco; se você expõe um serviço ao público, cumpra também as obrigações de provedor (revisão de conteúdo, registro do modelo e rotulagem de IA).

Com essas opções ativadas, temperature, top_p e outros parâmetros de amostragem são ignorados pelo serviço.

- safety_check: {"level": "high"}
- title: {"enabled": true}

```
"safety_check": {"level": "high"},
"title": {"enabled": true},
```

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Passo 6 — Envie a pergunta em streaming

Feche o corpo com messages e stream: true, e rode o comando completo. Os eventos chegam em sequência; o primeiro é message_start.

- messages: [{"role": "user", "content": "..."}]
- stream: true

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Passo 7 — Exiba raciocínio e buscas

No seu chat, escolha o que mostrar conforme o tipo de cada bloco. O pensamento vira um painel recolhível; as buscas chegam em dois blocos (consultas e resultados) e viram cartões com título, nome do site e ícone; a leitura de página aparece como uma página aberta.

- thinking > painel recolhível
- server_tool_use + web_search_tool_result > etapa de busca com cartões
- server_tool_use + web_fetch_tool_result > página aberta

Fonte: <https://api-docs.deepseek.com/guides/build_a_chatbot>

## Além do vídeo

- Guia oficial Build a Chatbot: https://api-docs.deepseek.com/guides/build_a_chatbot
- Exemplo de Web Tools (segunda rodada): https://api-docs.deepseek.com/guides/web_tools/
- Chat demo em código aberto: https://github.com/deepseek-ai/chat-demo e versão online https://cdn.deepseek.com/chat-demo
- Plataforma da API DeepSeek para obter a chave: https://www.deepseek.com/en/platform/
- Lista de parâmetros ignorados por protocolo (Messages, Responses e Chat Completions) no guia oficial
