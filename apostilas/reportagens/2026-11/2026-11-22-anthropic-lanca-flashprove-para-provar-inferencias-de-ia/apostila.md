# Anthropic lança FlashProve para provar inferências de IA

_2026-11-22 · reportagem_

A Anthropic lançou o FlashProve, protótipo de código aberto que usa provas criptográficas (zkSNARKs) para confirmar que uma resposta saiu do modelo declarado, sem expor os pesos. No teste com o Llama 4 Maverick, uma única GPU H100 gera provas a cerca de 110 tokens por segundo. O custo é alto: de 70 a 95 vezes o tempo de GPU do vLLM, e cerca de 18,78 MB de prova a cada janela de 1.024 tokens. Esta apostila traz os números, as condições do teste e os passos para reproduzir.

## O problema: quem respondeu?

Quem consulta um modelo hoje não tem como checar que a resposta veio do modelo que o provedor declara. Um serviço de roteamento pode trocar o modelo por outro mais barato, e um atacante que adultere o fluxo de tokens também passa despercebido. Julgar pela qualidade do texto não resolve, porque uma resposta convincente não prova quais pesos a geraram.

Isso pesa para quem paga por um modelo específico, para avaliadores independentes que precisam saber se testam o modelo que está no ar e para quem usa um modelo por um serviço de terceiros.

Fonte: <https://www.anthropic.com/research/provable-inference>

## Como a prova funciona

O provedor se compromete com um modelo e, a cada resposta, envia um certificado criptográfico. O usuário confere o certificado com poucos recursos: se a resposta fugir do modelo declarado, a checagem falha.

A técnica é o zkSNARK. O certificado não revela os pesos do modelo e é muito mais rápido de verificar do que a computação provada. Esconder a arquitetura do modelo não é objetivo do sistema.

Fonte: <https://www.anthropic.com/research/provable-inference>

## Os números e as condições do teste

Em uma única GPU H100, a geração de provas chega a cerca de 110 tokens por segundo. O número vale para esta configuração e não para qualquer modelo.

- Modelo: Llama 4 Maverick (huggingface.co/meta-llama/Llama-4-Maverick-17B-128E-Instruct)
- 400 bilhões de parâmetros, mistura de especialistas
- Pesos em 4 bits
- Aritmética inteira no prefill

Fonte: <https://huggingface.co/meta-llama/Llama-4-Maverick-17B-128E-Instruct>

## O preço: GPU e tamanho da prova

Gerar as provas consome entre 70 e 95 vezes o tempo de GPU que o vLLM (vllm.ai) leva para processar prompts do mesmo tamanho. Tomando o vLLM como 1, o FlashProve fica entre 70 e 95.

Cada janela de 1.024 tokens produz cerca de 18,78 MB de prova, que viajam junto com a resposta.

- vLLM (referência): 1
- FlashProve, limite inferior divulgado: 70
- FlashProve, limite superior divulgado: 95

Fonte: <https://www.anthropic.com/research/provable-inference>

## O que vem no lançamento

Tudo sai sob licença Apache 2.0. O verificador em Lean é formalmente provado correto, e os teoremas de nível mais alto podem ser auditados com um visualizador interativo.

- Gerador de provas
- Verificador rápido em C++
- Verificador em Lean
- Especificação do protocolo
- Relatório técnico
- Visualizador interativo dos teoremas

Fonte: <https://github.com/anthropics/FlashProve>

## Como reproduzir

O gerador de provas é pesado. O verificador roda só em CPU e confere uma prova em 17 s com 24 threads.

- Prover: 1 GPU H100 de 80 GB, 24 núcleos de CPU e cerca de 290 GB de RAM
- Download manual dos pesos de 4 bits no Hugging Face (huggingface.co)
- Verificador: só CPU
- Clone o repositório e compile o verificador com os comandos abaixo

Fonte: <https://github.com/anthropics/FlashProve>

## O que a prova não garante

A prova confirma que a execução foi feita pelo modelo declarado. Ela não garante que a resposta seja verdadeira.

A Anthropic apresenta o trabalho como progresso intermediário, com custo computacional ainda elevado, e pede que outros pesquisadores peguem o código e o melhorem.

Fonte: <https://www.anthropic.com/research/provable-inference>

## Além do vídeo

- Uso em regulação: um regulador pode pedir certificados das requisições atendidas num período e checar que o hardware serviu o modelo declarado, mas isso não mostra que o hardware não esteja treinando em paralelo.
- Detecção de adulteração: um servidor comprometido, ou um modelo que se faça passar por outro, não consegue produzir provas válidas para os pesos esperados.
- Proveniência de texto: dá para provar que um relatório ou análise foi feito por determinado modelo, o que logs de chat publicados não garantem.
- Sistemas anteriores de código aberto são ordens de magnitude mais lentos, segundo a Anthropic.
- A Anthropic cumpriu a meta de protótipo do Frontier Safety Roadmap por um projeto separado, que assina o tráfego de inferência e recalcula a inferência em servidor confiável.
