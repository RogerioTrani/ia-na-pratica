# NVIDIA ensina inferência no DLA com Python em 9 etapas

_2026-11-23 · tutorial_

Este tutorial ensina a rodar inferência de uma rede neural no DLA do Jetson AGX Orin usando apenas Python, com o módulo cuda.bindings.cudla, em nove etapas. Você vai preparar o ambiente, compilar um loadable com trtexec, criar o dispositivo em modo híbrido, alocar e registrar buffers, enviar a tarefa por um stream CUDA e ler o resultado. Ao final, terá um script reutilizável para qualquer rede e saberá conferir se tudo funcionou. O DLA libera a GPU e pode reduzir o consumo de energia: segundo um blog da NVIDIA de agosto de 2023, ele entrega em média de 3 a 5 vezes mais desempenho por watt que a GPU, conforme o modo de energia e a carga.

## O que você terá no fim

Ao final deste tutorial, você terá um script Python completo que executa uma rede neural no DLA (Deep Learning Accelerator) do Jetson AGX Orin, sem escrever C++. O script cria o dispositivo, carrega a rede compilada, aloca e registra buffers, envia a tarefa por um stream CUDA e lê o resultado na CPU.

O DLA é um acelerador de função fixa dedicado à inferência. Ao rodar a rede nele, a GPU fica livre para pré-processamento, pós-processamento e outras tarefas, e a eficiência energética pode melhorar. O resultado é um ciclo de inferência orquestrado em Python, reutilizável para qualquer loadable.

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Por que o DLA importa

Os números desta seção vêm de um blog da NVIDIA publicado em agosto de 2023. O Jetson AGX Orin entrega até 275 TOPs de IA (INT8 esparso, pico), e quase 40% desse total vem dos dois DLAs no modo MAXN. O DLA tem em média de 3 a 5 vezes melhor desempenho por watt que a GPU, conforme o modo de energia e a carga, o que permite atingir o teto de 275 TOPs dentro do orçamento de energia da plataforma.

Usar o DLA não é só economia: é paralelismo. No stack de condução autônoma NVIDIA DRIVE AV, mapear a inferência para o DLA e reservar a GPU para tarefas não-DNN reduziu a latência do pipeline de percepção em 2,5 vezes. No NVIDIA Isaac, o BI3D roda a cerca de 46 fps com 30 ms de latência no AGX Orin, com diversidade de hardware para segurança funcional.

No DeepStream SDK, rodar modelos do Model Zoo no DLA exige apenas uma flag, e a taxa combinada GPU + DLA1 + DLA2 chega a até 3.600 fps para algumas redes.

- 275 TOPs: pico de IA INT8 esparso do Jetson AGX Orin (GPU + 2 DLA) no modo MAXN.
- 38% a 74%: fatia do desempenho INT8 total que vem dos dois DLA, conforme o modo de energia (MAXN, 50 W, 30 W, 15 W).
- 3 a 5 vezes: vantagem média de desempenho por watt do DLA sobre a GPU, conforme o modo de energia e a carga.
- 2,5 vezes: redução de latência do pipeline de percepção do DRIVE AV ao mover DNNs para o DLA.
- Cerca de 46 fps e 30 ms: BI3D no DLA do AGX Orin, com três redes.
- Até 3.600 fps: throughput combinado GPU + DLA1 + DLA2 para algumas redes no DeepStream.

Fonte: <https://developer.nvidia.com/blog/maximizing-deep-learning-performance-on-nvidia-jetson-orin-with-dla/>

## Como isso funciona

O DLA é um acelerador de função fixa: executa operações fixas como convoluções e pooling, comuns em redes neurais, com menos camadas suportadas que a GPU, mas com boa cobertura das arquiteturas populares.

O cuDLA é a API de runtime que gerencia a execução nesse acelerador: cria dispositivos DLA, carrega redes compiladas, registra buffers de memória e envia tarefas de inferência. O módulo cuda.bindings.cudla expõe essa API C++ diretamente ao Python, sem C++.

O modo usado é o híbrido (cudla.Mode.CUDA_DLA): as tarefas do DLA são enviadas por um stream CUDA, o que permite enfileirar, na mesma fila e em ordem, kernels de pré-processamento na GPU, inferência no DLA e pós-processamento na GPU.

Introduzido no cuda-bindings 13.3.0, o módulo expõe treze funções, nove tipos de dados e oito enums para o fluxo híbrido. No Jetson Orin, a libcudla.so já vem com o JetPack. A mesma API vale para o NVIDIA RTX Spark, estendendo o cuDLA a laptops Windows.

Todo o fluxo passa por um único stream CUDA, que é o ponto de coordenação entre GPU e DLA.

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Antes de começar

Confira os requisitos antes de rodar o script. O runtime do DLA já vem com o JetPack, então não há SDK separado para instalar.

- Jetson AGX Orin com JetPack instalado (a libcudla.so já vem com o JetPack; não há SDK separado).
- Python 3.10 ou superior (o Python padrão do JetPack pode ser mais antigo; instale o 3.12 via deadsnakes se precisar).
- pip install "cuda-bindings>=13.3.0" (bindings Python do cuDLA).
- Um loadable DLA, como model.bin, gerado com trtexec.
- TensorRT apenas para compilar o loadable; não é necessário para rodar a inferência.
- Repositório oficial do projeto: github.com/NVIDIA/cuda-python.

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Como gerar o loadable DLA

O loadable é o artefato binário produzido pelo trtexec. Ele codifica a rede treinada em formato que o hardware DLA executa diretamente. A compilação é feita uma vez; a inferência roda só com a libcudla.so.

O exemplo a seguir mira TensorRT 11.4.1 com CUDA 13.4 Update 1 no Jetson AGX Orin com JetPack 7.2.2 ou superior, para um loadable FP16 em layout CHW16, com modelo ONNX FP16 de dimensões fixas.

Nem toda camada é compatível com o DLA; costuma ser necessário pré-processar o grafo ONNX para remover camadas incompatíveis nas pontas. O fluxo Python funciona com qualquer arquivo .bin ou .nvdla gerado.

- --useDLACore=0: seleciona o primeiro motor DLA do Orin.
- --buildDLAStandalone: gera um loadable bruto que não exige TensorRT em tempo de inferência.
- Formatos CHW16: selecionam o layout de I/O.
- No TensorRT 11, a precisão vem dos tipos do modelo; --fp16 e --int8 não são mais suportados.
- Dimensões fixas: --shapes é omitido neste exemplo.

```
trtexec \
  --onnx=your_model_fp16.onnx \
  --useDLACore=0 \
  --inputIOFormats=chw16 \
  --outputIOFormats=chw16 \
  --memPoolSize=dlaSRAM:1 \
  --saveEngine=model.bin \
  --buildDLAStandalone
```

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Passo a passo

1. Inicializar o CUDA: importe numpy, cudla, driver e runtime; chame cuInit e cudaSetDevice. Resultado: nenhuma saída e nenhuma exceção.
2. Criar o dispositivo DLA: chame create_device com índice 0 e modo CUDA_DLA. Resultado: a variável cudla_device é criada, sem erro.
3. Carregar o loadable: leia model.bin em modo binário e passe os bytes para module_load_from_memory. Resultado: module_handle criado, sem exceção.
4. Consultar descritores: obtenha número de entradas, número de saídas e os descritores de cada tensor. Resultado: as variáveis num_inputs, num_outputs, input_descs e output_descs preenchidas.
5. Alocar buffers na GPU: use cudaMalloc para entrada e saída com o tamanho de size_. Resultado: input_gpu e output_gpu definidos, sem erro.
6. Registrar buffers no cuDLA: chame mem_register para entrada e saída. Resultado: input_registered e output_registered criados, sem exceção.
7. Criar stream e copiar entrada: crie o stream, prepare input_cpu e copie com cudaMemcpyAsync; zere a saída. Resultado: stream criado e operações enfileiradas, sem erro.
8. Montar e enviar a tarefa: crie cudla.Task, atribua os tensores e chame submit_task. Resultado: chamada retorna sem exceção, tarefa enfileirada.
9. Sincronizar e ler a saída: espere o stream, copie o buffer de saída para a CPU, sincronize de novo e libere os recursos. Resultado: output_cpu com o resultado da rede.

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Passo 1: inicialize o CUDA no seu script

No início do script, importe numpy, cudla, driver e runtime, depois inicialize o driver e selecione a GPU zero. Esse passo existe porque o cuDLA trabalha em conjunto com a GPU: tudo passa por um contexto CUDA, e sem ele as chamadas seguintes não têm onde rodar.

Se der certo, nada aparece na tela; a ausência de exceção é o sinal de sucesso. Se o import de cudla falhar, confira se o pip instalou cuda-bindings 13.3.0 ou mais novo e se o Python do ambiente é 3.10 ou superior.

```
import numpy as np
from cuda.bindings import cudla
from cuda.bindings import driver, runtime
driver.cuInit(0)
runtime.cudaSetDevice(0)
```

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Passo 2: crie o dispositivo DLA em modo híbrido

Chame create_device com índice 0 e modo cudla.Mode.CUDA_DLA. Nele você envia tarefas do DLA por um stream CUDA, e pré-processamento na GPU, inferência no DLA e pós-processamento ficam na mesma fila, executados em ordem. Guarde o objeto, porque todas as chamadas seguintes dependem dele.

O modo standalone não é suportado nesta versão. Se você pedi-lo, create_device levanta CudlaError(ErrorUnsupportedOperation).

```
cudla_device = cudla.create_device(0, int(cudla.Mode.CUDA_DLA))
```

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Passo 3: carregue o loadable a partir da memória

Leia o model.bin em modo binário e passe os bytes para module_load_from_memory. O loadable é o resultado da compilação da rede e contém o que o hardware DLA executa. Como a função recebe bytes, você poderia ler de um arquivo mapeado em memória ou até da rede.

Se o arquivo não for encontrado, confira o caminho do model.bin e se a compilação com trtexec terminou.

```
with open("model.bin", "rb") as f:
    loadable_data = f.read()

module_handle = cudla.module_load_from_memory(
    cudla_device, loadable_data, len(loadable_data), 0
)
```

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Passo 4: consulte os descritores dos tensores

Faça quatro consultas de atributos: número de tensores de entrada, número de saídas, e as listas de descritores de entrada e saída. Vem antes de qualquer alocação porque cada descritor informa tamanho em bytes, formato, forma n c h w, nome e stride. Assim nenhum tamanho fica fixo no código, e o mesmo script serve para qualquer rede.

Cada descritor é um cudla.ModuleTensorDescriptor com size_, n, c, h, w, nome, formato e stride.

```
num_inputs = cudla.module_get_attributes(
    module_handle, int(cudla.ModuleAttributeType.NUM_INPUT_TENSORS)
)
num_outputs = cudla.module_get_attributes(
    module_handle, int(cudla.ModuleAttributeType.NUM_OUTPUT_TENSORS)
)
input_descs = cudla.module_get_attributes(
    module_handle, int(cudla.ModuleAttributeType.INPUT_TENSOR_DESCRIPTORS)
)
output_descs = cudla.module_get_attributes(
    module_handle, int(cudla.ModuleAttributeType.OUTPUT_TENSOR_DESCRIPTORS)
)
```

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Passo 5: aloque os buffers na GPU

Use runtime.cudaMalloc uma vez para a entrada e outra para a saída, com o tamanho vindo de size_ em cada descritor. O DLA lê e escreve em buffers que você prepara, e o tamanho exato está no descritor.

As chamadas CUDA devolvem uma tupla com o código de status na primeira posição; por isso o [1] pega o ponteiro. Em código de produção, confira o status. Para modelos com várias entradas ou saídas, itere sobre os descritores e aloque um buffer por tensor.

```
input_gpu = runtime.cudaMalloc(input_descs[0].size_)[1]
output_gpu = runtime.cudaMalloc(output_descs[0].size_)[1]
```

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Passo 6: registre os buffers no cuDLA

Chame mem_register para a entrada e para a saída, passando o dispositivo, o ponteiro convertido para inteiro, o tamanho e zero. Um buffer da GPU só pode aparecer numa tarefa depois de registrado; o registro devolve o identificador que o hardware usa para acessá-lo.

Não esqueça o int() em volta do buffer: os bindings devolvem objetos opacos, e a API espera o ponteiro bruto.

```
input_registered = cudla.mem_register(
    cudla_device, int(input_gpu), input_descs[0].size_, 0
)
output_registered = cudla.mem_register(
    cudla_device, int(output_gpu), output_descs[0].size_, 0
)
```

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Passo 7: crie o stream e copie a entrada

Crie um stream CUDA não bloqueante; esse é o stream único que coordena GPU e DLA. Prepare o array input_cpu no layout do descritor e copie com cudaMemcpyAsync; depois zere a saída com cudaMemsetAsync.

O pré-processamento é o único código que depende do modelo; o resto do script é igual para qualquer rede. O array precisa seguir o stride, o data_format e o data_type do descritor.

```
stream = driver.cuStreamCreate(driver.CUstream_flags.CU_STREAM_NON_BLOCKING)[1]

# Preprocess your input into a numpy array `input_cpu`
# matching the tensor layout described by input_descs[0]
...

runtime.cudaMemcpyAsync(
    input_gpu, input_cpu, input_descs[0].size_,
    runtime.cudaMemcpyKind.cudaMemcpyHostToDevice, stream
)
runtime.cudaMemsetAsync(output_gpu, 0, output_descs[0].size_, stream)
```

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Passo 8: monte a tarefa e envie ao DLA

Crie um cudla.Task, atribua as listas de tensores de entrada e de saída; a contagem é atualizada sozinha quando você atribui a lista. Depois chame submit_task para enfileirar no stream. É aqui que a inferência é de fato pedida ao DLA, usando os buffers registrados.

Falhas do cuDLA viram exceções Python (cudla.CudlaError); trate pelo enum cudla.Status.

```
task = cudla.Task()
task.module_handle = module_handle
task.input_tensor = [int(input_registered)]
task.output_tensor = [int(output_registered)]
task.wait_events = 0
task.signal_events = 0

cudla.submit_task(cudla_device, int(task), 1, int(stream), 0)
```

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Passo 9: sincronize o stream e leia a saída

A primeira sincronização espera o DLA terminar. Em seguida crie na CPU um array do tamanho da saída e copie o buffer da GPU para ele; a segunda sincronização garante que a cópia terminou antes de você ler. Depois vem a limpeza, na ordem do código abaixo.

Use try/finally para liberar os recursos mesmo quando uma chamada falhar. Os handles do DLA são recursos C opacos e não se liberam sozinhos na coleta de lixo.

```
runtime.cudaStreamSynchronize(stream)
output_cpu = np.empty(output_descs[0].size_, dtype=np.uint8)
runtime.cudaMemcpyAsync(
    output_cpu, output_gpu, output_descs[0].size_,
    runtime.cudaMemcpyKind.cudaMemcpyDeviceToHost, stream
)
runtime.cudaStreamSynchronize(stream)
cudla.mem_unregister(cudla_device, input_registered)
cudla.mem_unregister(cudla_device, output_registered)
cudla.module_unload(module_handle, 0)
cudla.destroy_device(cudla_device)
runtime.cudaFree(input_gpu)
runtime.cudaFree(output_gpu)
driver.cuStreamDestroy(stream)
```

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Exemplo completo

Para um exemplo ponta a ponta, com preparação e compilação do modelo, consulte os exemplos oficiais do Deep Learning Accelerator. O repositório traz scripts para preparar o modelo e compilar o loadable.

Após a sincronização, output_cpu contém a saída bruta da rede como array numpy. Para uma ResNet-50 compilada como loadable, a saída típica mostra tamanhos de buffer e nomes de tensores, como numInputTensors = 1 e numOutputTensors = 1, com formas como (1,64,56,56) na entrada e (1,2048,7,7) na saída. Interprete ou remodele o array usando data_type, data_format, stride e shape do descritor de saída.

- Repositório: github.com/NVIDIA/Deep-Learning-Accelerator-SW (samples/cuDLA/cuDLAPythonE2E).

Fonte: <https://github.com/NVIDIA/Deep-Learning-Accelerator-SW/tree/main/samples/cuDLA/cuDLAPythonE2E>

## Teste de pronto

- [ ] Execute o script do cuInit até a sincronização final: se nenhuma exceção aparecer, as chamadas do cuDLA funcionaram, porque cada uma levanta erro Python quando falha. As chamadas CUDA de driver e runtime devolvem um status na tupla; confira-o também.
- [ ] A saída deve ter o formato do descritor de saída (shape, stride e tipo de dado).
- [ ] Em um classificador de imagens, a classe mais provável deve fazer sentido para a imagem enviada.
- [ ] Se surgir uma exceção, leia o status em cudla.Status e volte ao passo correspondente.

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Erros comuns e cuidados

- Modo standalone não suportado nesta versão: create_device levanta CudlaError(ErrorUnsupportedOperation). Use cudla.Mode.CUDA_DLA.
- Import de cudla falha: confira pip install "cuda-bindings>=13.3.0" e Python 3.10 ou superior.
- Arquivo model.bin não encontrado: confira o caminho e se a compilação com trtexec terminou.
- Layout de entrada errado: o array precisa seguir stride, data_format e data_type do descritor; se não bater, a entrada chega errada ao DLA.
- Esquecer o int() em volta do buffer: os bindings devolvem objetos opacos.
- Esquecer o [1] em cudaMalloc: a chamada devolve tupla com status na primeira posição.
- Nem toda camada é DLA-compatível: pré-processe o grafo ONNX para remover camadas incompatíveis nas pontas.
- Handles do DLA são recursos C opacos: use try/finally para liberar tudo, inclusive em falha.
- O TensorRT 11 não aceita --fp16/--int8: a precisão vem dos tipos do modelo ONNX.

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Glossário

- DLA (Deep Learning Accelerator): acelerador de função fixa dedicado à inferência de redes neurais, presente no SoC Orin.
- cuDLA: API de runtime para gerenciar a execução no DLA.
- cuda.bindings.cudla: módulo Python que expõe a API C++ do cuDLA.
- Loadable: artefato binário (.bin ou .nvdla) produzido pelo trtexec, que o DLA executa diretamente.
- Modo híbrido (CUDA_DLA): modo em que tarefas do DLA são enviadas por um stream CUDA, permitindo pipeline GPU-DLA-GPU.
- Modo standalone: modo que exige primitivas NvSci; não suportado nesta versão.
- Stream CUDA: fila de execução que coordena GPU e DLA.
- Tensor descriptor: estrutura com size_, forma (n, c, h, w), nome, formato e stride de um tensor.
- libcudla.so: biblioteca de runtime do cuDLA, fornecida pelo JetPack.
- trtexec: ferramenta do TensorRT que compila um modelo ONNX em loadable DLA.
- JetPack: SDK da NVIDIA para Jetson, que inclui a libcudla.so.
- RTX Spark: plataforma que leva a inferência DLA a laptops Windows, com a mesma API.
- TOPs: trilhões de operações por segundo, medida de throughput de IA.

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Plano de 7 dias

- Dia 1: preparar o ambiente (JetPack, Python 3.10+, pip install cuda-bindings>=13.3.0) e clonar o cuda-python.
- Dia 2: compilar um loadable com trtexec (--buildDLAStandalone) a partir de um modelo ONNX FP16.
- Dia 3: implementar os passos 1 a 3 (inicializar CUDA, criar dispositivo híbrido, carregar loadable).
- Dia 4: implementar os passos 4 a 6 (descritores, cudaMalloc, mem_register).
- Dia 5: implementar os passos 7 a 9 (stream, cópia, task, sincronização, limpeza).
- Dia 6: rodar o teste de pronto, tratar exceções com cudla.Status e validar a saída.
- Dia 7: estudar o exemplo completo do repositório DLA-SW e experimentar modelos do DeepStream.

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Para onde ir depois

- Explorar os exemplos do Deep Learning Accelerator (cuDLA Python E2E) para um caso completo com preparação e compilação do modelo: github.com/NVIDIA/Deep-Learning-Accelerator-SW/tree/main/samples/cuDLA/cuDLAPythonE2E.
- Visitar o repositório NVIDIA/cuda-python para saber mais sobre o projeto CUDA Python e rodar testes unitários sem hardware: pytest cuda_bindings/tests/cudla/ -v.
- Ler 'Getting Started with the Deep Learning Accelerator on NVIDIA Jetson Orin' para decidir quando usar DLA.
- Consultar 'Working with DLA' na documentação do TensorRT para requisitos de plataforma (JetPack 7.2.2 ou superior no AGX Orin).
- Experimentar o DeepStream SDK para rodar modelos do Model Zoo no DLA com uma flag.

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Links citados

- https://developer.nvidia.com/blog/getting-started-with-the-deep-learning-accelerator-on-nvidia-jetson-orin/
- https://github.com/NVIDIA/cuda-python

## Além do vídeo

- No blog de agosto de 2023, a tabela do DeepStream para modelos do Model Zoo traz, em fps (GPU, DLA1 + DLA2 e os três juntos): PeopleNet-ResNet18 com 218, 128 e 346; TrafficCamNet com 251, 174 e 425; VehicleMakeNet com 2.434, 1.166 e 3.600.
- No estudo de caso do DRIVE AV, o pipeline de percepção recebe dados de oito câmeras e a parte de percepção responde por mais de 60% de todo o processamento.
- Segundo o mesmo blog, a equipe do Isaac usa TensorRT no DLA para ter diversidade de hardware em relação à GPU, melhorar a tolerância a falhas e liberar a GPU para outras tarefas.
- A documentação Working with DLA do TensorRT informa que, no TensorRT 11.4.1, o suporte ao DLA depende da plataforma e do pacote; no Jetson AGX Orin com JetPack 7.2.2 ou superior ele está em disponibilidade geral.
