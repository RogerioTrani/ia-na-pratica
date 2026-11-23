# Calibração do d1.2 define quando um humano revisa

_2026-11-23 · noticia_

A Liquid AI lançou o d1.2 e o d1.2-ultra, modelos de decisão que devolvem probabilidades calibradas. Com elas, você define um limite de confiança e manda para revisão humana só os casos em que o modelo hesita. Os dois modelos estão na API da Liquid hoje, cobram apenas tokens de entrada e custam o mesmo que o d1.1 e o d1-ultra.

## O que é calibração

A probabilidade que um modelo de decisão entrega só serve se estiver correta. Quando o modelo diz 80%, ele deve acertar cerca de 80% das vezes. É isso que permite definir um limite.

Fonte: <https://www.liquid.ai/blog/d1-2>

## Como usar na prática

Com probabilidades confiáveis, você escolhe um corte de confiança. A revisão humana fica só onde o modelo tem dúvida.

- Defina o limite de confiança do seu fluxo.
- Acima do limite, o fluxo segue sozinho.
- Abaixo do limite, a tarefa vai para uma pessoa conferir.

Fonte: <https://www.liquid.ai/blog/d1-2>

## Cinco tarefas novas na API

O d1.2 e o d1.2-ultra acrescentam cinco tarefas à API. Um exemplo: ao perguntar a uma fatura quanto há a pagar, o modelo devolve o valor correto junto com os caracteres de onde o leu, o que facilita a conferência.

- Ler um valor da entrada (texto, número ou data).
- Achar todos os trechos de um tipo em um texto (spans).
- Localizar coisas em uma imagem (uma caixa para um objeto, caixas para todas as ocorrências).
- Estimar um número, com uma faixa.
- Escolher todas as opções que se aplicam (choice).

Fonte: <https://www.liquid.ai/blog/d1-2>

## Qual modelo escolher

O d1.2-ultra ocupa o primeiro lugar entre os modelos de decisão no Decision Index v2.1 da Artificial Analysis, com 75 pontos. O d1.2 custa menos da metade e oferece a melhor relação entre qualidade e custo.

Fonte: <https://www.liquid.ai/blog/d1-2>

## Preço

Os valores são em dólares por milhão de tokens de entrada. Não há cobrança de tokens de saída, então o custo depende só do que você envia. Os preços são os mesmos do d1.1 e do d1-ultra.

- d1.2: US$ 0,02
- d1.2-ultra: US$ 0,042

Fonte: <https://www.liquid.ai/blog/d1-2>

## Como testar hoje

Crie uma chave de API no console da Liquid (Dashboard > API Keys) e chame o modelo pelo nome: d1.2 ou d1.2-ultra. OpenRouter e Vercel chegam em breve. A empresa diz que vai abrir os pesos em algum momento.

- Acesse console.liquid.ai e crie uma chave em Dashboard > API Keys.
- Chame d1.2 ou d1.2-ultra pela API da Liquid.

Fonte: <https://console.liquid.ai/>

## Além do vídeo

- Os dois modelos processam texto, imagens e áudio, e são descritos pela Liquid como modelos de decisão omnimodais.
- O índice usado no ranking é o Artificial Analysis Decision Index v2.1.
