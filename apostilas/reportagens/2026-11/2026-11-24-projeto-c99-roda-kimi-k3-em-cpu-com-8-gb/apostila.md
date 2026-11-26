# Projeto C99 roda Kimi K3 em CPU com 8 GB

_2026-11-24 · reportagem_

Um modelo com 2,78 trilhões de parâmetros roda em um computador comum, sem placa de vídeo e com apenas 8 GB de RAM, graças ao projeto kimi-k3-in-c, escrito em C 99 puro. Esta apostila explica como isso é possível: a arquitetura de mistura de especialistas, a quantização de 4 bits, a leitura sob demanda do disco e as quatro reduções que levam o modelo de um cluster a um laptop. Você também verá os números reais de consumo, velocidade e armazenamento, além dos comandos para compilar e testar o motor. Ao final, saberá avaliar se vale a pena rodar um modelo gigante na sua máquina e quais cuidados tomar.

## O contexto

O kimi-k3-in-c é um motor de inferência open source, escrito em C 99 portável, sem BLAS, sem framework e sem GPU. Ele roda o modelo Kimi K3, com 2,78 trilhões de parâmetros, em uma única CPU, com pico medido de 8,24 GB de RAM.

Modelos dessa escala normalmente exigem clusters de GPUs. Este projeto mostra que otimização extrema de sistemas pode democratizar o acesso a modelos gigantescos, mantendo a mesma resposta em qualquer máquina.

O truque central é não carregar todos os pesos na RAM. O motor lê do disco e processa sob demanda, mantendo apenas os componentes ativos. Os 1,45 TB de especialistas roteados nunca ficam residentes e são multiplicados direto da forma compactada em 4 bits.

O repositório está sob licença Apache 2.0, na versão 2.0.0, com suporte a Linux, macOS e Windows e CI público. A fonte oficial é github.com/FareedKhan-dev/kimi-k3-in-c.

Fonte: <https://github.com/FareedKhan-dev/kimi-k3-in-c>

## O projeto: C 99 puro, sem frameworks

O motor é escrito em C 99 portável: sem PyTorch, sem TensorFlow, sem bibliotecas BLAS. Tudo feito à mão, com controle total do hardware e da memória.

O motor inteiro ocupa 176 KB. A portabilidade cobre Linux, macOS e Windows.

Dá para compilar e rodar a suíte de testes do motor em cerca de um minuto, sem baixar o modelo. Os três passos são git clone, make -j e make test.

Fonte: <https://github.com/FareedKhan-dev/kimi-k3-in-c>

## A escala: 2,78 trilhões de parâmetros

2,78 trilhões de parâmetros é uma escala que normalmente exige clusters de GPUs. Aqui ela roda em CPU graças à engenharia do código.

O checkpoint completo ocupa 1,56 TB em disco. Os 1,45 TB de especialistas roteados nunca ficam residentes na RAM.

O pico de memória medido, de 8,24 GB, mostra que dá para rodar um modelo gigante com pouca RAM.

Fonte: <https://github.com/FareedKhan-dev/kimi-k3-in-c>

## Como funciona: MoE e quantização de 4 bits

Mistura de especialistas (MoE): em vez de ativar toda a rede para cada token, o modelo seleciona um subconjunto de especialistas. O projeto escolhe 16 especialistas entre 896.

Os especialistas já vêm em 4 bits no formato MXFP4. Eles são lidos do disco sob demanda e multiplicados direto da forma compactada, sem descompactar na RAM.

Resultado: só os componentes necessários ficam ativos, reduzindo consumo e tráfego de dados.

Fonte: <https://github.com/FareedKhan-dev/kimi-k3-in-c>

## Os números do projeto

O repositório publica uma tabela de métricas medidas. Cada número vem da saída de medição em docs/data/.

- 2,78 trilhões de parâmetros no modelo
- 1,56 TB de checkpoint em disco
- 8,24 GB de pico de RAM (medido)
- 176 KB o motor inteiro
- 0 GPUs usadas
- 1,45 TB de especialistas roteados, nunca residentes

Fonte: <https://github.com/FareedKhan-dev/kimi-k3-in-c>

## O custo em disco: 1,56 TB

Pouca RAM não significa modelo leve. O checkpoint ocupa 1,56 TB em disco e o projeto pede cerca de 1,7 TB livre.

Fonte: <https://github.com/FareedKhan-dev/kimi-k3-in-c>

## A velocidade: cerca de 26 segundos por token

Sem GPU e com 8 GB de RAM, a inferência levou cerca de 26 segundos por token (26,5 s por token na faixa de 8 GB da tabela do repositório).

Um token é aproximadamente um pedaço curto de palavra.

Mais memória só compra velocidade: o modelo é o mesmo e a resposta é a mesma.

Fonte: <https://github.com/FareedKhan-dev/kimi-k3-in-c>

## RAM versus velocidade: a tabela

O mesmo prompt curto em todas as configurações produz saída byte-idêntica; só o relógio muda.

Todas as faixas foram medidas em uma única máquina, com 124 cores e NVMe rápido. Nela, as três primeiras faixas ainda leem o modelo do disco a cada passo, então disco mais lento significa mais lento. A faixa de 128 GB+ mantém tudo em memória e não espera mais o disco.

- 8 GB de RAM (laptop comum): 26,5 s por token, o modelo inteiro sai do disco a cada passo
- 32 GB de RAM (laptop topo): 24,2 s por token, parte do modelo já fica em memória
- 64 GB de RAM (desktop): 19,8 s por token, mais dele fica em memória
- 128 GB+ de RAM (workstation pesada): 5,6 s por token, o modelo cabe inteiro em memória, sem espera de disco

Fonte: <https://github.com/FareedKhan-dev/kimi-k3-in-c>

## Saída idêntica em qualquer máquina

O mesmo modelo, a mesma resposta, em qualquer máquina que você tiver. Mais memória só compra velocidade.

O modelo roda em 8 GB e em 224 GB e produz saída byte-idêntica em qualquer orçamento entre os dois.

Na mesma máquina, a versão 1.0.0 tornou a matemática por token cerca de 8 vezes mais leve, uma pergunta de acompanhamento no chat 3,9 vezes mais rápida e prompts longos cerca de metade do custo.

Fonte: <https://github.com/FareedKhan-dev/kimi-k3-in-c>

## As quatro reduções que levam um cluster ao laptop

Quatro decisões sobre onde os bytes vivem levam o modelo de um cluster de servidores a um laptop, com a mesma resposta nos dois extremos.

A Parte II do repositório constrói cada componente passo a passo. Os tópicos documentados são os seguintes.

- Leitura do checkpoint de 1,56 TB pelos cabeçalhos
- Leitor de configuração que se recusa a chutar
- Tokenizer byte a byte
- Redução 1: os especialistas já vêm em meio byte (4 bits)
- Kernels com contrato de ponto flutuante
- Redução 2: KDA, atenção com memória que nunca cresce
- Redução 3: MLA, um latente em vez de noventa e seis cabeças
- Resíduos de atenção: camadas que olham para trás
- Escolha de 16 especialistas entre 896
- Empacotamento do trunk: 93 camadas, uma leitura para cada
- Redução 4: streaming do trunk transforma um piso em um dial
- Cache LRU para os especialistas
- Tamanho do cache definido pelo traço

Fonte: <https://github.com/FareedKhan-dev/kimi-k3-in-c>

## Como funciona na prática

O repositório traz dois exemplos rodados. O primeiro usa o preset laptop em uma máquina comum; o segundo usa o preset server em uma máquina com muita RAM. Os dois geram texto, mas em velocidades muito diferentes; o primeiro pede de propósito uma continuação crua, não uma resposta de chat. São as capturas originais, feitas com um disco mais lento, por isso os tempos ficam um pouco acima dos da tabela.

No primeiro, 8 tokens em 261,5 s (média de 32,69 s por token) com pico de 8,24 GB. No segundo, 28 tokens em 299,3 s (média de 10,69 s por token) com pico de 127,92 GB.

```
$ ./bin/k3 ~/k3model --trunk ~/k3trunk --preset laptop \
           --tok ~/k3model --prompt "The capital of France is" --gen 8 --incremental
--- generated text ---
 Paris.",
+            "The Eiffel
----------------------
8 tokens in 261.5 s, 32.69 s/token average
PEAK RSS for the whole run: 8.24 GB
$ ./bin/k3 ~/k3model --trunk ~/k3trunk --preset server \
           --tok ~/k3model --prompt "def fibonacci(n):" --gen 28 --incremental
--- generated text ---
    if n <= 1:
        return n
    else:
        return fibonacci(n-1) + fibonacci
----------------------
28 tokens in 299.3 s, 10.69 s/token average
PEAK RSS for the whole run: 127.92 GB
```

Fonte: <https://github.com/FareedKhan-dev/kimi-k3-in-c>

## Quem ganha e quem perde

Ganham donos de máquinas comuns, que podem rodar um modelo de 2,78 trilhões de parâmetros sem comprar GPU nem cluster. Ganham estudantes e engenheiros de software de baixo nível, que têm uma aula prática de otimização extrema. Ganham pesquisadores que querem reproduzir resultados em hardware modesto.

Perdem quem precisa de resposta rápida: 26 segundos por token em 8 GB é inviável para chat em tempo real. Perdem quem não tem 1,7 TB de disco livre. Perdem quem esperava aceleração por GPU, já que o projeto não usa nenhuma.

A troca é clara: memória e velocidade viram disco e paciência, sem mudar a resposta.

Fonte: <https://github.com/FareedKhan-dev/kimi-k3-in-c>

## O que ainda não se sabe

- Os números vêm da saída de medição em docs/data/; são resultados do repositório, não garantia de desempenho na sua máquina.
- O projeto pede cerca de 1,7 TB livre em disco.
- Sem GPU: toda a inferência é em CPU.
- A velocidade depende do disco: nas três primeiras faixas de RAM o modelo é lido do disco a cada passo, então disco mais lento significa mais lento.
- A saída byte-idêntica entre orçamentos é uma propriedade afirmada pelo projeto; confira nos dados publicados.
- A versão atual é 2.0.0; portes para macOS, Windows e NEON, modo chat e o preset ultra vieram de contribuidores listados no repositório.

Fonte: <https://github.com/FareedKhan-dev/kimi-k3-in-c>

## O que você pode fazer

1. Clone o repositório oficial em github.com/FareedKhan-dev/kimi-k3-in-c.
2. Compile e teste o motor sem baixar o modelo: git clone, make -j, make test (cerca de um minuto).
3. Se quiser gerar texto, provisione cerca de 1,7 TB livre e baixe o checkpoint (1,56 TB); os exemplos também usam uma pasta de trunk (--trunk).
4. Rode com o preset adequado à sua RAM: laptop para 8 GB, server para 128 GB+.
5. Compare seus tempos com a tabela do repositório e consulte docs/data/ para os dados completos.
6. Estude a Parte II do repositório para entender cada redução e replicar a engenharia.
7. Use os comandos de diagnóstico e códigos de saída documentados no repositório para depurar.

Fonte: <https://github.com/FareedKhan-dev/kimi-k3-in-c>

## Glossário

- Parâmetro: peso numérico aprendido pelo modelo durante o treino.
- Inferência: usar o modelo treinado para gerar uma resposta.
- MoE (Mixture of Experts): arquitetura que ativa apenas um subconjunto de especialistas por entrada.
- Especialista: sub-rede dentro de um modelo MoE.
- Quantização: representar pesos com menos bits (aqui, 4 bits).
- MXFP4: formato de 4 bits usado para os especialistas.
- Token: aproximadamente um pedaço curto de palavra.
- Checkpoint: arquivos com os pesos do modelo (aqui, 1,56 TB).
- Trunk: parte densa do modelo, mantida em memória até a profundidade escolhida; o restante é lido do disco em streaming.
- RSS (peak RSS): pico de memória residente usada pelo processo.
- LRU cache: cache que descarta o item menos usado recentemente.
- BLAS: biblioteca de álgebra linear usada por frameworks de ML.
- Apache 2.0: licença open source permissiva.
- NVMe: tipo de SSD rápido, usado para ler o modelo do disco.

## Para onde ir depois

- Repositório oficial: https://github.com/FareedKhan-dev/kimi-k3-in-c
- Dados completos de medição: docs/data/ no repositório
- Parte II do README: construção passo a passo da engenharia
- CONTRIBUTORS.md: quem fez o quê
- Estude a arquitetura para aplicar as técnicas (streaming, cache LRU, quantização) em seus próprios projetos

Fonte: <https://github.com/FareedKhan-dev/kimi-k3-in-c>

## Além do vídeo

- A versão 2.0.0 reúne portes para macOS, Windows e NEON, modo chat, preset ultra, kernels MXFP4 mais rápidos e admissão de memória ciente de cgroup, a maioria contribuída pela comunidade.
- O repositório traz dezenas de contribuidores; CONTRIBUTORS.md detalha quem fez o quê.
- O README também cobre perguntas frequentes, códigos de saída, variáveis de ambiente, exemplos comentados, escolha de preset e leitura do relatório de execução.
