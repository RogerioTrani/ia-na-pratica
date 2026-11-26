# Motif-3 e o custo de colocar experts para trabalhar

_2026-11-25 · reportagem_

O Motif-3 reúne aproximadamente 314 bilhões de parâmetros, mas ativa 13,2 bilhões por token com uma arquitetura MoE. Esta apostila explica como os experts roteados, a atenção GDLA e a cabeça MTP se combinam para especializar respostas e reduzir o cálculo por token. Você vai entender o treino, o contexto de 262.144 tokens e os resultados dos principais benchmarks, distinguindo pontuação de teste de desempenho garantido. Também verá as diferenças entre H200 e B200, o comando publicado de implantação e os cuidados com hardware, código remoto e versões quantizadas. Ao final, você terá critérios para testar o modelo nas suas tarefas e escolher o próximo passo.

## O contexto

O Motif-3 é um modelo de linguagem decoder-only do tipo Mixture-of-Experts, criado pela Motif Technologies com design proprietário totalmente interno. A ficha oficial registra aproximadamente 314 bilhões de parâmetros no total e 13,2 bilhões ativados por token. O repositório disponibiliza os pesos para download sem pedido de acesso e informa a licença MIT.

O tamanho total descreve a quantidade de parâmetros armazenados no modelo. O número ativo indica quanto desse conjunto participa do cálculo de um token. Essa diferença permite manter um grande pool de especialistas e usar apenas uma parte dele a cada etapa da geração.

A proposta combina eficiência computacional com especialização. A ativação esparsa reduz o trabalho por token, enquanto o roteador decide quais experts devem contribuir. A qualidade depende dessa escolha: especializar bem pode melhorar a resposta, e uma seleção inadequada pode reduzir o resultado.

Fonte: <https://huggingface.co/Motif-Technologies/Motif-3>

## A arquitetura MoE

Em um modelo denso, todos os parâmetros participam do processamento de cada token. No Mixture-of-Experts, o modelo divide parte da rede em especialistas e um roteador escolhe quais deles ativar. O Motif-3 tem 384 experts roteados, seleciona oito por token e mantém um expert compartilhado.

A estrutura tem 53 camadas: duas densas e 51 MoE. As camadas densas processam o fluxo completo. Nas camadas MoE, o roteador pontua os experts disponíveis e ativa o grupo mais adequado para aquele token. Os demais parâmetros continuam armazenados, mas não entram no cálculo daquela etapa.

Os 13,2 bilhões ativados por token representam o conjunto de parâmetros que participa do processamento naquele momento. O valor não é a quantidade de experts nem o tamanho de cada expert. Ativar menos parâmetros reduz o custo computacional por token, mas não elimina a memória necessária para armazenar o modelo inteiro.

A armadilha é tratar a ativação esparsa como garantia de qualidade. Se o roteador escolher especialistas que não combinam com a tarefa, o modelo pode calcular menos e responder pior. Por isso, eficiência e especialização precisam ser avaliadas juntas.

Fonte: <https://huggingface.co/Motif-Technologies/Motif-3>

## A atenção GDLA

A atenção permite que um token consulte informações de outros tokens. Durante a geração, o modelo também precisa guardar chaves e valores de posições anteriores para não recalcular tudo. Essa memória costuma ser chamada de KV cache e cresce com o contexto processado.

O Grouped Differential Latent Attention, ou GDLA, combina atenção diferencial agrupada com a representação latente comprimida de chaves e valores do Multi-head Latent Attention. A atenção diferencial usa cabeças assimétricas de sinal e ruído, com um coeficiente dependente do token. O GDLA também inclui uma porta de saída que depende da consulta.

Segundo a ficha técnica, essa composição preserva a dinâmica expressiva da atenção diferencial e reduz bastante a necessidade de KV cache. O modelo tem 80 cabeças de consulta, 16 cabeças de chave e valor e dimensão oculta de 4.096.

Para quem trabalha com contexto longo, a consequência prática é uma representação de atenção mais compacta. O ganho descrito pela arquitetura não deve ser convertido em uma promessa de latência: velocidade e consumo de memória dependem da configuração de execução e precisam ser medidos no ambiente usado.

Fonte: <https://huggingface.co/Motif-Technologies/Motif-3>

## Expert-Specific PolyNorm e mHC

O Expert-Specific PolyNorm substitui a porta SiLU por uma normalização polinomial aprendida. Seus coeficientes são ajustados separadamente para cada expert. A ficha técnica atribui a essa peça a redução de outliers de ativação e a possibilidade de cada expert desenvolver uma especialização própria.

O modified manifold-constrained hyper-connections, ou mHC, muda a forma como os fluxos residuais se combinam. Em vez de somas residuais convencionais, ele usa uma mistura duplamente estocástica de quatro fluxos residuais paralelos, associada ao politopo de Birkhoff. O multiplicador aplicado depois do mapeamento é reduzido de 2 para 1 durante o pré-treinamento para limitar o acúmulo de outliers.

Um outlier de ativação é um valor que se afasta muito do padrão dos demais. Em uma rede profunda, esses valores podem dificultar o treinamento e o uso eficiente da memória. PolyNorm atua na normalização das ativações dos experts; o mHC organiza a combinação dos fluxos residuais.

As duas peças servem à estabilidade e à especialização, mas a ficha não apresenta um resultado numérico isolado para cada uma. Elas devem ser entendidas como partes da arquitetura, não como melhorias independentes que possam ser somadas fora do modelo.

Fonte: <https://huggingface.co/Motif-Technologies/Motif-3>

## A cabeça Multi-Token Prediction

O Multi-Token Prediction, ou MTP, aparece no Motif-3 como uma cabeça de uma camada. Durante o pré-treinamento, ela funciona como objetivo auxiliar e ajuda o modelo a antecipar tokens. Na inferência, permite a decodificação especulativa do próprio modelo.

A decodificação especulativa usa previsões para tentar adiantar parte da geração. No Motif-3, a documentação informa que a cabeça MTP integrada usa num_nextn_predict_layers=1 e que num_speculative_tokens: 1 é a configuração ideal para este modelo.

O valor 1 nessa configuração descreve o mecanismo de predição. Não é uma nota de benchmark nem uma promessa de velocidade. O efeito depende da implementação, do hardware e da carga de trabalho.

## O treino e o pós-treinamento

O Motif-3 foi pré-treinado com aproximadamente 12,5 trilhões de tokens. O conjunto inclui documentos da web, STEM, código, matemática, conteúdo multilíngue e corpora especializados por domínio. Houve ênfase adicional em coreano, conteúdo que exige raciocínio, dados jurídicos e dados financeiros.

A contagem de tokens indica o volume de texto processado no treinamento. Ela não equivale ao número de documentos, usuários ou exemplos únicos. Tokens podem representar palavras, partes de palavras, símbolos ou trechos de código, dependendo do tokenizer.

O pós-treinamento combina ajuste fino supervisionado geral, seis professores especialistas treinados por aprendizado por reforço, um professor de engenharia de software e Multi-teacher On-Policy Distillation. O resultado é um modelo unificado.

Na destilação, um modelo aluno aprende com saídas produzidas por professores. A variante on-policy usa exemplos gerados no fluxo de decisão do próprio aluno, e a versão com múltiplos professores reúne contribuições diferentes. Isso ajuda a explicar como conhecimentos de raciocínio e engenharia de software podem chegar ao mesmo modelo.

Fonte: <https://huggingface.co/Motif-Technologies/Motif-3>

## Contexto, idiomas e formato dos pesos

O Motif-3 tem contexto nativo de 262.144 tokens, apresentado como 256K. O treinamento usa paralelismo de contexto ciente de janelas. O limite é medido em tokens, não em palavras ou caracteres, e representa a janela configurada para o modelo.

O tokenizer é descrito como forte em bytes por token para inglês, coreano, código e matemática. O vocabulário tem 220.160 entradas. O modelo é multilíngue e de uso geral, com destaque para coreano e para tarefas que exigem raciocínio.

Os pesos usam bfloat16. O metadado Safetensors registra 314.841.775.750 parâmetros BF16, enquanto a página arredonda o tamanho para 315 bilhões e o resumo técnico usa aproximadamente 314 bilhões. Os arquivos são particionados e somam 629.683.982.084 bytes.

Esses números descrevem armazenamento, não a quantidade ativada por token. O repositório lista 12 quantizações e oferece o checkpoint Motif-Technologies/Motif-3-NVFP4 para quem busca uma pegada menor. Uma versão quantizada deve ser avaliada separadamente, porque seus resultados não podem ser transferidos automaticamente do checkpoint original.

Fonte: <https://huggingface.co/Motif-Technologies/Motif-3>

## Os números

Todas as avaliações do Motif-3 foram realizadas com temperatura de amostragem 1,0, top-p 0,95 e comprimento máximo de sequência de 262.144 tokens. As comparações usam pontuações reportadas nos leaderboards correspondentes.

Cada valor abaixo é uma pontuação no benchmark indicado. Os números não representam acerto geral, preço, latência ou qualidade garantida em qualquer tarefa. A leitura correta compara o mesmo teste, nas mesmas condições, e mantém o recorte de cada resultado.

- GDPVal v2: 38,7, pontuação do Motif-3 em tarefas agênticas avaliadas por esse benchmark.
- τ²-Bench Telecom: 94,7, pontuação na categoria de telecomunicações.
- τ³-Banking: 35,3, pontuação na categoria bancária.
- ITBench: 51,5, pontuação obtida apenas com o conjunto de dados público, indicado pelo asterisco na tabela.
- SWE-Bench Verified: 76,2, pontuação em resolução de problemas de engenharia de software.
- Terminal-Bench 2.1: 74,9, pontuação em problemas executados por terminal.
- SciCode: 40,6, pontuação em tarefas de código científico.
- IMOAnswerBench: 83,2, pontuação em respostas de matemática olímpica.
- Apex-Shortlist: 75,5, pontuação no benchmark de raciocínio indicado pela ficha.
- GPQA Diamond: 83,4, pontuação em questões de ciência.
- HLE: 37,0, pontuação no benchmark de conhecimento indicado pela ficha.
- CritPt: 6,6, pontuação no benchmark de raciocínio listado pela ficha.
- OmniScience — Accuracy: 30,1, medida de precisão nas respostas do teste OmniScience.
- OmniScience — Non-Hallucination: 71,6, medida de não alucinação; a ficha associa o resultado à capacidade de se abster quando a resposta não tem suporte.
- AA-LCR: 72,3, pontuação no teste de contexto longo.
- IFBench: 78,2, pontuação no teste de seguimento de instruções.

Fonte: <https://huggingface.co/Motif-Technologies/Motif-3>

## Como funciona na prática

Exemplo: imagine que uma equipe entrega ao Motif-3 um problema que exige usar ferramentas e resolver etapas por terminal. O texto da tarefa é dividido em tokens. A atenção GDLA consulta o contexto por meio de uma representação comprimida de chaves e valores.

Em cada camada MoE, o roteador escolhe oito experts roteados para trabalhar com o token, além do expert compartilhado. A normalização específica de cada expert e as conexões residuais modificadas ajudam a manter esse processamento estável. A cabeça MTP antecipa tokens e participa da decodificação especulativa durante a inferência.

Se os especialistas escolhidos combinarem com a tarefa, o modelo concentra o cálculo nas partes úteis. Se a escolha for ruim, ativar menos parâmetros não compensa a perda de qualidade. O resultado de 74,9 no Terminal-Bench 2.1 descreve aquele teste; não garante que toda tarefa de terminal será resolvida.

Fonte: <https://huggingface.co/Motif-Technologies/Motif-3>

## Linha do tempo

As datas seguem os metadados do repositório e da publicação técnica. Elas situam o conteúdo, mas não indicam quando cada etapa do treinamento aconteceu.

- 7 de agosto de 2026: data de criação registrada para o repositório Motif-Technologies/Motif-3.
- 10 de agosto de 2026: data de publicação indicada para o relatório técnico de identificação 2608.09119.
- 1º de setembro de 2026: data da última modificação registrada no repositório.
- 2026: ano informado na citação do relatório técnico do Motif-3.

Fonte: <https://huggingface.co/Motif-Technologies/Motif-3>

## Quem ganha e quem perde

A comparação muda conforme a tarefa. No τ³-Banking, o Motif-3 marca 35,3 e supera todos os outros valores apresentados. No ITBench com dados públicos, marca 51,5 e também supera os resultados listados. No Terminal-Bench 2.1, chega a 74,9, atrás de Qwen-3.7 max com 75,0 e à frente dos demais valores da tabela, incluindo Kimi-K2.6 com 65,9.

No SWE-Bench Verified, o Motif-3 empata com Kimi-K2.6 em 76,2, mas fica atrás de GLM-5.1 com 76,4, DS-v4-Pro com 77,4 e Qwen-3.7 max com 80,4. No GPQA Diamond, seus 83,4 ficam abaixo de todos os resultados comparativos apresentados. No SciCode, 40,6 fica atrás de Kimi-K2.6 e Qwen-3.7 max, ambos com 53,5, e de DS-v4-Pro com 50,0.

No IFBench, 78,2 fica atrás de MiniMax-3 com 82,9 e de Qwen-3.7 max com 79,1. No OmniScience, a precisão de 30,1 convive com a medida de não alucinação de 71,6. Esses dois valores precisam ser lidos juntos, porque responder corretamente e reconhecer quando não há suporte são objetivos diferentes.

Quem tende a ganhar é quem procura um modelo aberto para tarefas agênticas, uso de ferramentas, terminal e contexto longo, além de equipes com infraestrutura compatível. Quem perde é quem espera um provedor hospedado já disponível, hardware modesto ou uma liderança única em todos os benchmarks. A página informa que o modelo não está implantado por nenhum Inference Provider, e a execução recomendada foi testada em GPUs B200 e H200.

Fonte: <https://huggingface.co/Motif-Technologies/Motif-3>

## O que ainda não se sabe

Os números de parâmetros não determinam preço, latência ou consumo energético. A ativação de 13,2 bilhões por token reduz o cálculo em relação ao total, mas o custo real depende da infraestrutura, do paralelismo, da quantização e da carga. Uma medição própria é necessária para comparar eficiência.

Os resultados de benchmark mantêm o recorte de cada teste. No registro de Terminal-Bench 2.1, a página não nomeia um harness ou agente específico e usa as configurações gerais de amostragem. Os registros de avaliação exibidos no repositório aparecem marcados como não verificados pela plataforma. Isso não invalida os números, mas pede leitura atenta das condições.

O comando publicado inclui --trust-remote-code. Essa opção permite executar código remoto e deve ser usada apenas com o repositório oficial do projeto. A disponibilidade aberta dos pesos e a licença MIT não eliminam a necessidade de hardware adequado nem o trabalho de revisar a execução.

O checkpoint NVFP4 oferece uma pegada de armazenamento menor. Já a block-fp8 é uma quantização online, ativada ao servir o modelo com --quantization modelopt_blockfp8. Os resultados do modelo original não se transferem automaticamente para versões quantizadas. Da mesma forma, a capacidade de se abster em avaliações sensíveis a alucinação não garante que toda resposta será correta. Contexto longo e bons benchmarks continuam exigindo testes com as tarefas reais do usuário.

- Não converta 314 bilhões de parâmetros totais em 314 bilhões ativos por token; os valores descrevem coisas diferentes.
- Não trate 315 bilhões, o arredondamento da página, como um número incompatível com os aproximadamente 314 bilhões do resumo técnico.
- Não leve uma pontuação de um benchmark para outro produto, checkpoint ou configuração sem repetir o teste.
- Não presuma suporte a qualquer GPU apenas porque os pesos podem ser baixados; a documentação recomenda vLLM e informa testes em B200 e H200.
- Não confunda a configuração de um token especulativo com uma medição de velocidade.

Fonte: <https://huggingface.co/Motif-Technologies/Motif-3>

## O que você pode fazer

O caminho começa pela página oficial e termina com um teste na sua tarefa. Os comandos de servidor estão nas duas seções seguintes, separados por hardware.

1. Abra https://huggingface.co/Motif-Technologies/Motif-3 e identifique o modelo, a licença MIT e o acesso sem solicitação; o resultado esperado é localizar a ficha oficial e os arquivos de pesos.
2. Leia o resumo do modelo e confirme a diferença entre aproximadamente 314 bilhões de parâmetros totais e 13,2 bilhões ativados por token; o resultado esperado é escolher o checkpoint com base no objetivo, não apenas pelo tamanho total.
3. Se precisar de uma pegada menor, avalie o checkpoint oficial Motif-Technologies/Motif-3-NVFP4; o resultado esperado é uma opção quantizada para teste, mantendo a avaliação separada do modelo original.
4. Escolha o vLLM recomendado, o fork público MotifTechnologies/vllm baseado na vLLM v0.26.0 ou a imagem ghcr.io/motiftechnologies/vllm:v0.26.0-motif3; o resultado esperado é um ambiente com suporte ao Motif-3.
5. Confirme se o ambiente corresponde ao exemplo de H200 ou B200; o resultado esperado é usar o comando publicado para a placa correta.
6. Inicie o servidor com o comando da seção correspondente e mantenha os parsers motif; o resultado esperado é um serviço disponível na porta 8080 com suporte a ferramentas e raciocínio.
7. Teste uma tarefa que represente seu uso real e registre qualidade, latência e memória; o resultado esperado é uma decisão baseada no seu cenário, além das pontuações de benchmark.

Fonte: <https://huggingface.co/Motif-Technologies/Motif-3>

## Como servir no H200

A documentação recomenda o vLLM e informa que o modelo foi testado em GPUs H200. O comando abaixo usa quantização block-fp8, decodificação especulativa com um token, paralelismo de dados e paralelismo de experts.

A configuração mantém o comprimento máximo em 262.144 tokens, usa bfloat16 e define a fração de memória de GPU como 0,85. Os parsers motif tratam chamadas de ferramentas e raciocínio. O serviço é exposto no endereço 0.0.0.0, na porta 8080.

1. Em um ambiente com GPUs H200, execute o comando publicado no terminal; o resultado esperado é o servidor vLLM iniciar com paralelismo de dados configurado para 8.
2. Mantenha --enable-expert-parallel junto com a configuração de dados; o resultado esperado é distribuir o processamento dos experts entre os recursos disponíveis.
3. Mantenha --tool-call-parser motif e --reasoning-parser motif; o resultado esperado é interpretar chamadas de ferramentas e separar a saída de raciocínio.
4. Acesse o serviço pela porta 8080; o resultado esperado é encontrar o endpoint iniciado pelo comando.

```
vllm serve "Motif-Technologies/Motif-3" \
--trust-remote-code \
--quantization modelopt_blockfp8 \
--speculative-config '{"model": "Motif-Technologies/Motif-3", "num_speculative_tokens": 1}' \
--tensor-parallel-size 1 \
--data-parallel-size 8 \
--data-parallel-size-local 8 \
--enable-expert-parallel \
--enable-auto-tool-choice \
--tool-call-parser motif \
--reasoning-parser motif \
--dtype bfloat16 \
--gpu-memory-utilization 0.85 \
--max-model-len 262144 \
--block-size 128 \
--attention-backend FLASH_ATTN_MLA \
--host 0.0.0.0 --port 8080
```

Fonte: <https://huggingface.co/Motif-Technologies/Motif-3>

## Como servir no B200

O exemplo para B200 mantém quase toda a configuração do H200. A diferença visível é a ausência da opção --attention-backend FLASH_ATTN_MLA no comando publicado para B200.

A quantização, a decodificação especulativa, o paralelismo de experts, os parsers motif e o limite de 262.144 tokens continuam iguais. O serviço também é exposto na porta 8080.

1. Em um ambiente com GPUs B200, execute o comando publicado no terminal; o resultado esperado é o servidor iniciar com a configuração específica divulgada para essa plataforma.
2. Preserve a ausência de --attention-backend FLASH_ATTN_MLA neste exemplo; o resultado esperado é seguir exatamente a variante B200 da documentação.
3. Mantenha os parsers motif e a decodificação especulativa com num_speculative_tokens: 1; o resultado esperado é habilitar ferramentas, raciocínio e a cabeça MTP integrada.
4. Acesse o serviço pela porta 8080; o resultado esperado é confirmar que o endpoint ficou disponível.

```
vllm serve "Motif-Technologies/Motif-3" \
--trust-remote-code \
--quantization modelopt_blockfp8 \
--speculative-config '{"model": "Motif-Technologies/Motif-3", "num_speculative_tokens": 1}' \
--tensor-parallel-size 1 \
--data-parallel-size 8 \
--data-parallel-size-local 8 \
--enable-expert-parallel \
--enable-auto-tool-choice \
--tool-call-parser motif \
--reasoning-parser motif \
--dtype bfloat16 \
--gpu-memory-utilization 0.85 \
--max-model-len 262144 \
--block-size 128 \
--host 0.0.0.0 --port 8080
```

Fonte: <https://huggingface.co/Motif-Technologies/Motif-3>

## Teste de pronto

Use estas verificações depois de iniciar o servidor. Elas confirmam a configuração e o funcionamento básico; a qualidade do modelo continua sendo testada nas suas tarefas.

- [ ] Servidor: o serviço responde na porta 8080 definida pelo comando.
- [ ] Modelo: a identificação exibida corresponde a Motif-Technologies/Motif-3.
- [ ] Ferramentas: uma chamada de ferramenta é reconhecida pelo parser motif.
- [ ] Raciocínio: a saída de raciocínio é separada pelo reasoning-parser motif.
- [ ] Especulação: a configuração registra num_speculative_tokens: 1 e a cabeça MTP integrada está habilitada.
- [ ] Contexto: uma entrada dentro do limite de 262.144 tokens é aceita, e uma entrada acima do limite é recusada pela configuração.
- [ ] Comparação: ao reproduzir a avaliação publicada, a temperatura 1,0 e o top-p 0,95 são mantidos, com comprimento máximo de sequência de 262.144 tokens.

Fonte: <https://huggingface.co/Motif-Technologies/Motif-3>

## Glossário

- Parâmetro: valor ajustado durante o treinamento e usado nos cálculos do modelo.
- Token: unidade de texto processada pelo modelo, que pode representar uma palavra, parte de uma palavra, símbolo ou trecho de código.
- Modelo denso: arquitetura em que todos os parâmetros participam do processamento de cada token.
- MoE: Mixture-of-Experts, arquitetura que divide parte da rede em especialistas e ativa apenas alguns por token.
- Expert: sub-rede especializada que processa tokens selecionados pelo roteador.
- Roteador: componente que decide quais experts recebem cada token.
- Top-8: seleção dos oito experts com maior pontuação do roteador para um token.
- Shared expert: expert adicional que participa do processamento junto dos experts roteados.
- Decoder-only: modelo que gera texto sequencialmente, prevendo o próximo token a partir do contexto anterior.
- Atenção: mecanismo que permite ao modelo consultar informações de outras posições do texto.
- KV cache: memória que guarda chaves e valores de posições anteriores durante a geração.
- GDLA: Grouped Differential Latent Attention, atenção que combina atenção diferencial agrupada e representação latente comprimida.
- MLA: Multi-head Latent Attention, atenção baseada em uma representação latente comprimida de chaves e valores.
- Expert-Specific PolyNorm: normalização polinomial com coeficientes aprendidos separadamente para cada expert.
- Outlier de ativação: valor de ativação que se afasta bastante do padrão dos demais.
- Fluxo residual: caminho que leva adiante parte da informação anterior e ajuda o treinamento de redes profundas.
- mHC: modified manifold-constrained hyper-connections, mistura modificada de fluxos residuais paralelos.
- MTP: Multi-Token Prediction, cabeça auxiliar usada para antecipar tokens e apoiar a decodificação especulativa.
- Decodificação especulativa: técnica que usa previsões para tentar adiantar a geração de tokens.
- Quantização: representação dos pesos com menos precisão para reduzir o espaço de armazenamento.
- bfloat16: tipo numérico de ponto flutuante de 16 bits usado nos pesos do modelo.
- Aprendizado por reforço: treinamento em que o comportamento é ajustado a partir de sinais de recompensa.
- Destilação: processo em que um modelo aluno aprende com as saídas de um ou mais modelos professores.
- Benchmark: teste padronizado usado para comparar desempenho em uma tarefa específica.
- Contexto: quantidade de tokens que o modelo pode considerar em uma sequência.

Fonte: <https://huggingface.co/Motif-Technologies/Motif-3>

## Para onde ir depois

Comece pelo modelo oficial e leia o relatório técnico em https://arxiv.org/abs/2608.09119 para aprofundar a arquitetura. Depois, escolha uma tarefa que represente seu trabalho, como uso de ferramentas, terminal, código ou contexto longo, e teste o Motif-3 com a configuração publicada.

Se o seu objetivo é executar o modelo, confirme a infraestrutura B200 ou H200 e siga o comando correspondente. Se o seu objetivo é reduzir armazenamento, avalie o checkpoint NVFP4 oficial. Em qualquer caminho, compare tarefas equivalentes e registre os resultados do seu ambiente.

- Pratique com uma tarefa de uso de ferramentas e observe se o parser motif reconhece as chamadas.
- Pratique com uma tarefa de terminal e separe o resultado específico da sua tarefa da pontuação do Terminal-Bench 2.1.
- Pratique com um contexto longo dentro do limite de 262.144 tokens e registre a qualidade da resposta.
- Compare o checkpoint original e uma versão quantizada apenas depois de executar os mesmos testes em ambos.
- Use a ficha oficial e o fork MotifTechnologies/vllm como referência para atualizações de implantação.

Fonte: <https://huggingface.co/Motif-Technologies/Motif-3>

## Além do vídeo

- O repositório traz um template de chat próprio com blocos para mensagens de sistema, usuário, assistente, ferramentas e raciocínio.
- O modelo base listado é Motif-Technologies/Motif-3-Base, e o Motif-3 aparece como ajuste fino derivado dele.
- A ficha técnica identifica a classe customizada modeling_motif.MotifForCausalLM no ecossistema Transformers.
- A demonstração de chat do repositório inclui exemplos de matemática, fatos sobre o universo e explicação de computação quântica.
