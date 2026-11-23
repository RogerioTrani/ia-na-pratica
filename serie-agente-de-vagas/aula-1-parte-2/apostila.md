# Aula 1 (2/2): escreva o plano do seu orquestrador de agentes

_2026-11-23 · tutorial_

Você vai pedir ao agente do Zed um plano.md que descreve o Regente, o orquestrador com quem você conversa. O plano traz a saudação, o quiz de cinco perguntas e o menu de opções. Nenhum agente é criado neste vídeo: primeiro o desenho, depois a obra. O arquivo fica na pasta agente-de-vagas e é a base do que a série constrói na Aula 2.

## Antes de começar

Esta é a parte 2 da Aula 1. Ela parte do ambiente da parte 1.

- Zed aberto na pasta agente-de-vagas
- OpenRouter configurado (Aula 1, parte 1)
- Um modelo gratuito escolhido no painel do agente
- Objetivo em mente: um orquestrador que busca vagas de emprego na área de tecnologia

Fonte: <https://zed.dev/docs/ai/zed-agent>

## Passo 1: abra uma conversa nova

No painel do agente do Zed, com a pasta agente-de-vagas aberta, pressione Ctrl+N ou clique no ícone + no topo do painel. Uma conversa limpa não carrega mensagens antigas, então o agente parte só do que você pedir agora.

Cada mensagem consome requisições e tokens (pedaços de palavras, a unidade de consumo por trás da IA). Não mande "oi" para testar: isso gasta requisições sem produzir plano.

```
Ctrl+N
```

Fonte: <https://zed.dev/docs/ai/agent-panel>

## Passos 2 a 6: escreva o pedido completo

Um agente de IA não é uma pessoa do outro lado: funciona mais como um time, e precisa de um pedido completo e explícito. Escreva as cinco partes abaixo no campo de mensagem, ainda sem enviar. A primeira linha termina com dois pontos para abrir a lista.

O Regente é o orquestrador: o único agente com quem você fala, que leva o trabalho a outros agentes. O agente de vagas só entra mapeado no plano. Sem a frase "não crie ele agora", o agente sai implementando.

Habilidade (skill) é um arquivo de texto em Markdown que especializa um agente. Não é treinamento do modelo. O Zed tem a ferramenta nativa spawn_agent, que inicia um subagente para uma tarefa delegada, e o pedido fala em ferramenta nativa de despacho para o próprio agente descobrir qual usar.

No quarto item, escreva a sequência completa, como está abaixo. Instruções vagas fazem o modelo gratuito ir para outro lado, porque ele segue o texto ao pé da letra.

- Passo 2: objetivo e nome do arquivo (primeira linha do bloco)
- Passo 3: descreva o Regente
- Passo 4: mapeie o agente de vagas, sem criá-lo
- Passo 5: dê ao Regente a habilidade de delegar
- Passo 6: descreva a rotina (playbook) do Regente, com saudação, quiz de cinco perguntas e menu

Fonte: <https://zed.dev/docs/ai/tools>

## Passo 7: envie e espere

Pressione Enter no campo de mensagem. O agente lê o pedido, pensa e cria o plano.md com a estrutura do orquestrador, tudo em uma única requisição. Um pedido bem escrito faz o trabalho de várias frases soltas e gasta menos requisições e tokens.

Demora um pouco: espere o agente avisar que criou o arquivo antes de abri-lo. Se nada acontecer por muito tempo, confira se o modelo gratuito continua escolhido no painel do agente.

```
Enter
```

Fonte: <https://zed.dev/docs/ai/agent-panel>

## Passo 8: abra o plano e revise

Abra o painel de arquivos, entre na pasta agente-de-vagas, abra o plano.md e leia com calma. A IA executa, mas o produto final é responsabilidade de quem pede, então a revisão é a sua parte.

Você deve ver um documento em Markdown, com títulos e negritos, descrevendo o Regente, as perguntas e o menu. Se algo estiver diferente do que você pediu, edite o texto ou peça o ajuste ao agente e leia de novo.

```
Ctrl+Shift+E
```

Fonte: <https://github.com/zed-industries/zed/blob/main/assets/keymaps/default-windows.json>

## Teste: confira o conteúdo do plano

A IA generativa é probabilística: ela adivinha a próxima palavra e pode errar. Se algo faltar, o pedido foi subjetivo em algum ponto. Ajuste o texto e confira de novo.

- O Regente aparece como a única interface com você
- O agente de vagas está apenas mapeado
- A habilidade de delegar está descrita
- Há uma saudação
- As cinco perguntas do quiz estão escritas (por exemplo, área de interesse, nível e modelo de trabalho)
- O menu traz as opções A e B

## Lição de casa

Altere as perguntas do quiz para a sua realidade e compartilhe o plano com a comunidade para ver se está claro. Se você quer vagas de um nicho, como fintechs ou bancos, isso entra no plano.

Guarde o plano.md. Na Aula 2, parte 1, ele vira um orquestrador funcionando.

## Além do vídeo

- A série tem cinco vídeos: Aula 1 partes 1 e 2, Aula 2 partes 1 e 2 e Aula 3. O Faro é o agente que busca as vagas (Aula 2, parte 2) e o Prumo é o que ranqueia as vagas (Aula 3).
- Quanto mais ferramentas um agente tem, mais difícil ele acerta qual usar. Por isso os agentes da série são pequenos e especializados.
- Modelos mais caros percebem nuances, enquanto os gratuitos vão ao pé da letra. Por isso o pedido precisa ser explícito.
- O plano deste vídeo é o MVP (mínimo produto viável): o menor sistema funcional que valida a ideia. Depois ele cresce.
