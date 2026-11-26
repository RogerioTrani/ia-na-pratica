# Fable 5.2 gera mundo 3D por shader ray marching

_2026-11-26 · tutorial_

O Fable 5.2 monta, a partir de um pedido no Claude, uma demonstração interativa em um único arquivo HTML com cinco cenas. Você vai gerar a página e testar cada cena: enxame de agentes, mundo 3D por ray marching, física ao vivo, um milhão de tokens e a comparação entre versões. Basta um navegador, uma conta no Claude e espaço para salvar o arquivo.

## Uma página, cinco cenas

No fim você tem uma demonstração interativa em um único arquivo HTML: enxame de agentes, mundo 3D por ray marching, física ao vivo, um milhão de tokens e a comparação entre versões.

Serve para quem quer testar o modelo na prática, sem programar. Página oficial: anthropic.com/claude/fable.

Fonte: <https://www.anthropic.com/claude/fable>

## O que você precisa

Se você já usa o Claude, a conta está pronta. Se nunca entrou, crie a sua antes de seguir.

- Computador com navegador
- Conta no Claude
- Navegador já instalado
- Espaço para salvar o arquivo

## Gerar a página no Claude

- Na home, escolha chat, ao lado de cowork; a conversa abre com o campo de texto.
- No seletor de modelos, escolha Fable 5.2 e deixe o esforço em extra. Níveis de esforço em platform.claude.com/docs/en/build-with-claude/effort.
- No campo de conversa, envie o pedido exato do comando; o modelo entrega um arquivo com cinco cenas.
- Abra o arquivo único no navegador: aparece um menu com cinco cenas.

```
crie uma demo interativa em um único arquivo HTML para demonstrar o poder do novo Fable 5.2. busque a documentação de lançamento e gere demos que demonstram o poder de forma interativa dessa novidade.
```

Fonte: <https://www.anthropic.com/claude/fable>

## Cena 1: enxame de agentes

Na primeira cena, clique na aba tab, digite seu nome e mude a velocidade na legenda.

Os agentes acompanham o cursor em tempo real, com o texto digitado.

```
tab
```

## Cena 2: mundo 3D por ray marching

Na segunda cena, H esconde o menu, espaço muda a cor, e muda a textura; o cenário se refaz a cada quadro.

Cada quadro é calculado de novo pelo modelo, ponto por ponto. Olhe para os lados e use as teclas da tela.

## Cena 3: física ao vivo

Na terceira cena, veja as ondas passarem pelos dois furos e formarem o padrão da dupla fenda; use a pausa.

A página mostra uma equação de onda sendo resolvida ao vivo, no lugar de um vídeo pronto.

Fonte: <https://www.anthropic.com/claude/fable>

## Cena 4: um milhão de tokens

Na quarta cena, use a lupa e clique no pixel diferente; o scanner aponta o ponto certo. A janela de contexto é de 1 milhão de tokens: platform.claude.com/docs/en/models/overview.

Token é a menor parte de texto que o modelo lê. Cada pixel desse painel é um token.

Fonte: <https://platform.claude.com/docs/en/models/overview>

## Cena 5: comparação das versões

Na quinta cena, veja se o 5.2 aparece à frente do 5.1 em todos os critérios. Comparação oficial em anthropic.com/claude-fable-and-mythos-5-2.

Olhe cada um, um por um. Se a cena mostrar o mesmo resultado, a demonstração saiu como esperado.

Fonte: <https://www.anthropic.com/claude-fable-and-mythos-5-2>

## Além do vídeo

- Tabela de benchmarks do lançamento: Fable 5.2, Fable 5.1 e modelos de outras empresas (GPT6 Astra e Gemini 4 Carbon). O material cita resultados 30% mais rápidos que a versão 5.1, melhora de 10% em codificação agentiva e avanços em pesquisa científica e robótica.
- Preço: o material diz que o Fable 5.2 é 20% mais barato que o anterior, com custo de 8 por milhão de token, e que ainda custa o dobro do OP 5.
- Mythos 5.2: o material o descreve como um modelo perigoso, liberado só para empresas em teste, e apresenta o Fable como a versão controlada e segura para o público.
- Um sistema operacional feito pelo Claude, mostrado em vídeo como uma das demonstrações das novidades.
- A promoção da Voz Academy na Black Friday, com acesso vitalício à comunidade e aos cursos, e o pedido para curtir, se inscrever e comentar a palavra 'incrível'.
