# VoiceStudio, é alternativa local ao ElevenLabs

_2026-11-23 · tutorial_

VoiceStudio é uma alternativa local e gratuita ao ElevenLabs: clona voz a partir de 30 segundos de áudio e transcreve, traduz e dubla vídeo na sua máquina, sem enviar nada para a nuvem. A apostila abaixo reúne os comandos e caminhos exatos usados no vídeo, do instalador até o teste com a rede desligada. Você vai precisar de Linux x64 ou WSL2, cerca de 10 GB de disco e, opcionalmente, uma GPU NVIDIA.

## O que você terá funcionando

Voz clonada a partir de 30 segundos de áudio, mais transcrição, tradução e dublagem de um vídeo, rodando na sua máquina. Repositório oficial: github.com/debpalash/VoiceStudio.

Fonte: <https://github.com/debpalash/VoiceStudio>

## Antes de começar

Confira os requisitos antes de instalar.

- Linux x64 ou WSL2 no Windows
- GPU NVIDIA com VRAM livre (opcional)
- Cerca de 10 GB de disco livre
- Microfone para gravar a amostra
- Conta no Hugging Face (huggingface.co), só para diarização

## Instalar o VoiceStudio

Use o instalador em uma linha no terminal; funciona no Ubuntu e no WSL2. O app baixa Python e o ambiente na primeira execução; nada responde até acabar. O sinal de que terminou é "Ready". Se parecer travado, espere e não feche a janela.

- Se o terminal não achar o comando, abra um terminal novo

Fonte: <https://github.com/debpalash/VoiceStudio/blob/main/docs/install/linux.md>

## Instalar o Lemonade Server e o modelo de chat

No mesmo distro, instale pelo PPA e adicione o backend CUDA. Depois carregue o Qwen3.5-9B com o raciocínio desligado para respostas rápidas.

- Servidor Lemonade respondendo na porta 13305
- Se a porta não responder, confira se o serviço subiu
- Se a resposta demorar, confira se o raciocínio foi desligado

Fonte: <https://github.com/lemonade-sdk/lemonade/blob/main/docs/guide/install/ubuntu.md>

## Conectar o VoiceStudio ao Lemonade

Em Settings -> System -> LLM Providers, escolha Custom e cole a URL base. Se der 404, confira se colou a URL no campo de modelo por engano.

- Modelo listado e teste de conexão ok

Fonte: <https://github.com/debpalash/VoiceStudio>

## Clonar sua voz com 30 segundos de áudio

Grave a abertura de um livro em domínio público, corte para 30 segundos e importe. O campo de transcrição é opcional; vazio, o motor escuta o áudio. Depois, "Save as voice profile" guarda a voz. Se sair errado, regenere após reiniciar o app.

- Voz clonada reproduzindo o texto de teste

```
Abra Voice cloning; na seção Voice, em "Reference recording", clique em "Upload audio" (ou arraste o arquivo para "Drop audio here — or click. WAV, MP3, M4A…") e escolha o arquivo de 30 segundos. Opcional: o campo "Transcript" aceita o texto lido; vazio, o motor escuta o áudio. Depois, "Save as voice profile" guarda a voz.
```

Fonte: <https://github.com/debpalash/VoiceStudio/blob/main/electron/src/renderer/src/i18n/locales/en.json>

## Dublar um vídeo em inglês

Importe o vídeo, revise a transcrição em 15 segmentos e gere o áudio. Leia cada linha traduzida antes de gerar. Se o clone automático for pulado, crie o perfil de voz à mão.

- Áudio em inglês gerado em cerca de 15 segundos
- Sem diarização automática, crie um perfil com o áudio do narrador

```
Open Dub → choose a local audio/video file or paste a supported media URL → Upload & Transcribe → Generate Dub

Criar o perfil manualmente: abra Voice e escolha From audio, adicione a referência (áudio do narrador) e clique em Save as profile. Atribuir aos segmentos: no Dubbing, abra Cast (casting board) e escolha o perfil salvo na lista ou arraste o chip de voz sobre o falante. Link oficial do pyannote para diarização: https://huggingface.co/pyannote/speaker-diarization-3.1
```

Fonte: <https://voicestudio.sh/docs/guides/dubbing>

## Teste com a Wi-Fi desligada

Desligue a rede, confirme que não alcança o GitHub, reinicie o VoiceStudio e rode importação, transcrição, tradução, clone e dublagem. Se falhar, confira se os modelos já foram baixados antes.

- Toda a cadeia concluída sem erro

## Além do vídeo

- O clone pode errar palavras não gravadas, como "mini PC" saindo como "mini psss", e um leve sibilo pode permanecer antes de algumas palavras
- A tradução precisa de revisão: um trecho pode ser mistraduzido ou deixado no idioma original
- A importação do vídeo não mostra progresso na tela até a transcrição aparecer
- Outros já clonaram voz com 5 segundos de áudio e sem GPU
- A geração fica um pouco mais lenta offline, cerca de 3,1 segundos para 20 segundos de áudio
