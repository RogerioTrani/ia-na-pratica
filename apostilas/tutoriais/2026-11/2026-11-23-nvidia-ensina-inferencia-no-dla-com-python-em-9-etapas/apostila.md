# NVIDIA ensina inferência no DLA com Python em 9 etapas

_2026-11-23 · tutorial_

A NVIDIA publicou em 13 de novembro um tutorial que roda inferência no DLA do Jetson AGX Orin só com Python, pelo módulo cuda.bindings.cudla. O ciclo tem nove etapas: iniciar o CUDA, criar o dispositivo, carregar a rede, alocar e registrar memória, enviar a tarefa e ler a saída. Esta apostila reúne o que preparar, os comandos de cada etapa na ordem e como conferir o resultado.

## O que você precisa antes de começar

O módulo cudla chegou no cuda-bindings 13.3.0 e conversa com a libcudla.so, que já vem com o JetPack. Não há SDK separado do cuDLA para instalar. O TensorRT só entra para compilar o loadable; para rodar um loadable que você já tem, basta a libcudla.so.

- Jetson AGX Orin com JetPack
- Python 3.10 ou superior
- Bindings do cuDLA, com o comando abaixo
- Um loadable DLA, como o model.bin, gerado pelo trtexec no modo standalone de DLA

```
pip install "cuda-bindings>=13.3.0"
```

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Passos 1 e 2: iniciar o CUDA e criar o dispositivo DLA

Importe numpy, cudla, driver e runtime, inicialize o driver e selecione a GPU 0. O cuDLA trabalha junto com a GPU, então tudo passa por um contexto CUDA. Se der certo, nada aparece na tela.

Em seguida crie o dispositivo com o modo híbrido (cudla.Mode.CUDA_DLA). Nele você envia tarefas do DLA por um stream CUDA, e pré-processamento na GPU, inferência no DLA e pós-processamento ficam na mesma fila, executados em ordem.

- Se o import de cudla falhar, confira se o pip instalou cuda-bindings>=13.3.0 e se o Python do ambiente é 3.10 ou superior.
- Se aparecer CudlaError(ErrorUnsupportedOperation), você pediu o modo standalone, que esta versão não suporta. Use cudla.Mode.CUDA_DLA.

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Passos 3 e 4: carregar o loadable e consultar os tensores

Leia o model.bin em modo binário e passe os bytes para module_load_from_memory. Como a função recebe bytes, você também pode carregar de um arquivo mapeado em memória ou da rede.

Antes de alocar qualquer memória, pergunte ao módulo o que ele espera. Cada descritor traz o tamanho em bytes (size_), a forma (n, c, h, w), o nome, o formato e o stride. Nenhum tamanho fica fixo no código, e o mesmo script serve para qualquer rede.

- Se o arquivo não for encontrado, confira o caminho do model.bin e se a compilação com trtexec terminou.
- Se uma chamada falhar, ela levanta uma exceção Python. Leia a mensagem e confira se o loadable certo foi carregado.

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Passos 5 e 6: alocar buffers na GPU e registrar no cuDLA

Aloque um buffer para a entrada e outro para a saída, com o tamanho vindo de size_ em cada descritor. As chamadas CUDA devolvem uma tupla com o status na primeira posição, por isso o [1] pega o ponteiro. Em produção, verifique o status.

O registro é a etapa exclusiva do cuDLA: um buffer da GPU só pode aparecer numa tarefa depois de registrado, e o registro devolve o identificador que o hardware usa para acessá-lo. O int() extrai o ponteiro bruto do objeto CUDA, porque os bindings devolvem objetos opacos.

- Se a rede tiver várias entradas ou saídas, repita em laço, um buffer por tensor.
- Se der erro de tipo no registro, confira se o buffer está dentro do int().

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Passo 7: criar o stream e copiar a entrada

O stream não bloqueante é o ponto único que coordena GPU e DLA. O pré-processamento é o único código que depende do modelo: o array input_cpu precisa seguir o stride, o data_format e o data_type do descritor de entrada. O resto do script é igual para qualquer rede.

Se o resultado ficar estranho, o layout do array provavelmente não bate com o descritor.

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

## Passos 8 e 9: enviar a tarefa, sincronizar e ler a saída

cudla.Task representa a estrutura de tarefa do cuDLA. Ao atribuir uma lista a task.input_tensor ou task.output_tensor, a contagem é atualizada sozinha. O submit_task enfileira a tarefa no stream e retorna sem esperar o DLA terminar.

A primeira sincronização espera o DLA concluir. Depois você copia a saída da GPU para um array na CPU, sincroniza de novo para garantir que a cópia terminou e libera cada recurso, do registro de memória ao stream.

- Envolva o ciclo em try/finally para liberar os recursos mesmo quando uma chamada falhar.
- Falhas do cuDLA viram exceções Python (cudla.CudlaError). Trate pelo enum cudla.Status.

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Como conferir se funcionou

Rode o script inteiro, da inicialização até a sincronização. Toda chamada do cuDLA levanta erro Python quando falha, então um script que termina sem exceção completou o ciclo. Depois olhe output_cpu: a saída deve ter o formato do descritor de saída. Num classificador de imagens, a classe mais provável deve fazer sentido para a imagem enviada.

- Sem exceção: o ciclo completo funcionou.
- Com exceção: leia o status em cudla.Status e volte ao passo correspondente.

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Exemplo completo e links oficiais

O repositório Deep Learning Accelerator da NVIDIA traz o exemplo de ponta a ponta, com preparação e compilação do modelo.

- Tutorial da NVIDIA: https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/
- Exemplo cuDLA Python E2E: https://github.com/NVIDIA/Deep-Learning-Accelerator-SW/tree/main/samples/cuDLA/cuDLAPythonE2E
- Projeto CUDA Python (cuda-bindings): https://github.com/NVIDIA/cuda-python
- Introdução ao DLA no Jetson Orin: https://developer.nvidia.com/blog/getting-started-with-the-deep-learning-accelerator-on-nvidia-jetson-orin/

Fonte: <https://github.com/NVIDIA/Deep-Learning-Accelerator-SW/tree/main/samples/cuDLA/cuDLAPythonE2E>

## Além do vídeo

- O comando trtexec que compila um modelo ONNX FP16 em loadable DLA (TensorRT 11.4.1, CUDA 13.4 Update 1, JetPack 7.2.2 ou superior), com as flags --useDLACore=0, --buildDLAStandalone e formato chw16.
- Como instalar o Python 3.12 pelo PPA deadsnakes e criar um ambiente virtual, caso o Python padrão do JetPack seja anterior ao 3.10.
- No TensorRT 11, a precisão vem dos tipos de tensor do modelo, e as flags --fp16 e --int8 não são mais aceitas.
- Nem toda camada é compatível com o DLA, e muitas vezes é preciso cortar do grafo ONNX as camadas iniciais e finais incompatíveis.
- A mesma API cuDLA em Python vale para o NVIDIA RTX Spark, em notebooks Windows para desenvolvedores de IA, e o repositório cuda-python tem testes unitários que rodam sem hardware.
