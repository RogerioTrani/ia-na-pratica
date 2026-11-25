# Projeto C99 roda Kimi K3 em CPU com 8 GB

_2026-11-24 · reportagem_

O kimi-k3-in-c roda inferência do Kimi K3, um modelo de 2,78 trilhões de parâmetros, em uma única CPU, sem GPU e com pico medido de 8,24 GB de RAM. O código é C 99 portátil. O custo está no disco, com 1,56 TB de checkpoint, e na velocidade, de cerca de 26 segundos por token.

## O contexto

O kimi-k3-in-c é um mecanismo open source que roda o Kimi K3, de 2,78 trilhões de parâmetros, em CPU comum. Não usa placa de vídeo.

O código é escrito em C 99 puro, sem PyTorch, TensorFlow ou bibliotecas BLAS. O código está no GitHub sob licença Apache 2.0.

Fonte: <https://github.com/FareedKhan-dev/kimi-k3-in-c>

## Quem ganha e quem perde

Os pesos não são carregados inteiros na RAM. O projeto lê do disco e processa sob demanda.

O modelo usa mistura de especialistas. Os especialistas já vêm em 4 bits (MXFP4), então só os componentes necessários ficam ativos.

Nos testes do repositório, o pico medido foi de 8,24 GB de RAM.

## O que ainda não se sabe

Pouca RAM não significa modelo leve. O checkpoint ocupa 1,56 TB em disco, com cerca de 1,7 TB livres necessários.

A velocidade é de cerca de 26 segundos por token, sem GPU e com 8 GB de RAM.

## O que você pode fazer

Antes de baixar o modelo completo, teste o motor em cerca de um minuto.

1. Clone o repositório e compile com make -j. Resultado: o motor fica compilado.
2. Rode a suíte de testes com make test. Resultado: os testes rodam sem baixar o modelo.

```
make test
```

Fonte: <https://github.com/FareedKhan-dev/kimi-k3-in-c>

## Além do vídeo

- A quantização de 4 bits reduz o consumo de memória e o tráfego de dados.
