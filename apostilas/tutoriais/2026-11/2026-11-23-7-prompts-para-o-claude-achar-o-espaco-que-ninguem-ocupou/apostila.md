# 7 prompts para o Claude achar o espaço que ninguém ocupou

_2026-11-23 · tutorial_

Sete prompts que fazem o Claude percorrer com você o caminho de achar um espaço que o seu mercado ainda não ocupou: do mapa do mercado até um plano de teste de 72 horas, antes de gastar dinheiro. Serve para quem vende um serviço e está cansado de disputar por preço. Você vai aprender a mapear o mercado em quatro zonas, riscar o que todo mundo já oferece, organizar as reclamações que ninguém atende, montar uma oferta difícil de comparar pela tabela de preço, achar a demanda que existe sem oferta, inverter as regras não escritas e testar qual ideia vale o investimento. No fim, você terá sete conversas prontas no Claude, com os campos para preencher, e um plano de teste de 72 horas.

## O que você terá no fim

No fim, você terá sete conversas prontas no Claude, do mapa do seu mercado até um plano de teste de 72 horas. Cada conversa devolve uma lista curta de apostas, cada uma com público, promessa e um jeito barato de testar.

Serve para quem vende um serviço e está cansado de disputar por preço. O Claude raciocina em cima do que você conta do seu mercado: ele levanta hipóteses, não pesquisa dado real de concorrente. Quem confirma é a conversa com cliente.

## Como isso funciona

Os sete prompts percorrem um caminho em ordem. Primeiro você mapeia o mercado em quatro zonas, para enxergar onde está pisando antes de criar qualquer coisa. Depois risca o que todo mundo já oferece, porque é mais fácil ver o espaço vazio depois de tirar o que está repetido.

Em seguida você organiza as reclamações que ninguém atende, monta uma oferta difícil de comparar pela tabela de preço e procura a demanda que existe sem oferta. No fim, o último prompt escolhe uma ideia e entrega um plano de teste de 72 horas, antes de você gastar dinheiro.

Cada seção de prompt traz o texto completo, pronto para copiar: preencha os campos entre colchetes e cole no Claude.

## Por que esse caminho funciona

Irritação de cliente é o caminho mais direto para uma oferta nova: o Prompt 3 transforma reclamações em grupos e padrões. Improviso é sinal de demanda que ninguém atendeu: o Prompt 5 parte do que o cliente já faz sozinho. E preço qualquer concorrente copia, enquanto um modelo de negócio inteiro é bem mais difícil: o Prompt 6 busca uma posição difícil de copiar.

Os prompts mandam o Claude não fazer perguntas, e o primeiro manda assumir o que faltar e avisar. Os prompts 1, 2 e 4 pedem que a suposição venha marcada como HIPÓTESE; o Prompt 3 pede que o que você colou fique separado do que o Claude supôs.

## Antes de começar

- Uma conta no Claude (claude.ai).
- Uma frase dizendo o que você vende e para quem.
- A lista dos concorrentes que você conhece.
- As reclamações que já ouviu de clientes, seus ou dos concorrentes, do jeito que eles falaram.
- Quanto mais concreto for o que você escrever nos campos entre colchetes, menos o Claude vai precisar supor.

Fonte: <https://claude.ai>

## Passo a passo

1. Peça ao Claude que trate o seu mercado como um mapa. Você preenche serviço, público, concorrentes e oferta; ele divide em quatro zonas (lotada, disputada, pouco explorada e espaço aberto) e devolve as três melhores oportunidades das zonas 3 e 4, com nota de 0 a 10 em cinco critérios. Resultado esperado: três oportunidades, cada uma com por que está aberta, quem compraria e o que você venderia.
2. Peça a lista do que as empresas do seu mercado normalmente oferecem, prometem ou ensinam e mande riscar o que se repete. Resultado esperado: dez frases no formato 'Todo mundo vende [X] pra [Y], mas quase ninguém resolve [Z]' e as três com mais chance de virar venda.
3. Cole as reclamações que já ouviu e peça os quatro grupos: eu queria, eu odeio, já tentei e eu pagaria por. Resultado esperado: os cinco padrões mais fortes, cada um com a dor não atendida, como o mercado resolve hoje, por que essa solução é ruim, a solução nova e como cobrar.
4. Descreva como são as ofertas hoje e peça a matriz de eliminar, reduzir, aumentar e criar. Resultado esperado: a proposta vencedora com nome, promessa, para quem é, o que entra e o que sai, mais a frase 'Somos a única [CATEGORIA] que ajuda [PÚBLICO] a [RESULTADO] sem [O QUE ELE ODEIA].'
5. Diga o seu serviço e peça para começar pelo comportamento do cliente, antes de olhar os concorrentes. Resultado esperado: as três hipóteses mais fortes, cada uma com a versão mais simples que dá para vender antes de construir qualquer coisa.
6. Peça as dez regras não escritas do seu mercado e, para cada uma, o que aconteceria se você fizesse o contrário. Resultado esperado: até três modelos de negócio e qual tem mais chance de virar uma categoria própria.
7. Cole as oportunidades dos prompts anteriores e peça a avaliação de um investidor exigente. Resultado esperado: a ideia para testar primeiro e um plano de 72 horas.

## Prompt 1 - O mapa do mercado em 4 zonas

Este passo existe para você enxergar onde está pisando antes de criar qualquer coisa. O Claude trata o seu mercado como um mapa e o divide em quatro zonas: a lotada, onde todo mundo fala e promete a mesma coisa; a disputada; a pouco explorada; e o espaço aberto, onde há procura e pouca oferta.

Você deve ver as três melhores oportunidades, com nota de zero a dez em tamanho da dor, frequência, disposição de pagar, concorrência e facilidade de explicar. Para cada uma: por que está aberta, quem compraria e o que você venderia. Se ele responder com perguntas, peça que assuma o que falta e avise.

Prompt completo. Copie, preencha os campos entre colchetes e cole no Claude.

```
Trate o meu mercado como um mapa.

Meu serviço: [SERVIÇO]
Quem eu atendo: [PÚBLICO]
Concorrentes que eu conheço: [CONCORRENTES]
O que eu vendo hoje: [OFERTA]

Divida o mercado em 4 zonas:
1. Lotada: o que todo mundo já fala, vende e promete.
2. Disputada: o que ainda funciona, mas tem muita gente brigando.
3. Pouco explorada: problemas, públicos ou formatos que recebem pouca atenção.
4. Espaço aberto: tem procura, pouca oferta e dá pra ser diferente de um jeito claro.

Pra cada oportunidade das zonas 3 e 4, dê nota de 0 a 10 em: tamanho da dor, frequência, disposição de pagar, concorrência e facilidade de explicar.

Escolha as 3 melhores e diga, de cada uma: por que tá aberta, quem compraria e o que eu venderia.

O que for suposição sua, marque como HIPÓTESE. Não faça perguntas: se faltar informação, assuma e avise.
```

## Prompt 2 - Riscar o que todo mundo já oferece

É mais fácil ver o espaço vazio depois de tirar o que está repetido. O Claude lista o que as empresas do seu mercado normalmente oferecem, prometem ou ensinam e risca o que aparece em quase todo concorrente, compete só por preço, parece cópia de outra oferta ou depende de 'fazer melhor'.

Na busca do que sobra, vale olhar para o público ignorado, o problema ignorado, o momento da jornada ignorado, o resultado pouco explorado e um jeito novo de entregar. Peça também por onde começar a ocupar a primeira das três escolhidas.

O que sobra é o que quase ninguém cobre. Você deve receber dez frases dizendo o que todo mundo vende e o que quase ninguém resolve, e as três com mais chance de virar venda. Se as frases vierem genéricas, descreva melhor o seu mercado e rode de novo.

Prompt completo. Copie, preencha os campos entre colchetes e cole no Claude.

```
Meu mercado: [MERCADO]

Liste 20 coisas que as empresas desse mercado normalmente oferecem, prometem ou ensinam.

Agora risque tudo que:
- aparece em quase todo concorrente
- compete só por preço
- parece cópia de outra oferta
- depende só de "fazer melhor"

Com o que sobrou, procure espaço em 5 direções: público ignorado, problema ignorado, momento da jornada ignorado, resultado pouco explorado e jeito novo de entregar.

Escreva 10 frases neste formato: "Todo mundo vende [X] pra [Y], mas quase ninguém resolve [Z]."

Escolha as 3 com mais chance de virar venda e diga por onde eu começaria a ocupar a primeira.

O que você não tem como saber, marque como HIPÓTESE. Não faça perguntas.
```

## Prompt 3 - As reclamações que ninguém atende

Irritação de cliente é o caminho mais direto para uma oferta nova. Você cola as reclamações que já ouviu, de clientes seus ou de concorrentes, e o Claude separa em quatro grupos: o que o cliente queria e ninguém oferece, o que ele odeia que a empresa faça, o que já tentou sem resolver e aquilo pelo que pagaria. Ele completa cada grupo com hipóteses próprias.

Você deve ver os cinco padrões mais fortes e, para cada um, a dor não atendida, como o mercado resolve hoje, por que essa solução é ruim, a solução nova e como cobrar. No fim ele aponta o padrão em que a insatisfação é mais forte e a solução atual é mais fraca.

Prompt completo. Copie, preencha os campos entre colchetes e cole no Claude.

```
Meu mercado: [MERCADO]
Meu público: [PÚBLICO]
Reclamações que eu já ouvi de clientes, meus ou de concorrentes: [COLE AQUI]

Organize as reclamações em 4 grupos:
- "Eu queria, mas ninguém oferece…"
- "Eu odeio quando a empresa…"
- "Já tentei, mas…"
- "Eu pagaria por…"

Complete cada grupo com hipóteses suas até ter 10 por grupo, sempre separando o que eu colei do que você supôs.

Aponte os 5 padrões mais fortes. Pra cada um, entregue: a dor não atendida, como o mercado resolve hoje, por que é ruim, a solução nova e como eu cobraria.

Termine escolhendo o padrão em que a insatisfação é mais forte e a solução atual é mais fraca. Não faça perguntas.
```

## Prompt 4 - Eliminar, reduzir, aumentar, criar

Este passo monta uma oferta que não se compara pela tabela de preço. Você descreve como são as ofertas do seu mercado hoje e pede uma matriz com quatro movimentos: eliminar o que todo concorrente trata como obrigatório e o cliente quase não valoriza; reduzir o que o mercado exagera; aumentar o que o cliente valoriza e recebe pouco; e criar o que quase ninguém oferece e mudaria a percepção de valor.

O Claude lista pelo menos cinco possibilidades por movimento e combina tudo em cinco propostas, avaliadas por diferenciação, vontade do mercado, facilidade de entregar e margem. Você deve ver a proposta vencedora com nome, promessa, para quem é, o que entra e o que sai, e uma frase dizendo em que você é o único.

Prompt completo. Copie, preencha os campos entre colchetes e cole no Claude.

```
Meu mercado: [MERCADO]
Como são as ofertas hoje: [DESCREVA]

Monte uma matriz com 4 movimentos:
ELIMINAR: o que todo concorrente trata como obrigatório e o cliente quase não valoriza?
REDUZIR: o que o mercado exagera e dava pra simplificar?
AUMENTAR: o que o cliente valoriza e recebe pouco?
CRIAR: o que quase ninguém oferece e mudaria a percepção de valor?

Liste pelo menos 5 possibilidades por movimento.

Combine os movimentos em 5 propostas diferentes. Avalie cada uma por: diferenciação, vontade do mercado, facilidade de entregar e margem.

Escolha a vencedora e entregue: nome da oferta, promessa, pra quem é, o que entra, o que sai e esta frase preenchida: "Somos a única [CATEGORIA] que ajuda [PÚBLICO] a [RESULTADO] sem [O QUE ELE ODEIA]."

O que for suposição sua, marque como HIPÓTESE. Não faça perguntas.
```

## Prompt 5 - A demanda que existe sem oferta

Aqui o ponto de partida muda: em vez de olhar para os concorrentes, o Claude olha para o que o cliente já faz sozinho. O que ele improvisa, o que resolve juntando duas ou três ferramentas, que tarefa ainda faz na mão, que solução feita para outra coisa ele adapta, o que compra 'quase certo' por não existir o específico e que problema tolera porque acha que não tem jeito.

Improviso é sinal de demanda que ninguém atendeu. Ele levanta pelo menos quinze hipóteses e filtra com três perguntas: acontece com frequência, resolver gera valor claro e há motivo para os concorrentes terem ignorado. Você deve ficar com as três mais fortes, cada uma com a versão mais simples que dá para vender antes de construir qualquer coisa.

Prompt completo. Copie, preencha os campos entre colchetes e cole no Claude.

```
Meu mercado: [MERCADO]
Meu serviço hoje: [SERVIÇO]

Não comece pelos concorrentes. Comece pelo comportamento do cliente:
- O que ele improvisa sozinho?
- O que ele junta usando 2 ou 3 ferramentas?
- Que tarefa ele ainda faz na mão?
- Que solução feita pra outra coisa ele adapta?
- O que ele compra "quase certo" porque não existe o específico?
- Que problema ele tolera porque acha que não tem jeito?

Levante pelo menos 15 hipóteses. Transforme cada uma em: comportamento → desejo escondido → problema sem solução → oferta possível.

Filtre com 3 perguntas: acontece com frequência? Resolver gera valor claro? Tem motivo pros concorrentes terem ignorado?

Fique com as 3 mais fortes e, pra cada uma, desenhe a versão mais simples que eu consigo vender antes de construir qualquer coisa. Não faça perguntas.
```

## Prompt 6 - Inverter as regras não escritas

Este passo busca uma posição difícil de copiar. Peça ao Claude as dez regras não escritas do seu mercado: como todo mundo cobra, como vende, que público atende, que resultado promete. Para cada regra ele pergunta o que aconteceria se você fizesse o contrário e gera vinte inversões.

Inversão absurda só para ser diferente não vale: cada uma precisa trazer um benefício real para o cliente. Depois ele classifica em diferente e inútil, diferente e interessante e pode mudar o jogo. Você deve ver até três modelos, qual tem mais chance de virar uma categoria própria e o que te impediria de fazer.

Prompt completo. Copie, preencha os campos entre colchetes e cole no Claude.

```
Meu mercado: [MERCADO]

Liste as 10 regras não escritas desse mercado. Exemplos: "todo mundo cobra assim", "todo mundo vende desse jeito", "todo mundo atende esse público", "todo mundo promete esse resultado".

Pra cada regra, pergunte: e se eu fizesse o contrário?

Gere 20 inversões. Não vale inversão absurda só pra ser diferente: cada uma precisa trazer um benefício real pro cliente.

Classifique em: diferente e inútil, diferente e interessante, pode mudar o jogo.

Pegue as que podem mudar o jogo e combine em até 3 modelos de negócio difíceis de comparar com os concorrentes.

Diga qual dos 3 tem mais chance de virar uma categoria própria e o que me impediria de fazer. Não faça perguntas.
```

## Prompt 7 - Testar antes de investir

No último prompt você cola as oportunidades que saíram dos seis anteriores e pede ao Claude que aja como um investidor exigente. Cada ideia passa por sete portões: se existe dor de verdade, se o cliente entende a oferta em uma frase, se já tem dinheiro circulando, se a concorrência direta é baixa, se você tem uma vantagem difícil de copiar, se dá para testar sem investir muito e se há espaço para crescer.

Ele aprova ou reprova em cada portão, com o motivo em uma frase, e dá a cada ideia uma nota de 0 a 100, ficando só com as acima de 75. Depois imagina que você tentou e deu errado em doze meses, lista as cinco causas mais prováveis e ajusta a ideia. Você deve ver a ideia para testar primeiro e um plano de 72 horas, com hipótese, público, promessa, oferta, mensagem de teste e o sinal mínimo para continuar ou parar.

Prompt completo. Copie, cole as ideias no campo entre colchetes e envie ao Claude.

```
Estas são as oportunidades que saíram dos prompts anteriores: [COLE AS IDEIAS]

Aja como um investidor exigente. Cada ideia passa por 7 portões:
1. Existe dor ou desejo de verdade?
2. O cliente entende a oferta em uma frase?
3. Já tem dinheiro circulando nesse mercado?
4. A concorrência direta ainda é baixa?
5. Eu tenho uma vantagem difícil de copiar?
6. Dá pra testar sem investir muito?
7. Tem espaço pra crescer depois?

Aprove ou reprove em cada portão, com o motivo em uma frase. Dê uma nota de 0 a 100 e fique só com as acima de 75.

Imagine que eu tentei e deu errado depois de 12 meses: liste as 5 causas mais prováveis e ajuste a ideia.

Termine com a ideia que você testaria primeiro e um plano de 72 horas: hipótese, público, promessa, oferta, a mensagem de teste e o sinal mínimo pra continuar ou parar. Não faça perguntas.
```

## Exemplo completo

Imagine que você vende consultoria de marketing para pequenas empresas. No Prompt 1, você preenche [SERVIÇO] com o que você vende, [PÚBLICO] com quem você atende, [CONCORRENTES] com os que você conhece e [OFERTA] com o que vende hoje. O Claude divide o mercado em quatro zonas e devolve as três melhores oportunidades das zonas 3 e 4, cada uma com nota de zero a dez nos cinco critérios.

Exemplo: no Prompt 7, você cola as oportunidades que saíram dos seis anteriores e recebe a ideia para testar primeiro, com hipótese, público, promessa, oferta, mensagem de teste e o sinal mínimo para continuar ou parar. A mensagem de teste é o que você manda para clientes reais; o sinal mínimo é o que define se você continua ou para.

## Teste de pronto

- [ ] Nenhum prompt parou para fazer pergunta.
- [ ] Nos prompts 1, 2 e 4 a suposição veio marcada como HIPÓTESE; no 3, separada do que você colou.
- [ ] O Prompt 1 devolveu três oportunidades com nota de zero a dez nos cinco critérios.
- [ ] O Prompt 2 devolveu dez frases no formato combinado e as três com mais chance de virar venda.
- [ ] O Prompt 3 devolveu os cinco padrões mais fortes, cada um com dor, solução atual, por que é ruim, solução nova e como cobrar.
- [ ] O Prompt 4 devolveu a proposta vencedora com nome, promessa, para quem é, o que entra e o que sai.
- [ ] O Prompt 5 devolveu as três hipóteses mais fortes, cada uma com a versão mais simples que dá para vender.
- [ ] O Prompt 6 devolveu até três modelos e qual tem mais chance de virar uma categoria própria.
- [ ] O Prompt 7 devolveu a ideia para testar primeiro e um plano de 72 horas.
- [ ] O teste de verdade acontece fora do Claude: pegue a mensagem de teste do plano de 72 horas, mande para clientes reais e veja se o sinal mínimo aparece.

## Erros comuns e cuidados

- O Claude raciocina em cima do que você conta do seu mercado; ele levanta hipóteses, não pesquisa dado real de concorrente. Quem confirma é a conversa com cliente.
- Se uma resposta dos prompts 1, 2 ou 4 vier sem a marca HIPÓTESE, peça de novo que ele marque as suposições.
- Se o Claude devolver perguntas no Prompt 1, peça que assuma o que falta e avise.
- Se as frases do Prompt 2 vierem genéricas, descreva melhor o seu mercado e rode de novo.
- Inversão absurda só para ser diferente não vale (Prompt 6): cada inversão precisa trazer um benefício real para o cliente.
- Hipótese não confirmada não vira investimento: teste com cliente antes de mexer no preço.
- Confira se a sua conta no Claude está ativa em claude.ai antes de começar.

## Glossário

- HIPÓTESE: suposição do Claude sobre o seu mercado, marcada para separar o que você contou do que ele imaginou.
- Zona lotada: o que todo mundo já fala, vende e promete.
- Zona disputada: o que ainda funciona, mas tem muita gente brigando.
- Zona pouco explorada: problemas, públicos ou formatos que recebem pouca atenção.
- Espaço aberto: tem procura, pouca oferta e dá para ser diferente de um jeito claro.
- Matriz dos quatro movimentos: eliminar, reduzir, aumentar e criar, para montar uma oferta que não se compara pela tabela de preço.
- Regras não escritas: como todo mundo cobra, vende, atende e promete no seu mercado.
- Inversão: fazer o contrário de uma regra não escrita, desde que traga benefício real para o cliente.
- Portões: os sete critérios pelos quais cada ideia é aprovada ou reprovada.
- Plano de 72 horas: hipótese, público, promessa, oferta, mensagem de teste e sinal mínimo para continuar ou parar.
- Sinal mínimo: o resultado que define se você continua ou para o teste.

## Plano de 7 dias

- Dia 1: rode o Prompt 1 e mapeie o mercado em quatro zonas.
- Dia 2: rode o Prompt 2 e risque o que todo mundo já oferece.
- Dia 3: rode o Prompt 3 e organize as reclamações que ninguém atende.
- Dia 4: rode o Prompt 4 e monte a matriz dos quatro movimentos.
- Dia 5: rode o Prompt 5 e ache a demanda que existe sem oferta.
- Dia 6: rode o Prompt 6 e inverta as regras não escritas.
- Dia 7: rode o Prompt 7, escolha a ideia e monte o plano de 72 horas.
- Depois dos sete dias: teste a primeira ideia com cliente real antes de mexer no preço.

## Para onde ir depois

- Rode os sete prompts na ordem, com o seu mercado nos campos.
- Teste a primeira ideia com cliente antes de mexer no preço.
- Se uma resposta vier genérica, descreva melhor o mercado e rode o prompt de novo.
- Volte aos prompts anteriores quando precisar refinar uma oportunidade.
