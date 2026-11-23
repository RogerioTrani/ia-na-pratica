# Aula 2 (1/2): faça seu orquestrador de agentes funcionar

_2026-11-23 · tutorial_

Você transforma o plano.md da Aula 1 no Regente, o orquestrador, dentro da pasta agente-de-vagas. O agente do Zed cria personas, skills, data e o AGENTS.md a partir do plano. Numa conversa nova, o Regente se apresenta e faz a primeira pergunta do quiz. O Faro, que busca vagas, fica para a parte 2.

## Antes de começar

Esta parte parte do que a Aula 1 deixou pronto. Trabalhe sempre num ambiente de desenvolvimento no seu computador, nunca de produção. Já houve agentes com acesso à produção que apagaram bancos de dados ao tentar corrigir algo. A IA é tão segura quanto você a configura.

- Zed aberto na pasta agente-de-vagas (zed.dev)
- OpenRouter com um modelo gratuito (Aula 1, parte 1) (openrouter.ai)
- Arquivo plano.md do Regente (Aula 1, parte 2)
- Ambiente de desenvolvimento no seu computador

Fonte: <https://zed.dev>

## Passos 1 e 2: complete o plano e confira a arquitetura

Abra o plano.md e, na conversa do agente, peça três partes novas, sendo a terceira o quiz ampliado para sete perguntas. Modelos baratos e gratuitos costumam usar uma arquitetura chamada mistura de especialistas (MoE), que gasta menos hardware, e por isso respondem melhor a instruções claras e explícitas.

Depois leia o desenho das camadas no plano.md. A revisão é sua: quem garante o resultado é você. Procure um agente que só busca vagas. Com uma única missão ele erra menos, e cada agente disparado começa com a janela de contexto limpa. Se o desenho estiver confuso, peça ajuste.

- Resultado esperado: o plano.md ganha as diretrizes para modelos baratos, o desenho em três camadas (usuário, Regente, agentes) e o quiz com sete perguntas.
- Se o agente não acrescentar uma das partes, repita o pedido dizendo qual delas falta.

Fonte: <https://zed.dev/docs/ai/agent-panel>

## Passos 3 e 4: peça a implementação e envie

Numa conversa do agente, escreva a frase abaixo e digite @ para escolher o plano.md na lista. O @ aponta o arquivo exato. Sem ele, o agente gasta tempo e tokens procurando na pasta. Se esqueceu a citação, apague e refaça.

Clique em Send Message ou aperte Enter. Como o plano foi escrito de ponta a ponta, o agente sabe o que se espera dele. Há uma pequena demora: espere em vez de reenviar.

- Resultado esperado: o plano.md aparece citado dentro da mensagem e o agente começa a trabalhar, mostrando o que faz.

Fonte: <https://zed.dev/docs/ai/agent-panel>

## Passo 5: libere as permissões com cuidado

O Zed para e pergunta se pode criar pastas e diretórios. Leia o pedido inteiro antes de responder. As opções são Allow once (só desta vez) ou Always for (sempre para aquela ferramenta). O Always for vale também fora deste projeto. Quer mais controle? Escolha Allow once. Quer menos paradas? Escolha Always for.

Se o agente pedir acesso a algo fora da pasta do projeto, não aceite e desconfie. Pular todas as permissões só cabe numa sandbox, um ambiente isolado. Se o agente parar de novo, leia o novo pedido antes de liberar.

- Resultado esperado: o agente segue criando pastas e arquivos dentro do projeto.

Fonte: <https://zed.dev/docs/ai/tool-permissions>

## Passos 6 e 7: mantenha e revise o que foi criado

Quando o agente terminar, clique em Keep All para manter todos os arquivos. Se o botão não aparece, o agente ainda não terminou. Olhe também o círculo de contexto ao lado do campo de mensagem: aqui ele mostra cerca de 7% da janela de 262 mil tokens do modelo. Quando a conversa passa de uns 100 a 150 mil tokens, o modelo perde o foco, e vale abrir uma conversa nova.

Na lateral do Zed, abra a lista de arquivos e confira a estrutura.

- Pasta de personas: onde ficam os agentes
- Pasta skills: as habilidades
- Pasta data: onde o Regente guarda o quiz e o perfil de quem usa
- AGENTS.md: diz à IA, ao abrir a pasta, para ler e adotar a persona do Regente
- Se faltar algo, peça ao agente que complete a estrutura do plano.

```
Keep All
```

Fonte: <https://zed.dev/docs/ai/agent-panel>

## Passos 8 e 9: teste numa conversa nova

Clique no sinal de mais para criar uma nova thread e escolha o Zed Agent. A conversa começa sem histórico nem contexto, e isso prova se o plano funciona sozinho. Se aparecer histórico, clique de novo no sinal de mais.

Escreva a frase abaixo, digite @ e escolha o AGENTS.md na lista, depois envie. "Leia e siga" deixa a instrução mais determinística. Se o agente responder como assistente comum, confira se o arquivo foi citado pela lista do @ e não só digitado.

- Resultado esperado: o agente lê o arquivo e assume a persona do Regente.

Fonte: <https://zed.dev/docs/ai/instructions>

## Confira a resposta do Regente

O Regente deve se apresentar como assistente de desenvolvimento de carreira, verificar se já existe um quiz seu e, como ainda não existe, fazer a primeira pergunta, como a área de interesse. Se isso aconteceu, o plano virou um sistema de verdade.

Não responda ao quiz agora, para não gastar requisições. Ele será respondido na parte 2. Se o Regente não se apresentar, confira se a pasta de personas e o AGENTS.md existem e refaça o pedido citando o arquivo.

## Erros comuns

- O agente para esperando permissão: leia o pedido e libere só o que faz sentido dentro da pasta do projeto.
- Aceitar tudo de uma vez ou pular todas as permissões fora de uma sandbox.
- Esquecer o @ e deixar o agente procurar o arquivo na pasta.
- Usar um plano gigante: planos pequenos funcionam melhor, então use um plano por agente.

Fonte: <https://zed.dev/docs/ai/agent-panel>

## Além do vídeo

- Quanto mais a conversa cresce, mais o modelo perde o foco (drift), por isso o agente disparado pelo orquestrador começa com a janela limpa.
- O modo que pula todas as permissões (Dangerous Skip Permissions, no Claude Code) só deve ser usado dentro de uma sandbox.
- A IA não tem o nosso senso crítico: dizer o que o agente não deve fazer é tão importante quanto dizer o que ele deve fazer. Esses limites são as proteções (guardrails).
- Software com IA exposto ao público é probabilístico: espere o pior e defina limites. Exemplo conhecido: um chatbot de atendimento que acabou escrevendo scripts em Python em vez de anotar pedidos.
- A série tem cinco partes: Aula 1 (partes 1 e 2), Aula 2 (partes 1 e 2, com o Faro na parte 2) e Aula 3, com o Prumo, que ranqueia as vagas.
