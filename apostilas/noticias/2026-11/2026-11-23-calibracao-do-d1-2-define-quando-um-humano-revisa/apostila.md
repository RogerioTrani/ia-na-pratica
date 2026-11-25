# Calibração do d1.2 define quando um humano revisa

_2026-11-23 · noticia_

A Liquid AI lançou o d1.2 e o d1.2-ultra, modelos de decisão que devolvem probabilidades calibradas. Com elas, você define um limite de confiança e manda para revisão humana só os casos em que o modelo hesita. Os dois estão na API da Liquid.

## O fato

A Liquid AI lançou o d1.2 e o d1.2-ultra, modelos de decisão que devolvem probabilidades calibradas.

Os dois modelos estão na API da Liquid e cobram apenas tokens de entrada. Custam o mesmo que o d1.1 e o d1-ultra.

Fonte: <https://www.liquid.ai/blog/d1-2>

## Os números

- US$ 0,02 por milhão de tokens de entrada no d1.2.
- US$ 0,042 por milhão de tokens de entrada no d1.2-ultra.
- 75 pontos do d1.2-ultra no Decision Index v2.1, da Artificial Analysis, em primeiro lugar.
- Cinco tarefas novas na API.

## O que muda para você

Quando o modelo diz 80%, ele deve acertar cerca de 80% das vezes. É isso que permite definir um limite.

Acima do limite, o fluxo segue sozinho. Abaixo do limite, a tarefa vai para uma pessoa conferir.

Um exemplo: ao perguntar a uma fatura quanto há a pagar, o modelo devolve o valor correto junto com os caracteres de onde o leu.

## O que fazer hoje

1. Acesse console.liquid.ai e crie uma chave em Dashboard > API Keys. Resultado: você tem uma chave de API.
2. Chame d1.2 ou d1.2-ultra pela API da Liquid. Resultado: o modelo responde com a probabilidade calibrada.

Fonte: <https://console.liquid.ai/>

## O que conferir

OpenRouter e Vercel chegam em breve. A empresa diz que vai abrir os pesos em algum momento, sem data.

O d1.2-ultra lidera o ranking, mas custa mais que o d1.2. O d1.2 oferece a melhor relação entre qualidade e custo, segundo a Liquid.
