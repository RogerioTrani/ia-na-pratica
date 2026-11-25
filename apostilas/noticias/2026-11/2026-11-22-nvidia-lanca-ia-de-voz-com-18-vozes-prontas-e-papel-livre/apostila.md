# Nvidia lança IA de voz com 18 vozes prontas e papel livre

_2026-11-22 · noticia_

A Nvidia liberou o PersonaPlex, um modelo de voz aberto com 7 bilhões de parâmetros que conversa em tempo real e roda no seu computador. Ele tem 18 vozes prontas e deixa você definir o papel da IA. Foi treinado para inglês e precisa de placa de vídeo.

## O fato

A Nvidia liberou o PersonaPlex, um modelo de voz aberto com 7 bilhões de parâmetros.

Ele ouve e fala ao mesmo tempo e aceita interrupções. Você pode baixar, ver como funciona e rodar no seu computador, sem pagar.

Fonte: <https://github.com/NVIDIA/personaplex>

## Os números

- 7 bilhões de parâmetros.
- 18 vozes prontas.
- Mais de 12 mil estrelas no repositório oficial do GitHub.

## O que muda para você

Se você interrompe no meio da frase, ele para e responde na hora. Ele também solta um 'uhum' enquanto você fala e entende as suas pausas.

Você escolhe uma das 18 vozes prontas e escreve o papel que a IA vai assumir na conversa, como professor simpático ou atendente de restaurante.

Fonte: <https://research.nvidia.com/labs/adlr/personaplex/>

## O que fazer hoje

1. Abra o repositório oficial da Nvidia no GitHub e siga a instalação passo a passo. Resultado: o modelo fica pronto para rodar no seu computador.
2. Se faltar memória da placa, rode o servidor com a opção --cpu-offload. Resultado: parte do trabalho passa para o processador.

```
--cpu-offload
```

Fonte: <https://github.com/NVIDIA/personaplex>

## O que conferir

O modelo foi treinado para conversar em inglês.

Ele precisa de placa de vídeo. Sem memória suficiente, a opção de offload para o processador ajuda, mas o texto não traz desempenho.

Fonte: <https://huggingface.co/nvidia/personaplex-7b-v1>
