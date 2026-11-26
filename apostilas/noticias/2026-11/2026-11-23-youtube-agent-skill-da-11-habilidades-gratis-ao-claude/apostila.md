# YouTube Agent Skill dá 11 habilidades grátis ao Claude

_2026-11-23 · noticia_

Um pacote de código aberto chamado YouTube Agent Skill reúne onze habilidades para o Claude que assumem parte do trabalho de produção de um canal do YouTube, da escrita de roteiros à análise de retenção. É gratuito, tem licença MIT e não pede cadastro nem chave de API. Depois de ler esta apostila você saberá o que cada habilidade faz, como instalá-las no Claude Code, como preparar a voz do canal e quais limites conferir antes de confiar nos números que aparecem.

## O fato

A YouTube Agent Skill é um conjunto de onze habilidades (skills) para o Claude, publicado no GitHub por Jakeschincariol sob licença MIT. O repositório oficial é https://github.com/Jakeschincariol/youtube-agent-skill.

O pacote é gratuito, não exige cadastro nem chave de API e nada é publicado por conta própria: as habilidades escrevem, e quem envia o vídeo é você.

O projeto se apresenta como uma equipe de produção para YouTube que não cobra nada e não é feita de gente: onze habilidades assumem parte do trabalho que normalmente exigiria um time.

Fonte: <https://github.com/Jakeschincariol/youtube-agent-skill>

## Por que isso importa

Produzir um vídeo do YouTube exige roteiro, embalagem (título e thumbnail), edição, SEO, capítulos, resposta a comentários, planejamento da semana, análise de retenção, extração de Shorts e auditoria do canal. Fazer tudo isso à mão consome horas. O pacote reúne essas tarefas em comandos que rodam dentro do Claude.

O diferencial é que seis dessas tarefas têm ferramentas em Python que rodam com Python 3 puro, sem dependências, em vez de serem apenas prompts. Isso torna o resultado mais determinístico do que uma resposta de chat.

Para canais pequenos e médios, o ganho está em repetir o mesmo processo de produção sem precisar contratar.

Fonte: <https://github.com/Jakeschincariol/youtube-agent-skill>

## As onze habilidades

Cada habilidade é um comando que começa com /yt- e executa uma parte do trabalho de produção. A lista completa, com o que cada uma faz.

- /yt-script: uma ideia vira roteiro. Cinco ganchos a partir de 21 fórmulas, com nota, e depois um roteiro falado com os retention beats marcados.
- /yt-package: título e thumbnail como um par, avaliados para truncamento, duplicação e vagueness.
- /yt-edit: uma transcrição vira edit decision list: dead air, filler cues, retakes, com timecodes.
- /yt-comment: a seção de comentários triada em quatro pilhas, depois respostas na sua voz. Indica qual fixar.
- /yt-plan: uma semana que cabe nas horas que você tem. Um anchor, um cheap one, três Shorts.
- /yt-viral: o que está funcionando no nicho, ordenado por múltiplo sobre a mediana do próprio canal.
- /yt-retention: o export de retenção lido direito: hook leak, cliffs, slide e o que mudar.
- /yt-shorts: os Shorts já escondidos dentro de um vídeo longo, com uma nova primeira linha para cada.
- /yt-seo: a descrição, as tags que valem a pena e as três queries que este vídeo deve vencer.
- /yt-chapters: capítulos a partir da transcrição, validados pelas regras do YouTube para renderizar.
- /yt-audit: o canal inteiro, terminando em uma correção em vez de vinte.

Fonte: <https://github.com/Jakeschincariol/youtube-agent-skill>

## Roteiro com cinco ganchos

Você entrega a ideia do vídeo e recebe um roteiro com cinco aberturas diferentes. Cada abertura ganha uma nota, então você escolhe a melhor antes de ligar a câmera.

A habilidade parte de 21 fórmulas de gancho. A nota serve para você não gastar uma gravação com um gancho fraco.

Depois dos ganchos, vem um roteiro falado com os retention beats marcados, ou seja, os pontos onde a retenção costuma cair, sinalizados para você cuidar na edição.

Fonte: <https://github.com/Jakeschincariol/youtube-agent-skill>

## Título e thumbnail como um par

Escrever título e thumbnail separados é por que metade da superfície de clique diz a mesma coisa duas vezes. A habilidade trata os dois como um único par e avalia truncamento, duplicação e vagueness.

Truncamento é o título que o YouTube corta na busca. Duplicação é thumbnail e título repetindo a mesma informação. Vagueness é promessa genérica que não diz o que o vídeo entrega.

Fonte: <https://github.com/Jakeschincariol/youtube-agent-skill>

## Edição, comentários e planejamento

/yt-edit transforma uma transcrição em edit decision list: dead air, filler cues, retakes, com timecodes. Você sabe exatamente o que cortar e onde.

/yt-comment tria a seção de comentários em quatro pilhas e depois responde na sua voz. A habilidade também diz qual comentário fixar.

/yt-plan planeja uma semana que cabe nas horas que você tem: um anchor (vídeo principal), um cheap one (vídeo barato de fazer) e três Shorts.

Fonte: <https://github.com/Jakeschincariol/youtube-agent-skill>

## Viralidade e retenção

/yt-viral vai atrás do que está funcionando no seu nicho. Ordena os vídeos pelo quanto cada um superou a mediana do próprio canal, e não pelo tamanho do canal. Assim você aproveita ideias que já deram certo, sem ser enganado por canais grandes.

Quando a habilidade diz que um título usou 'The Statistic', é um julgamento sobre o título que você vê, não uma afirmação sobre por que o vídeo ganhou views.

/yt-retention, com o relatório de retenção em mãos, mostra em que momento exato as pessoas cansaram e saíram. Exibe hook leak (vazamento no gancho), cliffs (penhascos de queda), slide (declínio gradual) e o que mudar.

Fonte: <https://github.com/Jakeschincariol/youtube-agent-skill>

## Shorts, SEO, capítulos e auditoria

/yt-shorts encontra os Shorts já escondidos dentro de um vídeo longo e escreve uma nova primeira linha para cada.

/yt-seo gera a descrição, as tags que valem a pena (o pacote deixa claro que tags pouco importam) e as três queries que este vídeo deve vencer.

/yt-chapters gera capítulos a partir da transcrição e valida contra as regras do YouTube para que renderizem.

/yt-audit audita o canal inteiro e termina em uma correção em vez de vinte.

Fonte: <https://github.com/Jakeschincariol/youtube-agent-skill>

## As seis ferramentas Python

Seis ferramentas rodam em Python 3 puro, sem dependências. São a razão pela qual as habilidades não são só prompts.

- hookscore.py: painel de 5 propriedades do gancho.
- title.py: linter de título + thumbnail.
- deadair.py: edit decision list.
- chapters.py: capítulos validados.
- retention.py: onde saíram e por quê.
- swipe.py: outliers por múltiplo do próprio canal, com --min 2.0.

```
python3 skills/yt-script/hookscore.py --hook "one line"
python3 skills/yt-package/title.py --title "..." --thumb "..."
python3 skills/yt-edit/deadair.py transcript.srt
python3 skills/yt-chapters/chapters.py transcript.srt
python3 skills/yt-retention/retention.py retention.csv
python3 skills/yt-viral/swipe.py collected.json --min 2.0
```

Fonte: <https://github.com/Jakeschincariol/youtube-agent-skill>

## Como instalar

1. No Claude Code: clone o repositório com git clone https://github.com/Jakeschincariol/youtube-agent-skill.git e copie as pastas com cp -r youtube-agent-skill/skills/yt-* ~/.claude/skills/.
2. Como plugin: rode /plugin marketplace add Jakeschincariol/youtube-agent-skill e depois /plugin install youtube-agent.
3. Dentro do Claude (sem terminal): cole https://github.com/Jakeschincariol/youtube-agent-skill e peça para instalar a skill, depois confirme que /yt-script funciona.
4. Project-local: copie as mesmas pastas para .claude/skills/ do seu repositório.
5. Sem Claude Code: cole qualquer SKILL.md no topo de um chat e ele roda como modo. Você perde as seis ferramentas Python, que é a maior parte do ponto de /yt-script, /yt-retention e /yt-edit, mas o resto funciona.

```
git clone https://github.com/Jakeschincariol/youtube-agent-skill.git
cp -r youtube-agent-skill/skills/yt-* ~/.claude/skills/
```

Fonte: <https://github.com/Jakeschincariol/youtube-agent-skill>

## A voz do canal

Gaste dez minutos em templates/voice.md. Copie para ~/.claude/youtube/voice.md e preencha, ou envie ao Claude três dos seus próprios vídeos e diga 'write my voice.md from these'. Cada skill lê esse arquivo.

Importa mais aqui do que em qualquer outro lugar, porque você tem de dizer as palavras em voz alta.

Fonte: <https://github.com/Jakeschincariol/youtube-agent-skill>

## O que o pacote não faz

- Não publica. A YouTube Data API permitiria com seu próprio OAuth, mas não está implementado. Cada skill termina em um bloco que você copia e uma pergunta: ship it, or change it? Qualquer coisa que afirme rodar seu canal sem supervisão deve ser lida com essa distinção em mente.
- hookscore.py é heurística, não preditor. O painel foi calibrado em 74 hooks reais de short-form (os primeiros 15 segundos de auto-captions, top-8 e bottom-8 por views em cinco canais). Separa bem hooks deliberadamente ruins de hooks reais; separa pouco os hits de um criador de seus próprios misses. Nota baixa é motivo para olhar de novo; nota alta não é promessa.
- O classificador de fórmula julga as palavras, não o resultado. Quando /yt-viral diz que um título usou The Statistic, é julgamento sobre o título visível, não sobre por que o vídeo ganhou views.
- /yt-viral lê, não scrapeia. Listagens públicas apenas. Nunca loga como você e nunca toca suas credenciais.
- Tags pouco importam e o pacote diz isso em vez de vender gerador de tags.
- Nada inventa número. Se uma skill quer uma figura que não tem, pede ou escreve a linha sem ela.

Fonte: <https://github.com/Jakeschincariol/youtube-agent-skill>

## Os números

- 11 habilidades no pacote.
- 21 fórmulas de gancho na habilidade de roteiro.
- 5 ganchos gerados por roteiro, cada um com nota.
- 6 ferramentas em Python 3 puro, sem dependências.
- 74 hooks reais usados para calibrar o hookscore.py.
- 5 canais e os primeiros 15 segundos de auto-captions na calibração.
- Top-8 e bottom-8 por views na calibração.

Fonte: <https://github.com/Jakeschincariol/youtube-agent-skill>

## O que muda para você

Imagine que você tem um canal pequeno e publica um vídeo por semana. Antes, você escrevia um roteiro, inventava título e thumbnail na hora, editava sem saber onde cortar, e só descobria que o público saiu no minuto dois quando o vídeo já tinha morrido.

Com o pacote, você roda /yt-script com a ideia e escolhe o melhor dos cinco ganchos antes de gravar. Roda /yt-package para casar título e thumbnail. Depois de publicar, roda /yt-retention no export e sabe o segundo exato em que o público foi embora. /yt-viral mostra o que está funcionando no seu nicho por múltiplo sobre a mediana do próprio canal, não por tamanho de canal, então você copia ideias que já provaram que dão certo.

Exemplo: se um vídeo do nicho com canal pequeno teve 3x a mediana do próprio canal, essa é a ideia que vale estudar, não o vídeo do canal grande com mais views absolutas.

Fonte: <https://github.com/Jakeschincariol/youtube-agent-skill>

## O que fazer hoje

1. Clone o repositório e instale as habilidades no Claude Code seguindo os comandos da seção Como instalar.
2. Confirme que /yt-script funciona colando a URL no Claude e pedindo para instalar.
3. Gaste dez minutos preenchendo templates/voice.md em ~/.claude/youtube/voice.md, ou envie três vídeos seus ao Claude para gerar.
4. Escolha um vídeo antigo seu e rode /yt-retention no export de retenção para ver onde o público saiu.
5. Rode /yt-viral no seu nicho com --min 2.0 para achar vídeos que bateram a mediana do próprio canal.
6. Antes do próximo vídeo, rode /yt-script na ideia e /yt-package no título e thumbnail antes de gravar.

Fonte: <https://github.com/Jakeschincariol/youtube-agent-skill>

## O que conferir

- Confira se o repositório é o oficial: https://github.com/Jakeschincariol/youtube-agent-skill. Comando ou link que não venha do domínio do projeto é suspeito.
- hookscore.py é heurística: nota baixa pede revisão do gancho, nota alta não promete resultado.
- O classificador de fórmula julga palavras do título, não a causa do desempenho.
- /yt-viral usa listagens públicas: não loga como você e não toca credenciais. Se pedir login, pare.
- Tags pouco importam: não compre gerador de tags.
- Nada é publicado por você: revise o bloco final de cada skill antes de enviar.
- Sem Claude Code, você perde as seis ferramentas Python: o resultado de /yt-script, /yt-retention e /yt-edit fica mais fraco.

Fonte: <https://github.com/Jakeschincariol/youtube-agent-skill>

## Glossário

- Skill: habilidade instalável no Claude que executa uma tarefa específica.
- Gancho: os primeiros segundos do vídeo, quando o público decide ficar ou sair.
- Retention beats: pontos de um roteiro onde a retenção costuma cair, marcados para cuidado na edição.
- Hook leak: perda de público no gancho.
- Cliff: queda brusca de retenção.
- Slide: declínio gradual de retenção.
- Mediana do canal: valor central da distribuição de views do próprio canal, usado como régua.
- Múltiplo: quantas vezes um vídeo superou a mediana do próprio canal.
- Edit decision list: lista de cortes e ajustes com timecodes.
- Dead air: silêncio ou pausa inútil na gravação.
- Filler cues: muletas de fala (é, tipo, então).
- Retake: nova tomada de uma mesma fala.
- Thumbnail: miniatura do vídeo.
- Truncamento: corte do título pelo YouTube na busca.
- Vagueness: promessa genérica sem dizer o que o vídeo entrega.
- Anchor: vídeo principal da semana.
- Cheap one: vídeo barato e rápido de produzir.
- Shorts: vídeos curtos do YouTube.
- SEO: otimização para busca.
- Capítulos: marcadores de tempo que viram seções clicáveis.
- Auditoria: revisão completa do canal.
- voice.md: arquivo com a voz do criador, lido por todas as skills.
- Heurística: regra prática que aproxima, não garante.

Fonte: <https://github.com/Jakeschincariol/youtube-agent-skill>

## Para onde ir depois

- Salvar este vídeo e a apostila para consultar antes de cada produção.
- Instalar o pacote e preencher voice.md.
- Rodar /yt-audit no canal para descobrir a única correção que mais importa agora.
- Acompanhar o repositório oficial para atualizações: https://github.com/Jakeschincariol/youtube-agent-skill
- Praticar: gerar roteiro com /yt-script para a próxima ideia e comparar os cinco ganchos.

Fonte: <https://github.com/Jakeschincariol/youtube-agent-skill>

## Links citados

- https://raw.githubusercontent.com/Jakeschincariol/youtube-agent-skill/main/README.md

## Além do vídeo

- Os seis comandos Python e o que cada um faz.
- A opção de instalar como plugin do Claude Code.
- A opção project-local em .claude/skills/.
- Rodar sem Claude Code colando um SKILL.md no chat.
- O arquivo templates/voice.md e como preenchê-lo.
- A regra de que nada é publicado até você enviar.
- hookscore.py como heurística, não preditor, e sua calibração em 74 hooks.
- O classificador de fórmula julga palavras, não resultado.
- /yt-viral lê listagens públicas e não toca credenciais.
- Tags pouco importam.
- Nada inventa número.
- Os detalhes de /yt-comment, /yt-plan, /yt-shorts, /yt-seo, /yt-chapters e /yt-audit.
