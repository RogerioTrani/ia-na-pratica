# Colibri, motor em C que roda IAs gigantes direto do disco, exige 370 GB livres para o GLM 5.2

_2026-11-23 · tutorial_

O Colibri é um motor em C que roda o GLM 5.2, modelo de 744 bilhões de parâmetros, lendo o que não cabe na memória direto do disco, sem placa de vídeo. Esta apostila leva você do espaço livre até a primeira conversa, offline, no seu computador. O ponto que mais pesa é o disco: o download do GLM 5.2 ocupa 429 GB.

## O que você terá no fim

Ao final, você terá o Colibri instalado e o GLM 5.2 baixado no seu computador, com uma primeira conversa rodando offline. O Colibri mantém na memória só a parte do modelo em uso e busca o resto no disco. Fonte: https://github.com/JustVugg/colibri

Fonte: <https://github.com/JustVugg/colibri>

## Antes de começar

O disco pesa mais que a placa de vídeo, que é opcional.

- Windows, Linux ou macOS.
- 16 GB de RAM para o GLM 5.2 (24 GB é melhor).
- 429 GB livres no disco, o tamanho do GLM 5.2 na tabela de modelos do README.
- Conexão com a internet.
- Git e Python (instalados no passo 2).

Fonte: <https://github.com/JustVugg/colibri>

## Passo a passo

Siga os passos na ordem. Os comandos ficam em seções próprias.

1. confira 429 GB livres. Veja o espaço livre do disco onde o modelo vai ficar. Se faltar espaço, o instalador avisa needs N GB free for the download. Resultado esperado: o disco tem espaço para o download.
2. Passos 2 a 4: pacotes, clone e pasta do projeto. Instale Git, Python e as ferramentas de compilação, clone o repositório e entre na pasta colibri. No Windows, baixe o projeto com Code > Download ZIP e descompacte. Resultado esperado: você está dentro da pasta do projeto.
3. liste os modelos que cabem. Dentro da pasta do projeto, o instalador compara cada modelo com a sua máquina. O identificador do GLM 5.2 é glm-5.2. Resultado esperado: você confirma que o GLM 5.2 cabe na sua máquina.
4. rode o instalador no disco grande. Troque DIR pela pasta no disco com espaço. O padrão é ~/colibri-models. Resultado esperado: o instalador prepara o motor e começa o download com progresso.
5. acompanhe o download e retome. Deixe o terminal aberto. Para pausar, use Ctrl+C. Para continuar, rode de novo o mesmo comando do passo 6: ele segue dos bytes que já estão no disco. Resultado esperado: no fim aparece Starting colibri com os endereços locais.
6. confira o status. Em outro terminal, dentro da pasta do projeto, rode o comando de status. Resultado esperado: você vê o que está instalado e se o Colibri está rodando.

Fonte: <https://github.com/JustVugg/colibri>

## Instalar pacotes e clonar

No Ubuntu ou Debian, o primeiro comando instala Git, Python e as ferramentas de compilação. Outras distribuições têm esses pacotes com outros nomes. No macOS, rode xcode-select --install e depois brew install libomp git python. Se o terminal não achar o comando git, volte e instale os pacotes. Se disser que a pasta colibri não existe, volte ao diretório onde você rodou o clone.

```
sudo apt install git python3 build-essential
git clone https://github.com/JustVugg/colibri
cd colibri
```

Fonte: <https://github.com/JustVugg/colibri>

## Rodar o instalador no disco grande

Troque DIR pela pasta no disco com espaço. Se aparecer needs N GB free for the download, aponte --dir para um disco maior. No WSL, deixe o modelo no disco do Linux e não use a pasta em /mnt/c, que é muito mais lenta. No Windows, use START-HERE.bat --list para listar os modelos.

```
./start-here.sh --model glm-5.2 --dir DIR
```

Fonte: <https://github.com/JustVugg/colibri>

## Confira o status

Se algo falhar, c/coli logs -n 50 mostra o log do servidor em segundo plano. No Windows, use c\coli.cmd status. Se o problema continuar, abra uma issue em https://github.com/JustVugg/colibri/issues com as últimas linhas que o instalador mostrou.

```
c/coli status
```

Fonte: <https://github.com/JustVugg/colibri>

## Teste de pronto

Na pasta do projeto, abra o chat no terminal e escreva uma saudação. A conversa roda sem internet e nada sai da sua máquina. A velocidade da resposta depende do seu disco.

- [ ] Aparecem o banner com o nome do motor e do modelo.
- [ ] Aparece a linha ready com o tempo de carga e a memória residente.
- [ ] O campo para digitar aparece e a resposta chega.

```
./coli chat
```

Fonte: <https://github.com/JustVugg/colibri>

## Cuidados e outras opções

Se nada responder, confira com c/coli status se o motor está rodando. Para criar aplicativos, o servidor do Colibri oferece um endereço compatível com a OpenAI, que aparece na mensagem de inicialização.

Opções do instalador: --yes (aceita a recomendação sem perguntas), --backend vulkan, cuda ou cpu, --model-dir DIR (usa um modelo já baixado) e --reconfigure (escolhe outro modelo). O comando c/coli stop para parar o Colibri (c\coli.cmd stop no Windows). Depois da primeira instalação, rodar ./start-here.sh de novo inicia o Colibri direto, sem download nem compilação.

Guia de início rápido em https://github.com/JustVugg/colibri/blob/main/docs/quickstart.md e site em https://justvugg.github.io/colibri.

Fonte: <https://github.com/JustVugg/colibri/blob/main/docs/quickstart.md>
