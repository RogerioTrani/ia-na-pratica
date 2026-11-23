# Lemo-Opuscar chega a 99 estilos para filmes em código

_2026-11-23 · tutorial_

O Lemo-Opuscar reúne 99 estilos de filme feitos em código para o Claude Code. A atualização de 12 de novembro de 2026 acrescentou 33 estilos, em 15 categorias. Esta apostila leva do zero ao primeiro filme: instalar o Claude Code e o plugin, abrir a sessão na pasta do projeto, configurar o esforço, escolher o estilo Neon Tubes e pedir o filme. O agente escreve o código das imagens, organiza a trilha e monta o vídeo, sem modelo gerador de vídeo.

## O que você precisa ter

O caminho desta apostila usa Windows com PowerShell. Cada filme leva cerca de 30 a 60 minutos de trabalho do agente e consome uma boa quantidade de tokens.

- Acesso ao Claude Code
- Node 20 ou superior
- ffmpeg 7 ou superior
- Python 3.11 ou superior, ou uv (https://docs.astral.sh/uv/)
- Tokens disponíveis para a sessão

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Passo 1: instale o Claude Code

No PowerShell do Windows, execute o comando abaixo. Se você já usa o Claude Code neste computador, pule para o passo 2. Outras formas de instalação estão na documentação oficial: https://code.claude.com/docs/en/setup

```
irm https://claude.ai/install.ps1 | iex
```

Fonte: <https://github.com/anthropics/claude-code>

## Passos 2 e 3: adicione o marketplace e instale o plugin

O marketplace é o catálogo de onde o Claude Code busca o plugin, então ele entra primeiro. Execute os dois comandos no terminal, um depois do outro.

Se algum passo travar, o projeto orienta abrir uma issue em https://github.com/lemomo-ai/lemo-opuscar/issues.

- Primeiro comando: adiciona o marketplace do projeto.
- Segundo comando: instala o plugin Lemo-Opuscar a partir dele.

```
claude plugin marketplace add lemomo-ai/lemo-opuscar
claude plugin install lemo-opuscar@lemolab
```

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Passo 4: abra o Claude na pasta do filme

O plugin funciona a partir de qualquer pasta. O projeto de cada filme, do código ao vídeo pronto, fica na pasta em que você iniciou a sessão. Deixe o terminal aberto na pasta que receberá o filme e execute:

No primeiro uso, o agente baixa guias, ferramentas e estilos para ~/lemo-opuscar, uma biblioteca compartilhada por todos os seus filmes.

```
claude
```

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Passo 5: configure o esforço alto

Dentro do Claude Code (não no PowerShell), digite o comando abaixo. O projeto foi feito para o Claude: Fable, Opus e Sonnet funcionam. Outros modelos podem reproduzir mal os estilos.

```
/effort high
```

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Passo 6: escolha o estilo Neon Tubes

Abra a galeria oficial, lemomo-ai.github.io/lemo-opuscar, e encontre Neon Tubes na Estação 12 (Light & Lines). Assista à demonstração de 0:48. A página do estilo traz o filme demonstrativo, imagens e as orientações que o agente segue.

Nesta apostila o estilo fica fixo em Neon Tubes porque ele aparece no pedido de exemplo.

Fonte: <https://lemomo-ai.github.io/lemo-opuscar/>

## Passo 7: peça o primeiro filme

No Claude Code, envie o pedido de exemplo. Ele dá ao agente duas informações: a aparência (o estilo) e o assunto.

O agente pode perguntar detalhes do tema, que materiais você tem (voz, música, fotos) e se você quer ver um storyboard antes. Responda para a produção avançar. Se escolher o storyboard, o agente faz uma pausa para mostrar os planos principais no estilo real. Essa prévia ainda não é o filme final.

```
Make a film in the Neon Tubes style about the coffee farm my family runs.
```

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Teste: confira o vídeo final

Na pasta em que iniciou a sessão, abra o arquivo .mp4 entregue e reproduza até o fim. Ao lado dele vêm uma imagem de capa e, se o filme tem narração, um arquivo de legendas.

- Há imagem e o som toca.
- O assunto corresponde ao pedido.
- A aparência bate com a demonstração de Neon Tubes.
- Se só apareceram os planos do storyboard, volte à conversa: a produção final vem depois da pausa.
- Se houver defeito, descreva o problema ao agente e peça a correção.

Fonte: <https://github.com/lemomo-ai/lemo-opuscar/blob/main/DIRECTOR.md>

## Além do vídeo

- Atualizar o plugin: `claude plugin marketplace update lemolab && claude plugin update lemo-opuscar@lemolab`, depois reiniciar o Claude Code.
- Desinstalar: `claude plugin uninstall lemo-opuscar@lemolab` e apagar ~/lemo-opuscar. Seus estilos próprios em ~/lemo-my-styles/ ficam até você apagar a pasta.
- Personalizar um estilo da biblioteca ou criar um do zero, com o fluxo descrito em MY-STYLES.md no repositório.
- Três estilos (Manga Panels, Text Flash Cuts, Comic History Cartoon) desenham os personagens com um gerador de imagens que você traz, como o Codex CLI. Os demais funcionam sem ele.
- Saída padrão em 1920×1080 a 24 fps; alguns estilos definem a própria taxa de quadros, e outros tamanhos podem ser pedidos.
