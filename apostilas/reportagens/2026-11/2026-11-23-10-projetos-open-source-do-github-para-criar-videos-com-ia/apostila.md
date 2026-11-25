# 10 projetos open source do GitHub para criar vídeos com IA

_2026-11-23 · reportagem_

Esta é a segunda parte da lista: dez projetos open source do GitHub, do 20º ao 11º, para editar, transcrever, legendar, animar e publicar vídeo com IA. A apostila traz o que cada projeto faz, o link do repositório e os comandos de instalação que o roteiro cita. A promessa é levar de uma ideia a um projeto instalado, com o ponto de partida de cada um.

## Como usar esta lista

Esta é a segunda parte da lista: dez projetos open source do GitHub, do 20º ao 11º, para editar, transcrever, legendar, animar e publicar vídeo com IA. A apostila traz o que cada projeto faz, o link do repositório e os comandos de instalação que o roteiro cita. Para o Whisper-WebUI há o passo a passo completo com Docker.

Fonte: <https://github.com/0xsline/OpenChatCut>

## Por onde começar

Escolha o projeto pela etapa do vídeo e siga a seção dele.

1. escolha o projeto pela etapa do vídeo: edição, legenda, animação ou publicação. Resultado: você reduz a lista a uma ou duas opções.
2. abra o repositório do projeto escolhido e siga os comandos da seção dele. Resultado: o projeto roda na sua máquina.

Fonte: <https://github.com/0xsline/OpenChatCut>

## Open Chat Cut

Open Chat Cut (20º) edita vídeos com IA a partir de comandos em linguagem natural. A edição acontece numa linha do tempo real e editável, então você descreve a mudança e continua podendo ajustar o projeto à mão. Repositório: github.com/0xsline/OpenChatCut

- Edição de vídeo por comandos em linguagem natural.
- Linha do tempo real e editável.

Fonte: <https://github.com/0xsline/OpenChatCut>

## AI Video Transcriber

AI Video Transcriber (18º) transcreve e resume vídeos e podcasts a partir de um link ou de um arquivo local. Serve para transformar uma gravação em base de roteiro ou de post. Repositório: github.com/wendy7756/AI-Video-Transcriber

- Transcrição e resumo de vídeos e podcasts.
- Entrada por link ou arquivo local.

## Whisper-WebUI

Whisper-WebUI (19º) é uma interface web para transcrever áudio e vídeo. Você escolhe entre três implementações do Whisper: openai/whisper, SYSTRAN/faster-whisper e Vaibhavs10/insanely-fast-whisper. Repositório: https://github.com/jhj0517/Whisper-WebUI

- Clone o repositório.
- Rode docker compose build.
- Rode docker compose up.
- Abra http://localhost:7860 no navegador.
- Sem Docker: rode install.bat ou install.sh e inicie com start-webui.bat ou start-webui.sh.

Fonte: <https://github.com/jhj0517/Whisper-WebUI>

## Open Storyline

Open Storyline (17º) é um agente de edição. Você conversa com ele, e ele monta o roteiro e a narração e organiza as cenas a partir dos seus vídeos e imagens. Repositório: github.com/FireRedTeam/FireRed-OpenStoryline

- Agente de edição por conversa.
- Monta roteiro, narração e cenas a partir de vídeos e imagens.

Fonte: <https://github.com/FireRedTeam/FireRed-OpenStoryline>

## Easel

Easel (16º) é um assistente de redes sociais. Descobre pautas, planeja, cria texto, imagem, áudio e vídeo, e publica. Repositório: github.com/ZJU-REAL/Easel

- Descobre pautas e planeja conteúdo.
- Cria texto, imagem, áudio e vídeo, e publica.

## Auto Subs

Auto Subs (15º) gera legendas no seu computador, sem nuvem. Ele se conecta ao DaVinci Resolve, ao Premiere e ao After Effects. Repositório: github.com/tmoroney/auto-subs

- Legendas geradas no seu computador, sem nuvem.
- Conexão com DaVinci Resolve, Premiere e After Effects.

Fonte: <https://github.com/tmoroney/auto-subs>

## Stickman Video Director

Stickman Video Director (14º) transforma roteiros em vídeos animados com personagens palito, em vários estilos. Dá para publicar sem gravar nada. Repositório: github.com/kaomei/stickman-video-director

- Roteiro vira vídeo animado com personagens palito.
- Vários estilos disponíveis.

## YouTube Automation Agent

Agente que pesquisa, roteiriza e produz vídeos para o YouTube (13º). Ele só publica depois da sua aprovação. Repositório: https://github.com/darkzOGx/youtube-automation-agent. Clone: https://github.com/darkzOGx/youtube-automation-agent.git

- Pesquisa, roteiro e produção de vídeos para o YouTube.
- Publicação somente após a sua aprovação.

```
git clone https://github.com/darkzOGx/youtube-automation-agent.git
```

Fonte: <https://github.com/darkzOGx/youtube-automation-agent>

## LinkedIn Skills

São 12 skills que escrevem posts, comentários e respostas no LinkedIn com a sua voz (12º). Repositório: https://github.com/sergebulaev/linkedin-skills

- Posts, comentários e respostas no LinkedIn.
- Escrita com a sua voz.

```
npx skills add sergebulaev/linkedin-skills
```

Fonte: <https://github.com/sergebulaev/linkedin-skills>

## AI YouTube Shorts Generator

Corta vídeos longos do YouTube em Shorts verticais 9:16, com os melhores trechos (11º). Repositório: https://github.com/Anil-matcha/AI-Youtube-Shorts-Generator. Clone: https://github.com/Anil-matcha/AI-Youtube-Shorts-Generator.git

- Corte de vídeos longos em Shorts verticais 9:16.
- Seleção dos melhores trechos.

```
git clone https://github.com/Anil-matcha/AI-Youtube-Shorts-Generator.git
```

Fonte: <https://github.com/Anil-matcha/AI-Youtube-Shorts-Generator>

## Cuidados

Os comandos de instalação são os que o roteiro cita. Confira o repositório antes de rodar cada um.

Whisper-WebUI roda também sem Docker, com install.bat ou install.sh e start-webui.bat ou start-webui.sh. É feito em Gradio.

Fonte: <https://github.com/jhj0517/Whisper-WebUI>
