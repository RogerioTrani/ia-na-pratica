# Verificação de prova em 1,3 s para GPT-2 com 512 tokens

_2026-11-18 · tutorial_

DeepProve gera provas zero-knowledge da passagem à frente de LLMs inteiros, da embedding ao argmax do próximo token. Esta apostila leva do build do bench-llm até a verificação da prova do GPT-2 com 512 tokens. No servidor de referência do projeto, a verificação leva 1,3 s e a prova 7,6 min. Ao final, o mesmo fluxo roda no Gemma 3 para comparar a escala.

## O que a prova garante

Rodar um modelo não garante que a saída veio de uma execução correta dos pesos. Uma prova zero-knowledge mostra, criptograficamente, que a inferência foi feita como deveria, sem revelar pesos nem entradas.

O DeepProve é o primeiro sistema de prova zero-knowledge de ponta a ponta para inferência completa de LLMs. Usa sumchecks e logup GKR, e o tempo de prova é sublinear no tamanho do modelo. Modelos confirmados: GPT-2, Gemma 3 e Llama 2. Inferência de MLP e CNN também é suportada.

Fonte: <https://github.com/Lagrange-Labs/deep-prove>

## Passo 1: compilar o bench-llm

Instale Rust e Cargo e, na pasta do repositório github.com/Lagrange-Labs/deep-prove, rode o comando abaixo. O zkml é a biblioteca central de provas (quantização do modelo, camadas de transformer, geração e verificação das provas). O bench-llm é o programa que roda o fluxo completo.

```
cargo build --release -p zkml --bin bench-llm
```

Fonte: <https://github.com/Lagrange-Labs/deep-prove/blob/master/zkml/README.md>

## Passo 2: preparar o GPT-2

Você não baixa nada à mão. Na primeira execução, a opção --hf openai-community/gpt2 faz o bench-llm baixar os pesos e o tokenizador e guardar em cache. O suporte cobre o transformador inteiro, das embeddings ao argmax do próximo token.

Modelo: huggingface.co/openai-community/gpt2

Fonte: <https://huggingface.co/openai-community/gpt2>

## Passo 3: gerar a prova de 512 tokens

O comando monta o contexto de prova, roda a inferência, gera a prova e já a verifica.

- Para perfilar a divisão distribuída em uma só máquina, acrescente --distributed --num_chunks 4 ao mesmo comando.

```
cargo run --release --bin bench-llm -- --model gpt2 --hf openai-community/gpt2 --sequence 512
```

Fonte: <https://github.com/Lagrange-Labs/deep-prove/blob/master/zkml/README.md>

## Passo 4: ler o tempo de verificação

O mesmo comando verifica a prova no fim, sem reexecutar a inferência. No servidor de referência do projeto (24 núcleos, 504 GB), o GPT-2 com 512 tokens leva 1,3 s para verificar e 7,6 min para provar. A prova tem cerca de 10,7 MiB.

O arquivo bench.csv, na pasta onde você rodou, registra o tempo de prova e o tamanho da prova. A verificação é muito mais rápida que a geração, o que torna a auditoria viável em escala.

Fonte: <https://github.com/Lagrange-Labs/deep-prove/blob/master/zkml/README.md>

## Passo 5: comparar com o Gemma 3

Repita o fluxo trocando o modelo. Com 512 tokens, o Gemma 3 leva 19 min para provar e 4,3 s para verificar. O throughput é de cerca de 0,45 tokens/s, contra 1,12 tokens/s do GPT-2. O gargalo está na geração da prova, e a verificação continua rápida.

Modelo: huggingface.co/google/gemma-3-1b-it

```
cargo run --release --bin bench-llm -- --model gemma3 --hf google/gemma-3-1b-it --sequence 512
```

Fonte: <https://github.com/Lagrange-Labs/deep-prove/blob/master/zkml/README.md>

## Acurácia, origem do código e licença

Com a opção --accuracy e quantização de 12 bits, o GPT-2 mantém ao menos 99,6% de similaridade cosseno em relação ao baseline de ponto flutuante.

O projeto reaproveita as implementações de sumcheck e GKR do github.com/scroll-tech/ceno e é licenciado pela Lagrange License. Para auditoria em ambientes regulados, a prova permite checar que a inferência foi executada corretamente sem expor pesos, entradas ou saídas.

Fonte: <https://github.com/Lagrange-Labs/deep-prove>

## Além do vídeo

- Gemma 3 com 512 tokens gera prova de 27 MiB, contra 10,7 MiB do GPT-2.
- O Llama 2 também está entre os modelos confirmados, com todas as camadas de transformer provadas de ponta a ponta.
- O projeto informa ser 10 a 30 vezes mais rápido que o estado da arte publicado anteriormente (o zkGPT reporta cerca de 0,05 tokens/s em hardware parecido).
- A distribuição horizontal de provas e a aceleração por GPU já são suportadas, e clusters de workers com GPU estão no roadmap.
