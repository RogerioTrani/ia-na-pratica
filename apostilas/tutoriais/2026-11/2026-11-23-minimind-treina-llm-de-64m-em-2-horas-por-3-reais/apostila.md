# MiniMind treina LLM de 64M em 2 horas por 3 reais

_2026-11-23 · tutorial_

O MiniMind é um projeto aberto que treina do zero, em PyTorch puro, um modelo de linguagem de cerca de 64M de parâmetros. Esta apostila leva você do clone do repositório ao chat no terminal e à interface web, com cada comando pronto para copiar. O projeto roda em GPU NVIDIA com CUDA, e sem GPU o treino fica bem mais lento.

## O que você terá no fim

Ao final, você terá o MiniMind clonado, treinado nas duas etapas (pretrain e fine-tuning) e um chat no terminal para conversar com o modelo. A interface web é opcional. Fonte: https://github.com/jingyaogong/minimind

Requisitos: Python 3.10 (python.org), GPU NVIDIA com CUDA (nvidia.com/cuda), Git e pip funcionando (git-scm.com), cerca de 2 GB livres em disco e conexão para baixar os dados (modelscope.cn). Os autores usaram Python 3.10.16 e CUDA 12.2. Sem GPU, é possível usar CPU ou MPS, mas o treino fica bem mais lento.

Fonte: <https://github.com/jingyaogong/minimind>

## Passo a passo

Siga os passos na ordem. Os comandos ficam em seções próprias.

1. Passos 1 e 2: clone e instale as dependências. Baixe o código e instale as dependências. Se a instalação falhar por versão do Python, use o Python 3.10. Resultado esperado: a pasta minimind criada no diretório atual e uma mensagem de sucesso ao final da instalação.
2. baixe os dados de treino. Baixe os dois arquivos da versão mini no ModelScope ou no HuggingFace e coloque os dois na pasta ./dataset. O pretrain_t2t_mini.jsonl tem 1,2 GB. Resultado esperado: os arquivos pretrain_t2t_mini.jsonl e sft_t2t_mini.jsonl estão em ./dataset.
3. confirme a GPU. Rode um trecho no Python que verifica a placa. Se a saída for True, o PyTorch enxerga a placa. Se imprimir False, instale o PyTorch com CUDA em https://pytorch.org. Resultado esperado: a saída é True.
4. Passos 5 e 6: pretrain e fine-tuning. O pretrain ensina o modelo a prever o próximo token em texto bruto. O fine-tuning completo ajusta o modelo para seguir instruções. Rode os dois em sequência, dentro da pasta trainer. Resultado esperado: os arquivos out/pretrain_*.pth e out/full_sft_*.pth são gerados.
5. converse com o modelo no terminal. Na raiz do projeto, rode o comando de chat com o peso do fine-tuning. Faça perguntas em português e confira se as respostas fazem sentido. Resultado esperado: o chat interativo responde.
6. interface web, opcional. O comando baixa o modelo minimind-3, copia a pasta para scripts e abre a interface em Streamlit no navegador. Resultado esperado: a interface abre no navegador.

Fonte: <https://github.com/jingyaogong/minimind>

## Clonar e instalar as dependências

Baixe o código e instale as dependências. O segundo comando usa o mirror Aliyun do PyPI: https://mirrors.aliyun.com/pypi/simple Se a instalação falhar por versão do Python, use o Python 3.10. Erro de rede no clone: verifique a conexão e tente de novo. Fonte: https://github.com/jingyaogong/minimind

```
git clone --depth 1 https://github.com/jingyaogong/minimind
cd minimind && pip install -r requirements.txt -i https://mirrors.aliyun.com/pypi/simple
```

Fonte: <https://github.com/jingyaogong/minimind>

## Conversar no terminal

Na raiz do projeto, rode o comando abaixo para abrir o chat interativo com o peso do fine-tuning. Se o peso não for encontrado, confira o conteúdo de ./out. Se as respostas vierem sem sentido, treine mais épocas. Para retomar um treino interrompido, repita o comando de treino com --from_resume 1. Fonte: https://github.com/jingyaogong/minimind

```
python eval_llm.py --weight full_sft
```

Fonte: <https://github.com/jingyaogong/minimind>

## Interface web

O web_demo procura em scripts as subpastas com pesos e dá erro se não achar nenhuma. Se isso acontecer, confira a pasta scripts e o nome da pasta copiada. Alternativa de download do modelo: git clone https://huggingface.co/jingyaogong/minimind-3. Fonte: https://github.com/jingyaogong/minimind

```
modelscope download --model gongjy/minimind-3 --local_dir ./minimind-3 && cp -r minimind-3 ./scripts/minimind-3 && cd scripts && pip install streamlit && streamlit run web_demo.py
```

Fonte: <https://github.com/jingyaogong/minimind>

## Teste de pronto

Como saber que funcionou. Cada item é verificável.

- [ ] A saída do teste de GPU é True.
- [ ] Os arquivos pretrain_*.pth e full_sft_*.pth aparecem em out.
- [ ] O chat no terminal responde a perguntas em português com sentido.

Fonte: <https://github.com/jingyaogong/minimind>

## Cuidados e opções avançadas

Se faltar memória no pretrain, confirme que está usando a versão mini dos dados. Os checkpoints ficam em ./checkpoints/ e a retomada funciona mesmo com número diferente de GPUs. Com N placas na mesma máquina, o treino multi-GPU roda com torchrun --nproc_per_node N train_xxx.py.

O treino pode ser acompanhado com --use_wandb; o projeto usa SwanLab como padrão. Dá para baixar pesos .pth já treinados pelo autor e testar sem treinar. O projeto cobre ainda LoRA, DPO, PPO/GRPO/CISPO, Tool Use e Agentic RL, além de rodar via ollama (ollama run jingyaogong/minimind-3) e vllm.

Fonte: <https://github.com/jingyaogong/minimind>
