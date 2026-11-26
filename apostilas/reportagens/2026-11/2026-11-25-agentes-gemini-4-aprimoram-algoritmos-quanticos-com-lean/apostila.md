# Agentes Gemini 4 aprimoram algoritmos quânticos com Lean

_2026-11-25 · reportagem_

Em 23 de novembro de 2026, o Google DeepMind mostrou como times de agentes Gemini 4 podem melhorar algoritmos quânticos conhecidos e provar cada resultado em Lean. O custo de um circuito de fusão por confinamento inercial caiu 11,8 vezes, e outras tarefas tiveram ganhos de 2,5 a 290 vezes. A biblioteca em Lean, as especificações dos problemas e as soluções provadas foram abertas no GitHub.

## O contexto

Computadores quânticos prometem resolver problemas além do alcance dos supercomputadores clássicos. Mas existe um obstáculo: mesmo com os melhores algoritmos quânticos, algumas aplicações importantes ainda exigem mais recursos do que o hardware quântico inicial vai suportar.

Em 23 de novembro de 2026, o Google DeepMind publicou um trabalho que ataca esse obstáculo. A equipe usou times de agentes Gemini 4 para melhorar algoritmos quânticos conhecidos, criando circuitos quânticos muito mais eficientes. Cada resultado foi provado matematicamente com Lean, um verificador de provas formal.

Os circuitos otimizados podem um dia ajudar a rodar simulações que resolvem desafios científicos complexos, de energia de fusão a design de fármacos. Para que a comunidade construa sobre o trabalho, a biblioteca em Lean, as especificações de problemas e as soluções provadas foram abertas no GitHub.

O trabalho é uma colaboração entre Google DeepMind e Google Quantum AI, assinado por Sergey Shirobokov, Ben Jaderberg e Ryan Babbush, entre outros. O artigo se chama Discovering formally verified quantum programs with AI e está no arXiv sob o número 2611.09822.

Fonte: <https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/>

## Como as equipes de agentes trabalham

Para cada problema, a equipe encarregou times separados e independentes de agentes de buscar melhorias nos algoritmos. As ideias eram verificadas com Lean antes de entrarem em um caderno compartilhado.

A cada quatro horas, agentes de cada time se reuniam em uma conferência virtual para trocar, debater e comparar ideias. À medida que os times produziam ideias mais eficazes, o custo computacional caía gradualmente até o fim do experimento.

O foco foi aplicações que podem um dia impactar grandes desafios da humanidade, como energia limpa e design de fármacos, mas o método não se limita a essas áreas.

A equipe também pôde definir a direção da pesquisa especificando os problemas para os times de agentes e supervisionar o progresso. O conhecimento em algoritmos quânticos, combinado com a forma de organizar os times, levou a resultados científicos reais.

Fonte: <https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/>

## Por que provar em Lean

Não é possível testar circuitos quânticos de alto custo em computadores clássicos nem nos processadores quânticos atuais, que são pequenos. Por isso, cada resultado precisa ser provado matematicamente.

Os times de agentes provaram cada resultado usando Lean, um provador de teoremas formal. A biblioteca em Lean para algoritmos quânticos foi construída para ser usada por times de agentes colaborando, de modo que as ideias viessem acompanhadas de garantias de correção matemática.

A biblioteca é fundamentada em lógica de Hoare quântica com variáveis clássicas. Ela cobre fundamentos da computação quântica, como circuitos, portas, registradores e a matemática subjacente, além da formalização da lógica de Hoare quântica com variáveis clássicas, da contagem de recursos e da verificação de algoritmos quânticos importantes.

A busca com IA verificada por prova comprime trabalho que antes levava anos de projeto manual, permitindo que pesquisadores se concentrem em escolher problemas e interpretar resultados.

Fonte: <https://github.com/google-deepmind/formal-quantum-computation>

## Fusão por confinamento inercial: 11,8 vezes mais barato

O caso central foi a fusão por confinamento inercial: um método de fusão que usa lasers para comprimir combustível de hidrogênio até a ignição. O circuito quântico ajuda a calcular uma propriedade importante desse processo.

Os times de agentes cortaram o custo computacional exigido, métrica que combina qubits e operações necessárias, em 11,8 vezes.

A memória quântica, medida em qubits, caiu de 5.650 para 4.338 qubits com correção de erros. É menos memória para o mesmo cálculo.

Exemplo: imagine que um cálculo de fusão exigia 5.650 qubits de memória. Depois da otimização, o mesmo cálculo passa a exigir 4.338. O ganho de 11,8 vezes no custo total vem da combinação de menos qubits e menos operações.

Fonte: <https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/>

## Química e enzimas: moléculas e remédios

Os agentes também reduziram custos para simular moléculas no metabolismo de fármacos e certas reações fotoquímicas, que são reações complexas difíceis de simular em computadores clássicos.

Para uma molécula comum sensível à luz, os times tornaram a simulação quântica 8 vezes mais barata, simplificando a forma como o algoritmo acompanha posições de partículas e forças elétricas.

Para o Citocromo P450, uma enzima que quebra a maioria dos remédios humanos e é importante para o design de fármacos, houve melhoria de 2,5 vezes e a memória caiu de 481 para 333 qubits, ao substituir consultas de memória volumosas.

Fonte: <https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/>

## Algoritmos fundamentais: busca e aritmética

Foram melhorados um algoritmo quântico fundamental e um bloco aritmético muito usado.

Encontrou-se aceleração de 2,57 vezes para uma implementação específica do algoritmo de Grover, operação quântica fundamental que busca em uma lista não ordenada.

E aceleração de 290 vezes para o arcseno, rotina comum usada por muitos outros algoritmos quânticos para carregar números em estados quânticos.

Fonte: <https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/>

## Como funciona na prática

Exemplo: um pesquisador quer otimizar um algoritmo de simulação de fusão. Ele define o problema para um time de agentes Gemini 4. Cada time de agentes busca melhorias de forma independente. Cada proposta é verificada em Lean antes de entrar no caderno compartilhado. A cada quatro horas, agentes de cada time se reúnem, trocam e debatem ideias, e o custo do circuito cai. No fim, o circuito resultante está provado matematicamente, com custo computacional menor.

Outro caso: a biblioteca em Lean, as especificações dos problemas e as soluções provadas foram publicadas em um repositório público no GitHub, no endereço github.com/google-deepmind/formal-quantum-computation. Assim, outra equipe pode usar o mesmo método e conferir os resultados.

Fonte: <https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/>

## Linha do tempo

- Julho de 2024: IA alcança padrão de medalha de prata resolvendo problemas da Olimpíada Internacional de Matemática.
- Novembro de 2024: AlphaQubit enfrenta um dos maiores desafios da computação quântica.
- Maio de 2025: AlphaEvolve, agente de código com Gemini para projetar algoritmos avançados.
- 23 de novembro de 2026: o Google DeepMind publica o post sobre o trabalho e anuncia a abertura da biblioteca em Lean no GitHub.

Fonte: <https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/>

## Quem ganha e quem perde

Pesquisadores ganham: a busca com IA verificada por prova comprime trabalho que antes levava anos de projeto manual, e eles podem se concentrar em escolher problemas e interpretar resultados.

A comunidade ganha: biblioteca, especificações de problemas e soluções provadas estão abertas no GitHub, com licença Apache 2.0 para software e CC-BY 4.0 para demais materiais.

As áreas de aplicação ganham: energia limpa, com a fusão, e design de fármacos, com a química e as enzimas, são os focos iniciais.

O limite: rodar esses algoritmos em simulações científicas ainda exige mais recursos do que os primeiros computadores quânticos com correção de erros devem oferecer. Ainda assim, os ganhos são reais e o método pode acelerar outras frentes da pesquisa quântica e da descoberta científica em geral.

Fonte: <https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/>

## O que ainda não se sabe

- Rodar esses algoritmos em simulações científicas ainda pede mais recursos do que os primeiros computadores quânticos com correção de erros provavelmente oferecerão. Os ganhos são reais, mas a execução prática ainda está fora do alcance imediato.
- A biblioteca não é produto oficial do Google. Está sob desenvolvimento ativo, e o próximo marco previsto é modelar explicitamente o custo de computação clássica e de fluxo de controle.
- Os programas descobertos estão no ramo discoveries do repositório, separado do núcleo da biblioteca.
- A biblioteca depende de Mathlib4 e de QuantumInfo, parte do Physlib, obtidos automaticamente durante o build. A versão usada acompanha lançamentos marcados dessas bibliotecas, não os ramos de desenvolvimento.
- Verifique sempre a fonte: os números de ganho vêm do artigo publicado pelo Google DeepMind. Reproduza e confira antes de citar em trabalho próprio.

Fonte: <https://github.com/google-deepmind/formal-quantum-computation>

## O que você pode fazer

1. Leia o artigo Discovering formally verified quantum programs with AI no arXiv, número 2611.09822, para entender o método completo.
2. Acesse a biblioteca em Lean no GitHub em github.com/google-deepmind/formal-quantum-computation para ver as especificações e as soluções provadas.
3. Se for usar a biblioteca: instale elan, lake e lean, depois rode os comandos de cache e build na pasta do projeto. O build baixa Mathlib4 e QuantumInfo automaticamente.
4. Explore o ramo discoveries para ver os programas descobertos e descritos no artigo.
5. Cite o trabalho usando a referência BibTeX fornecida no repositório, se for usar em publicação.

```
lake exe cache get
lake build
```

Fonte: <https://github.com/google-deepmind/formal-quantum-computation>

## Glossário

- Agente (Gemini 4): sistema de IA que propõe melhorias de algoritmo de forma autônoma.
- Algoritmo quântico: sequência de operações que um computador quântico executa para resolver um problema.
- Circuito quântico: conjunto de instruções de como o computador quântico deve executar um algoritmo.
- Qubit: unidade básica de informação quântica; a memória quântica é medida em qubits.
- Qubit com correção de erros: qubit protegido contra erros, usado para contar recursos de forma realista.
- Lean: provador de teoremas formal usado para provar matematicamente que os circuitos funcionam.
- Verificação formal: provar com matemática, em vez de testar, que um resultado está correto.
- Lógica de Hoare quântica: formalismo para especificar e verificar programas quânticos.
- Fusão por confinamento inercial: método de fusão que usa lasers para comprimir combustível de hidrogênio até a ignição.
- Citocromo P450: enzima que quebra a maioria dos remédios humanos, importante para design de fármacos.
- Algoritmo de Grover: operação quântica fundamental que busca em uma lista não ordenada.
- Arcseno: rotina comum usada por muitos algoritmos quânticos para carregar números em estados quânticos.
- Mathlib4: biblioteca padrão de matemática para Lean 4.
- Physlib/QuantumInfo: biblioteca de informação quântica usada como base.

Fonte: <https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/>

## Para onde ir depois

- Leia o artigo completo no arXiv: https://arxiv.org/abs/2611.09822
- Acesse a biblioteca em Lean: https://github.com/google-deepmind/formal-quantum-computation
- Leia o post do Google DeepMind: https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/
- Explore trabalhos relacionados: AlphaEvolve (maio de 2025), AlphaQubit (novembro de 2024) e o resultado na Olimpíada Internacional de Matemática (julho de 2024).

Fonte: <https://deepmind.google/blog/finding-faster-quantum-algorithms-with-agents-and-formal-verification/>

## Além do vídeo

- Autores do artigo: Sergey Shirobokov, Ben Jaderberg, Katerina Hristova, George Tsoukalas, Johannes Bausch, Eric Wieser, Francisco J. H. Heras, Nicholas C. Rubin, Guang Hao Low, Sébastien Racanière, Nenad Tomašev, Lei M. Zhang, James D. Watson, Tanuj Khattar, Aws Albarghouthi, Stavan Jain, Harun Khan, Leopoldo Sarra, Andrew W. Senior, Michael Broughton, Hussain Masoom, Sergio Boixo, Ryan Babbush, Swarat Chaudhuri e Pushmeet Kohli.
- Agradecimentos do post: Kevin Ishimwe, Ibrahim Alkhashem, Matthew Harrigan, Emilien Dupont, Sebastian Nowozin, Brendan Tracey, Uchechi Okereke, Ali Douraghy, Andy Song, Alex Wilkins, Evie Gray, Danielle Breen, Dimple Vijaykumar, Muinat Abdul, Jason Freidenfelds, Chris Kwaku-Abdullahi e Rob Ashley.
- O repositório traz uma entrada BibTeX para citar o artigo em publicações.
- A biblioteca é organizada em duas bibliotecas Lean: QuantumComputation, o núcleo, e QuantumComputationSpecs, com especificações e desafios de referência para prova automatizada e descoberta assistida por IA.
