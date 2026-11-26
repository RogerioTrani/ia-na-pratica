# Como fazer o Jev funcionar como seu modelo de decisão

_2026-11-22 · tutorial_

Este tutorial mostra como transformar um modelo de linguagem aberto em um modelo de decisão no estilo do Jev, da TypeSafe AI, que lê um texto e uma lista de perguntas e devolve probabilidades calibradas em uma única passada, sem gerar texto nem usar parsers de regex. Você vai escolher o modelo base, montar o dataset, treinar com LoRA, repetir o treino e tirar a média, calibrar a confiança, validar com bootstrap pareado e ler cada resposta em quatro ordens. No fim, terá um modelo treinado, calibrado e testado, pronto para classificar, rotear ou decidir com uma confiança que dá para medir. Serve para quem já programa em Python e quer aplicar IA a decisões do dia a dia.

## O que você terá no fim

Um modelo de decisão que recebe uma situação, em texto ou JSON, e uma lista de perguntas tipadas, e devolve uma distribuição de probabilidade calibrada para cada pergunta, em uma única passada pelo modelo, sem gerar texto e sem precisar interpretar a resposta com regex. O exemplo do tutorial é o CatDecide, um modelo para catalão, treinado sobre o Prelude-9B com adaptadores LoRA. O método serve para quem já programa em Python e quer classificar, rotear ou decidir com uma confiança que dá para medir.

O resultado final é um modelo treinado, calibrado e testado, que responde perguntas de escolha, de sim ou não e de nota. Esta apostila reúne os passos, os conceitos e as armadilhas para você seguir sozinho.

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Como isso funciona: do texto à probabilidade

Um modelo de decisão do estilo System One não escreve prosa. Ele recebe um state, que pode ser um texto ou um JSON, e uma lista de perguntas tipadas, e devolve distribuições de probabilidade calibradas em uma única passada, sem usar generate() nem parsers de regex. A ideia central é o truque dos logits: cada alternativa recebe um código de um único token, como A, B ou C, e o sistema lê apenas os logits da posição imediatamente seguinte ao prompt para esses códigos e aplica softmax somente sobre eles.

Isso faz com que a resposta saia no primeiro token depois do prompt, o que permite medir a confiança de cada alternativa de forma direta. O modelo base precisa ser aberto e de licença permissiva, e cada letra usada como código precisa virar exatamente um token depois do template de conversa.

O conceito foi apresentado pela TypeSafe AI com o nome Jev, dentro da família System One de modelos de decisão. A apresentação oficial do System One e do Jev está disponível no site da TypeSafe AI.

Fonte: <https://typesafe.ai/blog/introducing-system-one-models-and-jev>

## Os três tipos de pergunta

O modelo responde três tipos de pergunta, cada um com uma forma própria de extrair a probabilidade dos logits do primeiro token.

Choice, ou escolha: seleciona uma entre K opções, de 2 a 255. Quando há mais de 26 opções, o sistema avalia em grupos de 20 e leva os 3 melhores de cada grupo para uma rodada final. Noul, ou booleano: pergunta de sim ou não. Para mitigar o viés de posição, que é a preferência pela letra A, o servidor lê duas vezes, invertendo a ordem de sim e não, e tira a média. Score, ou nota: escala ordenada de 2 a 10 níveis, e a resposta final é extraída pela mediana da distribuição acumulada, no ponto em que a soma passa de 50%, o que reduz erros graves de distância.

- Choice (escolha): 1 entre K opções, de 2 a 255. Acima de 26 opções, avalia em grupos de 20 e leva os 3 melhores de cada grupo para a rodada final.
- Noul (booleano): sim ou não. Lê duas vezes invertendo a ordem e tira a média, para mitigar o viés de posição.
- Score (nota): escala ordenada de 2 a 10 níveis. A resposta final é a mediana da distribuição acumulada, onde a soma passa de 50%.

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## A leitura direta de logits

Cada alternativa recebe um código de um único token, como A, B, C e assim por diante. O sistema lê apenas os logits da posição imediatamente seguinte ao prompt para esses códigos específicos e aplica softmax somente sobre eles. Por isso, a resposta sai no primeiro token depois do prompt, e a confiança de cada alternativa pode ser medida de forma direta.

Essa leitura direta é o que permite responder em uma única passada e sem gerar texto. Ela também exige que o modelo base tenha um tokenizador em que cada letra de A a Z vire exatamente um token depois do template de chat. Se alguma letra render dois tokens, o método não funciona e é preciso trocar de modelo.

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Proteção contra prompt injection

O texto de entrada, o state, é encapsulado entre delimitadores dinâmicos, como <<7F3A21>>, gerados a partir de um hash SHA-256 do próprio texto somado a um salt aleatório sorteado na inicialização do servidor. Quem escreve o texto não consegue adivinhar o delimitador e fechar a seção por conta própria, o que protege contra prompt injection.

No script, a função montar_prompt cerca o state com esses delimitadores, e a função ids_dos_codigos extrai o id de token de cada letra, já depois do template de conversa. O resultado esperado é ver o texto entre delimitadores parecidos com o exemplo e uma lista de identificadores, um por letra. Se algum identificador faltar, volte à escolha do modelo base e confira o tokenizador.

```
ids_dos_codigos
```

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Antes de começar

Você precisa ter em mãos os seguintes itens antes de começar a treinar.

- Python com as bibliotecas torch, transformers e peft instaladas, com o comando do bloco no fim desta seção.
- Uma GPU de 24 GB ou menos, suficiente para um modelo pequeno com LoRA.
- Exemplos rotulados do seu problema, cada um com a situação, a pergunta e a resposta certa.
- Um modelo base aberto, de licença permissiva, como o sugerido no primeiro passo.
- Um conjunto de desenvolvimento separado do treino, para calibrar e validar.
- Um conjunto de teste separado, para medir o resultado final.

```
pip install -U torch transformers peft
```

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Escolha do modelo base: quatro critérios

Escolha o modelo base antes de qualquer treino. Use quatro critérios. Primeiro, a licença deve ser permissiva, como Apache 2.0 ou MIT. Segundo, cada letra usada como código de alternativa precisa virar exatamente um token depois do template de conversa. Terceiro, se o modelo tem modo de raciocínio, você precisa conseguir desligá-lo, porque a resposta sai no primeiro token depois do prompt. Quarto, ele tem que caber em uma única GPU, para manter respostas abaixo de 150 ms.

Esses critérios existem porque o método lê só uma posição da saída. Você deve ver as letras com um token cada. Se alguma letra render dois tokens, troque de modelo. O modelo sugerido no tutorial é o BSC-LT/salamandra-2b-instruct, disponível no Hugging Face.

Para verificar o modelo, use HfApi e AutoTokenizer e confira licença, contagem de tokens por palavra e token único para cada letra de A a Z.

- Licença permissiva: Apache 2.0 ou MIT.
- Tokenizador: cada letra-código de A a Z vira exatamente 1 token depois do template de chat, com baixa taxa de tokens por palavra no idioma alvo.
- Modo de raciocínio desativável: modelos com thinking precisam permitir o desligamento, pois a resposta sai no primeiro token pós-prompt.
- Orçamento de hardware: o modelo deve caber em uma única GPU, como uma H100 ou GPU de 24 GB, para manter respostas abaixo de 150 ms.

```
BSC-LT/salamandra-2b-instruct
```

Fonte: <https://huggingface.co/BSC-LT/salamandra-2b-instruct>

## Passo a passo

Siga os oito passos na ordem. Cada um diz a ação e o resultado esperado, para você saber se deu certo.

1. Passo 1, escolher o modelo base: confira licença, tokenizador, modo de raciocínio e tamanho com HfApi e AutoTokenizer. Resultado esperado: licença permissiva e cada letra de A a Z vira exatamente 1 token após o template de chat. Erro comum: se uma letra virar mais de um token, ou o modelo só responder depois de pensar, troque de modelo.
2. Passo 2, montar o dataset em linhas de texto: crie um arquivo .jsonl com um exemplo por linha, com os campos state, question e gold. Resultado esperado: um arquivo com um exemplo por linha, cada um com situação, pergunta e resposta certa. Erro comum: se todo exemplo tem resposta, o modelo não aprende a dizer que não dá para saber, então inclua casos em que a frase da resposta foi removida do texto.
3. Passo 3, montar o prompt com delimitadores: no script, montar_prompt cerca o state com delimitadores gerados por hash SHA-256 do texto mais um salt aleatório, e ids_dos_codigos extrai o id de token de cada letra. Resultado esperado: o texto aparece entre delimitadores como <<7F3A21>>, e você tem o id de token de cada letra. Se algum identificador faltar, volte ao passo 1 e confira o tokenizador.
4. Passo 4, treinar com LoRA e perda restrita: no loop de fine-tuning com peft, calcule a entropia cruzada só sobre as letras-código e, ao final, funda o adaptador. Resultado esperado: no CatDecide, só 0,48% dos parâmetros, 43,6 milhões, são treinados, com taxa de aprendizado de 1e-4 por 2 épocas. Se o treino ficar viciado em uma letra, confira se o embaralhamento das alternativas está ativo.
5. Passo 5, repetir o treino e tirar a média: treine 6 vezes mudando só a semente e some os pesos em float32 percorrendo named_parameters(). Resultado esperado: um único modelo, média dos 6 treinos, com pontuação maior e sem custo extra na inferência. Erro comum: some cada peso compartilhado, de embedding e de saída, uma vez só, para não duplicar.
6. Passo 6, calibrar a temperatura e o limiar: num conjunto de desenvolvimento, ajustar_temperatura minimiza a entropia cruzada e limiar_para acha o corte de confiança. Resultado esperado: no exemplo do tutorial, o erro de calibração caiu de 0,13 para 0,03. Se não cair, confira se o conjunto de desenvolvimento é separado do treino.
7. Passo 7, validar com bootstrap pareado: compare duas versões do modelo com a função bootstrap_pareado, em NumPy, usando a métrica Skill. Resultado esperado: a diferença de skill entre as versões, com intervalo de confiança de 95% em 10.000 sorteios. Se o intervalo incluir o zero, a melhora não está provada, então mantenha a versão anterior.
8. Passo 8, ler a resposta em quatro ordens: na inferência, use ler_em_ordens para ler cada pergunta de escolha rotacionando as alternativas. Resultado esperado: probabilidades médias das 4 leituras, uma por alternativa. Se uma letra dominar sempre, revise o passo de embaralhamento no treino.

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Montagem do dataset

A qualidade do modelo vem quase toda dos dados. Crie um arquivo de texto com um exemplo por linha, e em cada linha guarde a situação, a pergunta e a resposta certa, com os nomes dos campos que aparecem abaixo. Esse formato existe para que o treino leia tudo de forma simples. Misture fontes: regras calculadas por código, exemplos de modelos professores, bases públicas e até textos com ataques plantados.

Você deve ter um arquivo com uma linha por exemplo. Um tropeço comum é todo exemplo ter resposta. Então o modelo nunca aprende a dizer que não dá para saber. Inclua casos em que a frase da resposta foi removida do texto.

```
state, question, gold
```

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Curadoria e engenharia de dados

A qualidade do modelo reside quase integralmente nos dados. O dataset final do CatDecide abrangeu 213.561 exemplos e 321 famílias de perguntas, sendo 66,8% em catalão, 22,8% em espanhol e 10,4% em inglês, divididos em cinco fontes.

Os dados vêm de cinco fontes, cada uma com volume e metodologia próprios, como descrito abaixo.

- Calculados por código: 86.910 exemplos, 40,7%. Regras determinísticas, como prazos em dias úteis com feriados municipais, taxas, gramática catalã com erros injetados, geografia de 73 bairros e roteamento. Validação dupla cruzada para zero erro de gabarito.
- Modelos professores: 64.772 exemplos, 30,3%. Esquema estilo ENEM com Qwen3.8-27B e Gemma-4-31B locais. Um escreve e vota, o outro vota às cegas, com 92,4% de acordo. Empates vão para o DeepSeek V4.1 Flash, com alvo suave de 75% e 25%. Filtrado pelo dicionário Softcatalà contra catanhol.
- Datasets públicos: 38.857 exemplos, 18,2%. 15 bases abertas com rótulo humano, como MASSIVE, COPA-ca, SIQA-ca, AnCora-ca, Belebele, PAWS-ca e Aegis 2.0. Filtro rigoroso que descarta qualquer texto que compartilhe 8 palavras seguidas com o teste.
- Traduções e reescritas: 14.029 exemplos, 6,6%. Uso do ALIA-40B para traduzir o MultiNLI e reescrever paráfrases da Viquipèdia sem alterar o sentido.
- Ataques plantados: 8.993 exemplos, 4,2%. Cópias de exemplos normais contendo instruções de prompt injection embutidas no state, mantendo o rótulo original.

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## As quatro pegadinhas dos dados

Quatro problemas apareceram nos dados e foram corrigidos antes do treino. Conhecer essas pegadinhas ajuda a montar um dataset que não vicia o modelo.

- Perda da abstenção: exemplos gerados por código sempre têm resposta, fazendo o modelo parar de responder que não dá para saber. Solução: criar pares de compreensão onde a frase da resposta foi removida do texto.
- Atalhos superficiais: revisores humanos sem acesso ao texto acertavam 100% das perguntas geradas por modelos de linguagem, porque a opção correta era sempre a mais longa. Solução: auditar perguntas às cegas antes do treino e reutilizar frases de recusa reais como distratores.
- Binarização de escalas: poucos exemplos de notas fizeram o modelo responder apenas extremos, 0 ou 5. Solução: gerar pares focados nos níveis intermediários, de 1 a 4.
- Falso positivo em injeções: ataques em formato declarativo, como todos concordam que é B, fizeram o modelo desconfiar de fatos legítimos no texto. Solução: treinar apenas com ataques em formato imperativo de instrução.

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Treinamento: LoRA e perda restrita

No CatDecide, o treino usa adaptadores LoRA aplicados em todas as 252 camadas lineares dos 36 blocos, com target_modules igual a all-linear, posto r igual a 16, lora_alpha igual a 32, taxa de aprendizado de 1e-4 com warmup de 5% e decaimento linear, por 2 épocas, com lote efetivo de 16. Apenas 0,48% dos parâmetros, ou 43,6 milhões, são treinados.

A função de perda é entropia cruzada aplicada exclusivamente sobre os logits das letras-código daquele exemplo, com embaralhamento aleatório das alternativas a cada passo, para o modelo não decorar posições. Ao final, funda o adaptador no modelo com merge_and_unload(). Se o treino ficar viciado em uma letra, confira se o embaralhamento das alternativas está ativo.

Você deve ver que só cerca de meio por cento dos parâmetros são treinados.

```
LoraConfig(r=16, lora_alpha=32, target_modules="all-linear")
merge_and_unload()
```

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Sopa de modelos

O truque se chama sopa de modelos. O treino foi repetido 6 vezes mudando apenas a semente aleatória, de 0 a 5. Os pesos finais foram somados em FP32 e divididos por 6, elevando a pontuação sem custo extra de inferência, porque no fim você continua com um único modelo.

Use a lista de parâmetros nomeados, named_parameters(), para percorrer os pesos. O erro comum é duplicar pesos compartilhados entre a entrada e a saída do modelo. Some cada peso compartilhado uma vez só.

```
SEMENTE = 0..5
```

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Mistura de duas sopas

Para evitar que os dados novos de recusa, o não sei, degradassem o benchmark de ambiguidade CaBBQ, foi feita no CatDecide uma média de 50% e 50% entre a sopa completa, com 214 mil exemplos, e a sopa âncora anterior, com 153 mil exemplos. O resultado é a média de 12 modelos. Use essa mistura quando perceber que os dados novos pioram um benchmark que você quer preservar.

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Calibração da confiança

Calibre o modelo num conjunto separado, o de desenvolvimento. Procure, para cada tipo de pergunta, a temperatura que minimiza a entropia cruzada. No CatDecide, um grid search encontrou as temperaturas ideais: 1,58 para Choice, 2,27 para Noul e 1,19 para Score. Aplique a temperatura antes de transformar os números em probabilidades. Isso existe para que a confiança declarada combine com a taxa de acerto. A calibração reduziu o erro de calibração de 0,13 para 0,03.

Depois, use limiar_para para definir o limiar decidida, acima do qual a taxa de erro fica em até 1%. No exemplo, esse limiar foi de 98,7% para Choice. Se o erro não cair, confira se o conjunto de desenvolvimento é separado do treino.

```
ajustar_temperatura
limiar_para
```

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Validação estatística com bootstrap

Valide cada mudança com estatística. A métrica usada é a Skill, que é o acerto descontado do acaso: acerto menos chance, dividido por um menos chance. Use bootstrap pareado com 10.000 sorteios e intervalo de confiança de 95% para comparar duas versões do modelo no mesmo conjunto de teste, com a função bootstrap_pareado, escrita em NumPy. Ela sorteia as amostras com reposição e dá o intervalo de confiança da diferença.

Fixe a regra de aprovação antes de rodar cada experimento. Se o intervalo de confiança incluir o zero, a melhora não está provada e você mantém a versão anterior. No desempenho competitivo, entre 17 modelos abertos avaliados, o CatDecide ficou em primeiro lugar em Encaminhamento Administrativo, com 77,9 de skill, e em Resistência a Ataques, aceitando apenas 7,2% contra 11,6% do segundo colocado e 33,6% do Jev 1.14 fechado.

```
bootstrap_pareado
```

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Leitura em quatro ordens em produção

Na inferência, use ler_em_ordens para ler cada pergunta de escolha quatro vezes, girando a ordem das alternativas a cada leitura. Depois, tire a média das probabilidades das quatro passadas. Isso existe para eliminar o viés de posição que sobrar, o gosto do modelo pela primeira letra. Nas perguntas de sim ou não, o servidor lê duas vezes, invertendo as opções.

Ponha o texto da situação no começo do prompt: o servidor o processa uma vez para todas as perguntas. Você deve ver uma probabilidade por alternativa, somando 100%. Se uma letra dominar sempre, revise o passo de embaralhamento no treino.

```
ler_em_ordens
```

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Arquitetura de produção e latência

Em produção, o modelo roda com vLLM e usa prefix caching. O state é posicionado no início do prompt. Ao enviar 20 perguntas sobre um mesmo documento de 4.000 tokens em uma GPU H100 via vLLM, o servidor processa o texto uma única vez, resolvendo todas as 20 decisões em 336 ms, ou 137 ms se o texto já estiver em cache.

Cada pergunta do tipo Choice é lida 4 vezes rotacionando a ordem das alternativas, e as probabilidades resultantes são médias das quatro passadas, para eliminar qualquer viés posicional residual.

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Exemplo completo: CatDecide

Imagine que você quer um modelo que decide sobre textos em catalão. O CatDecide serve de exemplo: um modelo de decisão aberto focado em catalão, construído sobre o Prelude-9B no Barcelona Supercomputing Center, treinado com adaptadores LoRA sobre 213.561 exemplos de 321 famílias de perguntas.

O fluxo completo foi: escolher o modelo base aberto, montar o dataset com state, question e gold, montar o prompt com delimitadores gerados por hash SHA-256 mais salt, treinar com LoRA e perda restrita às letras-código, repetir o treino seis vezes e tirar a média, calibrar a temperatura e o limiar num conjunto de desenvolvimento, validar com bootstrap pareado e, em uso, ler cada resposta em quatro ordens. O resultado é um modelo que responde em uma passada, com confiança medida.

Exemplo: para classificar se um chamado deve ser encaminhado, o modelo recebe o texto do chamado e a pergunta com as alternativas, e devolve a probabilidade de cada uma, sem gerar texto.

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Teste de pronto

Rode os testes abaixo para saber se o modelo funcionou.

- [ ] Faça uma pergunta de escolha e rode a função de leitura em quatro ordens. Se funcionou, você vê uma probabilidade para cada alternativa, e a mais alta continua a mesma em qualquer que seja a ordem.
- [ ] Teste um ataque: coloque no texto uma instrução mandando escolher uma resposta. Como referência, o CatDecide aceitou apenas 7,2% dos ataques.
- [ ] Confira se as probabilidades somam 100% para cada pergunta.
- [ ] Confira se o erro de calibração caiu no conjunto de desenvolvimento (no CatDecide, de 0,13 para 0,03).
- [ ] Confira se o intervalo de confiança do bootstrap pareado não inclui o zero para a melhora que você quer manter.

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Erros comuns e cuidados

Confira os pontos abaixo antes de confiar no modelo.

- Se uma letra virar mais de um token, ou o modelo só responder depois de pensar, troque de modelo base.
- Se todo exemplo tem resposta, o modelo não aprende a dizer que não dá para saber: inclua casos em que a frase da resposta foi removida do texto.
- Se o treino ficar viciado em uma letra, confira se o embaralhamento das alternativas está ativo.
- Some cada peso compartilhado, de embedding e de saída, uma vez só, para não duplicar.
- Se o erro de calibração não cair, confira se o conjunto de desenvolvimento é separado do treino.
- Se o intervalo de confiança do bootstrap incluir o zero, a melhora não está provada: mantenha a versão anterior.
- Se uma letra dominar sempre na inferência, revise o passo de embaralhamento no treino.
- O CatDecide usa dados em catalão, espanhol e inglês. Para outro idioma, confira a taxa de tokens por palavra no tokenizador.
- A taxa de erro de 1% vale acima do limiar decidida, como 98,7% para Choice. Abaixo desse limiar, a confiança não garante essa taxa.

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Glossário

- State: a situação que o modelo avalia, em texto ou JSON.
- Gold: o campo do dataset com a resposta certa.
- Logits: os números que o modelo calcula para cada token antes de virarem probabilidades.
- Softmax: a operação que transforma esses números em probabilidades.
- LoRA: adaptadores que treinam só uma pequena parte dos parâmetros.
- Temperatura: ajuste aplicado antes do cálculo das probabilidades, para calibrar a confiança.
- Prompt injection: instrução plantada no texto para desviar a resposta do modelo.
- Skill: acerto descontado do acaso.
- Prefix caching: reaproveitamento do começo do prompt já processado.

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>

## Para onde ir depois

O tutorial em que esta apostila se baseia foi publicado em 9 de novembro de 2026 e republicado no portal iMasters em 10 de novembro de 2026. Os scripts completos em Python, com torch, transformers e peft, estão no final do artigo original. Há também uma versão em inglês.

- Texto em português: https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/
- Versão em inglês: https://fabriciocarraro.com.br/posts/how-to-train-your-own-decision-model-jev-using-an-llm/
- Republicação no iMasters: https://imasters.com.br/inteligencia-artificial/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm
- Troque os dados do exemplo pelos do seu problema e repita calibração, validação e teste.

Fonte: <https://fabriciocarraro.com.br/posts/como-treinar-o-seu-proprio-modelo-de-decisao-jev-usando-um-llm/>
