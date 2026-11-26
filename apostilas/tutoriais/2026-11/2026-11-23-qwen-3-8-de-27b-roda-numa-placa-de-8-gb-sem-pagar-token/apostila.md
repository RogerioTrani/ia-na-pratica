# Qwen 3.8 de 27B roda numa placa de 8 GB, sem pagar token

_2026-11-23 · tutorial_

O Qwen 3.8 é um modelo aberto da Alibaba com 27 bilhões de parâmetros e licença Apache 2.0, que você pode rodar na sua própria máquina sem pagar por token. Esta apostila mostra como escolher a versão certa para a sua placa (1 bit para 8 GB, 4 bits para RTX 3090, modelo completo para o NVIDIA DGX Spark), baixar os arquivos oficiais no Hugging Face, conferir a licença e fazer o primeiro teste com o llama.cpp. Ao final, você terá o modelo respondendo localmente e saberá quais erros evitar.

## O que você terá no fim

Ao terminar, você terá o Qwen 3.8 respondendo na sua máquina, sem cobrança por token e sem depender de um serviço remoto. O modelo é aberto, da Alibaba, com licença Apache 2.0, e pode ser usado inclusive em projetos comerciais.

O mesmo modelo de 27 bilhões de parâmetros roda em três máquinas diferentes: uma placa de vídeo de 8 GB, uma RTX 3090 usada e o NVIDIA DGX Spark. A diferença está na versão escolhida, que troca um pouco de precisão por espaço em memória.

Você também terá os comandos oficiais de download, o caminho para conferir a licença e o teste que mostra se tudo funcionou.

Fonte: <https://github.com/QwenLM/Qwen3.8>

## Como isso funciona

O Qwen 3.8 é um modelo de linguagem com visão: entende texto, imagens e vídeos. A versão de 27 bilhões de parâmetros (Qwen3.8-27B) é densa, o que significa que todos os parâmetros participam de cada resposta.

Para caber em placas pequenas, o modelo é comprimido em versões quantizadas. A quantização reduz a precisão de cada número, o que diminui o espaço ocupado em memória. A versão de 1 bit pede de 7 a 8 GB de memória, a de 4 bits pede de 16 a 19 GB e o modelo completo em BF16 ocupa 56 GB.

Os arquivos vêm no formato GGUF, lidos pelo llama.cpp, um programa em C/C++ que carrega o modelo e responde no terminal. Quem tem o NVIDIA DGX Spark pode servir o modelo completo com o vLLM, um motor de inferência de alto desempenho.

A licença Apache 2.0, listada no cartão do modelo no Hugging Face, permite uso comercial e redistribuição, desde que os avisos de licença sejam mantidos.

Fonte: <https://github.com/QwenLM/Qwen3.8>

## Antes de começar

Confira se você tem tudo o que o teste exige antes de baixar qualquer coisa. Faltar espaço em disco no meio do download é o problema mais comum.

- Uma das três máquinas: placa de vídeo com 8 GB, RTX 3090 ou NVIDIA DGX Spark (até 128 GB de memória unificada).
- Conexão com a internet para baixar o modelo.
- Espaço livre em disco: pelo menos 18 GB para a versão de 4 bits (o arquivo ocupa 17,7 GB); 7 GB para a de 1 bit; 56 GB para o modelo completo.
- O llama.cpp compilado, usado no teste final. O guia de compilação está na documentação da Unsloth.
- O cliente do Hugging Face (huggingface_hub[cli]) para rodar os comandos hf download.

Fonte: <https://unsloth.ai/docs/models/qwen3.8>

## Versões por memória

A regra vem da memória disponível, não do preço da máquina. Escolha a versão antes de baixar qualquer coisa, porque a versão errada não cabe na placa.

O erro mais comum é tentar a versão de 4 bits na placa de 8 GB. O arquivo tem 17,7 GB e não cabe. Se isso acontecer, volte e escolha a de 1 bit.

- Placa de 8 GB: versão de 1 bit (UD-IQ1_S, 6,19 GB). Pede de 7 a 8 GB de memória (VRAM mais RAM).
- RTX 3090: versão de 4 bits (UD-Q4_K_XL, 17,7 GB). Pede de 16 a 19 GB de memória.
- NVIDIA DGX Spark: modelo completo BF16 (56 GB). Roda sem cortes, com a precisão original.

Fonte: <https://unsloth.ai/docs/models/qwen3.8>

## Onde estão os arquivos

Os pesos oficiais ficam no Hugging Face. A coleção Qwen 3.8 reúne os modelos da família; o modelo de 27 bilhões está em Qwen/Qwen3.8-27B.

As versões quantizadas (1 bit e 4 bits) são publicadas pela Unsloth no repositório unsloth/Qwen3.8-27B-GGUF.

Se você não conseguir acessar o Hugging Face na sua rede ou país, o projeto indica o ModelScope como alternativa, com os mesmos modelos publicados.

- Coleção Qwen 3.8: https://huggingface.co/collections/Qwen/qwen38
- Modelo oficial Qwen3.8-27B: https://huggingface.co/Qwen/Qwen3.8-27B
- GGUF da Unsloth: https://huggingface.co/unsloth/Qwen3.8-27B-GGUF
- Alternativa ModelScope: https://modelscope.cn/collections/Qwen/Qwen38

Fonte: <https://github.com/QwenLM/Qwen3.8>

## Passo a passo

Siga na ordem. Cada item diz a ação e o resultado esperado, para você saber se deu certo.

1. Abra a página oficial do projeto no GitHub (github.com/QwenLM/Qwen3.8). Resultado esperado: a página QwenLM/Qwen3.8 abre, com a introdução e a lista de novidades, incluindo a data de lançamento da versão de 27 bilhões de parâmetros.
2. Abra a coleção do Qwen 3.8 no Hugging Face (huggingface.co/collections/Qwen/qwen38). Resultado esperado: a coleção abre com o modelo Qwen3.8-27B na lista.
3. Escolha a versão pela memória da sua máquina, conforme a seção 'Versões por memória'. Resultado esperado: você sabe qual versão baixar.
4. Baixe a versão de 1 bit (placa de 8 GB) ou a de 4 bits (RTX 3090) do repositório da Unsloth. Resultado esperado: o arquivo chega ao disco na pasta unsloth/Qwen3.8-27B-GGUF.
5. No NVIDIA DGX Spark, baixe o modelo oficial completo com hf download Qwen/Qwen3.8-27B. Resultado esperado: os arquivos do modelo são baixados e guardados no disco.
6. Confira a licença no cartão do modelo no Hugging Face (Qwen/Qwen3.8-27B). Resultado esperado: o cartão mostra a licença apache-2.0.
7. Faça uma pergunta ao modelo com o llama-cli. Resultado esperado: a resposta aparece na sua máquina, sem cobrança por token.

Fonte: <https://github.com/QwenLM/Qwen3.8>

## Comando: instalar o cliente do Hugging Face

Rode antes de qualquer download, se ainda não tiver o cliente instalado.

```
pip install -U "huggingface_hub[cli]"
```

Fonte: <https://huggingface.co/unsloth/Qwen3.8-27B-GGUF>

## Comando: baixar a versão de 1 bit

Para a placa de 8 GB. O arquivo UD-IQ1_S pesa 6,19 GB. Resultado esperado: o arquivo Qwen3.8-27B-UD-IQ1_S.gguf é baixado para a pasta unsloth/Qwen3.8-27B-GGUF.

```
hf download unsloth/Qwen3.8-27B-GGUF --local-dir unsloth/Qwen3.8-27B-GGUF --include "*UD-IQ1_S*"
```

Fonte: <https://huggingface.co/unsloth/Qwen3.8-27B-GGUF>

## Download da versão de 4 bits

Para a RTX 3090. Use o mesmo comando hf download da versão de 1 bit, trocando apenas o filtro depois de --include para "*UD-Q4_K_XL*". O arquivo UD-Q4_K_XL ocupa 17,7 GB, então o disco precisa ter esse espaço livre. Resultado esperado: o arquivo Qwen3.8-27B-UD-Q4_K_XL.gguf é baixado para a pasta unsloth/Qwen3.8-27B-GGUF.

Fonte: <https://huggingface.co/unsloth/Qwen3.8-27B-GGUF>

## Comando: baixar o modelo completo

Para o NVIDIA DGX Spark. Baixa do Hugging Face o modelo de 27 bilhões de parâmetros em BF16, com 56 GB. Resultado esperado: os arquivos do modelo são baixados e ficam guardados no disco.

```
hf download Qwen/Qwen3.8-27B
```

Fonte: <https://huggingface.co/Qwen/Qwen3.8-27B>

## Comando: testar com o llama.cpp

Com o llama.cpp compilado, roda o comando que carrega o arquivo de 4 bits e abre uma conversa no terminal. Quem está com a placa de 8 GB troca o nome do arquivo pelo de 1 bit (Qwen3.8-27B-UD-IQ1_S.gguf). Resultado esperado: o modelo carrega e a resposta aparece na sua máquina, sem cobrança por token.

```
./llama.cpp/llama-cli --model unsloth/Qwen3.8-27B-GGUF/Qwen3.8-27B-UD-Q4_K_XL.gguf --temp 1.0 --top-p 0.95 --top-k 20 --min-p 0.0
```

Fonte: <https://unsloth.ai/docs/models/qwen3.8>

## Servir no DGX Spark com o vLLM

No DGX Spark, com o modelo completo, o caminho é o servidor do vLLM, iniciado com vllm serve seguido do nome do modelo, Qwen/Qwen3.8-27B. Resultado esperado: o modelo fica disponível por uma API local.

Fonte: <https://github.com/vllm-project/vllm>

## Licença Apache 2.0

Antes de usar o modelo em um projeto, abra o cartão do modelo no Hugging Face e confira a licença. Lá está indicada a licença Apache 2.0, que permite uso comercial.

O cartão também mostra a descrição do modelo e os resultados de testes. Esse passo evita surpresa se você pretende colocar o Qwen em um produto.

Se não encontrar a licença, procure no topo da página do modelo de 27 bilhões.

- Cartão do modelo: https://huggingface.co/Qwen/Qwen3.8-27B
- Licença listada: apache-2.0

Fonte: <https://huggingface.co/Qwen/Qwen3.8-27B>

## Exemplo completo

Imagine uma pessoa com uma placa de 8 GB que quer testar o Qwen 3.8 sem gastar nada. Ela abre a página oficial no GitHub, depois a coleção no Hugging Face, escolhe a versão de 1 bit e instala o cliente do Hugging Face. Roda o comando de download com o filtro *UD-IQ1_S* e aguarda o arquivo de 6,19 GB. Confere a licença Apache 2.0 no cartão do modelo. Por fim, com o llama.cpp compilado, troca o nome do arquivo no comando de teste para Qwen3.8-27B-UD-IQ1_S.gguf e faz uma pergunta simples. A resposta aparece no terminal, sem cobrança por token.

Se a máquina fosse uma RTX 3090, o fluxo seria o mesmo trocando a versão de 1 bit pela de 4 bits (UD-Q4_K_XL, 17,7 GB) e mantendo o comando de teste original. No DGX Spark, o fluxo troca o download pelo modelo completo e o teste pelo servidor vLLM.

Fonte: <https://unsloth.ai/docs/models/qwen3.8>

## Parâmetros de geração recomendados

O modelo roda em modo de pensamento por padrão, gerando conteúdo de raciocínio antes da resposta final. Para desativar, consulte os exemplos no cartão do modelo.

Parâmetros sugeridos (modo pensamento): temperature=1.0, top_p=0.95, top_k=20, min_p=0.0, presence_penalty=0.0, repetition_penalty=1.0.

Modo instrução (sem pensamento): temperature=0.7, top_p=0.80, top_k=20, min_p=0.0, presence_penalty=1.5, repetition_penalty=1.0.

Profundidade de raciocínio ajustável com reasoning_effort: xhigh (padrão), medium ou low. O preserve_thinking vem habilitado por padrão.

Fonte: <https://huggingface.co/Qwen/Qwen3.8-27B>

## Outras formas de rodar

Além do llama.cpp, o modelo é suportado por vários frameworks de inferência e por serviços hospedados.

Transformers: transformers serve Qwen/Qwen3.8-27B --port 8000 --continuous-batching (API compatível com OpenAI em localhost:8000/v1).

SGLang: sglang serve --model-path Qwen/Qwen3.8-27B --port 8000 --tp-size 4 --context-length 262144 --reasoning-parser qwen3 --tool-call-parser qwen3_coder.

vLLM: vllm serve Qwen/Qwen3.8-27B --port 8000 --tensor-parallel-size 4 --max-model-len 262144 --reasoning-parser qwen3, além das opções de chamada de ferramentas mostradas na página do projeto.

Os exemplos de SGLang e vLLM dividem o modelo entre 4 GPUs (--tp-size 4 e --tensor-parallel-size 4); ajuste esse número ao seu hardware.

MLX para Apple Silicon (mlx-lm para texto, mlx-vlm para visão e texto). Unsloth traz interface local para rodar e treinar.

APIs hospedadas: Qwen Studio, Qoder, QwenWork, Qwen Cloud e Qwen Code.

Fonte: <https://github.com/QwenLM/Qwen3.8>

## Teste de pronto

Confira cada item para ter certeza de que tudo funcionou.

- [ ] A página QwenLM/Qwen3.8 abre no GitHub.
- [ ] A coleção no Hugging Face mostra o modelo Qwen3.8-27B.
- [ ] O arquivo baixado corresponde à versão escolhida: UD-IQ1_S (6,19 GB), UD-Q4_K_XL (17,7 GB) ou modelo completo (56 GB).
- [ ] O cartão do modelo no Hugging Face lista a licença apache-2.0.
- [ ] O comando de teste roda sem erro de memória e a resposta aparece no terminal.
- [ ] Se der erro de memória, a versão é grande demais para a placa: volte ao passo de escolha e baixe a menor.

Fonte: <https://unsloth.ai/docs/models/qwen3.8>

## Erros comuns e cuidados

Estas são as armadilhas que mais aparecem ao seguir o passo a passo.

- Tentar a versão de 4 bits na placa de 8 GB: o arquivo de 17,7 GB não cabe. Use a de 1 bit.
- Disco cheio no meio do download da versão de 4 bits: libere pelo menos 18 GB e comece de novo.
- Comando com erro: confira se o nome do repositório está exatamente como unsloth/Qwen3.8-27B-GGUF.
- Sem acesso ao Hugging Face: use o ModelScope, que publica os mesmos modelos.
- Licença não encontrada na página: procure no topo da página do modelo de 27 bilhões.
- Erro de memória no teste: a versão escolhida é grande demais para a placa. Baixe a menor e tente de novo.
- O guia da Unsloth cita o IQ1_S para outro modelo (2.4T-A95B), enquanto a página do repositório 27B-GGUF lista UD-IQ1_S, de 6,19 GB. Depois de baixar, confira se o arquivo Qwen3.8-27B-UD-IQ1_S.gguf está na pasta.

Fonte: <https://huggingface.co/unsloth/Qwen3.8-27B-GGUF>

## Glossário

Termos técnicos que aparecem no processo, com definição curta.

- Parâmetro: número ajustável que o modelo aprende durante o treinamento. O Qwen 3.8-27B tem 27 bilhões deles.
- Quantização: compressão que reduz a precisão de cada número para diminuir o espaço em memória.
- Bit (1 bit, 4 bits): nível de compressão. Menos bits, menos memória e menos precisão.
- GGUF: formato de arquivo que guarda o modelo quantizado, lido pelo llama.cpp.
- llama.cpp: programa em C/C++ que carrega e roda modelos GGUF no terminal.
- vLLM: motor de inferência de alto desempenho, usado para servir modelos completos.
- BF16: formato de 16 bits em ponto flutuante, usado no modelo completo.
- VRAM: memória da placa de vídeo, onde o modelo é carregado.
- Memória unificada: memória compartilhada entre CPU e GPU, como no DGX Spark.
- Apache 2.0: licença de software aberto que permite uso comercial e redistribuição.
- Hugging Face: site onde os pesos do modelo ficam hospedados.
- ModelScope: alternativa ao Hugging Face para baixar os mesmos modelos.
- reasoning_effort: parâmetro que ajusta a profundidade do raciocínio (xhigh, medium, low).
- preserve_thinking: recurso que mantém o contexto de raciocínio entre mensagens.
- Token: unidade de texto cobrada por serviços de IA; aqui não há cobrança.

Fonte: <https://github.com/QwenLM/Qwen3.8>

## Plano de 7 dias

Para quem prefere avançar devagar, os mesmos passos distribuídos em sete dias.

- Dia 1: abra a página oficial no GitHub e leia a introdução e as novidades.
- Dia 2: abra a coleção no Hugging Face e identifique o modelo Qwen3.8-27B.
- Dia 3: escolha a versão pela memória da sua máquina.
- Dia 4: instale o cliente do Hugging Face e baixe a versão escolhida.
- Dia 5: confira a licença Apache 2.0 no cartão do modelo.
- Dia 6: compile o llama.cpp seguindo o guia da Unsloth.
- Dia 7: rode o teste e faça uma pergunta ao modelo.

Fonte: <https://unsloth.ai/docs/models/qwen3.8>

## Para onde ir depois

Depois do primeiro teste, você pode ir além.

- Teste os parâmetros de geração (temperature, top_p) e compare as respostas.
- Experimente o modo sem pensamento (instruct) para respostas mais diretas.
- Ajuste o reasoning_effort (medium ou low) para equilibrar velocidade e qualidade.
- Explore a entrada de imagens e vídeos, já que o modelo é vision-language.
- Se tiver o DGX Spark, sirva o modelo com vLLM e conecte uma aplicação via API.
- Consulte o guia da Unsloth para treinar ou ajustar o modelo localmente.
- Conheça o llama.cpp: https://github.com/ggml-org/llama.cpp
- Conheça o vLLM: https://github.com/vllm-project/vllm
- Veja a página oficial do DGX Spark: https://www.nvidia.com/en-us/products/workstations/dgx-spark/

Fonte: <https://unsloth.ai/docs/models/qwen3.8>

## Mais sobre o modelo

- O Qwen 3.8-27B entende imagens e vídeos, além de texto (modelo vision-language).
- O contexto nativo é de 262.144 tokens, extensível até 1.000.000 com RoPE scaling.
- A família inclui o Qwen3.8-2.4T-A95B, lançado em 12 de agosto de 2026.
- A Unsloth oferece interface local para rodar e treinar o modelo.
- Formas oficiais de uso: Qwen Studio, Qoder, QwenWork, Qwen Cloud e Qwen Code.
- Benchmarks detalhados estão no cartão do modelo no Hugging Face.
- A versão GGUF da Unsloth oferece dezenas de quants, de 1 bit a 16 bits.
- O modelo suporta preserve_thinking por padrão e reasoning_effort ajustável.
- MLX permite rodar em Apple Silicon.
- TokenSpeed é mais um motor de inferência suportado.
