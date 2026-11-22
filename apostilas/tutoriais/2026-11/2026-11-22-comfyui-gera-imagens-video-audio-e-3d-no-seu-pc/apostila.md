# ComfyUI gera imagens, vídeo, áudio e 3D no seu PC

_2026-11-22 · tutorial_

O ComfyUI é uma ferramenta de código aberto em que você liga blocos (nós) para gerar imagens, vídeo, áudio e 3D no seu computador. Esta apostila leva você da escolha da instalação até a primeira imagem gerada e o fluxo salvo, com os comandos, atalhos e soluções de erro de cada passo. O resultado depende dos modelos e do hardware.

## O que você precisa antes de começar

O ComfyUI roda em Windows, Linux e macOS. O repositório oficial cita como mínimo para rodar até modelos grandes 4 GB de VRAM e 8 GB de RAM.

- Windows, macOS ou Linux
- Placa de vídeo compatível
- 4 GB de VRAM e 8 GB de RAM (mínimo citado)
- Espaço livre em disco para os modelos, que são arquivos grandes
- Internet para baixar o instalador

Fonte: <https://github.com/Comfy-Org/ComfyUI>

## Passo 1: escolha o modo de instalação

O repositório oficial lista três caminhos. O aplicativo desktop é o jeito mais fácil de começar e existe para Windows e macOS. A instalação manual atende todos os sistemas e tipos de placa de vídeo (NVIDIA, AMD, Intel, Apple Silicon, Ascend). A nuvem paga, a Comfy Cloud, serve a quem não tem hardware local.

Esta apostila segue o aplicativo desktop. No Linux não há aplicativo desktop: use a instalação manual descrita no repositório.

Fonte: <https://github.com/Comfy-Org/ComfyUI>

## Passos 2 e 3: baixe o instalador

Baixe só pela página oficial. Ela detecta o seu sistema e oferece o instalador para Windows ou macOS. Se algum site pedir para baixar de outro endereço, ignore e volte a ela.

- Abra a página de download no navegador.
- Clique no instalador do seu sistema.
- Confira se o arquivo chegou à pasta de downloads.

```
https://www.comfy.org/download
```

Fonte: <https://www.comfy.org/download>

## Passo 4: instale e abra o ComfyUI

Na primeira abertura, o programa pergunta se você quer usar na nuvem ou neste computador. Escolha rodar localmente neste computador. O resultado esperado é a janela do ComfyUI com o quadro de nós.

- Windows: execute o arquivo .exe baixado, siga as telas e abra o Comfy Desktop pelo Menu Iniciar ou pelo atalho.
- macOS (Apple Silicon, macOS 13 Ventura ou mais recente, 4,85 GB livres): abra o .dmg, arraste o Comfy Desktop para Aplicativos e abra pelo Launchpad ou Spotlight.
- Aviso de segurança no macOS: Ajustes do Sistema > Privacidade e Segurança > Abrir Mesmo Assim.
- Se a janela não abrir, baixe o instalador de novo em comfy.org/download e repita o passo.

Fonte: <https://docs.comfy.org/installation/desktop/macos>

## Passos 5 e 6: abra um fluxo de texto para imagem

Um template já vem com os blocos conectados, então você não precisa montar nó por nó no primeiro dia. Escolha um fluxo de texto para imagem. Ele mostra um bloco para o texto do pedido e outro para o modelo carregado.

Se faltar algum modelo, o ComfyUI avisa. Clique em Download na lista de modelos faltando e aguarde terminar antes de continuar.

- Clique no ícone Templates na barra lateral, ou use o menu Workflow > Browse Workflow Templates.
- Escolha um template de texto para imagem. A biblioteca online tem a categoria text-to-image.

```
Workflow > Browse Workflow Templates
```

Fonte: <https://docs.comfy.org/interface/features/template>

## Passo 7: escreva a descrição e execute

Digite o que você quer ver no bloco CLIP Text Encode (Prompt) e clique em Run. A imagem aparece no bloco Save Image ao fim da execução.

- Atalho: Ctrl+Enter (Cmd+Enter no macOS).
- Se aparecer Required input missing, ligue a entrada citada na mensagem e rode de novo.
- Se o modelo não aparecer na lista, coloque o arquivo na pasta checkpoints e aperte R.

```
Run (Ctrl+Enter; Cmd+Enter no macOS)
```

Fonte: <https://docs.comfy.org/get_started/first_generation>

## Passo 8: salve o fluxo

O ComfyUI guarda o fluxo como arquivo JSON, e você abre de novo quando quiser sem refazer as ligações. O repositório também diz que é possível recuperar o fluxo completo e as sementes a partir de mídia gerada compatível.

```
Ctrl+S (Cmd ⌘ + S no macOS)
```

Fonte: <https://docs.comfy.org/interface/shortcuts>

## O teste que confirma tudo

Uma janela aberta não prova que a geração funciona. Só uma imagem criada por você prova.

- Rode o fluxo com uma descrição nova e confira se uma imagem nova aparece na saída.
- Feche o fluxo e abra o arquivo salvo com Ctrl+O.
- O fluxo deve voltar com os mesmos blocos.
- Se a imagem não aparecer, volte ao passo 7 e leia a mensagem de erro. Em computador fraco, use um modelo menor.

Fonte: <https://docs.comfy.org/interface/shortcuts>

## Além do vídeo

- O repositório lista modelos de imagem compatíveis, como Stable Diffusion 1.5, SDXL, SD3.5, Flux.1, Flux.2, Qwen Image, Z-Image, HiDream e Chroma.
- Há modelos de vídeo (Wan 2.1 e 2.2, LTX-Video 2 e 2.3, HunyuanVideo 1.5, CogVideoX, Mochi) e de áudio (ACE-Step 1.5, Stable Audio 3).
- Para 3D, o repositório cita o Hunyuan3D 2.1.
- O ComfyUI também tem ferramentas de inpainting, outpainting, upscaling e interpolação de quadros.
- Dá para rodar totalmente offline com o parâmetro --offline, que desativa os nós de API pagos.
