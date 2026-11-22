# Como fazer o Jev funcionar como seu modelo de decisão

_2026-11-22 · tutorial_

Este guia mostra como montar, em 8 passos, um modelo de decisão no estilo do Jev a partir de um modelo de linguagem aberto. Ele lê um texto e uma lista de perguntas e devolve probabilidades calibradas em uma única passada. O exemplo do tutorial é o CatDecide, um modelo para catalão treinado com adaptadores LoRA. Serve para quem programa em Python e quer classificar, rotear ou decidir com uma confiança que dá para medir.

## O que você precisa

Quatro itens antes de começar.

- Python com torch, transformers e peft
- Uma GPU de 24 GB ou menos
- Exemplos rotulados do seu problema, com situação, pergunta e resposta certa
- Um modelo base aberto, de licença permissiva: huggingface.co/BSC-LT/salamandra-2b-instruct

```
pip install -U torch transformers peft
```

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Passo 1: escolha o modelo base

Decida o modelo antes de qualquer treino. O método lê uma só posição da saída, então o modelo precisa atender a quatro critérios. Confira licença, tokenizador, modo de raciocínio e tamanho com HfApi e AutoTokenizer.

- Licença permissiva, como Apache 2.0 ou MIT.
- Cada letra de A a Z vira exatamente 1 token depois do template de chat.
- Se o modelo tem modo de raciocínio, você precisa conseguir desligá-lo, porque a resposta sai no primeiro token depois do prompt.
- O modelo cabe em uma única GPU.
- Se uma letra virar mais de um token, ou o modelo só responder depois de pensar, troque de modelo.

```
BSC-LT/salamandra-2b-instruct
```

Fonte: <https://huggingface.co/BSC-LT/salamandra-2b-instruct>

## Passo 2: monte o dataset

A qualidade do modelo vem quase toda dos dados. Crie um arquivo .jsonl com um exemplo por linha, com os campos state, question e gold. Misture fontes: regras calculadas por código, exemplos de modelos professores, bases públicas e textos com ataques plantados.

Se todo exemplo tem resposta, o modelo não aprende a dizer que não dá para saber. Inclua casos em que a frase da resposta foi removida do texto.

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Passo 3: monte o prompt com delimitadores

A função montar_prompt cerca o state com delimitadores gerados por hash SHA-256 do texto mais um salt aleatório, sorteado quando o servidor inicia. Quem escreve o texto não consegue adivinhar o delimitador e fechar a seção por conta própria, o que protege contra prompt injection.

A função ids_dos_codigos extrai o id de token de cada letra, depois do template de chat. Se algum id faltar, volte ao passo 1 e confira o tokenizador.

```
ids_dos_codigos
```

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Passo 4: treine com LoRA e perda restrita

No loop de fine-tuning com peft, calcule a entropia cruzada só sobre as letras-código do exemplo, em vez de olhar o vocabulário inteiro. Embaralhe as alternativas a cada passo para o modelo não decorar posições. Ao final, funda o adaptador no modelo.

A taxa de aprendizado é 1e-4, por 2 épocas. Se o treino ficar viciado em uma letra, confira se o embaralhamento das alternativas está ativo.

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Passo 5: repita o treino e tire a média

Treine 6 vezes mudando só a semente, de 0 a 5. Some os pesos dos 6 modelos em float32, percorrendo named_parameters(), e divida por 6. A técnica se chama sopa de modelos: a pontuação sobe e a inferência não custa nada a mais, porque você fica com um único modelo, do mesmo tamanho dos anteriores.

Pesos compartilhados entre embedding e saída entram na soma uma vez só, para não duplicar.

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Passo 6: calibre temperatura e limiar

Num conjunto de desenvolvimento separado do treino, ajustar_temperatura minimiza a entropia cruzada, com uma temperatura para cada tipo de pergunta, aplicada antes de transformar os números em probabilidades. Assim a confiança declarada combina com a taxa de acerto. Depois, limiar_para acha o corte de confiança acima do qual a taxa de erro fica em até 1%.

Se o seu não cair, confira se o conjunto de desenvolvimento está separado do treino.

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Passo 7: valide com bootstrap pareado

A função bootstrap_pareado, escrita em NumPy, compara duas versões do modelo no mesmo conjunto de teste.

Skill é o acerto descontado do acaso: (acerto − chance) / (1 − chance). Fixe a regra de aprovação antes de rodar cada experimento. Se o intervalo incluir o zero, a melhora não está provada e você mantém a versão anterior.

```
bootstrap_pareado
```

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>
