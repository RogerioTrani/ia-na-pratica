# Como montar um agente autônomo com 5 primitivos

_2026-11-24 · reportagem_

Um agente autônomo passa a maior parte do tempo dormindo: recebe um evento, executa uma tarefa, salva o que aconteceu e volta a dormir. Cinco primitivos sustentam esse ciclo: caixa de entrada de eventos, temporizadores, memória durável, permissões e saída. Juntos, evitam duplicação, perda de contexto e uso descontrolado de credenciais.

## O contexto

Um agente que trabalha sozinho não fica ligado o tempo todo. Ele acorda para cumprir tarefas e, terminada a run, salva o que aconteceu e volta a dormir.

Cada trecho de trabalho é uma run dentro de uma session, a transcrição de mensagens e chamadas de ferramentas daquela execução.

Fonte: <https://claude.ai/en/guides/building-always-on-agents>

## Linha do tempo

- Primitivo 1: caixa de entrada de eventos, que grava tudo numa tabela durável.
- Primitivo 2: temporizadores e agendador, que sinalizam follow-ups e schedules vencidos.
- Primitivo 3: memória em armazenamento durável, que carrega só um índice no início de cada run.
- Primitivo 4: permissões, com cada chamada de ferramenta decidida.
- Primitivo 5: caixa de saída, com dispatcher que decide o que enviar.

## Quem ganha e quem perde

Só um worker pode estar ativo por caixa de eventos. Isso impede que duas execuções disputem o mesmo evento. Se a caixa acumular muitos eventos, agrupe-os numa única execução.

Credenciais ficam num proxy fora do ambiente do agente, que injeta os dados antes de encaminhar a requisição. Chamadas sensíveis podem esperar aprovação.

O contexto inicial de cada run inclui system prompt, definições de ferramentas e arquivos de memória. Mantenha isso enxuto e use cache de prompt para reduzir custo.

## O que ainda não se sabe

O agendador não inicia a run sozinho. Ele apenas sinaliza o que venceu.

O material cita o benchmark de longo prazo como exemplo do custo 78% menor do Opus 5.5 frente ao Opus 5, e a queda de 40% em cargas típicas.

Fonte: <https://claude.ai/en/guides/building-always-on-agents>

## O que você pode fazer

Monte o agente em cinco peças, nesta ordem.

1. Crie uma tabela durável de eventos, com um handler que grava cada evento e um worker que lê os pendentes. Resultado: nenhum evento se perde.
2. Guarde instruções, notas e progresso em arquivos ou registros, e carregue só um índice no início de cada run. Resultado: o agente puxa os detalhes quando precisar.
3. Coloque as credenciais num proxy fora do ambiente do agente e decida cada chamada de ferramenta. Resultado: o agente não guarda credenciais.

Fonte: <https://claude.ai/en/guides/building-always-on-agents>

## Além do vídeo

- O material menciona o auto memory do Claude Code e a memory tool da Messages API como implementações práticas de memória durável.
