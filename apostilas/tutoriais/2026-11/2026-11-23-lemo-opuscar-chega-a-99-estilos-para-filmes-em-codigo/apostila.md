# Lemo-Opuscar chega a 99 estilos para filmes em código

_2026-11-23 · tutorial_

O Lemo-Opuscar é uma caixa de ferramentas com 99 estilos de filme feitos em código para o Claude Code: o agente escreve as imagens, a trilha e a montagem, sem modelo gerador de vídeo. Nesta apostila você aprende a instalar o Claude Code, adicionar o marketplace do projeto, instalar o plugin, configurar o esforço alto, escolher um estilo na galeria oficial e enviar o primeiro pedido. Ao fim, terá o caminho completo da instalação à conferência do vídeo final, além dos requisitos, cuidados, glossário e plano de 7 dias. O tutorial usa o estilo Neon Tubes como exemplo e pode ser repetido com qualquer um dos 99 estilos.

## O que você terá no fim

O Lemo-Opuscar é uma caixa de ferramentas de estilos de filme feitos em código para o Claude Code. São 99 estilos prontos, mais os seus próprios. Cada estilo é um prompt de estilo acompanhado de um filme demonstrativo feito inteiramente em código, sem modelo gerador de vídeo. Ao fim deste tutorial você terá instalado o Claude Code, adicionado o marketplace do projeto, instalado o plugin Lemo-Opuscar, escolhido um estilo na galeria oficial e enviado o primeiro pedido de filme. A entrega final é um arquivo .mp4 reproduzível, com imagem e som, seguindo o estilo e o tema pedidos. O caminho completo vai da instalação à conferência do vídeo.

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Como isso funciona

O Lemo-Opuscar não usa modelo gerador de vídeo nem material de estoque. O agente escreve o código das imagens, organiza a trilha sonora e faz a montagem. As imagens são páginas de canvas e WebGL renderizadas quadro a quadro. A narração é feita por texto para fala (TTS) e a música vem de bibliotecas de amostras gratuitas. Cada estilo é um prompt de estilo (STYLE.md) que descreve como o estilo se parece e soa; a história é sua.

O fluxo tem três passos: escolher um estilo na galeria, assistir à demonstração e pedir ao agente em uma frase. O estilo pode ser nomeado em inglês ou em chinês, ou pelo nome da pasta; o índice de estilos lista todos. É possível adicionar duração, narrador, fotos ou música próprias.

Os estilos estão organizados em 15 categorias, ordenadas pelo aspecto da imagem, e cada um tem uma página com o filme demonstrativo, imagens estáticas e as orientações que o agente segue. A atualização de 12 de novembro de 2026 acrescentou 33 estilos, totalizando 99, e disponibilizou a galeria em inglês e chinês, com uma página para cada estilo.

Para dirigir, o agente lê três guias: DIRECTOR.md (direção: história, som, ritmo, câmera, performance e autoverificação), TECHNIQUE.md (construção: renderização quadro a quadro, voz, música e mixagem) e styles/<estilo>/STYLE.md (o que o estilo parece e soa).

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Antes de começar

Confira os requisitos abaixo antes de instalar. Eles são a base para o tutorial funcionar.

- Acesso ao Claude Code: exige conta paga (Pro, Max, Ultra, Team, Enterprise ou Console; o plano gratuito do claude.ai não dá acesso) ou provedor de API de terceiros (Amazon Bedrock, Google Cloud Agent Platform ou Microsoft Foundry). O login é feito pelo navegador na primeira execução de claude, ou via variável de ambiente ANTHROPIC_API_KEY.
- Node 20 ou superior instalado.
- ffmpeg 7 ou superior instalado.
- Python 3.11 ou superior, ou uv como alternativa aceita pelo projeto.
- Tempo e tokens: um filme leva de 30 a 60 minutos e consome uma quantidade considerável de tokens.
- Três dos 99 estilos exigem um gerador de imagens externo: Manga Panels, Text Flash Cuts e Comic History Cartoon, marcados com ✦ na lista de estilos. Use o Codex CLI autenticado em uma conta que gere imagens, ou outra ferramenta de imagem. Sem isso, esses três não começam; os outros 96 funcionam sem gerador de imagens.
- Saída padrão: 1920×1080 a 24 fps (alguns estilos definem outro ritmo, como 30 fps). Outros tamanhos, sob pedido.
- No Windows, o uso nativo via PowerShell não tem sandboxing e usa o PowerShell como ferramenta de shell caso o Git for Windows não esteja instalado. O WSL 2 é recomendado se você precisar de isolamento ou de ferramentas Linux.
- Ubuntu 24.04 traz ffmpeg 6.1, versão antiga demais para o projeto; use um build estático.

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Passo a passo

Siga os passos na ordem. Cada um diz a ação e o resultado esperado.

1. Instale o Claude Code executando o comando de instalação do repositório oficial no PowerShell do Windows. Resultado esperado: Claude Code instalado para uso pelo terminal.
2. Adicione o marketplace do projeto executando o comando que cadastra o catálogo do Lemo-Opuscar no Claude Code. Resultado esperado: marketplace do projeto adicionado.
3. Instale o plugin Lemo-Opuscar executando o comando que identifica o pacote e o marketplace. Resultado esperado: plugin instalado e disponível para os próximos projetos.
4. Abra o Claude Code na pasta do filme, com o terminal na pasta que receberá o projeto. Resultado esperado: sessão aberta na pasta destinada ao projeto.
5. Configure o esforço alto enviando o comando dentro da sessão do Claude Code. Resultado esperado: esforço configurado como high.
6. Escolha o estilo na galeria oficial: encontre Neon Tubes na Estação 12 (Light & Lines) e assista à demonstração de 0:48. Resultado esperado: referência visual concreta para o pedido.
7. Envie o pedido do primeiro filme colando o pedido de exemplo com o estilo Neon Tubes. Resultado esperado: o agente esclarece o pedido e inicia a produção; no primeiro uso, baixa a biblioteca para ~/lemo-opuscar.
8. Confira o vídeo final abrindo o arquivo .mp4 entregue na pasta em que iniciou a sessão e reproduzindo até o fim. Resultado esperado: filme reproduzível, com imagem e som, seguindo o estilo e o tema pedidos.

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Comando — Instalar o Claude Code (Windows)

No PowerShell do Windows, execute o comando abaixo. Ele usa o instalador nativo indicado pelo repositório oficial do Claude Code e atualiza automaticamente em segundo plano. Se preferir, a alternativa via WinGet é winget install Anthropic.ClaudeCode, mas essa via não tem atualização automática: exige rodar winget upgrade Anthropic.ClaudeCode manualmente.

Após a instalação, valide com claude --version. O filme ainda não começa aqui: este passo prepara o programa que vai receber os pedidos e executar a produção.

```
irm https://claude.ai/install.ps1 | iex
```

Fonte: <https://code.claude.com/docs/en/setup>

## Comando — Instalar o uv (alternativa ao Python)

Se preferir usar o uv em vez do Python instalado diretamente, execute o comando abaixo no PowerShell. O uv é aceito pelo projeto como alternativa ao Python 3.11 ou superior.

```
winget install --id=astral-sh.uv -e
```

Fonte: <https://docs.astral.sh/uv/getting-started/installation/>

## Comando — Instalar Node, ffmpeg e Python via WinGet

O repositório oficial do Lemo-Opuscar exige apenas os requisitos mínimos (Node 20+, ffmpeg 7+ e Python 3.11+ ou uv) e não dita o instalador do Windows. Os comandos abaixo são um exemplo prático via WinGet.

```
winget install -e --id OpenJS.NodeJS.LTS
winget install -e --id Gyan.FFmpeg
winget install -e --id Python.Python.3.12
```

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Comando — Adicionar o marketplace do projeto

No terminal, execute o comando abaixo. Pense nele como o cadastro do catálogo de onde o Claude Code vai buscar o plugin. Esse cadastro precisa vir antes da instalação do plugin.

```
claude plugin marketplace add lemomo-ai/lemo-opuscar
```

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Comando — Instalar o plugin Lemo-Opuscar

Execute o comando abaixo para instalar o plugin do Lemo-Opuscar. Ele identifica tanto o pacote quanto o marketplace que acabamos de adicionar. Este passo coloca a ferramenta à disposição do Claude Code para os próximos projetos.

```
claude plugin install lemo-opuscar@lemolab
```

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Comando — Abrir o Claude Code na pasta do filme

Com o terminal na pasta que receberá o filme, execute o comando abaixo. O plugin funciona a partir de qualquer pasta, e o projeto de cada filme, do código ao vídeo pronto, fica na pasta em que você começou. Se perceber que começou na pasta errada, encerre essa tentativa antes de pedir o filme e abra a sessão na pasta desejada.

```
claude
```

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Comando — Configurar o esforço alto

Dentro da sessão do Claude Code, envie o comando abaixo. É uma recomendação expressa do Lemo-Opuscar para executar o trabalho com Claude. O projeto informa que Claude Fable, Opus e Sonnet funcionam, e alerta que outros modelos podem não reproduzir bem os estilos. Digite o comando dentro do Claude Code, não no PowerShell.

```
/effort high
```

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Escolher o estilo na galeria oficial

Abra a galeria oficial em lemomo-ai.github.io/lemo-opuscar e procure o estilo Neon Tubes, que fica na Estação 12, chamada Light & Lines. Entre na página dele e assista à demonstração, que dura 48 segundos, antes de voltar ao terminal. A página mostra o filme demonstrativo, imagens e as orientações que o agente segue.

Manter Neon Tubes neste primeiro teste faz sentido porque ele aparece no pedido de exemplo. Depois, você pode repetir o fluxo com qualquer estilo da biblioteca.

Fonte: <https://lemomo-ai.github.io/lemo-opuscar/>

## Exemplo completo

Volte ao Claude Code e envie o pedido abaixo. Ele solicita um filme no estilo Neon Tubes sobre a fazenda de café da família. A frase dá ao agente duas informações essenciais: a aparência (o estilo) e o assunto (a história).

No primeiro uso, o agente baixa guias, ferramentas e estilos para a biblioteca compartilhada em ~/lemo-opuscar. Depois, pode perguntar detalhes do tema, materiais disponíveis (voz, música ou outras mídias) e se você quer ver um storyboard. Responda a essas perguntas para a produção avançar.

```
Make a film in the Neon Tubes style about the coffee farm my family runs.
```

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Prompt pronto

O prompt mínimo nomeia o estilo e o assunto. Você pode acrescentar duração, narrador e materiais próprios, como nas variações abaixo.

- Variação com duração e narrador: Make a 45-second film in the watercolor style about the coffee farm my family runs. Warm female narrator.
- Variação com dados públicos: Make a 40-second LiDAR Survey film about the old quarry in the hills behind our town, from public laser-scan data.
- Para começar sem ideia pronta: digite /lemo-opuscar:lemo-opuscar e nada mais. O agente pergunta o idioma e o que você quer fazer (filme em estilo da biblioteca, criar seu próprio estilo, ou filme em estilo salvo).

```
Make a film in the Neon Tubes style about the coffee farm my family runs.
```

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Teste de pronto

Use a lista abaixo para conferir a entrega. Cada item é verificável.

- [ ] Abra o arquivo .mp4 entregue na pasta em que você iniciou a sessão e reproduza até o fim.
- [ ] Confira se há imagem na tela durante toda a reprodução.
- [ ] Confira se o som toca (narração e/ou música).
- [ ] Confira se o assunto corresponde ao pedido (fazenda de café da família).
- [ ] Compare a aparência com a demonstração de Neon Tubes na galeria.
- [ ] Verifique os arquivos entregues ao lado do vídeo: poster.jpg e, se houver narração, diálogo ou legendas, o arquivo .srt; além de TREATMENT.md, CREDITS e o código-fonte com build.sh de um comando.
- [ ] Se só aparecerem os planos do storyboard, volte à conversa: essa etapa prevê uma pausa antes da produção final.
- [ ] Se houver defeito no vídeo entregue, descreva ao agente o problema observado e peça a correção.

Fonte: <https://github.com/lemomo-ai/lemo-opuscar/blob/main/DIRECTOR.md>

## Erros comuns e cuidados

Atenção aos pontos abaixo antes e durante a produção.

- Se a instalação do Claude Code não concluir, confira se copiou o comando inteiro e consulte as instruções de instalação vinculadas no repositório antes de avançar.
- Se o marketplace não for adicionado, confira o endereço do projeto exibido e volte às instruções oficiais; o comando de instalação do plugin depende desse catálogo.
- Se a instalação do plugin não terminar, confira se a etapa anterior foi concluída e compare o comando com o texto exibido. O projeto orienta abrir uma issue se algum passo continuar travado após essas verificações.
- Se a sessão do Claude Code não abrir, volte à instalação do programa antes de continuar.
- Digite /effort high dentro do Claude Code, não no PowerShell. Se o esforço não ficar como high, confira onde digitou.
- Outros modelos podem não reproduzir bem os estilos; use Claude Fable, Opus ou Sonnet, conforme a recomendação do projeto.
- No Windows, o uso nativo via PowerShell não tem sandboxing. Se precisar de isolamento ou de ferramentas Linux, use o WSL 2.
- Ubuntu 24.04 traz ffmpeg 6.1, versão antiga demais; use um build estático.
- Três estilos exigem gerador de imagens externo (Manga Panels, Text Flash Cuts, Comic History Cartoon). Sem ele, esses três não começam.
- O plano gratuito do claude.ai não dá acesso ao Claude Code.
- Fique atento às licenças: filmes feitos com a biblioteca são seus, inclusive comerciais, sem necessidade de crédito. O código é MIT e a documentação é CC BY-NC 4.0. Seis faixas de narração não são CC BY 4.0 (Chalkboard, Circuit Board, Tabletop App Flythrough, Isometric People Scene e Scratchboard Long Take via Microsoft Edge TTS; Broadcast News Package via Doubao TTS): não extraia nem reutilize essas narrações. Em seus próprios filmes, use o Kokoro (padrão) ou uma voz com direito de uso.
- Se escolheu storyboard, o agente faz uma pausa para mostrar os planos; essa prévia ainda não é o filme final.

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Estilos: 99 opções em 15 categorias

Os estilos são ordenados pelo aspecto da imagem. Uma estação abre a estação no site; um cartão ou um nome abre a página do estilo, com o filme, as imagens estáticas e a frase para copiar. Três estilos (Manga Panels, Text Flash Cuts e Comic History Cartoon) exigem gerador de imagens externo.

- 01 Edit & Documentary: Caption News, 1920s Newsreel, Live Countdown Split-screen, City Symphony, Visual Investigation, Constructivist Montage, Sports Telestrator, Broadcast News Package.
- 02 Painting & Illustration: Crayon Picture Book, Watercolor Brush, Impasto Oil Painting, Urban Sketch, Pen & Wash, Colored-Pencil Science Illustration.
- 03 Sketch & Board: One-line Drawing, Whiteboard Explainer, Chalkboard, Sketchnote, Stick-figure Explainer, Tablet Sketch Explainer, Marker on Paper.
- 04 Traditional Crafts: Chinese Ink Wash, Shadow Puppetry, Ukiyo-e, Red Paper-cut, Paper-cut Lightbox, Stained Glass, Gilded Illumination.
- 05 Print & Printmaking: Risograph Print, Halftone Dossier, Woodcut Print, Copperplate Engraving, Silkscreen Travel Poster, Scratchboard Long Take, Pop Art, Vintage Engraving Collage.
- 06 Graphic & Type: Swiss Motion Graphics, 60s Spy Title Sequence, Art Deco, Pictogram Motion, Bauhaus Shapes, Scale Zoom Explainer, Text Flash Cuts, Silhouette Rhythm.
- 07 Line Diagrams: Blueprint, Isometric Infographic, Exploded Teardown, Line-Art Cutaway, Color-Coded Mechanism, Instruction Manual Art, Pen Plotter, Assembly-Line Diagram.
- 08 Cartoons: 1930s Rubber Hose Cartoon, 80s Cel Anime, Sci-Fi Sitcom Toon, Mid-century Cartoon, Comic History Cartoon, Manga Panels.
- 09 Games: 16-bit Pixel RPG, 2.5D Pixel Art, Microgame Frenzy, Rhythm Game Show.
- 10 Film & Tape: CRT ASCII Terminal, 1920s Silent Film, Liminal Found Footage, Scratch Film, Double Exposure.
- 11 Screens & Interfaces: Dark Tech Keynote, Mascot Screencast, Sci-fi Hologram HUD, Tabletop App Flythrough, Spreadsheet Film, 1-bit Dither.
- 12 Light & Lines: Circuit Board, Firefly Pointillism, Flow-field Wind Lines, Oscilloscope Math, Neon Tubes.
- 13 3D & Miniature: Brick Toy, Paper Pop-up Book, Tilt-Shift Miniature, Low-poly Isometric Island, Glass Product Render, Memphis Diorama (por @EianLu), Isometric People Scene, Crayon World 3D (por @2nd1st).
- 14 Instruments & Evidence: Satellite Briefing, Engineering Briefing Board, LiDAR Survey, Under the Microscope, Archive Light Table, Security X-ray, Radar Sweep Documentary, Thermal Camera.
- 15 Data & Maps: Data Storytelling, Projection-Mapped Model, Data Physicalization, Transit Map, 3D Map Explainer, Blob Simulation.

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Criar seu próprio estilo

Você pode mudar um estilo da biblioteca para que seja só seu (cores da marca, logo, personagens, tom do canal) ou criar um do zero que a biblioteca não tem. É o mesmo processo usado para adicionar um estilo novo à biblioteca.

Duas formas de começar: depois de iniciar a skill, escolha a opção; ou diga em uma linha: 'I want to change the Ukiyo-e style into my own version.' ou 'Start from a blank page: a chalk-on-blackboard style, warm and slow.'

Para mudar um estilo da biblioteca, o agente lista todos os estilos com o link da galeria e você digita o que quer mudar. A partir de uma página em branco, descreva a aparência com suas palavras ou compartilhe uma imagem ou filme; o Claude escolhe o estilo da biblioteca mais próximo como base técnica, explica o porquê e você concorda ou escolhe outro.

Cinco passos: (1) planejar uma pergunta por vez (para que serve, plataforma, cores da marca, logo, fontes, personagens recorrentes, o que mudar e em qual direção, e por fim um nome); um estilo da biblioteca é classificado em seguro de mudar (paleta, tipo, ritmo, som, movimentos assinatura), muda o caráter (materiais e renderização, lógica de cor, gramática de câmera) e não pode mudar (a essência do estilo); (2) revisar o resumo (antes, depois e custo de cada parte, nada escrito sem sua concordância); (3) ver um quadro de estilo primeiro, desenhado com código real, com original à esquerda e o seu à direita quando mudou um estilo da biblioteca; (4) um filme demonstrativo de 15 a 30 segundos, com todas as mudanças na tela, música e efeitos sonoros; (5) guardar quando estiver satisfeito.

Um estilo guardado fica em ~/lemo-my-styles/<nome>/, com a mesma forma de um estilo da biblioteca (prompt de estilo, o que mudou, filme demonstrativo e código-fonte), para reutilizar as técnicas depois. Nomeie como qualquer outro estilo: 'Make a 30-second film in my Night Ukiyo-e style about…'. Seus estilos aparecem primeiro na lista. Atualizações e reinstalações da biblioteca não tocam neles.

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Atualizar ou remover

Comandos para manter ou desinstalar o plugin.

- Para atualizar, execute claude plugin marketplace update lemolab && claude plugin update lemo-opuscar@lemolab e reinicie o Claude Code. A biblioteca em ~/lemo-opuscar se atualiza sozinha no próximo filme.
- Para atualizar automaticamente: no Claude Code, digite /plugin, abra Marketplaces, escolha lemolab e ative Enable auto-update (marketplaces de terceiros como lemolab não atualizam sozinhos até você ligar isso).
- Se instalou por clone: git pull, depois rode sh plugin/skills/lemo-opuscar/scripts/setup.sh deps uma vez (atualiza só os pacotes centrais que mudaram; se instalou pacotes de voz ou música, rode … deps voice music).
- Para desinstalar: claude plugin uninstall lemo-opuscar@lemolab e depois apague ~/lemo-opuscar. Seus estilos em ~/lemo-my-styles/ permanecem; apague essa pasta você mesmo se não quiser mais.
- Se um passo continuar travado, abra uma issue no repositório.

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Glossário

- Lemo-Opuscar: caixa de ferramentas de estilos de filme feitos em código para o Claude Code, com 99 estilos prontos e a possibilidade de criar os seus.
- Claude Code: ferramenta de programação agêntica que roda no terminal, entende a base de código e executa tarefas por comandos em linguagem natural.
- Plugin: pacote instalado no Claude Code que adiciona capacidades; aqui, o lemo-opuscar@lemolab.
- Marketplace: catálogo de onde o Claude Code busca e instala plugins.
- Skill: instrução que o agente segue; o Lemo-Opuscar é distribuído como skill e plugin.
- Estilo (STYLE.md): arquivo que descreve como um estilo se parece e soa; a história é do usuário.
- DIRECTOR.md: guia de direção (história, som, ritmo, câmera, performance, autoverificação).
- TECHNIQUE.md: guia de construção (renderização quadro a quadro, voz, música, mixagem).
- Storyboard: prévia com os planos principais no estilo real; o agente faz uma pausa antes da produção final.
- TTS (text-to-speech): narração gerada a partir de texto; o padrão do projeto é o Kokoro.
- Kokoro: motor de voz padrão do projeto, usado na narração dos filmes.
- Canvas e WebGL: tecnologias de desenho no navegador usadas para renderizar as imagens quadro a quadro.
- ffmpeg: programa que processa e converte áudio e vídeo; requisito mínimo versão 7.
- uv: gerenciador e instalador de Python, alternativa aceita pelo projeto ao Python 3.11+.
- Node: ambiente de execução JavaScript; requisito mínimo versão 20.
- LUFS: medida de volume percebido; a entrega padrão fica em torno de −14 LUFS.
- lemo-my-styles: pasta ~/lemo-my-styles/ onde ficam os estilos próprios guardados.

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Plano de 7 dias

- Dia 1: instale o Claude Code no PowerShell e valide com claude --version.
- Dia 2: adicione o marketplace do Lemo-Opuscar e instale o plugin lemo-opuscar@lemolab.
- Dia 3: instale Node 20+, ffmpeg 7+ e Python 3.11+ (ou uv) e confira as versões.
- Dia 4: abra o Claude Code na pasta do projeto e configure /effort high.
- Dia 5: explore a galeria oficial e assista à demonstração de Neon Tubes (0:48).
- Dia 6: envie o pedido de exemplo e responda às perguntas do agente sobre tema e materiais.
- Dia 7: confira o .mp4 entregue, compare com a demonstração e anote os ajustes para o próximo filme.

## Para onde ir depois

- Repita o fluxo com um tema seu, mantendo um estilo que você já assistiu na galeria.
- Use o comando /lemo-opuscar:lemo-opuscar para o fluxo interativo quando não tiver ideia pronta.
- Experimente adicionar duração, narrador e materiais próprios (voz, música, fotos) ao pedido.
- Explore os 99 estilos das 15 categorias e compare o resultado com as demonstrações.
- Crie seu próprio estilo a partir de um estilo da biblioteca ou de uma página em branco.
- Consulte o OPUSCAR 98, que redesenha os 98 vencedores do Oscar de Melhor Filme em estilos da biblioteca, com frames e prompts reutilizáveis.
- Acompanhe as atualizações do projeto pelo repositório oficial e ative o auto-update do marketplace se quiser.

Fonte: <https://github.com/lemomo-ai/lemo-opuscar>

## Comandos e blocos para copiar

```
claude plugin marketplace add lemomo-ai/lemo-opuscar
claude plugin install lemo-opuscar@lemolab
```

## Links citados

- https://github.com/anthropics/claude-code
- https://github.com/lemomo-ai/lemo-opuscar/issues

## Além do vídeo

- Em 26 de novembro de 2026, o projeto publicou o Twenty Thousand Dominoes, filme de agradecimento pelas 20.000 estrelas no GitHub, com um dominó para cada estrela, construído em Blender a partir de Python.
- O mesmo criador mantém o lemo-wake (um loop de cerca de 5 segundos a partir de uma imagem), o lemo-mod (nova aparência para o Claude Code com 21 estilos) e o Stampy (carimbo na barra de menus do Mac para marcar cópias).
- Na versão 2.0.0, a biblioteca de estilos foi atualizada com Claude Fable 5.2 e a documentação atualizada passou a CC BY-NC 4.0; versões publicadas antes e os forks feitos a partir delas mantêm a licença com que saíram.
- O arquivo LICENSE diz qual licença vale para cada arquivo, os textos completos estão em LICENSES/ e o REUSE.toml traz as mesmas regras arquivo por arquivo.
