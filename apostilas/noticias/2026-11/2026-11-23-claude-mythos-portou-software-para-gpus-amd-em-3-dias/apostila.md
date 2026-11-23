# Claude Mythos portou software para GPUs AMD em 3 dias

_2026-11-23 · noticia_

A Anthropic disse a investidores, antes do IPO, que o Claude Mythos Preview fez em cerca de 3 dias o trabalho de software para rodar sua IA em GPUs da AMD, tarefa que a empresa estima em 6 a 12 meses. Os três dias cobrem uma etapa específica: o processamento do prompt de um modelo em GPUs AMD MI355X. A Nvidia rebate dizendo que conhece melhor o próprio chip. O que falta saber é se os chips da AMD, rodando código escrito por IA, chegam ao desempenho dos da Nvidia.

## O número: de 6 a 12 meses para cerca de 3 dias

A Anthropic contou a investidores que o Claude Mythos Preview fez o trabalho de software necessário para colocar sua IA para rodar em GPUs da AMD em cerca de três dias, com "basically no human intervention" (quase nenhuma intervenção humana).

A estimativa de seis a doze meses vem da experiência passada da empresa ao preparar novos aceleradores com engenharia tradicional. Tom Brown, cofundador e diretor de computação da Anthropic, fez a comparação e disse que o trabalho original exigia uma equipe de dezenas de engenheiros durante meses.

## O que o Mythos fez: quase 100% dos kernels

Kernels são o código de baixo nível que faz o modelo conversar com o chip. Segundo a Anthropic, o Mythos portou ou escreveu quase 100% dos kernels.

Fonte: <https://www.anthropic.com>

## O que os três dias cobrem

A nota do slide da Anthropic limita o prazo a uma etapa: o processamento do prompt de um modelo, em GPUs AMD MI355X, com desempenho útil.

O processamento do prompt é o passo em que o modelo lê e processa o que recebeu antes de começar a responder. A Anthropic não disse se a etapa de resposta entrou na conta.

- Cobertura: processamento do prompt de um modelo.
- Hardware: GPUs AMD MI355X.
- Em aberto: se a etapa de resposta entrou na conta.
- Em aberto: a velocidade do modelo nas GPUs da AMD frente às da Nvidia.

## Por que isso mexe com o CUDA

O CUDA, plataforma de programação da Nvidia, prende modelos aos chips dela. Código de baixo nível que amarra o modelo a um fabricante é parte desse fosso.

Se uma IA reescreve esse código em dias, trocar de fornecedor de chip tende a virar decisão de compra, e não um projeto de meses de engenharia.

Fonte: <https://developer.nvidia.com/cuda-zone>

## O outro lado: a posição da Nvidia

Em entrevista de abril, Jensen Huang, CEO da Nvidia, disse que a empresa também usa IA para criar os próprios kernels e que ninguém conhece a arquitetura dela melhor que a Nvidia.

Perguntado por que laboratórios como a Anthropic usam outros aceleradores, Huang chamou a Anthropic de "a unique instance, not a trend" (um caso único, não uma tendência).

## A Anthropic usa vários chips

A Anthropic já roda seus modelos em GPUs da Nvidia e da AMD, nos TPUs do Google e no Trainium da AWS. A empresa trata tudo como um único conjunto de computação.

Nvidia e AMD estão entre as sete empresas que compram US$ 26 bilhões em ações da Anthropic no IPO. Ou seja, a Nvidia financia a empresa que Huang chamou de exceção.

## O que acompanhar

Portar software para um chip novo, que era caro, parece ficar mais barato. A pergunta que decide a história é o desempenho: se os chips da AMD, rodando código escrito por IA, entregam o que os da Nvidia entregam.

## Além do vídeo

- O prospecto da Anthropic (S-1/A nº 2) diz que a empresa consegue "onboard new chip platforms in a fraction of the time it once took", sem citar número nem chip.
- A AMD tem o ROCm como equivalente ao CUDA e a ferramenta HIPify para converter código. Anush Elangovan, vice-presidente de software de IA da AMD, disse ao EE Times em abril que "Claude is better than HIPify because it has web search built in".
- Em julho, no evento Advancing AI da AMD, Tom Brown contou que um engenheiro pediu ao Claude para colocar um rack de MI355X no ar e o deixou rodando "over the weekend".
- A SemiAnalysis apontou que, com programação por agentes, cada agente precisa de GPUs para testar o próprio código. A falta de GPUs dentro da AMD pode ser um novo gargalo.
- Os chips do conjunto da Anthropic não são totalmente intercambiáveis. Os TPUs do Google, por exemplo, são cada vez mais especializados.
