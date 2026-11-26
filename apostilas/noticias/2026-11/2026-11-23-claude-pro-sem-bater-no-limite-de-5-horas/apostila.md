# Claude Pro sem bater no limite de 5 horas

_2026-11-23 · noticia_

O modo opusplan do Claude Code ajuda a esticar o uso do Claude Pro ao deixar Opus no planejamento e Sonnet na execução. Esta apostila explica os limites de cinco horas e semanal, mostra como ativar o modo e acompanhar o consumo. Você vai entender o teste com Tetris, os números de custo e linhas e o custo da troca de modelo. No fim, conseguirá escolher entre manter o Pro com opusplan ou avaliar o Max conforme seu volume de uso.

## O fato

Um teste publicado em 21 de novembro de 2026 comparou duas formas de usar o Claude Code para construir o mesmo jogo: uma com Opus em toda a sessão e outra com opusplan. O modo opusplan usa Opus no planejamento e passa a execução para Sonnet depois que o plano é aprovado.

No teste com um Tetris em arquivo HTML único, a execução com opusplan teve custo estimado 16% menor que a de Opus puro. Os dois jogos funcionaram. O resultado interessa a quem usa Claude Pro e quer reduzir o consumo sem mudar para Claude Max em meses leves.

## Por que isso importa

Claude Pro tem dois tetos de consumo: um limite de sessão e um limite semanal. Os dois são compartilhados entre o app e o Claude Code. Uma sessão longa de programação usa o mesmo saldo que atende às conversas no app.

Cada mensagem pesa de um jeito. A duração da conversa, o modelo escolhido e o nível de esforço mudam o consumo. Por isso, uma quantidade fixa de mensagens não representa com precisão o saldo disponível.

A divisão entre Opus e Sonnet ataca um desses fatores: o modelo. Opus atua no planejamento, onde seu custo maior é justificado pela elaboração do plano. Sonnet assume a implementação por um custo menor. Quando existe bastante execução depois do plano, mais trabalho fica com Sonnet e a pressão sobre os limites diminui. O modo não elimina os limites.

## Como os limites do Claude Pro funcionam

O limite de sessão começa com a primeira mensagem e é renovado cinco horas depois. O limite semanal tem um reinício próprio e separado. Os dois valem para o app e para o Claude Code, então vale acompanhar os dois medidores.

Os planos são dimensionados em relação uns aos outros: Pro oferece pelo menos 5 vezes o uso do plano gratuito, e Max oferece 5 vezes o uso do Pro. Esses múltiplos descrevem volume de uso, não uma quantidade fixa de mensagens. A página Usage nas configurações e o comando /usage mostram medidores em porcentagem.

## Como acompanhar o consumo

A leitura em porcentagem serve para acompanhar a sessão e a semana sem transformar o uso em uma contagem de mensagens. O histórico ajuda a perceber se o consumo está concentrado em conversas, na programação ou em tarefas com modelos mais caros.

1. Abra a página Usage nas configurações do Claude para ver os medidores da sessão e da semana. O resultado esperado é uma leitura em porcentagem, não em mensagens.
2. No Claude Code, digite /usage para consultar o uso por ali. O comando também pode mostrar a mudança de modelo entre as causas prováveis de um cache miss.
3. Antes de uma tarefa longa, observe a barra de cinco horas e a semanal. Depois, compare os dois medidores para entender o que a sessão consumiu.
4. Leve em conta a duração da conversa, o modelo e o nível de esforço. Esses fatores mudam o consumo e explicam por que duas tarefas aparentemente semelhantes podem gastar saldos diferentes.

```
/usage
```

Fonte: <https://docs.anthropic.com/en/docs/claude-code>

## opusplan: planejar com Opus e executar com Sonnet

opusplan é o modo do Claude Code que separa planejamento e execução. Opus entra na etapa de planejamento. Depois da aprovação, Sonnet assume a construção do código.

A lógica é concentrar o modelo de maior custo na parte em que ele justifica o preço: pensar e organizar o plano. No recorte do teste, Sonnet custava metade do preço de Opus. Quanto maior a execução que sai do planejamento, mais trabalho fica no modelo de menor custo.

O modo muda a distribuição do trabalho e não cria uma nova franquia de uso. Se a execução for pequena, a vantagem pesa menos porque o planejamento ainda consome Opus. A troca para Sonnet também pode gerar uma releitura de contexto.

Fonte: <https://code.claude.com/docs/en/model-config>

## Como ativar e usar o opusplan

A ativação acontece dentro do Claude Code. O ponto central do fluxo é a aprovação do plano: antes dela, Opus trabalha no planejamento; depois dela, Sonnet assume a execução.

1. No Claude Code, digite /model opusplan. O resultado esperado é ativar o modo que separa planejamento e execução.
2. Inicie a tarefa pelo planejamento e acompanhe a elaboração do plano. Opus deve atuar nessa etapa.
3. Leia o plano antes de aprovar. A aprovação marca a passagem do planejamento para a execução.
4. Acompanhe a execução com Sonnet e use /usage para verificar a mudança de modelo. O resultado esperado é ver a troca registrada no uso.

```
/model opusplan
```

Fonte: <https://code.claude.com/docs/en/model-config>

## O teste do Tetris

O mesmo pedido básico foi dado duas vezes: construir um Tetris simples em um único arquivo HTML. Uma execução manteve Opus do início ao fim; outra usou opusplan.

As duas começaram no modo de planejamento, com esforço médio, em pastas vazias separadas e uma depois da outra, na mesma janela de cinco horas. Esse recorte manteve o ponto de partida equivalente e permitiu comparar o modo de uso dos modelos.

Nos dois resultados, o jogo abria, limpava linhas e terminava quando os blocos se acumulavam. A versão com opusplan escreveu menos linhas e teve custo estimado menor. Quem fez o teste preferiu um pouco o acabamento visual dos blocos na versão com opusplan, mas essa foi uma avaliação subjetiva. O teste também registrou uma leitura de tokens a mais na troca para Sonnet.

## Os números

Os valores abaixo pertencem ao teste do Tetris e à estrutura de planos. Cada número precisa ser lido com seu recorte para não virar uma promessa geral.

- 5 horas: é a janela do limite de sessão, que começa na primeira mensagem e é renovada depois desse período.
- 16%: foi a redução do custo estimado do opusplan em relação a Opus puro, segundo a estimativa do Claude Code.
- 239 linhas contra 431 linhas: foram os tamanhos dos dois arquivos do Tetris. Menos linhas não mede qualidade sozinho; os dois jogos funcionaram.
- US$ 0,34 contra US$ 0,40: foram os custos estimados das execuções com opusplan e Opus, respectivamente. A estimativa usa tarifas de API e não representa a fatura da assinatura.
- Mais da metade de US$ 0,34: foi a parcela da rodada com opusplan consumida só no planejamento com Opus.
- 19,3 mil tokens: foi a quantidade relida por causa do cache miss na passagem para Sonnet.
- Dois pontos na barra de sessão e nenhum na semanal: foi o consumo registrado pelos dois testes. Uma tarefa pequena não mostrou diferença no limite semanal.
- 5 vezes: Pro oferece pelo menos esse múltiplo do uso do plano gratuito, e Max oferece esse múltiplo do Pro. O valor compara volume de uso, não mensagens.

## O custo escondido da troca de modelo

Cache é o reaproveitamento de contexto que já foi processado. Quando esse reaproveitamento falha, ocorre um cache miss e parte do contexto precisa ser lida novamente.

No teste, a passagem de Opus para Sonnet causou o único cache miss. O /usage listou a mudança de modelo entre as causas prováveis e registrou 19,3 mil tokens relidos.

Esse custo entra na conta do handover. Em uma tarefa pequena, ele pode responder por uma parte relevante do valor final. Em uma execução maior, o trabalho de Sonnet pode diluir a importância dessa única releitura por tarefa.

```
/usage
```

Fonte: <https://code.claude.com/docs/en/model-config>

## Pro ou Max: quando cada plano faz sentido

Claude Max custa US$ 100 por mês. Para quem fez o teste, em um mês ruim, comprar créditos para atravessar os limites custou mais de US$ 300. Passar ao Max significaria um valor adicional de US$ 80 em relação à assinatura Pro.

Para quem esgota o Pro toda semana, Max pode fazer sentido. Para meses leves e uso variável, pagar um valor mensal fixo maior pesa mais do que o benefício.

Nesse cenário, opusplan funciona como caminho do meio: mantém Opus no planejamento, usa Sonnet na execução e reduz a pressão sobre o saldo. Ele não substitui Max para quem consistentemente precisa de muito mais uso.

Fonte: <https://www.anthropic.com/pricing>

## O que muda para você

Quem usa Claude Pro pode trocar o modelo de uma sessão sem trocar de plano. A mudança prática é começar pelo planejamento com Opus e deixar a implementação com Sonnet. Isso ajuda quando o gargalo é o consumo de sessões longas de código.

Imagine que você vai transformar uma ideia em um script Python. Opus organiza o plano, você revisa e aprova, e Sonnet escreve a implementação. O /usage ajuda a acompanhar a troca e o consumo. O ganho depende de quanto código será executado depois do plano.

Em um dia inteiro de construções, a economia pode aparecer mais claramente do que em um pequeno teste. O limite semanal continua existindo; se ele acabar sendo esgotado toda semana, a decisão sobre Max volta a entrar.

Fonte: <https://code.claude.com/docs/en/model-config>

## O que fazer hoje

Para testar a divisão de modelos, comece registrando o consumo atual e termine comparando a sessão e a semana. O objetivo é entender o efeito em uma tarefa real, sem tratar o resultado do Tetris como garantia.

1. Abra o Claude Code e consulte /usage para registrar o estado atual da sessão e da semana. O resultado esperado são os medidores em porcentagem.
2. Digite /model opusplan para ativar o modo. O resultado esperado é separar planejamento com Opus de execução com Sonnet.
3. Inicie uma tarefa de código pelo planejamento e leia o plano antes de aprovar. Opus deve atuar nessa etapa.
4. Depois da aprovação, acompanhe a execução com Sonnet. Volte ao /usage para verificar a mudança de modelo e o consumo.
5. Repita a observação ao longo de um dia de trabalho. Se o Pro for esgotado toda semana, avalie Max; se o uso for leve e variável, compare o custo do opusplan com o de Opus puro.

```
/model opusplan
```

Fonte: <https://code.claude.com/docs/en/model-config>

## O que conferir

O opusplan reduz a participação de Opus na execução, mas não remove os limites. O resultado de 16% pertence a um teste específico de Tetris, com o mesmo pedido, esforço médio e mesma janela de cinco horas.

A estimativa de custo do Claude Code usa tarifas de API. Ela ajuda a comparar execuções, mas não é o valor cobrado na assinatura. Os dois testes somaram dois pontos na barra de sessão e nada na semanal, então o teste não comprova economia semanal.

- Confira se a tarefa tem planejamento e execução suficientes para justificar a divisão. Uma execução curta deixa mais peso no planejamento com Opus.
- Observe o cache miss da troca. No teste, ele gerou a leitura de 19,3 mil tokens.
- Acompanhe sessão e semana separadamente. O consumo do app e do Claude Code é compartilhado.
- Considere duração da conversa, modelo e nível de esforço ao interpretar as porcentagens.
- Use Max como referência para quem esgota o Pro toda semana; para uso leve e variável, compare o custo mensal com os créditos eventuais.

## Glossário

- Claude Code: ferramenta do Claude usada para sessões de programação e comandos como /usage.
- Opus: modelo da Anthropic usado no planejamento do opusplan e na execução quando usado puro.
- Sonnet: modelo da Anthropic que assume a execução depois da aprovação no opusplan.
- opusplan: modo do Claude Code que usa Opus no planejamento e Sonnet na execução.
- Modo de planejamento: etapa em que o plano é elaborado antes da aprovação.
- Limite de sessão: teto que começa com a primeira mensagem e é renovado cinco horas depois.
- Limite semanal: teto com reinício separado do limite de sessão.
- Token: unidade usada para medir o texto processado ou relido.
- Cache: reaproveitamento de contexto já processado para evitar uma nova leitura.
- Cache miss: falha nesse reaproveitamento que exige ler contexto novamente.
- Handover: passagem do trabalho de Opus para Sonnet.
- Nível de esforço: ajuste que, junto do modelo e da duração da conversa, influencia o consumo.
- Tarifa de API: preço usado pela estimativa do Claude Code para calcular o custo das execuções.
- /usage: comando do Claude Code para consultar o uso.

Fonte: <https://code.claude.com/docs/en/model-config>

## Para onde ir depois

O próximo passo é repetir a divisão em uma tarefa real de código e acompanhar o uso ao longo do dia. Pratique revisar o plano antes da aprovação e observar quando Sonnet assume a execução.

Use o histórico da sessão e da semana para decidir se o Pro está suficiente. A escolha entre permanecer no Pro com opusplan e pagar Max depende da regularidade com que o limite semanal é esgotado.

- Pratique uma tarefa com planejamento definido e execução longa.
- Compare o consumo antes e depois de /model opusplan.
- Registre se houve cache miss na troca de modelo.
- Reavalie a escolha do plano depois de um dia inteiro de uso.

Fonte: <https://code.claude.com/docs/en/model-config>
