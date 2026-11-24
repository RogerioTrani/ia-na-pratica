# Guia hands-on MoE com 378 curtidas no Hugging Face

_2026-11-23 · tutorial_

The Ultimate MoE Training Handbook é um guia da Hugging Face sobre como treinar modelos Mixture-of-Experts em escala, uma configuração por vez, com as execuções que sustentam cada escolha. O guia se apoia em 800 mil horas de GPU e tem 55 figuras interativas. Esta apostila mostra como abrir o guia, navegar por ele, ler os resultados e levar o estudo para a prática no Hugging Face Jobs e no Megatron-LM.

## O que é o handbook

O guia mostra como treinar um modelo Mixture-of-Experts em escala, configuração por configuração. Cada escolha vem com as execuções que a sustentam, então você vê o resultado medido de cada decisão, não só o conceito.

O material soma 800 mil horas de GPU e 55 figuras interativas. O Space já passa de 630 curtidas no Hugging Face.

Fonte: <https://huggingface.co/spaces/huggingface/moe-blogpost>

## Passo 1: abra o guia

O guia está publicado como um Space no Hugging Face. Deixe a página aberta enquanto segue os próximos passos e use-a como referência para as escolhas de treinamento que os autores apresentam.

Fonte: <https://huggingface.co/spaces/huggingface/moe-blogpost>

## Passo 2: escolha como navegar

- Para ir direto a um assunto, clique na seção que quer estudar no sumário.
- Para ler em ordem, role a página do começo ao fim.

Fonte: <https://huggingface.co/spaces/huggingface/moe-blogpost>

## Passo 3: compare cada configuração com as execuções

Em cada escolha de treinamento, olhe o gráfico e as execuções que sustentam aquela decisão. São 800 mil horas de GPU por trás desses resultados. Volte ao sumário sempre que precisar ir para outra seção.

Fonte: <https://huggingface.co/spaces/huggingface/moe-blogpost>

## Passo 4: teste a GPU no Hugging Face Jobs

Este comando roda um teste rápido de GPU no Hugging Face Jobs e mostra o nome da placa que você recebeu.

```
hf jobs run --name gpu-check --flavor a10g-small pytorch/pytorch:2.6.0-cuda12.4-cudnn9-devel python -c "import torch; print(torch.cuda.get_device_name())"
```

Fonte: <https://huggingface-moe-blogpost.hf.space/>

## Passo 5: reproduza os treinos do guia

Os autores treinaram com o Megatron-LM da NVIDIA fixado em um commit específico, junto com os scripts de treino que eles mesmos publicaram. Use o mesmo commit e os mesmos scripts. Depois, compare o seu resultado com a escolha que você estudou no guia.

- Repositório: https://github.com/NVIDIA/Megatron-LM
- Commit: d6316eb45bf1bfbb6f1f848c0b56e55166564d80
- Scripts dos autores: https://gist.github.com/nmntz/5de952d686f66d7bce5bce8cba9d7139

```
d6316eb45bf1bfbb6f1f848c0b56e55166564d80
```

Fonte: <https://huggingface-moe-blogpost.hf.space/>

## Além do vídeo

- Os autores do handbook são Nouamane Tazi, Leandro von Werra e Thomas Wolf, da Hugging Face.
- O guia foi publicado em 5 de novembro de 2026.
