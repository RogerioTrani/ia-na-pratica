# FlashProve: protótipo não mantido prova qual modelo respondeu

_2026-11-22 · reportagem_

O FlashProve é um protótipo de pesquisa da Anthropic para provas de conhecimento zero sobre inferência de IA: permite provar qual modelo respondeu a uma requisição sem revelar os pesos. A versão 0.16.0 roda o Llama 4 Maverick em uma H100, tem partes provadas em Lean 4, e se declara explicitamente não mantida, sem aceitar contribuições. Depois de ler, você entenderá a diferença entre protocolo provado e implementação testada, saberá o que foi e o que não foi demonstrado, e terá os comandos para compilar o verificador e checar uma prova.

## O contexto

O FlashProve é um protótipo de pesquisa publicado em github.com/anthropics/FlashProve. Ele permite a um provedor de IA provar qual modelo respondeu a uma requisição sem revelar os pesos do modelo. A versão atual é a 0.16.0, distribuída sob licença Apache 2.0, e o repositório se declara explicitamente como artefato de pesquisa: não é mantido e não aceita contribuições.

A promessa técnica tem base concreta: a configuração de referência roda o Llama 4 Maverick em tamanho completo. As ressalvas estão no alcance da prova formal, detalhado adiante, e na condição de uso. Trata-se de um artefato de pesquisa, não de um serviço com manutenção, suporte e garantias de operação contínua.

O caso serve para discutir a distância entre uma proposta documentada e algo que opere no dia a dia. Concluir, a partir dele, que toda a verificabilidade de IA existe apenas no papel seria ampliar a conclusão além da evidência: o projeto tem código, uma configuração de referência e partes provadas formalmente, e ainda assim se declara um protótipo não mantido.

Fonte: <https://github.com/anthropics/FlashProve>

## O que é o FlashProve

Em termos simples, o FlashProve responde à pergunta: como provar que uma resposta veio de um modelo específico sem mostrar o modelo? A resposta usa provas de conhecimento zero (zero-knowledge proofs) sobre a inferência de IA.

O ciclo tem três etapas. Commit: o provedor publica um identificador de compromisso (commitment ID) que o vincula a um conjunto de pesos; os pesos permanecem secretos e todo valor publicado que depende deles é mascarado, exceto uma lista declarada. Prove: para cada resposta, a GPU do provedor gera uma prova de que a resposta é a saída do modelo comprometido. Verify: qualquer pessoa verifica a prova em uma CPU comum em segundos, usando cp_verify, sem ter acesso aos pesos.

Quem verifica não precisa confiar no provedor nem rodar o modelo. Basta conferir a prova contra o commitment ID obtido de uma fonte confiável.

Fonte: <https://github.com/anthropics/FlashProve>

## O modelo de referência

A configuração de referência do FlashProve roda o Llama 4 Maverick em tamanho completo, com janela de contexto de 1.024 tokens, em uma única GPU NVIDIA H100. O prover atinge cerca de 110 tokens por segundo de prefill em lotes de 24 requisições.

Essa configuração é um artefato de pesquisa, não um serviço. Ela documenta que o protocolo funciona em escala real de modelo, mas não oferece manutenção, suporte nem garantias de disponibilidade.

Fonte: <https://github.com/anthropics/FlashProve>

## O que foi provado formalmente

A soundness do protocolo é provada em Lean 4, na página lean/THEOREM.md do repositório. A prova assume o modelo de oráculo aleatório e estabelece três propriedades do protocolo: soundness, completeness e zero-knowledge.

Soundness: um provedor que tentar passar uma saída que não é do modelo comprometido é detectado, exceto com probabilidade aproximada de q/2^124 + 2^-101 após q consultas de hash. Completeness: erro de no máximo 2^-40. Zero-knowledge: válido para uma requisição por vez.

As provas formais assumem três condições: modelo de oráculo aleatório, correspondência exata (exact match) e arquivos públicos fixos. Fora dessas condições, as garantias não se aplicam.

Fonte: <https://github.com/anthropics/FlashProve/blob/main/lean/THEOREM.md>

## O que não foi provado

A distinção entre o que está provado em Lean e o que é apenas testado é o ponto central do projeto. Os itens abaixo são o que fica de fora da prova formal.

- O verificador rápido em C++ (cp_verify) e o prover em CUDA (cp_prove) não são provados em Lean; são apenas testados.
- O committer (cp_commit) também não é provado em Lean; é apenas testado.
- Zero-knowledge em lotes (batching) fica fora da prova formal; a prova cobre uma requisição por vez.
- A política tolerante de diferença (clipped gap, reportada como WITHIN LIMITS) não é coberta pela prova formal.
- O protocolo trabalha com um modelo inteiro (integer model); nenhuma prova mede a distância entre esse modelo e o modelo de ponto flutuante usado na prática.

Fonte: <https://github.com/anthropics/FlashProve/blob/main/guide/what-is-proved.md>

## As medições publicadas

O paper (paper/paper.pdf) reúne o protocolo, a delimitação do que é provado em Lean e do que não é, além das medições desta versão. A página do paper afirma que as alegações desta release se limitam ao que está escrito no paper e nos demais documentos do repositório.

- Llama 4 Maverick 4-bit, 1.024 tokens, em uma H100: cerca de 110 tokens/s de prefill em lote de 24.
- Custo relativo: 70x a 95x o tempo de GPU do vLLM.
- Tamanho da prova: cerca de 19 MB.
- Verificação em CPU: cerca de 17 segundos com 24 threads.

Fonte: <https://github.com/anthropics/FlashProve/tree/main/paper>

## Como funciona na prática

Um cenário concreto: um provedor publica um commitment ID para um modelo. Um usuário obtém esse ID de uma fonte em quem confia, monta o arquivo de requisição, roda cp_verify com os arquivos da prova e lê o código de saída. Se for 0 com 'YES' ou 'WITHIN LIMITS', a prova foi aceita; se for 1 com 'NO', foi rejeitada. O exemplo armazenado no repositório usa um modelo pequeno com pesos sintéticos e atesta apenas que o verificador funciona, não diz nada sobre um modelo servido.

O commitment ID nunca deve vir do servidor verificado nem dos arquivos enviados com a prova. As provas armazenadas são a única exceção.

Fonte: <https://github.com/anthropics/FlashProve>

## Build do verificador

O primeiro passo para usar o FlashProve é compilar o verificador cp_verify, que roda em CPU comum e não exige GPU.

1. Execute o comando; ele fica silencioso por 1 a 2 minutos.
2. Código de saída 0 e linha começando em 'THE VERIFIER IS BUILT:' indicam sucesso.
3. Linha começando em 'build.sh: note:' é aviso, não erro.
4. Se a ferramenta expirar por tempo, rode em segundo plano com nohup e acompanhe com tail; não inicie um segundo build.

```
verifier/build.sh
```

Fonte: <https://github.com/anthropics/FlashProve>

## Verificação da prova de exemplo

Com o verificador compilado, confira a prova armazenada no repositório. O exemplo usa um modelo pequeno com pesos sintéticos.

1. Última linha esperada: 'YES', código de saída 0.
2. O exemplo não diz nada sobre um modelo servido em produção.

```
bin/cp_verify examples/accepted-proof/config examples/accepted-proof/ivk examples/accepted-proof/example.req examples/accepted-proof/example.y examples/accepted-proof/example.proof -id "$(cat examples/accepted-proof/ID.txt)"
```

Fonte: <https://github.com/anthropics/FlashProve>

## Verificação de uma prova real

Para verificar uma prova real, use bin/cp_verify com o diretório de configuração, o diretório da chave pública, o arquivo de requisição, o arquivo de tokens, o arquivo de prova e o commitment ID.

O arquivo de requisição deve ser montado pelo próprio verificador, conforme o guia 'Verify a proof'.

- 0, última linha 'YES' ou 'WITHIN LIMITS: …': aceita (correspondência exata ou diferença tolerada).
- 1, última linha 'NO: <nome>': rejeitada (ou falha local).
- 5, 'NOT CHECKED: <nome>': sem veredito; repetir uma vez apenas para 'internal-stage' ou 'internal-exception-parFor', caso contrário reportar.
- 14, 'NOT-A-VERIFICATION': chamada inválida; ver linhas após '---- the call ----'.
- 2, 3, 4 ou 15: linha de comando ou arquivo inválido, ou chamada parcial; sem veredito.

```
bin/cp_verify CONFIG_DIR PUBLIC_KEY_DIR REQUEST_FILE TOKEN_FILE PROOF_FILE -id COMMITMENT_ID
```

Fonte: <https://github.com/anthropics/FlashProve>

## As rotas de execução

O repositório documenta quatro rotas, da mais leve à mais pesada. A rota 1 exige apenas o verificador; as rotas 3 e 4 exigem a pilha de GPU.

- Rota 1 — Verificar prova armazenada: compila cp_verify e checa a prova de exemplo. Linux, bash, g++ 13+; menos de 2 GB de RAM. Build de 1 a 2 minutos, verificação em menos de 2 segundos.
- Rota 2 — Provas de brinquedo (CPU): auto-teste da biblioteca de provas na CPU. Exige a rota 1 mais make e python3; menos de 1,5 GB de RAM. Cerca de 1 minuto.
- Rota 3 — Modelo pequeno: compila o prover; compromete, prova e verifica um modelo sintético de 8 camadas. Pilha de GPU; 10 GB de RAM. Build de cerca de 29 minutos, execução de 23 a 30 segundos.
- Rota 3, tamanho completo: mesmo fluxo na forma do Llama 4 Maverick, com pesos sintéticos e 1.001 tokens. Pilha de GPU; 280 GB de RAM. Cerca de 42 minutos.
- Rota 4 — Llama 4 Maverick: baixa uma conversão pública em 4 bits (232 GB) e prova um token. Pilha de GPU, curl, Python 3.13; 330 GB de RAM, 245 GB de disco; exige um conjunto de calibração criado antes. Leva horas.

Fonte: <https://github.com/anthropics/FlashProve>

## Requisitos da pilha de GPU

As rotas 3 e 4 só rodam na pilha de GPU suportada.

- Linux x86-64, kernel 4.14 ou posterior, em CPU com extensões SHA.
- Uma NVIDIA H100 de 80 GB, usada por nenhum outro processo.
- CUDA 13.2 Update 2 (nvcc 13.2.86) no PATH.
- gcc e g++ 13 primeiro no PATH; binutils, flock, python3.
- Repositório e diretórios de trabalho em disco local.
- Em Ubuntu 24.04 mínimo, as dependências das rotas 1 e 2 são as do comando abaixo.

```
apt-get update && apt-get install -y --no-install-recommends g++ make python3 unzip
```

Fonte: <https://github.com/anthropics/FlashProve>

## Como rodar o modelo pequeno em GPU

Após compilar o verificador, a rota do modelo pequeno compromete, prova e verifica uma requisição de 64 tokens.

1. Execute examples/quickstart-gpu.sh; ele compila cp_verify, cp_commit e cp_prove e roda o fluxo completo.
2. Pode ficar silencioso por mais de 15 minutos; o log vai para quickstart-gpu.log no diretório anunciado primeiro.
3. Sucesso: código de saída 0 e linha começando em 'quickstart-gpu: all steps ended as expected'.
4. Confira que toda linha 'Compiled by' termina em 'release 13.2, V13.2.86'. Um nvcc mais novo não interrompe o build, mas não é suportado.
5. Para o tamanho completo após o build: execute prover/examples/run_target_example.sh target_full_f2 com um diretório de trabalho; espere 'status 0', uma linha 'proof of work:' e 'YES'. Com pouca memória, sai com código 2 no início.

```
examples/quickstart-gpu.sh
```

Fonte: <https://github.com/anthropics/FlashProve>

## Provas de brinquedo na CPU

A rota 2 é o auto-teste da biblioteca de provas na CPU.

1. Código de saída 0 e a terceira linha a partir do fim começando em 'AS EXPECTED: the honest copy was accepted'.

```
W=$(mktemp -d) && LOOK="$W/look" && echo "LOOK=$LOOK"
blocks/first_look.sh "${LOOK:?first run the line with mktemp}"
```

Fonte: <https://github.com/anthropics/FlashProve>

## Construído para ser rodado por um agente

O repositório foi pensado para ser operado por um agente de programação: builds longos e muitas comparações exatas. O ponto de partida sugerido é ler README.md a partir de 'For agents' e AGENTS.md, rodar como usuário comum (nunca root), compilar o verificador, checar a prova de exemplo e reportar código de saída e última linha.

```
Read README.md in the FlashProve repository, starting at "For agents", and AGENTS.md. Working from
the repository root as an ordinary (non-root) user, build the verifier, check the stored example
proof, and report the exit code and last line. Then tell me which other routes (toy proofs on CPU,
small model on an H100, full size) this machine can run, and ask me before starting any of them.
```

Fonte: <https://github.com/anthropics/FlashProve>

## Regras de operação

Quem roda o FlashProve precisa seguir as regras documentadas no repositório.

- Nunca contorne um erro com sudo, chmod, chown, rm ou editando arquivo de fonte. Pare e pergunte ao usuário.
- Não compile o diretório prover/ a menos que a tarefa exija.
- Reporte o comando exato, o código de saída e a última linha completa. Para prova aceita, reporte também o commitment ID usado e as linhas 'covered:' e 'result-v1'.
- A suíte de testes CPU (D=$(mktemp -d) && ./run_suite.py cpu "$D/work") sobrescreve bin/cp_verify e bin/weight_sums; código 0 passa, 77 faltam ferramentas, 3 indica algo falso aceito (reportar conforme SECURITY.md).

Fonte: <https://github.com/anthropics/FlashProve>

## Quem ganha e quem perde

Ganham pesquisadores e provedores que precisam demonstrar qual modelo atendeu a uma requisição sem expor pesos: o protocolo oferece uma rota verificável, com código e uma configuração de referência que roda em hardware real.

Perdem quem espera um produto: o repositório é não mantido, não aceita contribuições e não oferece suporte. Quem depender dele assume o risco de manter o código e de validar as partes não provadas.

A área como um todo não pode ser julgada por este caso: o FlashProve documenta um protótipo, não o estado de toda a pesquisa em IA verificável.

Fonte: <https://github.com/anthropics/FlashProve>

## O que ainda não se sabe

Alguns pontos ficam fora do que está demonstrado e merecem atenção antes de qualquer uso.

- Distância para o ponto flutuante: o protocolo trabalha com um modelo inteiro, e nenhuma prova mede quão perto ele fica do modelo de ponto flutuante.
- Zero-knowledge em lotes: não está demonstrado formalmente, porque a prova cobre uma requisição por vez.
- Correção do prover e do verificador rápidos: não há prova formal, pois eles são apenas testados.
- O compromisso com um modelo próprio exige leitura obrigatória de Serving e das obrigações do provedor antes de usar pesos que devem permanecer secretos.

Fonte: <https://github.com/anthropics/FlashProve/blob/main/guide/what-is-proved.md>

## O que você pode fazer

Passos práticos para quem quer entender ou avaliar o FlashProve.

1. Ler o repositório em github.com/anthropics/FlashProve, começando por README.md e AGENTS.md.
2. Ler o paper em paper/paper.pdf e o teorema em lean/THEOREM.md para entender o que é e o que não é provado.
3. Compilar o verificador e checar a prova de exemplo (rota 1) para confirmar que o ambiente funciona.
4. Se houver GPU H100 disponível, rodar a rota do modelo pequeno (quickstart-gpu.sh) e, depois, o tamanho completo.
5. Antes de depender do código, considerar o aviso de projeto não mantido e limitar o uso aos cenários de pesquisa documentados.
6. Para verificar provas reais, obter o commitment ID de fonte confiável e montar o arquivo de requisição conforme o guia 'Verify a proof'.

Fonte: <https://github.com/anthropics/FlashProve>

## Glossário

- Prova de conhecimento zero (zero-knowledge proof): prova criptográfica de que uma afirmação é verdadeira sem revelar a informação por trás dela.
- Commitment ID: identificador que vincula o provedor a um conjunto de pesos do modelo.
- Soundness: propriedade de que uma afirmação falsa não passa pela verificação, exceto com probabilidade desprezível.
- Completeness: propriedade de que uma afirmação verdadeira passa pela verificação, exceto com uma probabilidade de erro muito pequena.
- Modelo de oráculo aleatório (ROM): modelo teórico em que funções hash se comportam como oráculos verdadeiramente aleatórios.
- Inferência: execução de um modelo de IA para produzir uma resposta a partir de uma entrada.
- Prefill: fase da inferência em que o modelo processa o prompt de entrada.
- cp_verify: verificador em C++ que checa provas em CPU comum.
- cp_prove: prover em CUDA que gera provas na GPU.
- cp_commit: programa que cria o compromisso com os pesos.
- Lean 4: linguagem de prova formal usada para verificar o protocolo.
- Exact match: verificação que exige correspondência exata entre saída provada e saída esperada.
- Clipped gap (WITHIN LIMITS): política tolerante que aceita pequenas diferenças entre saída provada e saída esperada.
- H100: GPU NVIDIA usada como plataforma de referência.

Fonte: <https://github.com/anthropics/FlashProve>

## Para onde ir depois

- Repositório oficial: github.com/anthropics/FlashProve.
- Paper: paper/paper.pdf (protocolo, o que é provado, o que não é e medições).
- Provas em Lean: pasta lean/ e lean/THEOREM.md.
- Guia de início: guide/getting-started.md.
- Como funciona: guide/how-it-works.md.
- Verificar uma prova: guide/verify-a-proof.md.
- O que é provado: guide/what-is-proved.md.
- Limites conhecidos: guide/known-limits.md, docs/limits.md, docs/limits-further.md, lean/LIMITS.md.
- Performance: guide/performance.md.
- Servir um modelo: guide/serving.md e docs/operators-duties.md.
- Segurança: SECURITY.md.
- Termos: guide/terms.md.

Fonte: <https://github.com/anthropics/FlashProve>

## Links citados

- https://github.com/anthropics/FlashProve/blob/main/paper/paper.pdf
- https://github.com/anthropics/FlashProve/tree/main/lean
- https://lean-lang.org
