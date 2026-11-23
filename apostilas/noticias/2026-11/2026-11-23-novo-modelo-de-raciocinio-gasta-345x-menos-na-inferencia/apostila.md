# Novo modelo de raciocínio gasta 345x menos na inferência

_2026-11-23 · noticia_

O Energy-Based Reasoner (EBR) é proposto como alternativa ao raciocínio em loop. No Sudoku-Extreme, os autores relatam 345x menos computação na inferência que o EqR, o segundo melhor modelo, e 99,9% de acurácia com 1,8 milhão de parâmetros. Esta apostila reúne os números, a ideia central e os links oficiais do projeto.

## O que é o EBR

O Energy-Based Reasoner, ou EBR, é um modelo de raciocínio proposto como alternativa ao raciocínio em loop, também chamado de raciocínio recorrente.

O artigo foi enviado ao arXiv em 6 de novembro de 2026, com o título "Energy-Based Reasoners: Your Recurrent Reasoner Should Be an Energy-Based Model".

Fonte: <https://arxiv.org/abs/2611.08977>

## A tese do artigo

Os autores defendem que um raciocinador recorrente deve ser um modelo baseado em energia.

O modelo aprende uma função de energia que avalia cada estado de raciocínio. O gradiente dessa energia indica como melhorar a resposta e quando parar.

Fonte: <https://arxiv.org/abs/2611.08977>

## Os números no Sudoku-Extreme

Todos os números abaixo são do teste Sudoku-Extreme e foram divulgados pelos autores. A comparação é com o EqR, o segundo melhor modelo.

- Computação na inferência: 345x menor que a do EqR.
- Acurácia: 99,9% com apenas 1,8 milhão de parâmetros, com computação de treino comparável.
- Para igualar a melhor acurácia do EqR, o EBR usa 7x menos iterações e 43x menos amostras.

Fonte: <https://energy-based-reasoners.github.io/>

## Como ler esses resultados

Os ganhos de 345x, 7x e 43x são resultados divulgados pelos autores no artigo, medidos contra o EqR no Sudoku-Extreme.

Testes de outros grupos vão mostrar se o ganho se mantém fora do estudo original. Se os números se confirmarem, raciocinar com muito menos computação pode baratear a execução desses modelos.

Fonte: <https://energy-based-reasoners.github.io/>

## Links oficiais

- Artigo no arXiv: https://arxiv.org/abs/2611.08977
- Repositório oficial no GitHub: https://github.com/wwillchen/ebr
- Página do projeto: https://energy-based-reasoners.github.io/

Fonte: <https://energy-based-reasoners.github.io/>
