# Colibri, motor em C que roda IAs gigantes direto do disco, exige 370 GB livres para o GLM 5.2

_2026-11-23 · tutorial_

O Colibri é um motor em C que roda o GLM 5.2, modelo de 744 bilhões de parâmetros, lendo o que não cabe na memória direto do disco, sem placa de vídeo. Esta apostila leva você do espaço livre até a primeira conversa, offline, no seu computador. O ponto que mais pesa é o disco: o download do GLM 5.2 ocupa 429 GB.

## O que você precisa

O Colibri mantém na memória só a parte do modelo em uso e busca o resto no disco. Por isso o disco pesa mais que a placa de vídeo, que é opcional.

- Windows, Linux ou macOS
- 16 GB de RAM para o GLM 5.2 (24 GB é melhor)
- 429 GB livres no disco, o tamanho do GLM 5.2 na tabela de modelos do README
- Conexão com a internet
- Git e Python (instalados no passo 2)

Fonte: <https://github.com/JustVugg/colibri>

## Passo 1: confira 429 GB livres

No gerenciador de arquivos ou de discos do seu sistema, veja o espaço livre do disco onde o modelo vai ficar. Você precisa de pelo menos 429 GB livres nele.

Se faltar espaço, o instalador avisa `needs N GB free for the download`. Nesse caso, use `--dir` com uma pasta em um disco maior (passo 6).

Fonte: <https://github.com/JustVugg/colibri>

## Passos 2 a 4: pacotes, clone e pasta do projeto

No Ubuntu ou Debian, o primeiro comando instala Git, Python e as ferramentas de compilação. Outras distribuições têm esses pacotes com outros nomes. No macOS, rode `xcode-select --install` e depois `brew install libomp git python`. No Windows, baixe o projeto em github.com/JustVugg/colibri com Code > Download ZIP e descompacte; o instalador oferece instalar o Python se ele faltar.

Se o terminal não achar o comando git, volte e instale os pacotes. Se disser que a pasta colibri não existe, volte ao diretório onde você rodou o clone.

- Instale os pacotes (Ubuntu/Debian)
- Clone o repositório
- Entre na pasta colibri

```
sudo apt install git python3 build-essential
git clone https://github.com/JustVugg/colibri
cd colibri
```

Fonte: <https://github.com/JustVugg/colibri>

## Passo 5: liste os modelos que cabem

Dentro da pasta do projeto, o instalador compara cada modelo com a sua máquina e mostra o motivo quando um não cabe. O identificador do GLM 5.2 é `glm-5.2`. No Windows, use `START-HERE.bat --list`.

Fonte: <https://github.com/JustVugg/colibri>

## Passo 6: rode o instalador no disco grande

Troque `DIR` pela pasta no disco com espaço. O padrão é `~/colibri-models`. O instalador examina a máquina, prepara o motor e começa o download com progresso.

Se aparecer `needs N GB free for the download`, aponte `--dir` para um disco maior. No WSL, deixe o modelo no disco do Linux e não use a pasta em `/mnt/c`, que é muito mais lenta.

```
./start-here.sh --model glm-5.2 --dir DIR
```

Fonte: <https://github.com/JustVugg/colibri>

## Passo 7: acompanhe o download e retome

Deixe o terminal aberto. Para pausar, use Ctrl+C. Para continuar, rode de novo o mesmo comando do passo 6: ele segue dos bytes que já estão no disco. A regra vale também para queda de conexão ou janela fechada.

No fim aparece `Starting colibri` com os endereços locais, como

```
./start-here.sh --model glm-5.2 --dir DIR
```

Fonte: <https://github.com/JustVugg/colibri>

## Passo 8: confira o status

Em outro terminal, dentro da pasta do projeto, rode o comando abaixo para ver o que está instalado e se o Colibri está rodando. No Windows, use `c\coli.cmd status`.

Se algo falhar, `c/coli logs -n 50` mostra o log do servidor em segundo plano. Se o problema continuar, abra uma issue em https://github.com/JustVugg/colibri/issues com as últimas linhas que o instalador mostrou.

```
c/coli status
```

Fonte: <https://github.com/JustVugg/colibri>

## Teste: converse com o modelo

Na pasta do projeto, abra o chat no terminal e escreva uma saudação. Aparecem o banner com o nome do motor e do modelo, a linha `✓ ready` com o tempo de carga e a memória residente, e o campo para digitar. A conversa roda sem internet e nada sai da sua máquina. A velocidade da resposta depende do seu disco.

Se nada responder, confira com `c/coli status` se o motor está rodando. Para criar aplicativos, o servidor do Colibri oferece um endereço compatível com a OpenAI, que aparece na mensagem de inicialização.

```
./coli chat
```

Fonte: <https://github.com/JustVugg/colibri>

## Além do vídeo

- Opções do instalador: `--yes` (aceita a recomendação sem perguntas), `--backend vulkan`, `cuda` ou `cpu`, `--model-dir DIR` (usa um modelo já baixado) e `--reconfigure` (escolhe outro modelo).
- O comando `c/coli stop` para parar o Colibri (`c\coli.cmd stop` no Windows).
- Depois da primeira instalação, rodar `./start-here.sh` de novo inicia o Colibri direto, sem download nem compilação.
- O servidor MCP do Colibri (`coli mcp`) e o guia docs/AI_SETUP.md para deixar um assistente de IA fazer a instalação.
- Guia de início rápido em https://github.com/JustVugg/colibri/blob/main/docs/quickstart.md e site em https://justvugg.github.io/colibri.
