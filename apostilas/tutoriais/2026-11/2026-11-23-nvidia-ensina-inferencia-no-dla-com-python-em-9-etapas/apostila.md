# NVIDIA ensina inferência no DLA com Python em 9 etapas

_2026-11-23 · tutorial_

A NVIDIA publicou em 13 de novembro um tutorial que roda inferência no DLA do Jetson AGX Orin só com Python, pelo módulo cuda.bindings.cudla. O ciclo tem nove etapas: iniciar o CUDA, criar o dispositivo, carregar a rede, alocar e registrar memória, enviar a tarefa e ler a saída. Esta apostila reúne o que preparar, os comandos de cada etapa na ordem e como conferir o resultado.

## O que você terá no fim

Ao final, você terá uma inferência rodando no DLA do Jetson AGX Orin só com Python. O módulo cudla chegou no cuda-bindings 13.3.0 e conversa com a libcudla.so, que já vem com o JetPack. Não há SDK separado do cuDLA para instalar. O TensorRT só entra para compilar o loadable; para rodar um loadable que você já tem, basta a libcudla.so. Fonte: https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/

- Jetson AGX Orin com JetPack.
- Python 3.10 ou superior.
- Bindings do cuDLA, com o comando de instalação da seção seguinte.
- Um loadable DLA, como o model.bin, gerado pelo trtexec no modo standalone de DLA.

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Passo a passo

O ciclo tem nove etapas, na ordem abaixo. O comando de instalação e o bloco do stream ficam em seções próprias.

1. Passos 1 e 2: iniciar o CUDA e criar o dispositivo DLA. Importe numpy, cudla, driver e runtime, inicialize o driver e selecione a GPU 0. Crie o dispositivo com o modo híbrido cudla.Mode.CUDA_DLA. Resultado esperado: nada aparece na tela se der certo.
2. Passos 3 e 4: carregar o loadable e consultar os tensores. Leia o model.bin em modo binário e passe os bytes para module_load_from_memory. Pergunte ao módulo o que ele espera: cada descritor traz o tamanho em bytes (size_), a forma, o nome, o formato e o stride. Resultado esperado: você conhece os tamanhos dos tensores.
3. Passos 5 e 6: alocar buffers na GPU e registrar no cuDLA. Aloque um buffer para a entrada e outro para a saída, com o tamanho vindo de size_ em cada descritor. Registre cada buffer, que devolve o identificador usado pelo hardware. Resultado esperado: os buffers estão registrados e prontos para a tarefa.
4. criar o stream e copiar a entrada. O stream não bloqueante coordena GPU e DLA. O array input_cpu precisa seguir o stride, o data_format e o data_type do descritor de entrada. Resultado esperado: a entrada está copiada para a GPU.
5. Passos 8 e 9: enviar a tarefa, sincronizar e ler a saída. Atribua a lista de tensores à tarefa e envie com submit_task. Espere o DLA concluir, copie a saída da GPU para a CPU, sincronize de novo e libere cada recurso. Resultado esperado: o array output_cpu tem a saída.

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Instalar os bindings do cuDLA

Rode o comando abaixo para instalar os bindings do cuDLA. Se o import de cudla falhar, confira se o pip instalou cuda-bindings>=13.3.0 e se o Python do ambiente é 3.10 ou superior. Fonte: https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/

```
pip install "cuda-bindings>=13.3.0"
```

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Criar o stream e copiar a entrada

O pré-processamento é o único código que depende do modelo. O resto do script é igual para qualquer rede. Se o resultado ficar estranho, o layout do array provavelmente não bate com o descritor. Se aparecer CudlaError(ErrorUnsupportedOperation), você pediu o modo standalone, que esta versão não suporta. Use cudla.Mode.CUDA_DLA.

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

## Teste de pronto

Rode o script inteiro, da inicialização até a sincronização. Toda chamada do cuDLA levanta erro Python quando falha, então um script que termina sem exceção completou o ciclo. Depois olhe output_cpu: a saída deve ter o formato do descritor de saída. Num classificador de imagens, a classe mais provável deve fazer sentido para a imagem enviada.

- [ ] Sem exceção: o ciclo completo funcionou.
- [ ] Com exceção: leia o status em cudla.Status e volte ao passo correspondente.
- [ ] A saída tem o formato do descritor de saída.

Fonte: <https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/>

## Cuidados, exemplo completo e links oficiais

O repositório Deep Learning Accelerator da NVIDIA traz o exemplo de ponta a ponta, com preparação e compilação do modelo. Tutorial da NVIDIA: https://developer.nvidia.com/blog/run-native-dla-inference-in-python-on-nvidia-jetson-agx-orin-using-cudla/. Exemplo cuDLA Python E2E: https://github.com/NVIDIA/Deep-Learning-Accelerator-SW/tree/main/samples/cuDLA/cuDLAPythonE2E. Projeto CUDA Python (cuda-bindings): https://github.com/NVIDIA/cuda-python. Introdução ao DLA no Jetson Orin: https://developer.nvidia.com/blog/getting-started-with-the-deep-learning-accelerator-on-nvidia-jetson-orin/

Nem toda camada é compatível com o DLA, e muitas vezes é preciso cortar do grafo ONNX as camadas iniciais e finais incompatíveis. No TensorRT 11, a precisão vem dos tipos de tensor do modelo, e as flags --fp16 e --int8 não são mais aceitas. O trtexec compila um modelo ONNX FP16 em loadable DLA com as flags --useDLACore=0, --buildDLAStandalone e formato chw16. Se o Python padrão do JetPack for anterior ao 3.10, dá para instalar o Python 3.12 pelo PPA deadsnakes e criar um ambiente virtual.

Fonte: <https://github.com/NVIDIA/Deep-Learning-Accelerator-SW/tree/main/samples/cuDLA/cuDLAPythonE2E>
