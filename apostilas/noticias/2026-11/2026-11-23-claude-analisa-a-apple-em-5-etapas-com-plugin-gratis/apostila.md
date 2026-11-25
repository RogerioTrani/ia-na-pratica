# Claude analisa a Apple em 5 etapas com plugin grátis

_2026-11-23 · noticia_

A Anthropic liberou de graça um pacote de plugins financeiros para o Claude. Nele, a habilidade Initiating Coverage monta o relatório que o analista escreve ao começar a acompanhar uma empresa. Você escolhe a ação, como a Apple, e o Claude conduz o trabalho em cinco etapas, com um arquivo por etapa. É uma ferramenta de estudo, não uma recomendação de investimento.

## O fato

Initiating Coverage é o nome do relatório que o analista escreve quando começa a acompanhar uma empresa. A habilidade com esse nome faz parte do plugin equity-research, dentro do pacote Financial Services, da Anthropic.

Você escolhe a ação, por exemplo a Apple, e pede uma etapa de cada vez. Cada etapa entrega o seu arquivo. Fonte: https://github.com/anthropics/financial-services/tree/main/plugins/vertical-plugins/equity-research

Fonte: <https://github.com/anthropics/financial-services/tree/main/plugins/vertical-plugins/equity-research>

## Como instalar no Claude Code

Os comandos de instalação estão no README oficial do repositório: https://raw.githubusercontent.com/anthropics/financial-services/main/README.md

1. siga o README e rode o primeiro comando, que adiciona o repositório como marketplace. Resultado: o repositório fica disponível como marketplace.
2. rode o segundo e o terceiro comandos, nesta ordem, para instalar os plugins financial-analysis e equity-research. Resultado: os dois plugins ficam instalados.

Fonte: <https://raw.githubusercontent.com/anthropics/financial-services/main/README.md>

## Como usar

Com os plugins instalados, diga ao Claude qual ação você quer estudar. O Claude conduz o trabalho em cinco etapas, e você pede uma por vez. Habilidade initiating-coverage: https://raw.githubusercontent.com/anthropics/financial-services/main/plugins/vertical-plugins/equity-research/skills/initiating-coverage/SKILL.md

1. escolha a ação, como a Apple. Resultado: o estudo fica focado nessa empresa.
2. peça a etapa 1 e confira o arquivo que ela entrega. Resultado: você tem o primeiro arquivo do estudo.
3. siga pedindo as etapas seguintes, uma de cada vez, até a etapa 5. Resultado: o relatório fica completo.
4. cada etapa se apoia no que a anterior levantou, então siga a ordem. Resultado: o relatório reúne o trabalho de todas as etapas.

Fonte: <https://raw.githubusercontent.com/anthropics/financial-services/main/plugins/vertical-plugins/equity-research/skills/initiating-coverage/SKILL.md>

## As cinco etapas

Cada etapa gera o seu arquivo, na ordem abaixo.

- Etapa 1, pesquisa do negócio inteiro: o Claude estuda a empresa por completo antes de qualquer número.
- Etapa 2, modelo financeiro no Excel: planilha de seis abas montada a partir dos balanços oficiais da empresa. Os números do relatório saem dela, e você pode abrir o arquivo e conferir.
- Etapa 3, avaliação por fluxo de caixa descontado: o método projeta o dinheiro futuro da empresa para calcular quanto ela vale, e o resultado é comparado com o das concorrentes.
- Etapa 4, de 25 a 35 gráficos: gerados para a ação analisada, depois entram no texto do relatório.
- Etapa 5, relatório final de 30 a 50 páginas: pesquisa, planilha, avaliação e gráficos reunidos em um único documento, no formato que um analista usa para começar a cobrir uma empresa.

Fonte: <https://raw.githubusercontent.com/anthropics/financial-services/main/plugins/vertical-plugins/equity-research/skills/initiating-coverage/SKILL.md>

## O repositório

O pacote se chama Financial Services, é da Anthropic e fica no GitHub. O código é aberto, então você pode ler como a habilidade funciona. O repositório já passou de 41.000 estrelas. Endereço do repositório:

```
github.com/anthropics/financial-services
```

Fonte: <https://github.com/anthropics/financial-services>

## Antes de usar o resultado

É uma ferramenta de estudo, não uma recomendação de investimento. Confira sempre os números, a começar pela planilha da etapa 2, que está aberta para você revisar.

Página do plugin equity-research no GitHub, onde fica a habilidade initiating-coverage: https://github.com/anthropics/financial-services/tree/main/plugins/vertical-plugins/equity-research

Fonte: <https://github.com/anthropics/financial-services/tree/main/plugins/vertical-plugins/equity-research>
