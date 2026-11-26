# 4 modelos coreanos ganham receitas de implantação no Dynamo

_2026-11-16 · noticia_

A NVIDIA anunciou em 9 de novembro de 2026 receitas de implantação otimizadas para quatro modelos abertos coreanos no Dynamo: A.X K2, K-EXAONE 2.0, Solar Open 2 e Motif-3. As receitas reúnem checkpoints oficiais no Hugging Face e manifestos YAML para GPUs NVIDIA B200, com roteamento e comunicação multi-nó tratados pelo framework. Você vai entender por que modelos grandes precisam de distribuição entre GPUs e como cada receita muda o caminho até a produção. Também vai aprender a escolher o checkpoint e o manifesto corretos, instalar o Dynamo e aplicar a configuração no Kubernetes. Ao final, você terá um roteiro para começar com segurança, medir o próprio cenário e evitar confusões entre licença, variante do checkpoint e topologia de implantação.

## O fato

Em 9 de novembro de 2026, a NVIDIA anunciou receitas de implantação otimizadas para A.X K2, da SK Telecom; K-EXAONE 2.0, da LG AI Research; Solar Open 2, da Upstage; e Motif-3, da Motif Technologies. Cada receita combina um checkpoint público no Hugging Face com um manifesto YAML no repositório ai-dynamo/dynamo. O alvo declarado é a produção em ambientes multi-nó, com GPUs NVIDIA B200.

O anúncio reúne configurações validadas para o NVIDIA Dynamo, um framework open source de serving de inferência distribuído. O recurso Kubernetes usado nas receitas é DynamoGraphDeploymentRequest, com apiVersion nvidia.com/v1beta1. Para a equipe de implantação, a receita é um ponto de partida conhecido: ela já relaciona o modelo, o arquivo de configuração e a forma de solicitar a implantação.

Fonte: <https://blogs.nvidia.com/blog/nvidia-dynamo-korea-open-models/>

## Por que isso importa

Quando um modelo passa da capacidade de uma única GPU, seus pesos precisam ser divididos entre várias GPUs. A partir daí, cada requisição depende de coordenação. Alguém precisa decidir para onde enviar o pedido, manter os trabalhadores sincronizados e administrar a troca de informações entre eles. Se essa organização falha, o modelo até pode estar disponível, mas o desempenho sofre.

O Dynamo existe para coordenar roteamento de requisições e comunicação em ambientes distribuídos. As receitas levam essa coordenação para configurações específicas de modelos e hardware. O ganho prático é começar com uma topologia multi-nó já endereçada pelo framework, reduzindo as variáveis que a equipe precisaria descobrir sozinha no início da operação.

Fonte: <https://blogs.nvidia.com/blog/nvidia-dynamo-korea-open-models/>

## Como o Dynamo organiza a inferência

Inferência é o momento em que o modelo recebe uma entrada e produz uma resposta. O serving de inferência é a camada que recebe essas requisições, encaminha o trabalho e devolve o resultado. Em uma implantação distribuída, esse fluxo atravessa várias GPUs e pode atravessar várias máquinas. Cada máquina participante é um nó.

O roteamento determina qual trabalhador receberá cada requisição. A comunicação permite que as partes do modelo troquem os dados necessários durante o processamento. O Dynamo gerencia esses dois pontos de coordenação para serving em escala de data center. No Kubernetes, o manifesto declara a implantação por meio de apiVersion nvidia.com/v1beta1 e kind DynamoGraphDeploymentRequest.

Os caminhos das receitas também distinguem configurações agg e disagg. Esses nomes indicam organizações de implantação diferentes. Antes de aplicar um arquivo, o leitor deve identificar qual delas corresponde ao arranjo que pretende operar. Copiar o nome do checkpoint não substitui essa escolha.

Fonte: <https://github.com/ai-dynamo/dynamo>

## A.X K2, da SK Telecom

O checkpoint oficial é skt/A.X-K2-NVFP4, disponível em https://huggingface.co/skt/A.X-K2-NVFP4. O modelo é registrado com 688 bilhões de parâmetros totais e 33 bilhões de parâmetros ativos, com licença Apache 2.0. O total descreve o porte do modelo; os parâmetros ativos ajudam a entender quanta parte é acionada durante o processamento.

A receita agregada está em recipes/ax-k2/vllm/agg-b200-chat/deploy-generic.yaml. Há também uma versão desagregada em recipes/ax-k2/vllm/disagg-b200-chat/deploy-generic.yaml. As duas pertencem ao repositório ai-dynamo/dynamo e usam a variante NVFP4 indicada para a configuração B200.

Para implantar pelo Kubernetes, execute o comando no diretório do manifesto escolhido. O resultado esperado é que o cluster receba a solicitação de criação da implantação no namespace dynamo-system. Depois disso, o próximo trabalho é testar o serviço com requisições reais.

```
kubectl apply -f deploy-generic.yaml -n dynamo-system
```

Fonte: <https://github.com/ai-dynamo/dynamo/blob/main/recipes/ax-k2/vllm/agg-b200-chat/deploy-generic.yaml>

## K-EXAONE 2.0, da LG AI Research

O checkpoint oficial é LGAI-EXAONE/K-EXAONE-2.0-750B-A37B-NVFP4, em https://huggingface.co/LGAI-EXAONE/K-EXAONE-2.0-750B-A37B-NVFP4. A licença registrada é Apache 2.0. O identificador completo deve ser preservado na configuração para manter a variante NVFP4 usada pela receita.

A receita fica em recipes/k-exaone-2.0/vllm/agg-b200-chat/deploy-generic.yaml. A NVIDIA a descreve como otimizada para GPUs B200, com até 2x de desempenho fora da caixa. O valor é uma referência para a configuração anunciada e deve ser avaliado no ambiente de destino.

O comando de implantação usa deploy-generic.yaml e o namespace dynamo-system. Depois da aplicação, verifique se o serviço responde e se o modelo carregado corresponde ao checkpoint indicado. Isso evita concluir o deploy com uma variante diferente da receita.

```
kubectl apply -f deploy-generic.yaml -n dynamo-system
```

Fonte: <https://github.com/ai-dynamo/dynamo/blob/main/recipes/k-exaone-2.0/vllm/agg-b200-chat/deploy-generic.yaml>

## Solar Open 2, da Upstage

O checkpoint oficial é upstage/Solar-Open2-250B, em https://huggingface.co/upstage/Solar-Open2-250B. A ficha registra 250 bilhões de parâmetros totais, 15 bilhões de parâmetros ativos e contexto de 1 milhão de tokens. A licença é Upstage Solar License.

A janela de contexto indica quantos tokens o modelo pode considerar em uma entrada. Um número maior amplia a quantidade de informação que cabe em uma mesma requisição, mas o custo de processamento e a utilidade prática continuam dependendo da carga. Por isso, o contexto declarado deve ser avaliado junto com a arquitetura de serving.

A receita agregada está em recipes/solar-open2-250b/vllm/agg-b200-chat/deploy.yaml. A versão desagregada fica em recipes/solar-open2-250b/vllm/disagg-b200-chat/deploy.yaml. No diretório do arquivo escolhido, aplique o manifesto e confirme a criação da implantação no namespace dynamo-system.

```
kubectl apply -f deploy.yaml -n dynamo-system
```

Fonte: <https://github.com/ai-dynamo/dynamo/blob/main/recipes/solar-open2-250b/vllm/agg-b200-chat/deploy.yaml>

## Motif-3, da Motif Technologies

O checkpoint oficial é Motif-Technologies/Motif-3, em https://huggingface.co/Motif-Technologies/Motif-3. A receita usa a variante Motif-3-NVFP4. O modelo é descrito com 314 bilhões de parâmetros em arquitetura MoE e licença MIT.

MoE significa mixture of experts, uma arquitetura com vários especialistas. Em cada processamento, apenas parte desses especialistas participa. Essa estrutura ajuda a explicar a diferença entre o porte total de um modelo e a quantidade de parâmetros efetivamente ativa, sem reduzir a importância da comunicação entre as partes distribuídas.

A receita do Dynamo está em recipes/motif-3/vllm/agg-b200-chat/base/deploy.yaml. O deploy no Kubernetes usa deploy.yaml no namespace dynamo-system. O vLLM também pode ser executado diretamente, em um caminho separado da receita Kubernetes.

```
vllm serve Motif-Technologies/Motif-3
```

Fonte: <https://github.com/ai-dynamo/dynamo/blob/main/recipes/motif-3/vllm/agg-b200-chat/base/deploy.yaml>

## Os números

Os números descrevem coisas diferentes. Parâmetros totais indicam o porte do modelo. Parâmetros ativos indicam a parte acionada no processamento. Contexto mede a quantidade de tokens considerada em uma entrada. A versão do container identifica a imagem usada para executar o runtime.

Esses valores ajudam a dimensionar a avaliação, mas não medem, por si só, a qualidade da resposta nem o desempenho da implantação. A leitura correta é combinar cada número com o modelo, a variante e o recurso ao qual ele se refere.

- 688 bilhões de parâmetros totais e 33 bilhões ativos: porte declarado do checkpoint skt/A.X-K2-NVFP4. O total e a parte ativa descrevem aspectos diferentes do modelo.
- 250 bilhões de parâmetros totais e 15 bilhões ativos: porte declarado do checkpoint upstage/Solar-Open2-250B.
- 1 milhão de tokens: janela de contexto declarada para Solar Open 2. O valor não representa, sozinho, uma medida de velocidade.
- 314 bilhões de parâmetros MoE: porte declarado de Motif-3. O número está associado à arquitetura MoE da variante apresentada.
- 1.6.0: versão do container NGC nvcr.io/nvidia/ai-dynamo/vllm-runtime:1.6.0 registrada nas opções oficiais de instalação.

Fonte: <https://github.com/ai-dynamo/dynamo>

## O desempenho declarado

O anúncio atribui às receitas otimizadas para GPUs NVIDIA B200 até 2x de desempenho fora da caixa. A expressão fora da caixa indica que a configuração já parte de um ponto ajustado para esse hardware, reduzindo o trabalho inicial de roteamento e comunicação multi-nó.

Trate o valor como um teto declarado para a configuração anunciada. Ele não garante o dobro em qualquer carga e não serve para ranquear os quatro modelos entre si. A equipe precisa medir latência, capacidade de atendimento e comportamento sob a própria carga antes de usar o número em uma decisão de produção.

- B200: geração de GPU para a qual as receitas foram otimizadas. Em outra geração, os manifestos podem precisar de adaptação.
- Até 2x: desempenho máximo declarado fora da caixa para a configuração B200. O valor não estabelece uma garantia para todo ambiente.

Fonte: <https://blogs.nvidia.com/blog/nvidia-dynamo-korea-open-models/>

## O que muda para você

Antes das receitas, a equipe precisava traduzir o tamanho do modelo em uma topologia, definir o roteamento e ajustar a comunicação entre os nós. Com a receita, o trabalho começa em uma configuração já preparada para o Dynamo e para a GPU B200. A equipe ainda responde pela avaliação do modelo, pelos testes e pelas adaptações necessárias.

Imagine que uma equipe avalia Solar Open 2 para atender documentos longos. Ela começa pelo checkpoint upstage/Solar-Open2-250B, verifica a licença Upstage Solar License e escolhe entre a receita agregada e a desagregada. Depois de aplicar o manifesto, envia entradas representativas do próprio uso e observa respostas, latência e consumo dos recursos. Se o cluster usa outra geração de GPU, a equipe adapta os parâmetros antes de repetir os testes.

Nesse fluxo, a receita reduz a incerteza inicial. Ela não substitui a revisão humana sobre qualidade, carga e requisitos do serviço.

Fonte: <https://github.com/ai-dynamo/dynamo>

## Instalação via PyPI

A instalação via PyPI é uma das opções oficiais para o Dynamo. O extra vllm corresponde ao runtime usado pelas receitas deste anúncio. A opção --prerelease=allow permite considerar versões pré-lançamento durante a instalação.

Esse comando instala o pacote no ambiente Python. Ele não aplica o manifesto Kubernetes nem inicia o modelo sozinho. Depois da instalação, a equipe precisa escolher a receita, revisar o YAML e executar o deploy.

```
uv pip install --prerelease=allow "ai-dynamo[vllm]"
```

Fonte: <https://github.com/ai-dynamo/dynamo>

## Instalação via container NGC

A segunda opção oficial é o container NGC nvcr.io/nvidia/ai-dynamo/vllm-runtime:1.6.0. A imagem reúne o runtime vLLM na versão indicada. O comando expõe as GPUs com --gpus all, usa a rede do host com --network host e abre um terminal interativo.

O container é uma alternativa de execução à instalação via PyPI. Para usar as receitas Kubernetes, o passo de implantação continua sendo a aplicação do manifesto DynamoGraphDeploymentRequest no cluster.

```
docker run --gpus all --network host --rm -it nvcr.io/nvidia/ai-dynamo/vllm-runtime:1.6.0
```

Fonte: <https://nvcr.io/nvidia/ai-dynamo/vllm-runtime:1.6.0>

## O que fazer hoje

O caminho começa pela escolha do modelo e termina com um teste de serviço. Cada etapa tem um resultado verificável, para separar a instalação do runtime da validação da implantação.

1. Escolha o modelo no checkpoint oficial e leia a licença correspondente. O resultado é uma variante definida e condições de uso identificadas antes do deploy.
2. Confirme a geração das GPUs disponíveis no cluster. O resultado é saber se o ambiente corresponde à base B200 das receitas ou se precisará de adaptação.
3. Localize a receita no repositório ai-dynamo/dynamo. O resultado é ter o caminho exato do manifesto agregado, desagregado ou base escolhido.
4. Abra o YAML e confirme apiVersion nvidia.com/v1beta1, kind DynamoGraphDeploymentRequest e o identificador do checkpoint. O resultado é descartar diferenças de variante ou de versão de API antes da aplicação.
5. Instale o Dynamo pela opção via PyPI ou pelo container NGC. O resultado é ter o runtime disponível no ambiente escolhido.
6. No diretório da receita, aplique o manifesto no namespace dynamo-system. O resultado é enviar a solicitação de implantação ao Kubernetes.
7. Envie requisições de teste representativas e observe respostas, latência e uso dos recursos. O resultado é ter evidências do comportamento do serviço antes de ampliar a carga.

```
kubectl apply -f <caminho-da-receita>.yaml -n dynamo-system
```

Fonte: <https://github.com/ai-dynamo/dynamo>

## O que conferir

Uma receita validada reduz tentativa e erro, mas ainda exige conferência no ambiente de destino. Hardware, variante do modelo, licença e topologia precisam permanecer coerentes com o arquivo aplicado.

- Hardware: as receitas são otimizadas para GPUs NVIDIA B200. Outra geração pode exigir alterações nos manifestos e nova validação de desempenho.
- Desempenho: até 2x é um valor máximo declarado fora da caixa. Use seus próprios testes para decidir se a configuração atende à carga.
- Licenças: A.X K2 e K-EXAONE 2.0 usam Apache 2.0; Solar Open 2 usa Upstage Solar License; Motif-3 usa MIT. Modelo aberto não significa termos idênticos.
- Variantes: preserve os identificadores skt/A.X-K2-NVFP4, LGAI-EXAONE/K-EXAONE-2.0-750B-A37B-NVFP4, upstage/Solar-Open2-250B e Motif-Technologies/Motif-3. A variante Motif-3-NVFP4 aparece na receita.
- Topologia: A.X K2 e Solar Open 2 têm caminhos agg e disagg. Aplicar um arquivo esperando o comportamento do outro compromete a avaliação.
- Kubernetes: confira apiVersion nvidia.com/v1beta1, kind DynamoGraphDeploymentRequest e o namespace dynamo-system. A aplicação do manifesto não valida, sozinha, a qualidade do serviço.
- Caminhos de execução: a receita do Motif-3 no Dynamo e o comando vllm serve Motif-Technologies/Motif-3 são opções diferentes. Não presuma que elas produzam a mesma topologia.
- Revisão humana: teste respostas, roteamento, comunicação e comportamento sob carga antes de tratar a receita como pronta para produção.

Fonte: <https://github.com/ai-dynamo/dynamo>

## Glossário

- GPU: processador gráfico usado para executar os cálculos da inferência de IA.
- Inferência: processo de receber uma entrada e produzir uma resposta com um modelo treinado.
- Serving de inferência: camada que recebe requisições, encaminha o processamento e devolve respostas.
- Modelo distribuído: modelo cujo processamento é dividido entre várias GPUs ou nós.
- Multi-nó: ambiente com várias máquinas participando da mesma implantação.
- Roteamento de requisições: decisão sobre qual trabalhador recebe cada pedido.
- Checkpoint: conjunto de pesos e metadados que identificam a versão do modelo a ser carregada.
- Parâmetros totais e ativos: o total indica o porte do modelo; os ativos indicam a parte acionada no processamento.
- MoE: arquitetura mixture of experts, com vários especialistas e participação de apenas parte deles em cada processamento.
- NVFP4: formato de quantização de baixa precisão de 4 bits identificado nas variantes dos checkpoints.
- Token e janela de contexto: token é uma unidade de texto processada pelo modelo; a janela de contexto é a quantidade que ele considera em uma entrada.
- Kubernetes: plataforma que gerencia aplicações e seus recursos em clusters.
- Manifesto YAML: arquivo que descreve o recurso e a configuração que serão aplicados no cluster.
- Namespace: espaço lógico usado para organizar recursos no Kubernetes; as receitas usam dynamo-system.
- apiVersion: versão da API Kubernetes do recurso; nas receitas, nvidia.com/v1beta1.
- kind: tipo de recurso declarado; nas receitas, DynamoGraphDeploymentRequest.
- vLLM: runtime de serving usado pelas receitas vllm indicadas nos caminhos do Dynamo.
- NGC: catálogo de containers da NVIDIA usado para distribuir a imagem do runtime.
- PyPI: repositório de pacotes Python onde o ai-dynamo é distribuído.
- Receitas agg e disagg: nomes que distinguem configurações de implantação agregadas e desagregadas.

Fonte: <https://github.com/ai-dynamo/dynamo>

## Para onde ir depois

O próximo passo é transformar a leitura em um teste controlado. Escolha um modelo, mantenha a variante exata e pratique o fluxo completo até receber respostas do serviço.

- Comece pelo checkpoint oficial do modelo escolhido e identifique a licença aplicável.
- Abra a receita correspondente e marque o caminho do manifesto, o checkpoint, apiVersion e kind.
- Instale o Dynamo por uma das opções oficiais e aplique o manifesto em um ambiente de teste.
- Envie entradas representativas do seu uso e registre respostas, latência e consumo de recursos.
- Se o hardware for diferente de B200, adapte os parâmetros e repita a validação antes de ampliar a operação.

Fonte: <https://github.com/ai-dynamo/dynamo>

## Além do vídeo

- A instalação via PyPI também oferece um extra para SGLang; as receitas divulgadas neste anúncio usam vLLM.
- A página do produto NVIDIA Dynamo reúne a apresentação da plataforma: https://www.nvidia.com/en-us/ai-data-science/products/dynamo/.
- A página do pacote ai-dynamo no PyPI concentra a distribuição do pacote: https://pypi.org/project/ai-dynamo/.
