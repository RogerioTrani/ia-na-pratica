# Planner do Dynamo corta 80% de breaches de SLA

_2026-11-21 · reportagem_

O NVIDIA Dynamo é a camada de orquestração acima dos motores de inferência SGLang, TensorRT-LLM e vLLM, transformando um cluster de GPUs em um sistema coordenado de inferência. No benchmark Alibaba APSARA 2025, o autoscaling do Planner aparece associado a 80% menos violações de SLA e TCO 5% menor. A apostila explica o que o Dynamo faz, como o Planner usa metas de latência para dimensionar pools, como instalar a plataforma no Kubernetes com o recurso zero-config, e o que conferir antes de depender desses números.

## O contexto

A maioria dos motores de inferência otimiza uma única GPU ou um único nó. O Dynamo fica acima deles e coordena várias GPUs e nós em um sistema único de inferência. Ele não substitui SGLang, TensorRT-LLM ou vLLM; adiciona roteamento, gerenciamento de cache e escalabilidade para servir modelos entre GPUs e nós.

Quando você roda um único modelo em uma única GPU, o motor sozinho provavelmente basta. O Dynamo entra quando há vários modelos ou várias GPUs para coordenar, quando se quer roteamento ciente de cache KV para evitar prefill redundante, quando se quer escalar prefill e decode de forma independente, ou quando se busca scaling automático que cumpra metas de latência com o menor custo total de propriedade.

O projeto é open source, escrito em Rust para desempenho e Python para extensibilidade, e está disponível no repositório oficial github.com/ai-dynamo/dynamo.

Fonte: <https://github.com/ai-dynamo/dynamo>

## Os números do benchmark Alibaba APSARA 2025

No README oficial do projeto, a tabela de resultados-chave lista os ganhos do autoscaling do Planner no contexto da conferência Alibaba APSARA 2025, no minuto 2:50:00 da transmissão. Os dois números são reduções percentuais de indicadores diferentes e não devem ser lidos como a mesma coisa.

A redução de 80% refere-se a violações de SLA. A redução de 5% refere-se ao TCO. O destaque está no cumprimento do SLA; a economia de custo acompanha esse resultado em escala menor.

- 80% menos violações de SLA: redução de falhas no cumprimento do acordo de nível de serviço, no benchmark Alibaba APSARA 2025.
- 5% menor TCO: redução no custo total de propriedade associado ao mesmo autoscaling.
- Contexto: Alibaba APSARA 2025, minuto 2:50:00 da transmissão, citado na tabela Key Results do repositório oficial do Dynamo.

Fonte: <https://github.com/ai-dynamo/dynamo>

## O que o Dynamo faz, em capacidades

O Dynamo organiza um conjunto de capacidades que trabalham juntas para maximizar throughput e minimizar latência em cargas de LLM, raciocínio, multimodal e geração de vídeo.

Prefill e decode separados em pools de GPU independentes permitem que cada fase rode em hardware ajustado ao seu trabalho. O roteamento ciente de cache KV encaminha requisições com base na carga do worker e na sobreposição de cache KV, eliminando prefill redundante. O KV Block Manager descarrega cache KV entre GPU, CPU, SSD e armazenamento remoto, estendendo o contexto efetivo além da memória da GPU. O ModelExpress transmite pesos de modelo GPU a GPU via NIXL/NVLink, com cold-start mais rápido para novas réplicas. O Planner é o autoscaler guiado por SLA que caracteriza workloads e dimensiona pools buscando atender metas de latência com menor TCO. O Grove é o operador Kubernetes para agendamento em gang com consciência de topologia. O AISimulate prevê comportamento de serving e busca configurações de deploy offline.

- Disaggregated Prefill/Decode: pools independentes de GPU para prefill e decode.
- KV-Aware Routing: roteamento por carga do worker e sobreposição de cache KV.
- KV Block Manager (KVBM): offload de cache KV entre GPU, CPU, SSD e armazenamento remoto.
- ModelExpress: streaming de pesos GPU a GPU via NIXL/NVLink.
- Planner: autoscaler guiado por SLA.
- Grove: operador Kubernetes para agendamento em gang com consciência de topologia.
- AISimulate: previsão de serving e busca de configurações offline.
- Fault Tolerance: health checks canário e migração de requisições em voo.

Fonte: <https://github.com/ai-dynamo/dynamo>

## Os motores de inferência suportados

O Dynamo opera sobre três motores de inferência. Ele coordena a inferência entre múltiplos nós, adicionando roteamento, gerenciamento de cache e escalabilidade ao conjunto. Os endereços oficiais de cada motor estão listados abaixo.

A matriz de suporte de features mostra que disaggregated serving, roteamento ciente de KV e o Planner baseado em SLA estão disponíveis nos três motores. O KVBM está em desenvolvimento para SGLang e disponível para TensorRT-LLM e vLLM. Multimodal, tool calling e outros recursos também constam na matriz completa.

- SGLang: repositório github.com/sgl-project/sglang.
- TensorRT-LLM: repositório github.com/NVIDIA/TensorRT-LLM.
- vLLM: repositório github.com/vllm-project/vllm, site vllm.ai.

Fonte: <https://github.com/vllm-project/vllm>

## Como o Planner age

Separar prefill e decode permite dimensionar essas fases de forma independente. O Planner caracteriza a carga de trabalho e ajusta os pools buscando atender às metas de latência com menor TCO.

A meta declarada orienta o dimensionamento. Para quem depende de latência rígida, cumprir esse contrato é o teste decisivo. Declarar uma meta não equivale a garanti-la: se o plano automático falhar, a aplicação continua dependendo daquele prazo de resposta.

Fonte: <https://github.com/ai-dynamo/dynamo>

## TTFT e ITL: as duas metas de latência

TTFT mede a espera pelo primeiro token. ITL mede o intervalo entre tokens. São duas exigências de latência distintas que entram explicitamente na configuração apresentada no exemplo de implantação.

No exemplo, as metas declaradas são TTFT de 200 ms e ITL de 20 ms. Esses valores aparecem no arquivo de manifesto como parâmetros do SLA, e a automação assume a estimativa das configurações e a otimização da topologia a partir deles.

- TTFT: time to first token, tempo até o primeiro token.
- ITL: inter-token latency, intervalo entre tokens.
- Metas do exemplo: TTFT 200,0 ms e ITL 20,0 ms.

Fonte: <https://github.com/ai-dynamo/dynamo>

## Zero-config deploy: o que é o DGDR

O zero-config deploy é um recurso beta. Você informa modelo, hardware e SLA em um único YAML, e o AISimulate estima configurações, o Planner otimiza a topologia e o Dynamo implanta. Isso reduz o trabalho manual de escolher configurações de serving.

Ainda assim, declarar o que será servido e qual latência se espera é obrigatório. A automação não elimina a necessidade de declarar a meta; ela assume a partir dela a estimativa de configurações e a otimização da topologia.

Fonte: <https://github.com/ai-dynamo/dynamo>

## Exemplo completo: instalar e implantar no Kubernetes

O fluxo abaixo instala a plataforma Dynamo no cluster e implanta um modelo com o recurso zero-config. O primeiro bloco define o namespace e a versão e instala a plataforma com Helm.

```
export NAMESPACE=dynamo-system
export DYNAMO_VERSION=1.6.1
helm upgrade --install dynamo-platform \
  "https://helm.ngc.nvidia.com/nvidia/ai-dynamo/charts/dynamo-platform-${DYNAMO_VERSION}.tgz" \
  --namespace "$NAMESPACE" --create-namespace --wait --timeout=10m
```

Fonte: <https://docs.nvidia.com/dynamo/kubernetes/getting-started/quickstart>

## Exemplo completo: instalar e implantar no Kubernetes (continuação)

Salve o conteúdo abaixo como dgdr.yaml. Ele descreve o modelo, o backend e as duas metas de latência, em milissegundos. Com autoApply true, o Dynamo aplica a configuração escolhida.

```
apiVersion: nvidia.com/v1beta1
kind: DynamoGraphDeploymentRequest
metadata:
  name: my-model
spec:
  model: Qwen/Qwen3-0.6B
  backend: vllm
  sla:
    ttft: 200.0
    itl: 20.0
  autoApply: true
```

Fonte: <https://github.com/ai-dynamo/dynamo/blob/main/README.md>

## Exemplo completo: aplicar e acompanhar

O primeiro comando aplica o arquivo no cluster. O segundo acompanha o pedido, que passa pelos estágios Pending, Profiling, Ready, Deploying e Deployed durante a reconciliação.

```
kubectl apply -f dgdr.yaml -n dynamo-system
kubectl get dgdr -n dynamo-system -w
```

Fonte: <https://docs.nvidia.com/dynamo/kubernetes/getting-started/quickstart>

## Testar sem Kubernetes: contêiner ou PyPI

Para experimentar o Dynamo com vLLM em um contêiner pronto, use o comando abaixo; há também as imagens sglang-runtime e tensorrtllm-runtime, na mesma versão 1.6.0. Dentro do contêiner, você inicia o frontend e o worker antes de enviar requisições. Outra opção é instalar pelo PyPI com uv pip install --prerelease=allow "ai-dynamo[vllm]" (ou "ai-dynamo[sglang]"). Para TensorRT-LLM, a instalação usa pip com --extra-index-url https://pypi.nvidia.com.

```
docker run --gpus all --network host --rm -it nvcr.io/nvidia/ai-dynamo/vllm-runtime:1.6.0
```

Fonte: <https://github.com/ai-dynamo/dynamo>

## Topologias de roteamento de requisições

O Dynamo pode expor tráfego por duas topologias Kubernetes. Ambas expõem uma API compatível com OpenAI e suportam os mesmos backends, serving disagregado e roteamento ciente de KV.

Na topologia Dynamo-native, o Frontend do Dynamo serve HTTP e o Router integrado decide a seleção de workers, sem gateway externo. É indicada para desenvolvimento local, implantações em cluster único e ambientes onde o Dynamo deve controlar a entrada de requisições de ponta a ponta. Na topologia Gateway API, um gateway Kubernetes chama o plugin Endpoint Picker do Dynamo antes de encaminhar para o sidecar do Frontend no modo router direct. É indicada para plataformas que padronizam Gateway API, ou onde políticas de gateway, autenticação, rate limiting e observabilidade devem ficar na borda do cluster.

O fluxo da rota Dynamo-native é client, Frontend, Router, workers. O fluxo da rota Gateway API é client, Gateway, EPP, sidecar do Frontend em modo direct, workers.

Fonte: <https://github.com/ai-dynamo/dynamo>

## Quando usar Dynamo

Use o Dynamo quando estiver servindo LLMs em várias GPUs ou nós e precisar coordená-los, quando quiser roteamento ciente de KV para evitar prefill redundante, quando precisar escalar prefill e decode de forma independente, quando quiser scaling automático que cumpra metas de latência com o menor TCO, ou quando precisar de cold-starts rápidos ao subir novas réplicas.

Se você roda um único modelo em uma única GPU, o motor de inferência sozinho provavelmente é suficiente.

Fonte: <https://github.com/ai-dynamo/dynamo>

## Como funciona na prática

Imagine que você serve um modelo com vLLM em vários nós e precisa manter uma latência rígida. Com o Dynamo, você declara o modelo, o backend e as metas de TTFT e ITL em um único arquivo YAML. O AISimulate estima configurações candidatas sem subir um cluster de GPU, o Planner otimiza a topologia, e o Dynamo implanta. O roteamento ciente de KV evita prefill redundante, e o autoscaling do Planner ajusta os pools de prefill e decode de forma independente quando a carga muda.

Exemplo: com metas de TTFT 200 ms e ITL 20 ms, o sistema busca atender esses prazos com o menor TCO, em vez de provisionar capacidade fixa para o pico.

Fonte: <https://github.com/ai-dynamo/dynamo>

## Linha do tempo

A linha do tempo abaixo reúne as datas e versões citadas na documentação oficial do projeto.

- Dynamo 1.0: lançamento anunciado em 15/03, descrito como pronto para produção com forte adoção pela comunidade.
- Versão de container citada no quick start: 1.6.0, nas imagens vllm-runtime, sglang-runtime e tensorrtllm-runtime.
- Versão da plataforma no exemplo de instalação: 1.6.1, via chart Helm do NGC.
- Alibaba Cloud Apsara Conference 2025: realizada de 24 a 26 de setembro de 2025 em Hangzhou, onde foi citado o resultado de 80% menos violações de SLA.
- Novidades da versão 1.0: zero-config deploy (beta), agentic inference, multimodal E/P/D, geração de vídeo, plugin do K8s Inference Gateway e offload de KV para S3/Azure blob.

Fonte: <https://github.com/ai-dynamo/dynamo>

## Quem ganha e quem perde

Quem ganha: equipes que servem LLMs em vários GPUs ou nós e precisam cumprir metas de latência com menor custo, além de quem quer evitar prefill redundante e cold-starts lentos. O roteamento ciente de KV e o ModelExpress atacam diretamente esses pontos.

Quem perde ou não se beneficia: quem roda um único modelo em uma única GPU, para quem o motor de inferência sozinho provavelmente basta. Também perde quem depende de uma garantia rígida de SLA sem validação própria, já que os números vêm de um benchmark específico e não de medição independente.

Fonte: <https://github.com/ai-dynamo/dynamo>

## O que ainda não se sabe

Os números de 80% menos violações de SLA e 5% menor TCO vêm do benchmark Alibaba APSARA 2025, citado no repositório oficial do Dynamo. Eles não trazem validação independente nem medição em outras cargas. Trate-os como resultados daquele cenário, não como garantia universal.

O recurso zero-config deploy está em beta. Ainda exige declarar modelo, hardware e SLA; a automação estima e otimiza, mas não remove a responsabilidade de definir a meta.

Declarar uma meta de latência não equivale a garanti-la. Se o plano automático falhar, a aplicação continua dependendo daquele prazo de resposta.

A sessão do Alibaba APSARA 2025 citada no README está em yunqi.aliyun.com/2025/session?agendaId=6062, e 2:50:00 é o ponto da transmissão indicado na tabela de resultados. A página oficial do evento é a indicada na fonte desta seção.

- Confira se o cenário do benchmark se aproxima da sua carga antes de depender dos números.
- Valide o SLA em produção, não apenas na estimativa offline.
- Considere que o zero-config está em beta e pode mudar.
- Não trate a meta declarada como garantia automática.

Fonte: <https://www.alibabacloud.com/en/apsara-conference/index?_p_lc=1>

## O que você pode fazer

Os passos abaixo seguem o fluxo oficial do quick start Kubernetes. Execute-os em ordem e confira cada resultado antes de avançar.

1. instale a plataforma Dynamo via Helm no namespace dynamo-system, com a versão 1.6.1, usando o chart oficial do NGC. Resultado esperado: CRDs e o Dynamo Operator instalados no namespace.
2. crie o arquivo dgdr.yaml com o modelo, o backend e as metas de SLA, e aplique-o no cluster com kubectl apply. Resultado esperado: o recurso DynamoGraphDeploymentRequest criado.
3. acompanhe a reconciliação com kubectl get dgdr até o estágio Deployed. Resultado esperado: o recurso passa por Pending, Profiling, Ready, Deploying e Deployed.
4. envie uma requisição ao endpoint compatível com OpenAI exposto pelo Frontend e confira a resposta. Resultado esperado: resposta válida do modelo servido.
5. se precisar de roteamento ciente de KV, ative os eventos de cache conforme a documentação; caso contrário, use roteamento baseado em previsão.

Fonte: <https://docs.nvidia.com/dynamo/kubernetes/getting-started/quickstart>

## Glossário

- Dynamo: camada de orquestração acima dos motores de inferência, que coordena GPUs e nós.
- Planner: autoscaler guiado por SLA que caracteriza workloads e dimensiona pools.
- TTFT: time to first token, tempo de espera pelo primeiro token.
- ITL: inter-token latency, intervalo entre tokens.
- SLA: acordo de nível de serviço, aqui expresso por metas de latência.
- TCO: custo total de propriedade.
- Prefill: fase de processamento inicial da entrada.
- Decode: fase de geração dos tokens de saída.
- KV cache: cache de chaves e valores usado na inferência.
- DGDR: DynamoGraphDeploymentRequest, recurso Kubernetes para deploy zero-config.
- AISimulate: componente que estima configurações de serving offline.
- Grove: operador Kubernetes para agendamento em gang com consciência de topologia.
- ModelExpress: streaming de pesos de modelo GPU a GPU via NIXL/NVLink.
- KVBM: KV Block Manager, gerenciador de cache KV com offload entre camadas.
- GAIE: Gateway API Inference Extension, topologia de roteamento alternativa.

## Para onde ir depois

Os próximos passos sugeridos pela documentação oficial do projeto.

- Consulte o repositório oficial github.com/ai-dynamo/dynamo para a documentação completa, recipes e exemplos.
- Leia o quickstart Kubernetes em docs.nvidia.com/dynamo/kubernetes/getting-started/quickstart.
- Acompanhe o walkthrough do DGDR em docs.nvidia.com/dynamo/kubernetes/auto-deployment/dgdr-walkthrough.
- Explore os recipes de modelos pré-construídos, como Qwen3-32B-FP8 com TensorRT-LLM e DeepSeek-R1 com SGLang.
- Consulte a documentação de SLA-Driven Deployments para otimizar implantações segundo metas de SLA.
- Use o AIPerf para comparar topologias de deploy.
- Junte-se à comunidade via Slack e reuniões semanais citadas no repositório.

Fonte: <https://github.com/ai-dynamo/dynamo>

## Links citados

- https://github.com/ai-dynamo/dynamo/blob/main/README.md
- https://yunqi.aliyun.com/2025/session?agendaId=6062

## Além do vídeo

- O Dynamo é escrito em Rust para desempenho e Python para extensibilidade.
- A matriz completa de features inclui LoRA, migração de requisições, speculative decoding e interações de features.
- O ModelExpress oferece cold-start 7x mais rápido para novas réplicas via streaming de pesos GPU a GPU.
- O KV-aware routing oferece 2x mais rápido time to first token no benchmark citado para Qwen3-Coder 480B.
- O multimodal E/P/D oferece 30% mais rápido TTFT em cargas de imagem.
- A geração de vídeo tem suporte nativo a FastVideo e SGLang Diffusion.
- O serving disagregado suporta encode, prefill e decode separados com cache de embedding.
- O Grove é o operador Kubernetes para agendamento em gang com consciência de topologia em NVL72.
- A descoberta de serviço pode usar etcd ou NATS JetStream em deployments Slurm ou distribuídos.
- A documentação inclui guias específicos para AWS EKS, Google GKE, Azure AKS e Amazon ECS.
- O projeto mantém benchmarking com AIPerf e documentação de SLA-Driven Deployments.
- A comunidade tem SIGs, office hours e reuniões semanais listadas no repositório.
