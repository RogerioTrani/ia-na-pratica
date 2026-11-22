# Skill /watch deixa o Claude Code assistir vídeos do YouTube

_2026-11-22 · tutorial_

A skill /watch deixa o Claude Code analisar um vídeo do YouTube: ela baixa o vídeo, tira os quadros, transcreve a fala e entrega tudo ao Claude. Esta apostila leva da instalação ao teste, e termina com o pedido que transforma o vídeo em uma skill sua. Ela só roda no Claude Code, não no chat comum do Claude.

## O que a skill faz

A /watch é de código aberto. Ela baixa o vídeo, tira os quadros, transcreve a fala e entrega tudo ao Claude, que responde como se tivesse assistido. Funciona com vídeo do YouTube, arquivo do seu computador e podcast.

Ela roda no Claude Code: no terminal, no VS Code ou no modo Code do aplicativo do Claude. No chat comum do Claude ela não funciona.

Fonte: <https://github.com/Nacib45/claude-skill-watch>

## O que você precisa antes

- macOS ou Linux (os comandos desta apostila são desses sistemas)
- Conta para usar o Claude Code
- Python 3.10 ou mais novo
- Git instalado
- Chave Groq, opcional, para transcrever vídeos sem legenda: console.groq.com

Fonte: <https://github.com/Nacib45/claude-skill-watch>

## Passo 1: instale o Claude Code

Rode o comando no terminal do macOS ou Linux. Se você já usa o Claude Code, pule para o passo 2. No Windows, use `irm | iex`.

Ao terminar, o Claude Code fica disponível no terminal.

```
curl -fsSL https://claude.ai/install.sh | bash
```

Fonte: <https://github.com/anthropics/claude-code>

## Passos 2 e 3: instale o yt-dlp e o ffmpeg

O yt-dlp (github.com/yt-dlp/yt-dlp) baixa o vídeo. No macOS, `brew install yt-dlp` também serve. Se o terminal não reconhecer o pip, confira se o Python 3.10 ou mais novo está instalado.

O ffmpeg (ffmpeg.org) extrai os quadros. O comando abaixo é do macOS. No Linux, use `sudo apt install ffmpeg`. Em ambos os casos a instalação termina sem mensagem de erro.

Fonte: <https://github.com/yt-dlp/yt-dlp>

## Passos 4 e 5: coloque a skill no lugar

Clone o repositório na pasta de skills do Claude Code. Outra opção é colar o link do repositório (github.com/Nacib45/claude-skill-watch) no Claude Code e pedir que ele instale a skill.

Depois marque o `watch.py` como executável. O comando não mostra nada quando dá certo.

Fonte: <https://github.com/Nacib45/claude-skill-watch>

## Passos 6 e 7: abra o Claude Code e rode em um vídeo

Entre na pasta de um projeto seu e rode `claude`. A skill watch deve aparecer na lista de skills disponíveis. Ela é carregada na inicialização, então, se não aparecer, saia do Claude Code e abra de novo.

Dentro do Claude Code, digite `/watch` e o link de um vídeo do YouTube, de preferência curto. O Claude baixa o vídeo, extrai quadros e transcrição e passa a responder sobre o conteúdo.

- Vídeo sem legenda e sem chave Groq: o Claude analisa só os quadros.
- Vídeo longo: peça um trecho com `python3 ~/.claude/skills/watch/watch.py "<url>" --start 12:00 --end 15:00`.

Fonte: <https://github.com/Nacib45/claude-skill-watch>

## Passo 8: peça para o Claude virar uma skill

No mesmo chat, depois da análise, envie o pedido abaixo. O Claude resume o que o vídeo ensina e cria uma skill nova a partir dele. Se ele só resumir, repita o pedido dizendo que quer uma skill reutilizável.

```
assiste, aprende o que ele ensina e transforma numa skill que eu possa usar pra sempre
```

## Teste: resumo de três ideias

Use um vídeo curto que você já conhece e compare o resumo com o que viu. Devem voltar três ideias que batem com o vídeo. Se o Claude responder sem usar a skill, escreva `/watch` na frente do link para chamá-la.

Fonte: <https://github.com/Nacib45/claude-skill-watch>

## Além do vídeo

- A skill também analisa vídeos do Vimeo e do TikTok, além de arquivos locais.
- Outras formas de instalar o Claude Code: `brew install --cask claude-code` (Homebrew, macOS e Linux) e `winget install Anthropic.ClaudeCode` (Windows).
- Mais opções de instalação e solução de problemas do Claude Code estão na documentação oficial:
