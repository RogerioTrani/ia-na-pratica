# DeepSeek lança Super-Agent que corrige bug e abre PR sozinho

_2026-11-23 · noticia_

A DeepSeek mostrou duas novidades: um agente aberto que corrige bugs a partir de um pedido no chat e um modo que transforma uma frase em aplicativo. O Super-Agent monitora o repositório e age quando alguém do time pede ou quando uma regra do time permite. Ambos ainda estão em fase inicial, o Super-Agent é protótipo de pesquisa e o DeepSeek Harness está em developer preview. O código é aberto; o modelo você paga à parte ou roda na sua própria máquina.

## O que é o Super-Agent

O Super-Agent é um agente aberto da DeepSeek que monitora o repositório do time. Ele age quando alguém do time pede no chat ou quando uma regra do time permite.

Fonte: <https://github.com/deepseek-ai/dsh-superagent-prototype>

## Bug no chat vira pull request

Um bug cai no chat do time. O agente reproduz o problema, corrige e abre o pull request sozinho. Quem reportou o erro já encontra a correção pronta para revisão; o time só precisa olhar o pull request e decidir se aceita.

Fonte: <https://github.com/deepseek-ai/dsh-superagent-prototype>

## Equipe de funcionários digitais

Um roteador distribui o trabalho entre funcionários digitais. Cada um guarda o próprio contexto. O trabalho continua com o notebook fechado.

Fonte: <https://github.com/deepseek-ai/dsh-superagent-prototype>

## Creator Mode: uma frase vira um app

No Creator Mode, você descreve a ideia em uma frase e o modo de criação monta o aplicativo. Os exemplos mostrados vão de um mural de post-its a um jogo de voxels, um editor de vídeo e um guia de viagem em 3D.

Fonte: <https://github.com/deepseek-ai/deepseek-harness>

## Plugin da comunidade: dsh-claude-design

Há um plugin da comunidade que roda o fluxo do Claude Design no DeepSeek Harness.

```
dsh plugin --profile desktop add dsh-claude-design
```

Fonte: <https://registry.npmjs.org/dsh-claude-design>

## Como testar

O Super-Agent é protótipo de pesquisa e o DeepSeek Harness está em developer preview. Vale testar com calma em projeto de experimento antes de apostar o fluxo do time nisso.

Fonte: <https://www.npmjs.com/package/@deepseek-ai/dsh>

## Custo e licença

O software é aberto e não cobra licença. O custo vem do modelo, que você paga à parte ou roda na sua própria máquina.

Fonte: <https://github.com/deepseek-ai/deepseek-harness>

## Links oficiais

- Repositório do Super-Agent: https://github.com/deepseek-ai/dsh-superagent-prototype
- Repositório do DeepSeek Harness: https://github.com/deepseek-ai/deepseek-harness
- Página oficial do DeepSeek Harness: https://www.deepseek.com/en/harness/
- Download do DeepSeek Harness: https://www.deepseek.com/en/download/
- Pacote dsh-claude-design no npm: https://www.npmjs.com/package/dsh-claude-design
- Plugin dsh-claude-design (Open Plugin Market): https://dshopen.org/plugins/dsh-claude-design
- Repositório do plugin (baoyu-design): https://github.com/JimLiu/baoyu-design
- Pacote @deepseek-ai/dsh no npm: https://www.npmjs.com/package/@deepseek-ai/dsh

## Além do vídeo

- O DeepSeek Harness está disponível para desktop, com versões para macOS (Apple silicon, macOS 13 ou posterior) e Windows, e permite trabalhar em segundo plano, editar arquivos locais e lidar com tarefas longas e complexas.
- O plugin dsh-claude-design também está no Open Plugin Market (dshopen.org) e seu código-fonte está no repositório baoyu-design.
- A página oficial do DeepSeek Harness (deepseek.com/en/harness) traz mais detalhes sobre o produto.
