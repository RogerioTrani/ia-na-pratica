# Anthropic lança FlashProve para provar inferências de IA

_2026-11-22 · reportagem_

A Anthropic apresentou o FlashProve, um protótipo aberto que usa provas criptográficas do tipo zkSNARK para mostrar que uma resposta de IA veio do modelo declarado, sem revelar seus pesos. Nesta apostila você entende o problema de confiança que ele resolve, como funcionam o commitment e a prova, os números do teste com Llama 4 Maverick e como conferir uma prova em uma CPU. Você também vê os requisitos para reproduzir o protótipo, o histórico da área e o que ainda falta para virar produto.

## O contexto: quem realmente respondeu?

Quando você envia uma pergunta para um modelo de IA, não há como ter certeza, só pelo texto da resposta, de qual modelo realmente gerou aquela resposta. Um serviço de roteamento pode trocar o modelo por um mais barato. Um atacante pode alterar o fluxo de tokens. Um modelo mais avançado pode se passar por um mais fraco. A resposta pode ser excelente e mesmo assim não provar nada sobre os pesos usados.

Isso incomoda em três situações concretas. Avaliadores independentes precisam saber que o modelo testado é o que está sendo servido. Clientes que usam um modelo via terceiro querem garantia de que os tokens vieram do modelo pago. E empresas precisam saber quais pesos rodam nos seus próprios servidores.

O objetivo da inferência provável (provable inference) é permitir que alguém com pouco poder de computação e sem acesso aos pesos verifique que uma resposta veio do modelo pedido. A Anthropic apresentou o FlashProve como um protótipo aberto que avança nessa direção usando um tipo de prova criptográfica chamado zkSNARK.

Fonte: <https://www.anthropic.com/research/provable-inference>

## O que é o FlashProve

FlashProve é um sistema de inferência provável para modelos de linguagem grandes com arquitetura Mixture-of-Experts (MoE). Ele tem dois participantes: o provedor (quem roda o modelo) e o verificador (quem confere). A prova é zero-knowledge: não revela os pesos. E é succinct: pequena e rápida de verificar.

O lançamento inclui cinco artefatos: o post no blog da Anthropic, um relatório técnico, uma especificação do protocolo, código executável (um prover e dois verifiers, um em C++ rápido e um em Lean formalmente verificado) e as provas em Lean com um visualizador interativo dos teoremas. Tudo sob licença Apache 2.0.

O repositório é um artefato de pesquisa, não mantido e sem aceitar contribuições. Versão 0.16.0.

Fonte: <https://github.com/anthropics/FlashProve>

## Os dois atores e as duas fases

O protocolo se divide em duas fases. Na fase offline, o provedor publica um commitment, uma impressão digital curta que fixa uma escolha exata de pesos. Os pesos em si ficam ocultos. Na fase online, para cada pedido do verificador (prompt e tokens de saída), o provedor gera um arquivo de prova mostrando que o modelo comprometido produz aqueles tokens.

Quem tem o commitment, o prompt e a resposta pode conferir, sem os pesos e com pouco poder de computação, e se convencer de que os pesos comprometidos, rodando naquele prompt, produzem exatamente aqueles tokens.

Fonte: <https://www.anthropic.com/research/provable-inference>

## Fase offline: o commitment

O commitment é uma impressão digital curta dos pesos. Ele fixa uma escolha exata de pesos enquanto os pesos permanecem ocultos. As provas posteriores são verificadas contra esse commitment.

A fase offline roda uma vez por modelo e leva cerca de 39 minutos. O commitment resultante vale para cerca de 16 milhões de pedidos, depois dos quais o provedor precisa comprometer de novo.

O commitment não esconde a arquitetura do modelo. Apenas os pesos ficam ocultos. Esconder a arquitetura é trabalho futuro.

Fonte: <https://www.anthropic.com/research/provable-inference>

## Fase online: a prova acompanha a resposta

Na fase online, o provedor lê o texto já gerado em uma passagem paralela (como prefill) e prova em lote. O prover abre o commitment aos pesos uma vez por lote, não uma vez por pedido.

Cada prova afirma: o modelo comprometido produz estes tokens de saída quando avaliado. Se a resposta alegada se desviar do modelo especificado, a verificação falha.

A prova é vinculada a um commitment específico aos pesos. Ela certifica não apenas que algum modelo produziu a resposta, mas que o modelo comprometido o fez.

Fonte: <https://www.anthropic.com/research/provable-inference>

## As quatro garantias

Completude: se a afirmação está correta, a prova é aceita pelo verificador. Um provedor honesto tem sua prova aceita.

Solidez: é efetivamente impossível produzir uma prova válida de uma afirmação falsa, exceto com probabilidade desprezível (aproximadamente q/2^124 + 2^-101 após q consultas de hash).

Zero-knowledge: o verificador não aprende nada sobre os pesos, os valores intermediários da computação nem quais experts rodaram em cada camada. A arquitetura (exceto os pesos) não é oculta.

Succinctness: a computação atestada é a execução de um modelo de 400 bilhões de parâmetros em uma GPU H100, enquanto o verificador recebe um arquivo de prova de cerca de 18,78 MB que leva segundos para conferir em uma CPU de 24 núcleos.

Fonte: <https://www.anthropic.com/research/provable-inference>

## zkSNARK: o que é e por que se encaixa

zkSNARK é a sigla de zero-knowledge succinct argument of knowledge. É um sistema que permite a um provedor convencer um verificador, por meio de um certificado curto, de que uma computação foi executada corretamente. O certificado é zero-knowledge (não revela informação além do que decorre da correção da computação) e succinct (exponencialmente mais rápido de verificar do que a computação provada).

A Anthropic escolheu zkSNARK porque combina forte privacidade dos pesos com eficiência. A prova é montada a partir de um objeto informacional chamado interactive oracle proof (IOP), compilado em prova criptográfica com funções hash, com segurança pós-quântica.

A arquitetura do modelo não é escondida. O sistema assume MoE, em que cada camada transformer tem múltiplos experts e um router ativa só um subconjunto. O trabalho do prover é proporcional aos experts que realmente rodaram (cerca de 17 bilhões dos 400 bilhões por token).

Fonte: <https://www.anthropic.com/research/provable-inference>

## Os números do teste

A medição usou o Llama 4 Maverick, um modelo de 400 bilhões de parâmetros com mistura de especialistas, cerca de 17 bilhões ativados por token, pesos quantizados em 4 bits (cerca de 232 GB) e aritmética inteira no prefill. Cada pedido do verificador é uma janela de 1.024 tokens e cada prova confere um token.

- Modelo: Llama 4 Maverick, 400 bilhões de parâmetros, MoE, cerca de 17 bilhões ativados por token, pesos em 4 bits (cerca de 232 GB), aritmética inteira no prefill.
- Contexto: janela de 1.024 tokens. Cada prova confere um token.
- Prover: 1 GPU NVIDIA H100, 24 núcleos de CPU, cerca de 290 GB de RAM no host.
- Velocidade do prover: cerca de 110 tokens por segundo, em lote de 24 pedidos (cerca de 223 segundos por lote).
- Tamanho da prova: 18,78 MB por janela de 1.024 tokens.
- Custo computacional: gerar as provas consome entre 70 e 95 vezes o tempo de GPU que o vLLM leva para processar prompts do mesmo tamanho (por GPU, cerca de 72 vezes com os mesmos 24 pedidos de uma vez, de 66 a 77 entre execuções, e cerca de 94 vezes na maior carga testada; o vLLM rodou a versão FP8 do mesmo modelo em oito H100).
- Commitment: download de cerca de 6,5 MB.
- Verificador: CPU apenas, 17 segundos em 24 threads (21 segundos em uma única thread), incluindo as verificações da fase offline.
- Comparação com VerInf: o único trabalho anterior de prova do mesmo modelo conhecido pelos autores reportava 14,3 horas para 1.000 tokens em um DGX Spark, com prova de 93,6 GB que levava quase um dia para verificar.

Fonte: <https://www.anthropic.com/research/provable-inference>

## O que os números não dizem

A prova verifica a execução pelo modelo declarado. Ela não garante que a resposta seja verdadeira. Um modelo pode produzir uma resposta errada e a prova ainda ser válida.

A prova é sobre uma versão do modelo em aritmética de números inteiros, com decodificação greedy. Uma resposta de uma implementação em ponto flutuante, ou com amostragem, pode divergir em alguma posição e não bater exatamente com a computação provada.

O custo de 70 a 95 vezes mais tempo de GPU é uma faixa, não um número único. Depende da carga do vLLM de referência.

O protótipo é de pesquisa. Não há garantia formal de que o código executável rápido corresponda ao protocolo formalizado em Lean.

Fonte: <https://www.anthropic.com/research/provable-inference>

## O que muda para quem usa IA

Para um usuário final, a mudança proposta é conceitual: a resposta poderia vir com um certificado. Em vez de confiar no texto, o usuário (ou um auditor) poderia conferir a prova em segundos em uma CPU, sem acesso aos pesos.

Exemplo: um desenvolvedor afirma que sua biblioteca foi escaneada por um modelo de cibersegurança de ponta. Hoje ele pode publicar os logs de chat, mas alguém pode ter forjado esses logs com um modelo mais barato. Com inferência provável, o provedor anexa uma prova de que a saída foi produzida pelo modelo declarado naquele input. A succinctness permite a verificação rápida sem hardware especializado.

Ainda não é um produto de consumo. É um protótipo que exige uma H100 e centenas de gigabytes de RAM para provar.

Fonte: <https://www.anthropic.com/research/provable-inference>

## Para que serve: quatro casos de uso

Pacing: reguladores podem pedir certificados cobrindo os pedidos servidos em um período, para garantir que o hardware está rodando o modelo declarado. A prova não estabelece, porém, que o hardware não está treinando em paralelo.

Detecção de adulteração: um atacante que compromete um servidor, ou um modelo que se substitui por outro, precisaria produzir provas válidas para os pesos esperados para evitar detecção, o que não consegue fazer.

Proveniência de texto: provar que certo esforço foi gasto em uma análise, por exemplo que uma biblioteca foi escaneada por um modelo específico, ou que um plano de negócio foi aprovado por um modelo adequado.

Aprovação de modelos: reguladores podem exigir que o provedor anexe a prova às respostas, forçando o uso apenas de modelos aprovados.

Fonte: <https://www.anthropic.com/research/provable-inference>

## Como funciona na prática: verificar uma prova

A verificação é o passo que qualquer pessoa pode rodar. O verificador é um binário em C++ que recebe o diretório de configuração, o diretório da chave pública, o arquivo de pedido, o arquivo de tokens e o arquivo de prova, mais o commitment ID.

- O commitment ID deve vir de uma parte em quem você confia, nunca do servidor sendo verificado nem dos arquivos enviados com a prova. Os exemplos armazenados são a única exceção.
- O arquivo de pedido deve ser montado por você mesmo.
- Leia o código de saída junto com a última linha.
- 0, última linha YES ou WITHIN LIMITS: aceito (correspondência exata ou diferença dentro do limite).
- 1, NO: <nome>: rejeitado (ou falha local).
- 5, NOT CHECKED: <nome>: sem veredito; tente de novo uma vez só para internal-stage ou internal-exception-parFor.
- 14, NOT-A-VERIFICATION: chamada inválida; veja as linhas após '---- the call ----'.
- 2, 3, 4 ou 15: linha de comando ou arquivo inválido, ou chamada parcial; sem veredito.

```
bin/cp_verify CONFIG_DIR PUBLIC_KEY_DIR REQUEST_FILE TOKEN_FILE PROOF_FILE -id COMMITMENT_ID
```

Fonte: <https://github.com/anthropics/FlashProve>

## Reproduzir o protótipo: passos

1. Clone o repositório e leia o README a partir de 'For agents' e o AGENTS.md. Rode como usuário comum, nunca como root.
2. Instale as dependências de sistema no Ubuntu 24.04 (precisa de root): apt-get update && apt-get install -y --no-install-recommends g++ make python3 unzip.
3. Crie o ambiente virtual Python 3.13 e instale requirements.txt com --require-hashes.
4. Compile o verificador com verifier/build.sh. Espere 1 a 2 minutos e a linha THE VERIFIER IS BUILT.
5. Verifique a prova de exemplo incluída (comando completo na seção de comandos). Última linha esperada: YES, código 0.
6. Rode os testes de CPU com a primeira linha do bloco abaixo. Código 0 passa; 77 faltam ferramentas; 3 viu algo falso aceito (reportar).
7. Para GPU, compile com examples/quickstart-gpu.sh (pode levar mais de 15 minutos, loga em quickstart-gpu.log). Sucesso: exit code 0 e linha quickstart-gpu: all steps ended as expected.
8. Para o teste em tamanho completo (formato do Llama 4 Maverick, com pesos sintéticos), depois do build de GPU, rode a segunda e a terceira linhas do bloco abaixo.
9. Para os pesos reais do Llama 4 Maverick, siga examples/maverick/run.sh all com o diretório de pesos preparado (inclui download, verificação de hash, calibração, commit, prova e verificação).

```
D=$(mktemp -d) && ./run_suite.py cpu "$D/work"
W=$(mktemp -d) && WORK="$W/example" && echo "WORK=$WORK"
prover/examples/run_target_example.sh target_full_f2 "${WORK:?first run the line with mktemp}"
```

Fonte: <https://github.com/anthropics/FlashProve>

## Requisitos de hardware e software

- Verificador (CPU): Linux x86-64, bash, g++ 13 ou superior, menos de 2 GB de RAM. Para testes e exemplos de CPU: make, python3, unzip.
- Prover (GPU): Linux x86-64 (kernel 4.14 ou mais novo) em CPU com extensões SHA (sha_ni); uma GPU NVIDIA H100 de 80 GB dedicada; driver NVIDIA 580 ou mais novo; CUDA 13.2 Update 2 (nvcc 13.2.86); gcc e g++ 13; binutils, flock, curl; Python 3.13 com os pacotes fixados.
- Modelo completo: 330 GB de RAM disponível no host para o commit (290 GB para a prova) e 245 GB de espaço livre em disco local.
- Os pesos quantizados (232,13 GB) vêm do Hugging Face, pasta UD-Q4_K_XL, conversão pública de terceiros em formato GGUF (revisão 41032e5471dd6ea5b349062d978626215d6c5bba, 5 arquivos). Sujeitos à Llama 4 Community License da Meta.
- Antes de rodar o pipeline completo, gere o arquivo calibration_set.npy com python3 scales/make_calibration_set.py a partir do dataset Salesforce/wikitext e dos tokenizers oficiais de meta-llama/Llama-2-7b-hf e meta-llama/Llama-4-Maverick-17B-128E-Instruct (exige aprovação de acesso da Meta no Hugging Face).

Fonte: <https://github.com/anthropics/FlashProve>

## Comandos oficiais

Estes são os comandos publicados no repositório oficial. Rode a partir da raiz do repositório como usuário comum.

```
verifier/build.sh
bin/cp_verify examples/accepted-proof/config examples/accepted-proof/ivk examples/accepted-proof/example.req examples/accepted-proof/example.y examples/accepted-proof/example.proof -id "$(cat examples/accepted-proof/ID.txt)"
examples/quickstart-gpu.sh
prover/build.sh
examples/maverick/run.sh all "$M" --weights "$F"
```

Fonte: <https://github.com/anthropics/FlashProve>

## Linha do tempo do zkML

A prova de inferência evoluiu de centenas de segundos por token em modelos pequenos para mais de 100 tokens por segundo em um modelo de 400 bilhões. Os marcos abaixo mostram essa curva.

- 2017: SafetyNets verificou uma CNN de 2 camadas para MNIST e um modelo de fala pequeno.
- 2021: zkCNN alcançou VGG-16 (15 milhões de parâmetros) a 88,3 segundos por prova.
- 2022: Kang et al. provaram MobileNet v2 em ImageNet em resolução completa.
- 2023: EZKL provou um transformer de 1 milhão de parâmetros em cerca de 966 segundos por token. Outro marco das provas de transformers, o ZKML, provou o GPT-2 de 117 milhões em cerca de 159 segundos por token.
- 2024: zkLLM provou LLaMA-2-13B em entrada de 2.048 tokens em cerca de 15 minutos em GPU (cerca de 2,5 tokens por segundo em lote).
- 2025: zkGPT reduziu GPT-2 para 21,8 segundos; zkPyTorch provou Llama-3 8B a cerca de 150 segundos por token em um núcleo de CPU; ZKTorch provou GPT-J (6B) em cerca de 20 minutos; VerInf provou Llama 4 Maverick a cerca de 0,02 tokens por segundo.
- 2026: SASH alcançou cerca de 1,25 tokens por segundo em Llama 3.1 8B em uma H100.
- Atual: DeepProve alcança cerca de 2,9 tokens por segundo no GPT-2 e 1,4 no Gemma 3 em uma máquina, e 31 tokens por segundo em execução distribuída.
- Atual: FlashProve prova Llama 4 Maverick (400B) a cerca de 110 tokens por segundo em uma H100, com provas de 18,78 MB verificáveis em segundos.
- Atual: Attestable reporta 53 a 77 tokens por segundo para Gemma 4 31B em uma H100 (sem biblioteca open source correspondente).

Fonte: <https://www.anthropic.com/research/provable-inference>

## Quem ganha e quem perde

Ganham os provedores que querem demonstrar integridade: eles podem mostrar que servem o modelo declarado sem revelar pesos. Ganham também auditores e reguladores, que podem conferir de forma leve.

Ganham avaliadores independentes, que poderiam ter certeza do modelo testado. E clientes que pagam por um modelo específico via terceiro.

Perdem, em termos relativos, os serviços que dependem de substituição silenciosa de modelo para reduzir custo, e atacantes que adulteram o fluxo de tokens.

O custo é alto: 70 a 95 vezes mais tempo de GPU. Isso limita o uso a cenários onde a verificação vale o preço.

Fonte: <https://www.anthropic.com/research/provable-inference>

## O que ainda não se sabe

- A prova não garante veracidade da resposta, apenas que ela veio do modelo declarado.
- A prova é sobre a versão do modelo em aritmética de números inteiros, com decodificação greedy. Respostas de implementações em ponto flutuante ou com amostragem podem divergir.
- O código executável rápido (C++) não tem garantia formal de corresponder ao protocolo provado em Lean. O verificador Lean é o que carrega a garantia formal, mas é lento.
- A arquitetura do modelo não é oculta. Só os pesos ficam escondidos.
- Canais laterais (tempo de geração da prova, por exemplo) podem vazar informação sobre os pesos. Isso está fora do escopo desta versão.
- O contexto máximo é 1.024 tokens, curto para chats reais.
- O protótipo não é mantido e não aceita contribuições. É um artefato de pesquisa.

Fonte: <https://www.anthropic.com/research/provable-inference>

## O que você pode fazer hoje

1. Leia o anúncio oficial da Anthropic para entender as motivações e os casos de uso.
2. Clone o repositório e compile o verificador em CPU para ver uma prova ser aceita.
3. Rode os testes de CPU e confira o código de saída.
4. Se tiver uma H100 disponível, rode o quickstart de GPU e compare os tempos.
5. Acompanhe a área de inferência provável: zkML evoluiu de cerca de 0,001 tokens por segundo em 2023 (EZKL, transformer de 1 milhão de parâmetros) para cerca de 110 em 2026 (FlashProve, Llama 4 Maverick em uma H100).
6. Não use o protótipo em produção: ele não é mantido e tem limitações conhecidas.

Fonte: <https://www.anthropic.com/research/provable-inference>

## Glossário

- zkSNARK: zero-knowledge succinct argument of knowledge, prova criptográfica curta e rápida de verificar que não revela os pesos.
- Commitment: impressão digital curta dos pesos do modelo, publicada pelo provedor.
- Prover: quem roda o modelo e gera as provas (provedor).
- Verifier: quem confere as provas (usuário ou auditor).
- MoE: Mixture-of-Experts, arquitetura em que cada camada tem vários experts e um router ativa só alguns por token.
- Prefill: fase de processamento do prompt em paralelo.
- Zero-knowledge: propriedade de não revelar informação além do que decorre da correção da computação.
- Succinctness: propriedade de ser pequena e rápida de verificar.
- Completeness: prova honesta é aceita.
- Soundness: prova falsa é rejeitada, exceto com probabilidade desprezível.
- Lean: assistente de prova formal usado para verificar matematicamente as garantias.
- vLLM: biblioteca de inferência usada como referência de velocidade.

## Para onde ir depois

- Leia o anúncio oficial: https://www.anthropic.com/research/provable-inference
- Explore o repositório: https://github.com/anthropics/FlashProve
- Confira o modelo usado no teste: https://huggingface.co/meta-llama/Llama-4-Maverick-17B-128E-Instruct
- Compare com o vLLM: https://vllm.ai
- Conheça o Lean: https://lean-lang.org
- Acompanhe a literatura de zkML e provable inference para ver a evolução dos números.

Fonte: <https://www.anthropic.com/research/provable-inference>

## Além do vídeo

- Segundo a Anthropic, o Claude produziu melhorias em zkSNARKs para inferência; o documento de especificação do protocolo também foi escrito pelo Claude.
- A Anthropic descreve a publicação como progresso intermediário e convida outras pessoas a examinar e melhorar o trabalho.
- A meta pública da empresa de desenvolver um protótipo de inferência provável até 30 de setembro de 2026 foi cumprida, segundo ela, por um projeto separado, que assina o tráfego de inferência e recalcula a inferência em um servidor confiável.
- Ambientes de execução confiáveis, baseados em hardware, são outra abordagem, com garantias e compromissos diferentes; a Anthropic os considera complementares à criptografia.
- Para caber em uma única GPU de 80 GB, os pesos ficam na memória comum e são enviados à GPU aos poucos, e o modelo é provado um segmento de camadas por vez.
