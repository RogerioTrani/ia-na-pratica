# Tether AI Research apresenta BotPsy para uso no dispositivo

_2026-11-18 · reportagem_

O BotPsy é um modelo de 0,8 bilhão de parâmetros criado pela Tether AI Research para funcionar como assistente pessoal no próprio dispositivo, especializado em chamar ferramentas e executar ações cotidianas. Publicado em 11 de novembro de 2026 e construído sobre o Qwen3.5-0.8B, ele supera modelos até 2,5 vezes maiores em testes de uso de ferramentas, mantendo os dados no aparelho do usuário. Esta apostila explica o que ele faz, como foi treinado, onde funciona bem, onde ainda falha, como rodá-lo localmente e como avaliar se serve para o seu caso.

## O fato

A Tether AI Research anunciou em 11 de novembro de 2026 o BotPsy, um modelo de 0,8 bilhão de parâmetros voltado a funcionar como assistente pessoal no próprio dispositivo. Construído sobre o Qwen3.5-0.8B, ele foi especializado em chamadas de ferramentas e fluxos agênticos, ou seja, em decidir qual ação executar e quando executá-la.

O modelo é descrito como capaz de realizar tarefas simples para o usuário, com foco em rotinas cotidianas. Por ter menos de um bilhão de parâmetros, é mais adequado a tarefas de dificuldade baixa a média.

Os pesos são distribuídos sob licença Apache 2.0, em formatos safetensors e GGUF, e podem ser usados com o llama.cpp.

Fonte: <https://huggingface.co/blog/qvac/botpsy>

## Por que isso importa

Modelos de linguagem hospedados na nuvem cobram por uso e podem mudar, negar ou descontinuar o acesso a qualquer momento. Além disso, enviam dados do usuário para servidores de terceiros, o que afeta privacidade e controle. Nem toda tarefa, porém, exige um modelo de fronteira: agentes pequenos e especializados podem resolver rotinas com custo muito menor e processamento no próprio aparelho.

A aposta do BotPsy é que a inteligência por parâmetro está melhorando rápido o suficiente para que um modelo de 0,8 bilhão de parâmetros, treinado especificamente para usar ferramentas, supere modelos maiores em tarefas cotidianas de assistente pessoal. Isso mantém os dados do usuário no dispositivo e reduz a dependência de serviços externos.

A equipe também descreve uma visão mais ampla: expandir as capacidades agênticas no dispositivo para integrar com mais hardware e serviços locais, evoluir consultas privadas ponto a ponto, otimizar mecanismos de ajuste fino local e permitir delegação de tarefas pesadas para computadores domésticos ou nós confiáveis. Protocolos de privacidade seriam fortalecidos para manter dados, credenciais e decisões no hardware local.

O modelo ainda comete erros e não se destina a decisões de alto risco, como operações financeiras ou médicas. A equipe afirma que ele foi feito para avançar o estado da arte e apoiar pesquisa e educação.

Fonte: <https://huggingface.co/blog/qvac/botpsy>

## O que é o BotPsy

O BotPsy é um modelo de linguagem de 0,8 bilhão de parâmetros baseado no Qwen3.5-0.8B. Foi pós-treinado para duas capacidades centrais: chamada de funções (function calling) e fluxos agênticos, ou seja, sequências de ações em que o modelo decide o que fazer, executa e reage ao resultado.

Ele funciona como assistente pessoal: o usuário pede algo em linguagem natural e o modelo decide qual ferramenta usar, com quais parâmetros, e devolve a chamada estruturada para o aplicativo executar. A equipe descreve o modelo como capaz de realizar tarefas simples para o usuário, com foco em rotinas cotidianas.

Por causa do tamanho compacto, o modelo é mais adequado a tarefas de dificuldade baixa a média. A equipe afirma que ele alcança desempenho de ponta em uso de ferramentas para o seu porte, superando todos os modelos de até 1,2 bilhão de parâmetros testados.

Fonte: <https://huggingface.co/blog/qvac/botpsy>

## Como o assistente usa ferramentas

O BotPsy não executa ações diretamente. O aplicativo que o hospeda declara as ferramentas disponíveis por meio de um esquema JSON de function calling, como uma função create_event para criar eventos no calendário. Quando o usuário faz um pedido, o modelo retorna uma chamada de função estruturada no campo tool_calls da resposta, e o aplicativo é responsável por executá-la.

Antes de executar, o aplicativo hospedeiro deve solicitar permissão explícita do usuário para acessar calendário, caixa de entrada ou arquivos. Depois da execução, o resultado da ferramenta é devolvido ao modelo para que ele produza a resposta final ao usuário.

O modelo também foi treinado para saber quando não agir: em testes, ele recusa inventar chamadas quando nenhuma ferramenta disponível atende ao pedido. No teste de alucinação de ferramentas do BFCL v4, marcou 86,1 pontos, a maior pontuação entre os modelos testados. No ACEBench, nos casos em que o pedido está incompleto, tem parâmetros errados ou não pode ser atendido pelas ferramentas fornecidas, marcou 51,3, contra 13,7 do modelo base; nesse recorte, o Qwen3.5-2B-Think ficou à frente, com 58,0.

Fonte: <https://huggingface.co/qvac/BotPsy-0.8B-GGUFs>

## Resultados nos testes de uso de ferramentas

A equipe testou o BotPsy em seis benchmarks de uso de ferramentas e fluxos agênticos: BFCL v4, ACEBench, τ-bench, ToolSandbox, Claw-Eval e BrowseComp-Plus. Em cinco dos seis, o BotPsy ficou à frente do Qwen3.5-2B-Think, um modelo 2,5 vezes maior. Apenas no Claw-Eval o modelo maior liderou.

Em relação à própria base, o BotPsy praticamente dobrou o desempenho: no BFCL v4, a pontuação subiu de 23,4 para 44,0; no ACEBench, de 30,1 para 58,7; no τ-bench, de 23,2 para 51,5; no ToolSandbox, de 30,5 para 64,6; e no BrowseComp-Plus, de 1,9 para 4,5. No Claw-Eval, subiu de 39,3 para 46,5, mas ficou abaixo dos 48,9 do Qwen3.5-2B-Think.

O BotPsy também superou todos os modelos de até 1,2 bilhão de parâmetros testados (Qwen3.5-0.8B-Think, LFM2.5-1.2B-Think e MiniCPM5-1B-Think) nos seis benchmarks. A média não ponderada dos seis benchmarks foi de 45,0 para o BotPsy, contra 24,7 da base e 38,8 do Qwen3.5-2B-Think.

Fonte: <https://huggingface.co/blog/qvac/botpsy>

## Conhecimento geral e seguimento de instruções

O treinamento para uso de ferramentas não custou conhecimento geral. No GPQA Diamond, a pontuação subiu de 33,2 para 38,1; no MMLU-Pro, de 41,6 para 48,9. Em ambos, o BotPsy liderou entre os modelos de até 1,2 bilhão de parâmetros testados, embora o Qwen3.5-2B-Think, maior, tenha marcado 59,9 e 65,5 respectivamente.

O seguimento de instruções melhorou de forma mais acentuada. No IFEval, a pontuação subiu de 59,7 para 90,8, a maior entre os cinco modelos testados. No IFBench, subiu de 22,0 para 55,9, também a maior. No Multi-IF, que testa seguimento de instruções em três turnos e oito idiomas, marcou 67,2, empatando com o Qwen3.5-2B-Think (66,9) e o LFM2.5-1.2B-Think (68,2).

O BotPsy começa forte no primeiro turno (84,3, a maior pontuação entre os cinco) mas cai mais rápido à medida que as instruções se acumulam (51,0 no terceiro turno, contra 56,5 e 56,2 dos dois modelos citados). Idiomas de menos recursos continuam sendo ponto fraco: hindi marcou 24,5 e russo 57,6, bem abaixo dos 72 a 80 alcançados em inglês, chinês, francês, espanhol, italiano e português.

Fonte: <https://huggingface.co/blog/qvac/botpsy>

## Conversas em várias etapas

Os maiores ganhos relativos aparecem em interações multi-turno, com estado, onde o agente precisa manter uma conversa longa, seguir uma política rígida e agir em nome do usuário. No BFCL v4 multi-turn, a pontuação subiu de 7,5 para 46,1, quase o dobro do Qwen3.5-2B-Think (23,8). No ACEBench Agent, subiu de 7,9 para 28,3, contra 16,2 do modelo maior.

No τ²-bench, o BotPsy dobrou o desempenho da base no varejo (67,8 contra 33,9, com vantagem estreita sobre os 65,5 do Qwen3.5-2B-Think) e alcançou 82,5 em telecomunicações, onde o agente guia o usuário por muitos turnos de solução de problemas. Nesse cenário, o Qwen3.5-2B-Think marcou 69,3 e o MiniCPM5-1B-Think, 74,0.

O BotPsy também foi o mais confiável dos cinco em chamadas únicas (BFCL não-live: 83,0) e em não chamar ferramenta quando nenhuma serve (BFCL alucinação: 86,1). O τ³-banking foi o único benchmark multi-turno em que não liderou: nenhum modelo ultrapassou 5 pontos (BotPsy 4,1, igual à base; Qwen3.5-2B-Think 4,8).

Fonte: <https://huggingface.co/blog/qvac/botpsy>

## Onde funciona melhor e onde ainda falha

Em cenários simples, com um turno e uma chamada de ferramenta, o BotPsy marcou entre 70 e 79 em todos os grupos de aplicativos com amostra significativa, e 75 no geral, cerca de 21 pontos acima da base (54) e ligeiramente acima do Qwen3.5-2B-Think (70).

Em cenários complexos, com múltiplos turnos ou ferramentas, marcou 39,5 no geral, contra 17,9 da base e 30,8 do Qwen3.5-2B-Think. Os maiores ganhos aparecem em Comunicação e Redes Sociais (61 contra 13 da base), Comércio e Serviços (58 contra 27) e Gestão de Dispositivo e Sistema (46 contra 15). O Qwen3.5-2B-Think ficou à frente apenas em Produtividade Pessoal e Trabalho (64 contra 58), e o MiniCPM5-1B-Think teve leve vantagem em Comunicação e Redes Sociais (61,5 contra 60,5).

Busca de informações em várias etapas é o ponto fraco: cenários complexos de recuperação de informação marcaram 15, contra 79 em chamadas únicas. A maioria são perguntas de pesquisa profunda do BrowseComp-Plus, que permanecem difíceis para todos os modelos nessa faixa de tamanho (base: 9; Qwen3.5-2B-Think: 14). Busca na web no BFCL marcou 14,0 (Qwen3.5-2B-Think: 19,8) e memória 16,3 (Qwen3.5-2B-Think: 26,1). Tarefas multi-etapa ainda pontuam mais baixo que chamadas únicas, o que segue sendo o principal limite para tarefas mais difíceis.

Fonte: <https://huggingface.co/blog/qvac/botpsy>

## Treinamento em quatro etapas

O BotPsy é baseado no Qwen3.5-0.8B e passou por pós-treinamento em quatro etapas sequenciais: SFT (Supervised Fine-Tuning), MOPD (Multi-teacher On-Policy Distillation) e duas rodadas de aprendizado por reforço (RL) com o método DAPO. Cada etapa usa o melhor checkpoint da anterior como ponto de partida e se beneficia de um sinal de aprendizado diferente: imitação de trajetórias de referência, distribuições de token de modelos professores muito maiores e recompensas baseadas em regras para chamadas de ferramentas.

Na primeira etapa, SFT, o modelo passa por ajuste fino supervisionado completo em conversas de uso de ferramentas, incluindo trajetórias de agentes em múltiplos turnos em ambientes simulados, chamadas únicas, paralelas e multi-etapa, e casos em que nenhuma ferramenta deve ser chamada.

Na segunda etapa, MOPD, o estudante gera suas próprias respostas e um professor especialista dá feedback em cada token, usando divergência KL reversa por token. São três professores baseados no Qwen3.5-4B, treinados com RL para uso de ferramentas, raciocínio geral ou seguimento de instruções, e cada pedido é encaminhado a um deles. Essa etapa visa recuperar conhecimento e seguimento de instruções, que degradaram durante o SFT, embora as métricas de uso de ferramentas também aumentem.

Nas duas etapas finais de RL, o modelo aprende apenas com recompensas calculadas por regras e verificadores, usando o método DAPO. A primeira rodada foca em chamadas de ferramentas, acompanhada de seguimento de instruções e questões de múltipla escolha em STEM. A segunda rodada amplia o mix para tarefas verificáveis de domínio geral: matemática, código, conhecimento, seguimento de instruções, saídas estruturadas e uso de ferramentas multi-etapa em ambiente de trabalho simulado.

Fonte: <https://huggingface.co/blog/qvac/botpsy>

## Segurança

Em testes automatizados de red-teaming cobrindo seis categorias de dano, o BotPsy gerou respostas inseguras em 21% dos casos, contra 36% do modelo base Qwen3.5-0.8B. Essa é a menor taxa entre os modelos de até 1,2 bilhão de parâmetros testados (LFM2.5-1.2B-Think: 35%; MiniCPM5-1B-Think: 47%).

Sob ataques de injeção de instruções (prompt injection), que são especialmente relevantes para agentes que leem saídas não confiáveis de ferramentas, a taxa de respostas inseguras caiu de 46% da base para 31%.

A equipe afirma que o modelo não se destina a decisões automatizadas de alto risco nem a aplicações envolvendo dinheiro, informações pessoais, saúde ou outros temas sensíveis. A menção a pesquisa, educação e tarefas cotidianas de baixa e média complexidade é uma recomendação de escopo técnico, não uma limitação da licença.

Fonte: <https://huggingface.co/blog/qvac/botpsy>

## Eficiência de raciocínio

O BotPsy chega às respostas corretas com muito menos raciocínio do que a base, e com menos turnos em tarefas agênticas multi-turno. As comparações abaixo foram feitas nas mesmas perguntas ou tarefas (aquelas em que todos os cinco modelos responderam corretamente), para que diferenças de dificuldade não influenciem os números.

Em perguntas que todos os cinco modelos acertaram, o BotPsy usou de 1,4 a 3,1 vezes menos tokens de raciocínio por resposta correta: no GPQA Diamond, 3.690 contra 11.563; no MMLU-Pro, 1.912 contra 5.105; no IFEval, 3.148 contra 4.433; e no IFBench, 4.204 contra 11.576. Ao mesmo tempo, marcou mais alto nos quatro benchmarks.

A taxa de ficar preso em loops de raciocínio repetitivo caiu de 22,9% para 1,4% em todas as tentativas do IFBench, e as execuções que atingiram o limite de 32 mil tokens caíram de 28,3% para 0,2%. Em tarefas do τ²-bench que todos os cinco modelos resolveram, o BotPsy precisou de menos turnos de assistente: 10,7 contra 11,7 da base no varejo (9% menos) e 13,1 contra 17,6 no telecom (26% menos), passando 2,0 e 2,6 vezes mais tarefas do que a base.

Fonte: <https://huggingface.co/blog/qvac/botpsy>

## Como rodar no seu computador

Os pesos estão disponíveis sob licença Apache 2.0 em três precisões: bf16 (safetensors, cerca de 1,73 GB), e em GGUF nas variantes bf16 (cerca de 1,52 GB), Q8_0 (cerca de 0,81 GB, a recomendada) e Q4_K_M (cerca de 0,53 GB).

O modelo roda localmente em celulares (iOS e Android), laptops e desktops (Windows, macOS e Linux) sem GPU dedicada. Requer cerca de 600 MB a 1 GB de RAM ou VRAM para as variantes quantizadas Q4 e Q8, ou cerca de 2 GB para a versão bf16.

Os comandos abaixo instalam a ferramenta de linha de comando do Hugging Face (primeira linha) e o llama.cpp (segunda linha no macOS, terceira no Windows; use só a do seu sistema). Em seguida, baixam a versão Q8 recomendada. Para subir o servidor local compatível com a API OpenAI, com o modo de raciocínio ativado, use o comando llama-server do model card.

```
pip install --user "huggingface_hub[cli,hf_xet]"
brew install llama.cpp
winget install llama.cpp
hf download qvac/BotPsy-0.8B-GGUFs botpsy-0.8b-q8_0.gguf --local-dir .
```

Fonte: <https://huggingface.co/qvac/BotPsy-0.8B-GGUFs>

## Os números

Os resultados abaixo foram divulgados pela equipe e medidos em modo de raciocínio (thinking) para todos os modelos. Todos os benchmarks que usam API externa foram executados em 3 de novembro de 2026.

- BFCL v4 (uso de ferramentas): 44,0 para o BotPsy, contra 23,4 da base Qwen3.5-0.8B-Think e 37,7 do Qwen3.5-2B-Think (2,5 vezes maior).
- ACEBench (precisão em chamadas de função): 58,7 contra 30,1 da base e 55,4 do modelo maior.
- τ-bench (média de varejo, telecom e banco): 51,5 contra 23,2 da base e 46,5 do modelo maior.
- ToolSandbox (similaridade média em 8 configurações): 64,6 contra 30,5 da base e 41,2 do modelo maior.
- BrowseComp-Plus (pesquisa profunda, máximo de 30 passos): 4,5 contra 1,9 da base e 2,8 do modelo maior.
- Claw-Eval (pontuação média de tarefa): 46,5 contra 39,3 da base; o Qwen3.5-2B-Think liderou com 48,9.
- GPQA Diamond (conhecimento científico): 38,1 contra 33,2 da base.
- MMLU-Pro (conhecimento geral): 48,9 contra 41,6 da base.
- IFEval (seguimento de instruções): 90,8 contra 59,7 da base.
- IFBench (seguimento de instruções): 55,9 contra 22,0 da base.
- Respostas inseguras em red-teaming (6 categorias de dano): 21% contra 36% da base.
- Respostas inseguras sob injeção de prompt: 31% contra 46% da base.

Fonte: <https://huggingface.co/blog/qvac/botpsy>

## O que muda para você

Imagine que você quer agendar uma reunião. Em vez de abrir o app de calendário manualmente, você diz ao assistente: "marque uma reunião com a equipe na quinta às 15h". O BotPsy, rodando no próprio aparelho, interpreta o pedido e devolve uma chamada de função estruturada, como create_event com título, dia e horário. O aplicativo pede sua permissão para acessar o calendário, executa a criação e devolve o resultado ao modelo, que confirma: "evento criado para quinta-feira às 15h".

Como o processamento acontece no dispositivo, os dados da conversa não saem do aparelho. O modelo também sabe recusar quando não há ferramenta adequada, em vez de inventar uma chamada. Isso é útil em fluxos onde o usuário pode pedir algo fora do escopo, como "envie um e-mail" quando não há ferramenta de e-mail declarada.

O modelo é mais indicado para rotinas de baixa a média complexidade: agendar, buscar informação simples, controlar configurações do dispositivo, organizar arquivos. Para tarefas que exigem pesquisa profunda em várias etapas ou raciocínio complexo, os resultados ainda são modestos e um modelo maior pode ser mais adequado.

Fonte: <https://huggingface.co/qvac/BotPsy-0.8B-GGUFs>

## O que fazer hoje

1. Verifique se o seu sistema atende aos requisitos: macOS, Linux ou Windows, com cerca de 600 MB a 1 GB de RAM para a versão Q8, ou cerca de 2 GB para a versão bf16. GPU dedicada não é necessária.
2. Instale o llama.cpp: no macOS, use brew install llama.cpp; no Windows, use winget install llama.cpp.
3. Baixe o modelo recomendado (Q8_0): hf download qvac/BotPsy-0.8B-GGUFs botpsy-0.8b-q8_0.gguf --local-dir .
4. Teste com um pedido simples em português ou inglês e verifique se o modelo retorna uma chamada de ferramenta no campo tool_calls.
5. Se preferir integrar em um aplicativo, consulte o QVAC SDK (pacote @qvac/sdk no npm) e o model card oficial para exemplos de integração com Node.js e TypeScript.

Fonte: <https://huggingface.co/qvac/BotPsy-0.8B-GGUFs>

## O que conferir

- O modelo ainda comete erros e não deve ser usado em decisões de alto risco, como operações financeiras, informações pessoais sensíveis ou aplicações de saúde.
- O inglês é o idioma recomendado. O modelo foi avaliado em mais sete idiomas (chinês, francês, hindi, italiano, português, russo e espanhol) e apresenta desempenho muito inferior em hindi (24,5) e russo (57,6).
- A taxa de respostas inseguras é de 21% em red-teaming e 31% sob injeção de prompt. Em agentes que leem saídas não confiáveis de ferramentas, o risco de injeção de instruções permanece real.
- Busca de informações em várias etapas é o ponto fraco mais claro: cenários complexos de recuperação marcaram 15, contra 79 em chamadas únicas. Não confie em respostas de pesquisa profunda sem verificação.
- O modelo não é um modelo de conhecimento: foi projetado para chamar ferramentas para obter fatos que não conhece. Para perguntas de conhecimento puro, modelos maiores pontuam bem mais alto (Qwen3.5-2B-Think: 59,9 no GPQA Diamond e 65,5 no MMLU-Pro, contra 38,1 e 48,9 do BotPsy).
- Os pesos são abertos sob Apache 2.0, mas o código de treinamento e os dados não acompanham o lançamento. A licença permite uso comercial e modificação, mas a recomendação da equipe é limitar o uso a tarefas cotidianas de baixa e média complexidade.

Fonte: <https://huggingface.co/blog/qvac/botpsy>

## Glossário

- Agente: programa que usa um modelo de linguagem para decidir e executar ações, não apenas responder texto.
- BFCL v4: benchmark de chamada de funções da UC Berkeley, usado para medir quão bem um modelo invoca ferramentas corretamente.
- Function calling (chamada de função): capacidade do modelo de devolver uma chamada estruturada (nome da função e parâmetros) em vez de texto livre, para que o aplicativo execute a ação.
- GGUF: formato de arquivo para armazenar pesos de modelos de linguagem, usado pelo llama.cpp e ferramentas compatíveis.
- llama.cpp: biblioteca de código aberto para rodar modelos de linguagem localmente, em CPU ou GPU, com suporte a quantização.
- MOPD (Multi-teacher On-Policy Distillation): técnica de treinamento em que o modelo estudante gera respostas e recebe feedback de vários modelos professores maiores.
- On-device (no dispositivo): execução do modelo diretamente no aparelho do usuário, sem enviar dados para servidores externos.
- Prompt injection (injeção de prompt): ataque em que instruções maliciosas são inseridas em dados que o modelo processa, como saídas de ferramentas, para fazê-lo agir de forma indevida.
- Quantização: redução da precisão numérica dos pesos do modelo para diminuir tamanho e consumo de memória, com pequena perda de qualidade.
- Red-teaming: testes adversariais para avaliar se o modelo gera respostas inseguras ou indesejadas.
- SFT (Supervised Fine-Tuning): etapa de treinamento em que o modelo aprende imitando exemplos de respostas corretas.
- Tool calls (chamadas de ferramenta): campo da resposta do modelo que contém a função a ser executada e seus argumentos.
- τ-bench / τ²-bench / τ³-bench: benchmarks de tarefas agênticas multi-turno em domínios como varejo, telecomunicações e banco.
- DAPO: método de aprendizado por reforço usado nas etapas finais de treinamento do BotPsy.

Fonte: <https://huggingface.co/blog/qvac/botpsy>

## Para onde ir depois

- Leia o anúncio oficial no Hugging Face: huggingface.co/blog/qvac/botpsy.
- Acesse a página do modelo e o model card com exemplos de integração: huggingface.co/qvac/BotPsy-0.8B-GGUFs.
- Baixe os pesos safetensors (bf16): huggingface.co/qvac/BotPsy-0.8B.
- Consulte o modelo base Qwen3.5-0.8B: huggingface.co/Qwen/Qwen3.5-0.8B.
- Leia o paper do método DAPO usado no treinamento: arxiv.org/abs/2503.14476.
- Acesse o repositório do llama.cpp: github.com/ggml-org/llama.cpp.
- Consulte o QVAC SDK: qvac.tether.io/dev/sdk/.
- Veja o leaderboard oficial do BFCL v4: gorilla.cs.berkeley.edu/leaderboard.html.
- Teste o modelo localmente com os comandos da seção de instalação e avalie se ele atende às suas necessidades de assistente pessoal no dispositivo.

Fonte: <https://huggingface.co/blog/qvac/botpsy>

## Links citados

- https://arxiv.org/abs/2503.14476
- https://github.com/ggml-org/llama.cpp
- https://huggingface.co/Qwen/Qwen3.5-0.8B

## Além do vídeo

- Citação acadêmica do BotPsy no formato BibTeX, disponível no anúncio oficial.
- Exemplo de requisição HTTP ao endpoint /v1/chat/completions com declaração de ferramentas em JSON (create_event) e leitura dos campos reasoning_content e tool_calls, disponível no model card oficial.
- Integração com o QVAC SDK em Node.js/TypeScript: funções loadModel, completion e unloadModel com o arquivo ./models/botpsy-0.8b-q8_0.gguf, tools: true e reasoning_budget: -1, disponível no model card.
- Desempenho no Multi-IF em inglês, chinês, francês, espanhol, italiano e português, na faixa de 72 a 80 pontos.
- Figura 7 do anúncio: desempenho médio por cenário por grupo de aplicativo, separando cenários simples e complexos, com número de cenários por grupo.
- Figuras 8 e 9 do anúncio: gráficos de acurácia contra tokens de raciocínio e taxa de sucesso contra turnos de assistente, com fronteira de Pareto.
- Visão futura detalhada: Hypersearch com consultas ponto a ponto privadas, QVAC Fabric para ajuste fino local, delegação de tarefas para PCs domésticos e nós confiáveis, e comunicação agent-to-agent.
- Comparação de eficiência de raciocínio com outros modelos: LFM2.5-1.2B-Think e MiniCPM5-1B-Think escrevem raciocínio mais curto em alguns benchmarks, mas com acurácia menor que o BotPsy em cada caso.
