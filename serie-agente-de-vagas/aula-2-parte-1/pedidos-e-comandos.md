# Pedidos e comandos: Aula 2 (1/2): faça seu orquestrador de agentes funcionar

Os textos abaixo são os que aparecem na tela do vídeo, na ordem. Copie, cole e adapte ao seu caso.

## PASSO 1: Peça ao agente que complete o plano

```text
Acrescente ao plano.md: (a) diretrizes para modelos mais baratos, com instruções mais claras e explícitas; (b) o desenho da arquitetura em texto, com a camada do usuário, o Regente (interface principal, que coordena os agentes e consolida o resultado) e, abaixo, os agentes, sendo um deles só para buscar vagas.
```

**Você deve ver:** O plano.md ganha as diretrizes para modelos baratos e o desenho da arquitetura em camadas.

**Se não deu certo:** Se o agente não acrescentar uma das partes, repita o pedido dizendo qual delas falta.

## PASSO 3: Peça a implementação citando o plano

```text
Por favor, implemente o plano @plano.md
```

**Você deve ver:** O arquivo plano.md aparece citado dentro da mensagem.

**Se não deu certo:** Sem o @, o agente gasta tempo e tokens procurando o arquivo na pasta: apague e cite o arquivo pela lista.

## PASSO 4: Envie a mensagem ao agente

```text
Send Message (ou Enter)
```

**Você deve ver:** O agente começa a trabalhar e mostra o que está fazendo.

**Se não deu certo:** Há uma pequena demora: espere um pouco em vez de reenviar a mensagem.

## PASSO 6: Mantenha os arquivos criados

```text
Keep All
```

**Você deve ver:** Os arquivos ficam no projeto e o círculo mostra cerca de 7% da janela de 262 mil tokens usada.

**Se não deu certo:** Se o botão não aparece, o agente ainda não terminou: aguarde.

## PASSO 8: Abra uma conversa nova

```text
+ > Zed Agent
```

**Você deve ver:** Abre uma conversa vazia, sem histórico nem contexto.

**Se não deu certo:** Se aparecer histórico, essa não é a conversa nova: clique de novo no sinal de mais.

## PASSO 9: Mande ler e seguir o AGENTS.md

```text
Leia e siga o @AGENTS.md
```

**Você deve ver:** O agente lê o arquivo e assume a persona do Regente.

**Se não deu certo:** Se ele responder como assistente comum, confira se o arquivo foi citado pela lista do @ e não só digitado.
