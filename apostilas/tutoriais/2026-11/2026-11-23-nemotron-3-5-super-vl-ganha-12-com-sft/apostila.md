# Nemotron 3.5 Super VL ganha 12% com SFT

_2026-11-23 · tutorial_

Receita da NVIDIA para pós-treinar o Nemotron 3.5 Super VL no seu domínio científico a partir de um CSV de dados experimentais. Você monta um ambiente de reforço com recompensa verificável e treina com SFT e GRPO. No exemplo de metabolismo de fármacos, o SFT elevou a acurácia em 12% e o reforço acrescentou mais 17%.

## O que você terá no fim

Você terá um ambiente de reforço com recompensa verificável, um modelo pós-treinado com SFT e GRPO, e a comparação de acurácia antes e depois.

A receita serve a qualquer domínio em que uma resposta possa receber uma nota.

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Antes de começar

O exemplo usa 16 GPUs, em 4 nós com 4 GPUs cada. O exemplo prevê metabolismo de fármacos, com registros do MetxBioDB.

- GPU NVIDIA com VRAM suficiente.
- NeMo Gym e NeMo RL clonados dos repositórios oficiais da NVIDIA.
- Python 3 e rdkit instalados.
- Chave de API do modelo professor, na variável POLICY_API_KEY.
- CSV com seus dados experimentais.

Fonte: <https://developer.nvidia.com/blog/post-training-nvidia-nemotron-to-increase-accuracy-in-your-scientific-domain/>

## Passo a passo

Siga os passos na ordem. Cada um diz a ação e o resultado esperado.

1. Crie o CSV com as colunas parent_smiles, enzyme, reaction_type e metabolite_smiles, com estes nomes exatos. Resultado: o script tem os dados que precisa.
2. Gere o train.jsonl com o script de conversão, sem editar o arquivo à mão. Resultado: uma linha por prompt, com a ferramenta e o ground truth.
3. Escreva o servidor de recursos com seed_session e verify, e instale o rdkit. Resultado: o módulo carrega sem erro. Para outro domínio, troque a função de similaridade e o schema da ferramenta.
4. Crie o config do ambiente, com o nome do agente igual ao agent_ref.name de cada linha do JSONL. Resultado: o ambiente aparece na lista de recursos.
5. Gere os traces destilados do modelo professor e mantenha só os pares que acertaram. Resultado: no exemplo, ficaram 1.123 traces de 1.934 prompts, com limiar 0.7.
6. Rode o SFT com LoRA e depois o GRPO a partir do checkpoint consolidado. Resultado: o modelo pós-treinado fica pronto para comparação.

## Teste de pronto

Compare a similaridade média de Tanimoto no conjunto de validação antes e depois do treino, usando o mesmo conjunto e o mesmo orçamento de tokens.

- [ ] No exemplo, com orçamento de 16.384 tokens, o SFT elevou a acurácia em 12%.
- [ ] O pós-treino por RL acrescentou mais 17%. Anote os dois valores para comparar com o seu domínio.

## Cuidados

Se o nome do agente não bater com o do JSONL, o treino cai sem mensagem clara.

Se a geração parar por chave inválida, confira a variável POLICY_API_KEY e repita.

Por ser um modelo MoE, ligue loss_fn.use_importance_sampling_correction=True.
