# Kimi K3.1 Pro bate o Opus 5.5 em 3 testes por US$ 2

_2026-11-23 · noticia_

A Moonshot AI lançou o Kimi K3.1 Pro com pesos abertos. Pela tabela da própria empresa, ele passa o Claude Opus 5.5 em DeepSWE, BrowseComp e HLE com ferramentas, e fica atrás em Terminal-Bench 4.0, GPQA-Diamond e OSWorld. Na OpenRouter custa US$ 2 por milhão de tokens de entrada e US$ 10 por milhão de saída.

## O fato

A Moonshot AI lançou o Kimi K3.1 Pro com pesos abertos. Pela tabela da própria empresa, ele passa o Claude Opus 5.5 em DeepSWE, BrowseComp e HLE com ferramentas, e fica atrás em Terminal-Bench 4.0, GPQA-Diamond e OSWorld.

Os pesos estão no Hugging Face. Você pode chamar o modelo pela API ou hospedar num servidor seu. Fonte: https://huggingface.co/moonshotai/Kimi-K3.1-Pro

Fonte: <https://huggingface.co/moonshotai/Kimi-K3.1-Pro>

## O modelo

O Kimi K3.1 Pro usa arquitetura Mixture-of-Experts (MoE). São 2,8 trilhões de parâmetros no total, mas só 104 bilhões entram em ação a cada token. O contexto chega a 1 milhão de tokens, e ele aceita texto e imagem.

- Parâmetros totais: 2.8T.
- Parâmetros ativos: 104B.
- Contexto: 1048576 tokens.
- Entrada: texto e imagem.

Fonte: <https://huggingface.co/moonshotai/Kimi-K3.1-Pro>

## Onde ele vence o Opus 5.5

As três vitórias são em código e em tarefas de agente com busca e ferramentas. Todas por margem curta.

- DeepSWE v1.1: 75,5 contra 74,2 do Claude Opus 5.5.
- BrowseComp: 92,1 contra 90,8 do Claude Opus 5.5.
- HLE-Full com ferramentas: 70,0 contra 67,7 do Claude Opus 5.5.

Fonte: <https://huggingface.co/moonshotai/Kimi-K3.1-Pro>

## Onde ele fica atrás

As derrotas também são apertadas. O Opus segue na frente em tarefas no terminal e no uso de computador. Em ciência avançada, quem lidera é o GPT-6 Astra.

- Terminal-Bench 4.0: 65,7 contra 66,4 do Claude Opus 5.5.
- GPQA-Diamond: 94,2 contra 96,1 do GPT-6 Astra.
- OSWorld V2.1: 79,6 contra 81,8 do Claude Opus 5.5.

Fonte: <https://huggingface.co/moonshotai/Kimi-K3.1-Pro>

## Preço e acesso

Na OpenRouter, o modelo custa US$ 2 por milhão de tokens de entrada e US$ 10 por milhão de tokens de saída.

Na API oficial da Kimi, selecione o modelo pelo nome abaixo. A API é compatível com o formato da OpenAI e com o da Anthropic, então dá para aproveitar o código que você já tem. Fonte: https://platform.kimi.ai

```
kimi-k3.1-pro
```

Fonte: <https://platform.kimi.ai>

## Como ajustar o raciocínio

O esforço de raciocínio é definido no campo reasoning_effort da requisição, que aceita "low", "high" e "max". O padrão é "max".

Em conversas com várias trocas e em chamadas de ferramenta, devolva em messages a mensagem completa do assistente, do jeito que a API mandou, com reasoning_content e tool_calls. Se você devolver só o content, o modelo perde o raciocínio que já fez. Fonte: https://huggingface.co/moonshotai/Kimi-K3.1-Pro

```
reasoning_effort="max",
```

Fonte: <https://huggingface.co/moonshotai/Kimi-K3.1-Pro>

## Antes de trocar de fornecedor

Todos os números desta apostila saem do cartão oficial do modelo, publicado pela própria Moonshot. Rode o Kimi nas suas tarefas antes de mudar o orçamento.

Se o seu trabalho é pesquisa e código, ele merece o teste. Se envolve operar o computador, o Opus 5.5 ainda leva vantagem. Fonte: https://huggingface.co/moonshotai/Kimi-K3.1-Pro

Fonte: <https://huggingface.co/moonshotai/Kimi-K3.1-Pro>
