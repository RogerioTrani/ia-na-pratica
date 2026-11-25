# 4 modelos coreanos ganham receitas de implantação no Dynamo

_2026-11-16 · noticia_

NVIDIA publicou em 9 de novembro de 2026 receitas de implantação no Dynamo para quatro modelos abertos coreanos: A.X K2, K-EXAONE 2.0, Solar Open 2 e Motif-3. Cada receita traz checkpoint oficial no Hugging Face, manifest YAML e comando de deploy via kubectl para GPUs B200. Os comandos e as fontes oficiais estão nesta apostila.

## O fato

Em 9 de novembro de 2026, a NVIDIA publicou receitas de implantação otimizadas no Dynamo para quatro modelos abertos coreanos: A.X K2 (SK Telecom), K-EXAONE 2.0 (LG AI Research), Solar Open 2 (Upstage) e Motif-3 (Motif Technologies).

As receitas ficam no repositório ai-dynamo/dynamo, em manifests YAML com apiVersion nvidia.com/v1beta1 e kind DynamoGraphDeploymentRequest. O NVIDIA Dynamo é um framework open source de serving de inferência distribuído feito para escala de data center. O código está aberto em https://github.com/ai-dynamo/dynamo para inspeção e adaptação.

Fonte: <https://blogs.nvidia.com/blog/nvidia-dynamo-korea-open-models/>

## A.X K2 (SK Telecom)

Checkpoint oficial: https://huggingface.co/skt/A.X-K2-NVFP4

- 688B parâmetros totais, 33B ativos.
- Licença Apache 2.0.
- Receita: recipes/ax-k2/vllm/agg-b200-chat/deploy-generic.yaml (e disagg-b200-chat/deploy-generic.yaml) no repositório ai-dynamo/dynamo.

```
kubectl apply -f deploy-generic.yaml -n dynamo-system
```

Fonte: <https://github.com/ai-dynamo/dynamo/blob/main/recipes/ax-k2/vllm/agg-b200-chat/deploy-generic.yaml>

## K-EXAONE 2.0 (LG AI Research)

Checkpoint oficial: https://huggingface.co/LGAI-EXAONE/K-EXAONE-2.0-750B-A37B-NVFP4

- Licença Apache 2.0.
- Otimizado para B200 com até 2x de desempenho fora da caixa.
- Receita: recipes/k-exaone-2.0/vllm/agg-b200-chat/deploy-generic.yaml no repositório ai-dynamo/dynamo.

```
kubectl apply -f deploy-generic.yaml -n dynamo-system
```

Fonte: <https://github.com/ai-dynamo/dynamo/blob/main/recipes/k-exaone-2.0/vllm/agg-b200-chat/deploy-generic.yaml>

## Solar Open 2 (Upstage)

Checkpoint oficial: https://huggingface.co/upstage/Solar-Open2-250B

- 250B parâmetros totais, 15B ativos.
- Contexto de 1M tokens.
- Licença Upstage Solar License.
- Receita: recipes/solar-open2-250b/vllm/agg-b200-chat/deploy.yaml (e disagg-b200-chat/deploy.yaml) no repositório ai-dynamo/dynamo.

```
kubectl apply -f deploy.yaml -n dynamo-system
```

Fonte: <https://github.com/ai-dynamo/dynamo/blob/main/recipes/solar-open2-250b/vllm/agg-b200-chat/deploy.yaml>

## Motif-3 (Motif Technologies)

Checkpoint oficial: https://huggingface.co/Motif-Technologies/Motif-3

- Variante Motif-3-NVFP4, 314B parâmetros MoE.
- Licença MIT.
- Receita: recipes/motif-3/vllm/agg-b200-chat/base/deploy.yaml no repositório ai-dynamo/dynamo.
- Também roda direto via vLLM: vllm serve Motif-Technologies/Motif-3

```
kubectl apply -f deploy.yaml -n dynamo-system
```

Fonte: <https://github.com/ai-dynamo/dynamo/blob/main/recipes/motif-3/vllm/agg-b200-chat/base/deploy.yaml>

## O que fazer hoje

Todas as receitas usam apiVersion: nvidia.com/v1beta1 e kind: DynamoGraphDeploymentRequest e são otimizadas para GPUs NVIDIA B200.

1. instale o Dynamo com uv pip install --prerelease=allow "ai-dynamo[vllm]", ou com docker run --gpus all --network host --rm -it nvcr.io/nvidia/ai-dynamo/vllm-runtime:1.6.0. Resultado: o framework fica disponível no ambiente.
2. aplique a receita do modelo com kubectl apply -f <caminho-da-receita>.yaml -n dynamo-system (ex: deploy-generic.yaml ou deploy.yaml). Resultado: o modelo parte de uma topologia multi-nó e de um roteamento já endereçados pelo framework.
3. Fonte dos comandos e do repositório: https://github.com/ai-dynamo/dynamo

Fonte: <https://github.com/ai-dynamo/dynamo>

## O que conferir

Fato: as receitas são otimizadas para GPUs NVIDIA B200. Se o ambiente usa outra geração, pode ser necessário ajustar os manifests.

Desempenho declarado: até 2x fora da caixa, sem tuning manual pesado. A página do produto: https://www.nvidia.com/en-us/ai-data-science/products/dynamo/

Fonte: <https://www.nvidia.com/en-us/ai-data-science/products/dynamo/>
