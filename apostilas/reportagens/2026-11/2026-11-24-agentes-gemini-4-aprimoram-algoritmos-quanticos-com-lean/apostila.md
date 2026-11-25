# Agentes Gemini 4 aprimoram algoritmos quânticos com Lean

_2026-11-24 · reportagem_

O Google DeepMind colocou equipes de agentes Gemini 4 para melhorar algoritmos quânticos conhecidos, e cada melhoria só valeu depois de provada em Lean, um verificador formal. O custo da simulação de fusão por confinamento inercial caiu 11,8 vezes. A biblioteca Lean e as soluções verificadas estão abertas no GitHub.

## O contexto

Mesmo com os melhores algoritmos, algumas aplicações importantes pedem mais qubits e operações do que as primeiras máquinas quânticas vão ter. Reduzir esse custo no papel abre caminho para essas aplicações.

Circuitos que consomem muitos recursos não rodam em computador comum nem nos pequenos processadores quânticos de hoje. Por isso o DeepMind provou matematicamente que cada um funciona, usando o Lean.

Fonte: <https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/>

## Linha do tempo

- Durante o experimento, as equipes de agentes se reuniam a cada quatro horas numa conferência virtual.
- Com o tempo, o custo computacional foi caindo até o fim do experimento.

## Quem ganha e quem perde

Fusão por confinamento inercial: custo computacional caiu 11,8 vezes, e a memória passou de 5.650 para 4.338 qubits com correção de erros.

Citocromo P450, enzima que quebra a maioria dos medicamentos humanos: ganho de 2,5 vezes e memória de 481 para 333 qubits.

Grover, em uma implementação específica: ganho de 2,57 vezes de velocidade. Rotina arcsin: ganho de 290 vezes de velocidade.

## O que ainda não se sabe

Rodar esses algoritmos em simulações científicas ainda exigiria mais recursos do que os primeiros computadores quânticos com correção de erros devem oferecer.

Os cortes encurtam o caminho, mas são resultados no papel, verificados em Lean, e não execuções em máquinas quânticas reais.

Fonte: <https://github.com/google-deepmind/formal-quantum-computation>

## O que você pode fazer

Para reproduzir as provas, use o repositório aberto da biblioteca Lean.

1. Acesse o repositório da biblioteca Lean no GitHub. Resultado: você tem as especificações e as soluções verificadas.
2. Leia o artigo Discovering formally verified quantum programs with AI. Resultado: você entende o método de busca assistida por prova.

Fonte: <https://arxiv.org/abs/2611.09822>
