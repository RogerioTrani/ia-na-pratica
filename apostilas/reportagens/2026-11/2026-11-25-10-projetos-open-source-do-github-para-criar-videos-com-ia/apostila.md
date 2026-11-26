# 10 projetos open source do GitHub para criar vídeos com IA

_2026-11-25 · reportagem_

Esta apostila apresenta dez projetos open source do GitHub para criar e publicar vídeos com IA, da transcrição à publicação. Você vai conhecer o que cada um faz, quando escolher, como instalar os principais e quais cuidados tomar antes de confiar. Ao final, terá um guia prático para montar seu próprio estúdio de produção audiovisual com IA, com comandos prontos para copiar. São abordados editores conversacionais, transcrição, legendagem, edição por narrativa, geração visual, animação e automação de publicação.

## Como usar esta lista

Esta lista reúne dez projetos open source do GitHub para criar e publicar vídeos com IA, formando um estúdio autônomo: transcrição, legendagem, edição, animação e publicação. São projetos de código aberto, disponíveis no GitHub.

Eles se complementam: uns transcrevem e legendam, outros editam por comando em linguagem natural, outros automatizam a publicação no YouTube e no LinkedIn, outros geram vídeos verticais ou animações.

Para quem serve: criadores, desenvolvedores e quem faz marketing de conteúdo e quer montar o próprio ambiente de produção com IA.

1. Salve esta lista para consultar no GitHub quando for montar o estúdio; resultado: as referências ficam sempre à mão.
2. Identifique o gargalo atual da sua produção (transcrição, legenda, edição, animação ou publicação).
3. Instale uma ferramenta correspondente e teste em um projeto real; resultado: você valida se resolve seu caso antes de combinar várias.
4. Combine as ferramentas em pipeline, uma por vez, validando cada etapa.
5. Verifique licença e requisitos de cada projeto antes de usar em produção.

## Open Chat Cut

Open Chat Cut é um editor de vídeo open source que une agentes de conversação e edição profissional em linha do tempo no mesmo espaço de trabalho. É uma alternativa open source ao ChatCut comercial, independente e licenciada sob AGPL; não tem afiliação com o produto comercial.

A ideia central é que cada edição seja escrita em faixas, clipes, transições, legendas, efeitos e mídia reais do projeto, em vez de gerar um vídeo final imutável. Você pode continuar editando manualmente, desfazer, refazer, salvar versões ou passar o projeto para outro agente.

O projeto é local-first: projetos e mídia ficam na sua máquina por padrão e as chaves de API permanecem no servidor. É voltado a criadores e desenvolvedores que querem IA participando do fluxo de edição real sem abrir mão do controle profissional.

- Tecnologia: TypeScript 6, React 19, Remotion 4 e Electron 43; integração com MCP (Model Context Protocol) para agentes externos.
- Funcionalidades: linha do tempo multifaixa com movimento, corte, divisão, ripple, snap, keyframes, marcadores, desfazer e refazer; efeitos WebGL, LUTs, chroma key, zoom, transições e shaders personalizados; áudio com várias faixas, efeitos sonoros, música de fundo, gravação de locução, loudness, auto-ducking e isolamento vocal; transcrição com edição por palavra, compressão de pausas, busca, falantes e visualização por clipes; legendas automáticas, estilos nomeados, tradução, sobreposição na linha do tempo e exportação SRT; motion graphics com templates, sandbox seguro e templates personalizados; segmentação de pessoas e zonas seguras para rosto no navegador, para que legendas evitem o falante, o reenquadramento siga o assunto e gráficos caiam em espaços vazios.
- Exportação: MP4, áudio, legendas, FCPXML e dados completos do projeto.
- Ciclo central: descreva o objetivo, o agente lê o projeto, produz edições verificáveis, escreve na linha do tempo, você pré-visualiza/ajusta/desfaz, legendas e mixagem, exportação.
- Como começar: acesse o site openchatcut.com ou o repositório oficial; há edição desktop (Pro) para instalar e começar a cortar.

Fonte: <https://github.com/0xsline/OpenChatCut>

## Anysub (antigo Whishper)

Anysub, antes chamado Whishper, transforma áudio e vídeo em legendas com uma interface web fácil de usar. Você envia uma gravação, o Whisper transcreve e, depois, você corrige texto e tempo no editor e exporta. Tudo roda na sua própria máquina ou servidor.

A transcrição usa Whisper, do modelo tiny ao large-v3-turbo, com tempos por palavra. O editor de legendas tem linha do tempo com forma de onda, desfazer e salvamento automático, além de avisos para legendas rápidas demais, longas demais ou que se sobrepõem.

Também traduz para outros idiomas no seu servidor ou com o modelo de chat de um provedor, e exporta em SRT, WebVTT, LRC, texto simples ou JSON. Uploads podem ser retomados em arquivos de horas. A biblioteca é pesquisável e há páginas de administração para modelos, padrões, limites de upload, espaço em disco e workers.

- Requisitos: Linux em x86-64 com Docker e Docker Compose.
- Transcrição em GPU é várias vezes mais rápida que em CPU; GPUs AMD e Intel ainda não são suportadas.
- Como começar: crie a pasta, baixe o arquivo compose.yaml da release, opcionalmente baixe compose.cuda.yaml para NVIDIA GPU ou compose.remote.yaml para apenas provedores externos, defina COMPOSE_FILE no .env e rode docker compose up -d. Acesse http://localhost:5173 e crie a conta; o código de configuração aparece em docker compose logs web.
- Licença: AGPL-3.0-only.

```
mkdir anysub && cd anysub
curl -fsSLO https://github.com/pluja/anysub/releases/latest/download/compose.yaml
docker compose up -d
```

Fonte: <https://github.com/pluja/anysub>

## AI Video Transcriber

Ferramenta para transcrever, resumir e arquivar vídeos e podcasts com IA. Aceita URL de YouTube, TikTok, Bilibili, Apple Podcasts, SoundCloud e mais de 30 plataformas, ou upload de arquivo local (áudio, vídeo ou texto).

A arquitetura é subtitle-first: em plataformas com legenda nativa (como YouTube), a transcrição é extraída instantaneamente, sem baixar áudio; o Whisper só entra como fallback, o que acelera muito o pipeline. O download do vídeo original ocorre em paralelo com a transcrição, com pré-visualização inline no cartão de resultados e salvamento em um clique. No caminho Whisper, o áudio é extraído desse mesmo arquivo, então o vídeo é baixado uma vez só. Desligue 'Manter vídeo original' para jobs só de texto.

O texto é otimizado por IA (correção de erros, completar frases, paragrafação), com resumos em 11 idiomas e tradução automática quando o idioma do resumo difere do idioma da fonte. Você traz seu próprio modelo: configure qualquer endpoint compatível com OpenAI (OpenAI, OpenRouter, LLM local etc.) direto na interface, informando URL base e chave de API, e clique em Fetch para descobrir os modelos disponíveis. As credenciais ficam no localStorage do navegador.

O progresso é transmitido em tempo real por server-sent events, com selo indicando se o job usou o caminho de legenda ou Whisper. A interface é responsiva e com tema escuro.

- Requisitos: Python 3.8+, FFmpeg (para extração de áudio do yt-dlp, merge de vídeo e normalização de mídia enviada) e chave de API de provedor compatível com OpenAI.
- Arquivos locais aceitos: .txt (tratado como texto de transcrição), .mp3, .mp4, .m4a, .wav, .webm, .mkv, .ogg, .flac.
- Idiomas de resumo: en, zh, es, fr, de, it, pt, ru, ja, ko, ar.
- Modelos Whisper: tiny a large, padrão base.
- Como começar (instalação automática): clone o repositório, entre na pasta, dê permissão ao install.sh e execute-o. Alternativas: Docker (copie .env.example para .env e rode docker-compose up -d, ou build direto) e manual (venv, pip install -r requirements.txt, FFmpeg via brew/apt/yum).
- Para iniciar: python3 start.py e abra http://localhost:8000. Para vídeos longos, use python3 start.py --prod (desativa hot-reload para manter a conexão SSE estável em tarefas de 30 a 60 minutos).
- Uso pela interface: escolha URL ou arquivo, selecione idioma do resumo, mantenha ou desligue 'Manter vídeo original', configure IA em 'AI Settings', clique em Transcrever. Selos: ⚡ Subtitle (verde) para legenda nativa, 🎙 Whisper (ciano) para transcrição por áudio. Resultados em abas Transcript, AI Summary e Translation (quando aplicável), com ícone de download em cada aba e player inline do vídeo original.
- Uso por linha de comando (headless): venv/bin/python transcribe.py URL --json; flags -l/--summary-language, --no-llm (sem chave de API), --no-video, --whisper-model, -o/--output-dir, --json/-q. Códigos de saída: 0 sucesso, 2 entrada inválida, 1 falha de download/transcodificação.
- Integração com agentes: plugin Codex (pasta .codex-plugin/plugin.json e skills/video-transcribe/SKILL.md), skill Claude Code (.claude/skills/video-transcribe/SKILL.md) e servidor MCP stdio com a ferramenta transcribe_video (verifique com venv/bin/python mcp_server.py --selftest).
- Quando a fonte não tem fala, o campo no_speech sinaliza isso; trate esse caso no seu fluxo.

```
git clone https://github.com/wendy7756/AI-Video-Transcriber.git
cd AI-Video-Transcriber
chmod +x install.sh
./install.sh
python3 start.py
venv/bin/python transcribe.py "https://www.youtube.com/watch?v=VIDEO_ID" --json
```

Fonte: <https://github.com/wendy7756/AI-Video-Transcriber>

## Open Storyline (FireRed-OpenStoryline)

Agente de edição de vídeo que transforma a edição manual em direção orientada por intenção, por meio de interação em linguagem natural, planejamento com LLM e orquestração precisa de ferramentas. A criação é transparente e com humano no loop, com Style Skills reutilizáveis para storytelling consistente e profissional.

Busca e organização inteligente de mídia: pesquisa online e baixa imagens e clipes que combinam com o pedido, com segmentação de clipes e compreensão de conteúdo a partir da mídia temática.

Geração inteligente de roteiro: combina tema do usuário, compreensão visual e reconhecimento de emoção para construir storylines e narração contextual, com transferência de estilo few-shot por texto de referência (replicando tom, ritmo e estrutura de frases).

Recomendação inteligente de música, locução e fontes: importa playlists pessoais, recomenda BGM conforme conteúdo e humor, com sincronização de batida; você descreve o tom desejado e o sistema combina locuções e fontes.

Refinamento conversacional: cortar, trocar ou resequenciar clipes; editar roteiros e ajustar detalhes visuais (cor, fonte, contorno, posição) só por prompts em linguagem natural, com resultado imediato.

Arquivamento de skills de edição: salve o fluxo completo de edição como Skill personalizada; troque a mídia e aplique a Skill para replicar o estilo, permitindo criação em lote.

Notícias do projeto: em 02/04/2026, geração de transições por IA (cria shots de transição a partir do último frame de um clipe, do primeiro frame do próximo e de uma descrição em linguagem natural); em 22/03/2026, skill de rough cut baseada em ASR para vídeos de fala (remove palavras de preenchimento, disfluências e frases repetidas, com segmentação alinhada por timestamp); em 12/03/2026, integração com OpenClaw e Claude Code; em 10/02/2026, código aberto.

- Requisitos: Python 3.11 ou superior; instalação via Conda (ambiente 'storyline').
- Como começar: clone o repositório, crie e ative o ambiente Conda com Python 3.11, execute sh build_env.sh (Linux/macOS, instalação automática) ou siga a instalação manual. Há Skills para OpenClaw (openstoryline-install, openstoryline-use) e Claude Code (/openstoryline-install, /openstoryline-use); outros agentes compatíveis, em caráter experimental, via npx skills add.
- Licença: Apache 2.0. Demonstração no Hugging Face e página inicial própria.
- Observação: transições por IA dependem de serviços AIGC de terceiros, com custo relativamente alto e resultados imprevisíveis; habilite só quando necessário. Os vídeos de demonstração são comprimidos; a saída real mantém a resolução original e suporta dimensões personalizadas.

```
git clone https://github.com/FireRedTeam/FireRed-OpenStoryline.git
cd FireRed-OpenStoryline
conda create -n storyline python=3.11
conda activate storyline
sh build_env.sh
```

Fonte: <https://github.com/FireRedTeam/FireRed-OpenStoryline>

## Easel

Utiliza modelos avançados de IA para facilitar a criação, o tratamento e a edição de conteúdo visual. É voltado a quem produz material visual com IA e quer tratar esse material em código aberto.

Para detalhes de instalação, requisitos e exemplos de uso, consulte o repositório oficial.

- Foco: criação, tratamento e edição de conteúdo visual com modelos avançados de IA.
- Como começar: acesse o repositório oficial e siga o README para instalação e requisitos.
- Repositório oficial: github.com/ZJU-REAL/Easel

Fonte: <https://github.com/ZJU-REAL/Easel>

## Auto Subs

Gera e sincroniza legendas automáticas a partir de arquivos de áudio e vídeo, com alta precisão. Serve para quem quer legendar vídeos sem fazer a sincronização manual.

Para detalhes de instalação, requisitos e exemplos de uso, consulte o repositório oficial.

- Foco: geração e sincronização de legendas automáticas a partir de áudio e vídeo.
- Como começar: acesse o repositório oficial e siga o README para instalação e requisitos.
- Repositório oficial: github.com/tmoroney/auto-subs

Fonte: <https://github.com/tmoroney/auto-subs>

## Stickman Video Director

Permite criar e dirigir vídeos animados com personagens Stickman e narrativas visuais. É uma opção para quem quer animação simples com personagens e história, sem montar tudo do zero.

Para detalhes de instalação, requisitos e exemplos de uso, consulte o repositório oficial.

- Foco: criação e direção de vídeos animados com personagens Stickman e narrativas visuais.
- Como começar: acesse o repositório oficial e siga o README para instalação e requisitos.
- Repositório oficial: github.com/kaomei/stickman-video-director

Fonte: <https://github.com/kaomei/stickman-video-director>

## YouTube Automation Agent

Agente de inteligência artificial desenvolvido para automatizar a produção de vídeos para o YouTube. Voltado a quem quer delegar etapas da produção de vídeos para o YouTube a um agente.

Para detalhes de instalação, requisitos e exemplos de uso, consulte o repositório oficial.

- Foco: automação da produção de vídeos para o YouTube por agente de IA.
- Como começar: acesse o repositório oficial e siga o README para instalação e requisitos.
- Repositório oficial: github.com/darkzOGx/youtube-automation-agent

Fonte: <https://github.com/darkzOGx/youtube-automation-agent>

## LinkedIn Skills

Conjunto de skills para automatizar a pesquisa, a redação e a publicação de conteúdos estratégicos no LinkedIn. Serve para quem produz conteúdo profissional no LinkedIn e quer automatizar pesquisa, texto e publicação.

Para detalhes de instalação, requisitos e exemplos de uso, consulte o repositório oficial.

- Foco: automação de pesquisa, redação e publicação de conteúdo estratégico no LinkedIn.
- Como começar: acesse o repositório oficial e siga o README para instalação e requisitos.
- Repositório oficial: github.com/Linked-API/linkedin-skills

Fonte: <https://github.com/Linked-API/linkedin-skills>

## AI YouTube Shorts Generator

Automação completa para converter ideias e materiais em vídeos verticais prontos para publicação. Voltado a quem quer transformar ideias em Shorts sem montar o vídeo manualmente.

Para detalhes de instalação, requisitos e exemplos de uso, consulte o repositório oficial.

- Foco: conversão de ideias e materiais em vídeos verticais prontos para publicar.
- Como começar: acesse o repositório oficial e siga o README para instalação e requisitos.
- Repositório oficial: github.com/Anil-matcha/AI-Youtube-Shorts-Generator

Fonte: <https://github.com/Anil-matcha/AI-Youtube-Shorts-Generator>

## Cuidados

Antes de instalar ou confiar em qualquer projeto, verifique licença, requisitos e instruções no README oficial.

- Open Chat Cut: licença AGPL; projeto independente, não afiliado ao ChatCut comercial; local-first, chaves de API no servidor. Verifique se sua máquina suporta o stack (Electron/Remotion) antes de instalar.
- Anysub: exige Linux x86-64 com Docker e Docker Compose; GPUs AMD e Intel ainda não são suportadas; a transcrição em CPU é mais lenta; Whishper 3 não é mais mantido e o Anysub não lê seus dados; recursos ainda não prontos incluem rótulos de falante, pastas monitoradas, importação por URL ou arquivo de legenda, mais de uma conta, workers em outras máquinas e imagens ARM.
- AI Video Transcriber: exige Python 3.8+, FFmpeg e chave de API de provedor compatível com OpenAI (na linha de comando, --no-llm dispensa a chave); use o modo de produção (python3 start.py --prod) para vídeos longos; quando a fonte não tem fala, o campo no_speech sinaliza isso.
- Open Storyline: exige Python 3.11+ e Conda; transições por IA dependem de serviços de terceiros com custo alto e resultados imprevisíveis; habilite só quando necessário; nos vídeos de demonstração, a primeira linha usa os assets open source padrão (modo restrito) e a segunda, efeitos da biblioteca do app Xiaohongshu.
- Para Easel, Auto Subs, Stickman Video Director, YouTube Automation Agent, LinkedIn Skills e AI YouTube Shorts Generator, verifique requisitos, licença e instruções de instalação no README de cada repositório antes de instalar.
- Não confunda nomes: o Anysub (antigo Whishper), em github.com/pluja/anysub, usa o modelo Whisper para transcrever; não é o repositório original do Whisper.

## Glossário

- AGPL: licença de software livre que exige que o código-fonte seja disponibilizado a quem usa o software, inclusive em rede.
- Apache 2.0: licença de software livre permissiva, permite uso comercial e modificação.
- MCP (Model Context Protocol): protocolo que permite agentes de IA se conectarem a ferramentas e dados externos.
- LLM (Large Language Model): modelo de linguagem de grande escala que gera e entende texto.
- Whisper: modelo de reconhecimento de fala (speech-to-text) usado para transcrever áudio.
- Faster-Whisper: implementação otimizada do Whisper para transcrição mais rápida.
- FFmpeg: ferramenta de linha de comando para processar áudio e vídeo.
- SRT / WebVTT / LRC: formatos de arquivo de legendas.
- FCPXML: formato de intercâmbio de projetos de edição de vídeo.
- LUT: tabela de consulta de cores usada para aplicar estilos de cor em vídeo.
- SSE (Server-Sent Events): tecnologia para enviar atualizações em tempo real do servidor para o navegador.
- Docker / Docker Compose: ferramentas para empacotar e rodar aplicações em contêineres.
- Conda: gerenciador de ambientes e pacotes para Python.
- localStorage: armazenamento no navegador, usado para guardar credenciais localmente.
- BYOK (Bring Your Own Key): modelo em que você usa sua própria chave de API.
- AIGC: conteúdo gerado por inteligência artificial.
- ASR: reconhecimento automático de fala (speech-to-text).
- Rough cut: corte grosseiro inicial de um vídeo.
- Style Skill: fluxo de edição salvo e reutilizável.

## Para onde ir depois

- Salve esta lista e consulte-a no GitHub quando for montar seu estúdio.
- Escolha o gargalo atual da sua produção (transcrição, legenda, edição, animação ou publicação) e instale uma ferramenta correspondente.
- Comece pela transcrição/legenda (Anysub ou AI Video Transcriber) se você ainda não tem texto dos seus vídeos.
- Teste uma ferramenta por vez em um projeto real antes de combinar várias.
- Combine ferramentas em pipeline: transcrever, legendar, editar e publicar.
- Verifique licenças (AGPL, Apache 2.0) antes de usar em projetos comerciais.

## Além do vídeo

- O OpenChatCut publicou comparativo próprio entre editores tradicionais, geração de vídeo em uma tacada e o próprio projeto, em tabela de capacidades.
- O repositório do OpenChatCut tem guias 'Open-source ChatCut alternative' e 'ChatCut vs OpenChatCut' no blog do projeto.
- O Anysub informa que LLMs ajudaram a escrever código e documentação, com revisão humana antes de cada entrega.
- O FireRed-OpenStoryline foi destaque no HelloGitHub.
- O FireRed-OpenStoryline tem tutorial de biblioteca de assets personalizada para desbloquear fontes, músicas e VFX de nível comercial.
- O AI Video Transcriber disponibiliza skill para Claude Code e plugin para Codex App, além de servidor MCP stdio.
