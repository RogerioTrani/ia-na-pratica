# Rato epiléptico operado por IA com 18 horas de preparo

_2026-11-21 · noticia_

Um agente de IA conduziu uma cirurgia cerebral em um camundongo com modelo de epilepsia, com a meta de reduzir convulsões. O preparo levou 18 horas de código e coordenação. O agente escolheu a droga, a região do cérebro e as coordenadas, e injetou 250 nanolitros. Uma veterinária licenciada aprovava cada passo irreversível e segurava um kill switch físico.

## O experimento

Gabriel Ocana-Santero, cofundador e CEO da Exin Therapeutics, publicou no X em 28 de outubro de 2026 que um agente de IA tinha feito uma cirurgia cerebral em um camundongo na noite anterior. O animal tinha um modelo de epilepsia, e a meta era reduzir convulsões.

O preparo levou 18 horas de código e coordenação. A WIRED também cobriu o caso.

Fonte: <https://x.com/OcanaSantero/status/2115442964574908902>

## O que o agente recebeu

O agente partiu de três entradas e de uma única meta: reduzir convulsões.

- 19 vetores de terapia gênica organizados em uma planilha
- um camundongo com modelo de epilepsia
- um rig cirúrgico motorizado com câmeras

Fonte: <https://x.com/OcanaSantero/status/2115442964574908902>

## O que o agente decidiu

O agente escolheu a droga, escolheu a região cerebral e derivou as coordenadas a partir de três artigos científicos. Ninguém disse a ele o que aplicar nem onde colocar.

Na execução, ele conduziu os braços estereotáxicos até o cérebro e injetou 250 nanolitros. Durante a injeção, olhou o ponto de entrada pela câmera do rig para checar sangramento.

Fonte: <https://x.com/OcanaSantero/status/2115442964574908902>

## Camadas de segurança

A autonomia do agente tinha limites definidos antes da cirurgia.

- Aprovação humana em cada passo irreversível, dada pela veterinária licenciada
- Validadores fixos para limites, como o volume injetado
- Aprovação vinculada por hash
- Kill switch físico que corta a energia de todos os motores, segurado pela veterinária

Fonte: <https://x.com/OcanaSantero/status/2115442964574908902>

## Como cada modelo se comportou

Mais de um modelo foi testado, e as respostas variaram.

- Opus 5.5: recusou imediatamente ao detectar o contexto biológico.
- Opus 5: completou o dry run com água e papel milimetrado e parou no início da cirurgia ao vivo.
- Claude Sonnet 5: conduziu a cirurgia.

Fonte: <https://www.wired.com/story/an-ai-agent-did-brain-surgery-on-live-mouse/>

## O que o experimento mostra

Um agente tomou decisões científicas e operou hardware real. Cada passo crítico teve supervisão humana e limite físico.

## Links oficiais

- Relato original de Gabriel Ocana-Santero no X: https://x.com/OcanaSantero/status/2115442964574908902
- Reportagem da WIRED: https://www.wired.com/story/an-ai-agent-did-brain-surgery-on-live-mouse/
- Exin Therapeutics: https://exintherapeutics.com
- Anthropic: https://anthropic.com

## Além do vídeo

- O rig cirúrgico foi feito sob medida em Arduino, e a câmera e os motores foram expostos ao agente por soluções próprias.
- O agente puxava quadros da câmera quando queria e fez 32 observações na sessão.
- No raciocínio do agente, a terapia proposta aumenta a sinalização de GABA, o principal neurotransmissor inibitório do cérebro.
- A craniotomia foi feita por um cirurgião humano, porque o agente ainda não tem permissão para isso por segurança.
- O autor diz que há um momento em que o agente se recusou a deixar que ele o sobrepusesse, detalhado na thread.
