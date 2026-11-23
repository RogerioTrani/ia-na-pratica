# Nemotron 3.5 Super VL ganha 12% com SFT

_2026-11-23 · tutorial_

Receita da NVIDIA para pós-treinar o Nemotron 3.5 Super VL no seu domínio científico a partir de um CSV de dados experimentais. Você monta um ambiente de reforço com recompensa verificável (RLVR), sem rotulagem humana, e treina com SFT e GRPO. No exemplo de metabolismo de fármacos, o SFT elevou a acurácia em 12% e o reforço acrescentou mais 17%, com orçamento de 16.384 tokens.

## O que você precisa antes de começar

O exemplo prevê metabolismo de fármacos: dados o composto de origem e a enzima, o modelo prevê o metabólito. Os registros vêm do MetxBioDB, base de reações de biotransformação confirmadas em experimento. A receita serve a qualquer domínio em que uma resposta possa receber uma nota.

- GPU NVIDIA com VRAM suficiente (o exemplo usa 16 GPUs: 4 nós com 4 GPUs cada)
- NeMo Gym clonado: github.com/NVIDIA-NeMo/Gym
- NeMo RL clonado: github.com/NVIDIA-NeMo/RL
- Python 3 e rdkit instalados
- Chave de API do modelo professor, na variável POLICY_API_KEY
- CSV com seus dados experimentais

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Como o ambiente verificável funciona

Cada linha do CSV vira um par pergunta e resposta. O modelo raciocina passo a passo e envia a previsão por uma chamada de ferramenta (submit_metabolite). O dado experimental serve de verificador e dá a nota automaticamente.

A nota é a similaridade de Tanimoto entre os fingerprints da molécula prevista e da molécula de referência. Fingerprints são representações numéricas de características estruturais. A similaridade de Tanimoto divide o tamanho da interseção pelo tamanho da união, e nos fingerprints de bits usados aqui vai de 0 a 1. Quanto maior, mais parecidas as moléculas.

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Passos 1 e 2: CSV e JSONL de treino

Passo 1: crie metxbiodb.csv com uma linha por reação confirmada e estas colunas, com estes nomes exatos, porque o script depende deles: parent_smiles, enzyme, reaction_type, metabolite_smiles. Se metabolite_smiles estiver vazia, preencha antes de seguir, senão o verificador não tem o que comparar.

Passo 2: o script abaixo lê metxbiodb.csv e escreve train.jsonl, com uma linha por prompt. Cada linha leva o prompt, a ferramenta submit_metabolite, o agente metxbiodb_simple_agent e o ground_truth_smiles. Não edite o arquivo à mão. Se sair vazio, confira o caminho do CSV e os nomes das colunas.

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Passos 3 e 4: servidor de recursos e rdkit

Passo 3: escreva resources_servers/metxbiodb/app.py com três partes. seed_session guarda o ground truth da sessão. verify devolve essa nota como recompensa. Esse é o único código específico do domínio: para outro problema, troque tanimoto_similarity e o schema da ferramenta. O código de referência está em github.com/NVIDIA-NeMo/Gym.

Passo 4: o servidor precisa de um pyproject.toml com a dependência rdkit, que calcula os fingerprints. Depois de instalar, importe o módulo num terminal para confirmar que carrega sem erro.

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Passos 5 e 6: registrar o ambiente e conectar o trainer

Passo 5: crie resources_servers/metxbiodb/configs/metxbiodb.yaml. O nome do agente tem de ser igual ao agent_ref.name de cada linha do JSONL; um nome diferente derruba o treino sem mensagem clara. Ao final, o ambiente deve aparecer na lista de recursos.

Passo 6: adicione os blocos data e env ao config do trainer, apontando para os JSONL e para o arquivo de registro do ambiente. Se aparecer erro de caminho, corrija as entradas do config.

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Passo 7: traces destilados do modelo professor

A destilação dá ao modelo menor um ponto de partida melhor antes do reforço. O pipeline roda o Claude Sonnet 5.5 sobre o conjunto de treino, pontua cada resposta por Tanimoto contra o metabólito de referência e mantém só os pares (pergunta, trace de raciocínio) que acertaram. No exemplo, com limiar de Tanimoto maior ou igual a 0.7, ficaram 1.123 traces de 1.934 prompts.

Se a geração parar por chave inválida, confira a variável POLICY_API_KEY e repita. Scripts em github.com/NVIDIA-NeMo/Gym.

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Passos 8 e 9: SFT com LoRA e GRPO

Passo 8: o SFT usa configs/sft_metxbiodb_super_vl_lora.yaml, o config completo de SFT do ambiente, e termina com o checkpoint final consolidado em safetensors. Esse checkpoint é o ponto de partida do GRPO. Repositório: github.com/NVIDIA-NeMo/RL.

Por ser um modelo MoE, ligue loss_fn.use_importance_sampling_correction=True.

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Teste: confira o ganho de acurácia

Compare a similaridade média de Tanimoto no conjunto de validação antes e depois do treino, usando o mesmo conjunto e o mesmo orçamento de tokens nas duas medições.

No exemplo de metabolismo, com orçamento de 16.384 tokens, o SFT elevou a acurácia do Nemotron for Science em 12% e o pós-treino por RL acrescentou mais 17%. Anote os dois valores para comparar com o seu domínio.

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Além do vídeo

- Um exemplo completo de trace destilado do Claude Sonnet 5.5 (N-desmetilação por CYP1A2), com o prompt de sistema e o raciocínio em cinco etapas.
- A destilação também pode ser feita por on-policy distillation direta, além do SFT.
- O verificador pode ser mais sofisticado que uma função de similaridade: bibliotecas de quimioinformática, simuladores moleculares ou até um laboratório autônomo podem entrar como chamada de ferramenta.
- O Nemotron Litmus-Bench V2.0 é um dataset e benchmark de raciocínio químico, de código aberto, para treinar e avaliar modelos em propriedades moleculares.
- O pipeline (loop de treino, servidor de recompensa, harness e workers de rollout) é autocontido e serve a qualquer domínio que devolva uma recompensa escalar.
