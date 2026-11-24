# 10 projetos open source do GitHub para criar vídeos com IA

_2026-11-24 · reportagem_

Esta é a segunda parte da lista: dez projetos open source do GitHub, do 20º ao 11º, para editar, transcrever, legendar, animar e publicar vídeo com IA. A apostila traz o que cada projeto faz, o link do repositório e os comandos de instalação que o roteiro cita. Para o Whisper-WebUI há o passo a passo completo com Docker.

## Edição e transcrição (20º ao 18º)

Open Chat Cut (20º) edita vídeos com IA a partir de comandos em linguagem natural. A edição acontece numa linha do tempo real e editável, então você descreve a mudança e continua podendo ajustar o projeto à mão.

AI Video Transcriber (18º) transcreve e resume vídeos e podcasts a partir de um link ou de um arquivo local. Serve para transformar uma gravação em base de roteiro ou de post.

- Open Chat Cut: github.com/0xsline/OpenChatCut
- AI Video Transcriber: github.com/wendy7756/AI-Video-Transcriber

Fonte: <https://github.com/0xsline/OpenChatCut>

## Whisper-WebUI (19º): instalação com Docker

Interface web para transcrever áudio e vídeo. Você escolhe entre três implementações do Whisper: openai/whisper, SYSTRAN/faster-whisper e Vaibhavs10/insanely-fast-whisper.

- Clone o repositório.
- Rode docker compose build.
- Rode docker compose up.
- Abra http://localhost:7860 no navegador.
- Sem Docker: rode install.bat ou install.sh e inicie com start-webui.bat ou start-webui.sh.

Fonte: <https://github.com/jhj0517/Whisper-WebUI>

## Agentes de edição e redes sociais (17º e 16º)

Open Storyline (17º) é um agente de edição. Você conversa com ele, e ele monta o roteiro e a narração e organiza as cenas a partir dos seus vídeos e imagens.

Easel (16º) é um assistente de redes sociais. Descobre pautas, planeja, cria texto, imagem, áudio e vídeo, e publica.

- Open Storyline: github.com/FireRedTeam/FireRed-OpenStoryline
- Easel: github.com/ZJU-REAL/Easel

Fonte: <https://github.com/FireRedTeam/FireRed-OpenStoryline>

## Legendas e animação (15º e 14º)

Auto Subs (15º) gera legendas no seu computador, sem nuvem. Ele se conecta ao DaVinci Resolve, ao Premiere e ao After Effects.

Stickman Video Director (14º) transforma roteiros em vídeos animados com personagens palito, em vários estilos. Dá para publicar sem gravar nada.

- Auto Subs: github.com/tmoroney/auto-subs
- Stickman Video Director: github.com/kaomei/stickman-video-director

Fonte: <https://github.com/tmoroney/auto-subs>

## YouTube Automation Agent (13º)

Agente que pesquisa, roteiriza e produz vídeos para o YouTube. Ele só publica depois da sua aprovação.

```
git clone https://github.com/darkzOGx/youtube-automation-agent.git
```

Fonte: <https://github.com/darkzOGx/youtube-automation-agent>

## LinkedIn Skills (12º)

São 12 skills que escrevem posts, comentários e respostas no LinkedIn com a sua voz.

```
npx skills add sergebulaev/linkedin-skills
```

Fonte: <https://github.com/sergebulaev/linkedin-skills>

## AI YouTube Shorts Generator (11º)

Corta vídeos longos do YouTube em Shorts verticais 9:16, com os melhores trechos.

```
git clone https://github.com/Anil-matcha/AI-Youtube-Shorts-Generator.git
```

Fonte: <https://github.com/Anil-matcha/AI-Youtube-Shorts-Generator>

## Além do vídeo

- Whisper-WebUI roda também sem Docker, com install.bat ou install.sh e start-webui.bat ou start-webui.sh.
- Whisper-WebUI é feito em Gradio.
- As três implementações do Whisper do Whisper-WebUI são openai/whisper, SYSTRAN/faster-whisper e Vaibhavs10/insanely-fast-whisper.
