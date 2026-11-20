# Pedidos e comandos: Aula 1 (2/2): escreva o plano do seu orquestrador de agentes

Os textos abaixo são os que aparecem na tela do vídeo, na ordem. Copie, cole e adapte ao seu caso.

## PASSO 1: Abra uma conversa nova com o agente

```text
Ctrl+N
```

**Você deve ver:** Uma conversa vazia abre no painel do agente.

## PASSO 2: Escreva o objetivo e o nome do arquivo

```text
Vamos construir um plano no arquivo plano.md para criar um orquestrador que busque vagas de emprego na área tech:
```

**Você deve ver:** O texto aparece no campo de mensagem, ainda sem ser enviado.

**Se não deu certo:** Pedir só "oi" ou uma frase solta gasta requisições sem produzir plano.

## PASSO 3: Descreva o Regente como primeiro item

```text
Precisamos de um agente com o qual nos comunicamos, chamado Regente. Ele leva as nossas demandas para um time de agentes, ou seja, para personas específicas.
```

**Você deve ver:** O primeiro item da lista está escrito abaixo do objetivo.

## PASSO 4: Mapeie o agente de vagas, sem criá-lo

```text
O primeiro agente a ser criado deve ser o agente que busca vagas de emprego na área de tecnologia. Mas não crie ele agora, só mapeie no plano.
```

**Você deve ver:** O segundo item da lista traz o agente de vagas como apenas mapeado.

**Se não deu certo:** Sem a frase "não crie ele agora", o agente sai implementando o agente de vagas.

## PASSO 5: Dê ao Regente a habilidade de delegar

```text
Temos que dar uma habilidade (skill) ao Regente de como delegar trabalho, usando a ferramenta nativa de despacho de agentes.
```

**Você deve ver:** O terceiro item da lista descreve a habilidade de delegar.

## PASSO 6: Descreva a rotina do Regente

```text
O playbook do Regente deve seguir esta sequência: saudar o usuário; conferir se já existe um quiz de habilidades e preferências do usuário; se não existir, enviar cinco perguntas para conhecer o usuário (anote as perguntas no plano); disponibilizar um menu de opções: opção A, responder o quiz; opção B, buscar vagas de emprego (futuramente, ainda não temos esse agente).
```

**Você deve ver:** O quarto item traz a sequência: saudação, quiz de cinco perguntas e menu com as opções A e B.

**Se não deu certo:** Instruções vagas fazem o modelo gratuito ir para outro lado: escreva a sequência completa, como na tela.

## PASSO 7: Envie a mensagem e espere

```text
Enter
```

**Você deve ver:** O agente lê o pedido, pensa e cria o plano.md com a estrutura do orquestrador, em uma única requisição.

**Se não deu certo:** Demora um pouco: espere o agente terminar antes de abrir o arquivo.

## PASSO 8: Abra o plano e revise

```text
Ctrl+Shift+E
```

**Você deve ver:** O plano.md abre com a descrição do Regente, do quiz e do menu.

**Se não deu certo:** Se algo estiver diferente do que você pediu, edite o texto do plano ou peça o ajuste ao agente.
