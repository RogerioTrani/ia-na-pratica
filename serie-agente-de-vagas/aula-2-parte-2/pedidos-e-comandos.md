# Pedidos e comandos: Aula 2 (2/2): crie o Faro, o agente que busca vagas reais

Os textos abaixo são os que aparecem na tela do vídeo, na ordem. Copie, cole e adapte ao seu caso.

## PASSO 1: Instale o nvm no Windows

```text
Releases > nvm-setup.exe > Mais informações > Executar assim mesmo
```

**Você deve ver:** O instalador do nvm termina sem erro.

**Se não deu certo:** Se já havia Node instalado, desinstale antes e rode o instalador de novo.

## PASSO 2: Libere scripts no PowerShell

```text
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

**Você deve ver:** O PowerShell volta à linha de comando sem mostrar erro.

**Se não deu certo:** Se reclamar de permissão, abra o PowerShell como administrador e rode de novo.

## PASSO 3: Instale a versão mais recente do Node

```text
nvm install latest
```

**Você deve ver:** O nvm instala o Node e a tela sugere o comando nvm use com o número da versão.

**Se não deu certo:** Erro de permissão: abra o PowerShell como administrador.

## PASSO 4: Ative a versão instalada do Node

```text
nvm use (com o número da versão sugerido na tela)
```

**Você deve ver:** O comando termina sem erro e o Node vira a versão padrão, com npm e npx.

**Se não deu certo:** Se falhar, confira se o PowerShell está como administrador e se o número é o da tela.

## PASSO 5: Crie a conta no Firecrawl

```text
Sign up > entrar com Google
```

**Você deve ver:** O painel da conta abre.

**Se não deu certo:** Se o login com Google falhar, entre com e-mail.

## PASSO 6: Instale o Firecrawl com o comando da tela

```text
Integrate Firecrawl myself > Continue > copiar o comando da tela e colar no PowerShell (na documentação: npx -y firecrawl-cli@latest init --all --browser)
```

**Você deve ver:** A instalação termina e configura a chave sozinha; pode pedir o login.

**Se não deu certo:** Comando errado ou sem a chave: copie o comando inteiro da tela de novo. Instalação manual: npm install -g firecrawl-cli e depois firecrawl login --api-key fc-YOUR-API-KEY (com a sua chave). Não compartilhe a chave.

## PASSO 7: Reabra o Zed e confira o Node

```text
node --version
```

**Você deve ver:** O terminal mostra um número de versão.

**Se não deu certo:** Se o Node não for reconhecido, o Zed foi aberto antes da instalação: feche e abra de novo.

## PASSO 8: Peça o plano do Faro

```text
Baseado no @plano.md, crie um segundo plano no arquivo plano-aula-2.md com o planejamento para a criação do agente buscador de vagas, que chamamos de Faro. Esse agente deve usar a ferramenta Firecrawl, já instalada e disponível como linha de comando. Caso essa ferramenta não funcione, use a ferramenta de acesso web nativa. Busque em sites como InfoJobs, Vagas, Indeed e Catho. Esse procedimento deve ser criado dentro da pasta skills.
```

**Você deve ver:** O agente cria o plano-aula-2.md, com cerca de 250 linhas.

## PASSO 9: Peça a implementação do Faro

```text
Já temos parte do projeto implementado, seguindo o @plano.md. Quero que você implemente o @plano-aula-2.md.
```

**Você deve ver:** O agente lista as pastas, vê o que existe e constrói só o que falta.

**Se não deu certo:** Se ele avisar que precisa do Node para testar, feche e abra o Zed.

## PASSO 10: Responda ao quiz do Regente

```text
Leia e siga o @AGENTS.md
```

**Você deve ver:** O Regente faz o quiz e salva o perfil em um arquivo da pasta data.

## PASSO 11: Mande o Faro buscar vagas

```text
Opção A, buscar vagas
```

**Você deve ver:** O Faro trabalha na subjanela e salva o resultado na pasta data.

**Se não deu certo:** Se a API do provedor falhar, peça ao Regente para tentar de novo.
