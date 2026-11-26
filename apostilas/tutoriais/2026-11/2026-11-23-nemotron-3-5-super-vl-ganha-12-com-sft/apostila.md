# Nemotron 3.5 Super VL ganha 12% com SFT

_2026-11-23 · tutorial_

Esta apostila ensina a pós-treinar o Nemotron 3.5 Super VL no seu domínio científico usando dados experimentais reais como verificador. Você monta um ambiente de reforço a partir de um CSV, treina com SFT e GRPO e mede o ganho com similaridade de Tanimoto. No exemplo de metabolismo de fármacos, o SFT eleva a acurácia em 12% e o reforço acrescenta mais 17%. No fim você terá um modelo adaptado ao seu domínio, com ambiente verificável e sem rotulagem humana.

## O que você terá no fim

Um Nemotron 3.5 Super VL adaptado ao seu domínio científico, com ambiente verificável e sem rotulagem humana. Serve a equipes de ciência que têm dados experimentais e querem agentes mais precisos em tarefas específicas.

O Nemotron 3.5 Super VL é um modelo multimodal aberto e personalizável que, segundo a NVIDIA, tem precisão de ponta em benchmarks científicos e o menor tempo de solução para código científico. A receita deste tutorial parte de um CSV de registros experimentais e termina em um modelo pós-treinado, medindo o ganho com similaridade de Tanimoto.

No exemplo de metabolismo de fármacos, o treino supervisionado (SFT) eleva a acurácia em 12% e o treino por reforço (GRPO) acrescenta mais 17%, com orçamento de 16.384 tokens de saída. A destilação opcional usa um modelo professor mais forte, como o Claude Sonnet 5.5, para gerar traces de raciocínio de alta qualidade que aquecem o modelo estudante antes do reforço.

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Como isso funciona: RLVR com dados experimentais

A ideia central é transformar dado experimental em recompensa verificável. Você tem um CSV de registros experimentais (por exemplo, moléculas SMILES, enzimas e resultados medidos). Cada linha vira um prompt com resposta esperada. O modelo recebe o problema, raciocina passo a passo e envia uma previsão por chamada de ferramenta. Um verificador automático compara a previsão com a referência e devolve uma nota. Essa nota é a recompensa do treino por reforço.

Isso é chamado de aprendizado por reforço com recompensas verificáveis (RLVR). A vantagem é que não exige rotulagem humana: o sinal de recompensa vem direto dos dados. A fidelidade do verificador pode ser ajustada à tarefa: uma função simples de similaridade de sequência funciona como verificador leve, enquanto ferramentas mais sofisticadas (bibliotecas de quimioinformática, simuladores moleculares ou até um laboratório autônomo) podem ser ligadas como camada de pontuação.

Para o exemplo de metabolismo, o modelo recebe a molécula inicial e a enzima, então envia o metabólito previsto. O verificador compara as impressões digitais moleculares prevista e de referência usando similaridade de Tanimoto. A similaridade de Tanimoto mede a sobreposição entre dois conjuntos ou vetores binários: divide o tamanho da interseção pelo tamanho da união. Para as impressões digitais de bits usadas aqui, a nota vai de 0 a 1; quanto maior, mais similares.

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## A receita em uma frase

O fluxo tem nove passos: preparar o CSV experimental, gerar o JSONL de treino, criar o servidor de recursos, adicionar o rdkit, registrar o ambiente no YAML, conectar o ambiente ao trainer, gerar traces destilados do modelo professor, rodar SFT com LoRA e rodar GRPO no ambiente. No fim, confere o ganho comparando a similaridade média de Tanimoto no conjunto de validação.

O ambiente é montado com o NeMo Gym, que fornece a infraestrutura do ambiente, e o treino é feito com o NeMo RL, que fornece o framework de pós-treino. Os dois repositórios servem de base para adaptar os arquivos ao seu caso.

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Antes de começar

Reúna os pré-requisitos antes de começar. O exemplo da NVIDIA roda em 16 GPUs, quatro nós com quatro GPUs cada. Com menos GPU, use um modelo menor.

- GPU NVIDIA com VRAM suficiente para o modelo (o exemplo roda em 16 GPUs).
- Repositórios NeMo Gym e NeMo RL clonados (github.com/NVIDIA-NeMo/Gym e github.com/NVIDIA-NeMo/RL).
- Python 3 e rdkit instalados.
- Chave de API do modelo professor (variável de ambiente POLICY_API_KEY).
- CSV com seus dados experimentais.

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Passo 1: prepare o CSV experimental

O arquivo tem quatro colunas: molécula inicial, enzima, tipo de reação e molécula de referência, uma linha por reação confirmada. Esse arquivo é a base de tudo, porque cada linha vira um prompt com resposta esperada.

Use os nomes de coluna exatamente como aparecem: o script depende deles.

1. Crie metxbiodb.csv com as colunas parent_smiles, enzyme, reaction_type e metabolite_smiles.
2. Preencha uma linha por reação confirmada.
3. Confira se o arquivo abre e tem uma linha por reação.
4. Se a coluna de referência estiver vazia, preencha antes de seguir, senão o verificador não tem o que comparar.

```
parent_smiles,enzyme,reaction_type,metabolite_smiles
```

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Passo 2: gere o JSONL de treino

O script lê metxbiodb.csv e escreve uma linha por reação no formato que o ambiente entende, com o prompt do sistema, a pergunta, a ferramenta de envio da molécula, o nome do agente e a molécula de referência. Esse passo existe para colocar os dados no formato que o ambiente entende.

Ao final, abra o arquivo e veja uma linha por prompt, com a molécula inicial e a enzima. Se ficar vazio, confira o caminho do CSV e os nomes das colunas. Não edite o arquivo à mão: uma vírgula fora do lugar quebra o treino.

1. Rode o script que gera train.jsonl a partir de metxbiodb.csv.
2. Confira se train.jsonl tem uma linha por prompt.

```
import csv
import json
SYSTEM = open("system_prompt.txt").read()
TOOLS = [{
    "type": "function",
    "name": "submit_metabolite",
    "strict": True,
    "description": (
        "Submit your predicted metabolite SMILES. Returns validity and Tanimoto"
        " similarity (0-1)."
    ),
    "parameters": {
        "type": "object",
        "additionalProperties": False,
        "required": ["smiles"],
        "properties": {
            "smiles": {
                "type": "string",
                "description": "Predicted metabolite SMILES (no extra text).",
            },
        },
    },
}]
with open("train.jsonl", "w") as f:
    for r in csv.DictReader(
        open("metxbiodb.csv")
    ):  # columns: parent_smiles, enzyme, reaction_type, metabolite_smiles
        user = (
            f"Parent compound SMILES: {r['parent_smiles']}\nMetabolising"
            f" enzyme: {r['enzyme']}\n\nReason through this biotransformation"
            " step by step, then call submit_metabolite with the predicted"
            " SMILES of the primary metabolite."
        )
        f.write(
            json.dumps({
                "responses_create_params": {
                    "input": [
                        {"role": "system", "content": SYSTEM},
                        {"role": "user", "content": user},
                    ],
                    "tools": TOOLS,
                },
                "agent_ref": {"name": "metxbiodb_simple_agent"},
                "parent_smiles": r["parent_smiles"],
                "enzyme": r["enzyme"],
                "reaction_type": r["reaction_type"],
                "ground_truth_smiles": r["metabolite_smiles"],
            }) + "\n"
        )
```

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Passo 3: crie o servidor de recursos

Escreva resources_servers/metxbiodb/app.py com três partes: seed_session guarda o ground truth da sessão, submit_metabolite pontua a primeira submissão com Tanimoto de fingerprint Morgan (raio 2, 2048 bits) e verify devolve essa nota como recompensa.

É o único código específico do seu domínio. Para outro problema, troque a função de similaridade e o formato da ferramenta. Se der erro de importação, confira o rdkit.

1. Crie o arquivo resources_servers/metxbiodb/app.py.
2. Implemente seed_session para guardar ground_truth_smiles por sessão.
3. Implemente submit_metabolite para pontuar a primeira submissão com fingerprint Morgan, raio 2 e 2048 bits, Tanimoto.
4. Implemente verify para devolver o score como recompensa.

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Passo 4: adicione o rdkit ao projeto

O servidor precisa de um pyproject.toml com a dependência rdkit, que calcula os fingerprints Morgan usados na pontuação. O passo existe porque o servidor precisa transformar as fórmulas em números para comparar.

Depois de instalar, importe o módulo num terminal e confira se carrega sem erro. Se a instalação falhar, repita pelo canal oficial do rdkit e não siga com o servidor quebrado. Guarde a versão instalada para reproduzir o ambiente.

1. Crie resources_servers/metxbiodb/pyproject.toml com a dependência rdkit.
2. Instale o rdkit e confira se importa sem erro.

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Passo 5: registre o ambiente no YAML

Crie resources_servers/metxbiodb/configs/metxbiodb.yaml. Ele declara o servidor, o agente com no máximo dois passos e os dois conjuntos de dados, treino e validação. O nome do agente precisa ser idêntico ao que você gravou em cada linha do JSONL; um nome diferente faz o treino falhar sem mensagem clara.

Ao final, o ambiente deve aparecer na lista de recursos.

1. Crie o arquivo de registro do ambiente.
2. Confira se o ambiente aparece na lista de recursos.

```
metxbiodb:
  resources_servers:
    metxbiodb:
      entrypoint: app.py
      domain: knowledge
metxbiodb_simple_agent:
  responses_api_agents:
    simple_agent:
      entrypoint: app.py
      max_steps: 2 # submit, then one closing turn; only the first submission is scored
      resources_server: {type: resources_servers, name: metxbiodb}
      model_server: {type: responses_api_models, name: policy_model}
      datasets:
        - {name: train, type: example, jsonl_fpath: data/train.jsonl}
        - {name: validation, type: example, jsonl_fpath: data/validation.jsonl}
```

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Passo 6: conecte o ambiente ao trainer

Adicione os blocos data e env ao config do trainer, apontando para os JSONL e para o arquivo de registro do ambiente. Esse passo existe para o treino usar o ambiente verificável.

Se aparecer erro de caminho, corrija as entradas e não invente diretórios. Faça uma execução curta de teste antes do treino longo.

1. Adicione o bloco data apontando para train.jsonl e validation.jsonl.
2. Adicione o bloco env ligando o NeMo Gym e listando os dois arquivos de configuração: o do modelo de rollout e o do registro.

```
data:
  train: {dataset_name: NemoGymDataset, data_path: data/train.jsonl}
  validation: {data_path: data/validation.jsonl}
  default: {dataset_name: NemoGymDataset, env_name: nemo_gym, processor: nemo_gym_data_processor, prompt_file: null, system_prompt_file: null}
  nemo_gym:
    metxbiodb_simple_agent:
      datasets:
        train: {jsonl_fpath: data/train.jsonl}
        validation: {jsonl_fpath: data/validation.jsonl}
env:
  should_use_nemo_gym: true
  nemo_gym:
    config_paths:
      - responses_api_models/vllm_model/configs/vllm_model_for_training.yaml
      - resources_servers/metxbiodb/configs/metxbiodb.yaml
```

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Passo 7: gere traces destilados do professor

Os dois comandos consultam o Claude Sonnet 5.5, pontuam cada resposta por similaridade de Tanimoto e montam o conjunto de treino supervisionado. Esse passo existe para dar um ponto de partida melhor ao modelo menor. Com limiar de 0,7, o exemplo guardou 1.123 traces de 1.934 prompts.

Se a geração parar por chave inválida, confira a variável de ambiente e repita. Filtrar só acerto exato (Tanimoto 1,0) deixa o conjunto mais rígido; para mais variação, use limiar 0,7.

1. Exporte a chave de API do modelo professor na variável POLICY_API_KEY.
2. Gere os rollouts com generate_sft.py.
3. Construa o conjunto de treino supervisionado com build_metxbiodb_sft_messages.py.

```
export POLICY_API_KEY=<your-inference-api-key>

# Step 1: Generate rollouts from Claude Sonnet 5.5
python3 tools/generate_sft.py \
    --model anthropic/claude-sonnet-5-5 \
    --split train \
    --num-repeats 8 \
    --min-reward 0.7 \
    --out-dir runs/metxbiodb_sft_distilled

# Step 2: Build OpenAI-format SFT dataset
python3 tools/build_metxbiodb_sft_messages.py \
    --in-file runs/metxbiodb_sft_distilled/generated.jsonl \
    --out-dir metxbiodb/distilled_datasets \
    --val-frac 0.05 \
    --seed 42
```

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Passo 8: rode o SFT com LoRA

Lance o treino supervisionado com sft_metxbiodb_super_vl_lora.yaml, o config completo de SFT do ambiente, em 16 GPUs e 55 passos. Esse passo existe para aquecer o modelo antes do reforço.

Durante a execução, acompanhe a perda e o salvamento do checkpoint final, que sai consolidado no formato de pesos (safetensors). Se o treino falhar por memória, reduza o lote ou use mais GPUs. Esse checkpoint é o ponto de partida do GRPO.

1. Lance o treino supervisionado.
2. Confira o checkpoint final consolidado em safetensors.

```
# Multi-node SFT run (16 GPUs)
python examples/run_sft.py \
    --config configs/sft_metxbiodb_super_vl_lora.yaml \
    cluster.num_nodes=4 cluster.gpus_per_node=4 \
    sft.max_num_steps=55
```

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Passo 9: rode o GRPO no ambiente

Lance o treino por reforço com grpo_metxbiodb_super_vl.yaml, 16 GPUs e 100 passos, sobre a versão de 120 bilhões de parâmetros do modelo. Esse passo existe para o modelo aprender com a recompensa automática.

Para modelos de mistura de especialistas (MoE), ligue a correção por amostragem de importância (loss_fn.use_importance_sampling_correction=True), que reduz a variância entre o motor de rollout e o de treino. Se a recompensa não subir, revise o verificador e as respostas esperadas.

1. Lance o treino por reforço.
2. Confira se a recompensa sobe ao longo dos passos.

```
# Multi-node GRPO run (16 GPUs)
python examples/nemo_gym/run_grpo_nemo_gym.py \
    --config configs/grpo_metxbiodb_super_vl.yaml \
    cluster.num_nodes=4 cluster.gpus_per_node=4 \
    grpo.max_num_steps=100
```

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Exemplo completo: metabolismo de fármacos com MetxBioDB

Dado um composto inicial e sua enzima transformadora, o modelo prevê o metabólito resultante. Os exemplos usam registros do MetxBioDB, uma base abrangente de reações de biotransformação confirmadas experimentalmente.

No exemplo de destilação, a pergunta é: molécula inicial Cc1nn(C)c(Cl)c1C(O)=Nc1cccc2c1C(C)OC2(C)C, enzima CYP1A2. O modelo professor, o Claude Sonnet 5.5, raciocina sobre a N-desmetilação e envia o metabólito previsto. A verdade de base é Cc1[nH]nc(Cl)c1C(O)=Nc1cccc2c1C(C)OC2(C)C, com similaridade de Tanimoto 1,0 (correspondência exata).

O trace de raciocínio do Claude Sonnet 5.5 identifica os grupos funcionais relevantes (N-metil pirazol), descreve o mecanismo da CYP1A2 (N-desmetilação via hidroxilação do carbono alfa), indica o sítio de biotransformação (o 1-metil no nitrogênio do pirazol) e conclui com a mudança estrutural no SMILES.

Apenas traces de alta qualidade são mantidos: aqueles em que a lógica passo a passo do professor leva a um SMILES que corresponde ao metabólito de referência. Um trace é de baixa qualidade mesmo quando o raciocínio parece fluente e plausível, mas tem lógica falha que resultou na previsão errada.

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Prompt pronto: system prompt do ambiente

O prompt fixo abaixo é incluído em toda requisição e pode ser variado entre ambientes. As requisições LLM são formatadas como mensagens de chat contendo a pergunta e o prompt do sistema.

O prompt define o modelo como especialista em metabolismo de fármacos, exige raciocínio passo a passo (grupos funcionais, mecanismo, sítio, transformação, mudança estrutural) e termina com a chamada de submit_metabolite. A regra principal: o SMILES passado deve ser válido, canônico e representar o produto metabólico correto, sem texto extra no argumento.

- Se múltiplas enzimas forem listadas (separadas por ponto e vírgula), use a reação combinada ou mais provável sobre o substrato.

```
You are an expert computational chemist specializing in drug metabolism. Your task is to predict the SMILES string of the metabolite produced when a given parent compound is biotransformed by a specified enzyme or enzyme family. Response format: 1. Provide step-by-step scientific reasoning: a. Identify the functional groups in the parent compound relevant to the enzyme. b. Describe the enzyme's known reaction mechanism and regioselectivity. c. Identify the specific site of biotransformation and explain why. d. Describe the chemical transformation applied (e.g. hydroxylation, glucuronidation). e. State the resulting structural change to the parent SMILES. 2. Finish by calling the submit_metabolite tool with your predicted metabolite SMILES. Rules: - The SMILES passed to submit_metabolite must be valid, canonical, and represent the chemically correct metabolic product — no extra text in the argument. - Apply knowledge of the named enzyme's typical reaction mechanism (e.g. CYP450 hydroxylation/oxidation, UGT glucuronidation, SULT sulfation, MAO deamination, NAT acetylation, etc.). - If multiple enzymes are listed (semicolon-separated), use their combined or most likely reaction on the substrate.
```

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Configuração do modelo: política GRPO

O trecho abaixo mostra a porção de política do config do trainer GRPO. O config completo inclui configurações de rollout, servidor de recompensa e logging.

A política usa nvidia/NVIDIA-Nemotron-3.5-Super-VL-120B-A128-BF16, com precisão bfloat16, paralelismo de especialistas 4 e checkpointing de ativação.

```
policy:
  model_name: nvidia/NVIDIA-Nemotron-3.5-Super-VL-120B-A128-BF16
  tokenizer:
    - name: $(policy.model_name)
  chat_template_kwargs: null
  hf_config_overrides:
    num_next_predict_layers: 0
  train_micro_batch_size: 1
  logprob_batch_size: 1
  logprob_chunk_size: 2048
  max_total_sequence_length: 5120
  make_sequence_length_divisible_by: 256
  precision: bfloat16
  offload_optimizer_for_logprob: true
  optimizer:
    - name: transformer_engine.pytorch.optimizers.fused_adam.FusedAdam
      kwargs:
        lr: 1.0e-06
        weight_decay: 0.1
        betas: [0.9, 0.999]
        eps: 1.0e-08
        master_weights: true
        store_param_remainders: true
        exp_avg_dtype: torch.bfloat16
        exp_avg_sq_dtype: torch.bfloat16
  scheduler:
    - name: torch.optim.lr_scheduler.ConstantLR
      kwargs:
        factor: 1.0
        total_iters: 1000000000
    - milestones: []
  automodel_cfg:
    enabled: true
    tensor_parallel_size: 1
    context_parallel_size: 1
    expert_parallel_size: 4
    sequence_parallel: false
    activation_checkpointing: true
    cpu_offload: false
    moe_parallelizer:
      ignore_router_for_ac: true
      reshard_after_forward: true
    automodel_kwargs:
      backend:
        _target_: nemo_automodel.components.models.common.utils.BackendConfig
      attn: te
      linear: te
      rms_norm: torch_fp32
      experts: gmm
      dispatcher: hybridep
      fake_balanced_gate: false
      rope_fusion: false
      enable_hf_state_dict_adapter: true
```

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Configuração SFT: aquecimento no modelo estudante

O config SFT abaixo aquece o modelo estudante nos traces destilados antes do loop de reforço. Usa formato de salvamento safetensors e consolidação final. No trecho publicado, lora_cfg aparece com enabled: false, embora o nome do arquivo de configuração completo cite LoRA; confira esse ponto no seu config antes de rodar.

```
policy:
  optimizer:
    kwargs:
      lr: 1.0e-5
      weight_decay: 0.0
  automodel_cfg:
    model_save_format: safetensors
  checkpoint:
    save_consolidated: final
    consolidation_timeout_minutes: 120
  lora_cfg:
    enabled: false
```

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Código de destilação: generate_sft.py

O snippet abaixo pontua os rollouts do professor por similaridade de Tanimoto e filtra os traces para o corpus de SFT com base no limiar definido pelo usuário.

```
async def generate(row, semaphore):
    async with semaphore:
        resp = await client.responses.create(
            model=model,
            instructions=SYSTEM_PROMPT,
            input=[{"role": "user", "content": row["prompt"]}],
            tools=TOOLS,
            temperature=1.0,
        )
        predicted_smiles = None
        response_text = getattr(resp, "output_text", "") or ""
        for item in getattr(resp, "output", []):
            if (
                getattr(item, "type", None) == "function_call"
                and getattr(item, "name", None) == "submit_metabolite"
            ):
                predicted_smiles = (
                    json.loads(item.arguments).get("smiles", "").strip()
                )
                break
        valid, reward = (
            tanimoto(predicted_smiles, ground_truth)
            if predicted_smiles
            else (False, 0.0)
        )
        return {
            "id": row["id"],
            "prompt": row["prompt"],
            "response": response_text,
            "predicted_smiles": predicted_smiles,
            "reward": reward,
        }
```

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Teste de pronto

Confira se o pós-treino funcionou comparando a similaridade média de Tanimoto no conjunto de validação antes e depois do treino.

- [ ] Compare a similaridade média de Tanimoto no conjunto de validação antes e depois do treino.
- [ ] Use como referência o exemplo da NVIDIA: o SFT melhorou a acurácia em 12% e o reforço, mais 17%, no orçamento de 16.384 tokens.
- [ ] Ao comparar duas medições, confira se usou o mesmo conjunto de validação e o mesmo orçamento.
- [ ] Anote os dois valores para comparar depois.
- [ ] Confira se o ambiente aparece na lista de recursos após o registro.
- [ ] Confira se o rdkit importa sem erro.

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Erros comuns e cuidados

Veja as armadilhas mais comuns e o que conferir antes de confiar no resultado.

- Não edite o JSONL à mão: uma vírgula fora do lugar quebra o treino.
- O nome do agente no YAML precisa ser idêntico ao agent_ref.name do JSONL; um nome diferente faz o treino falhar sem mensagem clara.
- Se o treino falhar por memória, reduza o lote ou use mais GPUs.
- Se a recompensa não subir no GRPO, revise o verificador e as respostas esperadas.
- Filtrar só acerto exato (Tanimoto 1,0) deixa o conjunto mais rígido; para mais variação, use limiar 0,7.
- A destilação é opcional: use-a quando o modelo base precisa de reforço de capacidade ou quando a convergência do RL é lenta.
- A verdade de base precisa estar preenchida; sem ela o verificador não tem o que comparar.
- Os ganhos de 12% e 17% são do exemplo de metabolismo de fármacos, com orçamento de 16.384 tokens.

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Glossário

- RLVR: aprendizado por reforço com recompensas verificáveis, onde o sinal de recompensa vem dos dados, sem rotulagem humana.
- GRPO: group relative policy optimization, algoritmo de treino por reforço usado com adaptadores LoRA.
- SFT: supervised fine-tuning, treino supervisionado que aquece o modelo antes do reforço.
- LoRA: low rank adapters, adaptadores de baixo posto para ajuste fino eficiente.
- SMILES: notação textual para descrever átomos e ligações de uma molécula.
- Tanimoto: métrica de similaridade entre dois vetores binários, de 0 a 1.
- Fingerprint Morgan: representação numérica de características estruturais de uma molécula, raio 2 e 2048 bits no exemplo.
- MetxBioDB: base de dados de reações de biotransformação confirmadas experimentalmente.
- NeMo Gym: infraestrutura de ambiente de reforço da NVIDIA.
- NeMo RL: framework de pós-treino por reforço da NVIDIA.
- Trace de raciocínio: sequência de raciocínio passo a passo do modelo.
- Destilação: usar um modelo professor mais forte para gerar traces que aquecem o modelo estudante.
- MoE: mixture of experts, arquitetura de modelo com mistura de especialistas.

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Plano de 7 dias

- Dia 1: prepare o CSV experimental e confira as colunas.
- Dia 2: gere o JSONL de treino e valide as linhas.
- Dia 3: crie o servidor de recursos e adicione o rdkit.
- Dia 4: registre o ambiente no YAML e conecte ao trainer; faça execução curta de teste.
- Dia 5: gere os traces destilados do modelo professor.
- Dia 6: rode o SFT com LoRA e salve o checkpoint.
- Dia 7: rode o GRPO e confira o ganho de acurácia.

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Para onde ir depois

- Aplique a mesma receita ao seu domínio com dados experimentais próprios.
- Comece com uma tarefa estreita, valide o método de pontuação e expanda só com evidência.
- Explore o repositório NeMo Gym para montar um ambiente a partir dos seus dados.
- Explore o repositório NeMo RL para aplicar o pós-treino por reforço.
- Meça sempre antes e depois do treino.

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Além do vídeo

- A NVIDIA descreve o Nemotron Litmus-Bench V2.0 como um conjunto de dados e benchmark de código aberto de raciocínio químico, criado para treinar e avaliar modelos de linguagem e de agentes em propriedades moleculares.
- O Nemotron 3.5 Super VL faz parte do NVIDIA Nemotron for Science, coleção de modelos, dados, ferramentas e receitas para cargas de trabalho científicas com agentes.
- Segundo a NVIDIA, o laço de treino, o servidor de recompensa, o harness e os workers de rollout são autocontidos, e o mesmo fluxo se generaliza para qualquer domínio que devolva uma recompensa escalar.
- Além do SFT, os traces de alta qualidade do professor podem ajustar o modelo estudante por destilação direta on-policy.
