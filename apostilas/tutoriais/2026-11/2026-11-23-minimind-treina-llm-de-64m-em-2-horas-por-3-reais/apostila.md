# MiniMind treina LLM de 64M em 2 horas por 3 reais

_2026-11-23 · tutorial_

O MiniMind é um projeto aberto que treina do zero, em PyTorch puro, um modelo de linguagem de cerca de 64M de parâmetros. Esta apostila leva você do clone do repositório ao chat no terminal e à interface web, com cada comando pronto para copiar.

## O que você precisa antes de começar

O projeto roda em GPU NVIDIA com CUDA. Sem GPU, é possível usar CPU ou MPS, mas o treino fica bem mais lento. Os autores usaram Python 3.10.16 e CUDA 12.2.

- Python 3.10 (python.org)
- GPU NVIDIA com CUDA (nvidia.com/cuda)
- Git e pip funcionando (git-scm.com)
- Cerca de 2 GB livres em disco
- Conexão para baixar os dados (modelscope.cn)

Fonte: <https://github.com/jingyaogong/minimind>

## Passo 1 e 2: clone e dependências

Baixe o código e instale as dependências. O segundo comando usa o mirror Aliyun do PyPI. Se a instalação falhar por versão do Python, use o Python 3.10.

- Resultado esperado: a pasta minimind criada no diretório atual e uma mensagem de sucesso ao final da instalação.
- Erro de rede no clone: verifique a conexão e tente de novo.

```
git clone --depth 1 https://github.com/jingyaogong/minimind
cd minimind && pip install -r requirements.txt -i https://mirrors.aliyun.com/pypi/simple
```

Fonte: <https://github.com/jingyaogong/minimind>

## Passo 3: baixe os dados de treino

Baixe os dois arquivos da versão mini no ModelScope ou no HuggingFace e coloque os dois na pasta ./dataset. O pretrain_t2t_mini.jsonl tem 1,2 GB e serve para reproduzir o modelo mais rápido. Se o download for lento, use o mirror do ModelScope.

- pretrain_t2t_mini.jsonl
- sft_t2t_mini.jsonl
- Resultado esperado: os dois arquivos presentes em ./dataset.

Fonte: <https://github.com/jingyaogong/minimind>

## Passo 4: confirme a GPU

Rode o trecho abaixo no Python. Se a saída for True, o PyTorch enxerga a placa. Se imprimir False, instale o PyTorch com CUDA em pytorch.org.

Fonte: <https://pytorch.org>

## Passos 5 e 6: pretrain e fine-tuning

O pretrain ensina o modelo a prever o próximo token em texto bruto. O fine-tuning completo ajusta o modelo para seguir instruções e responder como assistente. Rode os dois em sequência, dentro da pasta trainer.

Os scripts salvam checkpoints. Se o treino for interrompido, repita o comando com --from_resume 1 e ele retoma de onde parou. Se faltar memória no pretrain, confirme que está usando a versão mini dos dados.

- Pretrain: gera out/pretrain_*.pth
- Fine-tuning: gera out/full_sft_*.pth
- Retomar treino interrompido: python train_pretrain.py --from_resume 1 ou python train_full_sft.py --from_resume 1

Fonte: <https://github.com/jingyaogong/minimind>

## Passo 7: converse com o modelo no terminal

Na raiz do projeto, rode o comando abaixo para abrir o chat interativo com o peso do fine-tuning. Faça perguntas em português e confira se as respostas fazem sentido. Se o peso não for encontrado, confira o conteúdo de ./out. Se as respostas vierem sem sentido, treine mais épocas.

```
python eval_llm.py --weight full_sft
```

Fonte: <https://github.com/jingyaogong/minimind>

## Passo 8: interface web (opcional)

O comando baixa o modelo minimind-3, copia a pasta para scripts e abre a interface em Streamlit no navegador. O web_demo procura em scripts as subpastas com pesos e dá erro se não achar nenhuma. Se isso acontecer, confira a pasta scripts e o nome da pasta copiada.

Alternativa de download do modelo: git clone https://huggingface.co/jingyaogong/minimind-3

```
modelscope download --model gongjy/minimind-3 --local_dir ./minimind-3 && cp -r minimind-3 ./scripts/minimind-3 && cd scripts && pip install streamlit && streamlit run web_demo.py
```

Fonte: <https://github.com/jingyaogong/minimind>

## Além do vídeo

- Com N placas na mesma máquina, o treino multi-GPU roda com: torchrun --nproc_per_node N train_xxx.py
- Os checkpoints ficam em ./checkpoints/ e a retomada funciona mesmo com número diferente de GPUs.
- O treino pode ser acompanhado com --use_wandb; o projeto usa SwanLab como padrão, com interface quase igual à do WandB.
- Dá para baixar pesos .pth já treinados pelo autor e testar sem treinar.
- O projeto cobre ainda LoRA, DPO, PPO/GRPO/CISPO, Tool Use e Agentic RL, além de rodar via ollama (ollama run jingyaogong/minimind-3) e vllm.
