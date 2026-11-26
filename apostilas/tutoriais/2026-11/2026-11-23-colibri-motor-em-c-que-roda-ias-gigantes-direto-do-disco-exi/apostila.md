# Colibri, motor em C que roda IAs gigantes direto do disco, exige 429 GB livres para o GLM 5.2

_2026-11-23 · tutorial_

O Colibri é um motor de inferência escrito em C que roda modelos de centenas de bilhões de parâmetros direto do disco, sem placa de vídeo. Com este tutorial você prepara o computador, instala o projeto, baixa o GLM 5.2 e conversa com ele totalmente offline. Você também entende como o motor decide o que fica na RAM e o que é lido do disco, quais são os requisitos reais de espaço e memória, e como evitar o erro mais comum de falta de espaço. Ao fim, terá o Colibri instalado, com o modelo pronto, e saberá testar, acompanhar o status e usar o servidor local compatível com a OpenAI.

## O que você terá no fim

No fim deste tutorial, você terá o Colibri instalado no seu computador e conversando com o GLM 5.2, um modelo de 744 bilhões de parâmetros, sem placa de vídeo e sem internet.

Além do chat no terminal, o Colibri sobe um servidor local com endereços compatíveis com a OpenAI e com a Anthropic, que outros aplicativos podem usar. Quem cria aplicativos pode apontar o código para esse endereço local e parar de pagar por tokens, porque nada sai da máquina.

O custo real da preparação é o download de 429 GB do GLM 5.2 e o espaço em disco para guardá-lo. O resto da instalação se monta sozinho a partir do repositório.

Fonte: <https://github.com/JustVugg/colibri>

## Como isso funciona

O GLM 5.2 é um modelo de mistura de especialistas: tem 744 bilhões de parâmetros no total, mas usa cerca de 40 bilhões para cada token, e apenas cerca de 11 GB desses parâmetros mudam de um token para o outro. São os especialistas roteados.

Por isso o modelo não precisa caber inteiro na memória rápida. A parte densa (atenção, especialistas compartilhados, embeddings) fica na RAM. Os especialistas roteados ficam no disco e são lidos quando o roteador pede, por um cache que aprende quais especialistas seu trabalho usa. Se houver GPU, ela guarda os especialistas mais usados e as camadas densas.

Onde um peso fica muda a velocidade da resposta, não quais pesos ou decisões do roteador produzem a resposta. É o mesmo princípio de um filme em streaming: você não baixa o filme inteiro antes de assistir, o player busca as partes que precisa.

O Colibri é escrito em C, um arquivo por família de modelo, e roda no hardware que você já tem. Não exige GPU. A parte densa fica na RAM e o resto é lido do disco conforme necessário.

Fonte: <https://github.com/JustVugg/colibri>

## Antes de começar

Confira estes requisitos antes de instalar.

- Sistema operacional: Windows, Linux (Ubuntu e Debian; outras distribuições têm os mesmos pacotes com outros nomes) ou macOS.
- Memória RAM: em geral, pelo menos 8 GB, e 16 GB ou mais é melhor. Para o GLM 5.2 especificamente, 16 GB no mínimo e 24 GB é melhor.
- Espaço em disco: 22 GB livres para o modelo menor. Para o GLM 5.2, 429 GB livres no disco onde o modelo vai ficar.
- Conexão com a internet, para baixar o projeto e o modelo.
- Git e Python: no Linux e no macOS entram no passo 2; no Windows o instalador oferece instalar o Python se faltar.
- Placa de vídeo: opcional. O motor pode usar GPU quando isso vale a pena, mas funciona em CPU.
- Disco NVMe é o mais indicado, porque é dele que o Colibri lê as partes do modelo que não cabem na memória.

Fonte: <https://github.com/JustVugg/colibri>

## Passo a passo

Siga os passos na ordem. Cada um diz a ação e o resultado esperado, para você saber se deu certo. Os comandos estão em seções próprias mais abaixo.

1. Passo 1 — Conferir o espaço em disco. Abra o gerenciador de arquivos ou de discos e veja o espaço livre do disco onde o modelo vai ficar. Resultado esperado: pelo menos 429 GB livres, de preferência com folga.
2. Passo 2 — Instalar os pacotes do sistema. No terminal do Ubuntu ou Debian, instale Git, Python e as ferramentas de compilação. Resultado esperado: os pacotes são instalados e o terminal volta ao prompt sem erro.
3. Passo 3 — Clonar o repositório do Colibri. Copie o projeto para o seu computador. Resultado esperado: uma pasta nova com o nome do projeto aparece no diretório atual.
4. Passo 4 — Entrar na pasta do projeto. Todos os comandos seguintes precisam ser executados de dentro dela. Resultado esperado: o terminal passa a estar dentro da pasta colibri.
5. Passo 5 — Listar os modelos que cabem. Rode o instalador com --list. Resultado esperado: lista de modelos comparados com a sua máquina, com o motivo quando um não cabe.
6. Passo 6 — Rodar o instalador no disco grande. Troque DIR pela pasta no disco com espaço; o padrão é ~/colibri-models. Resultado esperado: o instalador examina a máquina, prepara o motor e começa o download com progresso.
7. Passo 7 — Acompanhar o download e retomar. Deixe o terminal aberto; para pausar use Ctrl+C; para continuar rode de novo o mesmo comando do passo 6. Resultado esperado: o download segue de onde parou e, no fim, aparece Starting colibri com os endereços locais.
8. Passo 8 — Conferir o status do Colibri. Em outro terminal, dentro da pasta do projeto. Resultado esperado: mostra o que está instalado e se o Colibri está rodando.
9. Teste — Conversar com o modelo. Na pasta do projeto, abra o chat no terminal e escreva uma saudação. Resultado esperado: aparece o banner com o nome do motor e do modelo, a linha ✓ ready com o tempo de carga e a memória residente, e o campo para digitar.

Fonte: <https://github.com/JustVugg/colibri>

## Comandos: instalar pacotes, clonar e entrar na pasta

Rode no terminal do Ubuntu ou Debian, uma linha de cada vez. A primeira instala Git, Python e as ferramentas de compilação. O Colibri é escrito em C e, com o compilador, a instalação monta o motor para a sua máquina. Em outras distribuições, os pacotes têm outros nomes. No macOS, o caminho é outro (veja a seção de comandos do macOS). No Windows, a instalação de pacotes não existe: o instalador se oferece para instalar o Python se ele faltar. Se o comando pedir senha, digite a senha do seu usuário.

A segunda linha copia todo o código do projeto para uma pasta no seu computador. É de lá que sai o instalador. Este passo é leve, porque o modelo de 429 GB ainda não foi baixado. Se der erro de comando não encontrado, o Git não foi instalado: volte à primeira linha. Se der erro de rede, confira a conexão e repita o comando. No Windows, este passo é o botão Code seguido de Download ZIP, na página do projeto.

A terceira linha entra na pasta do projeto. Todos os comandos seguintes precisam ser executados de dentro dela, porque o instalador e o programa de conversa estão ali. Esse passo não mostra nenhuma mensagem: o único sinal é o terminal passar a exibir o nome da pasta no início da linha, em muitos sistemas. Para ter certeza, liste os arquivos e procure o instalador do projeto. Se o terminal responder que a pasta não existe, você está em outro lugar: volte à pasta onde rodou o clone e tente de novo.

```
sudo apt install git python3 build-essential
git clone https://github.com/JustVugg/colibri
cd colibri
```

Fonte: <https://github.com/JustVugg/colibri>

## Comando: listar os modelos

Ainda dentro da pasta do projeto. O instalador examina a sua máquina (memória, espaço livre em disco, processador e placas de vídeo) e compara cada modelo disponível com o que você tem. Serve para você saber de antemão o que cabe e por que um modelo não cabe, antes de começar um download enorme. Você deve ver uma lista de modelos, cada um com a indicação de caber ou não. O identificador do GLM 5.2 é glm-5.2, e vamos usá-lo no próximo passo. Se o comando não for reconhecido, confirme que você está dentro da pasta do projeto. No Windows, use START-HERE.bat --list.

```
./start-here.sh --list
```

Fonte: <https://github.com/JustVugg/colibri>

## Comando: rodar o instalador no disco grande

Troque DIR pela pasta no disco com espaço; o padrão é ~/colibri-models. O identificador glm-5.2 já vem preenchido. O instalador olha a máquina, prepara o motor, baixa o modelo e abre a interface. A opção de pasta existe porque, por padrão, os modelos vão para uma pasta dentro do seu usuário, e o GLM 5.2 precisa dos 429 GB livres. Você deve ver o progresso do download. Se aparecer o aviso de que o download precisa de mais espaço livre, aponte a pasta para um disco maior. Em WSL, mantenha o modelo no disco do Linux, não em uma pasta do Windows, que é muito mais lenta.

```
./start-here.sh --model glm-5.2 --dir DIR
```

Fonte: <https://github.com/JustVugg/colibri>

## Comando: conferir o status

Em outro terminal, dentro da pasta do projeto. Mostra o que está instalado e se o Colibri está rodando. Serve para confirmar que o download terminou e o motor subiu, antes de você testar a conversa. Você deve ver o modelo instalado e o estado de funcionamento. No Windows, o comando usa a barra invertida e a extensão de lote: c\coli.cmd status. Se algo falhar, o comando de logs mostra o registro do servidor.

```
c/coli status
```

Fonte: <https://github.com/JustVugg/colibri>

## Comando: conversar com o modelo

Na pasta do projeto, abre um chat no terminal, direto com o GLM 5.2, sem internet e sem enviar nada para fora da sua máquina. Você deve ver uma linha com o nome do motor e do modelo, depois a mensagem de pronto com o tempo de carga e a memória residente, e então o campo para digitar. Escreva um oi e espere a resposta aparecer. A velocidade da resposta depende do seu disco, porque o motor lê dele as partes que precisa. Se nada responder, confira com o comando de status se o motor está de pé.

```
./coli chat
```

Fonte: <https://github.com/JustVugg/colibri>

## Comandos do macOS

No macOS, com Homebrew. O primeiro comando instala o kit de ferramentas da Apple; o segundo instala as dependências. Depois clone o repositório e rode o instalador, como no Linux.

```
xcode-select --install
brew install libomp git python
git clone https://github.com/JustVugg/colibri
cd colibri
./start-here.sh
```

Fonte: <https://github.com/JustVugg/colibri>

## Instalação no Windows

No Windows, o passo de terminal não existe. Na página do projeto, clique em Code e depois em Download ZIP, descompacte a pasta e dê dois cliques em START-HERE.bat dentro dela. Se o Python faltar, o instalador se oferece para instalá-lo. Para listar os modelos, use START-HERE.bat --list. Para conferir o status, use c\coli.cmd status.

Fonte: <https://github.com/JustVugg/colibri>

## Comando: ver os logs

Se algo falhar, estes comandos mostram o que aconteceu. O primeiro exibe o log de um servidor iniciado em segundo plano; o segundo, o log do próprio instalador. Abra uma issue no repositório com as últimas linhas.

```
c/coli logs -n 50
c/coli logs --install
```

Fonte: <https://github.com/JustVugg/colibri>

## Comando: iniciar depois da instalação

Nas próximas vezes, rode este comando (ou START-HERE.bat no Windows). O Colibri sobe direto, sem download e sem compilação.

```
./start-here.sh
```

Fonte: <https://github.com/JustVugg/colibri>

## Comando: parar o Colibri

Para o servidor. No Windows, use c\coli.cmd stop.

```
c/coli stop
```

Fonte: <https://github.com/JustVugg/colibri>

## Exemplo completo

Este é um exemplo do que aparece no chat do terminal. Os números de tempo de carga e memória residente variam conforme a máquina.

```
$ ./coli chat
  colibri v2.2.0 · GLM-5.2 · 744B MoE · int4 · streaming CPU
  ✓ ready in 32s · resident 9.9 GB
  › ciao!
  ◆ Ciao! Come posso aiutarti oggi?
```

Fonte: <https://github.com/JustVugg/colibri>

## Exemplo completo (continuação)

Ao terminar o download, o instalador inicia o Colibri e imprime os endereços que outros aplicativos podem usar.

```
Starting colibri
  Browser:             http://127.0.0.1:8000/
  OpenAI base URL:     http://127.0.0.1:8000/v1
  Anthropic base URL:  http://127.0.0.1:8000
  stop: press Ctrl+C here (or close this window)
```

Fonte: <https://github.com/JustVugg/colibri>

## Prompt pronto

Se você usa um assistente de código com IA, pode pedir que ele faça a instalação por você. O assistente tem todos os passos como comandos com resultado legível por máquina e pede confirmação antes de baixar um modelo ou instalar pacote do sistema. Assistentes que falam MCP podem usar o servidor do Colibri com coli mcp.

```
Set up colibri on this machine following docs/AI_SETUP.md from https://github.com/JustVugg/colibri
```

Fonte: <https://github.com/JustVugg/colibri>

## Teste de pronto

Confira estes pontos para saber se tudo funcionou.

- [ ] O comando ./coli chat mostra o banner com o nome do motor e do modelo (colibri v2.2.0 · GLM-5.2 · 744B MoE · int4 · streaming CPU).
- [ ] Aparece a linha ✓ ready in ... · resident ... com o tempo de carga e a memória residente.
- [ ] O campo para digitar aparece e o modelo responde a uma saudação.
- [ ] O comando c/coli status mostra o modelo instalado e o estado de funcionamento.
- [ ] O navegador abre em http://127.0.0.1:8000/ quando o download termina.
- [ ] Nada sai da sua máquina: a conversa é offline.

Fonte: <https://github.com/JustVugg/colibri>

## Erros comuns e cuidados

Armadilhas, limites e o que conferir antes de confiar no resultado.

- Falta de espaço: se aparecer o aviso `needs N GB free for the download`, aponte --dir para uma pasta em um disco maior. Este é o tropeço mais comum.
- No WSL, mantenha o modelo no disco do Linux (padrão ~/colibri-models). Pastas em /mnt/c são várias vezes mais lentas.
- Download interrompido por queda de conexão ou janela fechada: rode o mesmo comando outra vez; ele retoma dos bytes já no disco.
- Se uma compilação falhar (por exemplo, arquitetura de GPU não suportada), o instalador oferece a próxima opção (Vulkan, depois CPU). Force com --backend vulkan ou --no-gpu.
- Se o comando não for reconhecido, confirme que você está dentro da pasta do projeto.
- Depois de atualizar o repositório com git pull, rode ./start-here.sh de novo: ele reconstrói o motor quando as fontes mudaram.
- Se algo falhar, c/coli logs -n 50 mostra o log do servidor em segundo plano e c/coli logs --install o do instalador. Abra uma issue no repositório com as últimas linhas.
- O GLM 5.2 ocupa 429 GB, o tamanho indicado na tabela de modelos do projeto.
- A velocidade da resposta depende do disco, porque o motor lê dele as partes que precisa.
- O instalador recomenda um modelo com base na sua máquina; você pode escolher outro com --model ou --reconfigure, e --yes aceita a recomendação sem perguntas.

Fonte: <https://github.com/JustVugg/colibri>

## Glossário

Termos técnicos que podem ser novos, com definição curta.

- MoE (mistura de especialistas): modelo que tem muitos parâmetros no total, mas usa só uma parte deles para cada token.
- Parâmetro: número que o modelo aprendeu durante o treino; quanto mais, maior o modelo.
- Token: pedaço de texto que o modelo lê e gera por vez.
- Especialista roteado: parte do modelo ativada só quando o roteador a pede; fica no disco.
- Parte densa: atenção, especialistas compartilhados e embeddings; fica na RAM.
- NVMe: tipo de disco muito rápido, o mais indicado para o Colibri.
- GGUF: formato de arquivo de modelo já publicado, que o Colibri lê como está.
- Vulkan: interface de GPU usada pelo Colibri em várias placas.
- CUDA: interface de GPU para placas NVIDIA.
- Endpoint compatível com a OpenAI: endereço local que outros aplicativos usam como se fosse a API da OpenAI.
- Memória residente: parte do modelo que fica na RAM durante a execução.
- Streaming (do disco): ler as partes do modelo conforme são necessárias, em vez de carregar tudo de uma vez.

Fonte: <https://github.com/JustVugg/colibri>

## Plano de 7 dias

Uma sugestão para distribuir a instalação em sete dias.

- Dia 1: conferir os 429 GB livres no disco escolhido.
- Dia 2: instalar os pacotes do sistema (Git, Python, build-essential) no Linux.
- Dia 3: clonar o repositório e entrar na pasta do projeto.
- Dia 4: listar os modelos com --list e anotar o identificador do GLM 5.2 (glm-5.2).
- Dia 5: rodar o instalador apontando para o disco grande e começar o download.
- Dia 6: acompanhar o download, retomar se necessário e conferir o status com c/coli status.
- Dia 7: testar a conversa com ./coli chat e abrir o painel em http://127.0.0.1:8000/.

Fonte: <https://github.com/JustVugg/colibri>

## Para onde ir depois

Próximos passos depois de instalar.

- Nas próximas vezes, rode ./start-here.sh (ou START-HERE.bat no Windows): o Colibri sobe direto, sem download nem compilação.
- Pare o servidor com c/coli stop (c\coli.cmd stop no Windows).
- Experimente outros modelos: use --list para ver o que cabe na sua máquina e --model ID para instalar outro; --reconfigure troca de modelo.
- Use o Colibri como servidor local: o endereço compatível com a OpenAI é http://127.0.0.1:8000/v1. Aponte seu código para ele e a conta de tokens vai para zero.
- Leia o guia completo em docs/quickstart.md e o README.pt-BR.md do repositório.
- Peça a um assistente de código para instalar por você, usando o prompt pronto desta apostila.
- Assistentes que falam MCP podem usar o servidor do Colibri: coli mcp.
- Se quiser instalar à mão, há release pré-compilada ou compilação a partir do código, e depois coli chat, coli web ou coli serve.
- Modelos GGUF já publicados também rodam no Colibri, na CPU, em GPU via Vulkan e em NVIDIA via CUDA.
- Problemas? Rode c/coli logs -n 50 e abra uma issue no repositório com as últimas linhas.

Fonte: <https://github.com/JustVugg/colibri>

## Links citados

- https://github.com/JustVugg/colibri/blob/main/docs/quickstart.md
- https://github.com/JustVugg/colibri/issues

## Para saber mais

- O Colibri é gratuito e de código aberto; o autor aceita doações (Buy me a coffee).
- O site oficial é https://justvugg.github.io/colibri e há um Discord da comunidade.
- São treze motores hoje: dez para modelos de linguagem, um para imagens (Qwen-Image-2.1) e dois para decisões, com um terceiro (Clef) sobre o motor Qwen3.6.
- Há um mapa de especialistas no chat que mostra cada especialista disparando.
- O Colibri é uma plataforma de pesquisa aberta: uma otimização entra com medição reprodutível de ponta a ponta, e a política padrão nunca muda silenciosamente a precisão nem a semântica do roteador.
- Menos memória rápida pode custar velocidade, mas não pode redefinir silenciosamente o modelo.
- O instalador mede a largura de banda da RAM, lê a memória e a largura de banda de cada placa e o tipo de disco, e estima a velocidade de decodificação de cada modelo; recomenda o mais capaz que decodifica a 20 tokens por segundo ou mais.
- A tabela de modelos do projeto lista requisitos de RAM (dois números: abaixo do primeiro o modelo não inicia; a partir do segundo roda como medido), GPU suportada e velocidades medidas em máquinas nomeadas.
