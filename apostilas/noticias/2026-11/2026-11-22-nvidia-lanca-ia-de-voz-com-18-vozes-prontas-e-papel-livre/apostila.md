# Nvidia lança IA de voz com 18 vozes prontas e papel livre

_2026-11-22 · noticia_

A Nvidia liberou o PersonaPlex, um modelo de voz aberto com 7 bilhões de parâmetros que conversa em tempo real e roda no seu computador. Ele ouve e fala ao mesmo tempo, aceita interrupções, tem 18 vozes prontas e deixa você definir o papel da IA. Foi treinado para inglês e precisa de placa de vídeo. Esta apostila reúne o que ele faz, os limites e onde começar.

## O que é o PersonaPlex

O PersonaPlex é um modelo de voz da Nvidia com 7 bilhões de parâmetros e código aberto. Você pode baixar, ver como funciona e rodar no seu computador, sem pagar.

O repositório oficial no GitHub tem mais de 12 mil estrelas.

Fonte: <https://github.com/NVIDIA/personaplex>

## Como ele conversa

O modelo ouve e fala ao mesmo tempo. Se você interrompe no meio da frase, ele para e responde na hora.

Ele também solta um "uhum" enquanto você fala e entende as suas pausas.

Fonte: <https://research.nvidia.com/labs/adlr/personaplex/>

## Voz e papel sob medida

Você escolhe uma das 18 vozes prontas e escreve o papel que a IA vai assumir na conversa.

- Professor simpático
- Atendente de restaurante
- Astronauta a caminho de Marte

Fonte: <https://github.com/NVIDIA/personaplex>

## Limites: idioma e placa de vídeo

O modelo foi treinado para conversar em inglês.

Ele precisa de placa de vídeo. Se faltar memória da placa, rode o servidor com a opção --cpu-offload e parte do trabalho passa para o processador.

```
--cpu-offload
```

Fonte: <https://github.com/NVIDIA/personaplex>

## Por onde começar

O repositório oficial da Nvidia no GitHub traz a instalação passo a passo. O modelo também está publicado no Hugging Face, e a Nvidia mantém uma página de pesquisa sobre o PersonaPlex.

- Repositório: https://github.com/NVIDIA/personaplex
- Modelo personaplex-7b-v1: https://huggingface.co/nvidia/personaplex-7b-v1
- Pesquisa: https://research.nvidia.com/labs/adlr/personaplex/

Fonte: <https://github.com/NVIDIA/personaplex>
