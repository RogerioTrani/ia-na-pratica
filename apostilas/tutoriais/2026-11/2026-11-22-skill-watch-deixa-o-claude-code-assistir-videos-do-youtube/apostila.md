# Skill /watch deixa o Claude Code assistir vídeos do YouTube

_2026-11-22 · tutorial_

A skill /watch deixa o Claude Code analisar um vídeo do YouTube: ela baixa o vídeo, tira os quadros, transcreve a fala e entrega tudo ao Claude. Esta apostila leva da instalação ao teste, e termina com o pedido que transforma o vídeo em uma skill sua. Ela só roda no Claude Code, não no chat comum do Claude.

## O que você terá no fim

Ao final, o Claude Code analisa um vídeo do YouTube com a skill /watch, responde sobre o conteúdo e pode transformar o vídeo em uma skill sua. A /watch é de código aberto. Fonte: https://github.com/Nacib45/claude-skill-watch

Fonte: <https://github.com/Nacib45/claude-skill-watch>

## Antes de começar

Requisitos para seguir o tutorial. Os comandos desta apostila são de macOS ou Linux.

- macOS ou Linux.
- Conta para usar o Claude Code.
- Python 3.10 ou mais novo.
- Git instalado.
- Chave Groq, opcional, para transcrever vídeos sem legenda: console.groq.com

Fonte: <https://github.com/Nacib45/claude-skill-watch>

## Passo a passo

Siga os passos na ordem. O comando de instalação do Claude Code tem seção própria.

1. instale o Claude Code. Rode o comando no terminal do macOS ou Linux. No Windows, use irm | iex. Resultado esperado: o Claude Code fica disponível no terminal.
2. instale o yt-dlp, que baixa o vídeo. No macOS, brew install yt-dlp também serve. Resultado esperado: o yt-dlp responde no terminal. Repositório: https://github.com/yt-dlp/yt-dlp
3. instale o ffmpeg, que extrai os quadros. No Linux, use sudo apt install ffmpeg. Resultado esperado: a instalação termina sem mensagem de erro. Site: ffmpeg.org
4. clone o repositório na pasta de skills do Claude Code. Resultado esperado: a pasta da skill fica no lugar.
5. marque o watch.py como executável. Resultado esperado: o comando não mostra nada quando dá certo.
6. entre na pasta de um projeto seu e rode claude. Resultado esperado: a skill watch aparece na lista de skills disponíveis.
7. dentro do Claude Code, digite /watch e o link de um vídeo do YouTube, de preferência curto. Resultado esperado: o Claude baixa o vídeo, extrai quadros e transcrição e passa a responder sobre o conteúdo.
8. peça para o Claude virar uma skill. No mesmo chat, depois da análise, envie o pedido de skill. Resultado esperado: o Claude resume o que o vídeo ensina e cria uma skill nova a partir dele.

Fonte: <https://github.com/Nacib45/claude-skill-watch>

## Instalar o Claude Code

Endereço do instalador: https://claude.ai/install.sh. Rode o comando abaixo no terminal do macOS ou Linux. Se você já usa o Claude Code, pule para o passo 2. Ao terminar, o Claude Code fica disponível no terminal. Fonte: https://github.com/anthropics/claude-code

```
curl -fsSL https://claude.ai/install.sh | bash
```

Fonte: <https://github.com/anthropics/claude-code>

## Pedido para virar skill

Envie este pedido no mesmo chat, depois da análise. Se o Claude só resumir, repita o pedido dizendo que quer uma skill reutilizável.

```
assiste, aprende o que ele ensina e transforma numa skill que eu possa usar pra sempre
```

Fonte: <https://github.com/Nacib45/claude-skill-watch>

## Teste de pronto

Use um vídeo curto que você já conhece e compare o resumo com o que viu. Devem voltar três ideias que batem com o vídeo. Se o Claude responder sem usar a skill, escreva /watch na frente do link para chamá-la. Fonte: https://github.com/Nacib45/claude-skill-watch

- [ ] O resumo traz três ideias que batem com o vídeo.
- [ ] Vídeo sem legenda e sem chave Groq: o Claude analisa só os quadros.

Fonte: <https://github.com/Nacib45/claude-skill-watch>

## Cuidados e outras opções

Vídeo longo: peça um trecho com python3 ~/.claude/skills/watch/watch.py "<url>" --start 12:00 --end 15:00. A skill também analisa vídeos do Vimeo e do TikTok, além de arquivos locais. Outras formas de instalar o Claude Code: brew install --cask claude-code (Homebrew, macOS e Linux) e winget install Anthropic.ClaudeCode (Windows).

Mais opções de instalação e solução de problemas do Claude Code estão na documentação oficial: https://github.com/anthropics/claude-code

Fonte: <https://github.com/anthropics/claude-code>
