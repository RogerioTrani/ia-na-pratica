# Hugging Face passa a rotear modelos pela OpenRouter

_2026-11-23 · noticia_

A Hugging Face passou a rotear as chamadas a modelos de linguagem do Inference Providers pela OpenRouter, que escolhe o melhor provedor a cada pedido com base em preço, velocidade e confiabilidade ao vivo e tenta outro se o primeiro falhar. Seu código não muda, o preço continua o mesmo e a chamada ganha reserva. Esta apostila explica o que mudou, como controlar o roteamento com sufixos, o que quebra (chaves próprias de provedor) e como começar. Você também verá os números da melhora e do mercado de modelos abertos, além dos cuidados antes de confiar.

## O fato

Em 16 de novembro de 2026, a Hugging Face e a OpenRouter anunciaram uma parceria para facilitar o uso de modelos de pesos abertos. A partir desse dia, o Inference Providers da Hugging Face deixa de usar o próprio roteador e passa a usar o roteador da OpenRouter para chamadas a modelos de linguagem.

Na prática, quem chama um modelo pelo token da Hugging Face não precisa mudar código: a chamada ganha, por baixo, a escolha do melhor provedor a cada pedido e a repetição automática em outro provedor se o primeiro falhar.

Fonte: <https://huggingface.co/blog/openrouter>

## Por que isso importa

Modelos de pesos abertos já são publicados no Hugging Face Hub, e a OpenRouter os serve em escala, roteando cada pedido entre mais de 80 provedores com base em medições ao vivo de cada um. A parceria junta as duas pontas: todo modelo aberto do Hub que algum provedor serve pode ser chamado com o seu token da Hugging Face, pela mesma API, com o melhor provedor escolhido a cada chamada.

O roteamento não olha só o preço de tabela. A OpenRouter mede preço, velocidade e confiabilidade ao vivo e envia o pedido para a melhor combinação dos três. Se um provedor fica lento ou começa a errar, o tráfego sai dele até se recuperar, e a tentativa que falhou é refeita no próximo melhor provedor dentro da mesma chamada.

A OpenRouter serve mais de 800 trilhões de tokens por mês para mais de 10 milhões de usuários, em mais de 600 modelos de mais de 80 provedores. Essa base de tráfego é o que alimenta as medições ao vivo. O Inference Providers também oferece acesso a modelos de vários provedores (Cerebras, Groq, Together AI, Replicate, fal, entre outros) por uma interface única, sem prender você a um único fornecedor.

Fonte: <https://huggingface.co/blog/openrouter>

## Como o roteamento mudou

Antes, o Inference Providers escolhia um provedor para o seu pedido e devolvia o erro dele se falhasse. Agora, a chamada é refeita em outro provedor quando o primeiro falha.

A OpenRouter reconstruiu recentemente o próprio roteamento: em vez de olhar apenas o menor preço de tabela, envia cada pedido para o provedor com a melhor combinação de preço, velocidade e confiabilidade. Quando um provedor desacelera ou começa a falhar, o tráfego se afasta dele até a recuperação.

Nas medições da própria OpenRouter, o novo roteamento cortou 46% dos erros de capacidade, melhorou o tempo até o primeiro token em 16,9% e aumentou a vazão em 16,3%.

Fonte: <https://huggingface.co/blog/openrouter>

## Você no controle: sufixos no id do modelo

Você ainda pode escolher a política ou o provedor acrescentando um sufixo ao id do modelo. Sem sufixo, vale a melhor combinação de preço, velocidade e confiabilidade.

Você também pode escolher o provedor pelo nome, no formato modelo:provedor (por exemplo, deepseek-ai/DeepSeek-V4.1-Flash:novita).

- zai-org/GLM-5.3 — padrão: melhor combinação de preço, velocidade e confiabilidade
- zai-org/GLM-5.3:fastest — maior vazão
- zai-org/GLM-5.3:cheapest — menor preço
- zai-org/GLM-5.3:novita — apenas o provedor Novita

```
zai-org/GLM-5.3 # default: best mix of price, speed and reliability
zai-org/GLM-5.3:fastest # highest throughput
zai-org/GLM-5.3:cheapest # lowest price
zai-org/GLM-5.3:novita # only Novita
```

Fonte: <https://huggingface.co/blog/openrouter>

## Roteamento com cache de prompt

O roteamento também é sensível a cache: uma conversa permanece no provedor que guarda o cache de prompt dela. Para deixar isso explícito, envie um UUID estável por conversa no cabeçalho X-HF-Session-Id (veja o guia de cache de prompt).

Fonte: <https://huggingface.co/blog/openrouter>

## Modelos abertos em uso

No OpenRouter, modelos de pesos abertos passaram de 26,8% dos tokens servidos em outubro de 2025 para 71,7% no fim de setembro de 2026, com pico de 77,5% em julho (OpenRouter, outubro de 2026). No mesmo período, o volume semanal de modelos abertos cresceu mais de 60 vezes, contra quase 10 vezes para modelos fechados.

Na semana do anúncio, o modelo mais usado no OpenRouter era um de pesos abertos, o DeepSeek V4.1 Flash 1017, com 59,2 trilhões de tokens.

Em média, modelos abertos custam cerca de quatro vezes menos: US$ 0,28 por milhão de tokens de entrada e US$ 1,62 por milhão de saída, contra US$ 1,27 e US$ 6,36 dos fechados.

Os melhores modelos abertos ainda ficam atrás dos proprietários nos benchmarks mais difíceis. No Artificial Analysis Intelligence Index, o Kimi K3.1 Pro, o melhor modelo aberto, marca 46 contra 65 do Claude Fable 5.2, por cerca de um sétimo do custo por tarefa (US$ 3,68 contra US$ 26,54). Segundo o anúncio, para muitas cargas de trabalho essa troca vale a pena.

Fonte: <https://huggingface.co/blog/openrouter>

## Preço e créditos

O preço não muda: você paga o preço do provedor na sua fatura da Hugging Face, e a Hugging Face não adiciona margem sobre ele.

Usuários PRO recebem US$ 2 em créditos todo mês, e organizações Team e Enterprise recebem US$ 2 por assento.

O mesmo token da Hugging Face também dá acesso a armazenamento (Storage Buckets), computação (Jobs) e inferência dedicada (Inference Endpoints).

Fonte: <https://huggingface.co/blog/openrouter>

## Imagem, vídeo e áudio: sem mudança

Geração de imagem, vídeo e áudio continua funcionando exatamente como antes, diretamente pelo Inference Providers da Hugging Face, sem passar pela OpenRouter. Você mantém o mesmo token e a mesma API, com acesso a dezenas de milhares de LoRAs.

Além de texto, o Inference Providers cobre geração de imagem e vídeo, embeddings para busca e recuperação, e tarefas tradicionais de ML como classificação e reconhecimento de entidades.

Fonte: <https://huggingface.co/blog/openrouter>

## Onde ver para onde vai a chamada

Nas páginas de modelo, duas abas novas mostram o que está por trás: Providers lista cada provedor para o qual a OpenRouter pode rotear o modelo, com preço de entrada e saída, velocidade e disponibilidade das últimas 24 horas; Metrics mostra o melhor preço, vazão, tempo até o primeiro token, comprimento de contexto e disponibilidade entre eles.

Nas páginas de modelo você também pode conversar com o modelo direto no widget.

O resumo de uso detalha o gasto por provedor para o qual cada pedido foi enviado.

Nas configurações, você pode desligar qualquer provedor que não queira: o roteador nunca envia pedidos para ele. Organizações têm as mesmas configurações, que valem para todo pedido cobrado à organização.

Fonte: <https://huggingface.co/blog/openrouter>

## Mudança que quebra: chaves próprias de provedor

Pedidos a modelos de linguagem agora passam pela OpenRouter e são cobrados na sua conta ou organização da Hugging Face. Por isso, não é mais possível usar a sua própria chave de API de um provedor com esses modelos.

Você ainda pode escolher o provedor com um sufixo no id do modelo (modelo:provedor) ou desligar provedores nas configurações, e o código continua o mesmo.

Chaves próprias para provedores de imagem e vídeo continuam funcionando.

Fonte: <https://huggingface.co/blog/openrouter>

## APIs e ferramentas suportadas

O roteador suporta as APIs Chat Completions e Responses da OpenAI e a API Messages da Anthropic para todo modelo de chat, independentemente do provedor por trás.

A interface é compatível com a API de chat completions da OpenAI: basta trocar a URL base para acessar centenas de modelos de pesos abertos pela rede de provedores.

Guias de configuração estão disponíveis para Claude Code, Codex, OpenCode, Pi e Hermes Agent.

Fonte: <https://huggingface.co/docs/inference-providers>

## Como começar

Você precisa de um token da Hugging Face. Crie um em hf.co/settings/tokens, como token detalhado com a permissão 'Make calls to Inference Providers'.

A base para a API compatível com OpenAI é https://router.huggingface.co/v1, com o token no cabeçalho Authorization.

Para descobrir quais modelos são servidos por pelo menos um provedor, use o CLI com hf models ls --warm (adicione --json para scripts e agentes).

Há um playground de inferência para testar modelos de chat antes de integrar.

- Python: huggingface_hub, openai ou requests
- JavaScript: @huggingface/inference, openai ou fetch
- HTTP/cURL: chamada direta ao endpoint

```
pip install huggingface_hub
hf auth login # get a read token from hf.co/settings/tokens
hf models ls --warm
```

Fonte: <https://huggingface.co/docs/inference-providers>

## Os números

- 46% — redução dos erros de capacidade com o novo roteamento, nas medições da OpenRouter
- 16,9% — melhora no tempo até o primeiro token
- 16,3% — aumento na vazão
- 26,8% para 71,7% — participação de modelos abertos nos tokens servidos no OpenRouter de outubro de 2025 ao fim de setembro de 2026 (pico de 77,5% em julho)
- mais de 60 vezes — crescimento do volume semanal de modelos abertos no mesmo período, contra quase 10 vezes para modelos fechados
- 59,2 trilhões de tokens — volume do DeepSeek V4.1 Flash 1017, modelo mais usado no OpenRouter na semana do anúncio
- 800 trilhões de tokens por mês — volume servido pela OpenRouter, para mais de 10 milhões de usuários, em mais de 600 modelos de mais de 80 provedores

Fonte: <https://huggingface.co/blog/openrouter>

## O que muda para você

Para quem usa modelos abertos pela Hugging Face, o código segue igual e a chamada ganha reserva: se o provedor escolhido falhar ou ficar lento, a OpenRouter tenta outro dentro da mesma chamada. O gasto continua na fatura da Hugging Face, pelo preço do provedor.

Exemplo: uma aplicação que chama deepseek-ai/DeepSeek-V4.1-Flash pelo endpoint compatível com OpenAI continua funcionando sem alteração; basta manter o token da Hugging Face.

Fonte: <https://huggingface.co/docs/inference-providers>

## O que fazer hoje

1. Crie ou confira seu token da Hugging Face com a permissão 'Make calls to Inference Providers'.
2. Mantenha seu código como está: a base URL compatível com OpenAI (https://router.huggingface.co/v1) e o token continuam valendo, e a chamada passa a ganhar roteamento e repetição automática.
3. Se quiser mais vazão ou menor preço em uma chamada, acrescente o sufixo ao id do modelo (:fastest ou :cheapest) — a política escolhida passa a valer para aquela chamada.
4. Para fixar um provedor, use o sufixo com o nome dele (por exemplo, :novita) — o pedido vai só para esse provedor.
5. Se não quiser um provedor, desligue-o nas configurações — o roteador não enviará pedidos para ele.
6. Para conversas longas, envie um UUID estável por conversa no cabeçalho X-HF-Session-Id — a conversa fica no provedor que guarda o cache de prompt.
7. Confira as abas Providers e Metrics na página do modelo para ver preços, velocidade e disponibilidade das últimas 24 horas.
8. Acompanhe o resumo de uso para ver o gasto por provedor.

Fonte: <https://huggingface.co/blog/openrouter>

## O que conferir

- Chaves próprias de provedor não valem mais para modelos de linguagem: pedidos passam pela OpenRouter e são cobrados na conta da Hugging Face. Se o seu fluxo dependia de uma chave própria, ajuste antes de contar com ela.
- Chaves próprias para provedores de imagem e vídeo continuam funcionando — não misture os dois casos.
- Geração de imagem, vídeo e áudio não passa pela OpenRouter; continua direto pelo Inference Providers como antes.
- Os números de melhora (46%, 16,9%, 16,3%) são das medições da própria OpenRouter, não de um teste independente.
- Os dados de mercado (participação de modelos abertos, volume, custo, benchmark) vêm do anúncio da Hugging Face e da OpenRouter; confira a fonte original antes de citar em decisão.
- Desligar provedores nas configurações vale para a conta ou organização; em organização, aplica-se a todos os pedidos cobrados à organização.
- Confira o resumo de uso: ele detalha a qual provedor cada pedido foi enviado — use-o para validar onde seu gasto foi.

Fonte: <https://huggingface.co/blog/openrouter>

## Glossário

- Inference Providers: serviço da Hugging Face que oferece modelos abertos para texto, imagem, vídeo e áudio por uma API única, ao preço do provedor, sem margem.
- OpenRouter: interface unificada para modelos de linguagem que roteia pedidos entre provedores com base em medições ao vivo.
- Modelo de pesos abertos (open-weight): modelo cujos pesos são publicados e podem ser executados por terceiros.
- Roteamento: escolha automática do provedor que atenderá cada pedido.
- Provedor: empresa que serve um modelo para inferência.
- Vazão (throughput): quantidade de tokens processados por unidade de tempo.
- Tempo até o primeiro token (TTFT): atraso entre o envio do pedido e a chegada do primeiro token de resposta.
- Erro de capacidade: falha por falta de capacidade no provedor.
- Sufixo de política: complemento no id do modelo que define a política de roteamento (por exemplo, :fastest).
- Cache de prompt: reutilização de parte do prompt já processada por um provedor.
- LoRA: adaptação leve aplicada a um modelo para estilo ou tarefa específica.
- Token da Hugging Face: chave de autenticação usada para chamar os serviços da Hugging Face.
- PRO/Team/Enterprise: planos da Hugging Face com créditos mensais de computação e inferência.

Fonte: <https://huggingface.co/blog/openrouter>

## Para onde ir depois

- Experimente um modelo no playground de inferência da Hugging Face.
- Leia a documentação do Inference Providers para integrar em Python, JavaScript ou HTTP.
- Liste os modelos servidos por provedores com hf models ls --warm.
- Acompanhe os próximos passos anunciados: conexão da conta OpenRouter à Hugging Face e roteamento de mais tarefas pela OpenRouter.
- Confira as abas Providers e Metrics nas páginas de modelo antes de escolher provedor.

Fonte: <https://huggingface.co/docs/inference-providers>

## Links citados

- https://huggingface.co/docs/inference-providers/index
- https://openrouter.ai

## Outros pontos

- O anúncio cita artigos relacionados da Hugging Face sobre outros provedores no Inference Providers (Baseten e DeepInfra).
- Em comentários no anúncio, um usuário perguntou como o roteamento trata o preço de cache, e outro relatou ver pedidos indo a provedores fora da lista mesmo após desativar a maioria nas configurações. São relatos de usuários, não posições oficiais; confira no resumo de uso para onde vão os seus pedidos.
