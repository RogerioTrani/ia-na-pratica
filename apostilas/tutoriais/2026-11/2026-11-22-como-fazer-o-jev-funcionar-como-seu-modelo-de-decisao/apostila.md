# Como fazer o Jev funcionar como seu modelo de decisão

_2026-11-22 · tutorial_

Este guia mostra como montar um modelo de decisão no estilo do Jev a partir de um modelo de linguagem aberto. Ele lê um texto e uma lista de perguntas e devolve probabilidades calibradas em uma única passada. O exemplo do tutorial é o CatDecide, um modelo para catalão treinado com adaptadores LoRA. Serve para quem programa em Python e quer classificar, rotear ou decidir com uma confiança que dá para medir.

## O que você terá no fim

Ao final, você terá um modelo de decisão no estilo do Jev, treinado com adaptadores LoRA a partir de um modelo base aberto, com probabilidades calibradas e validadas. O exemplo do tutorial é o CatDecide, um modelo para catalão. Fonte: https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Antes de começar

Quatro itens antes de começar. Instale as bibliotecas com o comando abaixo.

- Python com torch, transformers e peft.
- Uma GPU de 24 GB ou menos.
- Exemplos rotulados do seu problema, com situação, pergunta e resposta certa.
- Um modelo base aberto, de licença permissiva: huggingface.co/BSC-LT/salamandra-2b-instruct

```
pip install -U torch transformers peft
```

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Passo a passo

Siga os passos na ordem. Os nomes de função ficam em seções próprias.

1. escolha o modelo base. Decida o modelo antes de qualquer treino. O método lê uma só posição da saída, então o modelo precisa atender a quatro critérios: licença permissiva, cada letra de A a Z como exatamente 1 token depois do template de chat, modo de raciocínio que dá para desligar e cabe em uma única GPU. Resultado esperado: o modelo base está escolhido e confirmado com HfApi e AutoTokenizer.
2. monte o dataset. Crie um arquivo .jsonl com um exemplo por linha, com os campos state, question e gold. Misture fontes: regras calculadas por código, exemplos de modelos professores, bases públicas e textos com ataques plantados. Resultado esperado: o dataset tem exemplos com e sem resposta.
3. monte o prompt com delimitadores. A função montar_prompt cerca o state com delimitadores gerados por hash SHA-256 do texto mais um salt aleatório. A função ids_dos_codigos extrai o id de token de cada letra, depois do template de chat. Resultado esperado: cada letra tem um id e o prompt fica protegido contra fechamento de seção.
4. treine com LoRA e perda restrita. No loop de fine-tuning com peft, calcule a entropia cruzada só sobre as letras-código do exemplo. Embaralhe as alternativas a cada passo. Ao final, funda o adaptador no modelo. A taxa de aprendizado é 1e-4, por 2 épocas. Resultado esperado: o adaptador fica fundido ao modelo.
5. repita o treino e tire a média. Treine 6 vezes mudando só a semente, de 0 a 5. Some os pesos dos 6 modelos em float32, percorrendo named_parameters(), e divida por 6. A técnica se chama sopa de modelos. Resultado esperado: um único modelo, do mesmo tamanho dos anteriores, com a pontuação maior.
6. calibre temperatura e limiar. Num conjunto de desenvolvimento separado do treino, ajustar_temperatura minimiza a entropia cruzada, com uma temperatura para cada tipo de pergunta. Depois, limiar_para acha o corte de confiança acima do qual a taxa de erro fica em até 1%. Resultado esperado: a confiança declarada combina com a taxa de acerto.
7. valide com bootstrap pareado. A função bootstrap_pareado, escrita em NumPy, compara duas versões do modelo no mesmo conjunto de teste. Skill é o acerto descontado do acaso: (acerto − chance) / (1 − chance). Fixe a regra de aprovação antes de rodar cada experimento. Resultado esperado: você sabe se a melhora está provada.

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Escolher o modelo base

Modelo base usado no tutorial, com licença permissiva. Confira licença, tokenizador, modo de raciocínio e tamanho com HfApi e AutoTokenizer. Se uma letra virar mais de um token, ou o modelo só responder depois de pensar, troque de modelo. Fonte: https://huggingface.co/BSC-LT/salamandra-2b-instruct

- Licença permissiva, como Apache 2.0 ou MIT.
- Cada letra de A a Z vira exatamente 1 token depois do template de chat.
- Se o modelo tem modo de raciocínio, você precisa conseguir desligá-lo, porque a resposta sai no primeiro token depois do prompt.
- O modelo cabe em uma única GPU.

```
BSC-LT/salamandra-2b-instruct
```

Fonte: <https://huggingface.co/BSC-LT/salamandra-2b-instruct>

## Montar o prompt com delimitadores

A função montar_prompt cerca o state com delimitadores gerados por hash SHA-256 do texto mais um salt aleatório, sorteado quando o servidor inicia. Quem escreve o texto não consegue adivinhar o delimitador e fechar a seção por conta própria, o que protege contra prompt injection. Se algum id faltar, volte ao passo 1 e confira o tokenizador. Fonte: https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/

```
ids_dos_codigos
```

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Validar com bootstrap pareado

A função bootstrap_pareado compara duas versões do modelo no mesmo conjunto de teste. Se o intervalo incluir o zero, a melhora não está provada e você mantém a versão anterior. Fonte: https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/

```
bootstrap_pareado
```

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Teste de pronto

Como saber que funcionou. Cada item é verificável.

- [ ] As letras de A a Z têm exatamente 1 token cada no tokenizador do modelo.
- [ ] O treino de 6 sementes foi médiado e gerou um único modelo.
- [ ] A taxa de erro no corte de confiança escolhido fica em até 1% no conjunto de desenvolvimento.
- [ ] O intervalo do bootstrap pareado não inclui o zero, para que a melhora seja considerada provada.

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Cuidados

Se todo exemplo tem resposta, o modelo não aprende a dizer que não dá para saber. Inclua casos em que a frase da resposta foi removida do texto.

Se o treino ficar viciado em uma letra, confira se o embaralhamento das alternativas está ativo. Se o seu corte não cair, confira se o conjunto de desenvolvimento está separado do treino. Fonte: https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>
