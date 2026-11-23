# Claude analisa a Apple em 5 etapas com plugin grátis

_2026-11-23 · noticia_

A Anthropic liberou de graça um pacote de plugins financeiros para o Claude. Nele, a habilidade Initiating Coverage monta o relatório que o analista escreve ao começar a acompanhar uma empresa. Você escolhe a ação, como a Apple, e o Claude conduz o trabalho em cinco etapas, com um arquivo por etapa. Esta apostila traz os comandos de instalação e o que cada etapa entrega.

## O que é a habilidade Initiating Coverage

Initiating Coverage é o nome do relatório que o analista escreve quando começa a acompanhar uma empresa. A habilidade com esse nome faz parte do plugin equity-research, dentro do pacote Financial Services, da Anthropic.

Você escolhe a ação, por exemplo a Apple, e pede uma etapa de cada vez. Cada etapa entrega o seu arquivo.

Fonte: <https://github.com/anthropics/financial-services/tree/main/plugins/vertical-plugins/equity-research>

## Como instalar no Claude Code

Rode os três comandos abaixo, nesta ordem. O primeiro adiciona o repositório como marketplace. Os outros dois instalam os plugins financial-analysis e equity-research.

Fonte: <https://raw.githubusercontent.com/anthropics/financial-services/main/README.md>

## Como usar

Com os plugins instalados, diga ao Claude qual ação você quer estudar. O Claude conduz o trabalho em cinco etapas, e você pede uma por vez.

- Escolha a ação, como a Apple.
- Peça a etapa 1 e confira o arquivo que ela entrega.
- Siga pedindo as etapas seguintes, uma de cada vez, até a etapa 5.
- Cada etapa se apoia no que a anterior levantou, então siga a ordem.

Fonte: <https://raw.githubusercontent.com/anthropics/financial-services/main/plugins/vertical-plugins/equity-research/skills/initiating-coverage/SKILL.md>

## As cinco etapas

- Etapa 1, pesquisa do negócio inteiro: o Claude estuda a empresa por completo antes de qualquer número.
- Etapa 2, modelo financeiro no Excel: planilha de seis abas montada a partir dos balanços oficiais da empresa. Os números do relatório saem dela, e você pode abrir o arquivo e conferir.
- Etapa 3, avaliação por fluxo de caixa descontado: o método projeta o dinheiro futuro da empresa para calcular quanto ela vale, e o resultado é comparado com o das concorrentes.
- Etapa 4, de 25 a 35 gráficos: gerados para a ação analisada, depois entram no texto do relatório.
- Etapa 5, relatório final de 30 a 50 páginas: pesquisa, planilha, avaliação e gráficos reunidos em um único documento, no formato que um analista usa para começar a cobrir uma empresa.

Fonte: <https://raw.githubusercontent.com/anthropics/financial-services/main/plugins/vertical-plugins/equity-research/skills/initiating-coverage/SKILL.md>

## O repositório

O pacote se chama Financial Services, é da Anthropic e fica no GitHub. O código é aberto, então você pode ler como a habilidade funciona. O repositório já passou de 41.000 estrelas.

```
github.com/anthropics/financial-services
```

Fonte: <https://github.com/anthropics/financial-services>

## Antes de usar o resultado

É uma ferramenta de estudo, não uma recomendação de investimento. Confira sempre os números, a começar pela planilha da etapa 2, que está aberta para você revisar.

## Além do vídeo

- Página do plugin equity-research no GitHub, onde fica a habilidade initiating-coverage: https://github.com/anthropics/financial-services/tree/main/plugins/vertical-plugins/equity-research
