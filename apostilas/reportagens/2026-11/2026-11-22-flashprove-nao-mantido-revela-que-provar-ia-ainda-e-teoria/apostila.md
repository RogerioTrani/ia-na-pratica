# FlashProve não mantido revela que provar IA ainda é teoria

_2026-11-22 · reportagem_

FlashProve é um protótipo de pesquisa para provas de conhecimento zero de inferência de IA, e o próprio repositório o declara não mantido. Ele traz código de prova e verificação e uma configuração de referência com Llama 4 Maverick em uma H100. Em Lean 4 estão provadas as propriedades do protocolo; os programas que o executam são apenas testados. A leitura que as evidências sustentam vale para este projeto, não para toda a área de IA verificável.

## Status do projeto

A descrição oficial define o FlashProve como um protótipo de pesquisa para provas de conhecimento zero de inferência de IA e traz o aviso "Not maintained". O repositório também informa que não aceita contribuições.

Na prática, quem o encontra tem uma proposta documentada para estudar, sem manutenção contínua por trás.

Fonte: <https://github.com/anthropics/FlashProve>

## O que o repositório traz

O repositório tem código de prova e verificação e uma configuração de referência.

- Modelo: Llama 4 Maverick
- Hardware: uma H100
- Contexto: 1.024 tokens
- Licença: Apache 2.0
- Versão: 0.16.0

Fonte: <https://github.com/anthropics/FlashProve/tree/main>

## Onde ler a parte técnica

A pasta paper reúne o documento técnico desta versão: o protocolo, o que é provado em Lean e o que não é, e as medições. A página informa que a versão alega apenas o que o paper e os outros documentos do repositório dizem.

- Pasta do paper: https://github.com/anthropics/FlashProve/tree/main/paper
- Documento: https://github.com/anthropics/FlashProve/blob/main/paper/paper.pdf

Fonte: <https://github.com/anthropics/FlashProve/tree/main/paper>

## O que foi provado e o que foi testado

As provas estão em Lean 4 (https://lean-lang.org), no modelo de oráculo aleatório. O protocolo usa um modelo inteiro, e nenhuma prova mede quão perto ele fica do modelo de ponto flutuante.

- Provado: soundness, completeness e zero-knowledge do protocolo.
- Não provado, apenas testado: o verificador em C++ (cp_verify), o prover em CUDA (cp_prove) e o committer (cp_commit).
- Sem prova: a distância entre o modelo inteiro e o ponto flutuante.

Fonte: <https://github.com/anthropics/FlashProve/blob/main/lean/THEOREM.md>

## Como ler o caso

O FlashProve é um protótipo de pesquisa não mantido, com código e uma configuração de referência. A conclusão cabe a ele. Usá-lo para afirmar que toda IA verificável existe só no papel iria além do que a evidência mostra.

Ao avaliar uma proposta parecida, cruze três pontos: a promessa, o que está provado e a condição de uso.

Fonte: <https://github.com/anthropics/FlashProve>

## Links oficiais

- Repositório: https://github.com/anthropics/FlashProve
- Pasta do paper: https://github.com/anthropics/FlashProve/tree/main/paper
- paper.pdf: https://github.com/anthropics/FlashProve/blob/main/paper/paper.pdf
- Provas em Lean: https://github.com/anthropics/FlashProve/tree/main/lean
- Teorema de soundness: https://github.com/anthropics/FlashProve/blob/main/lean/THEOREM.md
- Lean: https://lean-lang.org

## Além do vídeo

- Licença Apache 2.0 e versão 0.16.0 do repositório.
- Link direto para o paper.pdf.
- Pasta lean com as provas e o arquivo THEOREM.md.
