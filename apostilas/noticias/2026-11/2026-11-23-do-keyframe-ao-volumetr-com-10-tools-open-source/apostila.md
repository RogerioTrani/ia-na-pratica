# Do keyframe ao volumétrico com 10 tools open-source

_2026-11-23 · noticia_

Esta apostila apresenta dez ferramentas abertas para animação, motion design, captura de movimento, partículas, web, dados volumétricos e composição. Você vai entender o papel de cada projeto, como funcionam seus recursos centrais e por onde começar. Também aprenderá a distinguir keyframes, captura sem marcadores, nós, volumes esparsos e animação por código. Ao final, conseguirá escolher uma ferramenta pela tarefa, praticar seu fluxo básico e saber o que conferir antes de instalar.

## Como usar esta lista

Esta lista reúne dez projetos de código aberto que cobrem etapas diferentes da produção visual: desenho e animação 2D, captura de movimento, partículas, animação na web, dados volumétricos e composição. Ela serve para quem quer conhecer opções de software aberto e escolher a ferramenta pelo resultado que precisa produzir.

O ponto em comum é o software aberto, que amplia as opções disponíveis. As finalidades são distintas. Um editor de poses, uma biblioteca de volumes e um compositor de nós resolvem problemas diferentes, então a leitura pode começar pela categoria da sua cena.

1. Comece definindo o resultado da cena: animar elementos 2D, capturar movimento, criar partículas, animar a web, trabalhar com volumes ou compor imagens. O resultado indica a seção adequada.
2. Para motion 2D, compare Friction, Synfig Studio, OpenToonz e Pencil2D. Para web, compare Theatre.js e SVG.js. A comparação ajuda a escolher pelo formato de trabalho.
3. Abra o site ou repositório oficial indicado na seção escolhida e leia a licença e os requisitos antes de instalar. Esse cuidado mantém a decisão dentro das condições do projeto.
4. Pratique a operação central da ferramenta: poses-chave no Synfig Studio, captura e calibração no FreeMoCap, prévia de partículas no Effekseer ou conexão de nós no Natron. O exercício mostra se o modelo de trabalho atende à sua tarefa.

## Friction

Friction é um editor de motion graphics 2D em código aberto. Reúne vetores e imagens rasterizadas no mesmo ambiente e usa keyframes para registrar mudanças ao longo do tempo. Isso serve para animar elementos gráficos com uma ferramenta aberta.

Na timeline, cada keyframe marca um estado. Entre esses estados, o programa calcula a mudança para gerar movimento. As expressões acrescentam regras para controlar a animação. Entre as propriedades estão posição, escala, rotação, preenchimento, contorno e efeitos.

A exportação em SVG animado leva a animação para a web. O SVG descreve formas e movimento em um formato que o navegador pode apresentar. Para quem desenha e também publica na web, a vantagem é usar o trabalho gráfico como base da animação.

- Tecnologia: vetores, imagens, keyframes, expressões e exportação em SVG animado.
- Para começar: monte uma cena com os elementos gráficos, defina keyframes na timeline e use expressões para controlar o movimento.
- Organização: cena, camadas, timeline e propriedades de posição, escala, rotação, aparência e efeitos.
- Resultado esperado: um SVG animado para levar o resultado à web.

Fonte: <https://github.com/friction2d/friction>

## FreeMoCap

FreeMoCap é captura de movimento 3D sem marcadores. Ele usa imagens de câmeras para acompanhar o movimento e reconstruir a informação em três dimensões, sem prender marcadores ao corpo. O processo não exige roupas especiais.

A captura usa duas ou mais câmeras. Antes de processar as imagens, é preciso calibrar a captura, etapa que ajusta a relação entre as câmeras e o espaço registrado. Depois vêm o processamento e a exportação. O projeto destaca captura sincronizada, processamento local e dados descritos como de nível de pesquisa.

O fluxo termina com a exportação, que pode ir para o Blender ou para os formatos CSV e FBX. Isso permite levar o movimento reconstruído para um ambiente de animação 3D. A calibração faz parte do método e define a base usada na reconstrução.

- Tecnologia: captura sem marcadores, múltiplas câmeras, calibração, reconstrução 3D e exportação.
- Para começar: disponha duas ou mais câmeras, faça a captura, calibre, processe e exporte o resultado.
- Formatos: CSV, FBX e exportação para o Blender.
- Requisito destacado: duas ou mais câmeras; no exemplo ilustrado, a captura é sincronizada.

Fonte: <https://github.com/freemocap/freemocap>

## Effekseer

Effekseer é uma ferramenta em código aberto para criar efeitos de partículas em 2D e 3D. Partículas são elementos visuais individuais usados em conjunto para compor um efeito. A ferramenta organiza a criação em uma árvore de efeitos e oferece prévia em tempo real.

A prévia em tempo real deixa o resultado visível durante a edição. Os parâmetros controlam a criação e o comportamento do efeito. Há partículas, fitas e anéis, além de texturas, materiais, modelos, emissor e sprite sheets. A combinação desses recursos permite construir o efeito antes de levá-lo ao projeto final.

O Effekseer se integra com Unity e Unreal por meio de runtimes. Uma runtime é a parte que reproduz o efeito dentro do ambiente de destino. A ferramenta também é descrita como multiplataforma, e a mesclagem aditiva aparece como uma opção para combinar cores.

- Tecnologia: efeitos 2D e 3D, prévia em tempo real, árvore de efeitos e parâmetros.
- Recursos: partículas, fitas, anéis, texturas, mesclagem aditiva, materiais, modelos, emissor e sprite sheets.
- Para começar: crie o efeito na árvore, ajuste os parâmetros e acompanhe a prévia em tempo real.
- Integrações: Unity e Unreal.

Fonte: <https://github.com/effekseer/Effekseer>

## Theatre.js

Theatre.js é uma ferramenta de motion design para a web com edição visual. Traz timeline e editor de curvas para ajustar movimento de interfaces e cenas. O Theatre.js Studio reúne cena, editor e compartilhamento, além de controles como opacidade e câmera.

Uma timeline organiza os eventos no tempo. O editor de curvas permite refinar a passagem entre valores. A opção Ease In Out indica uma interpolação que começa e termina mais suavemente, ajudando a ajustar o ritmo do movimento. A timeline marca o tempo no formato 0:00.000, usado para posicionar eventos.

A biblioteca trabalha com Three.js e com elementos HTML e SVG. Three.js é usado para cenas 3D no navegador. HTML e SVG permitem animar elementos da interface e gráficos vetoriais. A escolha do objeto depende do que a cena precisa mostrar.

- Tecnologia: timeline, editor de curvas, easing, Three.js, HTML e SVG.
- Para começar: organize a cena, coloque os objetos na timeline e refine as curvas de movimento.
- Controles: opacidade, câmera, sequência, detalhes e estrutura da cena.
- Resultado esperado: movimento visualmente ajustável em uma cena Three.js, HTML ou SVG.

Fonte: <https://github.com/theatre-js/theatre>

## OpenToonz

OpenToonz é um estúdio de animação 2D em código aberto. Seus destaques são animação quadro a quadro, Xsheet e ferramentas de desenho. Há também digitalização e limpeza de desenhos, além de espaços de trabalho personalizáveis.

O Xsheet organiza os quadros e as células de animação. Ele ajuda a acompanhar a sequência de imagens e o tempo de cada uma. A paleta e a tira de níveis organizam cores e desenhos, enquanto as ferramentas de desenho atendem à produção quadro a quadro.

Essa estrutura serve para quem quer controlar cada desenho da sequência. A digitalização e a limpeza entram quando um desenho de origem precisa passar para o ambiente de animação. Os espaços de trabalho personalizáveis permitem reorganizar as ferramentas conforme a tarefa.

- Tecnologia: animação quadro a quadro, Xsheet, ferramentas de desenho, digitalização e limpeza.
- Para começar: desenhe os quadros, organize a sequência no Xsheet e acompanhe as células na linha do tempo.
- Recursos: paleta, tira de níveis, áreas de desenho e espaços de trabalho personalizáveis.

Fonte: <https://github.com/opentoonz/opentoonz>

## OpenVDB

OpenVDB é uma biblioteca em C++ para armazenar e manipular volumes esparsos em grades 3D. Foi criada originalmente pela DreamWorks Animation. Um volume esparso dedica estrutura às regiões com dados, uma abordagem usada em pipelines de efeitos visuais.

Voxel é uma célula de uma grade 3D. Um fluxo volumétrico pode incluir operações como voxelizar, gerar volume de neblina, filtrar e construir level sets. Um level set descreve uma superfície por valores de distância. Um volume de neblina ocupa uma região do espaço. Essas operações preparam dados que outros programas do pipeline podem consumir.

NanoVDB é a variante para GPU. A GPU executa muitas operações de cálculo em paralelo e pode acelerar o processamento de dados volumétricos. OpenVDB organiza os volumes no pipeline. NanoVDB trata da representação e do processamento voltados à GPU.

- Tecnologia: C++, volumes esparsos, grades 3D, voxels e NanoVDB para GPU.
- Operações: voxelização, volume de neblina, filtros e level sets.
- Para começar: identifique o dado volumétrico e a operação necessária no pipeline de efeitos visuais.
- Uso descrito: base para armazenar e manipular dados volumétricos em pipelines de VFX.

Fonte: <https://github.com/AcademySoftwareFoundation/openvdb>

## Natron

Natron é um compositor de efeitos visuais em código aberto baseado em nós. Cada nó realiza uma operação de imagem e as conexões definem por onde o resultado passa. Ele oferece mais de cem nós, plugins OpenFX, rotoscopia, rastreamento e script em Python.

Compor imagens significa combinar camadas e tratamentos para formar o resultado final. A árvore de nós torna esse percurso visível. Leitura, correção de cor, máscara, desfoque, rastreamento e escrita podem aparecer como etapas conectadas. Há também editor de curvas e dopesheet.

Rotoscopia cria máscaras para isolar partes de uma imagem. Rastreamento acompanha elementos ao longo do tempo. Plugins OpenFX ampliam as operações disponíveis. A ferramenta é descrita como multiplataforma.

- Tecnologia: fluxo por nós, plugins OpenFX, rotoscopia, rastreamento e script em Python.
- Para começar: conecte as operações de imagem em nós, ajuste os parâmetros e acompanhe o resultado no visualizador.
- Operações: leitura, mesclagem, correção de cor, desfoque, chroma key, rastreamento e escrita.
- Recursos de edição: cache, editor de curvas e dopesheet.

Fonte: <https://github.com/NatronGitHub/Natron>

## Synfig Studio

Synfig Studio é um programa gratuito e de código aberto de animação 2D. Trabalha com vetores e bitmaps e usa interpolação vetorial para calcular os quadros intermediários. Você define as poses-chave e o programa preenche o movimento entre elas.

Esse método reduz a necessidade de desenhar cada quadro manualmente. O sistema de ossos oferece outro controle: organiza partes do personagem para mudar poses sem tratar cada parte isoladamente. Um personagem pode ter camadas de cabeça, cachecol, corpo e cabelo, organizadas ao lado da linha do tempo.

O programa anuncia mais de cinquenta camadas e suporte a Windows, macOS e Linux. Camadas separam elementos da cena e ajudam a editar um personagem ou objeto sem alterar o restante. A interpolação e os ossos atendem a formas diferentes de controlar a animação.

- Tecnologia: vetores, bitmaps, interpolação vetorial, quadros intermediários automáticos e rig de ossos.
- Para começar: crie as poses-chave na linha do tempo e use ossos quando o personagem precisar de articulação.
- Organização: camadas, linha do tempo e separação das partes do personagem.
- Resultado esperado: o programa calcula os quadros intermediários entre as poses-chave.

Fonte: <https://github.com/synfig/synfig>

## SVG.js

SVG.js é uma biblioteca JavaScript leve para criar e animar SVG. Seus destaques são uma API legível, controle do DOM e ausência de dependências. Ela atende a quem prefere construir o gráfico por código, com controle direto sobre os elementos SVG.

Um código de exemplo cria um retângulo e um círculo, define cores, move os elementos e anima essas mudanças. O trecho traz ainda um comando de contorno, com `.stroke(...)`. A sequência mostra o fluxo básico: criar a forma, aplicar atributos, posicionar e animar.

O DOM é a estrutura de elementos que a página apresenta ao JavaScript. Controlar o DOM permite alterar formas e atributos do SVG enquanto a página está carregada. A licença é MIT.

- Tecnologia: API de JavaScript, controle do DOM, criação de formas e animação de elementos SVG.
- Para começar: crie os elementos SVG, defina os atributos e encadeie os comandos de movimento e animação.
- Exemplo: retângulo e círculo com preenchimento e movimento, mudança de cor no retângulo e um comando de contorno.
- Condições: biblioteca leve, sem dependências e com licença MIT.

Fonte: <https://github.com/svgdotjs/svg.js>

## Pencil2D

Pencil2D é um programa de animação 2D que combina camadas de bitmap e vetor. Um destaque é o onion skin, um recurso que mostra referências dos quadros vizinhos para ajudar a comparar poses durante o desenho.

Onion skin funciona como uma sequência de referências. O desenhista vê o quadro anterior e o seguinte enquanto trabalha no atual, o que ajuda a manter a continuidade do movimento. Há também controles de contorno e câmera e camadas vetoriais.

O número de versão, como em Pencil2D v0.6.6, identifica uma edição específica do programa. O uso de bitmap e vetor permite combinar desenho em pixels com formas vetoriais no mesmo trabalho de animação 2D.

- Tecnologia: camadas de bitmap e vetor, onion skin e animação 2D.
- Para começar: ative a referência dos quadros vizinhos, desenhe as poses e organize os elementos em camadas.
- Controles: Show Outlines, Show Camera e Vector Layers.
- Exemplo de versão: Pencil2D v0.6.6.

Fonte: <https://github.com/pencil2d/pencil>

## Os números

Os números abaixo pertencem a exemplos, requisitos ou conjuntos específicos. Eles ajudam a dimensionar cada ferramenta, mas não medem a qualidade do resultado final.

- Dez ferramentas: total da seleção.
- Duas ou mais câmeras: requisito do FreeMoCap para a captura usada na reconstrução 3D. O exemplo ilustrado usa duas câmeras.
- 30 FPS no exemplo do FreeMoCap: taxa de 30 quadros por segundo da captura ilustrada. O valor não define a taxa de toda configuração.
- Mais de cem nós no Natron: quantidade de nós de operação que o programa oferece. O número não determina a qualidade da composição.
- Mais de cinquenta camadas no Synfig Studio: número de camadas anunciado pelo programa.
- 24 FPS no Natron: taxa de 24 quadros por segundo de uma tela ilustrativa. Não é uma configuração universal do projeto.
- Pencil2D v0.6.6: número que identifica uma edição específica do programa.

## Exemplo: da pose ao movimento no Synfig Studio

Imagine que um personagem precisa mudar de expressão e posição do braço. No Synfig Studio, primeiro monte as camadas para separar as partes do personagem. Depois defina a pose inicial e a pose final como poses-chave. Quando o programa calcula os intermediários, a mudança deixa de depender do desenho manual de cada quadro.

Se o movimento exigir articulação, use o sistema de ossos para controlar as partes do personagem. A linha do tempo permite ver a sequência, e as camadas mantêm cabeça, corpo e acessórios separados. O exemplo termina quando as poses-chave e os quadros intermediários representam a ação planejada.

- Ação: separar os elementos em camadas e definir as poses-chave.
- Recurso usado: interpolação vetorial para calcular os quadros intermediários.
- Alternativa de controle: rig de ossos para articular o personagem.

Fonte: <https://github.com/synfig/synfig>

## Cuidados

- Leia a licença e os requisitos no repositório oficial antes de instalar. Software aberto mantém condições de uso e instalação próprias para cada projeto.
- SVG.js tem licença MIT. A ausência de dependências indicada para ele pertence especificamente a esse projeto.
- Os 30 FPS do FreeMoCap pertencem a uma captura de exemplo. Eles não definem a taxa de toda captura.
- As integrações com Unity e Unreal pertencem ao Effekseer. A exportação para Blender pertence ao FreeMoCap. A animação de cenas Three.js e de elementos HTML e SVG é do Theatre.js. Não presuma que um projeto tenha o recurso de outro.
- OpenVDB é uma biblioteca C++ para dados volumétricos. Seu trabalho acontece como base de um pipeline de efeitos visuais.
- Use os repositórios oficiais para reconhecer a interface, as instruções e a estrutura do Natron e do SVG.js.
- Friction exporta SVG animado. SVG.js cria e anima SVG por código. Theatre.js edita movimento visualmente. As três rotas para web têm mecanismos diferentes.

## Glossário

- Motion design: criação de movimento para elementos gráficos, interfaces e cenas.
- Vetor: forma descrita por coordenadas e curvas, sem depender de uma grade de pixels.
- Bitmap e raster: imagens formadas por pixels organizados em uma grade.
- Keyframe e pose-chave: estado ou quadro que marca uma mudança importante na animação.
- Interpolação e in-between: cálculo ou desenho dos estados intermediários entre duas poses-chave.
- Expressão: regra usada para controlar valores de uma animação.
- Timeline e easing: linha do tempo que organiza eventos e curva que ajusta a passagem entre valores.
- SVG: formato de gráficos vetoriais que também pode descrever movimento.
- Captura de movimento sem marcadores: reconstrução do movimento a partir de imagens, sem marcadores fixados ao corpo.
- Calibração: ajuste que relaciona as câmeras e o espaço registrado na captura.
- Partícula e emissor: elemento visual individual de um efeito e sistema que gera essas partículas.
- Sprite sheet: imagem que reúne vários quadros ou elementos usados na animação.
- Blend aditivo: modo de mesclagem que soma as contribuições de cor dos elementos.
- Runtime: parte que reproduz um efeito dentro do ambiente de destino.
- Three.js: biblioteca usada para criar cenas 3D no navegador.
- API: conjunto de operações que uma biblioteca oferece ao código.
- DOM: estrutura de elementos de uma página que o JavaScript pode manipular.
- Nó: operação individual dentro de um fluxo de composição.
- Composição: combinação de camadas e tratamentos de imagem para formar o resultado final.
- Rotoscopia: criação de máscaras para isolar partes de uma imagem.
- Rastreamento: acompanhamento de elementos ao longo do tempo.
- OpenFX: padrão de plugins usado para ampliar operações de efeitos visuais.
- Rig de ossos: estrutura de articulações usada para controlar partes de um personagem.
- Onion skin: referência visual dos quadros vizinhos durante o desenho.
- Pipeline: sequência de etapas e ferramentas usada para produzir um resultado.
- Volume esparso: representação 3D que concentra dados nas regiões ocupadas.
- Voxel: célula de uma grade tridimensional.
- Level set: representação de uma superfície por valores de distância.
- GPU: unidade de processamento gráfico usada para executar cálculo em paralelo.
- C++: linguagem de programação usada pelo OpenVDB.

## Para onde ir depois

- Escolha o formato da primeira prática: motion 2D, captura 3D, partículas, web, volumes ou composição.
- Para animação 2D, abra Friction se quiser vetores, imagens e SVG animado. Abra Synfig Studio se quiser poses-chave e intermediários automáticos. Compare OpenToonz e Pencil2D para desenho e controle de quadros.
- Para web, use Theatre.js quando quiser timeline e curvas visuais. Use SVG.js quando quiser criar e animar SVG por JavaScript.
- Para efeitos, pratique a prévia de partículas no Effekseer ou o fluxo de nós no Natron. Para dados volumétricos, estude a estrutura de volumes esparsos do OpenVDB.
- Para captura de movimento, ensaie no FreeMoCap a sequência de captura, calibração, processamento e exportação. Use duas ou mais câmeras.
- Depois do primeiro exercício, anote qual operação ficou clara e qual requisito apareceu. Esse registro ajuda a escolher o próximo projeto da lista.

## Links citados

- https://effekseer.github.io/en/
- https://freemocap.org
- https://friction.graphics
- https://natrongithub.github.io
- https://opentoonz.github.io
- https://svgjs.dev
- https://www.openvdb.org
- https://www.pencil2d.org
- https://www.synfig.org
- https://www.theatrejs.com
