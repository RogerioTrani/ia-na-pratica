# ComfyUI gera imagens, vídeo, áudio e 3D no seu PC

_2026-11-22 · tutorial_

ComfyUI é uma ferramenta de código aberto que roda no seu computador e gera imagens, vídeo, áudio e 3D a partir de fluxos visuais de nós. Esta apostila ensina a instalar o programa com o aplicativo desktop, abrir um fluxo pronto, gerar a primeira imagem e salvar o trabalho. Você também encontra requisitos de hardware, atalhos, cuidados e um plano de sete dias para praticar. Ao terminar, você terá o ComfyUI funcionando e saberá criar e guardar uma imagem por conta própria.

## O que você terá no fim

No fim desta apostila você terá o ComfyUI instalado no seu computador e uma primeira imagem criada por você, com o fluxo salvo para usar de novo.

Você também saberá escolher entre os caminhos de instalação, abrir templates da biblioteca, escrever a descrição da imagem, executar o fluxo e guardar o resultado em arquivo.

O ComfyUI é uma ferramenta de código aberto. Você liga blocos, chamados nós, para carregar modelos, ajustar parâmetros e gerar imagens, vídeo, áudio e conteúdos em três dimensões. Tudo roda localmente, e o resultado depende dos modelos e do hardware disponíveis.

Fonte: <https://github.com/Comfy-Org/ComfyUI>

## Como isso funciona

O ComfyUI funciona como um quadro de blocos. Cada bloco, chamado nó, faz uma tarefa, como carregar um modelo ou codificar um texto. Você liga um nó ao outro para formar o fluxo, e o programa percorre essas ligações na ordem em que estão conectadas.

O resultado sai no bloco final, como o bloco Save Image. Como o fluxo fica salvo em arquivo, você pode abri-lo de novo e repetir a geração sem refazer as ligações.

O programa roda em Windows, Linux e macOS. O repositório diz que consegue rodar até modelos grandes com quatro gigabytes de memória de vídeo e oito de memória comum, usando streaming assíncrono de pesos.

Fonte: <https://github.com/Comfy-Org/ComfyUI>

## O que o ComfyUI pode gerar

O ComfyUI tem suporte nativo a muitos modelos de código aberto. A biblioteca de fluxos prontos cobre geração e edição de imagens, geração de vídeo, áudio e áudio com vídeo, modelos em três dimensões e visão, além de geração de texto.

Entre os modelos de imagem citados no repositório estão Stable Diffusion 1.5, SDXL, SD3.5, Flux.1, Flux.2, Qwen Image, Z-Image, Hunyuan Image 2.1, HiDream e outros. Para vídeo, Wan 2.1 e 2.2, LTX-Video, HunyuanVideo 1.5 e mais. Para áudio, ACE-Step 1.5, Stable Audio 3, MiniMax Music 3 e Yue 2.

Há também nós parceiros que dão acesso a modelos fechados, como Nano Banana, Seedance e Hunyuan3D. A lista completa e atualizada está na biblioteca de fluxos do site oficial.

O ComfyUI também expõe fluxos complexos por meio do App Mode, que mostra uma interface simples, e oferece endpoints de API para integrar fluxos em aplicativos.

Fonte: <https://github.com/Comfy-Org/ComfyUI>

## Antes de começar

Antes de instalar, confira se o seu computador atende ao mínimo e se você tem espaço e internet.

- Sistema operacional: Windows, macOS ou Linux.
- Placa de vídeo compatível. O aplicativo desktop cobre Windows e macOS; a instalação manual atende todos os sistemas e vários tipos de placa.
- Mínimo citado para modelos grandes: quatro gigabytes de memória de vídeo e oito gigabytes de memória comum.
- Espaço livre em disco para os modelos, que são arquivos grandes.
- Conexão com a internet para baixar o instalador.
- No macOS, o Comfy Desktop exige chip Apple Silicon, macOS 13 Ventura ou mais recente e pelo menos 4,85 GB livres.

Fonte: <https://github.com/Comfy-Org/ComfyUI>

## Os três caminhos de instalação

O repositório oficial lista três caminhos. O aplicativo desktop é a forma mais fácil de começar e existe para Windows e macOS. A instalação manual serve para todos os sistemas e tipos de placa de vídeo e dá controle sobre as versões de Python e Torch. A nuvem paga serve para quem não tem hardware local.

Nesta apostila seguimos com o aplicativo desktop. Se você usa Linux, use a instalação manual descrita no repositório e aproveite o restante para entender o fluxo.

Há também um build portátil para Windows, que se descompacta e roda, além de versões em nuvem, linha de comando, plataforma para desenvolvedores e opção enterprise. Esta apostila foca no aplicativo desktop.

Fonte: <https://github.com/Comfy-Org/ComfyUI>

## Passo a passo: instalar com o Comfy Desktop

Siga os passos na ordem. Cada item traz a ação e o resultado esperado.

1. Escolha o modo de instalação. Decida entre aplicativo desktop, instalação manual ou nuvem, conforme o seu sistema. Resultado esperado: você sabe qual caminho combina com o seu computador. Se você usa Linux, vá pela instalação manual.
2. Abra a página oficial de download. No navegador, entre em comfy.org/download. Resultado esperado: a página oficial abre com a opção de download. Use só essa página para baixar.
3. Baixe o instalador do seu sistema. A página detecta a plataforma e oferece o instalador para Windows ou macOS. Resultado esperado: o navegador baixa o instalador para a pasta de downloads. Se o sistema for Linux, o aplicativo desktop não está disponível: volte ao passo 1.
4. Instale e abra o ComfyUI. No Windows, execute o arquivo .exe baixado e siga as telas; depois abra o Comfy Desktop pelo Menu Iniciar ou pelo atalho. No macOS, abra o .dmg, arraste o Comfy Desktop para Aplicativos e abra pelo Launchpad ou Spotlight; se aparecer aviso de segurança, vá em Ajustes do Sistema, Privacidade e Segurança, e clique em Abrir Mesmo Assim. Na primeira abertura, escolha rodar localmente neste computador. Resultado esperado: a janela do ComfyUI abre com o quadro de nós.
5. Abra um fluxo pronto da biblioteca. Clique no ícone Templates na barra lateral, ou use o menu Workflow, depois Browse Workflow Templates. Resultado esperado: um fluxo abre no quadro, com blocos ligados por linhas. Se faltar algum modelo, o ComfyUI avisa e oferece o botão Download na lista de modelos faltando.
6. Escolha um fluxo de texto para imagem. Nos templates, escolha um de texto para imagem; a biblioteca online tem a categoria text-to-image. Resultado esperado: o fluxo mostra um bloco de texto do pedido e um bloco do modelo carregado. Se o fluxo depender de um modelo que você não tem, clique em Download na lista de modelos faltando e aguarde terminar.
7. Escreva a descrição e execute. Digite o que você quer ver no bloco CLIP Text Encode (Prompt) e clique em Run. Resultado esperado: a imagem aparece no bloco Save Image ao fim da execução. Atalho: Ctrl+Enter no Windows e Linux, Cmd+Enter no macOS.
8. Salve o fluxo. Com o fluxo aberto, use o atalho de salvar. O ComfyUI guarda o fluxo como arquivo JSON. Resultado esperado: o fluxo fica salvo e pode ser aberto de novo quando você quiser. Atalho: Ctrl+S no Windows e Linux, Cmd+S no macOS.

```
Workflow > Browse Workflow Templates
```

Fonte: <https://docs.comfy.org/installation/desktop/windows>

## Instalação manual: comandos

Se você preferir a instalação manual, ou usa Linux, siga estes comandos do repositório oficial. Instale o PyTorch para a sua placa de vídeo antes de rodar.

- Coloque os checkpoints na pasta models/checkpoints e as VAEs na pasta models/vae.
- Python 3.13 é bem suportado; o 3.14 funciona, mas alguns nós personalizados podem ter problemas.
- Torch 2.7 é o mínimo suportado; em placas Nvidia da série 20 em diante é preciso cu130 ou superior.
- Se o PyTorch tiver mais de seis meses, atualize antes de instalar.

```
git clone https://github.com/Comfy-Org/ComfyUI.git
cd ComfyUI
pip install -r requirements.txt
python main.py
```

Fonte: <https://github.com/Comfy-Org/ComfyUI>

## Atalhos de teclado

Estes são os atalhos usados nos passos acima. O ComfyUI guarda o fluxo como JSON, e você pode recuperar o fluxo completo arrastando uma imagem, vídeo, áudio ou arquivo 3D gerado no ComfyUI para a tela.

- Executar o fluxo: botão Run, ou o atalho mostrado no bloco abaixo.
- Salvar o fluxo: o segundo atalho do bloco.
- Abrir um fluxo salvo: Ctrl+O.
- Atualizar a lista de modelos depois de colocar um arquivo na pasta checkpoints: tecla R.

```
Run (Ctrl+Enter; Cmd+Enter no macOS)
Ctrl+S (Cmd ⌘ + S no macOS)
```

Fonte: <https://docs.comfy.org/interface/shortcuts>

## Exemplo completo: do texto à imagem

Imagine que você acabou de instalar o ComfyUI e quer ver uma imagem aparecer na tela.

Você abre um template de texto para imagem, escreve uma descrição no bloco CLIP Text Encode (Prompt), por exemplo uma paisagem de montanhas ao pôr do sol, e clica em Run. O programa percorre os blocos ligados, carrega o modelo e gera a imagem, que aparece no bloco Save Image.

Se aparecer o aviso Required input missing, ligue a entrada citada na mensagem e rode de novo. Se o modelo não aparecer na lista, coloque o arquivo na pasta checkpoints e aperte R para atualizar.

Depois, salve com Ctrl+S e reabra com Ctrl+O para confirmar que o fluxo voltou com os mesmos blocos.

Fonte: <https://docs.comfy.org/get_started/first_generation>

## Teste de pronto

Faça o teste completo para confirmar que tudo funciona no seu computador.

- [ ] Rode o fluxo de texto para imagem com uma descrição nova e veja se uma imagem nova aparece no bloco de saída.
- [ ] Feche o fluxo e abra o arquivo salvo com Ctrl+O; o fluxo deve voltar com os mesmos blocos.
- [ ] Confirme que o fluxo salvo aparece identificado na aba do programa.
- [ ] Se a imagem não aparecer, volte ao passo de execução e leia a mensagem de erro; em computador mais fraco, use um modelo menor.

Fonte: <https://docs.comfy.org/interface/shortcuts>

## Erros comuns e cuidados

Confira estes pontos antes de confiar no resultado.

- No Linux não há aplicativo desktop: use a instalação manual do repositório.
- No macOS, se aparecer aviso de segurança, libere em Ajustes do Sistema, Privacidade e Segurança, Abrir Mesmo Assim.
- Se a janela não abrir, feche o programa e abra de novo; se continuar, baixe o instalador de novo em comfy.org/download.
- Se o download travar, tente de novo e confira o espaço livre no disco.
- Se faltar modelo, use o botão Download na lista de modelos faltando e aguarde terminar antes de continuar.
- O resultado depende do hardware: em computador fraco, escolha um modelo menor.
- Nvidia: use PyTorch cu130 ou superior. Remova nós e modelos GGUF se houver problemas de desempenho, e remova flags de linha de comando extras.
- O ComfyUI roda totalmente offline por padrão; use --offline para desativar nós de API pagos e forçar tudo offline.

Fonte: <https://github.com/Comfy-Org/ComfyUI>

## Recursos que você pode explorar depois

Depois do primeiro resultado, o ComfyUI oferece muitos recursos. A execução é eficiente: fila assíncrona, re-execução parcial do grafo, gerenciamento de memória de vídeo e RAM, descarregamento de modelos e suporte a modelos quantizados.

Você pode carregar checkpoints completos ou partes separadas: modelos de difusão, VAEs, codificadores de texto, LoRAs, ControlNets, adaptadores e upscalers. Há ferramentas para inpainting, outpainting, condicionamento por referência, máscaras e composição, fusão de modelos, upscaling, interpolação de frames, segmentação, estimativa de profundidade e processamento de mídia.

É possível criar subgrafos reutilizáveis e usar o App Mode para expor um fluxo complexo em uma interface simples. A API local permite integrar fluxos em aplicativos.

Workflows são salvos e carregados como JSON. Você pode arrastar uma imagem, vídeo, áudio ou arquivo 3D gerado no ComfyUI para a tela e recuperar o fluxo completo, sementes incluídas.

Extensões entram via ComfyUI-Manager, e locais adicionais de modelos podem ser configurados em extra_model_paths.yaml. O programa suporta imagens e vídeos de alta profundidade de bit, como PNG de 16 bits, EXR de 32 bits, AVIF de 10 bits e HDR.

Fonte: <https://github.com/Comfy-Org/ComfyUI>

## Glossário

- Nó: bloco que faz uma tarefa, como carregar um modelo ou codificar um texto.
- Fluxo (workflow): conjunto de nós ligados que define como a imagem é gerada.
- Template: fluxo pronto da biblioteca, usado para começar sem montar nó por nó.
- Checkpoint: arquivo do modelo de difusão usado para gerar a imagem.
- VAE: componente que converte entre espaço latente e imagem.
- CLIP Text Encode (Prompt): nó onde você digita a descrição da imagem.
- Run: botão que executa o fluxo.
- VRAM: memória da placa de vídeo.
- JSON: formato em que o fluxo é salvo.
- App Mode: modo que expõe um fluxo complexo em interface simples.
- LoRA: ajuste fino aplicado sobre um modelo base.
- ControlNet: controle extra sobre a geração, como pose ou bordas.

Fonte: <https://github.com/Comfy-Org/ComfyUI>

## Plano de 7 dias

- Dia 1: confira os requisitos e escolha o modo de instalação.
- Dia 2: baixe e instale o ComfyUI com o aplicativo desktop.
- Dia 3: abra um template de texto para imagem e explore os nós.
- Dia 4: escreva a primeira descrição e gere a imagem.
- Dia 5: salve o fluxo e reabra com Ctrl+O para confirmar.
- Dia 6: gere uma imagem com descrição nova e teste modelos menores se preciso.
- Dia 7: explore a biblioteca de fluxos e leia a documentação de atalhos.

## Para onde ir depois

- Explore a biblioteca de fluxos prontos em comfy.org/workflows, incluindo as categorias de imagem, vídeo, áudio e 3D.
- Leia a documentação oficial em docs.comfy.org, incluindo os atalhos e a instalação manual.
- Teste modelos de vídeo, áudio e três dimensões conforme o seu hardware aguentar.
- Acesse o repositório oficial em github.com/Comfy-Org/ComfyUI para novidades e instruções de instalação manual.
- Participe da comunidade no Discord para tirar dúvidas.

Fonte: <https://github.com/Comfy-Org/ComfyUI>

## Links citados

- https://docs.comfy.org/installation/desktop/macos
- https://docs.comfy.org/interface/features/template
- https://www.comfy.org/download

## O que mais o projeto oferece

- O build portátil para Windows, que se descompacta e roda sem instalador.
- O Comfy Cloud, para usar o ComfyUI sem hardware local.
- O Comfy Agent, que planeja e monta o fluxo a partir de uma descrição.
- O Comfy MCP, para dirigir o ComfyUI a partir de um cliente MCP.
- O Comfy CLI, para controlar o motor pelo terminal.
- A opção enterprise, para padronizar o ComfyUI em equipes.
- A plataforma para desenvolvedores, para expor um fluxo como endpoint de API escalável.
- Os nós parceiros, que dão acesso a modelos fechados como Nano Banana, Seedance e Hunyuan3D.
- A lista completa de modelos por categoria, disponível na biblioteca de fluxos.
- As instruções de instalação manual com PyTorch para Nvidia, AMD, Intel Arc, Apple Silicon e outros.
- As soluções de problemas comuns, como nós GGUF e flags de linha de comando.
- A comunidade no Discord e a documentação em docs.comfy.org.
