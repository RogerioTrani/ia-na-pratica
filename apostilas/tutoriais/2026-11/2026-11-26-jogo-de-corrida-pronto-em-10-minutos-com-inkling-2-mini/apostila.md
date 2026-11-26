# Jogo de corrida pronto em 10 minutos com Inkling 2 Mini

_2026-11-26 · tutorial_

Este tutorial mostra como rodar o Inkling 2 Mini no seu próprio computador, pelo Unsloth Studio, e ligá-lo ao agente de código Pi. No fim, você terá um jogo de corrida no estilo Subway Surfers, que abre no navegador e foi gerado por um prompt. No nosso teste, esse processo levou cerca de 10 minutos.

## O que você terá no fim

Ao final, você terá o Unsloth Studio instalado e o Inkling 2 Mini carregado no seu computador. Você também terá o Pi ligado ao modelo e um jogo de corrida infinita em HTML, CSS e JavaScript, que abre no navegador.

O jogo tem obstáculos, moedas e efeitos visuais. Se algo não funcionar como você quer, um novo pedido ao Pi corrige. Tudo roda no seu computador, sem pagar por um serviço na internet.

## Antes de começar

- Placa de vídeo NVIDIA. Ela ajuda bastante. No nosso teste, usamos uma placa com 24 GB de VRAM, a memória da placa.
- Versão de 4 bits do modelo, que cabe numa placa de 24 GB. Com uma placa menor, dá para usar uma versão menor do modelo, ou a memória RAM do sistema, conforme a versão escolhida.
- Terminal bash, para rodar os comandos.
- Navegador, para abrir o Studio e o jogo.
- Internet, para baixar o modelo. O tempo do download depende da sua conexão.
- Espaço livre no disco. Modelos de IA ocupam bastante espaço.

## Passo a passo: instalar e abrir o Unsloth Studio

1. Instale o Unsloth Studio. Rode o primeiro comando do bloco. Resultado: o instalador termina e pergunta se você quer iniciar o Studio agora. Responda n, porque a pasta dos modelos ainda será configurada.
2. Recarregue o terminal. Rode exec bash. Resultado: o terminal recarrega com um novo prompt, sem sair da janela.
3. Defina a pasta dos modelos e do cache. Rode as três linhas de export. Escolha uma pasta com espaço livre. Resultado: o terminal volta ao prompt, sem mensagem de erro.
4. Inicie o Studio na porta 8080. Rode o comando unsloth studio. Resultado: o servidor sobe na porta 8080. Deixe este terminal aberto enquanto usa o Studio, porque é ele que mantém o servidor ligado.
5. Abra http://localhost:8080 no navegador e crie sua senha. Resultado: aparece a tela do Unsloth Studio, com opções para conversar com modelos. Guarde a senha para os próximos acessos.

Fonte: <https://unsloth.ai/docs/new/studio/install>

## Passo a passo: baixar o modelo e ligar o Pi

1. Baixe o Inkling 2 Mini. No seletor de modelos do Studio, pesquise Inkling 2 Mini e escolha a versão UD-Q4_K_XL. Resultado: o modelo baixa sozinho e carrega, pronto para conversar. Se o download demorar, espere.
2. Instale o Pi. Rode o primeiro comando do bloco. Resultado: a instalação termina e o terminal volta ao prompt. Se aparecer um erro, leia a última linha dele antes de tentar de novo.
3. Recarregue o terminal com login. Rode exec bash -l. Resultado: o terminal recarrega com um novo prompt. Se o Pi ainda não for reconhecido, feche e abra a janela do terminal. Não pule este passo.
4. Conecte o Pi ao modelo. Na pasta do seu projeto, rode as duas últimas linhas do bloco. Resultado: o Pi abre no terminal, usando o Inkling 2 Mini como modelo.

Fonte: <https://unsloth.ai/docs/integrations/unsloth-start>

## Prompt pronto

Cole o prompt inteiro no Pi e envie, sem mudar o texto. O Pi começa a gerar o código do jogo em HTML, CSS e JavaScript. Se o personagem correr de lado, peça o ajuste num novo prompt.

```
Create a fully playable, visually stunning 2D Subway Surfers-style endless runner game using HTML5 Canvas, CSS, and JavaScript, featuring three-lane movement, jumping, sliding, trains, obstacles, collectible coins, power-ups, smooth character animations, parallax scrolling city backgrounds, colorful cartoon graphics, particle explosions, glowing effects, motion blur, speed trails, dynamic lighting, screen shake, realistic shadows, sound effects, background music, increasing difficulty, collision detection, score tracking, responsive keyboard and mobile swipe controls, animated menus, pause and restart functionality, and polished arcade-style gameplay optimized for 60 FPS, using original characters and assets.
```

## Teste de pronto

- [ ] A tela do Unsloth Studio abre em http://localhost:8080 e mostra opções para conversar com modelos.
- [ ] O Inkling 2 Mini aparece carregado e pronto para conversar no Studio.
- [ ] O Pi abre no terminal, pronto para receber pedidos.
- [ ] O Pi começa a escrever o código do jogo depois do prompt.
- [ ] Ao abrir no navegador o arquivo HTML que o Pi criou na pasta do projeto, a tela inicial do jogo aparece, com cores e efeitos.

## Cuidados

- O modelo gera o código, mas o resultado precisa de teste. No nosso teste, o personagem correu de lado. A correção foi um novo pedido ao Pi.
- Os números de desempenho e o tempo de cerca de 10 minutos são do nosso teste, com uma RTX 3090. Eles mudam com a placa, a quantização e a configuração.
- O comando de conexão do Pi segue o exemplo para Linux.
- Se o Studio roda em outra máquina, troque 127.0.0.1 pelo endereço dela. Para um servidor remoto, defina também a variável UNSLOTH_API_KEY.
- Guarde a senha criada no Studio. Ela serve para os próximos acessos.

## Plano de 7 dias

- Dia 1: instale o Unsloth Studio e recarregue o terminal.
- Dia 2: defina a pasta dos modelos, inicie o Studio na porta 8080 e crie sua senha.
- Dia 3: baixe o Inkling 2 Mini no Studio.
- Dia 4: instale o Pi e recarregue o terminal com login.
- Dia 5: conecte o Pi ao modelo.
- Dia 6: peça o jogo com o prompt.
- Dia 7: abra o jogo no navegador e faça o teste de pronto.

## Além do vídeo

- No teste de desempenho, o Inkling 2 Mini ficou em média com cerca de 52 tokens por segundo, numa RTX 3090 com 24 GB de VRAM.
- Uma pergunta com busca na web ativada no Studio: o modelo reuniu informações de fontes diferentes para responder.
- Um painel de mercado de petróleo gerado pelo modelo, sem ferramentas ativas. Os valores eram simulados, não cotações reais.
- O jogo é feito em HTML, CSS e JavaScript, por isso pode ser publicado na Vercel e jogado por outras pessoas no navegador.
