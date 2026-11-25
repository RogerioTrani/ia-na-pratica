# ComfyUI gera imagens, vídeo, áudio e 3D no seu PC

_2026-11-22 · tutorial_

O ComfyUI é uma ferramenta de código aberto em que você liga blocos (nós) para gerar imagens, vídeo, áudio e 3D no seu computador. Esta apostila leva você da escolha da instalação até a primeira imagem gerada e o fluxo salvo. O resultado depende dos modelos e do hardware.

## O que você terá no fim

Ao final, você terá o ComfyUI instalado no seu computador, a primeira imagem gerada com um fluxo de texto para imagem e o fluxo salvo para reabrir depois. O resultado depende dos modelos e do hardware. Fonte: https://github.com/Comfy-Org/ComfyUI

Fonte: <https://github.com/Comfy-Org/ComfyUI>

## Antes de começar

O ComfyUI roda em Windows, Linux e macOS. O repositório oficial cita como mínimo para rodar até modelos grandes 4 GB de VRAM e 8 GB de RAM.

- Windows, macOS ou Linux.
- Placa de vídeo compatível.
- 4 GB de VRAM e 8 GB de RAM (mínimo citado).
- Espaço livre em disco para os modelos, que são arquivos grandes.
- Internet para baixar o instalador.

Fonte: <https://github.com/Comfy-Org/ComfyUI>

## Passo a passo

Siga os passos na ordem. Os comandos e atalhos ficam em seções próprias.

1. escolha o modo de instalação. O aplicativo desktop é o jeito mais fácil de começar e existe para Windows e macOS. No Linux, use a instalação manual descrita no repositório. Resultado esperado: você sabe qual caminho seguir.
2. baixe o instalador pela página oficial. Resultado esperado: o instalador do seu sistema está na pasta de downloads.
3. instale e abra o ComfyUI, escolhendo rodar localmente neste computador. Resultado esperado: a janela do ComfyUI com o quadro de nós.
4. abra um fluxo de texto para imagem pelos templates. Resultado esperado: o fluxo mostra o bloco do texto e o bloco do modelo carregado.
5. escreva a descrição e execute. Resultado esperado: a imagem aparece no bloco Save Image.
6. salve o fluxo. Resultado esperado: o fluxo fica num arquivo JSON que você abre de novo.

Fonte: <https://docs.comfy.org/installation/desktop/macos>

## Baixar o instalador

Baixe só pela página oficial. Ela detecta o seu sistema e oferece o instalador para Windows ou macOS. Se algum site pedir para baixar de outro endereço, ignore e volte a ela. Endereço da página oficial:

- Abra a página de download no navegador.
- Clique no instalador do seu sistema.
- Confira se o arquivo chegou à pasta de downloads.

```
https://www.comfy.org/download
```

Fonte: <https://www.comfy.org/download>

## Primeiro fluxo de texto para imagem

Um template já vem com os blocos conectados, então você não precisa montar nó por nó no primeiro dia. Escolha um fluxo de texto para imagem. Se faltar algum modelo, o ComfyUI avisa. Clique em Download na lista de modelos faltando e aguarde terminar antes de continuar. Clique no ícone Templates na barra lateral, ou use o menu abaixo. A biblioteca online tem a categoria text-to-image. Fonte: https://docs.comfy.org/interface/features/template

```
Workflow > Browse Workflow Templates
```

Fonte: <https://docs.comfy.org/interface/features/template>

## Gerar a primeira imagem

Digite o que você quer ver no bloco CLIP Text Encode (Prompt) e clique em Run. A imagem aparece no bloco Save Image ao fim da execução. Se aparecer Required input missing, ligue a entrada citada na mensagem e rode de novo. Se o modelo não aparecer na lista, coloque o arquivo na pasta checkpoints e aperte R. Fonte: https://docs.comfy.org/get_started/first_generation

```
Run (Ctrl+Enter; Cmd+Enter no macOS)
```

Fonte: <https://docs.comfy.org/get_started/first_generation>

## Teste de pronto

Uma janela aberta não prova que a geração funciona. Só uma imagem criada por você prova. Salve o fluxo com o atalho abaixo. O ComfyUI guarda o fluxo como arquivo JSON, e você abre de novo quando quiser sem refazer as ligações. Fonte: https://docs.comfy.org/interface/shortcuts

- [ ] Rode o fluxo com uma descrição nova e confira se uma imagem nova aparece na saída.
- [ ] Feche o fluxo e abra o arquivo salvo com Ctrl+O.
- [ ] O fluxo deve voltar com os mesmos blocos.
- [ ] Se a imagem não aparecer, volte ao passo 5 e leia a mensagem de erro. Em computador fraco, use um modelo menor.

```
Ctrl+S (Cmd ⌘ + S no macOS)
```

Fonte: <https://docs.comfy.org/interface/shortcuts>

## Cuidados e outros modelos

O repositório também diz que é possível recuperar o fluxo completo e as sementes a partir de mídia gerada compatível. Dá para rodar totalmente offline com o parâmetro --offline, que desativa os nós de API pagos.

O repositório lista modelos de imagem compatíveis, como Stable Diffusion 1.5, SDXL, SD3.5, Flux.1, Flux.2, Qwen Image, Z-Image, HiDream e Chroma. Há modelos de vídeo (Wan 2.1 e 2.2, LTX-Video 2 e 2.3, HunyuanVideo 1.5, CogVideoX, Mochi) e de áudio (ACE-Step 1.5, Stable Audio 3). Para 3D, o repositório cita o Hunyuan3D 2.1. Repositório: https://github.com/Comfy-Org/ComfyUI

Fonte: <https://github.com/Comfy-Org/ComfyUI>
