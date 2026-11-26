---
name: design-glass-motion-effects
description: "Especifica superfícies translúcidas e animações de interface com controle de contraste, desempenho e alternativa sem efeitos. Use quando quiser aplicar visual de vidro fosco ou camadas animadas sem prejudicar a leitura."
---

# Movimento e efeito de vidro

Especifica superfícies translúcidas e animações de interface com controle de contraste, desempenho e alternativa sem efeitos. Use quando quiser aplicar visual de vidro fosco ou camadas animadas sem prejudicar a leitura.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Telas e elementos que receberão o efeito.
- Fundos reais que aparecerão atrás das superfícies.
- Tecnologia, navegadores e aparelhos mais fracos que precisam ser atendidos.
- Intenção do efeito, como separar camadas ou indicar mudança de estado.

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Selecione poucas superfícies em que a translucidez esclareça a profundidade, deixando áreas de leitura longa opacas.
2. Defina por camada o desfoque, a opacidade, o tom, a borda, a sombra e a ordem de empilhamento.
3. Descreva gatilhos, durações e curvas dos movimentos, priorizando transformação e opacidade.
4. Verifique o texto sobre o fundo mais claro, o mais escuro e o mais ruidoso, reforçando a película quando faltar contraste.
5. Limite áreas desfocadas e sobrepostas e crie variantes sólidas para falta de suporte, redução de transparência ou de movimento e aparelhos lentos.

## O que entregar

Especificação dos efeitos com valores por camada, animações e variantes de contingência.

## Conferência antes de entregar

- [ ] A interface continua completa e legível com todos os efeitos desligados.
- [ ] O contraste foi avaliado sobre os piores fundos previstos.
- [ ] O desempenho é marcado como não medido enquanto não houver teste em aparelho.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
