# Guia hands-on MoE com 378 curtidas no Hugging Face

_2026-11-23 · tutorial_

The Ultimate MoE Training Handbook é um guia da Hugging Face sobre como treinar modelos Mixture-of-Experts em escala, uma configuração por vez, com as execuções que sustentam cada escolha. O guia se apoia em 800 mil horas de GPU e tem 55 figuras interativas. Esta apostila mostra como abrir o guia, navegar por ele, ler os resultados e levar o estudo para a prática no Hugging Face Jobs e no Megatron-LM.

## O que você terá no fim

Ao final, você terá o guia aberto e navegado, com a GPU de teste checada no Hugging Face Jobs e o treino de referência pronto para reproduzir com o Megatron-LM no commit indicado. O guia soma 800 mil horas de GPU e 55 figuras interativas. Fonte: https://huggingface.co/spaces/huggingface/moe-blogpost

Fonte: <https://huggingface.co/spaces/huggingface/moe-blogpost>

## Passo a passo

Siga os passos na ordem. Os comandos ficam em seções próprias.

1. abra o guia. O guia está publicado como um Space no Hugging Face. Deixe a página aberta enquanto segue os próximos passos. Resultado esperado: a página do guia está aberta como referência.
2. escolha como navegar. Para ir direto a um assunto, clique na seção que quer estudar no sumário. Para ler em ordem, role a página do começo ao fim. Resultado esperado: você sabe por onde começar a leitura.
3. compare cada configuração com as execuções. Em cada escolha de treinamento, olhe o gráfico e as execuções que sustentam aquela decisão. Resultado esperado: cada decisão tem o resultado medido ao lado.
4. teste a GPU no Hugging Face Jobs. O comando abaixo roda um teste rápido de GPU e mostra o nome da placa que você recebeu. Resultado esperado: o nome da placa aparece no log.
5. reproduza os treinos do guia. Use o Megatron-LM no commit indicado e os scripts de treino dos autores. Depois, compare o seu resultado com a escolha que você estudou no guia. Resultado esperado: você tem o seu resultado para comparar.

Fonte: <https://huggingface-moe-blogpost.hf.space/>

## Testar a GPU no Hugging Face Jobs

Este comando roda um teste rápido de GPU no Hugging Face Jobs e mostra o nome da placa que você recebeu. Fonte: https://huggingface-moe-blogpost.hf.space/

```
hf jobs run --name gpu-check --flavor a10g-small pytorch/pytorch:2.6.0-cuda12.4-cudnn9-devel python -c "import torch; print(torch.cuda.get_device_name())"
```

Fonte: <https://huggingface-moe-blogpost.hf.space/>

## Commit do Megatron-LM

Os autores treinaram com o Megatron-LM da NVIDIA fixado em um commit específico, junto com os scripts de treino que eles mesmos publicaram. Use o mesmo commit e os mesmos scripts. Depois, compare o seu resultado com a escolha que você estudou no guia. Repositório: https://github.com/NVIDIA/Megatron-LM. Scripts dos autores: https://gist.github.com/nmntz/5de952d686f66d7bce5bce8cba9d7139

- Commit: indicado no bloco abaixo.

```
d6316eb45bf1bfbb6f1f848c0b56e55166564d80
```

Fonte: <https://huggingface-moe-blogpost.hf.space/>

## Teste de pronto

Como saber que funcionou. Cada item é verificável.

- [ ] O comando de teste de GPU roda e mostra o nome da placa recebida.
- [ ] Você abriu o guia e chegou a uma seção pelo sumário.
- [ ] Você usa o commit e os scripts indicados ao reproduzir o treino.

Fonte: <https://huggingface.co/spaces/huggingface/moe-blogpost>

## Cuidados e sobre o guia

Os números de horas de GPU e de curtidas são os que o próprio Space informa. Os autores do handbook são Nouamane Tazi, Leandro von Werra e Thomas Wolf, da Hugging Face. O guia foi publicado em 5 de novembro de 2026. Fonte: https://huggingface.co/spaces/huggingface/moe-blogpost

Fonte: <https://huggingface.co/spaces/huggingface/moe-blogpost>
