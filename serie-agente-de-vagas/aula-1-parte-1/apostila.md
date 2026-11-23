# Aula 1 (1/2): instale o Zed e conecte um modelo grátis

_2026-11-23 · tutorial_

Esta apostila monta o ambiente que a série inteira usa: o editor Zed, uma conta e uma chave no OpenRouter, a pasta agente-de-vagas e um modelo gratuito no painel do agente. A série constrói agentes de IA que buscam vagas de emprego reais e escolhem as melhores. Os passos seguem o Windows; no Mac e no Linux, download e configuração são os mesmos. Ao terminar, o Zed está aberto na pasta do projeto, com um modelo marcado como free respondendo.

## O que você precisa

O Zed é o editor onde você trabalha com os agentes durante a série. O OpenRouter dá acesso a muitos modelos com uma única conta e uma única chave. Nesta série você usa só modelos gratuitos.

- Um computador com Windows, Mac ou Linux
- Navegador e internet
- Conta Google ou e-mail para criar a conta no OpenRouter
- Gerenciador de senhas ou bloco de notas seguro para guardar a chave

Fonte: <https://zed.dev/docs/installation>

## 1. Instale o Zed e escolha o tema

No navegador, abra zed.dev e clique no botão de download da versão do seu sistema. No Windows, o navegador baixa o instalador.

- Abra o arquivo baixado. Se o Windows mostrar um aviso, clique em Mais informações e depois em Executar assim mesmo. Se o botão de executar não aparecer, clique primeiro em Mais informações.
- No assistente, avance com as opções padrão. O instalador cria o ícone na área de trabalho e adiciona o Zed ao PATH.
- Na tela Welcome to Zed, escolha Light, Dark ou System e clique em Finish Setup. O tema é só visual.

Fonte: <https://zed.dev/docs/windows>

## 2. Crie a conta no OpenRouter

Em outra aba do navegador, abra openrouter.ai e entre com a conta Google ou com um e-mail. Ao entrar, você cai no painel da sua conta.

Fonte: <https://openrouter.ai/docs/api-reference/authentication>

## 3. Crie a chave de API e guarde com segurança

A chave é o identificador que o Zed envia ao OpenRouter para ele saber quem você é. Quem tem a chave usa a sua conta. Depois que você fecha a tela, a chave não aparece de novo.

- Na área de chaves, clique em Create.
- Dê o nome agente-de-vagas. O limite de crédito é opcional: com modelos gratuitos a chave não gasta crédito.
- Clique em Create de novo para confirmar. A chave aparece na tela.
- Copie a chave e cole em um gerenciador de senhas ou em um documento seguro.
- Não coloque a chave em código nem em repositório público, e não a mostre em vídeo ou print.
- Se perder a chave ou se ela vazar, apague-a e crie outra.

Fonte: <https://openrouter.ai/docs/api-reference/authentication>

## 4. Crie a pasta do projeto

O agente grava nessa pasta os arquivos que criar ao longo da série. As próximas aulas usam o nome agente-de-vagas, então se ele sair diferente, renomeie agora.

- No Explorador de Arquivos do Windows, vá até a área de trabalho.
- Crie uma pasta nova com o atalho, digite o nome e aperte Enter.

```
Ctrl+Shift+N > agente-de-vagas > Enter
```

Fonte: <https://support.microsoft.com/en-us/windows/keyboard-shortcuts-in-windows-dcc61a57-8ff0-cffe-9796-cb9706c75eec>

## 5. Abra a pasta no Zed e confie só nela

O Zed abre o projeto em modo restrito e mostra uma janela de segurança. Como o agente vai criar e editar arquivos ali, confie apenas na pasta do projeto.

Se você marcou a caixa Trust all projects in por engano, a confiança vale para a pasta acima. Abra o projeto de novo e confie só em agente-de-vagas.

- No Zed, use Open Project e escolha a pasta agente-de-vagas.
- Clique em Trust and Continue, sem marcar a caixa que confia nos projetos da pasta acima.
- O Zed mostra o projeto aberto, com a pasta vazia na lateral.

```
Open Project > agente-de-vagas > Trust and Continue
```

Fonte: <https://zed.dev/docs/worktree-trust>

## 6. Conecte o OpenRouter e escolha um modelo gratuito

Abra o painel do agente pelo ícone de estrela brilhante, no canto inferior esquerdo do Zed. Em Configure Providers, desça até OpenRouter, cole a chave e aperte Enter. A lista de modelos pode levar alguns segundos. Quando der certo, o seletor de modelos, na parte inferior do painel, deixa de mostrar Select a Model e passa a mostrar o OpenRouter.

Depois, abra uma conversa nova e escolha no seletor um modelo com free entre parênteses no nome. A lista muda com o tempo: espere carregar e escolha qualquer um marcado como free. Daí em diante, esse modelo responde às suas mensagens e o agente pode criar e editar arquivos na pasta aberta.

- Painel do agente: ícone de estrela brilhante.
- Configure Providers, depois OpenRouter, cole a chave e aperte Enter.
- Conversa nova: Ctrl+N ou o ícone + do painel.
- Seletor de modelos: escolha um com (free) no nome.

Fonte: <https://zed.dev/docs/ai/agent-panel>

## Teste e erros comuns

Confira três pontos: o Zed está aberto na pasta agente-de-vagas, o seletor de modelos mostra o OpenRouter e o modelo escolhido tem free no nome.

- Seletor preso em Select a Model: espere mais alguns segundos, abra o painel do agente de novo e confira se a chave foi colada inteira, sem caractere a mais.
- Lista de modelos vazia: o erro mais comum é a chave colada com um caractere a mais.
- Chave perdida: apague a antiga e crie outra.
- Chave exposta em vídeo ou print: use sempre a sua própria chave.
- Caixa Trust all projects in marcada: abra o projeto de novo e confie só em agente-de-vagas.

Fonte: <https://zed.dev/docs/ai/agent-panel>

## Além do vídeo

- Se preferir o teclado, abra o painel do agente pelo comando agent: new thread na paleta de comandos.
- Fechar a tela Welcome do Zed ajuda a ganhar espaço para o painel do agente.
- Quando você avançar nos projetos, vale definir uma data de expiração para a chave e trocá-la de tempos em tempos.
- O Visual Studio Code chega a um resultado parecido, com muito mais etapas para integrar serviços externos.
- A série tem cinco vídeos: Aula 1 em duas partes (esta e o plano do orquestrador, o Regente), Aula 2 em duas partes (orquestrador funcionando e o Faro, que busca as vagas) e a Aula 3 (o Prumo, que ranqueia as vagas).
