# Lemo-Opuscar chega a 99 estilos para filmes em código

_2026-11-23 · tutorial_

O Lemo-Opuscar reúne 99 estilos de filme feitos em código para o Claude Code. A atualização de 12 de novembro de 2026 acrescentou 33 estilos, em 15 categorias. Esta apostila leva do zero ao primeiro filme: instalar o Claude Code e o plugin, abrir a sessão na pasta do projeto, configurar o esforço, escolher o estilo Neon Tubes e pedir o filme.

## O que você terá no fim

Ao final, você terá o plugin Lemo-Opuscar instalado no Claude Code e um primeiro filme em código no estilo Neon Tubes, com o vídeo final na pasta da sessão. O agente escreve o código das imagens, organiza a trilha e monta o vídeo, sem modelo gerador de vídeo. Fonte: https://github.com/lemomo-ai/lemo-opuscar

Requisitos: acesso ao Claude Code, Node 20 ou superior, ffmpeg 7 ou superior, Python 3.11 ou superior ou uv (https://docs.astral.sh/uv/) e tokens disponíveis para a sessão. O caminho desta apostila usa Windows com PowerShell. Cada filme leva cerca de 30 a 60 minutos de trabalho do agente e consome uma boa quantidade de tokens. Se houver defeito, descreva o problema ao agente e peça a correção.

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Passo a passo

Siga os passos na ordem. Os comandos ficam em seções próprias. Nesta apostila o estilo fica fixo em Neon Tubes.

1. instale o Claude Code. No PowerShell do Windows, execute o comando de instalação. Se você já usa o Claude Code neste computador, pule para o passo 2. Resultado esperado: o Claude Code fica disponível.
2. Passos 2 e 3: adicione o marketplace e instale o plugin. O marketplace é o catálogo de onde o Claude Code busca o plugin. Execute os dois comandos no terminal, um depois do outro. Resultado esperado: o plugin Lemo-Opuscar fica instalado.
3. abra o Claude na pasta do filme. O plugin funciona a partir de qualquer pasta. Deixe o terminal aberto na pasta que receberá o filme e execute o comando do Claude. No primeiro uso, o agente baixa guias, ferramentas e estilos para ~/lemo-opuscar. Resultado esperado: a sessão está aberta na pasta do filme.
4. configure o esforço alto. Dentro do Claude Code, digite o comando de esforço. O projeto foi feito para o Claude: Fable, Opus e Sonnet funcionam. Outros modelos podem reproduzir mal os estilos. Resultado esperado: o esforço fica alto.
5. escolha o estilo Neon Tubes. Abra a galeria oficial em lemomo-ai.github.io/lemo-opuscar e encontre Neon Tubes na Estação 12 (Light & Lines). Assista à demonstração de 0:48. Resultado esperado: você conhece a aparência do estilo.
6. peça o primeiro filme. No Claude Code, envie o pedido de exemplo. Ele dá ao agente duas informações: a aparência (o estilo) e o assunto. O agente pode perguntar detalhes do tema e se você quer ver um storyboard antes. Resultado esperado: a produção avança até o filme.

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Instalar o Claude Code

No PowerShell do Windows, execute o comando abaixo (o script fica em https://claude.ai/install.ps1). Outras formas de instalação estão na documentação oficial: https://code.claude.com/docs/en/setup

```
irm https://claude.ai/install.ps1 | iex
```

Fonte: <https://github.com/anthropics/claude-code>

## Adicionar o marketplace e instalar o plugin

Execute os dois comandos no terminal, um depois do outro. O primeiro adiciona o marketplace do projeto. O segundo instala o plugin Lemo-Opuscar a partir dele. Se algum passo travar, o projeto orienta abrir uma issue em https://github.com/lemomo-ai/lemo-opuscar/issues

```
claude plugin marketplace add lemomo-ai/lemo-opuscar
claude plugin install lemo-opuscar@lemolab
```

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Abrir o Claude na pasta do filme

Deixe o terminal aberto na pasta que receberá o filme e execute o comando abaixo. O projeto de cada filme, do código ao vídeo pronto, fica na pasta em que você iniciou a sessão.

```
claude
```

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Configurar o esforço alto

Dentro do Claude Code (não no PowerShell), digite o comando abaixo. O projeto foi feito para o Claude: Fable, Opus e Sonnet funcionam. Outros modelos podem reproduzir mal os estilos. Fonte: https://github.com/lemomo-ai/lemo-opuscar

```
/effort high
```

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Pedido de exemplo para o filme

No Claude Code, envie o pedido abaixo. Ele dá ao agente o estilo Neon Tubes e o assunto. Se escolher o storyboard, o agente faz uma pausa para mostrar os planos principais no estilo real. Essa prévia ainda não é o filme final. Fonte: https://lemomo-ai.github.io/lemo-opuscar/

```
Make a film in the Neon Tubes style about the coffee farm my family runs.
```

Fonte: <https://lemomo-ai.github.io/lemo-opuscar/>

## Teste de pronto

Na pasta em que iniciou a sessão, abra o arquivo .mp4 entregue e reproduza até o fim. Ao lado dele vêm uma imagem de capa e, se o filme tem narração, um arquivo de legendas. Se só apareceram os planos do storyboard, volte à conversa: a produção final vem depois da pausa. Fonte: https://github.com/lemomo-ai/lemo-opuscar/blob/main/DIRECTOR.md

- [ ] Há imagem e o som toca.
- [ ] O assunto corresponde ao pedido.
- [ ] A aparência bate com a demonstração de Neon Tubes.

Fonte: <https://github.com/lemomo-ai/lemo-opuscar/blob/main/DIRECTOR.md>
