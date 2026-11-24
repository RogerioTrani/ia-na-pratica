# OpenAI foi de 30 ferramentas a uma fábrica de agentes

_2026-11-24 · reportagem_

A equipe de desempenho da OpenAI saiu de investigações feitas à mão e chegou à Performance Factory, um sistema na nuvem em que agentes do Codex cuidam de regressões do alerta à verificação da recuperação. Esta apostila reúne os seis passos dessa evolução, as quatro peças do sistema e o resultado do primeiro fluxo, o Fluxo de Regressão. Em pouco mais de três meses, ele acompanhou mais de 1.700 investigações e identificou a causa raiz de mais de 600.

## Os seis passos, do manual à fábrica

A equipe percebeu uma evolução em como trabalhava ao ampliar o uso do Codex (chatgpt.com/codex) em desempenho. O trabalho foi do esforço manual para a parceria com máquinas e, depois, para fábricas de agentes.

- Passo 1, antes do Codex: engenheiros liam métricas e logs, comparavam traces, depuravam máquinas em operação e liam código. Para problemas repetidos, como regressões na latência do primeiro token do ChatGPT, criaram profilers de CPU e de alocação. Chegaram a mais de 30 ferramentas de desempenho.
- Passo 2, Codex como parceiro: o engenheiro pergunta "Por que isso ficou mais lento?" e investiga junto com o Codex, mesmo em um sistema que não conhece. Ainda precisa conduzir cada etapa e saber qual ferramenta usar.
- Passo 3, habilidade compartilhada: o processo de investigação virou a habilidade perf-forensics.
- Passo 4, o intermediário humano: um alerta dispara, o engenheiro copia no Codex com a habilidade certa e cola o resultado no Slack.
- Passo 5, investigações automatizadas: as investigações foram para a nuvem e um alerta inicia a sessão do Codex sozinho. O diagnóstico vai para a conversa do Slack, mas a correção e a verificação ainda dependem de pessoas.
- Passo 6, a fábrica: cada tarefa guarda estado e descobertas, e um agente assume cada etapa quando ela está pronta, do alerta à verificação da recuperação em produção.

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Passo 3: a habilidade perf-forensics

A perf-forensics registra o método da equipe de desempenho. Ela diz ao Codex quais ferramentas existem, quando usá-las e como investigar uma lentidão, para que ele tente resolver o problema por ângulos diferentes.

A equipe testou e refinou a habilidade com avaliações baseadas em regressões anteriores. Para os tipos de regressão em que se concentrou, como aumentos de latência e quedas de disponibilidade do ChatGPT, bastava entregar um alerta ao Codex e receber o diagnóstico em uma única execução, sem orientá-lo em cada etapa.

- Descobrir quando a lentidão começou
- Identificar as requisições afetadas
- Investigar se implantações ou mudanças de configuração poderiam explicá-la

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Passo 6: como a fábrica funciona

A Performance Factory acompanha o que cada tarefa ativa precisa fazer a seguir e atribui um agente quando a etapa está pronta. A tarefa mantém seu estado e suas descobertas, então o trabalho passa entre agentes e engenheiros e é retomado depois de uma revisão de código ou de uma implantação.

Um fluxo que identifica uma possível otimização pode abrir uma tarefa em outro fluxo para testá-la e implementá-la. Assim, otimizações comuns viram fluxos executados regularmente nos serviços.

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## As quatro peças do sistema

A Performance Factory tem quatro componentes. Cada um resolve uma parte do problema de manter um agente trabalhando sem um humano no meio.

- Serviço de tarefas: onde os engenheiros definem os fluxos. Todos os fluxos aparecem em uma interface, e dá para ver o que está em aberto, acompanhar o progresso e compartilhar a tarefa com um colega que tenha mais contexto.
- Loop de distribuição: verifica periodicamente quais tarefas estão prontas para a próxima etapa e atribui um agente a cada uma, iniciando um turno do Codex com as instruções do estado atual. O agente registra o progresso e move a tarefa para o próximo estado quando conclui a etapa.
- Codex na nuvem: uma API interna invoca um turno do Codex em um ambiente dentro da rede da OpenAI, com acesso aos repositórios de código e às ferramentas de observabilidade: métricas, logs, traces, perfis de CPU e snapshots de memória. O agente usa uma identidade de serviço, o que delimita suas permissões e permite identificar quais ações vieram dos agentes de desempenho. Rodar na nuvem permite executar em paralelo, sem depender de laptops abertos.
- Assinaturas de eventos: uma tarefa que precisa esperar uma pessoa ou uma implantação assina eventos, como comentários de revisão ou falhas de CI em um pull request do GitHub. Quando um evento bate com a assinatura, a tarefa volta a ficar pronta e o loop atribui um agente para continuar.

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Como um fluxo é definido

O engenheiro define o fluxo no serviço de tarefas com arquivos de configuração e prompts escritos em Markdown. A configuração lista os estados pelos quais a tarefa pode passar, as transições permitidas e quais etapas precisam de um engenheiro. Prompts separados dizem ao agente o que fazer em cada etapa.

Exemplo da OpenAI: uma tarefa de alteração de código tem um arquivo de configuração e prompts em Markdown para implementação e revisão.

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## O Fluxo de Regressão, do alerta à recuperação

Quando um dos alertas de desempenho configurados dispara, o Fluxo de Regressão abre uma tarefa que os agentes assumem. A tarefa registra status e descobertas fora do contexto de qualquer agente, para que outros agentes ou engenheiros continuem o trabalho. Os engenheiros acompanham pelo Slack ou pela interface do fluxo, acrescentam contexto e revisam as mudanças propostas.

Na etapa da causa raiz, o agente descobre quais métricas pioraram, quando começaram a mudar e quais requisições foram afetadas. Como o alerta dispara quando a métrica passa de um limite, a regressão pode ter começado horas antes, e o agente consulta o histórico para achar o início. Depois compara grupos de requisições para saber se requisições semelhantes ficaram mais lentas ou se passaram a chegar mais requisições já lentas. Então examina implantações e mudanças em feature flags e lê o código relevante.

- Detectada (sistema)
- Encontrar a causa raiz (agente)
- Propor correção (agente)
- Revisar e implantar (engenheiro)
- Verificar recuperação (agente): confere se o desempenho voltou ao nível de referência antes de marcar a tarefa como resolvida

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Resultado em pouco mais de três meses

Esse primeiro fluxo automatizou todo o processo de correção de regressões: investigação, elaboração da correção e verificação da mitigação. Em pouco mais de três meses, o Fluxo de Regressão acompanhou mais de 1.700 investigações e identificou a causa raiz de mais de 600 casos. Isso dá 17 investigações automatizadas por dia.

- Investigações acompanhadas: mais de 1.700
- Causas raiz identificadas: mais de 600
- Investigações automatizadas por dia: 17

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Para aplicar no seu time

A OpenAI espera que outras equipes de serviços aprendam com esse caminho ao adotar fluxos com agentes em outras áreas. O ponto de partida é achar onde o seu time ainda faz papel de intermediário, como o engenheiro que copia alertas para uma ferramenta e cola a resposta no Slack.

- Registre o método de investigação da equipe em uma habilidade que o agente leia
- Teste a habilidade com casos passados antes de confiar nela
- Guarde estado e descobertas na tarefa, fora do contexto de um agente só

Fonte: <https://openai.com/index/how-openai-performance-factory-keeps-chatgpt-fast/>

## Além do vídeo

- O agente opera com uma identidade de serviço, o que delimita suas permissões e marca quais ações vieram dos agentes de desempenho.
- O ambiente do Codex na nuvem dá acesso a métricas, logs, traces, perfis de CPU e snapshots de memória.
- Na etapa de causa raiz, o agente compara grupos de requisições para separar requisições semelhantes que ficaram mais lentas de um aumento de requisições já lentas.
- A estrutura de arquivos de um fluxo, com config.toml e prompts em Markdown para implementação e revisão.
- Um fluxo que identifica uma otimização possível pode abrir uma tarefa em outro fluxo para testá-la e implementá-la.
