# Hugging Face passa a rotear modelos pela OpenRouter

_2026-11-23 · noticia_

A Hugging Face trocou o roteador próprio do Inference Providers pela OpenRouter. As chamadas a modelos de linguagem agora são tentadas em outro provedor quando o primeiro falha, e o código de quem usa o token da Hugging Face continua o mesmo. Nas medições da OpenRouter, os erros de capacidade caíram 46%. Há uma quebra: em modelos de linguagem, a chave própria de provedor deixou de valer.

## O que mudou

O Inference Providers deixou de usar o roteador próprio da Hugging Face. As requisições a modelos de linguagem passam pela OpenRouter, que escolhe o provedor de cada chamada.

Antes, a Hugging Face escolhia um provedor para o pedido e devolvia o erro dele se falhasse. Agora o pedido é refeito em outro provedor dentro da mesma chamada. Quem chama pelo token da Hugging Face não precisa alterar o código.

Fonte: <https://huggingface.co/blog/openrouter>

## Como a OpenRouter escolhe o provedor

A cada chamada, a OpenRouter olha preço, velocidade e confiabilidade medidos ao vivo e envia o pedido para a melhor combinação dos três. Ela não se limita ao menor preço de tabela.

Se um provedor fica lento ou começa a errar, o tráfego sai dele até ele se recuperar. A tentativa que falhou é refeita no próximo melhor provedor.

O roteamento também considera o cache: uma conversa permanece no provedor que guarda o cache do prompt.

Fonte: <https://huggingface.co/blog/openrouter>

## O que as medições mostram

Nas medições da própria OpenRouter, o novo roteamento reduziu as falhas e melhorou a velocidade.

- Erros de capacidade: queda de 46%
- Tempo até o primeiro token: melhora de 16,9%
- Vazão: aumento de 16,3%

Fonte: <https://huggingface.co/blog/openrouter>

## Como mandar no roteamento

Para escolher a política ou o provedor, acrescente um sufixo ao id do modelo. Sem sufixo, vale a melhor combinação de preço, velocidade e confiabilidade.

- `:fastest` escolhe a maior vazão
- `:cheapest` escolhe o menor preço
- `:novita` envia só para esse provedor (o formato é modelo:provedor)

```
zai-org/GLM-5.3 # default: best mix of price, speed and reliability
zai-org/GLM-5.3:fastest # highest throughput
zai-org/GLM-5.3:cheapest # lowest price
zai-org/GLM-5.3:novita # only Novita
```

Fonte: <https://huggingface.co/blog/openrouter>

## Preço e cobrança

O preço não muda. Você paga o valor do provedor na fatura da Hugging Face, e a Hugging Face não cobra acréscimo sobre ele.

Nas configurações da conta ou da organização dá para desligar provedores. O roteador nunca envia seus pedidos a um provedor desligado, e a regra da organização vale para toda requisição cobrada nela.

Fonte: <https://huggingface.co/blog/openrouter>

## Quebra de compatibilidade: chave própria de provedor

Com modelos de linguagem, as requisições passam pela OpenRouter e são cobradas na sua conta ou organização da Hugging Face. Por isso, a chave própria de um provedor não vale mais nesses modelos.

Você ainda escolhe o provedor pelo sufixo `modelo:provedor` ou desliga provedores nas configurações, e o código segue o mesmo.

Fonte: <https://huggingface.co/blog/openrouter>

## Imagem, vídeo e áudio

A geração de imagem, vídeo e áudio continua como antes, direto pelo Inference Providers da Hugging Face, sem passar pela OpenRouter. O mesmo token e a mesma API seguem valendo. Chaves próprias de provedores de imagem e vídeo continuam funcionando.

Fonte: <https://huggingface.co/docs/inference-providers/index>

## Próximos passos e links

Esta é a primeira etapa da parceria com a OpenRouter. A Hugging Face anuncia a conexão da sua conta da OpenRouter e mais tarefas roteadas pela OpenRouter.

- Anúncio oficial: https://huggingface.co/blog/openrouter
- Documentação do Inference Providers: https://huggingface.co/docs/inference-providers
- OpenRouter: https://openrouter.ai

Fonte: <https://huggingface.co/blog/openrouter>

## Além do vídeo

- O roteador aceita as APIs Chat Completions e Responses da OpenAI e a Messages da Anthropic para todo modelo de chat, seja qual for o provedor por trás.
- Há guias de configuração para Claude Code, Codex, OpenCode, Pi e Hermes Agent.
- Para deixar o cache explícito, envie um UUID estável por conversa no cabeçalho X-HF-Session-Id.
- Nas páginas de modelos, a aba Providers lista os provedores com preço de entrada e saída, velocidade e disponibilidade nas últimas 24 horas, e a aba Metrics mostra o melhor preço, vazão, tempo até o primeiro token, contexto e disponibilidade entre eles.
- Usuários PRO recebem US$ 2 em créditos por mês, e organizações Team e Enterprise recebem US$ 2 por assento.
