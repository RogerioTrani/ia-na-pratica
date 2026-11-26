# Motif-3 e o custo de colocar experts para trabalhar

_2026-11-25 · reportagem_

O Motif-3 reúne 314 bilhões de parâmetros e ativa 13,2 bilhões por token. A cada token, o modelo escolhe quais especialistas entram em ação, em uma arquitetura de mistura de especialistas. Nos testes, marca 83,4 em GPQA e 76,2 em SWE-bench. O custo cai porque poucos experts ligam; errar a escolha custa qualidade na resposta.

## O que é o Motif-3

O Motif-3 é um modelo de linguagem decoder-only com 314 bilhões de parâmetros no total. A cada token, ativa 13,2 bilhões de parâmetros.

O modelo foi desenvolvido do zero pela Motif Technologies, com projeto interno e proprietário.

Fonte: <https://huggingface.co/Motif-Technologies/Motif-3>

## Como funciona a mistura de especialistas

O modelo é um MoE, uma mistura de especialistas. Para cada token, escolhe um grupo pequeno de partes para trabalhar; as outras ficam paradas.

- A cada token, o modelo escolhe quais especialistas ativam.
- As partes não escolhidas ficam paradas nesse token.
- Só 13,2 bilhões de parâmetros entram em ação por token. Menos conta para calcular, mais velocidade na resposta.

Fonte: <https://huggingface.co/Motif-Technologies/Motif-3>

## Por dentro da arquitetura

O modelo usa atenção comprimida e uma cabeça que antecipa tokens para treinar melhor. Juntas, essas peças melhoram a estabilidade de otimização, a especialização dos especialistas e a eficiência de inferência.

- Grouped Differential Latent Attention (GDLA): atenção diferencial agrupada com a representação comprimida de chave e valor da Multi-head Latent Attention.
- modified manifold-constrained hyper-connections (mHC).
- Expert-Specific PolyNorm activations.
- Multi-Token Prediction (MTP) head, que antecipa tokens no treino.

Fonte: <https://huggingface.co/Motif-Technologies/Motif-3>

## Como foi treinado

O pré-treinamento usou cerca de 12,5 trilhões de tokens.

- Documentos da web, STEM, código, matemática, conteúdo multilíngue e corpora especializados.
- Mais peso para coreano, tarefas que exigem raciocínio, jurídico e financeiro.

Fonte: <https://huggingface.co/Motif-Technologies/Motif-3>

## Os números dos testes

O modelo marca 83,4 em questões de ciência e 76,2 em correção de código.

- GPQA: 83,4
- SWE-bench: 76,2
- IFBench: 78,2
- Terminal: 74,9

Fonte: <https://huggingface.co/Motif-Technologies/Motif-3>

## O ponto fraco

Ativar poucos parâmetros só compensa se o modelo escolher os especialistas certos para cada tarefa. O custo cai porque poucos experts ligam. Errar a escolha custa qualidade na resposta.

Fonte: <https://huggingface.co/Motif-Technologies/Motif-3>

## Onde encontrar o modelo

O repositório oficial do Motif-3 fica no Hugging Face.

```
huggingface.co/Motif-Technologies/Motif-3
```

Fonte: <https://huggingface.co/Motif-Technologies/Motif-3>

## Além do vídeo

- HLE: 37 no conjunto de avaliações do modelo, resultado que ficou de fora do gráfico do vídeo.
- Licença MIT, com o arquivo LICENSE.md no repositório.
- Modelo base: Motif-Technologies/Motif-3-Base.
- Idiomas marcados no repositório: inglês e coreano, com tag multilingual.
- Relatório técnico: Motif 3: Technical Report (arxiv:2608.09119).
