# Modelos de até 700B parâmetros rodam no gabinete local

_2026-11-22 · noticia_

A NVIDIA apresentou na SC26 o DGX Spark HPC Developer Kit, um cluster de quatro nós DGX Spark ligados em anel, sem switch de rede. Juntos, os nós somam 512GB de memória e 16TB de armazenamento NVMe. Com NVFP4, o kit roda localmente modelos de até 700B parâmetros. Ele está em exposição na SC26 e à venda por parceiros OEM e pelo NVIDIA Marketplace.

## O que é o kit

O DGX Spark HPC Developer Kit é um cluster de quatro nós NVIDIA DGX Spark. Cada nó se conecta direto aos dois vizinhos, formando um anel, por rede NVIDIA ConnectX-7. Não há switch de rede para comprar nem configurar.

O kit traz o GB10 Grace Blackwell Superchip para a mesa de pesquisadores, acadêmicos e desenvolvedores. Ele escala de um nó até quatro e serve para rodar cargas científicas multinó, modelos de IA e agentes sem esperar tempo num cluster de GPU compartilhado.

Fonte: <https://www.nvidia.com/en-us/products/workstations/dgx-spark>

## Memória, armazenamento e modelos

Com quatro nós, o kit soma 512GB de memória combinada e 16TB de armazenamento NVMe. Essa capacidade permite distribuir modelos e cargas científicas entre os nós.

Com NVFP4, é possível rodar localmente, nos quatro DGX Spark, modelos de até 700B parâmetros, como o DeepSeek V4.1.

- Memória combinada: 512GB
- Armazenamento NVMe: 16TB
- Modelos locais com NVFP4: até 700B parâmetros

Fonte: <https://blogs.nvidia.com/blog/dgx-spark-hpc-developer-kit-sc26/>

## Autonomia no dia a dia

Quem tem alocação fixa de computação e servidores deixa de esperar na fila a cada job. A equipe desenvolve e depura por conta própria, guarda as horas do servidor para as execuções de produção e mantém resultados não publicados e dados proprietários na própria infraestrutura.

Fonte: <https://blogs.nvidia.com/blog/dgx-spark-hpc-developer-kit-sc26/>

## HPC SDK: playbook a caminho

Um playbook da NVIDIA para instalar e rodar o HPC SDK chega em breve. O SDK traz compiladores GPU-accelerated para C, C++ e Fortran, bibliotecas e ferramentas de MPI (message passing interface), as mesmas usadas em supercomputadores com tecnologia NVIDIA.

- Construir e testar aplicações científicas nos quatro nós
- Conferir como computação e dados são distribuídos
- Depurar problemas de comunicação antes de escalar para sistemas maiores
- Desenvolver aplicações de GPU multinó, explorar algoritmos FP32 e de precisão mista e rodar dinâmica molecular e simulações de materiais com LAMMPS com Kokkos antes de ir para o data center

Fonte: <https://developer.nvidia.com/hpc-sdk>

## Software que já roda

Em quatro sistemas, a NVIDIA demonstrou LAMMPS com Kokkos para simulação de materiais e NAMD para dinâmica molecular. A comunidade do DGX Spark validou GROMACS (dinâmica molecular), OpenFOAM (dinâmica de fluidos), WRF (modelagem do tempo) e microsserviços NVIDIA NIM como OpenFold3 e Boltz-2, para prever estruturas biomoleculares.

- LAMMPS: https://www.lammps.org/
- NAMD: https://www.ks.uiuc.edu/Research/namd/
- OpenFOAM: https://www.openfoam.com/
- GROMACS: https://www.gromacs.org/

Fonte: <https://blogs.nvidia.com/blog/dgx-spark-hpc-developer-kit-sc26/>

## Casos de pesquisa

O Rubin Lab, do IGI na Universidade da Califórnia em Berkeley, usa um DGX Spark e o modelo NVIDIA Evo 2 para prever traços bacterianos direto de sequências de genoma. Sem as 11 horas de fila do cluster, os resultados saíram 15 vezes mais rápido.

O Hartwig Group, também em Berkeley, faz fine-tuning com LoRA do modelo Nemotron 3 Super 120B-A12B para aprendizado de máquina em química, treinando uma cabeça de predição sobre valores experimentais. Com quantização NVFP4, o laboratório coube um modelo de classe 120B num único dispositivo e passou a rodar treinos contínuos de 8 a 24 horas, um atrás do outro, sem esperar dias na fila do cluster.

Fonte: <https://blogs.nvidia.com/blog/dgx-spark-hpc-developer-kit-sc26/>

## Onde encontrar

O kit está em exposição na SC26 e à venda. Os produtos DGX Spark e os cabos são vendidos por parceiros OEM como Dell Technologies, HP e Lenovo, e também pelo NVIDIA Marketplace.

- NVIDIA Marketplace: https://marketplace.nvidia.com/
- Página do produto: https://www.nvidia.com/en-us/products/workstations/dgx-spark

Fonte: <https://marketplace.nvidia.com/>

## Além do vídeo

- Outros parceiros que vendem o DGX Spark: Acer, ASUS, GIGABYTE, H3C, MSI e xFusion.
- Kvantify usa o NVIDIA cuQuantum e reporta simulações tensor-network de circuitos de química quântica com até 70 qubits e 975 gates em um único DGX Spark, com circuitos gerados para cálculos de energia do estado fundamental da penicilina.
- A CYRAN AI, spin-out do IIT Delhi, usa o DGX Spark e a biblioteca PixelFlux para acelerar a decodificação de JPEG 2000 em imagens de satélite grandes, apoiando análise geoespacial local.
- A OpenFold mostra como fazer fine-tuning do OpenFold3 no DGX Spark para melhorar previsões de estrutura proteína-ligante na descoberta de fármacos.
- Fluxos de trabalho com agentes que preparam entradas de simulação, disparam execuções e resumem resultados, modelos que aproximam simulações lentas para refinar projetos de asa rumo ao arrasto mínimo, e receitas de dados abertos e pós-treino do Nemotron 3.5 Super VL para ciências da vida e química.
