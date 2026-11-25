# Qwen 3.8 de 27B roda numa placa de 8 GB, sem pagar token

_2026-11-23 · tutorial_

O Qwen 3.8 de 27 bilhões de parâmetros é um modelo aberto da Alibaba, com licença Apache 2.0, e roda na sua máquina sem cobrança por token. A apostila mostra qual versão baixar para uma placa de 8 GB, uma RTX 3090 ou um NVIDIA DGX Spark. No fim, você faz a primeira pergunta ao modelo no terminal.

## O que você terá no fim

Ao final, o Qwen 3.8 de 27B estará baixado na versão certa para a sua máquina, e você terá feito a primeira pergunta ao modelo no terminal. Os pesos oficiais ficam no Hugging Face e a equipe do projeto publica as informações no GitHub do QwenLM. Use só esse repositório: cópias de terceiros não são oficiais. Fonte: https://github.com/QwenLM/Qwen3.8

- Uma placa de 8 GB, uma RTX 3090 ou um NVIDIA DGX Spark.
- Conexão com a internet para o download.
- Espaço em disco: 17,7 GB para a versão de 4 bits.
- llama.cpp para carregar o modelo: github.com/ggml-org/llama.cpp.

Fonte: <https://github.com/QwenLM/Qwen3.8>

## Passo a passo

Siga os passos na ordem. A regra de escolha da versão e o comando de teste ficam nas seções próprias. A regra vem da memória disponível: a compressão troca um pouco de precisão por espaço, e é isso que faz o modelo caber numa placa menor.

1. escolha a versão pela memória. Placa de 8 GB: versão de 1 bit. RTX 3090: versão de 4 bits. DGX Spark: modelo completo BF16. Resultado esperado: você sabe qual arquivo baixar.
2. baixe a versão de 1 bit numa placa de 8 GB. Baixe só o arquivo Qwen3.8-27B-UD-IQ1_S.gguf, de 6,19 GB, na pasta unsloth/Qwen3.8-27B-GGUF (repositório: https://huggingface.co/unsloth/Qwen3.8-27B-GGUF). Resultado esperado: o arquivo de 1 bit está na pasta.
3. baixe a versão de 4 bits numa RTX 3090. O arquivo Qwen3.8-27B-UD-Q4_K_XL.gguf pesa 17,7 GB e vai para a mesma pasta. Resultado esperado: o arquivo de 4 bits está na pasta.
4. no DGX Spark, baixe o modelo completo. O Qwen/Qwen3.8-27B, em BF16, ocupa 56 GB e vem direto do repositório oficial da Alibaba. Resultado esperado: o modelo completo fica disponível.
5. faça uma pergunta ao modelo no terminal. Com o llama.cpp compilado, rode o llama-cli com a versão de 4 bits. Resultado esperado: a resposta aparece na sua máquina, sem cobrança por token.

Fonte: <https://unsloth.ai/docs/models/qwen3.8>

## Repositório oficial do Qwen 3.8

Use o repositório oficial. Cópias de terceiros não são oficiais. Fonte: https://github.com/QwenLM/Qwen3.8

```
https://github.com/QwenLM/Qwen3.8
```

Fonte: <https://github.com/QwenLM/Qwen3.8>

## Escolher a versão pela memória

Antes de baixar, abra a coleção do Qwen 3.8 no Hugging Face (https://huggingface.co/collections/Qwen/qwen38) e veja o Qwen3.8-27B na lista. Sem acesso ao Hugging Face, o projeto indica o ModelScope: modelscope.cn/collections/Qwen/Qwen38. Fonte: https://unsloth.ai/docs/models/qwen3.8

- Placa de 8 GB: versão de 1 bit, que pede de 7 a 8 GB de memória.
- RTX 3090: versão de 4 bits, que pede de 16 a 19 GB.
- NVIDIA DGX Spark, com até 128 GB de memória unificada: modelo completo BF16, de 56 GB.
- A versão de 4 bits (arquivo de 17,7 GB) não cabe numa placa de 8 GB. Nessa placa, use a de 1 bit.

```
https://huggingface.co/collections/Qwen/qwen38
```

Fonte: <https://unsloth.ai/docs/models/qwen3.8>

## Baixar no DGX Spark

Se o download parar por falta de conexão ou de espaço, resolva e rode o mesmo comando de novo. Fonte: https://huggingface.co/Qwen/Qwen3.8-27B

```
hf download Qwen/Qwen3.8-27B
```

Fonte: <https://huggingface.co/Qwen/Qwen3.8-27B>

## Teste: faça uma pergunta ao modelo

Com o llama.cpp compilado (o guia de compilação está na documentação da Unsloth), rode o llama-cli. O comando abaixo carrega a versão de 4 bits e abre uma conversa no terminal. A resposta aparece na sua máquina, sem cobrança por token. Fonte: https://unsloth.ai/docs/models/qwen3.8

- [ ] Placa de 8 GB: troque o arquivo por Qwen3.8-27B-UD-IQ1_S.gguf.
- [ ] DGX Spark com o modelo completo: use vllm serve "Qwen/Qwen3.8-27B" (github.com/vllm-project/vllm).
- [ ] Erro de memória: a versão é grande demais para a placa. Baixe a menor.

```
./llama.cpp/llama-cli --model unsloth/Qwen3.8-27B-GGUF/Qwen3.8-27B-UD-Q4_K_XL.gguf --temp 1.0 --top-p 0.95 --top-k 20 --min-p 0.0
```

Fonte: <https://unsloth.ai/docs/models/qwen3.8>

## Confira a licença e outras opções

Antes de usar num produto, abra o cartão do modelo no Hugging Face. Ele mostra a descrição, os resultados de testes e a licença apache-2.0. Caminho: Hugging Face > Qwen/Qwen3.8-27B > Model card. O Qwen3.8-2.4T-A95B, outro modelo da série, também está no Hugging Face e no ModelScope. A profundidade do raciocínio se ajusta com reasoning_effort, e o contexto de raciocínio das mensagens anteriores é mantido com preserve_thinking. A página oficial do NVIDIA DGX Spark: nvidia.com/en-us/products/workstations/dgx-spark/

Fonte: <https://huggingface.co/Qwen/Qwen3.8-27B>
