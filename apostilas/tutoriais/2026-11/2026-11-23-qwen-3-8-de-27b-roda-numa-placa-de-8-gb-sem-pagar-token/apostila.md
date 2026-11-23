# Qwen 3.8 de 27B roda numa placa de 8 GB, sem pagar token

_2026-11-23 · tutorial_

O Qwen 3.8 de 27 bilhões de parâmetros é um modelo aberto da Alibaba, com licença Apache 2.0, e roda na sua máquina sem cobrança por token. A apostila mostra qual versão baixar para uma placa de 8 GB, uma RTX 3090 ou um NVIDIA DGX Spark, com os comandos prontos. No fim, você faz a primeira pergunta ao modelo no terminal.

## O modelo e o que você precisa

O Qwen 3.8 é um modelo aberto da Alibaba, com licença Apache 2.0. Os pesos oficiais ficam no Hugging Face e a equipe do projeto publica as informações no GitHub do QwenLM. Use só esse repositório: cópias de terceiros não são oficiais.

- Uma placa de 8 GB, uma RTX 3090 ou um NVIDIA DGX Spark
- Conexão com a internet para o download
- Espaço em disco: 17,7 GB para a versão de 4 bits
- llama.cpp para carregar o modelo: github.com/ggml-org/llama.cpp

```
https://github.com/QwenLM/Qwen3.8
```

Fonte: <https://github.com/QwenLM/Qwen3.8>

## Escolha a versão pela memória

A regra vem da memória disponível. A compressão troca um pouco de precisão por espaço, e é isso que faz o modelo caber numa placa menor. Antes de baixar, abra a coleção do Qwen 3.8 no Hugging Face e veja o Qwen3.8-27B na lista.

- Placa de 8 GB: versão de 1 bit, que pede de 7 a 8 GB de memória
- RTX 3090: versão de 4 bits, que pede de 16 a 19 GB
- NVIDIA DGX Spark, com até 128 GB de memória unificada: modelo completo BF16, de 56 GB
- A versão de 4 bits (arquivo de 17,7 GB) não cabe numa placa de 8 GB. Nessa placa, use a de 1 bit.
- Sem acesso ao Hugging Face, o projeto indica o ModelScope: modelscope.cn/collections/Qwen/Qwen38

```
https://huggingface.co/collections/Qwen/qwen38
```

Fonte: <https://unsloth.ai/docs/models/qwen3.8>

## Placa de 8 GB: baixe a versão de 1 bit

Instale o pacote do Hugging Face e baixe só o arquivo de 1 bit, o Qwen3.8-27B-UD-IQ1_S.gguf, de 6,19 GB. Ele vai para a pasta unsloth/Qwen3.8-27B-GGUF.

Se o comando der erro, confira se o nome do repositório está igual ao da apostila.

Fonte: <https://huggingface.co/unsloth/Qwen3.8-27B-GGUF>

## RTX 3090: baixe a versão de 4 bits

O arquivo Qwen3.8-27B-UD-Q4_K_XL.gguf pesa 17,7 GB e vai para a mesma pasta.

Fonte: <https://huggingface.co/unsloth/Qwen3.8-27B-GGUF>

## DGX Spark: baixe o modelo completo

No DGX Spark o Qwen roda com a precisão original. O Qwen/Qwen3.8-27B, em BF16, ocupa 56 GB e vem direto do repositório oficial da Alibaba. Se o download parar por falta de conexão ou de espaço, resolva e rode o mesmo comando de novo.

```
hf download Qwen/Qwen3.8-27B
```

Fonte: <https://huggingface.co/Qwen/Qwen3.8-27B>

## Confira a licença antes de usar num produto

Abra o cartão do modelo no Hugging Face. Ele mostra a descrição, os resultados de testes e a licença apache-2.0. Se não achar a licença, procure no topo da página do modelo de 27 bilhões.

- Caminho: Hugging Face > Qwen/Qwen3.8-27B > Model card

Fonte: <https://huggingface.co/Qwen/Qwen3.8-27B>

## Teste: faça uma pergunta ao modelo

Com o llama.cpp compilado (o guia de compilação está na documentação da Unsloth), rode o llama-cli. O comando abaixo carrega a versão de 4 bits e abre uma conversa no terminal. A resposta aparece na sua máquina, sem cobrança por token.

- Placa de 8 GB: troque o arquivo por Qwen3.8-27B-UD-IQ1_S.gguf
- DGX Spark com o modelo completo: use vllm serve "Qwen/Qwen3.8-27B" (github.com/vllm-project/vllm)
- Erro de memória: a versão é grande demais para a placa. Baixe a menor.

```
./llama.cpp/llama-cli --model unsloth/Qwen3.8-27B-GGUF/Qwen3.8-27B-UD-Q4_K_XL.gguf --temp 1.0 --top-p 0.95 --top-k 20 --min-p 0.0
```

Fonte: <https://unsloth.ai/docs/models/qwen3.8>

## Além do vídeo

- O Qwen3.8-2.4T-A95B, outro modelo da série, também está no Hugging Face e no ModelScope.
- O controle de raciocínio do Qwen3.8: a profundidade se ajusta com reasoning_effort, e o contexto de raciocínio das mensagens anteriores é mantido com preserve_thinking.
- Nos frameworks compatíveis, o download pelo ModelScope se ativa com variáveis de ambiente como SGLANG_USE_MODELSCOPE=true ou VLLM_USE_MODELSCOPE=true.
- A página oficial do NVIDIA DGX Spark: nvidia.com/en-us/products/workstations/dgx-spark/
