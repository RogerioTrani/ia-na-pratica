# MATH-500 sobe de 7,9% para 48,1% com Astra

_2026-11-12 · reportagem_

Esta apostila explica como uma IA leu e alterou pesos de outra IA para reduzir loops de raciocínio e melhorar o desempenho do Qwen3.5-0.8B em matemática. Você vai entender o que é Weight-Space Programming, por que a edição de 0,016% dos pesos elevou o MATH-500 de 7,9% para 48,1% e como o mesmo efeito apareceu no IFEval. Também verá experimentos com jogos, difusão, pequenos modelos de linguagem e um modelo sicofântico, incluindo os casos em que a leitura dos pesos falhou. Ao final, terá critérios para interpretar os números, reconhecer os limites da abordagem e escolher o próximo passo.

## O contexto

Em 2 de novembro de 2026, a pesquisa Sparks of Weight-Space Programming publicou resultados sobre a leitura e a escrita de pesos de redes neurais por modelos de linguagem. No caso central, o GPT-6 Astra editou o Qwen3.5-0.8B para melhorar seu desempenho em matemática. Com 50 passadas de inferência e as mesmas configurações de amostragem, o MATH-500 subiu de 7,9% para 48,1%.

A restrição definia o experimento: gradientes e loops de treino ficavam de fora, e os pesos eram o que se editava. O estudo também testou redes para jogos, modelos de difusão e pequenos modelos de linguagem. Esses resultados ampliam o contexto da proposta, mas cada número vale para o modelo, a tarefa e as condições do teste em que foi obtido.

Fonte: <https://rikiyat.github.io/blog/weight-space-programming/>

## O que é Weight-Space Programming

Uma rede neural guarda seu comportamento em pesos, os valores numéricos ajustados durante o treinamento. No método convencional, o treinamento calcula gradientes e um otimizador, como Adam ou Muon, usa essas informações para modificar os pesos. Ler essa coleção de números e prever o que ela faz é difícil até para quem trabalha com redes neurais.

Na proposta chamada Weight-Space Programming, um modelo de linguagem de uso geral lê e escreve pesos diretamente a partir de um objetivo descrito em linguagem natural. Ele pode receber os pesos como texto ou usar ferramentas para acessar arquivos quando a rede é grande. A abordagem dispensa o otimizador e a descida de gradiente; em alguns testes, também dispensou feedback do ambiente.

Isso cria duas possibilidades. Na leitura, o modelo tenta identificar tarefas, estruturas ou falhas codificadas nos pesos. Na escrita, ele altera pesos existentes ou cria uma rede do zero. No experimento com Qwen, o Astra trabalhava sobre outra rede; o resultado não foi um aperfeiçoamento dos próprios pesos do Astra.

Trabalhos anteriores já usavam modelos de linguagem para ler ativações ou pesos, explicar neurônios, executar treinamento e gerar pesos com modelos treinados para isso. Métodos sem gradiente também existiam, mas buscavam pesos por tentativa. A novidade relatada é um modelo de linguagem geral, usado como está, operando diretamente o espaço dos pesos para além de casos muito pequenos.

Fonte: <https://rikiyat.github.io/blog/weight-space-programming/>

## O experimento com Qwen3.5-0.8B

O Qwen3.5-0.8B tem 24 camadas e 0,8 bilhão de pesos. O Astra recebeu uma sessão Python com os pesos carregados, sem GPU. Para investigar o modelo, teve acesso a 7.469 problemas de treino do GSM8K e 7.275 problemas de treino do MATH. Os conjuntos de teste não foram fornecidos.

O orçamento de inferência variou entre 10, 25 e 50 passadas. Uma passada podia responder até 512 problemas ou processar até 1.024 textos, com lote médio de 64 sequências. Essas execuções serviam para examinar o comportamento do modelo; não havia treinamento nem informação de gradiente.

A avaliação final usou MATH-500, GSM8K e seis outros benchmarks, com o modo de raciocínio ativado e limite de 32.768 tokens. A amostragem usou temperature 0,6, top-p 0,95, top-k 20 e presence penalty 1,5. O modelo original e o editado foram comparados com essas mesmas configurações. O Astra nunca viu esses benchmarks de avaliação.

Fonte: <https://rikiyat.github.io/blog/weight-space-programming/>

## A correção dos loops de raciocínio

Um loop de raciocínio acontece quando o modelo repete o mesmo texto e não chega a uma resposta. No Qwen original, 85 das primeiras 96 respostas de prática atingiram o limite de 32.768 tokens. O model card do Qwen3.5-0.8B também alerta para esse comportamento.

O Astra associou os loops a uma direção presente nas saídas dos MLPs das camadas 15 e 19. Ele subtraiu essa direção de 64 colunas de saída em cada camada, alterando 131.072 pesos. Uma direção, nesse contexto, funciona como uma tendência conjunta de valores que contribui para um comportamento. Reduzir sua influência pode mudar a saída sem reescrever a rede inteira.

A edição atingiu 0,016% dos 0,8 bilhão de pesos. O mecanismo foi uma correção localizada de um obstáculo: o modelo passou a concluir respostas que já conseguia trabalhar. O estudo não apresenta isso como uma capacidade geral de acrescentar qualquer conhecimento matemático ausente.

Fonte: <https://rikiyat.github.io/blog/weight-space-programming/>

## Os números do Qwen

As porcentagens de MATH-500 e GSM8K indicam desempenho nas respectivas avaliações. O IFEval mede seguimento de instruções. A última medida é a fatia das respostas do MATH-500 que atingiram o limite de tokens. No MATH-500, cada problema entra com média de quatro amostras; no IFEval, com média de duas. O resultado principal corresponde a 50 passadas, e 10 ou 25 passadas produziram efeitos menores.

- MATH-500: o modelo base marcou 7,9%; com 10 passadas, 12,3%; com 25 passadas, 14,1%; com 50 passadas, 48,1%.
- GSM8K: o modelo base marcou 13,8%; com 10 passadas, 25,7%; com 25 passadas, 25,1%; com 50 passadas, 67,1%.
- IFEval: o modelo base marcou 21,0%; com 10 passadas, 49,0%; com 25 passadas, 39,9%; com 50 passadas, 62,3%.
- Limite de tokens no MATH-500: a fatia de respostas interrompidas pelo limite caiu de 93,0% no modelo base para 87,2% com 10 passadas, 86,4% com 25 passadas e 33,1% com 50 passadas.
- Pesos modificados: 131.072 de 0,8 bilhão, ou 0,016%, segundo o valor relatado pela pesquisa.

Fonte: <https://rikiyat.github.io/blog/weight-space-programming/>

## Por que o IFEval também melhorou

O IFEval avalia se o modelo segue instruções. A edição feita para matemática elevou seu resultado de 21,0% para 62,3%, aproximadamente três vezes o valor original. O Astra não recebeu o IFEval como tarefa de otimização; a melhoria apareceu na avaliação posterior.

Os autores relacionam esse efeito ao fato de os loops não serem exclusivos da matemática. Quando uma resposta fica presa em repetições, o modelo também pode deixar de cumprir a instrução recebida. Ao reduzir esse obstáculo, a mesma edição liberou o seguimento de instruções. O dado vale para o Qwen testado com as configurações do experimento; não estabelece que toda edição direcionada a uma tarefa melhora outras.

Fonte: <https://rikiyat.github.io/blog/weight-space-programming/>

## O limite da correção: Gemma 3 270M

O estudo tentou o mesmo tipo de intervenção no Gemma 3 270M, um modelo com cerca de um terço do tamanho do Qwen. Ele raramente entrava em loop: 8,5% de suas respostas atingiam o limite, contra 93% do Qwen original. O Astra encontrou erros comuns de raciocínio, como aritmética incorreta e passos algébricos inválidos, sem um componente único responsável por eles.

As edições ficaram pequenas e localizadas. Um exemplo foi dobrar um neurônio que respondia a números. Nenhuma mudança superou aproximadamente um ponto percentual no MATH-500, e o próprio Astra classificou o ganho como não estabelecido. O modelo base marcou 6,8%; as versões editadas marcaram 7,0% com 5 passadas, 7,6% com 10, 7,7% com 25 e 7,0% com 50.

O Gemma foi amostrado com temperature 1,0, top-k 64, top-p 0,95 e limite de 8.192 tokens, com média de quatro amostras por problema. Essas condições permitem interpretar o contraponto: editar pesos removeu um obstáculo que escondia uma capacidade no Qwen, mas não criou uma capacidade ausente no Gemma.

Fonte: <https://rikiyat.github.io/blog/weight-space-programming/>

## Leitura de pesos: jogos e difusão

No Experimento 1, quatro redes treinadas com PPO jogavam Breakout, Pong, Pac-Man e Freeway. Todas tinham as mesmas dimensões, os mesmos canais de entrada e as mesmas cinco ações. O Astra recebeu os 17.253 pesos como texto e a descrição da grade e das ações, sem os nomes dos jogos. Ele identificou corretamente os quatro. Em Breakout, por exemplo, reconheceu na primeira camada uma concentração de pesos na linha inferior, coerente com a posição da raquete.

No Experimento 2, três modelos de difusão DDPM geravam círculos, triângulos ou quadrados em imagens em tons de cinza de 12 × 12. Cada rede tinha 23.824 pesos. O Astra recebeu apenas os pesos, sem ferramentas e sem permissão para calcular uma passada adiante. Ele identificou as três formas e encontrou peças de suas bordas na camada de saída.

A leitura não foi perfeita. O Astra desenhou as formas como contornos, embora os modelos gerassem figuras preenchidas. Os autores interpretam o erro como sinal de que ele leu a geometria dos pesos, em vez de reproduzir a execução completa da rede. O teste mostra uma capacidade de leitura estrutural e seus limites.

Fonte: <https://rikiyat.github.io/blog/weight-space-programming/>

## Leitura no meio da rede: idiomas e copying heads

Para evitar que o Astra usasse apenas a primeira ou a última camada, o Experimento 3 removeu as camadas de entrada e saída de três pequenos modelos de linguagem com 7,2 milhões de parâmetros. As redes foram treinadas para prever o próximo caractere em código Python, literatura japonesa em romaji e Wikipédia em inglês. O Astra recebeu somente os quatro blocos transformer intermediários e não podia executar a rede nem buscar respostas.

Ele identificou o idioma correto nas duas tentativas para cada rede e encontrou todas as copying heads, sem apontar outras cabeças como candidatas. Uma copying head encontra caracteres anteriores no texto e copia o que veio depois delas. O Astra encontrou uma cabeça na primeira camada que olhava um caractere para trás e, multiplicando matrizes de pesos, identificou cabeças posteriores que usavam essa informação.

A explicação também usou regularidades dos dados. Código repete nomes com frequência, então várias copying heads indicaram Python. O romaji se destacou porque o último bloco intermediário escrevia em menos direções distintas, coerente com um alfabeto que não usa letras como q, l, v e x. A medição feita executando o modelo confirmou as cabeças encontradas.

- Python: o Astra indicou as copying heads 2.1, 3.1 e 3.5.
- Romaji: o Astra indicou a copying head 3.3.
- Inglês: o Astra indicou a copying head 3.1.
- Python para análise: o Astra podia usar até 100 execuções de código, mas não podia rodar a rede nem realizar busca.

Fonte: <https://rikiyat.github.io/blog/weight-space-programming/>

## Escrita de pesos: o carro e os jogos MinAtar

No Experimento 4, uma rede PPO com 171.664 pesos controlava um carro que precisava dar ré, acelerar e superar uma rampa. Depois de 1 bilhão de passos de treinamento, ela nunca conseguiu completar a tarefa em 256 episódios. O Astra recebeu os pesos, a descrição da cena e um episódio gravado. Sem ferramentas e em uma única resposta, explicou a falha e editou 3,5% dos pesos.

A rede havia convergido para um mínimo local: repetia uma estratégia que a impedia de progredir. A edição criou um pequeno caminho adicional que lia a posição e a velocidade do carro, fazia o veículo recuar e desligava esse caminho depois que a roda verde passava da faixa vermelha, deixando a rede treinada conduzir o restante. Com a alteração, o carro completou todos os 1.024 episódios de avaliação.

No Experimento 5, o Astra criou pesos do zero para Breakout, Seaquest e Asterix, do MinAtar. Recebeu as regras, o código-fonte e o desenho da rede, com todos os pesos iniciados em zero. Não teve dados, função de perda, gradientes, ferramentas ou partidas de prática. Escreveu os novos pesos diretamente em uma resposta e eles superaram o PPO treinado por 100 milhões de passos nos três jogos.

- Breakout: o Astra marcou 517,4; o PPO marcou 15,8 com 100 milhões de passos e 25,3 com 500 milhões.
- Seaquest: o Astra marcou 53,1; o PPO marcou 5,6 com 100 milhões de passos e 88,9 com 500 milhões.
- Asterix: o Astra marcou 53,2; o PPO marcou 25,8 com 100 milhões de passos e 55,2 com 500 milhões.
- Interpretação: esses valores são pontuações dos jogos, não porcentagens de acerto, e não devem ser comparados diretamente entre jogos diferentes.

Fonte: <https://rikiyat.github.io/blog/weight-space-programming/>

## Escrita em escala: uma rede para Go

O Experimento 6 levou a escrita de pesos a uma rede com 1.480.274 pesos, grande demais para caber diretamente no contexto. A arquitetura era 243 → 512 × 6 → 82, com todos os pesos começando em zero. O Astra recebeu as regras do Go, o layout de entrada e saída e um ambiente Python com numpy ou PyTorch na CPU. Não havia biblioteca de Go nem acesso à internet.

Ele podia editar os pesos no ambiente, mas só executava a rede nas passadas permitidas. Cada passada podia render até 128 partidas de prática ou mostrar saídas em até 256 posições. O orçamento variou de zero a 50 passadas. Sem nenhuma passada, a rede criada venceu mais da metade dos jogos contra duas redes PPO menores. Com 50 passadas, venceu a rede PPO de tamanho equivalente, treinada em 20 milhões de jogos.

A construção foi explicada camada por camada. As primeiras camadas marcavam pedras e liberdades; as intermediárias acompanhavam grupos de pedras conectadas; a última pontuava movimentos para capturar, salvar grupos e evitar colocar-se em atari ou preencher os próprios olhos. Sem passadas, o Astra escreveu esse programa em 336 linhas de Python. Com prática, observava derrotas, alterava a parte responsável e mantinha mudanças que melhoravam o resultado.

Fonte: <https://rikiyat.github.io/blog/weight-space-programming/>

## Interpretabilidade: identificar um modelo sicofântico

No Experimento 7, duas cópias do Gemma 3 270M passaram pelo mesmo ajuste fino. Uma aprendia a responder corretamente; a outra seguia a sugestão do usuário, comportamento chamado de sicofância. As incorporações de tokens e as camadas de saída ficaram congeladas. O Astra recebeu os pesos dos dois modelos e deveria identificar o sicofântico apenas por eles.

A leitura dos pesos falhou nas quatro tentativas. Ele encontrou diferenças numéricas, mas não conseguiu ligá-las ao comportamento. Quando o teste passou a permitir padrões de atenção, sem acesso às saídas dos modelos, ele identificou corretamente os três pares avaliados. O Astra não podia executar os modelos por conta própria: uma ferramenta de atenção rodava os dois em até 16 textos escritos por ele e devolvia somente os pesos de atenção, com limite de 20 execuções.

Nos modelos sicofânticos, cabeças de atenção das camadas intermediárias davam mais peso à sugestão do usuário. Na cabeça 10.2, o modelo honesto direcionava 94,3% da atenção para os números da pergunta e 0,75% para a resposta sugerida. O sicofântico invertia essa concentração: 3,5% para os números e 85,7% para a sugestão. Em fatos conhecidos que não entraram no ajuste, o sicofântico seguiu 100% das sugestões incorretas; o honesto seguiu entre 1% e 3%.

Fonte: <https://rikiyat.github.io/blog/weight-space-programming/>

## Como funciona na prática

Exemplo: no Qwen, o objetivo era melhorar matemática. O Astra examinou respostas de prática, percebeu que muitas terminavam por repetição e localizou uma direção associada ao loop nas camadas 15 e 19. Depois da edição das colunas indicadas, o modelo editado foi comparado com o original em avaliações que o Astra nunca viu. A sequência foi objetivo, inspeção, diagnóstico, edição e avaliação.

Uma passada de inferência não atualiza pesos; ela apenas produz saídas com a rede na configuração atual. A atualização veio da edição explícita feita pelo Astra. Esse detalhe separa a abordagem de um treinamento convencional. Se os loops diminuem e o desempenho sobe, a evidência aponta para a remoção de um obstáculo. Se o modelo não tem esse obstáculo e continua cometendo erros variados, como no Gemma, uma edição pequena pode não produzir ganho.

Fonte: <https://rikiyat.github.io/blog/weight-space-programming/>

## Quem pode ganhar e quais são os riscos

Pesquisadores de interpretabilidade ganham uma nova forma de investigar estruturas e comportamentos codificados nos pesos. Desenvolvedores podem usar edições localizadas para corrigir falhas específicas. Os autores também apontam potenciais reduções de tempo e computação, mas esses benefícios são possibilidades apresentadas pelo estudo, não economias medidas nos experimentos.

Para usuários de modelos, o resultado do Qwen sugere que uma correção pode melhorar mais de uma tarefa. Os resultados também indicam dois riscos para quem avalia ou implanta a técnica: assumir que pesos sempre revelam o comportamento e assumir que toda falha tem um único componente que pode ser removido. A sicofância não foi identificada apenas pelos pesos, e o Gemma não melhorou de forma estabelecida.

Fonte: <https://rikiyat.github.io/blog/weight-space-programming/>

## O que ainda não se sabe

Os resultados são iniciais, e a capacidade ainda é limitada por ineficiências no uso do contexto e dos ambientes de execução (harnesses). Redes pequenas couberam diretamente no contexto; redes maiores exigiram ferramentas e passadas de inferência. Os autores estão construindo um benchmark e um harness padronizados para avaliar a abordagem.

- Condições do Qwen: o ganho principal foi obtido no Qwen3.5-0.8B com 50 passadas, modo de raciocínio ativado e configuração específica de amostragem.
- Falha de leitura: no teste de sicofância, os pesos sozinhos não permitiram identificar o comportamento; os padrões de atenção foram necessários.
- Falha de escrita: no Gemma 3 270M, as edições não produziram ganho estabelecido no MATH-500.
- Escala: a capacidade depende do tamanho da rede, do contexto disponível e das ferramentas fornecidas.
- Hipóteses futuras: auditoria sem avaliação, inicialização de modelos em uma única intervenção, steering e unlearning sem dados, autoaperfeiçoamento recursivo e fusão de arquiteturas diferentes são possibilidades descritas pelos autores.
- Preservação do modelo: editar poucos pesos não prova, por si só, que toda edição evita efeitos colaterais ou esquecimento catastrófico.

Fonte: <https://rikiyat.github.io/blog/weight-space-programming/>

## O que você pode fazer

1. Abra o artigo oficial e identifique, em cada experimento, o modelo, os dados, as ferramentas, o orçamento de inferência e a avaliação. O resultado esperado é separar o que foi demonstrado do que foi apenas proposto.
2. Leia o model card do Qwen3.5-0.8B (https://huggingface.co/Qwen/Qwen3.5-0.8B-Instruct) e localize o aviso sobre loops de raciocínio. O resultado esperado é entender a falha que a edição pretendeu corrigir.
3. Abra o repositório de logs github.com/RikiyaT/lm_understand-logs indicado no artigo e compare os prompts, as respostas do Astra, o código executado e as saídas observadas. O resultado esperado é reconstruir o caminho entre diagnóstico e edição.
4. Ao reproduzir o Experimento 8, preserve thinking on, o limite de 32.768 tokens, temperature 0,6, top-p 0,95, top-k 20 e presence penalty 1,5. O resultado esperado é obter uma comparação válida entre o modelo base e o editado.
5. Registre MATH-500, GSM8K, IFEval e a fatia de respostas que atinge o limite de tokens com 10, 25 e 50 passadas. O resultado esperado é distinguir o efeito do orçamento de inferência.
6. Antes de editar outro modelo, classifique a falha: loop com um componente identificável ou erros distribuídos sem uma causa única. O resultado esperado é decidir se existe um alvo específico para uma intervenção localizada.

Fonte: <https://rikiyat.github.io/blog/weight-space-programming/>

## Glossário

- Peso: valor numérico que compõe uma rede neural e participa do cálculo de suas saídas.
- Espaço dos pesos: conjunto de todos os valores numéricos que definem uma rede.
- Gradiente: informação calculada no treinamento convencional para indicar como os pesos podem ser ajustados.
- Otimizador: algoritmo que usa gradientes para atualizar pesos, como Adam ou Muon.
- Descida de gradiente: processo de ajustar pesos repetidamente com base nos gradientes.
- Forward pass: passagem de dados pela rede já configurada para gerar uma saída.
- Inferência: uso de um modelo para produzir respostas ou previsões.
- Loop de raciocínio: repetição de texto que impede o modelo de concluir uma resposta.
- Token: unidade de texto processada pelo modelo; o limite de tokens define quanto ele pode gerar ou ler.
- MLP: bloco de rede neural formado por camadas densas; no Qwen, as saídas dos MLPs das camadas 15 e 19 foram o alvo da edição.
- Cabeça de atenção: componente que decide a quais partes da entrada o modelo dá mais atenção.
- Copying head: cabeça de atenção que encontra informação anterior e a repete em uma nova posição.
- PPO: algoritmo de treinamento por reforço usado para treinar as redes dos jogos.
- DDPM: modelo de difusão usado para gerar imagens a partir de um processo de remoção de ruído.
- Benchmark: avaliação padronizada usada para medir e comparar desempenho.
- Zero-shot: realização de uma tarefa sem treinamento específico para ela.
- Sicofância: comportamento de seguir a sugestão do usuário mesmo quando ela está errada.
- Esquecimento catastrófico: perda de capacidades anteriores quando um modelo passa por um novo treinamento ou ajuste.

Fonte: <https://rikiyat.github.io/blog/weight-space-programming/>

## Para onde ir depois

- Compare o caso do Qwen com o do Gemma e explique qual falha podia ser removida por uma edição localizada.
- Nos logs, acompanhe uma única edição das camadas 15 e 19 e verifique como a subtração da direção alterou as colunas de saída.
- Use a versão editada do Qwen indicada no artigo oficial no Hugging Face e repita as avaliações com as configurações do Experimento 8.
- Acompanhe o benchmark e o harness padronizados anunciados pela pesquisa para comparar resultados com critérios consistentes.
- Pratique explicar por que a melhoria no IFEval veio da remoção dos loops, sem tratar esse resultado como garantia para outros modelos.

Fonte: <https://rikiyat.github.io/blog/weight-space-programming/>

## Além do vídeo

- Nos quatro jogos do Experimento 1, as redes usaram uma grade de 10 × 10, as mesmas cinco ações e PPO por 1 bilhão de passos, escolhendo o melhor de três sementes por jogo.
- Os modelos de difusão do Experimento 2 foram treinados com Adam por 40.000 passos e lotes de 512.
- As redes MinAtar foram avaliadas em 1.000 episódios, com sticky actions 0,1 e limite de 10.000 passos; os resultados do PPO usaram o melhor de 3 a 10 sementes.
- A rede de Go foi avaliada em 2.000 jogos contra cada uma das duas redes PPO menores, jogando metade das partidas com as pedras pretas.
- No Qwen, as médias por problema variaram: 16 amostras na AMC23; quatro em MATH-500, Minerva Math, OlympiadBench e GPQA Diamond; duas em GSM8K e IFEval; uma em MMLU-Pro, com um conjunto fixo de 1.000 questões.
- Os logs completos reúnem tudo o que foi enviado ao Astra, suas respostas e resumos de raciocínio, o código executado, as saídas observadas, as redes lidas ou escritas e a avaliação por trás de cada número.
- A versão editada do Qwen3.5-0.8B foi reconstruída a partir dos logs, reavaliada e disponibilizada com uma demonstração ao vivo no Hugging Face.
