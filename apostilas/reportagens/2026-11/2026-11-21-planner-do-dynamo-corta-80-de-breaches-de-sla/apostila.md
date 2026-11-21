# Planner do Dynamo corta 80% de breaches de SLA

_2026-11-21 · reportagem_

O Planner do Dynamo é um autoscaler guiado por metas de latência. No benchmark Alibaba APSARA 2025, citado no repositório oficial, ele registrou 80% menos violações de SLA com TCO 5% menor. Esta apostila traz o resultado, as metas de latência, os motores que o Dynamo coordena e os comandos do recurso beta de implantação zero-config, na ordem de execução.

## O resultado do benchmark

No benchmark Alibaba APSARA 2025, o autoscaling do Planner aparece associado a 80% menos violações de SLA e a um TCO 5% menor. O ganho maior está no cumprimento do SLA, e a economia de custo acompanha esse resultado em escala menor.

Os números vêm do benchmark apresentado no repositório oficial do Dynamo. Eles valem para aquele contexto.

- Violações de SLA: redução de 80%
- TCO: redução de 5%

Fonte: <https://github.com/ai-dynamo/dynamo>

## A latência como entrada do sistema

O exemplo de implantação define duas metas de SLA. TTFT mede a espera pelo primeiro token. ITL mede o intervalo entre tokens. As duas entram explicitamente na configuração.

- TTFT: 200 ms
- ITL: 20 ms

Fonte: <https://github.com/ai-dynamo/dynamo>

## Quem executa a inferência

O Dynamo não substitui os motores de inferência. Ele é a camada de orquestração sobre eles e coordena a inferência entre múltiplos nós, com roteamento, gerenciamento de cache e escalabilidade para servir modelos entre GPUs e nós.

- SGLang: github.com/sgl-project/sglang
- TensorRT-LLM: github.com/NVIDIA/TensorRT-LLM
- vLLM: github.com/vllm-project/vllm (site vllm.ai)

Fonte: <https://github.com/vllm-project/vllm>

## O que o Planner faz

O Planner caracteriza a carga de trabalho e dimensiona os pools de GPUs. Prefill e decode podem escalar de forma independente, e o Planner ajusta cada pool para atender às metas com o menor TCO.

Fonte: <https://github.com/ai-dynamo/dynamo>

## Zero-config (beta): o que você declara

No recurso beta, você informa modelo, hardware e SLA em um YAML. Os modelos de desempenho do AISimulate estimam as configurações candidatas, o Planner otimiza a topologia e o Dynamo implanta.

Os três passos a seguir levam do cluster ao pedido de implantação acompanhado.

Fonte: <https://docs.nvidia.com/dynamo/kubernetes/getting-started/quickstart>

## Passo 1: instalar a plataforma Dynamo

Defina o namespace e a versão. O helm usa as duas variáveis.

Fonte: <https://docs.nvidia.com/dynamo/kubernetes/getting-started/quickstart>

## Passo 2: descrever o pedido e aplicar

Salve o conteúdo abaixo como dgdr.yaml. Ele declara o modelo, o backend e as duas metas de latência, em milissegundos. Com autoApply true, o Dynamo aplica a configuração escolhida.

Depois aplique o arquivo no cluster.

Fonte: <https://github.com/ai-dynamo/dynamo/blob/main/README.md>

## Passo 3: acompanhar o pedido

Acompanhe o pedido até ele ficar implantado. O passo a passo completo do DGDR está em docs.nvidia.com/dynamo/kubernetes/auto-deployment/dgdr-walkthrough.

Declarar uma meta não equivale a garanti-la. Para quem depende de latência rígida, cumprir o contrato de TTFT e ITL é o teste decisivo da automação.

```
kubectl get dgdr -n dynamo-system -w
```

Fonte: <https://docs.nvidia.com/dynamo/kubernetes/getting-started/quickstart>

## Além do vídeo

- Contêiner pronto para testar o Dynamo com vLLM: docker run --gpus all --network host --rm -it nvcr.io/nvidia/ai-dynamo/vllm-runtime:1.6.0
- Instalação pelo PyPI: uv pip install --prerelease=allow "ai-dynamo[vllm]" (há também a opção "ai-dynamo[sglang]").
- Dois modos de roteamento no Kubernetes: Frontend nativo do Dynamo ou Gateway API com GAIE. Ambos expõem API compatível com OpenAI.
- Outros resultados do README: 7x mais throughput por GPU no DeepSeek R1 em GB200 NVL72 e 2x mais rápido no primeiro token com roteamento consciente de KV.
- A sessão do Alibaba Apsara 2025 citada no README está em https://yunqi.aliyun.com/2025/session?agendaId=6062
