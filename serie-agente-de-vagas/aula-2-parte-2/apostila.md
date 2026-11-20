# Apostila: Aula 2 (2/2): crie o Faro, o agente que busca vagas reais

Nesta apostila você instala o Node pelo nvm, cria a conta no Firecrawl e monta o Faro, o agente que busca vagas reais com link. No fim, o resultado fica salvo na pasta data, com habilidades que faltam e contagem de correspondência. Esse arquivo é a entrada do Prumo, na Aula 3.

## Antes de começar

O Faro parte do que a Aula 2 (parte 1) deixou pronto. Os passos abaixo usam Windows.

- Windows com PowerShell
- Regente funcionando no Zed, na pasta agente-de-vagas
- Arquivos plano.md e AGENTS.md nessa pasta
- Conta Google ou e-mail para criar a conta no Firecrawl (o plano gratuito basta)

## 1. Instale o nvm e libere scripts no PowerShell

O Firecrawl é instalado pelo gerenciador de pacotes do Node, e o nvm é o jeito mais simples de ter o Node no Windows. No GitHub do nvm para Windows, em Releases, baixe e execute o nvm-setup.exe. Se o Windows mostrar um aviso, clique em Mais informações e depois em Executar assim mesmo. Se já havia Node instalado, desinstale antes e rode o instalador de novo.

Depois, no PowerShell, libere scripts só para o usuário atual. O comando permite os scripts criados no seu computador e exige assinatura de um editor confiável nos que vêm da internet. Se der permissão negada, abra o PowerShell como administrador e rode de novo.

- Releases > nvm-setup.exe > Mais informações > Executar assim mesmo
- Resultado esperado: o instalador termina sem erro e o PowerShell volta à linha de comando sem mostrar erro

```
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

Fonte: <https://github.com/coreybutler/nvm-windows>

## 2. Instale e ative o Node

Abra o PowerShell como administrador (botão direito no menu Iniciar), porque o nvm para Windows cria atalhos no sistema. Rode o comando abaixo. No fim, a tela sugere o comando nvm use com o número da versão instalada.

Rode nvm use com esse número. Sem esse passo a versão não vira a padrão. Com ele, o Node fica ativo junto com npm e npx. Se falhar, confira se o PowerShell está como administrador e se o número é o que a tela mostrou.

- Instale: nvm install latest
- Ative: nvm use (com o número da versão sugerido na tela)

```
nvm install latest
```

Fonte: <https://github.com/coreybutler/nvm-windows>

## 3. Crie a conta e instale o Firecrawl

O Firecrawl dá ao agente acesso limpo à web, com busca e raspagem (baixar o conteúdo de uma página). Muitos sites bloqueiam acesso automatizado, e a ferramenta nativa do agente costuma ser barrada. É uma sugestão: se preferir outra ferramenta, pode usar.

No site do Firecrawl, clique em Sign up, entre com a conta Google (ou com e-mail, se o login falhar) e use o plano gratuito. Na configuração, escolha Integrate Firecrawl myself, clique em Continue, copie o comando de instalação que aparece, já com a sua chave, e cole no PowerShell. A instalação configura a chave sozinha e pode pedir o login. Se perguntar por agentes de IA instalados e não achar nenhum, siga em frente.

Se o comando der erro, volte à tela e copie o comando inteiro de novo. A instalação manual, também da documentação, é o bloco abaixo. Troque fc-YOUR-API-KEY pela sua chave e não a compartilhe.

Fonte: <https://docs.firecrawl.dev/sdks/cli>

## 4. Reabra o Zed e confira o Node

O Zed só reconhece o Node depois de ser reaberto. Feche o Zed, abra de novo, abra o terminal com Ctrl+J e rode o comando abaixo. Deve aparecer um número de versão.

Se o terminal disser que o Node não é reconhecido, o Zed foi aberto antes da instalação: feche tudo e abra de novo. Esse é o erro mais comum desta aula.

```
node --version
```

## 5. Peça o plano e a implementação do Faro

Use uma conversa nova para cada pedido. Primeiro, cole o pedido que cria o plano-aula-2.md. O agente gera o arquivo com cerca de 250 linhas. Leia o que ele definiu para a ferramenta, os sites e a habilidade.

Depois, em outra conversa nova, cole o segundo pedido. O agente lista as pastas, vê o que já existe e constrói só o que falta. Se avisar que precisa do Node para testar, feche e abra o Zed. Se parar no meio, peça que continue de onde parou.

- Pedido 1: plano do Faro
- Pedido 2: implementação

Fonte: <https://zed.dev/docs/ai/agent-panel>

## 6. Responda ao quiz e mande o Faro buscar

Em uma conversa nova, escreva o pedido abaixo. O Regente se apresenta e faz o quiz: área, nível, modelo de trabalho, localização, soft skills, objetivo de carreira e habilidades técnicas. Para gastar menos requisições, peça as perguntas todas de uma vez e responda numerado. O perfil é salvo em um arquivo da pasta data. Se ele não perguntar nada, confira se você apontou o arquivo certo.

No menu do Regente, escolha a opção A, buscar vagas. O Faro roda como subagente em uma subjanela, que você pode abrir para acompanhar, e não gasta o contexto do Regente. Se o Zed ou o Firecrawl pedirem permissão, leia e libere o que fizer sentido. Se a API do provedor falhar, peça ao Regente para tentar de novo.

- Quiz: Leia e siga o @AGENTS.md
- Busca: Opção A, buscar vagas

```
Leia e siga o @AGENTS.md
```

Fonte: <https://zed.dev/docs/ai/zed-agent>

## 7. Teste: abra o arquivo de resultados

Na pasta data, abra o arquivo de resultados da busca. Ele deve listar vagas reais, cada uma com título, empresa, localização, link, habilidades que faltam e contagem de correspondência com o seu perfil. Exemplo: Desenvolvedor Web Júnior, São Paulo: 3 de 4 habilidades, falta Node.js.

Um arquivo com vagas reais e links significa que o Faro funciona. Guarde-o, porque é a entrada da Aula 3.

- Vaga sem link ou de site que exige login, como o LinkedIn: peça ao Regente nova busca só em sites abertos
- Node não reconhecido mesmo depois de instalar: feche e abra o Zed
- Comando do Firecrawl errado ou sem a chave: copie o comando inteiro da tela de configuração

## Além do vídeo

- Perfil usado no exemplo do quiz: front-end, júnior, híbrido, São Paulo, comunicação e resolução de problemas, transição de carreira, e as habilidades HTML, CSS, JavaScript, React e Git.
- Para instalar a versão estável do Node pelo nvm, o repositório indica nvm install lts, no lugar de nvm install latest.
- Um plano por agente: o plano do Faro é um segundo arquivo, apoiado no plano.md. Com os planos em Markdown, dá para reconstruir o sistema se os outros arquivos forem perdidos.
- Sites abertos funcionam melhor para a busca. O LinkedIn exige conta e não serve para este plano.
