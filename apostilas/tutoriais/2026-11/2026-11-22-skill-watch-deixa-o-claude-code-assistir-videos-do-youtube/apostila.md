# Skill /watch deixa o Claude Code assistir vídeos do YouTube

_2026-11-22 · tutorial_

Com a skill /watch, o Claude Code baixa um vídeo, extrai quadros, transcreve a fala e responde como se tivesse assistido. Este tutorial ensina a instalar tudo no macOS ou Linux, colocar a skill no lugar, rodar em um vídeo e transformar o conteúdo em uma skill reutilizável. Ao final, você saberá conferir se funcionou e contornar o erro mais comum de vídeo sem legenda. A skill roda no Claude Code, não no chat comum do Claude.

## O que você terá no fim

Ao final deste tutorial, o seu Claude Code vai baixar um vídeo do YouTube, extrair quadros, transcrever a fala e responder sobre o conteúdo como se tivesse assistido. Você também vai saber pedir que ele transforme o que aprendeu em uma skill nova para reutilizar sempre.

A skill /watch é de código aberto. Ela roda dentro do Claude Code: no terminal, no VS Code ou no modo Code do aplicativo. No chat comum do Claude ela não funciona.

Fonte: <https://github.com/Nacib45/claude-skill-watch>

## Como isso funciona

A skill segue três etapas. Primeiro, baixa o vídeo com o yt-dlp. Depois, tira quadros do vídeo com o ffmpeg. Por fim, busca a transcrição: usa as legendas nativas do YouTube quando existem; se não existem, envia o áudio ao Whisper pela API da Groq, quando você configurou a chave.

O Claude recebe os quadros e a transcrição juntos e responde com base no que foi dito e mostrado. Você pode chamar a skill digitando /watch seguido do link, ou pedir em linguagem natural que ele assista ao vídeo.

Funciona com vídeo do YouTube, Vimeo, TikTok e arquivo local do seu computador. Também é possível usá-la com podcast, mas o README do projeto recomenda um fluxo de transcrição dedicado para áudio puro, porque a skill foi pensada para vídeo.

Fonte: <https://github.com/Nacib45/claude-skill-watch>

## Antes de começar

Confira estes requisitos antes de instalar. Os programas Claude Code, yt-dlp e ffmpeg serão instalados nos primeiros passos.

- Computador com macOS ou Linux. Os comandos principais são desses sistemas; no Windows, use os comandos indicados nas alternativas.
- Conta para usar o Claude Code.
- Python na versão 3.10 ou mais nova.
- Git instalado, para baixar a skill.
- Chave gratuita da Groq em console.groq.com, opcional, para transcrever vídeos sem legenda.

Fonte: <https://github.com/Nacib45/claude-skill-watch>

## Passo 1: instale o Claude Code no terminal

A skill vive dentro do Claude Code e não funciona no chat comum do Claude. Sem ele, não há onde instalá-la.

No macOS ou Linux, rode o comando abaixo. Se você já usa o Claude Code, pode pular para o passo seguinte.

Ao terminar, o Claude Code deve estar disponível no terminal. Se algo falhar, a documentação oficial lista outras formas de instalar.

No Windows, use `irm https://claude.ai/install.ps1 | iex`. Pelo Homebrew, use `brew install --cask claude-code`. Pelo WinGet, use `winget install Anthropic.ClaudeCode`. O método por npm está obsoleto.

1. Ação: instalar o Claude Code.
2. Onde: terminal do macOS ou Linux.
3. Resultado esperado: a instalação termina sem erro e o Claude Code fica disponível no terminal.

```
curl -fsSL https://claude.ai/install.sh | bash
```

Fonte: <https://github.com/anthropics/claude-code>

## Passo 2: instale o programa que baixa vídeos

A skill precisa de um baixador para buscar o vídeo antes de qualquer análise. O pacote é o yt-dlp.

Rode o comando abaixo no terminal. Ele usa o gerenciador de pacotes do Python, por isso a lista de requisitos pediu a versão 3.10 ou mais nova.

Se o terminal não reconhecer o gerenciador de pacotes, confira se o Python está instalado. No macOS, também funciona `brew install yt-dlp`. No Linux, `pipx install yt-dlp`. No Windows, `winget install yt-dlp.yt-dlp`.

1. Ação: instalar o yt-dlp.
2. Onde: terminal.
3. Resultado esperado: a instalação termina sem mensagem de erro.

```
pip install yt-dlp
```

Fonte: <https://github.com/yt-dlp/yt-dlp>

## Passo 3: instale o ffmpeg para extrair os quadros

Sem o ffmpeg, a skill não consegue extrair as imagens que o Claude vai olhar.

No macOS, rode o comando abaixo. No Linux, use `sudo apt install ffmpeg`. No Windows, `winget install Gyan.FFmpeg`.

Se o terminal reclamar que não encontrou o gerenciador de instalação, confira se o Homebrew está instalado no Mac. No Linux, o comando pede a sua senha antes de instalar.

1. Ação: instalar o ffmpeg.
2. Onde: terminal.
3. Resultado esperado: a instalação termina sem mensagem de erro.

```
brew install ffmpeg
```

Fonte: <https://ffmpeg.org>

## Configurar a chave Groq (opcional)

A chave só é necessária para vídeos sem legenda. Sem ela, a skill ainda funciona em vídeos com legenda, que cobrem a maior parte do YouTube.

Crie o arquivo de configuração e coloque a sua chave no lugar indicado. Troque o texto de exemplo pela chave copiada do console.

O comando com chmod protege o arquivo. A chave gratuita é obtida em console.groq.com.

1. Ação: criar o arquivo ~/.config/watch/.env com a chave.
2. Onde: terminal.
3. Resultado esperado: o arquivo existe e a chave fica salva para as próximas execuções.

```
mkdir -p ~/.config/watch
echo 'GROQ_API_KEY=ta_cle_ici' > ~/.config/watch/.env
chmod 600 ~/.config/watch/.env
```

Fonte: <https://github.com/Nacib45/claude-skill-watch>

## Passo 4: baixe a skill para a pasta de skills

O Claude Code só enxerga skills que estejam na pasta ~/.claude/skills. O comando abaixo copia o repositório do projeto para essa pasta.

Você também pode colar o link do repositório no Claude Code e pedir que ele mesmo instale a skill.

Se o Git avisar que a pasta já existe, renomeie a anterior e rode o comando de novo.

1. Ação: clonar o repositório.
2. Onde: terminal.
3. Resultado esperado: o Git copia o repositório e cria a pasta da skill dentro da pasta de skills.

```
git clone https://github.com/Nacib45/claude-skill-watch.git ~/.claude/skills/watch
```

Fonte: <https://github.com/Nacib45/claude-skill-watch>

## Passo 5: libere a execução do script da skill

A skill chama esse script para baixar o vídeo, tirar os quadros e transcrever a fala. O sistema precisa de permissão para executá-lo.

Quando dá certo, o comando não mostra nada. A ausência de erro é o sinal de sucesso.

Se aparecer que o arquivo não existe, volte ao passo anterior e confira se a skill foi baixada exatamente para a pasta indicada.

1. Ação: marcar o arquivo watch.py como executável.
2. Onde: terminal.
3. Resultado esperado: o comando termina sem nenhuma mensagem de erro.

```
chmod +x ~/.claude/skills/watch/watch.py
```

Fonte: <https://github.com/Nacib45/claude-skill-watch>

## Passo 6: abra o Claude Code

O Claude Code carrega as skills quando começa, então só enxerga a nova depois de ser aberto.

No terminal, entre na pasta de qualquer projeto seu e rode o comando abaixo.

Você deve ver a skill de assistir vídeos na lista de skills disponíveis. Se ela não aparecer, saia do Claude Code e abra de novo, e confira se os passos de instalação terminaram sem erro.

A skill roda no Claude Code: no terminal, no VS Code ou no modo Code do aplicativo.

1. Ação: abrir o Claude Code.
2. Onde: dentro da pasta de um projeto.
3. Resultado esperado: o Claude Code abre e a skill watch aparece na lista de skills disponíveis.

```
claude
```

Fonte: <https://github.com/Nacib45/claude-skill-watch>

## Passo 7: rode a skill em um vídeo

Dentro do Claude Code, digite o comando abaixo com o link de um vídeo do YouTube no lugar do endereço de exemplo. Prefira um vídeo curto.

A skill baixa o vídeo, tira os quadros, transcreve a fala e entrega tudo ao Claude. Você deve ver o Claude trabalhando e depois respondendo sobre o conteúdo.

Se o vídeo não tiver legenda e você não configurou a chave opcional, ele analisa só os quadros, sem a fala. Em vídeo longo, peça um trecho com o comando indicado nos cuidados.

1. Ação: chamar a skill com um link.
2. Onde: dentro do Claude Code.
3. Resultado esperado: o Claude baixa o vídeo, extrai quadros e transcrição e passa a responder sobre o conteúdo.

```
/watch <url>
```

Fonte: <https://github.com/Nacib45/claude-skill-watch>

## Passo 8: peça para o Claude virar uma skill

Assistir resolve uma vez só. Virar skill deixa o conhecimento guardado para você reutilizar sempre.

Cole o pedido abaixo no mesmo chat, depois da análise. O Claude deve resumir o que o vídeo ensina e criar uma skill nova com isso.

Se ele só resumir e não criar a skill, repita o pedido dizendo claramente que quer uma skill reutilizável. Assim você guarda vários vídeos, um por skill, sem depender da memória.

1. Ação: pedir a transformação em skill.
2. Onde: no mesmo chat do Claude Code, após a análise.
3. Resultado esperado: o Claude resume o que o vídeo ensina e cria uma skill nova a partir dele.

```
assiste, aprende o que ele ensina e transforma numa skill que eu possa usar pra sempre
```

## Exemplo completo

Imagine um vídeo curto de cinco minutos que ensina a montar uma campanha de e-mail. Você roda /watch com o link, espera o Claude trabalhar e recebe um resumo do que foi dito e mostrado.

Depois você cola o pedido de virar skill. O Claude cria uma skill com os passos da campanha. Na próxima semana, você pede para ele aplicar essa skill em um produto seu e ele segue o método aprendido.

Fonte: <https://github.com/Nacib45/claude-skill-watch>

## Prompt pronto

Use este prompt depois da análise de um vídeo, no mesmo chat. Ele não tem campos entre colchetes porque o pedido é fixo.

- Quando usar: após o Claude terminar de assistir ao vídeo.
- O que esperar: um resumo do que o vídeo ensina e uma skill nova criada a partir dele.

```
assiste, aprende o que ele ensina e transforma numa skill que eu possa usar pra sempre
```

## Teste de pronto

Use um vídeo curto que você já conhece. Assim você consegue dizer se o resumo bate com o que foi mostrado e falado.

- [ ] Cole o pedido de teste do bloco abaixo, com o link no lugar de <url>, e confira se o Claude devolve três ideias coerentes com o conteúdo.
- [ ] Se o Claude responder sem usar a skill, escreva `/watch` na frente do link para chamá-la de forma explícita.
- [ ] Em um vídeo sem legenda e sem chave Groq, verifique se ele analisa só os quadros.
- [ ] Se funcionou, você já tem um Claude que assiste vídeos.

```
/watch <url> Assista a este vídeo e resuma as 3 ideias principais
```

Fonte: <https://github.com/Nacib45/claude-skill-watch>

## Erros comuns e cuidados

A skill roda no Claude Code, não no chat comum do Claude. Instalar fora do Claude Code não adianta.

Confira também a origem dos comandos: use os links oficiais do projeto, do Claude Code, do yt-dlp, do ffmpeg e do console da Groq.

- Vídeo sem legenda e sem chave Groq: a skill analisa só os quadros, sem a fala.
- Skill não aparece ao abrir o Claude Code: saia e abra de novo; confira se os passos de instalação terminaram sem erro.
- Terminal não reconhece o pip: confira se o Python 3.10 ou mais novo está instalado.
- Terminal reclama do gerenciador de instalação no Mac: confira se o Homebrew está instalado.
- Arquivo watch.py não existe: volte ao passo de clone e confira se a pasta é ~/.claude/skills/watch.
- Pasta da skill já existe no clone: renomeie a anterior e rode o comando de novo.
- Vídeo longo: a cobertura fica esparsa por causa do limite de 100 quadros; peça um trecho com `python3 ~/.claude/skills/watch/watch.py "<url>" --start 12:00 --end 15:00`.
- Conteúdo pago ou com restrição: o yt-dlp pode não conseguir baixar; ele mostra um erro claro.
- Live streams e conteúdo protegido por paywall não são suportados.
- Para áudio puro, como podcast, o README recomenda um fluxo de transcrição dedicado.
- No Windows, o atalho python da Microsoft Store pode não rodar scripts; instale o Python 3.10 ou mais novo pelo python.org e use `python` no lugar de `python3`.
- Os quadros e a transcrição são enviados ao Claude e, no vídeo sem legenda com chave configurada, o áudio vai para a Groq; trate vídeos sensíveis com cuidado.

Fonte: <https://github.com/Nacib45/claude-skill-watch>

## Glossário

- Claude Code: ferramenta de programação do Claude que roda no terminal, no VS Code ou no modo Code do aplicativo.
- Skill: pacote de instruções e scripts que o Claude Code carrega ao iniciar.
- Slash command: comando digitado com / dentro do Claude Code, como /watch.
- yt-dlp: programa de linha de comando que baixa vídeo e áudio de vários sites.
- ffmpeg: programa que extrai quadros e processa mídia.
- Transcrição: texto da fala do vídeo, com marcações de tempo.
- Quadro: imagem estática tirada do vídeo em um momento específico.
- Whisper: modelo de transcrição de áudio usado quando não há legenda.
- Groq: serviço que oferece a API do Whisper usada pela skill.
- Repositório: pasta do projeto hospedada no GitHub.

## Plano de 7 dias

- Dia 1: instale o Claude Code e confira que ele abre no terminal.
- Dia 2: instale o yt-dlp e o ffmpeg.
- Dia 3: clone a skill, libere o script e, se quiser, configure a chave Groq.
- Dia 4: abra o Claude Code e rode a skill em um vídeo curto.
- Dia 5: peça que o Claude transforme o conteúdo em skill e teste com um resumo de três ideias.
- Dia 6: teste um vídeo sem legenda e um trecho de vídeo longo com --start e --end.
- Dia 7: escolha um vídeo ou podcast que valha a pena aprender e transforme em skill; revise o resultado.

## Para onde ir depois

Escolha um vídeo ou podcast que valha a pena aprender de verdade e mande o Claude transformar em skill. Você pode guardar vários vídeos, um por skill.

Se quiser uma variação que gera um arquivo de notas em Markdown com resumo, linha do tempo, citações e notas visuais, existe a implementação Newuxtreme/watch-video-skill, também de código aberto. Ela dispara só com /watch-video e tem um assistente de configuração.

- Tente o modo focado em vídeos longos com --start e --end.
- Para a variação Newuxtreme, clone em ~/.claude/skills/watch-video e rode `python scripts/setup.py`.
- Confira a documentação do Claude Code em code.claude.com/docs para outras formas de instalação.
- Repositório oficial da skill: github.com/Nacib45/claude-skill-watch.
- Repositório do yt-dlp: github.com/yt-dlp/yt-dlp.
- Site do ffmpeg: ffmpeg.org.
- Console da Groq: console.groq.com.

```
git clone https://github.com/Newuxtreme/watch-video-skill.git ~/.claude/skills/watch-video
```

Fonte: <https://github.com/Newuxtreme/watch-video-skill>
