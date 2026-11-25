# OpenAI foi de 30 ferramentas a uma fábrica de agentes

_2026-11-24 · reportagem_

A equipe de desempenho da OpenAI saiu de investigações feitas à mão e chegou à Performance Factory, um sistema na nuvem em que agentes do Codex cuidam de regressões. Em pouco mais de três meses, o primeiro fluxo, o Fluxo de Regressão, acompanhou mais de 1.700 investigações e identificou a causa raiz de mais de 600.

## O contexto

A equipe de desempenho da OpenAI passou de investigações feitas à mão para parceria com o Codex e, depois, para fábricas de agentes.

Antes do Codex, os engenheiros liam métricas e logs e depuravam máquinas em operação. Chegaram a mais de 30 ferramentas de desempenho.

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Linha do tempo

- Passo 1: o trabalho era manual, com mais de 30 ferramentas de desempenho.
- Passo 2: o Codex vira parceiro na investigação.
- Passo 3: o método vira a habilidade perf-forensics.
- Passo 4: o engenheiro atua como intermediário, copiando alertas no Codex.
- Passo 5: as investigações passam para a nuvem, iniciadas por alerta.
- Passo 6: a fábrica, em que um agente assume cada etapa pronta.

## Quem ganha e quem perde

A Performance Factory tem quatro peças: serviço de tarefas, loop de distribuição, Codex na nuvem e assinaturas de eventos.

O agente roda com identidade de serviço, o que delimita suas permissões. Rodar na nuvem permite executar em paralelo, sem depender de laptops abertos.

Em pouco mais de três meses, o Fluxo de Regressão acompanhou mais de 1.700 investigações e identificou a causa raiz de mais de 600. Isso dá 17 investigações automatizadas por dia.

## O que ainda não se sabe

A correção e a verificação ainda dependem de pessoas no passo 5. Só no passo 6 a fábrica assume a verificação da recuperação.

Os resultados são da própria OpenAI, medidos no seu ChatGPT.

## O que você pode fazer

A OpenAI sugere começar pelo ponto em que o seu time ainda faz papel de intermediário.

1. Registre o método de investigação da equipe em uma habilidade que o agente leia. Resultado: o agente conhece as ferramentas e o caminho da investigação.
2. Teste a habilidade com casos passados antes de confiar nela. Resultado: você mede o acerto antes de usar.
3. Guarde estado e descobertas na tarefa, fora do contexto de um agente só. Resultado: o trabalho pode passar entre agentes e engenheiros.

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>
