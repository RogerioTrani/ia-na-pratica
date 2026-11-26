# Guia hands-on MoE com mais de 630 curtidas no Hugging Face

_2026-11-23 · tutorial_

O The Ultimate MoE Training Handbook é um Space do Hugging Face que explica, escolha por escolha, como treinar modelos Mixture-of-Experts em escala, apoiado em 800 mil horas de GPU e 55 figuras interativas. A apostila mostra o que é MoE, como navegar pelo guia, quais requisitos e comandos usar para reproduzir os treinos com o Megatron-LM da NVIDIA no commit d6316eb45bf1bfbb6f1f848c0b56e55166564d80, e quais cuidados conferir antes de confiar em um resultado. Você também encontra glossário, um plano de 7 dias e para onde ir depois.

## O que você terá no fim

Ao terminar esta apostila você saberá o que é um modelo Mixture-of-Experts, por que treiná-lo exige decisões diferentes do modelo denso, e como o The Ultimate MoE Training Handbook organiza essas decisões. Você terá um caminho prático para abrir o guia, navegar até a seção desejada, relacionar cada configuração às execuções apresentadas, e rodar um teste de GPU no Hugging Face Jobs. Também saberá quais ferramentas os autores usam para reproduzir os treinos em escala e quais números conferir na página oficial.

Fonte: <https://huggingface.co/spaces/huggingface/moe-blogpost>

## Como isso funciona: MoE e o handbook

Mixture-of-Experts, ou MoE, é uma arquitetura em que o modelo tem vários especialistas e ativa apenas alguns deles para cada token. Isso permite aumentar o número total de parâmetros sem aumentar proporcionalmente o custo de cada inferência ou passo de treino. A troca é que o treinamento exige roteamento, balanceamento de carga entre especialistas e paralelismo de especialistas.

O The Ultimate MoE Training Handbook é um Space do Hugging Face publicado em 5 de novembro de 2026 pelos autores Nouamane Tazi, Leandro von Werra e Thomas Wolf, da Hugging Face. A proposta é tratar o treinamento em escala escolha por escolha, mostrando os gráficos de cada configuração junto das execuções que a sustentam. Em vez de conceitos gerais, você acompanha decisões reais tomadas pelos autores.

O guia tem mais de 630 curtidas no Hugging Face e se apoia em 800 mil horas de GPU e 55 figuras interativas. O handbook é extenso e focado em análise de experimentos: ele não traz um comando único de terminal na página, mas sim o raciocínio por trás de cada escolha.

Fonte: <https://huggingface.co/spaces/huggingface/moe-blogpost>

## O que o guia cobre

O handbook organiza o conteúdo em capítulos navegáveis pelo sumário clicável. O capítulo mais útil para quem está começando é o Capítulo 2, chamado Setup and your first run, que vai da validação do hardware até a primeira execução de um MoE. Os capítulos seguintes aprofundam cada escolha de treinamento em escala.

- Seção 2.1: diagnóstico de hardware e rede, com validação dos nós e teste de banda all-to-all.
- Seção 2.2: imagem e código-base, com contêiner NGC PyTorch e checkout fixado do Megatron-LM.
- Seções 2.3 a 2.5: tokenização e baseline, com geração dos dados do FineWeb-Edu e conversão do modelo denso para o primeiro MoE.
- Demais capítulos: escolhas de treinamento em escala, cada uma com gráficos e execuções de suporte.

Fonte: <https://huggingface.co/spaces/huggingface/moe-blogpost>

## Antes de começar

Antes de abrir o guia, confira se você tem acesso ao que ele exige. O handbook é um material de leitura e análise: para reproduzir os treinos em escala você precisa de um cluster com GPUs e do ambiente descrito na Seção 2.2. Para apenas estudar, basta um navegador e tempo.

- Acesso à internet para abrir o Space The Ultimate MoE Training Handbook no Hugging Face.
- Conta no Hugging Face se quiser rodar jobs com o comando hf jobs run.
- Cluster com GPUs NVIDIA se for reproduzir os treinos em escala, com suporte a EFA e NCCL.
- Python 3.12 ou superior e PyTorch 2.6.0 ou superior, versões recomendadas pelo Megatron-LM.
- Ferramenta uv para instalar o megatron-core, se for instalar a partir do PyPI.
- Tempo para ler: o guia é longo e as figuras são interativas, então reserve mais de uma sessão.

Fonte: <https://github.com/NVIDIA/Megatron-LM>

## Passo a passo no handbook

Siga estes passos na ordem. Cada item diz a ação e o resultado esperado para você saber se deu certo.

1. Abra o Space The Ultimate MoE Training Handbook em huggingface.co/spaces/huggingface/moe-blogpost. Resultado esperado: a página do guia carrega com o sumário clicável e o conteúdo para rolagem.
2. Use o sumário clicável para ir direto à seção que deseja estudar, ou role a página para ler em sequência. Resultado esperado: você chega à seção escolhida sem precisar procurar manualmente.
3. Acompanhe as configurações apresentadas e compare os gráficos de cada escolha de treinamento com as execuções que a sustentam, num total de 800 mil horas de GPU. Resultado esperado: você consegue apontar qual execução sustenta qual escolha.
4. Para testar na prática, rode um teste rápido de GPU no Hugging Face Jobs e observe qual placa você recebeu. Resultado esperado: o comando imprime o nome ou a contagem de GPUs disponíveis.
5. Para reproduzir os treinos do guia, use o Megatron-LM da NVIDIA fixado no commit d6316eb45bf1bfbb6f1f848c0b56e55166564d80, junto com os scripts de treino publicados pelos autores. Resultado esperado: o repositório fica no commit correto e os scripts estão disponíveis na pasta de projeto.

Fonte: <https://huggingface.co/spaces/huggingface/moe-blogpost>

## Comandos para copiar

Os comandos abaixo podem ser copiados exatamente como estão. Rode o primeiro para validar o ambiente de GPU e o segundo para preparar o repositório do Megatron-LM com o commit do guia.

- Teste rápido de 8 GPUs no Hugging Face Jobs, da Seção 2.0 do guia:
- Preparação do ambiente de treino com Megatron-LM, da Seção 2.2 do guia:

```
hf jobs run --flavor h200x8 --timeout 10m \
  pytorch/pytorch:2.6.0-cuda12.4-cudnn9-devel \
  python -c "import torch; print(torch.cuda.device_count())"
git clone https://gist.github.com/nmntz/5de952d686f66d7bce5bce8cba9d7139.git "$PROJECT_DIR/scripts"
git clone https://github.com/NVIDIA/Megatron-LM.git "$SHARED_ROOT/Megatron-LM"
cd "$SHARED_ROOT/Megatron-LM" && git checkout d6316eb45bf1bfbb6f1f848c0b56e55166564d80
```

Fonte: <https://huggingface.co/spaces/huggingface/moe-blogpost>

## Teste rápido de GPU com o flavor a10g-small

Há também uma variante menor do teste de GPU, útil quando você quer apenas confirmar que uma GPU está disponível antes de rodar um treino maior. Ela roda no flavor a10g-small e imprime o nome da placa.

- Use esta variante para uma verificação rápida de GPU:
- Compare o resultado com a escolha de treinamento que você estudou no guia.

```
hf jobs run --name gpu-check --flavor a10g-small pytorch/pytorch:2.6.0-cuda12.4-cudnn9-devel python -c "import torch; print(torch.cuda.get_device_name())"
```

Fonte: <https://huggingface.co/spaces/huggingface/moe-blogpost>

## Exemplo completo: do modelo denso ao primeiro MoE

O Capítulo 2 do guia mostra um caminho completo que começa com diagnóstico de hardware e termina com a primeira conversão de um modelo denso para MoE. Este é o exemplo central para quem quer entender a prática e não apenas a teoria.

Imagine que você tem um cluster validado e o contêiner NGC PyTorch 26.06-py3 importado com Enroot e suporte a EFA e NCCL. A partir daí, o fluxo é: gerar os pares .bin e .idx do FineWeb-Edu usando Datatrove com o tokenizador Llama 3.2, rodar um modelo denso de referência em um nó com 8 GPUs, e converter esse modelo para o primeiro MoE. O resultado da conversão tem 6,86 bilhões de parâmetros totais e 1,22 bilhão de parâmetros ativos por token.

- Diagnóstico de hardware e rede na Seção 2.1: validação dos nós com dcgmi diag -r 1 --fail-early e teste de banda all-to-all via nccl-tests (alltoall_perf).
- Imagem e código-base na Seção 2.2: contêiner NGC PyTorch 26.06-py3 com Enroot e suporte EFA/NCCL, mais checkout do Megatron-LM no commit d6316eb45.
- Tokenização e baseline nas Seções 2.3 a 2.5: pares .bin e .idx do FineWeb-Edu com Datatrove e tokenizador Llama 3.2, modelo denso de referência em 1 nó com 8 GPUs, conversão para o primeiro MoE.

Fonte: <https://huggingface.co/spaces/huggingface/moe-blogpost>

## Os números do guia

Cada número abaixo vem da página oficial do Space. Use-os para dimensionar o esforço necessário e para comparar com seus próprios experimentos.

- Mais de 630 curtidas no Hugging Face.
- 800 mil horas de GPU por trás das execuções apresentadas.
- 55 figuras interativas no guia.
- 6,86 bilhões de parâmetros totais no primeiro MoE convertido a partir do baseline denso.
- 1,22 bilhão de parâmetros ativos por token nesse mesmo MoE.
- 1 nó com 8 GPUs na execução do modelo denso de referência.

Fonte: <https://huggingface.co/spaces/huggingface/moe-blogpost>

## Megatron-LM e Megatron Core

O guia usa o Megatron-LM da NVIDIA como base de código para reproduzir os treinos em escala. O repositório contém dois componentes. O Megatron-LM é um exemplo de referência que combina o Megatron Core com scripts de treino pré-configurados, indicado para equipes de pesquisa, aprendizado de treino distribuído e experimentação rápida. O Megatron Core é uma biblioteca composable com blocos otimizados para GPU, voltada a quem constrói pipelines de treino próprios.

O Megatron Core oferece blocos de transformer, estratégias de paralelismo tensor, pipeline, context, data e expert, suporte a precisão mista FP16, BF16, FP8 e FP4, e arquiteturas de modelo. O Megatron Bridge fornece conversão bidirecional de checkpoints entre Hugging Face e Megatron, com receitas prontas para produção.

- Repositório oficial: github.com/NVIDIA/Megatron-LM.
- Commit usado pelo guia: d6316eb45bf1bfbb6f1f848c0b56e55166564d80.
- Scripts de treino dos autores do handbook: gist.github.com/nmntz/5de952d686f66d7bce5bce8cba9d7139.
- Instalação a partir do PyPI: uv pip install megatron-core.
- Instalação a partir do código-fonte: git clone do repositório, cd Megatron-LM, uv pip install -e .
- Compatibilidade recomendada: Python 3.12 ou superior e PyTorch 2.6.0 ou superior.

Fonte: <https://github.com/NVIDIA/Megatron-LM>

## Benchmarks publicados pelo Megatron Core

O repositório do Megatron-LM publica resultados de throughput para modelos grandes. Eles servem como referência de desempenho sob condições publicadas e não como promessa para o seu ambiente, já que o throughput depende do modelo, da precisão, do hardware e da configuração. Os números abaixo são resultados selecionados do contêiner NeMo 26.08.01, de agosto de 2026.

- DeepSeek-V3 em DGX-GB300 com 256 GPUs, MXFP8, sequência de 4.096: 6.288 tokens por segundo por GPU e 1.636 TFLOPs por segundo por GPU.
- DeepSeek-V3 em DGX-GB200 com 256 GPUs, MXFP8, sequência de 4.096: 4.912 tokens por segundo por GPU e 1.277 TFLOPs por segundo por GPU.
- Qwen3-235B-A22B em DGX-GB300 com 256 GPUs, MXFP8, sequência de 4.096: 8.832 tokens por segundo por GPU e 1.306 TFLOPs por segundo por GPU.
- Nemotron 3 Ultra em DGX-GB300 com 256 GPUs, NVFP4, sequência de 8.192: 3.744 tokens por segundo por GPU e 1.348 TFLOPs por segundo por GPU.
- Os benchmarks de MoE usam roteamento de especialistas com balanceamento forçado e não descartam tokens.

Fonte: <https://github.com/NVIDIA/Megatron-LM>

## Teste de pronto

Use estes itens para verificar se você concluiu a exploração do handbook e do ambiente.

- [ ] Você abriu o Space The Ultimate MoE Training Handbook e viu o sumário clicável.
- [ ] Você navegou por sumário ou rolagem e chegou à seção desejada.
- [ ] Você relacionou pelo menos uma configuração às execuções que a sustentam, citando as 800 mil horas de GPU.
- [ ] Você rodou um teste de GPU no Hugging Face Jobs e viu o nome ou a contagem da placa.
- [ ] Você clonou o Megatron-LM e fez checkout no commit d6316eb45bf1bfbb6f1f848c0b56e55166564d80.
- [ ] Você localizou os scripts dos autores no gist indicado.

Fonte: <https://huggingface.co/spaces/huggingface/moe-blogpost>

## Erros comuns e cuidados

O handbook é um material de análise de experimentos, não um tutorial passo a passo com um único comando. Antes de confiar em um resultado ou reproduzir um treino, confira os pontos abaixo.

- O guia não traz um comando único de terminal na página: para reproduzir os treinos em escala use o repositório NVIDIA Megatron-LM no commit d6316eb45bf1bfbb6f1f848c0b56e55166564d80 com os scripts dos autores.
- O handbook está disponível apenas em inglês, então a navegação e os gráficos estão nesse idioma.
- Os benchmarks de throughput são medidos sob condições publicadas e dependem de modelo, precisão, hardware e configuração; não assuma o mesmo resultado no seu cluster.
- O contêiner base do guia é o NGC PyTorch 26.06-py3 com Enroot e suporte a EFA/NCCL.
- O commit do Megatron-LM deve ser exatamente d6316eb45bf1bfbb6f1f848c0b56e55166564d80; usar a branch principal pode introduzir diferenças.
- Os scripts dos autores vêm do gist indicado; não substitua por scripts de terceiros sem validar.
- A conversão do modelo denso para MoE descrita no guia tem 6,86 bilhões de parâmetros totais e 1,22 bilhão ativos por token; esse recorte vale para o caso do guia, não para qualquer MoE.
- Se a compilação do Megatron-LM a partir do código-fonte consumir muita memória, limite os jobs paralelos com MAX_JOBS, por exemplo MAX_JOBS=4.

Fonte: <https://huggingface.co/spaces/huggingface/moe-blogpost>

## Glossário

Termos técnicos usados no guia e na apostila, com definição curta em linguagem simples.

- MoE (Mixture-of-Experts): arquitetura com vários especialistas que ativa apenas alguns para cada token, aumentando parâmetros sem aumentar proporcionalmente o custo.
- Parâmetros totais: soma de todos os parâmetros do modelo, incluindo os especialistas inativos.
- Parâmetros ativos por token: parâmetros usados para processar um token específico, menor que o total em um MoE.
- Megatron-LM: exemplo de referência da NVIDIA com scripts de treino pré-configurados para transformers em escala.
- Megatron Core: biblioteca composable com blocos otimizados para GPU para construir pipelines de treino próprios.
- Megatron Bridge: ferramenta de conversão bidirecional de checkpoints entre Hugging Face e Megatron.
- NGC PyTorch: imagem de contêiner da NVIDIA com PyTorch e CUDA, usada como base do ambiente de treino.
- Enroot: ferramenta da NVIDIA para executar contêineres em clusters HPC.
- EFA: Elastic Fabric Adapter, rede de alta performance da AWS usada em clusters de treino.
- NCCL: biblioteca de comunicação coletiva da NVIDIA para GPUs.
- dcgmi: ferramenta de diagnóstico de GPUs da NVIDIA.
- alltoall_perf: teste do nccl-tests para medir banda all-to-all entre GPUs.
- FineWeb-Edu: conjunto de dados usado pelo guia para treino.
- Datatrove: biblioteca usada para processar e tokenizar os dados.
- Tokenizador Llama 3.2: tokenizador usado para gerar os pares .bin e .idx.
- Par .bin e .idx: formato de dados pré-processados consumido pelo treino.
- Commit: identificador fixo de uma versão do código, usado para reproduzir o ambiente.
- Gist: espaço do GitHub para compartilhar trechos de código, onde os autores publicaram os scripts de treino.
- Hugging Face Jobs: serviço para rodar comandos em GPUs gerenciadas pelo Hugging Face.
- Flavor: tipo de máquina de GPU oferecida pelo Hugging Face Jobs, como a10g-small ou h200x8.
- TFLOPs por segundo por GPU: medida de throughput de computação por GPU.
- MXFP8 e NVFP4: formatos de precisão de ponto flutuante de 8 e 4 bits usados nos benchmarks.
- TP, PP, DP, EP, CP: paralelismo tensor, pipeline, data, expert e context.

Fonte: <https://github.com/NVIDIA/Megatron-LM>

## Plano de 7 dias

O plano reparte em dias os passos do guia e desta apostila.

- Dia 1: abra o Space The Ultimate MoE Training Handbook e leia a introdução e o sumário.
- Dia 2: navegue pelas seções do Capítulo 2 usando o sumário clicável ou a rolagem.
- Dia 3: estude a Seção 2.1 de diagnóstico de hardware e rede e anote os comandos dcgmi e nccl-tests.
- Dia 4: estude a Seção 2.2 de imagem e código-base e prepare o contêiner NGC PyTorch.
- Dia 5: estude as Seções 2.3 a 2.5 de tokenização e baseline e entenda a conversão denso para MoE.
- Dia 6: rode um teste de GPU no Hugging Face Jobs e compare com a escolha estudada.
- Dia 7: clone o Megatron-LM no commit correto, localize os scripts dos autores e revise os cuidados da apostila.

Fonte: <https://huggingface.co/spaces/huggingface/moe-blogpost>

## Para onde ir depois

Depois de concluir a exploração do handbook, você pode aprofundar em três frentes.

- Aprofunde em paralelismo: leia o guia de estratégias de paralelismo do Megatron Core, que cobre TP, PP, DP, EP e CP.
- Estude reprodução de treinos: consulte a página de performance do Megatron Bridge para throughput, configurações e instruções de reprodução.
- Acompanhe as novidades do repositório: Megatron Bridge será unificado ao Megatron-LM e a versão 0.19.0 traz HybridModel e balanceamento de roteador MoE por quantis.
- Se for implementar MoE próprio, comece pelo Megatron Core instalado via uv pip install megatron-core e confira as versões recomendadas, Python 3.12+ e PyTorch 2.6.0+.
- Volte ao sumário do handbook e escolha a próxima configuração de treinamento para analisar, sempre relacionando a escolha às execuções apresentadas.

Fonte: <https://github.com/NVIDIA/Megatron-LM>

## O que muda para você

O guia concentra as decisões em um só lugar e mostra as execuções que as sustentam. Para quem está aprendendo, isso reduz o risco de copiar uma configuração sem entender o porquê. Para quem já treina modelos, o valor está em comparar suas próprias escolhas com as apresentadas e em ter um commit fixo e scripts oficiais para reproduzir.

Fonte: <https://huggingface.co/spaces/huggingface/moe-blogpost>

## Links citados

- https://huggingface-moe-blogpost.hf.space/

## Além do vídeo

- Em julho de 2026, o repositório noticiou que o Megatron Core alcançou 1.648 TFLOPs por segundo por GPU no pré-treino do DeepSeek-V3 671B em 256 GPUs GB300 NVL72.
- Desde maio de 2026, o branch dev do Megatron Core inclui uma implementação inicial do DeepSeek-V4, e o Megatron Bridge oferece receitas de conversão, inferência e pré-treino.
- Em abril de 2026, o Megatron Core passou a suportar o Muon e outros otimizadores emergentes por meio da biblioteca Emerging-Optimizers.
- O repositório publica roadmaps do terceiro trimestre de 2026 para o Megatron Core, para MoE e para o Megatron FSDP v2, este último experimental.
- No repositório, a pasta megatron/core reúne o Megatron Core, megatron/training guarda os scripts de treino e examples traz exemplos prontos.
- Para citar o Megatron em pesquisa, o repositório indica o artigo Megatron-LM: Training Multi-Billion Parameter Language Models Using Model Parallelism, de 2019.
