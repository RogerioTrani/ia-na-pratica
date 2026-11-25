# Tether AI Research apresenta BotPsy para uso no dispositivo

_2026-11-18 · reportagem_

A Tether AI Research apresentou em 11 de novembro de 2026 o BotPsy, um modelo de 0,8 bilhão de parâmetros feito para chamar ferramentas no próprio dispositivo. Ele parte do Qwen3.5-0.8B e mira tarefas de dificuldade baixa a média. No BFCL v4 marca 44,0 contra 23,4 da base. Os pesos são Apache 2.0 e rodam com llama.cpp.

## O contexto

A Tether AI Research apresentou em 11 de novembro de 2026 o BotPsy, um modelo de 0,8 bilhão de parâmetros feito para chamar ferramentas no próprio dispositivo. Ele parte do Qwen3.5-0.8B e mira tarefas de dificuldade baixa a média. Foi projetado para chamada de funções e fluxos de agente, e cabe em execução no próprio dispositivo.

Por ser pequeno, serve melhor para tarefas de dificuldade baixa a média. A equipe avisa que ele ainda comete erros e não se destina a usos de alto risco. Fonte: https://huggingface.co/blog/qvac/botpsy

Fonte: <https://huggingface.co/blog/qvac/botpsy>

## Como ele aciona ferramentas

O app declara as ferramentas disponíveis, como create_event para o calendário. Quando o usuário pede algo, o modelo devolve a chamada pronta no campo tool_calls da resposta, e o app a executa.

O treinamento inclui casos em que nenhuma ferramenta serve. Nesses, o modelo deve recusar em vez de inventar uma chamada. No teste de alucinação do BFCL v4, que mede justamente isso, o BotPsy fez 86,1, a maior nota entre os modelos testados. Fonte: https://huggingface.co/qvac/BotPsy-0.8B-GGUFs

- Escopo: arquivos, calendário e mensagens, entre outras tarefas de assistente pessoal.
- O app declara as ferramentas; o modelo responde com a chamada em tool_calls.

Fonte: <https://huggingface.co/qvac/BotPsy-0.8B-GGUFs>

## Resultados reportados pela equipe

No BFCL v4, o BotPsy fez 44,0. A base, Qwen3.5-0.8B-Think, fez 23,4, e o Qwen3.5-2B-Think, 2,5 vezes maior, fez 37,7. Os números são da própria equipe. A vantagem não se repete em todos os testes: no Claw-Eval, o Qwen3.5-2B-Think fica à frente (48,9 contra 46,5).

- Qwen3.5-0.8B-Think: 23,4.
- Qwen3.5-2B-Think: 37,7.
- BotPsy: 44,0.

Fonte: <https://huggingface.co/blog/qvac/botpsy>

## Como foi treinado

O treinamento passou por quatro etapas, cada uma partindo do melhor ponto da anterior. O DAPO, método usado nas rodadas de reforço, está descrito no paper de referência. Paper DAPO: https://arxiv.org/abs/2503.14476

- Ajuste fino supervisionado com conversas de uso de ferramentas, incluindo casos em que nenhuma ferramenta deve ser chamada.
- Destilação com três modelos especialistas Qwen3.5-4B (uso de ferramentas, raciocínio geral e seguir instruções), que dão retorno a cada token.
- Duas rodadas de aprendizado por reforço com o método DAPO, com recompensas calculadas por regras e verificadores.

Fonte: <https://arxiv.org/abs/2503.14476>

## Limites e segurança

Em testes automáticos de red-teaming, o BotPsy deu respostas inseguras em 21% dos casos de segurança, contra 36% da base. Sob ataques de injeção de instruções, que importam para agentes que leem saídas de ferramentas, o índice foi de 31%, contra 46% da base.

Rodar no aparelho mantém os dados locais, mas instruções maliciosas recebidas pelas ferramentas continuam sendo um risco. Não fizemos testes próprios. Fonte: https://huggingface.co/blog/qvac/botpsy

Fonte: <https://huggingface.co/blog/qvac/botpsy>

## O que ainda não se sabe

Os números são da própria equipe. Os resultados em outros testes não são sempre melhores: no Claw-Eval, o modelo maior fica à frente.

Modelo base Qwen3.5-0.8B: https://huggingface.co/Qwen/Qwen3.5-0.8B. Pesos safetensors: https://huggingface.co/qvac/BotPsy-0.8B. Pesos GGUF: https://huggingface.co/qvac/BotPsy-0.8B-GGUFs

Fonte: <https://huggingface.co/qvac/BotPsy-0.8B>

## Como rodar localmente

Licença Apache 2.0, em safetensors e GGUF (bf16, Q8, Q4). O exemplo usa a versão Q8, a recomendada. Projeto llama.cpp: https://github.com/ggml-org/llama.cpp

1. instale o llama.cpp com brew install llama.cpp (macOS) ou winget install llama.cpp (Windows). Resultado: o llama.cpp fica disponível no computador.
2. baixe o botpsy-0.8b-q8_0.gguf na pasta atual. Resultado: o arquivo do modelo fica no seu computador.
3. abra o llama-server com o modelo. Resultado: o servidor local fica ativo.

Fonte: <https://huggingface.co/qvac/BotPsy-0.8B-GGUFs>
