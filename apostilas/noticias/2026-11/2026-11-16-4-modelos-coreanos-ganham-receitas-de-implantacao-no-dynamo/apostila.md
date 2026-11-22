# 4 modelos coreanos ganham receitas de implantação no Dynamo

_2026-11-16 · noticia_

NVIDIA publicou em 9 de novembro de 2026 receitas de implantação no Dynamo para quatro modelos abertos coreanos: A.X K2, K-EXAONE 2.0, Solar Open 2 e Motif-3. Cada receita traz checkpoint oficial no Hugging Face, manifest YAML e comando de deploy via kubectl para GPUs B200. A apostila reúne os caminhos, os comandos e as fontes oficiais para colocar cada modelo em produção.

## O anúncio

Em 9 de novembro de 2026, a NVIDIA publicou receitas de implantação otimizadas no Dynamo para quatro modelos abertos coreanos: A.X K2 (SK Telecom), K-EXAONE 2.0 (LG AI Research), Solar Open 2 (Upstage) e Motif-3 (Motif Technologies).

Os checkpoints oficiais estão publicados no Hugging Face. As receitas ficam no repositório ai-dynamo/dynamo, em manifests YAML com apiVersion nvidia.com/v1beta1 e kind DynamoGraphDeploymentRequest.

- A.X K2 — skt/A.X-K2-NVFP4
- K-EXAONE 2.0 — LGAI-EXAONE/K-EXAONE-2.0-750B-A37B-NVFP4
- Solar Open 2 — upstage/Solar-Open2-250B
- Motif-3 — Motif-Technologies/Motif-3

Fonte: <https://blogs.nvidia.com/blog/nvidia-dynamo-korea-open-models/>

## O que é o NVIDIA Dynamo

Quando um modelo passa do tamanho de uma única GPU, ele precisa ser fatiado entre várias GPUs. Isso exige coordenar roteamento de requisições e comunicação entre nós, e é aí que muita implantação trava ou perde desempenho.

O NVIDIA Dynamo é um framework open source de serving de inferência distribuído feito para esse cenário em escala de data center. Ele cuida do roteamento e da comunicação para maximizar o desempenho da inferência.

O código está aberto em github.com/ai-dynamo/dynamo para inspeção e adaptação.

Fonte: <https://blogs.nvidia.com/blog/nvidia-dynamo-korea-open-models/>

## A.X K2 (SK Telecom)

- Checkpoint oficial: https://huggingface.co/skt/A.X-K2-NVFP4
- 688B parâmetros totais, 33B ativos
- Licença Apache 2.0
- Receita: recipes/ax-k2/vllm/agg-b200-chat/deploy-generic.yaml (e disagg-b200-chat/deploy-generic.yaml) no repositório ai-dynamo/dynamo

```
kubectl apply -f deploy-generic.yaml -n dynamo-system
```

Fonte: <https://github.com/ai-dynamo/dynamo/blob/main/recipes/ax-k2/vllm/agg-b200-chat/deploy-generic.yaml>

## K-EXAONE 2.0 (LG AI Research)

- Checkpoint oficial: https://huggingface.co/LGAI-EXAONE/K-EXAONE-2.0-750B-A37B-NVFP4
- Licença Apache 2.0
- Otimizado para B200 com até 2x de desempenho fora da caixa
- Receita: recipes/k-exaone-2.0/vllm/agg-b200-chat/deploy-generic.yaml no repositório ai-dynamo/dynamo

```
kubectl apply -f deploy-generic.yaml -n dynamo-system
```

Fonte: <https://github.com/ai-dynamo/dynamo/blob/main/recipes/k-exaone-2.0/vllm/agg-b200-chat/deploy-generic.yaml>

## Solar Open 2 (Upstage)

- Checkpoint oficial: https://huggingface.co/upstage/Solar-Open2-250B
- 250B parâmetros totais, 15B ativos
- Contexto de 1M tokens
- Licença Upstage Solar License
- Receita: recipes/solar-open2-250b/vllm/agg-b200-chat/deploy.yaml (e disagg-b200-chat/deploy.yaml) no repositório ai-dynamo/dynamo

```
kubectl apply -f deploy.yaml -n dynamo-system
```

Fonte: <https://github.com/ai-dynamo/dynamo/blob/main/recipes/solar-open2-250b/vllm/agg-b200-chat/deploy.yaml>

## Motif-3 (Motif Technologies)

- Checkpoint oficial: https://huggingface.co/Motif-Technologies/Motif-3
- Variante Motif-3-NVFP4, 314B parâmetros MoE
- Licença MIT
- Receita: recipes/motif-3/vllm/agg-b200-chat/base/deploy.yaml no repositório ai-dynamo/dynamo
- Também roda direto via vLLM: vllm serve Motif-Technologies/Motif-3

```
kubectl apply -f deploy.yaml -n dynamo-system
```

Fonte: <https://github.com/ai-dynamo/dynamo/blob/main/recipes/motif-3/vllm/agg-b200-chat/base/deploy.yaml>

## Instalação e deploy

Todas as receitas usam apiVersion: nvidia.com/v1beta1 e kind: DynamoGraphDeploymentRequest e são otimizadas para GPUs NVIDIA B200.

- Instalação via PyPI: uv pip install --prerelease=allow "ai-dynamo[vllm]"
- Instalação via container NGC: docker run --gpus all --network host --rm -it nvcr.io/nvidia/ai-dynamo/vllm-runtime:1.6.0
- Deploy em Kubernetes: kubectl apply -f <caminho-da-receita>.yaml -n dynamo-system (ex: deploy-generic.yaml ou deploy.yaml)
- Desempenho declarado: até 2x fora da caixa, sem tuning manual pesado

Fonte: <https://github.com/ai-dynamo/dynamo>

## O que as receitas entregam

Quando o modelo já vem com recipe do Dynamo, o time de implantação parte de um ponto conhecido: topologia multi-nó, comunicação entre GPUs e roteamento de requisições já endereçados pelo framework. Isso reduz tentativa e erro nas primeiras semanas em produção.

As receitas são otimizadas para GPUs NVIDIA B200. Se o ambiente usa outra geração, pode ser necessário ajustar os manifests. A estrutura do Dynamo é aberta, então dá para avaliar a integração e adaptar os parâmetros.

- As quatro receitas usam apiVersion: nvidia.com/v1beta1 e kind: DynamoGraphDeploymentRequest.
- Instalação oficial: uv pip install --prerelease=allow "ai-dynamo[vllm]" ou docker run --gpus all --network host --rm -it nvcr.io/nvidia/ai-dynamo/vllm-runtime:1.6.0
- Deploy: kubectl apply -f <caminho-da-receita>.yaml -n dynamo-system
- Checkpoints oficiais no Hugging Face: skt/A.X-K2-NVFP4, LGAI-EXAONE/K-EXAONE-2.0-750B-A37B-NVFP4, upstage/Solar-Open2-250B, Motif-Technologies/Motif-3.
- Otimizadas para GPUs NVIDIA B200 com até 2x de desempenho out-of-the-box, removendo ajuste manual de roteamento e comunicação multi-nó.

Fonte: <https://github.com/ai-dynamo/dynamo>

## Além do vídeo

- A página "Learn more about NVIDIA Dynamo" (produto): https://www.nvidia.com/en-us/ai-data-science/products/dynamo/
- Outras notícias do mesmo anúncio da NVIDIA na Coreia (IA física, ecossistema de IA agêntica, colaboração chips-to-skills, open source para 6G), listadas na página do anúncio.
- "The Best of GTC Berlin" — deep dive on-demand sobre avanços técnicos, citado na página do anúncio.
