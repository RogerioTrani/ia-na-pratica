# Astra e Fable não divulgam o número de parâmetros

_2026-11-23 · reportagem_

Astra e Fable não divulgam o número de parâmetros, e o vídeo lê isso como sinal de que a disputa por tamanho perdeu o peso de antes. A aposta é por modelos menores e especializados, com 50 a 100 bilhões de parâmetros. Esta apostila reúne a lógica da mistura de experts, a conta de memória e o hardware que comporta esse tamanho.

## O número que sumiu

Modelos anteriores chegaram ao mercado com 1 trilhão de parâmetros no cartaz. Astra e Fable não trazem o número na divulgação.

A leitura do vídeo é que o tamanho deixou de ser vitrine: parâmetro a mais já não chama atenção como antes.

## Mistura de experts: só um pedaço na memória

Um modelo denso exige o modelo inteiro carregado na RAM. Com experts por área, só uma fração entra.

Por isso o tamanho total diz menos sobre o custo de rodar.

## A aposta: modelos menores e especializados

A ideia é um modelo focado em código. Ele guarda só o vocabulário mínimo para conversar e perde os experts que não usa.

Depois do corte, o modelo ficaria na casa de 50, 70 ou talvez 100 bilhões de parâmetros. Ainda é um modelo bom, e muito menor que 1 trilhão.

## A conta de memória

Um modelo de 100 bilhões de parâmetros cabe em 128 GB só como modelo. O contexto também ocupa memória, então a conta sobe para 256 GB.

- Só o modelo (100 bilhões): 128 GB
- Modelo mais contexto: 256 GB

## Hardware que comporta essa conta

O Mac Studio com 256 ou 512 GB de memória unificada aloca até 400 GB para a GPU. Uma RTX 5090 tem 32 GB.

- Mac Studio: 256 ou 512 GB de memória unificada, até 400 GB alocados para a GPU
- GeForce RTX 5090: 32 GB

Fonte: <https://www.apple.com/mac-studio/specs/>

## Links oficiais

- Mac Studio, especificações (Apple): https://www.apple.com/mac-studio/specs/
- GeForce RTX 5090 (NVIDIA): https://www.nvidia.com/en-us/geforce/graphics-cards/50-series/rtx-5090/

## Além do vídeo

- A maior parte das ferramentas de IA local é feita para a biblioteca CUDA da NVIDIA e roda pior em AMD e em Mac.
- A NVIDIA vende o DGX Spark, por volta de 4 mil dólares, como opção de nível workstation.
- Circulam rumores de que a RTX 5090 sai de linha e só a 5080 continua.
