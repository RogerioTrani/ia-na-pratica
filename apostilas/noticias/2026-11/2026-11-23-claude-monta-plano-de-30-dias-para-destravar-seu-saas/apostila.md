# Cinco pedidos ao Claude levam seu SaaS da ideia à auditoria

_2026-11-23 · noticia_

Esta apostila mostra como usar cinco pedidos em sequência no Claude para conduzir um micro-SaaS da escolha da dor até a auditoria da receita. Você vai aprender a definir a proposta de valor, limitar o MVP a três funcionalidades essenciais, pedir a estrutura e o código do produto, montar a oferta e abordar os primeiros clientes. Também verá como organizar receita, custos de API e infraestrutura, churn e CAC para analisar margem líquida, LTV/CAC e ponto de equilíbrio. Ao final, terá os comandos exatos, os resultados esperados e as conferências necessárias para usar cada etapa sem perder o fio.

## Como usar esta lista

Os cinco pedidos usam o Claude em papéis diferentes, de estrategista de produto a auditor financeiro. O Claude faz o papel de estrategista, designer e engenheiro, enquanto você conduz o trabalho, escolhe o nicho e mantém o contexto de cada etapa.

A ordem começa pela dor do público e termina nos números da operação. Cada resposta deve orientar o pedido seguinte: a ideia validada define o MVP, o MVP orienta a construção e a oferta, e a operação formada fornece os dados da auditoria. Substitua os campos entre colchetes e preserve as escolhas feitas nas etapas anteriores.

1. Por onde começar: acesse https://claude.com, substitua [nicho/público] no Comando 1 e envie o texto. O resultado esperado é uma lista de 5 dores, a indicação da que tem maior disposição a pagar e uma proposta de valor em uma frase.
2. Use a ideia validada como contexto no Comando 2. O resultado esperado é um MVP para lançar em 7 dias, com apenas 3 funcionalidades essenciais, o fluxo principal da tela inicial e a stack mais simples e barata.
3. Envie o Comando 3 com o MVP definido. O resultado esperado é a estrutura completa de arquivos e o código funcional para rodar localmente, incluindo tela de login, painel principal e integração básica de pagamento.
4. Passe para o Comando 4 usando a mesma ideia de produto. O resultado esperado é uma landing page completa, com headline clara, prova de valor, tabela de preços simples e 5 mensagens curtas para buscar os 10 primeiros clientes pagantes.
5. Separe receita, custos de API/infraestrutura, churn e CAC e substitua o campo indicado no Comando 5. O resultado esperado é o cálculo de margem líquida, LTV/CAC e ponto de equilíbrio, a indicação de onde há perda de dinheiro e 3 ações imediatas para aumentar o lucro.

Fonte: <https://claude.com/product/overview>

## Por que a ordem dos cinco pedidos importa

O primeiro pedido define qual problema merece virar produto. Uma dor urgente, recorrente e que já gera gasto financeiro oferece um ponto de partida mais concreto do que uma ideia de aplicativo escolhida sem contexto. A proposta de valor resume essa escolha e passa a orientar as próximas decisões.

O segundo pedido transforma a ideia em escopo. O limite de três funcionalidades essenciais, o fluxo da tela inicial e a stack definem o que entra na primeira versão. O terceiro pedido converte esse recorte em arquivos e código. O quarto apresenta a mesma proposta ao cliente, e o quinto examina o dinheiro da operação.

Essa continuidade evita que produto, oferta e análise falem de coisas diferentes. A auditoria usa os números da operação construída, e a página de vendas comunica a dor e a proposta de valor definidas no início. Quando um pedido seguinte muda de direção, vale retomar a escolha anterior antes de continuar.

## Ideia e validação de dor

Uma dor urgente e recorrente aparece com frequência na rotina do público e já faz esse público gastar dinheiro para resolvê-la. O gasto atual é o sinal usado pelo pedido para procurar um problema com disposição a pagar. A lista de cinco dores permite comparar caminhos antes de escolher um.

A proposta de valor em uma frase deve dizer o que o produto fará por esse público. Ela funciona como fio condutor para o MVP, a construção e a página de vendas. A indicação da dor com maior disposição a pagar ajuda a decidir por onde começar, mas a escolha continua sendo sua.

- Tecnologia: Claude, acessado em https://claude.com.
- Como começar: substitua [nicho/público] por um público específico e envie o comando.
- Resultado esperado: 5 dores urgentes e recorrentes, a indicação da de maior disposição a pagar e uma proposta de valor em uma frase.
- O que levar adiante: a dor escolhida e a frase que resume o valor entregue ao público.

```
Atue como estrategista de produto. Quero criar um micro-SaaS para [nicho/público]. Liste 5 dores urgentes e recorrentes desse público que já geram gasto financeiro hoje, indique qual tem maior disposição a pagar e defina uma proposta de valor em uma frase.
```

## Escopo e arquitetura do MVP

MVP significa produto mínimo viável. É a versão com o conjunto essencial de funções necessário para colocar a proposta em prática. O pedido limita essa versão a três funcionalidades, descreve o fluxo principal da tela inicial e escolhe uma stack simples e barata.

O alvo de 7 dias força uma decisão de prioridade. Cada funcionalidade precisa ajudar o usuário a percorrer o fluxo principal ou sustentar a entrega de valor. A stack é o conjunto de tecnologias usado para construir e colocar o produto no ar; escolher uma opção simples e barata alinha a implementação ao prazo e ao orçamento do MVP.

- Tecnologia: Claude para definir escopo, fluxo e stack do MVP.
- Como começar: envie o comando com a ideia validada e a proposta de valor da etapa anterior como contexto.
- Resultado esperado: um MVP para lançar em 7 dias, com apenas 3 funcionalidades essenciais, o fluxo principal da tela inicial e a stack mais simples e barata.
- O que conferir: se as três funções formam um produto coerente com a dor escolhida e se o fluxo inicial mostra o que o usuário deve fazer.

```
Com base na ideia validada, defina o escopo mínimo viável (MVP) para lançar em 7 dias: liste apenas as 3 funcionalidades essenciais, o fluxo principal da tela inicial e a stack mais simples e barata para colocar no ar.
```

## Construção do produto

Aqui o escopo vira um entregável técnico. A estrutura completa de arquivos organiza as partes do produto, e o código funcional implementa o que foi definido no MVP. O pedido inclui tela de login, painel principal e integração básica de pagamento.

Esses elementos cobrem acessar o produto, usar a função principal e receber o pagamento. O código é pedido pronto para rodar localmente, ou seja, para você testar no próprio computador. Depois de receber a estrutura, execute o produto e percorra o fluxo para conferir se login, painel e pagamento correspondem ao MVP.

- Tecnologia: estrutura de arquivos e código funcional gerados a partir do MVP e da stack definidos.
- Como começar: envie o comando mantendo o MVP como referência e peça a entrega para execução local.
- Resultado esperado: arquivos e código com tela de login, painel principal e integração básica de pagamento.
- O que conferir: se o produto roda localmente e se o fluxo principal funciona com as três funcionalidades essenciais.

```
Gere a estrutura completa de arquivos e o código funcional do MVP definido acima, pronto para rodar localmente, incluindo tela de login, painel principal e integração básica de pagamento.
```

## Oferta e aquisição de clientes

A página de vendas apresenta a oferta para quem chega ao produto. O pedido reúne headline clara, prova de valor e tabela de preços simples para que o visitante entenda o problema resolvido, o benefício recebido e a opção de compra. A headline é o título principal, e a prova de valor mostra por que a proposta merece atenção.

As cinco mensagens curtas atendem à busca dos dez primeiros clientes pagantes. Elas devem partir do mesmo público e da mesma proposta de valor usados no início. A meta é conquistar clientes que pagam, e não apenas pessoas que conheceram a página. Use as mensagens como abordagem direta e mantenha a oferta coerente com o que o MVP entrega.

- Tecnologia: Claude para criar a landing page e as mensagens de abordagem.
- Como começar: envie o comando com o micro-SaaS, o público e a proposta de valor definidos nas etapas anteriores.
- Resultado esperado: página de vendas completa, headline clara, prova de valor, tabela de preços simples e 5 mensagens curtas de abordagem direta.
- O que conferir: se a página explica a mesma dor resolvida pelo produto e se as mensagens buscam os 10 primeiros clientes pagantes.

```
Crie a página de vendas (landing page) completa para este micro-SaaS focada em conversão, com headline clara, prova de valor, tabela de preços simples e 5 mensagens curtas de abordagem direta para conseguir os 10 primeiros clientes pagantes.
```

## Auditoria de receita e métricas

A auditoria começa com quatro entradas: receita, custos de API/infraestrutura, churn e CAC. A receita mostra quanto entrou. Os custos de API e infraestrutura mostram parte do gasto para manter o produto funcionando. O churn indica a perda de clientes, e o CAC representa o custo para adquirir um cliente.

A margem líquida mostra o que sobra da receita depois dos custos considerados. A relação LTV/CAC compara o valor gerado pelo cliente com o custo de aquisição. O ponto de equilíbrio indica o nível em que a receita cobre os custos. Cada medida responde a uma pergunta diferente sobre a operação.

Com esses resultados, o pedido procura onde há perda de dinheiro e pede três ações imediatas para aumentar o lucro. A análise precisa manter o recorte dos números usados. Um resultado de um produto ou período não deve ser transferido para outro sem a devida comparação.

- Tecnologia: Claude atuando como auditor financeiro de SaaS.
- Como começar: substitua [colar receita, custos de API/infraestrutura, churn e CAC] pelos números da operação que está sendo analisada.
- Resultado esperado: margem líquida, LTV/CAC e ponto de equilíbrio calculados, com indicação das perdas e 3 ações imediatas para aumentar o lucro.
- O que conferir: se cada cálculo parte dos dados colados e se as ações respondem ao problema apontado pela auditoria.

```
Atue como auditor financeiro de SaaS. Analise estes números do meu micro-SaaS [colar receita, custos de API/infraestrutura, churn e CAC], calcule margem líquida, LTV/CAC e ponto de equilíbrio, aponte onde estou perdendo dinheiro e liste 3 ações imediatas para aumentar o lucro.
```

## Os números da sequência

Os números funcionam como limites de escopo e metas de trabalho. Eles dizem quantas dores comparar, quantas funções priorizar, quantas mensagens criar e quantos clientes buscar. Cada número precisa ser lido junto com o que representa, para não virar uma promessa de resultado.

O prazo de 7 dias aparece no escopo do MVP. A meta de 10 clientes aparece na aquisição. As três ações finais pertencem à auditoria financeira. Esses recortes mantêm cada pedido ligado à sua função dentro da sequência.

- 5 dores: quantidade pedida para comparar problemas do público e escolher uma direção.
- 3 funcionalidades essenciais: limite do MVP, usado para priorizar o que entra na primeira versão.
- 7 dias: alvo de lançamento definido para o MVP, sem representar uma medição de desempenho.
- 5 mensagens: quantidade pedida para a abordagem direta aos clientes.
- 10 primeiros clientes pagantes: meta de aquisição, focada em clientes que compram.
- 3 ações imediatas: quantidade de recomendações solicitadas depois da análise financeira.

## O que muda para você

Imagine que você já tem um nicho em mente e quer descobrir qual problema merece virar produto. O primeiro pedido muda o ponto de partida: em vez de escolher uma tela ou uma função, você pede uma comparação entre dores que o público já custeia hoje. A dor escolhida passa a orientar o produto e a oferta.

Exemplo: depois de receber as cinco dores, selecione a que tiver maior disposição a pagar e preserve a proposta de valor em uma frase. No pedido seguinte, entregue essa escolha como contexto e limite o MVP a três funcionalidades essenciais. Quando chegar à auditoria, use receita, custos de API/infraestrutura, churn e CAC reais para avaliar a operação construída.

## Teste de pronto

Use estas verificações depois de cada resposta. Elas mostram se o pedido foi atendido no formato esperado e ajudam a corrigir o contexto antes de avançar para a próxima etapa.

- [ ] Validação de dor: a resposta apresenta 5 dores urgentes e recorrentes, identifica a de maior disposição a pagar e define uma proposta de valor em uma frase.
- [ ] MVP: a resposta apresenta apenas 3 funcionalidades essenciais, o fluxo principal da tela inicial e uma stack simples e barata para o alvo de 7 dias.
- [ ] Construção: a resposta apresenta estrutura completa de arquivos e código funcional para rodar localmente, incluindo login, painel principal e integração básica de pagamento.
- [ ] Oferta: a resposta apresenta landing page completa, headline clara, prova de valor, tabela de preços simples e 5 mensagens curtas para buscar os 10 primeiros clientes pagantes.
- [ ] Auditoria: a resposta usa os números fornecidos, calcula margem líquida, LTV/CAC e ponto de equilíbrio, aponta perdas e lista 3 ações imediatas para aumentar o lucro.

## Cuidados

Os comandos organizam o trabalho, mas cada saída precisa ser lida como proposta. A disposição a pagar indicada na primeira etapa deve ser confrontada com a realidade do público escolhido. O mesmo vale para preço e prova de valor na página de vendas.

O pedido de código funcional descreve o que você quer receber. Antes de colocar o produto à venda, teste o login, o painel e o pagamento no ambiente local e confira se o fluxo corresponde ao MVP. O alvo de 7 dias depende do escopo mantido enxuto.

Na auditoria, a qualidade do resultado depende dos números colados. Receita, custos de API/infraestrutura, churn e CAC precisam representar a mesma operação e um período coerente para que margem, LTV/CAC e ponto de equilíbrio façam sentido.

- Requisito para começar: escolher [nicho/público] e usar a ideia validada como contexto nas etapas seguintes.
- Requisito para construir: manter o MVP limitado às 3 funcionalidades essenciais e conferir se a stack atende ao alvo de 7 dias.
- Requisito para vender: usar uma prova de valor coerente com o que o produto realmente entrega.
- Requisito para auditar: separar receita, custos de API/infraestrutura, churn e CAC da operação analisada.
- Conferência de prazo: trate 7 dias como alvo do MVP e revise o escopo se ele não couber nesse prazo.
- Conferência de pagamento: teste a integração básica de pagamento no ambiente local antes de oferecer o produto.

## Glossário

- Micro-SaaS: SaaS de escopo reduzido, voltado a um público ou problema específico.
- SaaS: modelo de software oferecido como serviço ao usuário.
- MVP: versão mínima do produto, com as funcionalidades essenciais para colocar a proposta em prática.
- Stack: conjunto de tecnologias usado para construir e colocar o produto no ar.
- Landing page: página de vendas focada em apresentar a oferta e conduzir o visitante à ação.
- Headline: título principal da página de vendas, que comunica a proposta de valor.
- Prova de valor: demonstração concreta de que a oferta resolve o problema do público.
- Conversão: passagem do visitante ou interessado para a ação desejada, como a compra.
- Churn: perda de clientes ou cancelamentos em um período.
- CAC: custo de aquisição de cliente, ou seja, quanto é gasto para conquistar um cliente.
- LTV: valor que um cliente gera durante o relacionamento com o produto.
- LTV/CAC: relação entre o valor gerado pelo cliente e o custo para adquiri-lo.
- Margem líquida: parcela da receita que resta depois dos custos considerados.
- Ponto de equilíbrio: nível de receita em que as entradas cobrem os custos.
- API: interface que permite que sistemas conversem entre si; no comando, os custos de API entram na auditoria.
- Infraestrutura: recursos necessários para manter o produto disponível e funcionando.
- Prompt: instrução enviada ao Claude para obter uma resposta ou executar uma tarefa específica.

## Para onde ir depois

O próximo passo é executar a sequência com um nicho definido. Comece pela dor, mantenha a proposta de valor como referência e só avance para a auditoria quando houver números da operação para analisar.

- Comece pelo Comando 1 e registre a dor escolhida e a proposta de valor em uma frase.
- Use essa escolha para pedir o MVP de 3 funcionalidades essenciais e a stack para o alvo de 7 dias.
- Peça a estrutura de arquivos e o código, teste localmente o login, o painel e o pagamento.
- Monte a página de vendas e use as 5 mensagens para abordar diretamente os 10 primeiros clientes pagantes.
- Quando houver números da operação, coloque receita, custos de API/infraestrutura, churn e CAC no Comando 5 e trabalhe as 3 ações imediatas.
- Consulte a visão geral oficial do Claude em https://claude.com/product/overview.

Fonte: <https://claude.com/product/overview>
