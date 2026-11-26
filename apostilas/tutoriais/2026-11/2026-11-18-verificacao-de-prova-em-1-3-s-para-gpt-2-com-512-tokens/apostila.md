# Verificação de prova em 1,3 s para GPT-2 com 512 tokens

_2026-11-18 · tutorial_

DeepProve é o primeiro sistema end-to-end de prova zero-knowledge para inferência completa de LLMs. Com ele você compila o bench-llm, prepara o GPT-2 ou o Gemma 3, gera a prova da passagem à frente e verifica em segundos, sem expor pesos, entradas ou saídas. A apostila traz cada passo, os comandos exatos, os números reais de prova e verificação e os cuidados para não confundir o que a prova garante. Você termina sabendo o que foi provado, quanto tempo levou e como conferir se funcionou.

## O que você terá no fim

Ao final, você terá rodado o ciclo completo de uma prova zero-knowledge de inferência: compilar o programa de prova, preparar o modelo, gerar a prova e verificar se ela é válida. O exemplo principal usa o GPT-2 com uma sequência de 512 tokens.

Você também terá os números reais de tempo e tamanho de prova para comparar com a sua máquina, além de um segundo modelo, o Gemma 3, para observar como a escala muda.

A prova garante integridade da inferência sem revelar pesos, entradas ou saídas, o que torna auditoria de modelo viável em ambientes regulados.

Fonte: <https://github.com/Lagrange-Labs/deep-prove>

## Como isso funciona

Rodar um modelo não garante que a saída veio de uma execução correta dos pesos. Uma prova zero-knowledge mostra matematicamente que a inferência foi feita como deveria, sem revelar os pesos nem as entradas.

O DeepProve gera provas criptográficas da passagem à frente de redes neurais usando sumchecks e logup GKR. Ele é o primeiro sistema end-to-end de prova para inferência completa de LLMs e alcança tempo de prova sublinear no tamanho do modelo, ordens de magnitude mais rápido que abordagens baseadas em circuitos.

A biblioteca central é o crate zkml: cuida da quantização do modelo, das camadas de transformer e da geração e verificação das provas. O repositório é um workspace Rust; os demais crates formam a pilha de cliente, armazenamento e ferramentas de desenvolvimento.

Modelos confirmados: GPT-2, Gemma 3 e Llama 2, com todas as camadas de transformer provadas de ponta a ponta, das embeddings ao argmax do próximo token. Inferência de MLP e CNN também é suportada.

Fonte: <https://github.com/Lagrange-Labs/deep-prove>

## O que muda para você

Com a prova verificada, um auditor confirma que a inferência foi executada corretamente sem reexecutar o modelo nem ver pesos, entradas ou saídas. Isso ajuda em ambientes regulados e em cenários onde o modelo é aberto mas a execução precisa ser atestada.

Exemplo: uma equipe que disponibiliza um modelo aberto pode entregar a prova junto com a saída, e o cliente verifica em segundos em vez de rodar o modelo inteiro.

Fonte: <https://github.com/Lagrange-Labs/deep-prove>

## Estrutura do repositório

O repositório é um workspace Rust. O crate zkml é a biblioteca de prova central; os demais crates cobrem cliente, armazenamento e ferramentas.

- zkml: biblioteca de prova central, com quantização, camadas (MLP, CNN, transformer) e geração/verificação de provas.
- deep-prove: pilha de cliente; o deep-prove-worker roda um servidor de geração de provas e o deep-prove-cli submete trabalhos localmente ou a uma rede remota de prova.
- tenstore: fachada de armazenamento para persistir e recuperar dados de tensor, com backends local e remoto compatíveis com S3.
- tenvis: ferramenta de linha de comando interativa para inspecionar e depurar dados de prova no tenstore.
- telemetry: configuração compartilhada de rastreamento e log com OpenTelemetry.
- utils: utilitários compartilhados, como registro em CSV, rastreamento de memória e resumos estatísticos.

Fonte: <https://github.com/Lagrange-Labs/deep-prove>

## Escalabilidade e acurácia

O DeepProve escala horizontalmente: a distribuição da prova e a aceleração por GPU são suportadas hoje; clusters de workers com GPU estão no roadmap.

A acurácia se mantém com pelo menos 99,6% de similaridade cosseno em relação ao baseline de ponto flutuante para GPT-2, com quantização de 12 bits e a opção --accuracy ligada.

Em relação ao estado da arte anterior, o projeto se apresenta como 10 a 30 vezes mais rápido; o zkGPT reporta cerca de 0,05 tokens por segundo em hardware similar.

Fonte: <https://github.com/Lagrange-Labs/deep-prove>

## Antes de começar

Confira os requisitos antes de rodar os comandos. Os tempos de referência vêm de um servidor de referência com 24 núcleos e 504 GB.

- Rust e Cargo instalados, pré-requisito para compilar.
- Repositório oficial clonado: https://github.com/Lagrange-Labs/deep-prove.
- Conexão com a internet na primeira execução: o programa baixa os pesos e o tokenizador do modelo no Hugging Face e guarda em cache.
- Espaço em disco para o cache do modelo e para o arquivo bench.csv gerado na pasta onde você rodou.
- Máquina com recursos suficientes para os tempos de prova; em hardware menor os tempos serão diferentes.

Fonte: <https://github.com/Lagrange-Labs/deep-prove/blob/master/zkml/README.md>

## Passo a passo

Siga a ordem. Cada passo diz a ação e o resultado esperado para você saber se deu certo.

1. Compilar o programa de prova: rode o comando de build na pasta do repositório. Resultado esperado: o binário bench-llm fica pronto para uso.
2. Preparar o modelo: na primeira execução, use a opção --hf com o identificador do modelo; o programa baixa os pesos e o tokenizador e guarda em cache. Resultado esperado: cópia local do modelo disponível para as próximas execuções.
3. Gerar a prova: rode o bench-llm com o modelo, o identificador Hugging Face e o comprimento da sequência. O programa monta o contexto de prova, roda a inferência, gera a prova e já a verifica. Resultado esperado: prova gerada e verificada no fim do comando.
4. Ler o tempo de verificação: confirme que a prova é válida sem reexecutar toda a inferência. Resultado esperado: tempo de verificação de segundos e arquivo bench.csv com o tempo de prova e o tamanho da prova na pasta onde você rodou.
5. Testar com outro modelo: repita o fluxo com o Gemma 3 trocando o modelo no comando. Resultado esperado: prova e verificação funcionando em escala maior, com tempos maiores de prova.

Fonte: <https://github.com/Lagrange-Labs/deep-prove/blob/master/zkml/README.md>

## Comando para compilar o bench-llm

Pré-requisito: Rust e Cargo instalados. Rode na pasta do repositório oficial.

```
cargo build --release -p zkml --bin bench-llm
```

Fonte: <https://github.com/Lagrange-Labs/deep-prove/blob/master/zkml/README.md>

## Comando para gerar e verificar a prova com GPT-2

Monta o contexto de prova, roda a inferência, gera a prova e a verifica. Para perfilar a divisão distribuída em uma só máquina, acrescente as opções --distributed e --num_chunks 4 ao comando.

```
cargo run --release --bin bench-llm -- --model gpt2 --hf openai-community/gpt2 --sequence 512
```

Fonte: <https://github.com/Lagrange-Labs/deep-prove/blob/master/zkml/README.md>

## Comando para rodar Gemma 3

Repete o fluxo em outro modelo suportado para observar a escala.

```
cargo run --release --bin bench-llm -- --model gemma3 --hf google/gemma-3-1b-it --sequence 512
```

Fonte: <https://github.com/Lagrange-Labs/deep-prove/blob/master/zkml/README.md>

## Exemplo completo

No servidor de referência do projeto, com GPT-2 e 512 tokens, a prova leva 7,6 minutos e a verificação 1,3 segundo, com prova de cerca de 10,7 MiB e throughput de cerca de 1,12 tokens por segundo. Com Gemma 3 e 512 tokens, a prova leva 19 minutos e a verificação 4,3 segundos, com prova de 27 MiB e throughput de cerca de 0,45 tokens por segundo.

- GPT-2, 512 tokens: prova 7,6 min; verificação 1,3 s; prova ~10,7 MiB; throughput ~1,12 tokens/s.
- Gemma 3, 512 tokens: prova 19 min; verificação 4,3 s; prova 27 MiB; throughput ~0,45 tokens/s.
- GPT-2: 124 milhões de parâmetros (openai-community/gpt2). Gemma 3: variante de 1 bilhão de parâmetros instruída (google/gemma-3-1b-it).

Fonte: <https://github.com/Lagrange-Labs/deep-prove/blob/master/zkml/README.md>

## Teste de pronto

Confira estes pontos para saber se o fluxo funcionou de ponta a ponta.

- [ ] O comando terminou sem erro e indicou que a prova foi verificada.
- [ ] O arquivo bench.csv existe na pasta onde você rodou e registra o tempo de prova e o tamanho da prova.
- [ ] O tempo de verificação ficou na ordem de segundos, muito menor que o tempo de prova.
- [ ] Para GPT-2, a similaridade cosseno à referência de ponto flutuante fica em pelo menos 99,6% com quantização de 12 bits e a opção --accuracy ligada.

Fonte: <https://github.com/Lagrange-Labs/deep-prove/blob/master/zkml/README.md>

## Erros comuns e cuidados

Estes pontos evitam conclusões erradas sobre o que a prova garante.

- Não confunda tempo de prova com tempo de verificação: provar leva minutos, verificar leva segundos. O gargalo é a geração, não a checagem.
- Os tempos de referência vêm de um servidor de referência com 24 núcleos e 504 GB; em máquina menor os tempos de prova serão diferentes.
- A acurácia de pelo menos 99,6% de similaridade cosseno vale para GPT-2 com quantização de 12 bits e a opção --accuracy ligada; não estenda esse número a outros modelos ou quantizações.
- Os comandos documentados cobrem apenas o bench-llm. O README descreve deep-prove-worker e deep-prove-cli como partes do workspace, mas não publica comandos nem flags para eles.
- O README usa --sequence 64 no exemplo; 512 é um dos comprimentos da tabela de desempenho. Não assuma que outros comprimentos têm os mesmos tempos.
- O projeto é licenciado pela Lagrange License; verifique os termos antes de uso comercial.
- O DeepProve reaproveita sumcheck e GKR do projeto Ceno (scroll-tech/ceno), que está em construção e não é adequado para produção.
- A prova atesta a execução da inferência, não a correção do modelo em si: ela não diz se o modelo é bom, apenas que a saída veio da execução correta dos pesos.
- O Llama 2 é citado como modelo confirmado, mas não há comando nem números para ele.

Fonte: <https://github.com/Lagrange-Labs/deep-prove>

## Glossário

Termos técnicos usados na apostila, com definição curta.

- Prova zero-knowledge: prova criptográfica de que uma computação foi executada corretamente sem revelar entradas, pesos nem saídas.
- Inferência: passagem à frente do modelo, do token de entrada ao próximo token previsto.
- Sumcheck: protocolo de prova interativa usado pelo DeepProve para verificar computações.
- logup GKR: técnica de prova usada junto com sumcheck para gerar provas de redes neurais.
- GKR: protocolo de prova para circuitos em camadas, base para o logup GKR.
- Quantização: representação dos pesos com menos bits, no caso 12 bits.
- Similaridade cosseno: medida de quão próximas ficam as saídas da versão quantizada da versão de ponto flutuante.
- Throughput: tokens processados por segundo na geração da prova.
- bench-llm: programa do DeepProve que roda o fluxo completo de prova de LLM.
- zkml: crate central do DeepProve, com quantização, camadas e geração/verificação de provas.
- bench.csv: arquivo gerado na pasta de execução com o tempo de prova e o tamanho da prova.
- Argmax: escolha do token com maior probabilidade como próximo token.
- Token: unidade de texto processada pelo modelo.
- Lagrange License: licença do projeto DeepProve.

Fonte: <https://github.com/Lagrange-Labs/deep-prove>

## Plano de 7 dias

Os passos já apresentados, distribuídos ao longo de uma semana.

- Dia 1: clonar o repositório oficial e confirmar Rust e Cargo instalados.
- Dia 2: compilar o bench-llm e verificar que o binário foi gerado.
- Dia 3: rodar o fluxo com GPT-2 e sequência de 512 tokens e observar a verificação.
- Dia 4: abrir o bench.csv e registrar tempo de prova e tamanho da prova.
- Dia 5: repetir com Gemma 3 e comparar os tempos.
- Dia 6: testar a variante distribuída com --distributed e --num_chunks 4.
- Dia 7: revisar os cuidados de acurácia e licença e decidir se o fluxo serve para o seu caso de auditoria.

Fonte: <https://github.com/Lagrange-Labs/deep-prove/blob/master/zkml/README.md>

## Para onde ir depois

Próximos passos para aprofundar o assunto.

- Ler o README completo do zkml para instalação, build com GPU e tutorial end-to-end.
- Consultar o repositório oficial para atualizações e a tabela completa de desempenho por comprimento de sequência.
- Estudar o projeto Ceno (scroll-tech/ceno) para entender sumcheck e GKR reaproveitados.
- Acompanhar a publicação do artigo do DeepProve, citado no README como referência de metodologia.
- Avaliar o Llama 2, citado como modelo confirmado, quando houver documentação de comandos.

Fonte: <https://github.com/Lagrange-Labs/deep-prove>

## Links citados

- https://huggingface.co/openai-community/gpt2
- https://huggingface.co/google/gemma-3-1b-it

## Além do vídeo

- A tabela completa de desempenho do README traz outros comprimentos de sequência além de 512 tokens.
- O artigo do DeepProve ainda não tem link publicado, embora seja citado como referência de metodologia.
- A build com GPU e a instalação completa ficam no README do zkml.
- Para o Llama 2, citado pelo projeto como modelo confirmado, não há exemplo de execução nesta apostila.
- Além de LLMs, o projeto suporta inferência de MLP e CNN.
