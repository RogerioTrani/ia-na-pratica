# Kimi K3.1 Pro bate o Opus 5.5 em 3 testes por US$ 2

_2026-11-23 · noticia_

A Moonshot AI apresentou o Kimi K3.1 Pro, um modelo de pesos abertos, multimodal e agêntico com 2,8 trilhões de parâmetros e 104 bilhões ativos por vez. A tabela da própria empresa inclui três vitórias sobre o Claude Opus 5.5 e três resultados abaixo de concorrentes em outros cenários. Esta apostila explica como arquitetura, contexto, preço e metodologia de teste se relacionam. Ao final, você saberá escolher o caminho de acesso, configurar as chamadas e comparar o modelo nas suas próprias tarefas.

## O fato

A Moonshot AI divulgou o Kimi K3.1 Pro como o primeiro modelo da série K3.1. O cartão oficial descreve um modelo de pesos abertos, multimodal nativo e agêntico, pós-treinado a partir do Kimi K3 com aprendizado por reforço conjunto em grande escala. A empresa atribui ao modelo melhorias em programação, criação 3D, pesquisa financeira, precisão factual e outras capacidades de agente.

O anúncio reúne o Kimi K3.1 Pro e outros modelos na mesma tabela de avaliação. O Kimi supera o Claude Opus 5.5 em DeepSWE v1.1, BrowseComp e HLE-Full com ferramentas. Em Terminal-Bench 4.0 e OSWorld V2.1, o Opus 5.5 marca mais. Em GPQA-Diamond, o GPT-6 Astra lidera.

Os pesos estão publicados no Hugging Face. A API oficial permite selecionar kimi-k3.1-pro, e o cartão informa compatibilidade com as APIs da OpenAI e da Anthropic.

Fonte: <https://huggingface.co/moonshotai/Kimi-K3.1-Pro>

## Por que isso importa

Pesos abertos permitem que uma equipe avalie o modelo em servidor próprio ou por API. Isso separa duas decisões: a qualidade da resposta e o controle da execução. A hospedagem própria oferece controle sobre a infraestrutura e exige operação; a API concentra o acesso no serviço do fornecedor.

O formato agêntico também muda o tipo de trabalho avaliado. Um agente pode usar ferramentas e executar várias etapas para concluir uma tarefa. Por isso, testes com navegação, terminal, documentos e uso de computador ajudam a entender capacidades diferentes das de uma resposta isolada.

O preço por milhão de tokens entra na mesma conta, mas representa apenas uma parte do custo. A quantidade de entrada, a extensão da saída, as ferramentas usadas e o tempo de operação influenciam o resultado. Uma comparação útil repete uma tarefa real e mede qualidade e custo juntos.

Fonte: <https://huggingface.co/moonshotai/Kimi-K3.1-Pro>

## O modelo por dentro

O Kimi K3.1 Pro combina texto e imagem. O cartão informa o MoonViT-V2 como codificador de visão, com 401 milhões de parâmetros. Essa composição permite que a mesma entrada de trabalho envolva linguagem e conteúdo visual, conforme o tipo de tarefa.

O modelo foi pós-treinado a partir do Kimi K3. A Moonshot descreve aprendizado por reforço conjunto em grande escala, aplicado a centenas de domínios. O pós-treinamento ajusta o comportamento do modelo para executar tarefas e usar ferramentas depois da etapa de treinamento principal.

A janela de contexto de 1 milhão de tokens amplia a quantidade de informação que pode ser considerada em uma execução. A empresa apresenta o Kimi K3.1 Pro como seu modelo mais capaz da classe de 3 trilhões de parâmetros até então. Essa é uma afirmação do fabricante, sustentada no cartão pela arquitetura e pelos resultados publicados.

- Pesos abertos: os pesos estão no Hugging Face, com uso regido pela Kimi K3.1 Pro License.
- Multimodal nativo: o modelo trabalha com texto e imagem.
- Agêntico: o modelo foi avaliado em tarefas com ferramentas e ações ao longo de várias etapas.
- Pós-treinamento: o Kimi K3.1 Pro parte do Kimi K3 e recebe ajuste adicional em muitos domínios.

Fonte: <https://huggingface.co/moonshotai/Kimi-K3.1-Pro>

## Como funciona a arquitetura

O Kimi K3.1 Pro usa uma arquitetura Mixture-of-Experts, ou MoE. Em vez de acionar todos os parâmetros a cada token, o sistema seleciona parte dos especialistas disponíveis. O cartão registra 2,8 trilhões de parâmetros no total e 104 bilhões ativados por vez. Essa distinção explica como um modelo muito grande pode manter uma fração ativa durante o processamento.

Há 896 especialistas, com 16 selecionados por token e 2 especialistas compartilhados. A seleção distribui o trabalho entre partes especializadas da rede. O número total descreve a capacidade do modelo; o número ativo descreve a parte que participa de uma determinada decisão.

A quantização reduz a precisão usada para representar pesos e ativações. O cartão informa pesos MXFP4 e ativações MXFP8, com treinamento consciente da quantização. Essa escolha faz parte da arquitetura e precisa ser considerada ao planejar memória e execução.

- Parâmetros: 2,8 trilhões no total e 104 bilhões ativados por vez.
- Especialistas: 896 no total, 16 selecionados por token e 2 compartilhados.
- Camadas: 93, sendo 1 densa; a atenção reúne 69 camadas KDA e 24 Gated DSA.
- Dimensões: 7.168 na atenção, 3.584 no MoE latente e 3.072 por especialista.
- Atenção: 96 cabeças; o DSA tem 32 cabeças de índice, dimensão 128 e Top-K de 2.048.
- Vocabulário: 160 mil tokens; função de ativação SiTU-GLU.

Fonte: <https://huggingface.co/moonshotai/Kimi-K3.1-Pro>

## Contexto de 1 milhão e atenção esparsa

Um token é uma unidade de processamento de texto. A janela de contexto define quanto conteúdo o modelo pode considerar de uma vez. No Kimi K3.1 Pro, o comprimento informado é 1.048.576 tokens. Isso permite trabalhar com conjuntos maiores de documentos, código ou histórico de conversa, dentro dessa capacidade.

Uma janela grande aumenta o espaço disponível para a tarefa. A atenção esparsa organiza como o modelo consulta esse espaço. Segundo o cartão, as camadas Gated MLA de atenção completa do Kimi K3 foram substituídas por camadas Gated DeepSeek Sparse Attention no K3.1 Pro, para modelar contextos longos com mais eficiência.

O teste BrowseComp mostra como contexto e limite de execução aparecem na prática. A avaliação usa compactação ao alcançar 200 mil tokens e permite no máximo 500 passos. Se o agente atinge o limite, precisa responder antes do julgamento. Esses números descrevem a configuração desse teste, não um limite universal de uso.

Fonte: <https://huggingface.co/moonshotai/Kimi-K3.1-Pro>

## Onde o Kimi K3.1 Pro vence

A tabela da Moonshot coloca o Kimi K3.1 Pro à frente do Claude Opus 5.5 nos três testes abaixo, entre outros. Os resultados do Kimi usam esforço de raciocínio máximo, temperature 1,0 e top-p 0,95, salvo indicação diferente. As notas do cartão mostram que testes de modelos proprietários podem envolver comportamento de fallback.

Cada vitória vale para o teste indicado. Ela ajuda a escolher onde experimentar o modelo, mas não estabelece um resultado geral para toda tarefa de programação, pesquisa ou conhecimento.

- DeepSWE v1.1: 75,5 para o Kimi K3.1 Pro e 74,2 para o Claude Opus 5.5, na categoria de programação.
- BrowseComp: 92,1 para o Kimi K3.1 Pro e 90,8 para o Claude Opus 5.5, na categoria de avaliação agêntica.
- HLE-Full com ferramentas: 70,0 para o Kimi K3.1 Pro e 67,7 para o Claude Opus 5.5, na categoria de raciocínio e conhecimento.

Fonte: <https://huggingface.co/moonshotai/Kimi-K3.1-Pro>

## Onde o Kimi K3.1 Pro fica atrás

O mesmo cartão registra resultados abaixo de concorrentes, entre eles os três a seguir. As margens aparecem em testes diferentes, com ferramentas e ambientes próprios. Terminal-Bench 4.0 e OSWorld V2.1 avaliam capacidades ligadas ao terminal e ao uso de computador. GPQA-Diamond está na categoria de raciocínio e conhecimento.

Esses resultados orientam a escolha por tarefa. Um modelo que lidera um teste de pesquisa pode ficar atrás em operação de computador ou em perguntas de ciência avançada.

- Terminal-Bench 4.0: 65,7 para o Kimi K3.1 Pro e 66,4 para o Claude Opus 5.5.
- GPQA-Diamond: 94,2 para o Kimi K3.1 Pro, 96,1 para o GPT-6 Astra e 93,9 para o Claude Opus 5.5. Nesse teste, o Kimi supera o Opus e fica abaixo do GPT-6 Astra.
- OSWorld V2.1: 79,6 para o Kimi K3.1 Pro, 81,8 para o Claude Opus 5.5 e 75,8 para o GPT-6 Astra.

Fonte: <https://huggingface.co/moonshotai/Kimi-K3.1-Pro>

## A tabela além dos três testes

A tabela completa mostra um perfil irregular, com vantagens e desvantagens distribuídas por programação, agentes, conhecimento, multimodalidade e segurança. Os recortes abaixo mantêm o comparador e a unidade de cada resultado. Eles descrevem apenas o teste nomeado.

- Terminal-Bench-Science 0.1: 38,1 para o Kimi, contra 68,1 do GPT-6 Astra e 63,3 do Claude Opus 5.5.
- SWE Marathon v1.1: 51,7 para o Kimi, contra 46,3 do Claude Opus 5.5 e 42,5 do GPT-6 Astra.
- ProgramBench: 31,5 para o Kimi, contra 65,0 do Claude Opus 5.5. A nota é binária: 1 quando a pontuação da tarefa atinge pelo menos 95% e 0 nos demais casos.
- BenchCAD: 72,8 sem ferramentas, contra 73,0 do Claude Opus 5.5. Com ferramentas, o Kimi marca 92,7, contra 96,2 do Opus 5.5 e 95,9 do GPT-6 Astra. Os modelos abertos são avaliados em amostras de 1.000 casos retirados de 17.900.
- PostTrain Bench v1.2: 36,5 para o Kimi, contra 43,8 do Claude Opus 5.5 e 41,9 do GPT-6 Astra. O Kimi foi avaliado internamente com Claude Code e GPUs H20, usando DeepSeek-V4.1-Flash-1017 no esforço máximo como juiz.
- OfficeQA Pro v2: 64,4 para o Kimi, contra 62,2 do Claude Opus 5.5 e 54,4 do GPT-6 Astra. Em OfficeQA Pro, o Claude Fable 5.1 marca 68,6; o Kimi, 67,4; e o GPT-6 Astra, 66,2.
- GDPval-AA v2.1: Elo de 1.846 para o Kimi e 1.866 para o Claude Opus 5.5. Essa pontuação Elo não é uma taxa de acerto.
- HLE-Full sem ferramentas: 51,1 para o Kimi, contra 59,8 do Claude Opus 5.5 e 53,6 do GPT-6 Astra. HLE-Diamond: 39,4, contra 60,9 do Opus 5.5 e 65,8 do GPT-6 Astra.
- MMMU-Pro: 84,1 para o Kimi, contra 87,7 do Claude Opus 5.5 e 86,9 do GPT-6 Astra. PerceptionBench: 68,3, contra 72,1 do Opus 5.5 e 77,6 do GPT-6 Astra.
- Kimi Hallu Bench Hard com ferramentas: 8,3 para o Kimi, contra 15,0 do Claude Opus 5.5 e 5,5 do GPT-6 Astra. Nesse teste interno, a taxa de alucinação no nível de afirmações é medida com verificação por agentes, e quanto menor, melhor.
- Harvey Legal Agent: 23,7 em 1.251 tarefas públicas. A métrica é a taxa de tarefas que passam em todos os critérios de avaliação.
- ExploitBench: 74,7 para o Kimi, contra 91,0 do Claude Opus 5.5 e 100 do GPT-6 Astra. O resultado do Kimi usa a melhor de cinco sementes em um orçamento de 300 turnos. ExploitGym: 20,7, contra 34,5 do Opus 5.5 e 42,4 do GPT-6 Astra, com seis horas por tarefa.
- Testes internos: Kimi Code Bench 2.0 marca 77,1 e Kimi Code Bench 3.0 Long-horizon marca 61,2. Esses números descrevem os conjuntos internos da Moonshot.

Fonte: <https://huggingface.co/moonshotai/Kimi-K3.1-Pro>

## Como ler os benchmarks

Um benchmark é um teste padronizado, e o resultado depende da configuração usada. No cartão, os resultados do Kimi K3.1 Pro usam reasoning_effort max, temperature 1,0 e top-p 0,95, salvo exceções. BrowseComp usa temperature 1,0 e top-p 1,0. Manter a mesma configuração ajuda a tornar uma comparação mais justa.

O harness é o ambiente que conduz o modelo durante o teste. O Kimi usa Claude Code em várias avaliações de programação, Kimi Code em outras, como BioMysteryBench e ExploitGym, e Kimi Agent em OSWorld V2.1. Os comparadores podem usar outros ambientes ou relatórios técnicos. A coluna de modelos proprietários também indica fallback em parte dos resultados.

As unidades variam. Taxas de acerto, taxas de aprovação, Elo, notas binárias e pass@5 respondem a perguntas diferentes. O cartão orienta que pontuações maiores são melhores, exceto quando o teste declara o contrário. Um traço indica ausência de pontuação na tabela, e valores Elo não devem ser comparados diretamente com acerto.

- Reasoning effort: max é a configuração padrão do Kimi K3.1 Pro e o esforço usado na tabela, salvo exceções.
- ProgramBench: converte o resultado em 1 ou 0 usando o corte de 95%.
- Harvey Legal Agent: mede a proporção de tarefas que passam em todos os critérios.
- ExploitBench: usa pass@5, com a melhor pontuação entre cinco sementes.
- Kimi Hallu Bench: usa taxa de alucinação no nível de afirmações, em que menor é melhor.
- GDPval-AA e AA-Briefcase: usam Elo, uma escala de rating.
- Amostras: BenchCAD usa 1.000 de 17.900 casos para modelos abertos; HLE-Full tem 2.500 questões e HLE-Diamond tem 1.000.
- Agentes: Agents' Last Exam usa 122 tarefas, sendo 86 CLI; desrespeitar requisitos declarados zera a execução.
- Julgamento: DECK-Arena e Design Bench têm avaliador automático calibrado com mais de 10 mil julgamentos humanos.

Fonte: <https://huggingface.co/moonshotai/Kimi-K3.1-Pro>

## Os números do anúncio

Os números abaixo têm unidades e recortes diferentes. Preço por token, tamanho de contexto, amostra de teste e orçamento de execução medem coisas distintas. Juntos, eles ajudam a dimensionar uma avaliação sem transformar uma medida em outra.

- US$ 2 por milhão de tokens de entrada na OpenRouter: é o preço divulgado para a parte enviada ao modelo.
- US$ 10 por milhão de tokens de saída na OpenRouter: é o preço divulgado para a parte gerada pelo modelo.
- 1 milhão de tokens de contexto: equivale ao comprimento informado de 1.048.576 tokens.
- 104 bilhões de parâmetros ativos: é a fração acionada por vez em um modelo com 2,8 trilhões de parâmetros no total.
- 200 mil tokens e 500 passos no BrowseComp: são o ponto de compactação e o máximo de passos desse teste.
- 2.500 questões no HLE-Full e 1.000 no HLE-Diamond: são os tamanhos dos conjuntos de avaliação.
- 122 tarefas, sendo 86 CLI, no Agents' Last Exam: definem a composição do conjunto v1.1.
- 1.251 tarefas públicas no Harvey Legal Agent: formam a base da taxa de aprovação integral.
- 1.000 casos de um total de 17.900 no BenchCAD: definem a amostra usada para modelos abertos.
- Mais de 10 mil julgamentos humanos: calibraram o avaliador automático de DECK-Arena e Design Bench.
- 300 turnos e pass@5 no ExploitBench: limitam a execução e selecionam a melhor de cinco sementes.
- Seis horas por tarefa no ExploitGym: é o orçamento de tempo usado na avaliação do Kimi.

## KimiWork e execução em paralelo

KimiWork é uma função para executar mais de 300 agentes ao mesmo tempo. O exemplo relata um pedido para encontrar 30 empresas locais em Nova York sem sites e construir um site para cada. Segundo o relato, mais de 150 agentes foram lançados de uma vez e o trabalho terminou em 30 minutos.

O caso ilustra um padrão de automação: dividir um objetivo em tarefas independentes e executá-las em paralelo. Isso pode reduzir a espera entre etapas quando cada agente tem uma responsabilidade clara. A coordenação e a revisão dos resultados continuam necessárias.

Os números de KimiWork pertencem a esse relato específico. A tabela oficial do Kimi K3.1 Pro reúne resultados de testes próprios, com metodologia e comparadores diferentes.

- A tarefa foi dividida por empresa, criando unidades de trabalho independentes.
- A execução paralela concentrou vários agentes na mesma etapa.
- O resultado de 30 minutos descreve o caso relatado e serve como exemplo, não como velocidade geral para outras tarefas.

## O que muda para você

Exemplo: imagine que sua equipe precisa pesquisar um assunto e produzir código. Você pode testar o Kimi K3.1 Pro com a mesma instrução, as mesmas ferramentas e o mesmo critério de aceitação que já usa. Os resultados de DeepSWE e BrowseComp tornam essa uma hipótese de trabalho razoável para a sua avaliação.

Se a tarefa exigir operar um computador, OSWorld V2.1 e Terminal-Bench 4.0 indicam outra direção. Nesses testes, o Claude Opus 5.5 ficou à frente. A escolha pode variar conforme a etapa: pesquisa e código em uma parte, operação de interface em outra.

A abertura dos pesos adiciona a opção de hospedagem própria. Antes de decidir, compare o custo por tarefa concluída, a qualidade da resposta e o esforço de operação. Um preço menor por milhão de tokens só vira vantagem prática quando a execução atende ao critério definido.

Fonte: <https://huggingface.co/moonshotai/Kimi-K3.1-Pro>

## O que fazer hoje

Comece por uma tarefa que você já sabe julgar. O objetivo é criar uma comparação pequena e repetível antes de ampliar o uso.

Use o caminho de API para uma avaliação rápida. Considere a hospedagem própria depois de definir frequência, volume e necessidade de controle.

1. Defina uma tarefa de pesquisa, código ou operação de computador e registre o resultado que você considera aceitável. O resultado esperado é um critério de comparação antes do teste.
2. Abra a API oficial em https://platform.kimi.ai e selecione kimi-k3.1-pro. O resultado esperado é ver o modelo disponível para a chamada.
3. Na requisição, escolha reasoning_effort entre low, high e max, lembrando que max é o padrão. O resultado esperado é registrar o nível usado na comparação.
4. Envie uma pergunta curta no mesmo ambiente que será usado no teste. O resultado esperado é confirmar autenticação, modelo e formato da resposta.
5. Repita a tarefa com o seu modelo atual e com o Kimi K3.1 Pro, mantendo instruções e ferramentas equivalentes. O resultado esperado é comparar qualidade no mesmo trabalho.
6. Em conversas com várias rodadas ou chamadas de ferramenta, devolva a mensagem assistant completa, incluindo reasoning_content e tool_calls. O resultado esperado é preservar o histórico enviado pela API.
7. Some separadamente os tokens de entrada e saída de cada execução. O resultado esperado é estimar o custo por tarefa concluída.
8. Se optar pela hospedagem própria, escolha um dos motores recomendados no cartão e siga a receita oficial. O resultado esperado é ter um caminho de execução compatível com os pesos.

Fonte: <https://platform.kimi.ai>

## API, hospedagem e raciocínio preservado

A API oficial fica em https://platform.kimi.ai. O identificador do modelo é kimi-k3.1-pro, e a interface é compatível com OpenAI e Anthropic. O campo reasoning_effort aceita low, high e max, com max como padrão.

Para conversas com várias rodadas e chamadas de ferramenta, o cartão exige que a mensagem assistant retornada pela API volte em messages como foi recebida. Isso inclui reasoning_content e tool_calls, além de content. Enviar apenas o texto final pode descartar informações necessárias à continuidade.

Os pesos abertos permitem avaliar hospedagem própria. A Moonshot recomenda vLLM, SGLang e TokenSpeed, com receitas oficiais. A escolha do motor e da infraestrutura deve considerar memória, desempenho e operação. O exemplo abaixo recebe um cliente OpenAI já configurado e usa model_name para indicar o modelo.

```
import openai
def chat_with_preserved_thinking(client: openai.OpenAI, model_name: str):
 messages = [
 {
 "role": "user",
 "content": "Tell me three random numbers."
 },
 {
 "role": "assistant",
 "reasoning_content": "I'll start by listing five numbers: 473, 921, 235, 215, 222, and I'll tell you the first three.",
 "content": "473, 921, 235"
 },
 {
 "role": "user",
 "content": "What are the other two numbers you have in mind?"
 }
 ]
 response = client.chat.completions.create(
 model=model_name,
 messages=messages,
 stream=False,
 max_tokens=4096,
 reasoning_effort="max",
 )
 # the assistant should mention 215 and 222 that appear in the prior reasoning content
 print(f"response: {response.choices[0].message.reasoning}")
 return response.choices[0].message.content
```

Fonte: <https://huggingface.co/moonshotai/Kimi-K3.1-Pro>

## Teste de pronto

Use estes pontos para verificar se a avaliação está pronta. Cada item deve ser observável na requisição, no histórico ou no registro do teste.

- [ ] O identificador kimi-k3.1-pro aparece na requisição enviada.
- [ ] O reasoning_effort usado está registrado e é o mesmo na comparação.
- [ ] A tarefa produz o resultado que você definiu como aceitável antes do teste.
- [ ] O comparador recebeu instruções e ferramentas equivalentes.
- [ ] Os tokens de entrada e saída foram contados separadamente.
- [ ] A mensagem assistant completa foi preservada em messages quando houve várias rodadas ou chamadas de ferramenta.
- [ ] Na hospedagem própria, o motor recomendado respondeu à chamada de teste.

Fonte: <https://huggingface.co/moonshotai/Kimi-K3.1-Pro>

## O que conferir

A tabela é publicada pela Moonshot. Ela reúne avaliações próprias, resultados de líderes e relatórios de outros fabricantes. Harness, fallback, amostra e métrica mudam o significado de cada linha.

Pesos abertos ampliam as opções de execução, e a licença define as condições de uso. A hospedagem própria também adiciona custos de infraestrutura e operação. O relato de KimiWork deve ser lido como um caso específico, separado dos benchmarks do K3.1 Pro.

- Trate os resultados como dados publicados pela Moonshot e reproduza os testes que influenciarem sua decisão.
- Compare linhas com a mesma unidade: acerto, taxa de aprovação, Elo e pass@5 não são intercambiáveis.
- Confira se menor é melhor nos testes de alucinação antes de interpretar a pontuação.
- Registre harness, reasoning_effort, temperature, top-p e uso de fallback na sua comparação.
- Considere amostras e orçamentos: BenchCAD usa subconjunto, BrowseComp limita passos e ExploitGym limita tempo.
- Leia os termos da Kimi K3.1 Pro License antes de hospedar ou distribuir o modelo.
- Separe os resultados de KimiWork dos resultados de benchmark do Kimi K3.1 Pro.

Fonte: <https://huggingface.co/moonshotai/Kimi-K3.1-Pro>

## Glossário

- Agente: sistema que conduz uma tarefa por várias etapas e pode usar ferramentas para agir.
- API: interface usada para enviar solicitações e receber respostas do modelo.
- Benchmark: teste padronizado usado para medir uma capacidade específica.
- Contexto: quantidade de informação que o modelo pode considerar em uma execução.
- Token: unidade de processamento de texto usada também para contar entrada, saída e preço.
- Parâmetro: valor aprendido pelo modelo durante o treinamento.
- Pesos abertos: parâmetros do modelo disponíveis para acesso e uso conforme a licença.
- Mixture-of-Experts: arquitetura que seleciona parte de um conjunto de especialistas para processar cada token.
- Atenção esparsa: mecanismo que consulta partes relevantes do contexto em vez de aplicar atenção completa a todos os elementos.
- Multimodal: capacidade de trabalhar com mais de um tipo de dado, aqui texto e imagem.
- Quantização: representação de pesos e ativações com precisão reduzida para diminuir exigências de memória e processamento.
- Reasoning effort: campo da requisição que controla o esforço de raciocínio entre low, high e max.
- Reasoning content: conteúdo de raciocínio retornado pela API que deve ser preservado no histórico.
- Tool calls: chamadas de ferramenta retornadas pela API que também devem voltar no histórico.
- Harness: ambiente e conjunto de regras usado para conduzir o modelo durante uma avaliação.
- Fallback: comportamento de contingência que pode participar da execução de um modelo proprietário.
- Pass@5: no ExploitBench, a melhor pontuação obtida entre cinco sementes.
- Elo: pontuação de rating usada em alguns testes, distinta de taxa de acerto.
- Taxa de alucinação: proporção de afirmações identificadas como incorretas pelos verificadores do teste.
- Validação humana: revisão do resultado por uma pessoa antes de usar a saída em um trabalho real.

Fonte: <https://huggingface.co/moonshotai/Kimi-K3.1-Pro>

## Para onde ir depois

Comece pelo cartão oficial para revisar arquitetura, avaliações, licença e opções de execução. Depois, use a documentação da API para testar visão, saída estruturada, ferramentas e cache de contexto.

Pratique com uma tarefa sua e mantenha o mesmo critério de aceitação em todos os modelos. O próximo passo é repetir a comparação com outra tarefa e registrar onde cada modelo funciona melhor.

- Leia o cartão oficial do Kimi K3.1 Pro em https://huggingface.co/moonshotai/Kimi-K3.1-Pro.
- Acesse a API oficial em https://platform.kimi.ai e selecione kimi-k3.1-pro.
- Use o Quickstart em https://platform.kimi.ai/docs/guide/kimi-k3-1-pro-quickstart para os exemplos oficiais de integração.
- Consulte Thinking Effort em https://platform.kimi.ai/docs/guide/use-thinking-effort para ajustar low, high e max.
- Se for hospedar, siga as receitas oficiais de vLLM, SGLang ou TokenSpeed listadas no cartão do modelo.

Fonte: <https://platform.kimi.ai>
