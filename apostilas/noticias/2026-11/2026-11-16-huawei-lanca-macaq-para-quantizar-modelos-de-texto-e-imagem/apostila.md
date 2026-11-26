# Huawei lança MACaQ para quantizar modelos de texto e imagem

_2026-11-16 · noticia_

O MACaQ é uma ferramenta de quantização de código aberto da Huawei Computing Systems Lab para encolher modelos de texto, imagem, vídeo e áudio e rodá-los com menos memória. Ele quantiza um modelo de 122 bilhões de parâmetros em 64 minutos usando 32,5 GB de memória de dispositivo e, no Llama-3-8B, iguala a melhor perplexidade de MR-GPTQ e DuQuant++ com 11 vezes menos tempo. A apostila mostra como o método funciona, quais backends usar e os comandos para Diffusers, llama.cpp, vLLM e PyTorch. Ao final, você saberá escolher o caminho certo para o seu hardware e conferir limites, licenças e resultados antes de confiar.

## O fato

Huawei Computing Systems Lab publicou no GitHub o MACaQ, uma ferramenta de quantização de código aberto sob licença Apache 2.0. O projeto quantiza e roda modelos de texto, imagem, vídeo e áudio com llama.cpp, vLLM, Diffusers e PyTorch.

O artigo que descreve o método foi submetido em 7 de novembro de 2026 e revisado em 11 de novembro de 2026. Os autores são Lorenz K. Muller, Philippe Bich, Chiara Boretti, Hyun-Min Chang, Jiawei Zhuang e Lukas Cavigelli.

O projeto também inclui o MACaQ-R, que refina GGUFs existentes mantendo compatibilidade com o llama.cpp padrão, e anuncia que modelos Qwen4-27B quantizados com MACaQ e compatíveis com o llama.cpp padrão chegarão em breve.

- Código: https://github.com/huawei-csl/MACaQ
- Artigo: https://arxiv.org/abs/2611.10649
- Blog: https://huawei-csl.com/blog/macaq/

Fonte: <https://github.com/huawei-csl/MACaQ>

## Por que isso importa

Quantizar é reduzir a precisão dos números do modelo para que ele ocupe menos memória e gaste menos computação. O método descrito no artigo faz isso em W4A4, ou seja, pesos e ativações em 4 bits (o backend llama.cpp também oferece GGUF de 2 e 3 bits), e não se limita a texto: o mesmo projeto cobre geração de imagem, vídeo e áudio.

O ponto central é a independência por camada. Em vez de propagar transformações entre camadas, o MACaQ trata cada camada linear sozinha, aplica uma escala por canal e uma transformação block-Hadamard online nas ativações e absorve as transformações inversas nos pesos. Isso evita dependência entre camadas e permite processar o modelo em fluxo, com uma camada por vez na memória.

Na prática, isso aproxima a quantização de hardware mais modesto. Um modelo de 122 bilhões de parâmetros pode ser quantizado em 64 minutos usando 32,5 GB de memória de dispositivo, e o checkpoint resultante roda localmente.

Fonte: <https://arxiv.org/abs/2611.10649>

## Como o MACaQ funciona

O método é uma quantização pós-treino em MXFP4 W4A4. Ele quantiza cada camada linear de forma independente, com transformações de ativação online e refinamento consciente da Hessiana.

Para melhorar além do arredondamento direto, o projeto usa o Flip-Refinement, um procedimento de descida de coordenadas consciente da Hessiana que move códigos FP4 individuais para valores representáveis vizinhos.

Apesar de executar as transformações de ativação durante a inferência, o MACaQ adiciona 2,3% de sobrecarga de ponta a ponta sobre o MXFP4 puro no Qwen3-32B em vLLM.

Fonte: <https://arxiv.org/abs/2611.10649>

## Diffusers: imagem, vídeo e áudio

O backend Diffusers quantiza transformers de difusão, salva checkpoints em safetensors e gera imagem, vídeo ou áudio. A calibração de imagem para vídeo usa imagens de condicionamento. O modo é W4A4.

Receitas incluem FLUX.2-klein-4B para imagem, Wan2.2-TI2V-5B-Diffusers para vídeo e imagem para vídeo, e stable-audio-1.0 para áudio. O checkpoint do Stable Audio é uma publicação da comunidade e não declara licença para os pesos.

Use Python 3.12 e um ambiente separado para este backend. Os diretórios de saída da quantização precisam ser novos. Os comandos abaixo instalam o ambiente, preparam a calibração e quantizam o FLUX.2-klein-4B.

- Modelo de imagem: black-forest-labs/FLUX.2-klein-4B
- Modelo de vídeo: Wan-AI/Wan2.2-TI2V-5B-Diffusers
- Modelo de áudio: ylacombe/stable-audio-1.0
- Guia: https://github.com/huawei-csl/MACaQ/tree/main/diffusers
- Diffusers: https://github.com/huggingface/diffusers

```
python3.12 -m venv .venv-diffusers
.venv-diffusers/bin/python -m pip install -r requirements/diffusers.txt
python3.12 examples/prepare_diffusion_calibration.py --output data/diffusion
.venv-diffusers/bin/python diffusers/cli.py quantize --family flux2-klein --model black-forest-labs/FLUX.2-klein-4B --calibration data/diffusion/calibration.txt --output models/flux-macaq --gpu 0
```

Fonte: <https://github.com/huawei-csl/MACaQ/tree/main/diffusers>

## Diffusers: imagem, vídeo e áudio (continuação)

Para o Wan2.2-TI2V-5B-Diffusers e o stable-audio-1.0, no mesmo ambiente, prepare a calibração e rode a quantização de cada um.

```
python3.12 examples/prepare_diffusion_calibration.py --images --output data/wan-calibration
.venv-diffusers/bin/python diffusers/cli.py quantize --family wan --model Wan-AI/Wan2.2-TI2V-5B-Diffusers --calibration-jsonl data/wan-calibration/text_to_video-calibration.jsonl --output models/wan-macaq --keep-layers 'blocks.*.attn*.*' --flips 64 --gpu 0
python3.12 examples/prepare_diffusion_audio_calibration.py --output data/audio-calibration
.venv-diffusers/bin/python diffusers/cli.py quantize --family stable-audio --model ylacombe/stable-audio-1.0 --calibration-jsonl data/audio-calibration/calibration.jsonl --audio-seconds 10 --output models/audio-macaq --gpu 0
```

Fonte: <https://github.com/huawei-csl/MACaQ/tree/main/diffusers>

## llama.cpp: texto em GGUF e MACaQ-R

O backend llama.cpp quantiza modelos de texto para GGUF em 2, 3 ou 4 bits e também roda em CPU. Há receitas para Qwen/Qwen3-4B, Qwen/Qwen3.8-27B, Qwen/Qwen3-30B-A3B, Qwen/Qwen3-Coder-30B-A3B-Instruct, Qwen/Qwen3.6-35B-A3B, allenai/OLMoE-1B-7B-0125-Instruct, Qwen/Qwen3-Next-80B-A3B-Instruct e Qwen/Qwen3.8-Flash-Next.

Além do MACaQ, o projeto lança o MACaQ-R, que refina códigos de peso em um GGUF já quantizado (o repositório descreve o fluxo a partir de um GGUF de modelo MoE), preservando formatos e escalas de bloco, e continua compatível com uma instalação padrão do llama.cpp. Para isso, usa o GGUF quantizado, a fonte original correspondente, um teacher em F16 e texto de calibração.

Na comparação publicada para o Qwen3.6-35B-A3B, o GGUF MACaQ-R Q4_K_XL tem divergência KL para FP16 de 0,013367, contra 0,015731 do Unsloth UD-Q4_K_XL, ambos com 22,36 GB (quanto menor, melhor).

Os comandos abaixo criam o ambiente, convertem o Qwen3.8-27B para GGUF F16 e o quantizam. Antes da conversão e da quantização, compile o runtime incluído com suporte a CUDA, usando cmake, conforme o guia do backend.

- Guia: https://github.com/huawei-csl/MACaQ/tree/main/llamacpp
- llama.cpp: https://github.com/ggml-org/llama.cpp
- Download MACaQ-R: https://huggingface.co/huawei-csl/Qwen3.6-35B-A3B-MACaQ-R-GGUF

```
python3.12 -m venv .venv-llamacpp
.venv-llamacpp/bin/pip install -r requirements/llamacpp-qwen35.txt
.venv-llamacpp/bin/python llamacpp/llama.cpp/convert_hf_to_gguf.py models/Qwen3.8-27B --outtype f16 --outfile models/original-f16.gguf
.venv-llamacpp/bin/python llamacpp/macaq.py quantize --model models/original-f16.gguf --hf models/Qwen3.8-27B --calibration data/calibration.txt --format IQ4_XS --had-block 64 --device cuda --gpu 0 --gpu-layers 99 --output models/qwen38-27b-macaq.gguf --work-dir work/qwen38-27b
```

Fonte: <https://github.com/huawei-csl/MACaQ/tree/main/llamacpp>

## llama.cpp: texto em GGUF e MACaQ-R (continuação)

Para criar um modelo MACaQ-R a partir de um GGUF quantizado e da fonte original correspondente, use o primeiro comando abaixo. Com o GGUF salvo localmente, o segundo o executa no llama.cpp padrão; para servir o mesmo arquivo, o repositório indica llama serve -m models/model-macaq-r.gguf.

```
.venv-llamacpp/bin/python llamacpp/macaq.py refine \
  --model models/model-q4.gguf --hf models/original \
  --teacher models/original-f16.gguf --calibration data/calibration.txt \
  --output models/model-macaq-r.gguf --work-dir work/refinement
llama cli -m models/model-macaq-r.gguf
```

Fonte: <https://github.com/huawei-csl/MACaQ>

## vLLM: texto e API local

O backend vLLM quantiza texto em W4A4 por padrão ou só pesos e serve o resultado pela API HTTP. No Qwen3.8-27B, a perplexidade passa de 2,8463 em BF16 para 2,8994 em W4A4, com prefill 2,33 vezes e decode 2,58 vezes mais rápidos.

O fluxo tem quatro passos de instalação, depois um comando de quantização com texto de calibração e um comando de serviço. A API fica em http://127.0.0.1:8000/v1/chat/completions. O serviço usa o checkpoint salvo, sem calibrar de novo.

- Site: https://vllm.ai
- Guia: https://github.com/huawei-csl/MACaQ/blob/main/vllm/README.md

```
python3.12 -m venv .venv-vllm
.venv-vllm/bin/pip install -r requirements/vllm-qwen35.txt
.venv-vllm/bin/pip install -r requirements/build.txt
.venv-vllm/bin/pip install --no-build-isolation --no-deps -e .
.venv-vllm/bin/python vllm/cli.py quantize --model Qwen/Qwen3.8-27B --calibration data/calibration.txt --output models/qwen38-27b-macaq --gpu 0
.venv-vllm/bin/python vllm/cli.py serve --model models/qwen38-27b-macaq --gpu 0
```

Fonte: <https://github.com/huawei-csl/MACaQ/blob/main/vllm/README.md>

## PyTorch: síntese de voz

O backend PyTorch quantiza geradores de fala em W4A4 e gera áudio WAV mono de 24 kHz e 16 bits. Os checkpoints compactos carregam sem repetir a calibração. No Qwen3-TTS, são 231 camadas lineares quantizadas.

Receitas incluem Qwen3-TTS e Chatterbox Turbo. O projeto recomenda Python 3.12 e um ambiente separado por backend. Os comandos abaixo instalam o ambiente e quantizam os dois modelos.

- Guia: https://github.com/huawei-csl/MACaQ/tree/main/pytorch
- PyTorch: https://pytorch.org

```
python3.12 -m venv .venv-tts
source .venv-tts/bin/activate
pip install -r requirements/tts.txt
python pytorch/qwen3_tts.py quantize --model models/qwen3-tts-source --prompts data/qwen3-tts/prompts.json --output models/qwen3-tts-macaq --work-dir work/qwen3-tts --gpu 0
python pytorch/chatterbox_turbo.py quantize --model models/chatterbox-source --prompts data/chatterbox/prompts.json --work-dir work/chatterbox --output models/chatterbox-macaq --gpu 0
```

Fonte: <https://github.com/huawei-csl/MACaQ/tree/main/pytorch>

## Ascend: kernels para NPU

Kernels W4A4 densos e agrupados do MACaQ estão disponíveis em pull requests do CANN: ops-nn #12568, com kernels PTO-ISA via ascend_ops_nn, e ops-tilelang #44, com kernels TileLang e backend CCE.

É preciso seguir as instruções de compilação deles para versões compatíveis de CANN, PyTorch e torch_npu. A execução do modelo completo exige integração com um runtime de inferência Ascend.

- ops-nn #12568: https://gitcode.com/cann/ops-nn/pull/12568
- ops-tilelang #44: https://gitcode.com/cann/ops-tilelang/pull/44

Fonte: <https://github.com/huawei-csl/MACaQ>

## Os números

- 122 bilhões de parâmetros: tamanho do modelo quantizado em 64 minutos, usando 32,5 GB de memória de dispositivo.
- 11 vezes menos tempo: no Llama-3-8B, o MACaQ iguala a melhor perplexidade de MR-GPTQ e DuQuant++ com esse ganho de tempo; também pode alcançar perplexidade mais baixa que esses métodos.
- 2,8463 e 2,8994: perplexidade do Qwen3.8-27B em BF16 e em W4A4 no vLLM; valores mais baixos indicam menos erro de previsão.
- 2,33× e 2,58×: ganho de prefill e decode do Qwen3.8-27B em W4A4 no vLLM.
- 2,3%: sobrecarga de ponta a ponta do MACaQ sobre o MXFP4 puro no Qwen3-32B em vLLM.
- 0,015731 e 0,013367: divergência KL para FP16 do Qwen3.6-35B-A3B nos GGUFs Unsloth UD-Q4_K_XL e MACaQ-R Q4_K_XL, ambos com 22,36 GB.
- 231 camadas lineares: quantidade quantizada em W4A4 no Qwen3-TTS.
- 24 kHz, mono, 16 bits: formato do áudio WAV gerado pelos modelos de fala.
- Python 3.12: versão recomendada, com ambiente separado para cada backend.

Fonte: <https://arxiv.org/abs/2611.10649>

## O que muda para você

Para quem roda modelos localmente, o ganho é direto: menos memória para quantizar e checkpoints prontos para inferência sem calibrar de novo em alguns casos.

Exemplo: imagine um computador com 32,5 GB de memória de dispositivo e um modelo de 122 bilhões de parâmetros. Com o MACaQ, a quantização leva 64 minutos e o resultado fica pronto para uso local. Em texto, o Qwen3.8-27B em W4A4 mantém perplexidade próxima do BF16 e mais que dobra a velocidade de prefill e decode. Em imagem, vídeo e áudio, o Diffusers gera com W4A4. Em voz, o PyTorch gera WAV mono de 24 kHz sem repetir a calibração.

Fonte: <https://github.com/huawei-csl/MACaQ>

## O que fazer hoje

1. Escolha o backend pelo tipo de modelo: Diffusers para imagem, vídeo e áudio; llama.cpp para texto em GGUF; vLLM para texto com API HTTP; PyTorch para fala.
2. Instale Python 3.12 e crie um ambiente virtual separado para o backend escolhido.
3. Clone o repositório e leia o guia do backend antes de rodar comandos.
4. Prepare os dados de calibração indicados para o modelo escolhido.
5. Rode a quantização e confira se o diretório de saída é novo.
6. Teste a inferência com o runtime do backend e compare perplexidade ou qualidade.
7. Se você já tem um GGUF quantizado, use o MACaQ-R com a fonte original correspondente para refiná-lo.

Fonte: <https://github.com/huawei-csl/MACaQ>

## O que conferir

- Os diretórios de saída da quantização devem ser novos; não reutilize uma pasta anterior.
- O checkpoint do Stable Audio é uma publicação da comunidade e não declara licença para os pesos; confira a licença antes de distribuir.
- Os modelos Qwen4-27B compatíveis com llama.cpp padrão ainda estão chegando; não trate como disponíveis hoje.
- O MACaQ-R exige o GGUF quantizado, a fonte original correspondente, um teacher em F16 e texto de calibração.
- Os kernels Ascend exigem integração com runtime de inferência Ascend e versões compatíveis; não são plug and play.
- As comparações de perplexidade valem para os modelos e condições citados, como Llama-3-8B e Qwen3.8-27B em vLLM.
- O MACaQ é Apache 2.0, mas componentes de terceiros mantêm suas licenças próprias.
- O repositório informa que o llama.cpp também roda em CPU; os exemplos de quantização desta apostila usam GPU.

Fonte: <https://github.com/huawei-csl/MACaQ>

## Glossário

- Quantização: redução da precisão dos números do modelo para economizar memória e computação.
- W4A4: pesos e ativações representados com 4 bits.
- MXFP4: formato de ponto flutuante de 4 bits usado pelo método.
- GGUF: formato de arquivo para modelos quantizados usado pelo llama.cpp.
- Perplexidade: medida de erro ao prever texto; quanto menor, melhor.
- Calibração: dados de exemplo usados para ajustar a quantização.
- Block-Hadamard: transformação aplicada online às ativações de cada camada.
- Flip-Refinement: ajuste fino que move códigos FP4 para valores vizinhos.
- Prefill: etapa que processa o prompt antes da geração.
- Decode: etapa que gera os tokens seguintes.
- Diffusion transformer: modelo de difusão baseado em transformer.
- Safetensors: formato de checkpoint usado pelo Diffusers.
- MACaQ-R: refinamento de um GGUF já quantizado, mantendo compatibilidade com llama.cpp padrão.

Fonte: <https://arxiv.org/abs/2611.10649>

## Para onde ir depois

- Repositório oficial: https://github.com/huawei-csl/MACaQ
- Blog oficial: https://huawei-csl.com/blog/macaq/
- Artigo: https://arxiv.org/abs/2611.10649
- Guia Diffusers: https://github.com/huawei-csl/MACaQ/tree/main/diffusers
- Guia llama.cpp: https://github.com/huawei-csl/MACaQ/tree/main/llamacpp
- Guia vLLM: https://github.com/huawei-csl/MACaQ/blob/main/vllm/README.md
- Guia PyTorch: https://github.com/huawei-csl/MACaQ/tree/main/pytorch
- Modelos quantizados: https://huggingface.co/collections/huawei-csl/macaq
- Download MACaQ-R Qwen3.6-35B-A3B: https://huggingface.co/huawei-csl/Qwen3.6-35B-A3B-MACaQ-R-GGUF
- vLLM: https://vllm.ai
- Diffusers: https://huggingface.co/docs/diffusers
- PyTorch: https://pytorch.org
- llama.cpp: https://github.com/ggml-org/llama.cpp
- Cite o artigo em pesquisas: https://arxiv.org/abs/2611.10649

Fonte: <https://github.com/huawei-csl/MACaQ>

## Outros pontos

- Citação BibTeX do artigo, disponível na página do arXiv, para quem for usar o MACaQ em pesquisa.
- Comparação de tamanho e divergência KL para FP16 entre GGUFs publicados do Qwen3-4B, apresentada no blog oficial.
- Pergunta aberta da comunidade sobre o custo da transformação block-Hadamard em CPU ou GPUs antigas sem suporte nativo a FP4.
