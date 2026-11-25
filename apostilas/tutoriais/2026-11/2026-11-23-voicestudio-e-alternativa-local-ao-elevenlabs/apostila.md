# VoiceStudio, é alternativa local ao ElevenLabs

_2026-11-23 · tutorial_

VoiceStudio é uma alternativa local e gratuita ao ElevenLabs: clona voz a partir de 30 segundos de áudio e transcreve, traduz e dubla vídeo na sua máquina, sem enviar nada para a nuvem. A apostila reúne os comandos e caminhos exatos usados no vídeo, do instalador até o teste com a rede desligada. Você vai precisar de Linux x64 ou WSL2, cerca de 10 GB de disco e, opcionalmente, uma GPU NVIDIA.

## O que você terá funcionando

Voz clonada a partir de 30 segundos de áudio, mais transcrição, tradução e dublagem de um vídeo, rodando na sua máquina. Repositório oficial: github.com/debpalash/VoiceStudio. Fonte: https://github.com/debpalash/VoiceStudio

Antes de começar, confira os requisitos: Linux x64 ou WSL2 no Windows; GPU NVIDIA com VRAM livre (opcional); cerca de 10 GB de disco livre; microfone para gravar a amostra; e conta no Hugging Face (huggingface.co), só para diarização.

Fonte: <https://github.com/debpalash/VoiceStudio>

## Passo a passo

Siga os passos na ordem. Os comandos e caminhos de tela ficam em seções próprias.

1. instale o VoiceStudio. Use o instalador em uma linha no terminal; funciona no Ubuntu e no WSL2. O app baixa Python e o ambiente na primeira execução. O sinal de que terminou é Ready. Resultado esperado: a palavra Ready aparece no terminal. Fonte: https://github.com/debpalash/VoiceStudio/blob/main/docs/install/linux.md
2. instale o Lemonade Server e o modelo de chat. No mesmo distro, instale pelo PPA e adicione o backend CUDA. Depois carregue o Qwen3.5-9B com o raciocínio desligado para respostas rápidas. Resultado esperado: o servidor Lemonade responde na porta 13305. Fonte: https://github.com/lemonade-sdk/lemonade/blob/main/docs/guide/install/ubuntu.md
3. conecte o VoiceStudio ao Lemonade. Em Settings -> System -> LLM Providers, escolha Custom e cole a URL base. Resultado esperado: o modelo aparece listado e o teste de conexão dá ok.
4. clone sua voz com 30 segundos de áudio. Grave a abertura de um livro em domínio público, corte para 30 segundos e importe. O campo de transcrição é opcional. Depois, guarde a voz como perfil. Resultado esperado: a voz clonada reproduz o texto de teste.
5. dublar um vídeo em inglês. Importe o vídeo, revise a transcrição em 15 segmentos e gere o áudio. Leia cada linha traduzida antes de gerar. Resultado esperado: o áudio em inglês é gerado em cerca de 15 segundos.
6. teste com a Wi-Fi desligada. Desligue a rede, confirme que não alcança o GitHub, reinicie o VoiceStudio e rode importação, transcrição, tradução, clone e dublagem. Resultado esperado: toda a cadeia conclui sem erro.

Fonte: <https://github.com/debpalash/VoiceStudio>

## Clonar sua voz

Os campos e botões abaixo são os da tela de clonagem. Se sair errado, regenere após reiniciar o app. Fonte: https://github.com/debpalash/VoiceStudio/blob/main/electron/src/renderer/src/i18n/locales/en.json

```
Abra Voice cloning; na seção Voice, em "Reference recording", clique em "Upload audio" (ou arraste o arquivo para "Drop audio here — or click. WAV, MP3, M4A…") e escolha o arquivo de 30 segundos. Opcional: o campo "Transcript" aceita o texto lido; vazio, o motor escuta o áudio. Depois, "Save as voice profile" guarda a voz.
```

Fonte: <https://github.com/debpalash/VoiceStudio/blob/main/electron/src/renderer/src/i18n/locales/en.json>

## Dublar um vídeo

Se o clone automático for pulado, crie o perfil de voz à mão. Sem diarização automática, crie um perfil com o áudio do narrador. Fonte: https://voicestudio.sh/docs/guides/dubbing

```
Open Dub → choose a local audio/video file or paste a supported media URL → Upload & Transcribe → Generate Dub

Criar o perfil manualmente: abra Voice e escolha From audio, adicione a referência (áudio do narrador) e clique em Save as profile. Atribuir aos segmentos: no Dubbing, abra Cast (casting board) e escolha o perfil salvo na lista ou arraste o chip de voz sobre o falante. Link oficial do pyannote para diarização: https://huggingface.co/pyannote/speaker-diarization-3.1
```

Fonte: <https://voicestudio.sh/docs/guides/dubbing>

## Teste de pronto

Desligue a rede, confirme que não alcança o GitHub, reinicie o VoiceStudio e rode importação, transcrição, tradução, clone e dublagem. Se falhar, confira se os modelos já foram baixados antes.

- [ ] Toda a cadeia concluída sem erro com a rede desligada.
- [ ] A voz clonada reproduz o texto de teste.

Fonte: <https://github.com/debpalash/VoiceStudio>

## Cuidados

O clone pode errar palavras não gravadas, como mini PC saindo como mini psss, e um leve sibilo pode permanecer antes de algumas palavras. A tradução precisa de revisão: um trecho pode ser mistraduzido ou deixado no idioma original. A importação do vídeo não mostra progresso na tela até a transcrição aparecer.

A geração fica um pouco mais lenta offline, cerca de 3,1 segundos para 20 segundos de áudio. Outros já clonaram voz com 5 segundos de áudio e sem GPU. Sem diarização automática, crie um perfil com o áudio do narrador. Repositório: https://github.com/debpalash/VoiceStudio. Diarização: a conta no Hugging Face é usada só para ela, e o modelo oficial está em https://huggingface.co/pyannote/speaker-diarization-3.1

Fonte: <https://github.com/debpalash/VoiceStudio>
