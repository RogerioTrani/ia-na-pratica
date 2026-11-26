# Agentes Gemini 4 aprimoram algoritmos quânticos com Lean

_2026-11-25 · reportagem_

Equipes de agentes Gemini 4 melhoraram algoritmos quânticos e provaram cada resultado em Lean. No caso da fusão inercial, o custo caiu 11,8× e a memória foi de 5.650 para 4.338 qubits. A biblioteca, os problemas e as soluções provadas estão em um repositório público no GitHub.

## Circuitos difíceis de testar

Computadores comuns não rodam esses circuitos, e os processadores quânticos atuais são pequenos. A saída foi provar cada resultado com matemática, usando o Lean, um verificador de provas.

Fonte: <https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/>

## Como as equipes de agentes trabalham

- Cada equipe busca melhorias para o seu problema de forma independente.
- As ideias passam pelo Lean antes de entrar em um caderno compartilhado.
- A cada quatro horas, as equipes se reúnem em uma conferência virtual para trocar, debater e comparar ideias.
- Conforme as ideias melhoram, o custo computacional cai.

Fonte: <https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/>

## Fusão por confinamento inercial

O caso era a fusão por confinamento inercial, em que lasers comprimem hidrogênio até acender. As equipes de agentes melhoraram um circuito que calcula uma propriedade importante dessa reação.

- Custo computacional (qubits e operações): queda de 11,8×.
- Memória: de 5.650 para 4.338 qubits com correção de erros.

Fonte: <https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/>

## Moléculas e remédios

As equipes também reduziram o custo de simular moléculas do metabolismo de remédios e certas reações fotochímicas, difíceis para computadores clássicos.

- Molécula sensível à luz: simulação 8× mais barata, com simplificação no rastreamento de posições de partículas e forças elétricas.
- Citocromo P450, enzima que quebra a maioria dos remédios humanos: melhora de 2,5×.

Fonte: <https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/>

## Algoritmos e aritmética

- Grover: ganho de 2,57× em uma implementação específica do algoritmo, usado para buscar em lista não ordenada.
- Arcseno: ganho de 290× em rotina usada por muitos algoritmos quânticos para carregar números em estados quânticos.

Fonte: <https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/>

## Ciência aberta no GitHub

A biblioteca em Lean, os problemas e as soluções provadas saíram em um repositório público no GitHub. Outra equipe pode usar o mesmo método e conferir os resultados.

Fonte: <https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/>

## O limite atual

Rodar esses algoritmos em simulações científicas ainda pede mais recursos do que os primeiros computadores quânticos com correção de erros devem oferecer. Ainda assim, o ganho é real.

Fonte: <https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/>

## Além do vídeo

- A pesquisa foi uma colaboração entre Google DeepMind e Google Quantum AI, assinada pelos autores do paper e por colaboradores reconhecidos na publicação.
- O método não se limita a energia limpa e design de remédios: pode acelerar outras áreas da computação quântica e a descoberta científica de forma mais ampla.
- A busca com provas checadas comprime um trabalho que antes levava anos de projeto manual e deixa pesquisadores livres para escolher problemas e interpretar resultados.
- No Citocromo P450, a memória caiu de 481 para 333 qubits com a substituição de buscas de memória volumosas.
