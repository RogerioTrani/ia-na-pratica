# Projeto C99 roda Kimi K3 em CPU com 8 GB

_2026-11-24 · reportagem_

O kimi-k3-in-c roda inferência do Kimi K3, um modelo de 2,78 trilhões de parâmetros, em uma única CPU, sem GPU e com pico medido de 8,24 GB de RAM. O código é C 99 portátil, sem PyTorch, TensorFlow ou BLAS. O custo está no disco, com 1,56 TB de checkpoint e cerca de 1,7 TB livres, e na velocidade, de cerca de 26 segundos por token.

## O que é o projeto

O kimi-k3-in-c é um mecanismo open source que roda o Kimi K3, de 2,78 trilhões de parâmetros, em CPU comum. Não usa placa de vídeo.

O código é escrito em C 99 puro, sem PyTorch, TensorFlow ou bibliotecas BLAS.

Fonte: <https://github.com/FareedKhan-dev/kimi-k3-in-c>

## Teste em um minuto, sem baixar o modelo

Dá para compilar e rodar a suíte de testes do motor em cerca de um minuto, sem baixar o modelo. Os três comandos abaixo fazem isso.

- Clone o repositório.
- Compile com make -j.
- Rode a suíte com make test.

Fonte: <https://github.com/FareedKhan-dev/kimi-k3-in-c>

## Como cabe em 8 GB de RAM

Os pesos não são carregados inteiros na RAM. O projeto lê do disco e processa sob demanda.

O modelo usa mistura de especialistas (MoE). Os especialistas já vêm em 4 bits (MXFP4), então só os componentes necessários ficam ativos.

Fonte: <https://github.com/FareedKhan-dev/kimi-k3-in-c>

## O número de memória

Nos testes do repositório, o pico medido foi de 8,24 GB de RAM. Esse número mostra que dá para rodar um modelo gigante com pouca RAM.

Fonte: <https://github.com/FareedKhan-dev/kimi-k3-in-c>

## O custo: disco e velocidade

Pouca RAM não significa modelo leve. Antes de tentar rodar o modelo completo, veja o que a máquina precisa ter.

- Checkpoint: 1,56 TB em disco.
- Espaço livre: cerca de 1,7 TB.
- Velocidade: cerca de 26 segundos por token, sem GPU e com 8 GB de RAM.

Fonte: <https://github.com/FareedKhan-dev/kimi-k3-in-c>

## Licença e repositório

O código está no GitHub sob licença Apache 2.0. Serve como estudo de engenharia de baixo nível: mostra como otimização de sistemas pode levar modelos gigantes a hardware comum.

Fonte: <https://github.com/FareedKhan-dev/kimi-k3-in-c>

## Além do vídeo

- A quantização de 4 bits reduz o consumo de memória e o tráfego de dados.
