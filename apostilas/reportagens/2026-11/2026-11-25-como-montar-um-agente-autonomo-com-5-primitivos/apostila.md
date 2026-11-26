# Como montar um agente autônomo com 5 primitivos

_2026-11-25 · reportagem_

Um agente autônomo dorme, acorda com um evento, executa a tarefa e salva o que aconteceu antes de voltar a dormir. Cinco peças sustentam esse ciclo: caixa de eventos, temporizadores, memória, permissões e saída de mensagens. A montagem começa pela caixa de entrada, com um trabalhador só, e acrescenta as outras peças em seguida. O barateamento foi maior nas tarefas longas, e foi isso que trouxe esse modelo de volta.

## Por que os agentes autônomos voltaram

O modelo mais novo entende melhor a intenção do usuário e sabe quando entrar em contato. Somado a isso, a inteligência ficou mais barata, e o maior ganho apareceu nas tarefas longas.

Em um benchmark de programação de longo prazo, o custo por tarefa resolvida caiu 78% com o modelo mais novo em relação ao anterior. Nas tarefas típicas do dia a dia, a queda foi de 40%.

- Tarefa longa: 78% menos por tarefa resolvida
- Rotina: 40% menos

## O ciclo de uma execução

O agente passa a maior parte do tempo dormindo. Cada despertar gera uma execução: ele recebe um evento, faz a tarefa, salva o que aconteceu e volta a dormir.

Uma execução roda dentro de uma sessão, o histórico de mensagens e chamadas de ferramenta. Eventos que dão continuidade a um trabalho anterior retomam a sessão existente; os demais abrem uma sessão nova.

- Acorda com um evento
- Executa a tarefa
- Salva o que aconteceu
- Volta a dormir e repete o ciclo

## Caixa de entrada de eventos

Todas as fontes escrevem numa lista durável, e um trabalhador pega o que está pendente. Dois eventos que chegam juntos não disputam a mesma execução, e uma falha não apaga o pedido.

A versão simples tem três partes: uma lista durável de eventos, em geral uma tabela no banco de dados; um handler, normalmente um endpoint HTTP, que grava os eventos; e um trabalhador, um serviço em segundo plano, que lê a lista.

- Lista durável de eventos, normalmente uma tabela no banco
- Handler, em geral um endpoint HTTP, que grava os eventos
- Trabalhador, um serviço em segundo plano, que lê e executa
- A caixa guarda o status de cada evento e permite deduplicar pelos identificadores da fonte
- Comece com uma caixa por usuário

## Um trabalhador ativo por caixa

Cada caixa de entrada deve ter um trabalhador ativo por vez. Assim, duas execuções não repetem trabalho nem sobrescrevem uma à outra.

Quando um evento chega no meio de uma execução, há três saídas: empurrar para a próxima, incluir na atual ou interromper e reiniciar. Eventos pendentes em sequência podem ser agrupados numa execução só, para o agente responder uma vez.

- Um trabalhador ativo por caixa de entrada
- Evento no meio da execução: vai para a próxima, entra na atual ou interrompe e reinicia
- Agrupe mensagens seguidas em uma resposta só
- O handler responde rápido; verificações mais profundas ficam para a execução

## Temporizadores e agendador

Os temporizadores fazem o agente acordar sozinho. Há os lembretes, prazos que ele marca para si, e as rotinas, tarefas recorrentes em uma cadência conhecida. Eles ficam numa tabela própria, separada da caixa de eventos.

Um agendador varre essa tabela em intervalos fixos. No que venceu, ele marca o lembrete como feito ou atualiza a próxima ocorrência da rotina, grava um evento na caixa e acorda o trabalhador.

- Lembrete: prazo que o agente marca para si
- Rotina: tarefa recorrente em cadência conhecida
- Tabela de temporizadores separada da caixa de eventos
- Agendador varre a tabela, atualiza cada timer e cria o evento na caixa

## Memória durável

A memória fica em arquivos que sobrevivem ao trabalhador e às sessões. Vale guardar só o que o agente não consegue consultar de novo; se o dado já está em outro sistema, salve a indicação de onde achar.

Os arquivos ficam em armazenamento durável, como um banco de dados ou um armazenamento de objetos. No começo de cada execução, o agente carrega o prompt do sistema, as definições de ferramentas e os arquivos de memória.

- Guarde só o que não dá para buscar em outra fonte
- Se o dado vive em outro sistema, salve o caminho
- Use armazenamento durável para a memória sobreviver ao trabalhador
- Mantenha o contexto inicial enxuto

## Permissões, o maior risco

A execução carrega o acesso do usuário e corre sem ninguém olhando. Para cada chamada de ferramenta, o agente decide entre seguir, bloquear ou esperar aprovação.

As credenciais ficam num proxy fora do ambiente do agente. Ele envia a requisição sem credenciais e o proxy injeta as reais antes de encaminhar. Ações arriscadas esperam uma resposta, que volta como evento e retoma a sessão salva.

- Credenciais em um proxy fora do agente
- O agente envia a requisição sem credenciais; o proxy coloca as reais
- Ações de maior risco esperam a aprovação do usuário
- A resposta volta como evento e a sessão é retomada

## Ordem para montar

Comece pela caixa de entrada, com um trabalhador só. Depois encaixe os temporizadores, a memória durável, as permissões e, por último, a saída de mensagens.

O agente dorme, acorda com um evento, faz o trabalho e anota o que aprendeu. Com uma caixa por usuário e memória só do que não dá para buscar, as cinco peças mantêm o agente trabalhando quando você sai.

- Eventos em tabela durável
- Um trabalhador ativo por caixa
- Temporizadores viram eventos
- Memória só do que não dá para achar
- Credenciais fora do agente
- Saída de mensagens separada

## Além do vídeo

- Dreaming: uma revisão das sessões passadas para curar memórias, trocando entradas desatualizadas e encontrando padrões que só aparecem em várias execuções.
- Auto mode: classificadores revisam ações de maior risco e bloqueiam as consideradas perigosas, mesmo sem o usuário por perto.
- Os quatro tipos de memória: instruções do usuário, notas sobre o usuário, mensagens passadas e progresso de cada tarefa.
- Contexto inicial enxuto e prompt caching para reduzir o custo de cada execução.
- Evals para ajustar o volume de mensagens: agente que envia demais vira ruído, e o que envia de menos deixa passar informação importante.
