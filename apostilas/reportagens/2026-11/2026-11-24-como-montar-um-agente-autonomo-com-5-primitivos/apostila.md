# Como montar um agente autônomo com 5 primitivos

_2026-11-24 · reportagem_

Um agente autônomo passa a maior parte do tempo dormindo: recebe um evento, executa uma tarefa, salva o que aconteceu e volta a dormir. Cinco primitivos sustentam esse ciclo — caixa de entrada de eventos, temporizadores, memória durável, permissões e saída. Cada um tem um papel claro e, juntos, evitam duplicação, perda de contexto e uso descontrolado de credenciais.

## O ciclo do agente sempre ativo

Um agente que trabalha sozinho não fica ligado o tempo todo. Ele passa a maior parte do tempo dormindo e acorda para cumprir tarefas. Cada trecho de trabalho é uma run dentro de uma session — a transcrição de mensagens e chamadas de ferramentas daquela execução. Terminada a run, o agente salva o que aconteceu e volta a dormir, repetindo o ciclo indefinidamente.

Fonte: <https://claude.ai/en/guides/building-always-on-agents>

## Primitivo 1: caixa de entrada de eventos (event inbox)

Em vez de chamar o agente direto para cada evento, tudo é gravado numa tabela durável no banco. O handler escreve o evento nessa lista; um worker único lê os pendentes e inicia a execução. A caixa deve acompanhar o status de cada evento e permitir deduplicação por identificador único da fonte.

- Uma tabela durável (geralmente uma relação em banco) para listar os eventos
- Um handler, normalmente um endpoint HTTP, que escreve o evento na lista ao receber a notificação
- Um worker, geralmente um serviço de background, que lê os pendentes e inicia runs

Fonte: <https://claude.ai/en/guides/building-always-on-agents>

## Regra da caixa: um worker ativo por vez

Só um worker pode estar ativo por caixa de eventos. Isso impede que duas execuções disputem o mesmo evento ou sobrescrevam uma à outra. Se a caixa acumular muitos eventos, agrupe-os numa única execução para o agente responder de uma vez.

- Apenas um worker ativo por caixa
- Eventos pendentes podem ser agrupados em uma só run quando há volume
- Se o worker cair no meio de uma execução, outro worker assume o mesmo evento a partir da lista

Fonte: <https://claude.ai/en/guides/building-always-on-agents>

## Primitivo 2: temporizadores e agendador

Retornos (follow-ups) e rotinas recorrentes (schedules) ficam em outra tabela durável, separada da caixa de eventos. O agendador varre essa tabela em intervalos fixos: marca follow-ups como concluídos, atualiza o próximo horário dos schedules e joga os vencidos na caixa de entrada para o worker processar.

- Follow-up: prazo que o próprio agente define, como checar uma resposta
- Schedule: tarefa recorrente em cadência conhecida, como um boletim diário
- O agendador não inicia a run sozinho — ele apenas sinaliza o que venceu

Fonte: <https://claude.ai/en/guides/building-always-on-agents>

## Primitivo 3: memória em armazenamento durável

Instruções do usuário, notas, mensagens passadas e progresso de tarefas devem ser guardados como arquivos ou registros em banco ou objeto storage. Carregue apenas um índice no início de cada execução; o agente puxa os detalhes quando precisar. Se a informação já vive em outro sistema, como um issue tracker, salve só um ponteiro.

- Instruções do usuário: arquivo próprio, recarregado a cada run
- Notas sobre o usuário: papel, preferências e correções dadas por ele
- Mensagens passadas: para não repetir o que já foi dito
- Progresso de tarefas em andamento: resume o que foi feito e o que falta

Fonte: <https://claude.ai/en/guides/building-always-on-agents>

## Primitivo 4: permissões

A execução usa o acesso do usuário sem supervisão constante, então cada chamada de ferramenta precisa ser liberada, bloqueada ou postergada. Credenciais ficam num proxy fora do ambiente do agente, que injeta os dados antes de encaminhar a requisição. Chamadas sensíveis podem esperar aprovação e o resultado volta como evento na caixa de entrada.

- Cada tool call é decidida: prosseguir sozinho, bloquear ou aguardar aprovação
- Proxy fora do ambiente do agente injeta credenciais antes do envio
- Chamadas deferidas terminam a run atual e o resultado volta como evento para um novo run

Fonte: <https://claude.ai/en/guides/building-always-on-agents>

## Primitivo 5: caixa de saída (outbox)

Uma ferramenta de envio costuma bastar na maioria dos casos. Para dosar mensagens ou se recuperar de erros, use uma tabela de saída com um dispatcher — serviço que lê as mensagens pendentes e decide o que enviar ao usuário. Chamadas deferidas podem ir para a outbox ou aparecer direto na interface.

- A outbox é uma tabela separada de mensagens de saída
- O dispatcher lê as mensagens pendentes e decide o que entregar
- Chamadas deferidas podem sair pela outbox ou aparecer diretamente na interface

Fonte: <https://claude.ai/en/guides/building-always-on-agents>

## Como as cinco peças se encaixam

Eventos entram numa tabela durável, um worker por caixa executa, o agendador acorda o agente com follow-ups e schedules vencidos, a memória guarda só o que não dá para consultar de novo e o resultado chega ao usuário pela saída. O contexto inicial de cada run inclui system prompt, definições de ferramentas e arquivos de memória — mantenha isso enxuto e use cache de prompt para reduzir custo.

- Eventos → inbox → worker → run
- Follow-ups e schedules vencidos → dispatcher da caixa de entrada
- Memória: índice carregado no início; detalhes sob demanda
- Saída: mensagem, nada ou chamada deferida

Fonte: <https://claude.ai/en/guides/building-always-on-agents>

## Além do vídeo

- O material cita o benchmark de longo prazo em código como exemplo do custo 78% menor do Opus 5.5 frente ao Opus 5, e a queda de 40% em cargas típicas.
- O material menciona o auto memory do Claude Code e a memory tool da Messages API como implementações práticas de memória durável.
- O material explica que o contexto inicial de cada run inclui system prompt, definições de ferramentas e arquivos de memória, recomendando mantê-lo enxuto e usar cache de prompt.
- O material detalha que o worker pode agrupar eventos pendentes em uma única execução para reduzir a quantidade de respostas do agente.
- O material menciona que chamadas deferidas podem ser exibidas via cards interativos construídos com MCP Apps, além da outbox.
