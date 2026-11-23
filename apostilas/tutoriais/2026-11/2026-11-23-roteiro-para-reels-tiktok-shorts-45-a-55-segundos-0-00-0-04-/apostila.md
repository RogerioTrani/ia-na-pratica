# Roteiro para Reels / TikTok / Shorts — 45 a 55 segundos
[0:00 - 0:04] Gancho (Energia máxima + corte rápido na tela do terminal)
• Fala: "Seu Claude Code acabou de ganhar um estúdio de games inteiro no bolso! Olha isso aqui!"
• Texto na tela: 🎮 79 SKILLS DE GAMES NO CLAUDE CODE
[0:04 - 0:16] O Hype (Mostrando o repositório e as categorias de skills)
• Fala: "O projeto Awesome Gamedev Agent Skills já bateu mais de 8 mil estrelas no GitHub e entrega 79 habilidades prontas pra criar jogos do zero! Tem skill de física, shader, inteligência artificial de inimigos, design de fases e otimização. Em vez de quebrar a cabeça com prompt solto, você transforma o agente num time inteiro de desenvolvimento!"
• Texto na tela: ⭐ +8.000 estrelas | Física, Shaders, IA e Level Design
[0:16 - 0:30] A Virada / O Alerta (Tom firme, direto para a câmera)
• Fala: "Mas calma lá! Antes de sair jogando seu projeto comercial nisso, olha o detalhe que quase ninguém te conta: o repositório promete quase 99% de acerto, só que essa nota foi medida pelo próprio autor, sem auditoria externa. E no material oficial ainda não tem nenhum jogo real publicado em produção."
• Texto na tela: ⚠️ 99% de acerto = teste interno | Zero casos em produção
[0:30 - 0:45] Conclusão e Chamada para Ação (Empolgado, mas estratégico)
• Fala: "Ou seja: pra prototipar rápido, testar mecânica nova e aprender arquitetura de jogos, essa ferramenta é absurda! Mas pra colocar jogo na loja, valide cada linha e cobre evidência real antes de confiar no hype. Já salva esse vídeo pra testar e me diz nos comentários qual jogo você criaria primeiro!"
• Texto na tela: 🚀 Use pra prototipar | Valide antes de publicar!

_2026-11-23 · tutorial_

O Awesome Gamedev Agent Skills reúne 79 habilidades de desenvolvimento de jogos para agentes de programação, cobrindo 12 motores. Você instala o pacote uma vez e um roteador carrega as habilidades certas para o motor e a tarefa antes de o agente escrever código. Esta apostila leva você da pasta vazia ao teste que mostra o roteador funcionando no Claude Code. Use para prototipar, testar mecânicas e aprender arquitetura de jogos. Para publicar em loja, valide tudo por conta própria.

## O que é o pacote

O Awesome Gamedev Agent Skills traz 79 habilidades de desenvolvimento de jogos para o seu agente de programação, em 12 motores, como Godot, Unity, Unreal, Phaser e three.js. É gratuito, de código aberto e passa de 8 mil estrelas no GitHub.

Você descreve o jogo que quer fazer. Um roteador descobre o motor e a tarefa e carrega as habilidades certas antes de o agente escrever código. O projeto cita quase 99% de acerto do roteador, número medido nos testes do próprio projeto.

Fonte: <https://github.com/gamedev-skills/awesome-gamedev-agent-skills>

## O que você precisa antes de começar

- Computador com terminal (Windows, macOS ou Linux)
- Claude Code instalado e conta ativa (code.claude.com/docs/en/quickstart)
- Node.js 22.20 ou mais novo (nodejs.org)
- Conexão com a internet para baixar o pacote

Fonte: <https://github.com/gamedev-skills/awesome-gamedev-agent-skills/blob/main/README.md>

## Passo 1: abra o terminal em uma pasta nova

Crie uma pasta vazia para o experimento e abra o terminal dentro dela. Assim as habilidades e o jogo gerado ficam juntos. Antes de rodar o claude, o terminal precisa estar na pasta do projeto.

- Resultado esperado: o terminal aberto, com o nome da pasta no caminho exibido.
- Se o terminal abrir em outro lugar, navegue até a pasta certa antes de seguir.

Fonte: <https://code.claude.com/docs/en/quickstart>

## Passo 2: confira a versão do Node.js

Rode o comando abaixo e veja se o número é 22.20 ou maior.

- Resultado esperado: uma versão começando com v, igual ou maior que 22.20.
- Se a versão for menor ou o comando não for encontrado, instale ou atualize o Node.js em nodejs.org, reabra o terminal e repita.

Fonte: <https://nodejs.org>

## Passo 3: instale o pacote de habilidades

O instalador universal aponta para o repositório oficial, detecta o seu agente de código e instala o roteador e as habilidades. Sem este passo, o Claude Code não conhece nenhuma habilidade de jogos.

- Se falhar, confira a versão do Node.js e se o nome do repositório está idêntico ao do comando.
- Alternativa pelo plugin do Claude Code: rode os dois comandos do bloco abaixo, nesta ordem.

Fonte: <https://github.com/gamedev-skills/awesome-gamedev-agent-skills/blob/main/README.md>

## Passo 4: abra o Claude Code na pasta

Na mesma pasta, digite o comando abaixo e aperte Enter. O agente precisa começar dentro da pasta do projeto para enxergar as habilidades recém-instaladas e guardar os arquivos do jogo no lugar certo.

- Resultado esperado: a tela inicial do Claude Code, pronta para receber sua mensagem.
- Se o terminal disser que o comando claude não foi encontrado, confirme a instalação do Claude Code e reabra o terminal.
- Se o Claude Code pedir login, entre com a sua conta.

```
claude
```

Fonte: <https://code.claude.com/docs/en/quickstart>

## Passo 5: descreva o jogo que você quer

Escreva em linguagem natural o tipo de jogo, onde ele roda e o que o personagem faz. Você não escolhe habilidade nenhuma: o roteador descobre o motor e a tarefa. Quanto mais claro o pedido, melhor a escolha. Exemplo de pedido:

- Se a resposta vier genérica, refaça o pedido citando o motor, como Godot, Unity ou navegador.

Fonte: <https://github.com/gamedev-skills/awesome-gamedev-agent-skills/blob/main/README.md>

## Teste: confira se o roteador carregou

Observe a resposta do Claude Code ao seu pedido. O sinal de que funcionou é ele carregar habilidades de jogos ligadas ao motor e à tarefa antes de escrever código.

Se nada for carregado, repita o passo 3, feche e abra o Claude Code de novo e refaça o pedido.

Use o resultado para prototipar e aprender. O número de acerto vem dos testes do próprio projeto, então, para jogo de loja, valide cada linha antes de publicar.

Fonte: <https://github.com/gamedev-skills/awesome-gamedev-agent-skills>

## Além do vídeo

- O pacote tem habilidades para movimento do personagem, mecânica de plataforma e direção de arte, para que todos os desenhos do jogo sigam o mesmo estilo.
- Os motores incluem Unreal, Unity e Godot, além de jogos que rodam no navegador.
