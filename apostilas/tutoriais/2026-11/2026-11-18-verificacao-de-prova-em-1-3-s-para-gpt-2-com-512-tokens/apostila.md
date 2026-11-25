# Verificação de prova em 1,3 s para GPT-2 com 512 tokens

_2026-11-18 · tutorial_

DeepProve gera provas zero-knowledge da passagem à frente de LLMs inteiros. Esta apostila leva do build do bench-llm até a verificação da prova do GPT-2 com 512 tokens. No servidor de referência do projeto, a verificação leva 1,3 s e a prova 7,6 min. Ao final, o mesmo fluxo roda no Gemma 3 para comparar a escala.

## O que você terá no fim

Ao final, você terá o bench-llm compilado, a prova de 512 tokens do GPT-2 gerada e verificada, e a mesma medição repetida no Gemma 3 para comparar a escala. O arquivo bench.csv registra o tempo de prova e o tamanho da prova. Fonte: https://github.com/Lagrange-Labs/deep-prove

Fonte: <https://github.com/Lagrange-Labs/deep-prove>

## Antes de começar

Requisitos para seguir o tutorial.

- Instale Rust e Cargo.
- Tenha o repositório do projeto na sua pasta: github.com/Lagrange-Labs/deep-prove.
- Para o GPT-2, não é preciso baixar os pesos à mão: a primeira execução faz o download e guarda em cache.

Fonte: <https://github.com/Lagrange-Labs/deep-prove>

## Passo a passo

Siga os passos na ordem. Cada comando tem a sua seção logo abaixo.

1. compile o bench-llm. Resultado esperado: o programa fica pronto para rodar.
2. prepare o GPT-2. Resultado esperado: os pesos e o tokenizador são baixados e guardados em cache na primeira execução.
3. gere a prova de 512 tokens. Resultado esperado: o comando roda a inferência, gera a prova e já a verifica.
4. leia o tempo de verificação. Resultado esperado: você tem o tempo de verificação e o tempo de prova.
5. compare com o Gemma 3. Resultado esperado: você tem os mesmos indicadores para outro modelo.

Fonte: <https://github.com/Lagrange-Labs/deep-prove/blob/master/zkml/README.md>

## Passo 1: compilar o bench-llm

Na pasta do repositório github.com/Lagrange-Labs/deep-prove, rode o comando abaixo. O zkml é a biblioteca central de provas (quantização do modelo, camadas de transformer, geração e verificação das provas). O bench-llm é o programa que roda o fluxo completo. Fonte: https://github.com/Lagrange-Labs/deep-prove/blob/master/zkml/README.md

```
cargo build --release -p zkml --bin bench-llm
```

Fonte: <https://github.com/Lagrange-Labs/deep-prove/blob/master/zkml/README.md>

## Passo 3: gerar a prova de 512 tokens

O comando monta o contexto de prova, roda a inferência, gera a prova e já a verifica. Para perfilar a divisão distribuída em uma só máquina, acrescente --distributed --num_chunks 4 ao mesmo comando. Modelo: huggingface.co/openai-community/gpt2 (a opção --hf baixa os pesos na primeira execução).

```
cargo run --release --bin bench-llm -- --model gpt2 --hf openai-community/gpt2 --sequence 512
```

Fonte: <https://huggingface.co/openai-community/gpt2>

## Passo 5: comparar com o Gemma 3

Repita o fluxo trocando o modelo. Com 512 tokens, o Gemma 3 leva 19 min para provar e 4,3 s para verificar. O throughput é de cerca de 0,45 tokens/s, contra 1,12 tokens/s do GPT-2. O gargalo está na geração da prova, e a verificação continua rápida. Modelo: huggingface.co/google/gemma-3-1b-it

```
cargo run --release --bin bench-llm -- --model gemma3 --hf google/gemma-3-1b-it --sequence 512
```

Fonte: <https://github.com/Lagrange-Labs/deep-prove/blob/master/zkml/README.md>

## Teste de pronto

Como saber que funcionou. Cada item é verificável.

- [ ] O comando de geração termina e a verificação roda no fim, sem reexecutar a inferência.
- [ ] No servidor de referência do projeto (24 núcleos, 504 GB), o GPT-2 com 512 tokens leva 1,3 s para verificar e 7,6 min para provar. A prova tem cerca de 10,7 MiB.
- [ ] O arquivo bench.csv, na pasta onde você rodou, registra o tempo de prova e o tamanho da prova.

Fonte: <https://github.com/Lagrange-Labs/deep-prove/blob/master/zkml/README.md>

## Cuidados

Com a opção --accuracy e quantização de 12 bits, o GPT-2 mantém ao menos 99,6% de similaridade cosseno em relação ao baseline de ponto flutuante. O projeto reaproveita as implementações de sumcheck e GKR do github.com/scroll-tech/ceno e é licenciado pela Lagrange License. Para auditoria em ambientes regulados, a prova permite checar que a inferência foi executada corretamente sem expor pesos, entradas ou saídas.

Os números de servidor e de tempo são os do servidor de referência do projeto. Gemma 3 com 512 tokens gera prova de 27 MiB, contra 10,7 MiB do GPT-2. Fonte: https://github.com/Lagrange-Labs/deep-prove

Fonte: <https://github.com/Lagrange-Labs/deep-prove>
