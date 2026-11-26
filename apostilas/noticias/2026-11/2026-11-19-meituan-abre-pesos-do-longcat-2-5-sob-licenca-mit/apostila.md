# Meituan abre pesos do LongCat-2.5 sob licença MIT

_2026-11-19 · noticia_

O LongCat-2.5 reúne pesos abertos, leitura de imagens e vídeo e execução de tarefas de programação em várias etapas. A Meituan publicou o checkpoint em 9 de novembro de 2026, sob licença MIT, uma semana após apresentar o modelo multimodal. A arquitetura tem 1,6 trilhão de parâmetros no total e aproximadamente 48 bilhões ativos por token. Os resultados mostram salto grande sobre o LongCat-2.0, mas a posição diante dos rivais varia por tarefa e configuração de teste. A API tem tarifa por tempo limitado e o download completo exige aproximadamente 3,56 TB. Ao final, você saberá criar uma chave, calcular o custo por tokens, comparar modelos nas mesmas condições e escolher entre API e auto-hospedagem.

## O fato

Em 9 de novembro de 2026, a Meituan publicou no Hugging Face o checkpoint do LongCat-2.5, uma semana após apresentar o modelo. A empresa chinesa de entrega de comida e e-commerce liberou os pesos sob licença MIT. O LongCat-2.5 é multimodal e voltado a tarefas agênticas de longa duração, com foco em programação, construção de projetos e trabalho em bases de código.

Ele pode receber screenshots, imagens ou vídeo, interpretar essas informações junto com texto e usar ferramentas para escrever ou revisar software em várias etapas. Os pesos ficam disponíveis para download, modificação e redistribuição, respeitados os avisos da licença. A API hospedada é outro caminho de acesso, com preços e condições próprios.

Fonte: <https://venturebeat.com/technology/meituan-releases-the-open-weights-of-its-longcat-2-5-llm-with-vision-under-a-permissive-mit-license>

## Por que isso importa

Separar leitura de tela e correção de código pode transformar uma tarefa em vários sistemas. O LongCat-2.5 alinha informação visual e texto em um espaço semântico compartilhado, permitindo que a imagem participe da mesma sequência de trabalho que a instrução e o código. Isso interessa a quem depura interfaces, transforma referências visuais em páginas ou investiga um repositório a partir de evidências na tela.

Os pesos abertos permitem avaliar uma execução privada; a API evita operar o checkpoint enorme. O argumento econômico depende do trabalho: tokens baratos ajudam, mas retentativas, tempo de sandbox e revisão de patches também entram na conta. Benchmark orienta a escolha de tarefas e não mede o custo final em qualquer projeto.

Fonte: <https://venturebeat.com/technology/meituan-releases-the-open-weights-of-its-longcat-2-5-llm-with-vision-under-a-permissive-mit-license>

## Um modelo multimodal de mistura de especialistas

O LongCat-2.5 usa arquitetura de mistura de especialistas, ou MoE. A descrição técnica informa 1,6 trilhão de parâmetros no total e aproximadamente 48 bilhões ativados por token. Cada token passa por uma fração da rede, escolhida pelo roteamento entre especialistas. A inferência calcula menos parâmetros do que exigiria a passagem por toda a rede a cada token.

Esse número ativo não reduz o arquivo necessário para servir o modelo. Todos os pesos continuam no checkpoint. O dimensionamento também precisa considerar formato de precisão, buffers de execução e memória usada para manter o contexto.

O modelo aceita modo de pensamento ligado e desligado. A documentação indica o modo ligado para melhor desempenho, com opção de preservar o raciocínio no histórico, e o desligado para usar menos tokens. Essa escolha deve entrar no teste de custo e qualidade.

Fonte: <https://huggingface.co/meituan-longcat/LongCat-2.5>

## Como a visão entra no trabalho de programação

A entrada visual é nativa. A Meituan converte características de imagens em resolução nativa em tokens discretos e as alinha com o texto em um espaço semântico compartilhado. O guia da API aceita screenshots, gráficos, imagens e vídeos. Imagens podem ser incorporadas à requisição ou enviadas por URL; a interface de vídeo documentada usa URL, o que exige planejar o acesso a gravações internas.

O caso mais promissor combina julgamento visual e programação: localizar componentes em um repositório, propor uma correção e verificar a página renderizada. A Meituan destacou demos de desenvolvedores (site de lançamento de carro, interface de jogo de fantasia e site de gestão de loja) e exemplos próprios, como uma simulação fluida interativa e uma exposição 3D. Uma loja de produção ainda precisa passar pelas verificações funcionais, de acessibilidade e de manutenção aplicáveis a código humano.

Fonte: <https://venturebeat.com/technology/meituan-releases-the-open-weights-of-its-longcat-2-5-llm-with-vision-under-a-permissive-mit-license>

## O salto sobre o LongCat-2.0

A comparação mais direta é com o LongCat-2.0. No Terminal Bench v2.1, o LongCat-2.5 marcou 88,4 contra 70,8. No DeepSWE v1.1, foram 64,6 contra 9,7. No SWE Atlas de perguntas sobre a base de código, passou de 33,1 para 58,3. Os resultados justificam repetir avaliações de repositório feitas com a versão anterior.

As notas têm configurações próprias. O Terminal Bench v2.1 usou Claude Code v2.1.280, limite de sequência de 512 mil tokens e média de três execuções. O DeepSWE v1.1 usou mini-swe-agent, limite de 1 milhão de tokens e média de três execuções. A ficha técnica separa resultados internos de notas públicas marcadas com asterisco e chama os internos de indicativos. Repita as tarefas com o mesmo repositório, ferramentas e orçamento.

Fonte: <https://huggingface.co/meituan-longcat/LongCat-2.5>

## A comparação com os rivais é mista

Contra modelos pagos, o quadro varia. No Terminal Bench v2.1, o LongCat-2.5 ficou a menos de um ponto de GPT-5.6 Sol, com 88,8, e de Claude Opus 5, com 89,1. Na v4.0, marcou 38,5 contra 53,9 do Opus 5. O DeepSeek-V4.1-Flash teve 74,2 no DeepSWE v1.1, acima dos 64,6 do LongCat-2.5. No Vision2Web, o Opus 5 marcou 80,2 contra 78,6; no 3DCodeBench, o LongCat-2.5 teve 55,4 e liderou o grupo formado por ele, GPT-5.6 Sol, Claude Opus 5 e DeepSeek-V4.1-Flash.

A Meituan escolheu referências da geração anterior enquanto GPT-6.1 Sol e Opus 5.5 já estavam disponíveis. Na v4.0, os resultados de leaderboard desses sucessores foram 58,2 e 64,8, com esforço máximo e ferramentas Codex e Claude Code. A configuração diferente impede um confronto limpo. A tabela da Meituan também deixa o sufixo do checkpoint DeepSeek em aberto; a documentação da DeepSeek identifica o endpoint Flash como 1017. Para um teste, use os sucessores como controles e avalie GPT-6 Astra ou Claude Fable 5.2 como opção de escalonamento nos casos difíceis.

Fonte: <https://venturebeat.com/technology/meituan-releases-the-open-weights-of-its-longcat-2-5-llm-with-vision-under-a-permissive-mit-license>

## Pesos abertos sob licença MIT

A licença MIT permite uso comercial, modificação e redistribuição dos pesos, sujeitos à preservação dos avisos da licença. Ela não concede direitos sobre marcas ou patentes da Meituan. Isso permite integrar o modelo a produtos e adaptar os pesos.

O download e a API hospedada são decisões separadas. A MIT cobre os pesos; o serviço tem condições comerciais e de tratamento de dados próprias. Quem quer alterar o modelo ou controlar a execução pode avaliar auto-hospedagem. Um protótipo ocasional pode começar pela API.

Fonte: <https://huggingface.co/meituan-longcat/LongCat-2.5>

## A API e a criação da chave

O nome exato do modelo na API é LongCat-2.5. A plataforma informa compatibilidade com OpenAI na rota /v1/chat/completions e com Anthropic na rota /v1/messages, ambas em https://longcat.chat. A documentação registra janela de contexto de 1 milhão de tokens e saída máxima de 256 mil tokens.

1. Crie uma conta na LongCat API Platform e faça login; o resultado é o acesso à configuração da API.
2. Abra a página API Keys e clique em Create API Key; a plataforma exibirá o valor da chave uma vez.
3. Guarde o valor antes de fechar a tela; sem ele, será preciso gerar outra chave.
4. Selecione LongCat-2.5 na configuração do cliente e envie a chave no cabeçalho Authorization; a requisição usará o modelo correto.

```
Authorization: Bearer YOUR_APP_KEY
```

Fonte: <https://longcat.chat/platform/docs/>

## O preço da API e uma rodada de exemplo

A tarifa por tempo limitado é de US$ 0,30 por milhão de tokens de entrada sem cache, US$ 0,006 por milhão de entrada em cache e US$ 1,20 por milhão de saída. A documentação não divulga data de encerramento e avisa que os preços estão sujeitos a alterações.

Exemplo: 200 mil tokens de entrada sem cache e 100 mil de saída custam US$ 0,18 em tokens do LongCat-2.5.

O exemplo fica abaixo do limite em que o GPT-6.1 Sol cobra tarifa mais alta e mantém o volume fixo. Ele não mede o custo por resultado aceito. Raciocínio, chamadas repetidas e novas tentativas podem mudar o total. Some tempo de sandbox, eventuais modelos de reserva e revisão humana. Para agentes que reenviam contexto, meça a taxa real de acerto do cache; o tamanho da janela de contexto não define a conta. Com os mesmos volumes, os valores publicados na comparação são os seguintes.

- O DeepSeek-V4.1-Flash fora do pico custa US$ 0,09 para essa rodada.
- O LongCat-2.5 custa US$ 0,18 para essa rodada.
- O GPT-6.1 Sol custa US$ 1,40 para essa rodada.
- O Claude Opus 5.5 custa US$ 2,80 para essa rodada.
- O Claude Fable 5.2 custa US$ 5,60 para essa rodada.
- O GPT-6 Astra custa US$ 7 para essa rodada.

Fonte: <https://venturebeat.com/technology/meituan-releases-the-open-weights-of-its-longcat-2-5-llm-with-vision-under-a-permissive-mit-license>

## Baixar e dimensionar o checkpoint

O checkpoint completo aparece no Hugging Face em 208 arquivos .safetensors, em precisão BF16 / F32, somando aproximadamente 3,56 TB. O download via CLI do Hugging Face usa o comando abaixo. A Meituan também publicou meituan-longcat/LongCat-2.5-W4A4, versão quantizada em 4 bits para reduzir armazenamento e memória.

Baixar é só o começo. O runtime precisa carregar o formato dos pesos, e todos os especialistas precisam estar disponíveis, embora apenas 48 bilhões de parâmetros participem de cada token. Memória de execução e contexto também contam no dimensionamento.

Os metadados do Hugging Face exibem 1,8 trilhão de parâmetros, enquanto a descrição técnica informa 1,6 trilhão. Uma estimativa hipotética de dois bytes por parâmetro em 16 bits daria cerca de 3,2 TB apenas para pesos, sem buffers nem contexto. Esse cálculo é ilustrativo; use os arquivos e o formato de serviço reais para dimensionar.

```
hf download meituan-longcat/LongCat-2.5
```

Fonte: <https://huggingface.co/meituan-longcat/LongCat-2.5/tree/main>

## Auto-hospedagem: o que a documentação cobre

A ficha técnica direciona a implantação oficial para plataformas NPU e aponta o SGLang-FluentLLM. As otimizações publicadas pela Meituan foram testadas em aceleradores chineses.

O repositório público informa que o motor foi testado em GPUs Nvidia H800/H20, mas removeu o suporte multimodal da versão pública. Na arquitetura desacoplada, ele atua como backbone de texto. Há exemplos gerais de início rápido, sem comando oficial de lançamento para os pesos do LongCat-2.5 em GPU.

Antes de hospedar, valide se o runtime carrega o checkpoint e preserva visão e uso de ferramentas. Depois, meça requisições longas em paralelo, tempo de resposta e comportamento sob carga. A API facilita protótipos ocasionais; uma carga grande ou sensível pode justificar a pilha privada.

Fonte: <https://github.com/meituan-longcat/SGLang-FluentLLM>

## O treinamento e as otimizações por trás do modelo

O treinamento combina contexto longo, aprendizado por reforço e vários professores. O reforço agêntico de longa duração usa tarefas reais de engenharia e falhas reproduzíveis de agentes, com proteções contra reward hacking. O objetivo é melhorar a execução completa da tarefa.

Professores especializados em agir, raciocinar e interagir guiam o modelo por destilação de conhecimento em todo o vocabulário e atenção em estrutura de árvore. A infraestrutura mantém as probabilidades logarítmicas dos tokens idênticas bit a bit entre treinamento, prefill e decodificação. Nas tarefas SFT de sequência longa reportadas, a vazão por dispositivo foi 86% maior que a linha de base DDP. A otimização do cache KV, junto com a LSA, quase dobrou a capacidade de decodificação sem aumentar TPOT na carga testada.

A quantização W4A4 reduz pesos e ativações dos especialistas para 4 bits e permite cálculo INT4 nativo em aceleradores chineses. A Meituan afirma precisão comparável à do modelo sem quantização nos benchmarks avaliados. Em testes de estresse online contra uma base MoE W8A8, houve 43,3% mais vazão de prefill, 42,77% mais vazão de decodificação, 15,91% menos TTFT e 19,72% menos TPOT. Os kernels de GEMM agrupado tiveram aceleração média de 1,73 vezes sobre a base W8A8. Com cache KV quantizado, W4A4KV8 entregou 92% mais vazão de decodificação que W8A8KV16. Esses resultados valem para as cargas testadas.

Fonte: <https://huggingface.co/meituan-longcat/LongCat-2.5>

## Os números

Os valores abaixo medem tamanho, desempenho, preço e infraestrutura. Cada um precisa ser lido com sua unidade e comparação.

- O modelo tem 1,6 trilhão de parâmetros totais e aproximadamente 48 bilhões ativos por token; o cálculo usa uma fração da rede, mas servir o modelo exige o checkpoint completo.
- O checkpoint no Hugging Face reúne 208 arquivos e aproximadamente 3,56 TB, sem contar memória de execução e contexto.
- O LongCat-2.5 marcou 88,4 contra 70,8 do LongCat-2.0 no Terminal Bench v2.1 e 64,6 contra 9,7 no DeepSWE v1.1.
- O LongCat-2.5 marcou 38,5 contra 53,9 do Claude Opus 5 no Terminal Bench v4.0, na tabela da Meituan.
- A tarifa por tempo limitado cobra US$ 0,30 por milhão de entrada sem cache, US$ 0,006 por milhão de entrada em cache e US$ 1,20 por milhão de saída.
- A rodada com 200 mil tokens de entrada sem cache e 100 mil de saída custa US$ 0,18 só em tokens do LongCat-2.5.
- A documentação da API informa janela de contexto de 1 milhão de tokens e saída máxima de 256 mil tokens.
- A vazão por dispositivo foi 86% maior que a linha de base DDP nas tarefas SFT de sequência longa reportadas, sem formar uma medida universal.

Fonte: <https://huggingface.co/meituan-longcat/LongCat-2.5>

## O que muda para você

O uso mais claro aparece quando a tarefa exige ver e programar. Uma equipe de frontend pode começar por uma regressão visual com correção conhecida. O agente recebe a captura com falha, acesso a um repositório de teste e uma forma de renderizar a página alterada. O trabalho é localizar a causa, fazer uma mudança pontual e preservar navegação por teclado e comportamento responsivo.

Exemplo: imagine um checkout quebrado em uma captura de tela. O desenvolvedor entrega a imagem e pede que o agente encontre os componentes relacionados no repositório, proponha um patch e confira o resultado no navegador. A avaliação separa a tela renderizada do código: é preciso verificar a aparência, a correção da causa e possíveis danos a outras funções. Para manutenção pesada de texto, o DeepSeek é um comparador útil; para falhas caras ou revisões demoradas, mantenha um modelo mais forte como reserva.

Fonte: <https://venturebeat.com/technology/meituan-releases-the-open-weights-of-its-longcat-2-5-llm-with-vision-under-a-permissive-mit-license>

## O que fazer hoje

Comece pela API com artefatos públicos ou sintéticos. O objetivo é descobrir se o LongCat-2.5 melhora um fluxo que a equipe já usa.

Se o modelo concluir mais trabalho visual dentro da revisão e com custo total menor, direcione esse fluxo para ele. A compra de um cluster pode esperar até o teste mostrar a frequência e o valor da vantagem.

1. Escolha uma correção guiada por screenshot, uma tarefa de design para código e uma tarefa de repositório apenas com texto como controle; assim, o teste separa o ganho visual do ganho em programação.
2. Prepare o mesmo repositório, navegador, suíte de testes, permissões de ferramentas e limite de tempo para cada modelo; cada um enfrentará as mesmas condições.
3. Crie a conta, gere a chave em API Keys e selecione LongCat-2.5; você terá acesso autenticado para executar o teste.
4. Registre tokens, chamadas de ferramenta, retentativas e tempo de sandbox; o registro mostrará o custo observado de cada tentativa.
5. Avalie a tela renderizada e o código separadamente; nas correções, verifique a causa e o trabalho que o revisor precisa refazer.
6. Repita algumas tarefas e calcule o custo por resultado aceito, incluindo revisão humana e eventuais chamadas de reserva; a decisão de ampliar o uso terá uma base concreta.

Fonte: <https://venturebeat.com/technology/meituan-releases-the-open-weights-of-its-longcat-2-5-llm-with-vision-under-a-permissive-mit-license>

## O que conferir

Antes de enviar código ou screenshots proprietários à API, estabeleça como o serviço trata retenção, acesso e exclusão. Use um sandbox com artefatos públicos ou sintéticos no primeiro teste. A MIT cobre os pesos e não substitui as condições do serviço.

Para quem atende ao governo dos Estados Unidos, o local de execução e a permissão contratual são questões separadas. Em outubro de 2026, o Departamento de Segurança Interna divulgou uma ordem para excluir o DeepSeek da contratação de agências civis federais e remover sua tecnologia de sistemas cobertos, inclusive por terceiros. A ordem mira o DeepSeek e suas afiliadas. A VentureBeat informou que, até 9 de novembro de 2026, não havia restrição federal norte-americana publicamente divulgada que nomeasse a Meituan ou o LongCat-2.5. As regras podem mudar.

- Preserve os avisos da licença MIT e não trate a licença dos pesos como direito sobre marcas ou patentes da Meituan.
- Confira os preços vigentes e a taxa real de cache; a tarifa é por tempo limitado e não tem data de encerramento divulgada.
- Valide visão e uso de ferramentas no runtime; o repositório público não traz comando oficial de GPU para o LongCat-2.5.
- Compare benchmarks com o mesmo harness, ferramentas, permissões, tempo e orçamento; resultados internos e públicos podem usar configurações diferentes.
- Verifique contratos e ordens federais aplicáveis antes de trabalho governamental; auto-hospedagem ou nuvem controlada pela empresa não elimina essa checagem.
- Mantenha um segundo modelo testado nas mesmas tarefas para evitar reconstruir o fluxo se a elegibilidade mudar.

Fonte: <https://venturebeat.com/technology/meituan-releases-the-open-weights-of-its-longcat-2-5-llm-with-vision-under-a-permissive-mit-license>

## Glossário

- Token: unidade de informação processada pelo modelo, como um trecho de texto ou um recurso visual.
- Parâmetro: valor aprendido no treinamento; os parâmetros ativos são a parte usada no cálculo de um token.
- Checkpoint: conjunto de pesos e arquivos usado para carregar o modelo.
- MoE: arquitetura de mistura de especialistas, em que cada token usa uma fração da rede.
- Inferência: execução do modelo para gerar uma resposta.
- Multimodal: capacidade de processar tipos diferentes de informação, como texto e imagem.
- Agente: sistema que combina modelo e ferramentas para executar uma tarefa em etapas.
- API: interface usada por software para enviar requisições ao modelo.
- Cache de entrada: reaproveitamento de tokens já processados para reduzir o custo de entradas repetidas.
- Contexto: conjunto de tokens disponível em uma execução, incluindo instruções, histórico e dados da tarefa.
- Benchmark: teste definido para comparar desempenho em uma tarefa.
- Harness: ambiente que organiza ferramentas, limites e avaliação de um benchmark.
- Patch: alteração de código proposta para corrigir ou modificar um projeto.
- Regressão visual: mudança indesejada na aparência ou no comportamento de uma interface.
- KV cache: memória que guarda chaves e valores da atenção para reaproveitar informação durante a geração.
- Prefill e decode: etapas de processar o contexto e gerar os tokens da resposta.
- TTFT e TPOT: tempo até o primeiro token e tempo médio por token de saída.
- Quantização: redução da precisão numérica de pesos ou ativações para economizar memória e processamento.
- W4A4, W8A8, INT4, KV8 e KV16: W4A4 usa pesos e ativações de 4 bits; W8A8 usa 8 bits; INT4 é cálculo inteiro de 4 bits; KV8 e KV16 indicam cache de 8 ou 16 bits.
- NPU e GPU: aceleradores de redes neurais e processadores gráficos usados para treinar ou servir modelos.
- BF16 e F32: formatos de precisão numérica dos arquivos do checkpoint.
- RL: aprendizado por reforço, que usa recompensas para orientar o comportamento.
- Reward hacking: obtenção de recompensa por uma via que não cumpre corretamente o objetivo.
- SFT e DDP: ajuste fino supervisionado e paralelismo de dados distribuído, este último usado como linha de base.
- GEMM: operação de multiplicação de matrizes usada nos kernels do modelo.
- Tree Attention: organização da atenção em estrutura de árvore usada no treinamento multi-professor.
- Backbone de texto: parte responsável pelo processamento linguístico na arquitetura desacoplada.
- Sandbox: ambiente isolado usado para executar código e ferramentas com controle.
- Runtime de serviço: programa que carrega o modelo e atende às requisições de inferência.
- Leaderboard: classificação de resultados obtidos em um benchmark.

Fonte: <https://huggingface.co/meituan-longcat/LongCat-2.5>

## Para onde ir depois

Pratique primeiro em uma correção guiada por screenshot e registre o custo por resultado aceito. Se a vantagem aparecer nas tarefas visuais, amplie esse fluxo. Compare o DeepSeek na manutenção de texto e mantenha um modelo mais forte para os casos difíceis.

- Acesse https://longcat.chat/platform/docs/ para ver como criar a conta e a chave de acesso ao LongCat-2.5.
- Leia https://longcat.chat/platform/docs/pricing/longcat-2.5 antes de cada rodada; o cálculo usará as tarifas vigentes.
- Use https://huggingface.co/meituan-longcat/LongCat-2.5 para conhecer os pesos, a licença e a implantação documentada.
- Se avaliar serviço próprio, abra https://github.com/meituan-longcat/SGLang-FluentLLM e verifique as instruções de NPU e o suporte multimodal.
- Para conhecer as respostas do modelo, use a interface oficial https://longcat.ai/.

Fonte: <https://longcat.chat/platform/docs/>
