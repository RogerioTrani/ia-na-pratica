# Agentes Gemini 4 aprimoram algoritmos quânticos com Lean

_2026-11-24 · reportagem_

O Google DeepMind colocou equipes de agentes Gemini 4 para melhorar algoritmos quânticos conhecidos, e cada melhoria só valeu depois de provada em Lean, um verificador formal. O custo da simulação de fusão por confinamento inercial caiu 11,8 vezes e a memória exigida foi de 5.650 para 4.338 qubits com correção de erros. Houve ganhos também em química, em remédios, no algoritmo de Grover e na rotina arcsin. A biblioteca Lean, as especificações dos problemas e as soluções verificadas estão abertas no GitHub.

## O problema: faltam recursos

Mesmo com os melhores algoritmos, algumas aplicações importantes pedem mais qubits e operações do que as primeiras máquinas quânticas vão ter. Reduzir esse custo no papel é o que abre caminho para essas aplicações.

Os circuitos otimizados são as instruções de como o computador quântico executa um algoritmo. Um dia podem ajudar em simulações para energia de fusão e desenho de remédios.

Fonte: <https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/>

## Como o método funciona

Circuitos que consomem muitos recursos não rodam em computador comum nem nos pequenos processadores quânticos de hoje. Por isso o DeepMind provou matematicamente que cada um funciona, usando o Lean, um provador formal de teoremas.

- Para cada problema, equipes de agentes independentes procuraram melhorias no algoritmo.
- Cada ideia foi verificada em Lean antes de entrar num caderno compartilhado.
- A cada quatro horas, agentes de cada equipe se reuniam numa conferência virtual para trocar, debater e comparar ideias.
- Com o tempo, as equipes produziram ideias mais eficientes e o custo computacional foi caindo até o fim do experimento.
- Pesquisadores definiram os problemas e acompanharam o progresso.

Fonte: <https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/>

## Fusão por confinamento inercial

Os agentes encontraram um circuito quântico que ajuda a calcular uma propriedade importante da fusão por confinamento inercial, método que usa lasers para comprimir combustível de hidrogênio até a ignição.

O custo computacional, métrica que combina qubits e operações, caiu 11,8 vezes. A memória exigida passou de 5.650 para 4.338 qubits com correção de erros, mais de mil qubits a menos para a mesma simulação.

- Custo computacional: redução de 11,8×
- Memória: de 5.650 para 4.338 qubits com correção de erros

Fonte: <https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/>

## Química e remédios

Os agentes também baratearam a simulação de moléculas no metabolismo de remédios e de certas reações fotoquímicas, que são complexas e difíceis para computadores clássicos.

- Molécula comum sensível à luz: simulação quântica 8 vezes mais barata, com um jeito mais simples de acompanhar a posição das partículas e as forças elétricas.
- Citocromo P450, enzima que quebra a maioria dos medicamentos humanos e é importante para o desenho de remédios: ganho de 2,5 vezes e memória de 481 para 333 qubits, ao substituir consultas pesadas de memória.

Fonte: <https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/>

## Grover e arcsin

Duas peças básicas da computação quântica também ficaram mais rápidas. O algoritmo de Grover busca numa lista desordenada. O arcsin é uma rotina que muitos algoritmos usam para carregar números em estados quânticos.

- Uma implementação específica do algoritmo de Grover: ganho de 2,57 vezes de velocidade.
- Rotina arcsin: ganho de 290 vezes de velocidade.

Fonte: <https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/>

## O que ainda falta

Rodar esses algoritmos em simulações científicas ainda exigiria mais recursos do que os primeiros computadores quânticos com correção de erros devem oferecer. Os cortes encurtam o caminho, e a abordagem não se limita a energia limpa e remédios.

Fonte: <https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/>

## Código aberto e artigo

A biblioteca em Lean para algoritmos quânticos, as especificações dos problemas e as soluções verificadas estão abertas no GitHub. Outros pesquisadores podem reproduzir as provas e usar a mesma base. O trabalho é do Google DeepMind com o Google Quantum AI.

- Repositório da biblioteca Lean: github.com/google-deepmind/formal-quantum-computation
- Anúncio do Google DeepMind: https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/
- Artigo, Discovering formally verified quantum programs with AI: https://arxiv.org/abs/2611.09822

Fonte: <https://github.com/google-deepmind/formal-quantum-computation>

## Além do vídeo

- A abordagem pode acelerar outras áreas da pesquisa em computação quântica e a descoberta científica em geral.
- A busca assistida por prova compressa um trabalho que antes levava anos de desenho manual e deixa os pesquisadores livres para escolher problemas e interpretar resultados.
- A colaboração entre Google DeepMind e Google Quantum AI reúne mais de vinte autores, entre eles Sergey Shirobokov, Ben Jaderberg e Ryan Babbush.
