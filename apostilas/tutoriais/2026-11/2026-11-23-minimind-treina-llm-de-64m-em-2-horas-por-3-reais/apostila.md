# MiniMind treina LLM de 64M em 2 horas por 3 yuans

_2026-11-26 · tutorial_

Esta apostila ensina a treinar do zero um modelo de linguagem de cerca de 64 milhões de parâmetros com PyTorch puro, usando o projeto MiniMind. As 2 horas do título são o tempo medido pelo autor para uma época de fine-tuning supervisionado em uma única NVIDIA 3090, e os 3 yuans (moeda chinesa) são o custo de aluguel da GPU nesse período. Você vai ver por que um LLM pequeno pode ser treinado em poucas horas, quais são os requisitos, como clonar e instalar, baixar os dados, rodar o pretrain e o fine-tuning, testar no terminal e abrir a interface web. Também cobre como conferir se o treino funcionou, erros comuns, glossário, plano de 7 dias e para onde ir depois. O foco é entender cada etapa, não apenas copiar comandos.

## O que você terá no fim

Um modelo de linguagem de cerca de 64 milhões de parâmetros treinado por você, respondendo no terminal. Os dados de treino principais misturam chinês e inglês e os exemplos de conversa do projeto são em chinês, então não espere respostas confiáveis em português. O projeto publica o pipeline completo, do tokenizer à inferência, em PyTorch puro, sem frameworks que escondem o código.

Há também a variante MoE de 198 milhões de parâmetros totais, com 64 milhões ativos, e custo maior.

O objetivo é didático: entender como um LLM é montado, testar cada etapa e poder ler e modificar o código. Um modelo pequeno responde de forma coerente, mas pode errar fatos; isso faz parte do tamanho e do treino.

Fonte: <https://github.com/jingyaogong/minimind>

## Como isso funciona

Um LLM prevê o próximo token a partir do texto anterior. No pretrain, o modelo lê texto bruto e aprende padrões de linguagem e conhecimento básico. No fine-tuning supervisionado, ele aprende a seguir instruções e a conversar no formato de chat usado pelo projeto.

A arquitetura principal é um Transformer decoder-only: 8 camadas, dimensão 768, vocabulário de 6.400 tokens, 8 cabeças de atenção e 4 cabeças de chave/valor, contexto de até 32.768 posições e RoPE com theta 1e6. O tokenizer é próprio, com cerca de 6.400 entradas, e suporta marcas de pensamento e chamada de ferramenta.

Os dados mini recomendados são pretrain_t2t_mini.jsonl, com cerca de 1,2 GB, e sft_t2t_mini.jsonl, com cerca de 1,6 GB. Eles bastam para reproduzir o modelo Zero com menos tempo e memória. Se você tiver mais GPU e tempo, existem versões completas dos dados e opções de treino mais avançadas.

Fonte: <https://github.com/jingyaogong/minimind>

## Antes de começar

- Python 3.10 instalado (python.org).
- GPU NVIDIA com CUDA; a confirmação deve imprimir True (nvidia.com/cuda).
- Git e pip funcionando (git-scm.com).
- Espaço livre em disco: só os dois arquivos de dados mini somam cerca de 2,8 GB; reserve folga para código, dependências, pesos e checkpoints.
- Conexão para baixar dados e modelos (https://www.modelscope.cn/datasets/gongjy/minimind_dataset/files).
- Se não houver GPU, CPU ou MPS funcionam, mas o treino fica muito mais lento.

Fonte: <https://github.com/jingyaogong/minimind>

## Passo a passo

1. Clone o repositório MiniMind no terminal; resultado esperado: pasta minimind criada no diretório atual.
2. Entre na pasta e instale as dependências; resultado esperado: mensagem de sucesso ao final da instalação.
3. Baixe os dois arquivos jsonl mini e coloque-os em ./dataset; resultado esperado: arquivos presentes em ./dataset.
4. Confirme a GPU no Python; resultado esperado: True na saída.
5. Entre em trainer e rode o pretrain; resultado esperado: out/pretrain_*.pth gerado.
6. No mesmo diretório, rode o fine-tuning completo; resultado esperado: out/full_sft_*.pth gerado.
7. Na raiz do projeto, teste o modelo treinado; resultado esperado: chat interativo respondendo no terminal.
8. Opcional: baixe o minimind-3 já publicado (não é o modelo que você treinou), copie para scripts e rode o Streamlit; resultado esperado: WebUI abrindo no navegador.

Fonte: <https://github.com/jingyaogong/minimind>

## Comandos: clonar e instalar

O segundo comando entra na pasta e instala as dependências usando o mirror Aliyun do PyPI. Se falhar por versão do Python, use o Python 3.10.

```
git clone --depth 1 https://github.com/jingyaogong/minimind
cd minimind && pip install -r requirements.txt -i https://mirrors.aliyun.com/pypi/simple
```

Fonte: <https://github.com/jingyaogong/minimind>

## Comando: confirmar a GPU

Antes de treinar, rode este trecho no Python. Se imprimir False, instale ou troque a versão do PyTorch. Sem CUDA, dá para usar CPU ou MPS, com grande diferença de velocidade e compatibilidade.

```
import torch
print(torch.cuda.is_available())
```

Fonte: <https://github.com/jingyaogong/minimind>

## Comando: pretrain

Com os dois arquivos em ./dataset, rode a partir da raiz do projeto. A saída é out/pretrain_*.pth, em que o asterisco é a dimensão do modelo (768 por padrão).

```
cd trainer && python train_pretrain.py
```

Fonte: <https://github.com/jingyaogong/minimind>

## Comando: fine-tuning completo

Este comando também parte da raiz do projeto. Se o terminal ainda estiver dentro de trainer, volte à raiz antes. A saída é out/full_sft_*.pth.

```
cd trainer && python train_full_sft.py
```

Fonte: <https://github.com/jingyaogong/minimind>

## Comandos: retomar um treino interrompido

Rode dentro da pasta trainer o script que foi interrompido. O parâmetro --from_resume 1 detecta o checkpoint salvo em ./checkpoints/ e continua dali.

```
python train_pretrain.py --from_resume 1
python train_full_sft.py --from_resume 1
```

Fonte: <https://github.com/jingyaogong/minimind>

## Comando: conversar no terminal

Na raiz do projeto, abra o chat com o peso do fine-tuning, que precisa estar em ./out. Para testar a base, troque o peso para pretrain.

```
python eval_llm.py --weight full_sft
```

Fonte: <https://github.com/jingyaogong/minimind>

## Comandos: interface web

Na raiz do projeto, uma linha de cada vez: baixe o minimind-3 publicado, copie a pasta para scripts, instale o Streamlit e abra a interface. A interface pode exigir Python 3.10 ou mais novo e dá erro se não achar em scripts uma subpasta com pesos.

```
modelscope download --model gongjy/minimind-3 --local_dir ./minimind-3
cp -r minimind-3 ./scripts/minimind-3
pip install streamlit
cd scripts && streamlit run web_demo.py
```

Fonte: <https://github.com/jingyaogong/minimind>

## Comandos: alternativa de download e teste direto

Em vez do ModelScope, você pode clonar o modelo do Hugging Face. O segundo comando conversa com ele no terminal, a partir da raiz do projeto, sem treinar.

```
git clone https://huggingface.co/jingyaogong/minimind-3
python eval_llm.py --load_from ./minimind-3
```

Fonte: <https://github.com/jingyaogong/minimind>

## Comandos: ollama, vLLM e várias GPUs

As duas primeiras linhas são alternativas para rodar o modelo em motores de terceiros; no vLLM, troque /path/to/model pela pasta do modelo. A última é o formato para treinar com N placas na mesma máquina: troque N pelo número de placas e train_xxx.py pelo script, dentro de trainer.

```
ollama run jingyaogong/minimind-3
vllm serve /path/to/model --served-model-name "minimind"
torchrun --nproc_per_node N train_xxx.py
```

Fonte: <https://github.com/jingyaogong/minimind>

## Exemplo completo

Imagine que você quer reproduzir o modelo no menor tempo possível. Use a rota mini: clone, instale, baixe pretrain_t2t_mini.jsonl e sft_t2t_mini.jsonl, confirme a GPU, rode o pretrain e depois o fine-tuning.

Se faltar memória, use a versão mini dos dados; se interromper o treino, use --from_resume 1 para continuar do checkpoint. Ao final, rode python eval_llm.py --weight full_sft e faça perguntas simples, de preferência em chinês, para checar a coerência. O projeto mostra exemplos de respostas após o pretrain e após o SFT, incluindo perguntas sobre por que o céu é azul e o que é machine learning.

Fonte: <https://github.com/jingyaogong/minimind>

## O que esperar do modelo

Um modelo de 64 milhões de parâmetros é pequeno. Ele pode responder de forma coerente, mas pode errar fatos e repetir ideias. Isso não significa que o pipeline falhou.

- No benchmark de referência, minimind-3 obteve cerca de 24,89 em C-Eval, 25,38 em CMMLU, 28,49 em ARC-Easy, 50,65 em PIQA, 23,60 em OpenBookQA, 28,28 em HellaSwag e 34,19 em Social-IQa.
- A variante MoE tem 198 milhões de parâmetros totais e 64 milhões ativos; seus resultados são próximos, não uma melhoria automática em todos os testes.
- O peso agent melhora tarefas com chamada de ferramenta: em um teste de 20 contas, passou de 12 acertos para 17. Em contrapartida, pode perder estabilidade em perguntas factuais.
- O peso minimind-3-exam melhorou cerca de 2,9 pontos em média após alinhamento de formato, sem adicionar conhecimento novo.

Fonte: <https://github.com/jingyaogong/minimind>

## Teste de pronto

- [ ] torch.cuda.is_available() retorna True.
- [ ] Os dois arquivos mini estão em ./dataset.
- [ ] Existem arquivos out/pretrain_*.pth e out/full_sft_*.pth.
- [ ] python eval_llm.py --weight full_sft abre o chat e responde com coerência.
- [ ] A WebUI abre no navegador após copiar o modelo para scripts.
- [ ] Se a resposta for lenta em CPU, isso é esperado para um modelo pequeno.

Fonte: <https://github.com/jingyaogong/minimind>

## Erros comuns e cuidados

- Se a GPU não for detectada, instale o PyTorch com CUDA compatível com a placa (pytorch.org).
- Se faltar memória, use os dados mini e confira o tamanho dos arquivos para evitar corrupção.
- Se interromper o treino, use --from_resume 1; os checkpoints ficam em ./checkpoints.
- Se a WebUI não detectar o modelo, verifique a pasta scripts e o nome da pasta copiada.
- Se a resposta não fizer sentido, treine mais épocas ou revise os dados.
- Não confunda o peso pretrain, que é a base, com full_sft, que é o modelo conversável.
- Treino em CPU ou MPS é possível, mas muito mais lento.
- Não recrie o tokenizer sem necessidade; mudar o vocabulário afeta pesos e compatibilidade.
- Os tempos e custos são estimativas para uma 3090 e mudam conforme hardware e dados.

Fonte: <https://github.com/jingyaogong/minimind>

## Glossário

- LLM: modelo de linguagem que prevê o próximo token a partir do texto anterior.
- Token: pedaço de texto usado pelo modelo; pode ser palavra, parte de palavra ou símbolo.
- Tokenizer: dicionário que converte texto em números e números de volta em texto.
- Pretrain: treino inicial em texto bruto para o modelo aprender linguagem e conhecimento básico.
- Fine-tuning supervisionado (SFT): treino com exemplos de pergunta e resposta para o modelo conversar e seguir instruções.
- Checkpoint: ponto salvo do treino, com modelo e otimizador, usado para retomar.
- GPU/CUDA: placa e plataforma de aceleração usadas para treinar mais rápido.
- MoE: mistura de especialistas; usa vários blocos de rede e ativa apenas parte deles.
- RoPE: codificação de posição rotativa usada no Transformer.
- YaRN: método para estender o contexto além do treino sem treinar de novo.
- DDP: treino distribuído em várias GPUs.
- RLHF: reforço com feedback humano para alinhar o modelo a preferências.
- RLAIF: reforço com feedback automático ou de modelo, sem anotação humana direta.
- Tool calling: o modelo gera uma chamada de ferramenta e usa o resultado na resposta.
- PPL: medida de quão bem o modelo prevê o texto; menor costuma ser melhor.

Fonte: <https://github.com/jingyaogong/minimind>

## Plano de 7 dias

- Dia 1: Instale Python 3.10, Git e o driver/CUDA; clone o repositório e instale as dependências.
- Dia 2: Baixe os dados mini, confirme a GPU e leia a estrutura de pastas.
- Dia 3: Rode o pretrain e acompanhe a perda e os checkpoints.
- Dia 4: Rode o fine-tuning completo e confirme o peso gerado.
- Dia 5: Teste no terminal com perguntas simples e anote falhas.
- Dia 6: Abra a WebUI e repita os testes com interface visual.
- Dia 7: Ajuste épocas ou dados, ou estude o código para o próximo experimento.

Fonte: <https://github.com/jingyaogong/minimind>

## Para onde ir depois

- Estude model/model_minimind.py, trainer/ e scripts/ para entender cada etapa.
- Experimente a variante MoE e compare tempo e resultado.
- Use os dados completos se tiver mais GPU, tempo e memória.
- Teste LoRA, DPO, PPO, GRPO, CISPO ou Agentic RL conforme a documentação.
- Converta pesos com scripts/convert_model.py quando precisar de formato Transformers.
- Sirva o modelo com scripts/serve_openai_api.py ou motores como vLLM, SGLang, llama.cpp e ollama.
- Ative YaRN para contextos mais longos e avalie com lm-evaluation-harness.
- Compare seu resultado com a tabela de benchmark e com o modelo Zero de referência.

Fonte: <https://github.com/jingyaogong/minimind>

## Links citados

- https://huggingface.co/jingyaogong/minimind-3
- https://mirrors.aliyun.com/pypi/simple
- https://pytorch.org

## Outros recursos do projeto

- Treinos opcionais de pós-treino: LoRA, destilação, DPO, PPO, GRPO, CISPO e Agentic RL.
- Conversão entre pesos torch e Transformers e servidor compatível com OpenAI.
- Inferência em motores de terceiros, como ollama, vLLM, SGLang e llama.cpp.
- Dados completos e suas recomendações de comprimento máximo de tokens.
- Exemplo de diálogo do modelo Zero publicado no projeto.
- Tabela completa de benchmark com outros modelos e instruções de avaliação.
- Configuração de YaRN/RoPE para textos mais longos.
- Treino multi-GPU com DDP e visualização com wandb ou SwanLab.
- Licença Apache 2.0 e lista de modelos publicados.
