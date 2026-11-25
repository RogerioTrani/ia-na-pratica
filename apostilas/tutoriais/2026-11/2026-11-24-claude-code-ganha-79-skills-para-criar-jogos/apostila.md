# Claude Code ganha 79 skills para criar jogos

_2026-11-24 · tutorial_

O Awesome Gamedev Agent Skills reúne 79 habilidades de desenvolvimento de jogos para agentes de programação, cobrindo 12 motores. Você instala o pacote uma vez e um roteador carrega as habilidades certas para o motor e a tarefa antes de o agente escrever código. Esta apostila leva você da pasta vazia ao teste que mostra o roteador funcionando no Claude Code.

## O que você terá no fim

Ao final, o pacote de habilidades de jogos estará instalado e você verá o roteador carregar as habilidades certas no Claude Code. O Awesome Gamedev Agent Skills traz 79 habilidades de desenvolvimento de jogos para o seu agente de programação, em 12 motores, como Godot, Unity, Unreal, Phaser e three.js. É gratuito, de código aberto e passa de 8 mil estrelas no GitHub. Fonte: https://github.com/gamedev-skills/awesome-gamedev-agent-skills

Antes de começar: computador com terminal (Windows, macOS ou Linux); Claude Code instalado e conta ativa (code.claude.com/docs/en/quickstart); Node.js 22.20 ou mais novo (nodejs.org); e conexão com a internet para baixar o pacote. Fonte: https://github.com/gamedev-skills/awesome-gamedev-agent-skills/blob/main/README.md

Fonte: <https://github.com/gamedev-skills/awesome-gamedev-agent-skills/blob/main/README.md>

## Passo a passo

Siga os passos na ordem. O comando para abrir o Claude Code fica numa seção própria.

1. abra o terminal em uma pasta nova. Crie uma pasta vazia para o experimento e abra o terminal dentro dela. Resultado esperado: o terminal aberto, com o nome da pasta no caminho exibido.
2. confira a versão do Node.js. Veja se o número é 22.20 ou maior. Resultado esperado: uma versão começando com v, igual ou maior que 22.20. Se a versão for menor, instale ou atualize o Node.js em nodejs.org. Fonte: https://nodejs.org
3. instale o pacote de habilidades. O instalador universal aponta para o repositório oficial, detecta o seu agente de código e instala o roteador e as habilidades. Resultado esperado: o Claude Code conhece as habilidades de jogos. Alternativa pelo plugin do Claude Code: rode os dois comandos do bloco do README, nesta ordem.
4. abra o Claude Code na pasta. Na mesma pasta, digite o comando abaixo e aperte Enter. Resultado esperado: a tela inicial do Claude Code, pronta para receber sua mensagem.
5. descreva o jogo que você quer. Escreva em linguagem natural o tipo de jogo, onde ele roda e o que o personagem faz. Você não escolhe habilidade nenhuma: o roteador descobre o motor e a tarefa. Quanto mais claro o pedido, melhor a escolha. Resultado esperado: o roteador carrega as habilidades do motor e da tarefa.

Fonte: <https://github.com/gamedev-skills/awesome-gamedev-agent-skills/blob/main/README.md>

## Abrir o Claude Code na pasta

Na pasta do experimento, digite o comando abaixo e aperte Enter. O agente precisa começar dentro da pasta do projeto para enxergar as habilidades recém-instaladas. Se o terminal disser que o comando claude não foi encontrado, confirme a instalação do Claude Code e reabra o terminal. Fonte: https://code.claude.com/docs/en/quickstart

```
claude
```

Fonte: <https://code.claude.com/docs/en/quickstart>

## Teste de pronto

Observe a resposta do Claude Code ao seu pedido. O sinal de que funcionou é ele carregar habilidades de jogos ligadas ao motor e à tarefa antes de escrever código. Se nada for carregado, repita o passo 3, feche e abra o Claude Code de novo e refaça o pedido. Se a resposta vier genérica, refaça o pedido citando o motor, como Godot, Unity ou navegador.

- [ ] O Claude Code carrega habilidades de jogos ligadas ao motor e à tarefa antes de escrever código.
- [ ] Se nada for carregado, o passo 3 foi repetido e o pedido refeito.

Fonte: <https://github.com/gamedev-skills/awesome-gamedev-agent-skills>

## Cuidados e outras informações

O projeto cita quase 99% de acerto do roteador, número medido nos testes do próprio projeto. Use o resultado para prototipar e aprender. Para jogo de loja, valide cada linha antes de publicar, porque o número de acerto vem dos testes do próprio projeto.

O pacote tem habilidades para movimento do personagem, mecânica de plataforma e direção de arte, para que todos os desenhos do jogo sigam o mesmo estilo. Os motores incluem Unreal, Unity e Godot, além de jogos que rodam no navegador.

Fonte: <https://github.com/gamedev-skills/awesome-gamedev-agent-skills>
