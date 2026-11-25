# Claude agora instala artefatos como apps no Mac e Windows

_2026-11-25 · noticia_

Esta apostila mostra como transformar um artefato do Claude em programa no Mac ou no Windows e quais permissões pedem cuidado. Você sai com a versão mínima do aplicativo, o caminho no menu para instalar, um prompt para criar um painel de teste e uma lista do que conferir antes de dar acesso total a um app.

## O fato

A Anthropic liberou em beta o recurso Instalar como app (Install as app). Com ele, um artefato criado na conversa do Claude, como um painel de controle de pedidos, ganha ícone e janela próprios e abre como qualquer programa do computador.

O beta está chegando a todos os planos, no aplicativo do Claude para Mac e Windows. O app instalado pode mandar notificações, aparecer na barra do sistema e usar conectores, que ligam o Claude a outros serviços. O que cada app pode fazer depende da permissão que você der.

Fonte: <https://claude.com/resources/articles/install-as-app>

## Os números

- Versão mínima do aplicativo: Claude para Mac ou Windows 6.28899.0 ou mais nova.
- Planos: todos, em beta.
- Sistemas: Mac e Windows.
- Caminho para instalar: Share > Install as app, dentro do artefato.

Fonte: <https://support.claude.com/en/articles/18516354-install-an-artifact-as-an-app>

## O que muda para você

Antes, o artefato ficava perdido no meio das conversas. Agora um controle simples de pedidos, reuniões ou retornos de clientes abre direto do computador, com janela própria, e pode mandar avisos.

O que exige cuidado são as permissões. Com acesso total, o app roda programas e lê, altera ou apaga arquivos sem perguntar antes de cada ação.

Fonte: <https://claude.com/resources/articles/install-as-app>

## O que fazer hoje

Comece com um painel simples, com dados fictícios, sem conectores e sem arquivos do computador. Este é o prompt:

1. Confira se o seu Claude para Mac ou Windows está na versão 6.28899.0 ou mais nova. Com essa versão, a opção de instalar aparece no artefato.
2. Monte uma lista fictícia com cliente, etapa e prazo e mande o prompt abaixo. Você recebe um painel com três colunas, filtro por responsável e um botão que só marca a tarefa como revisada.
3. Use o painel no modo padrão, dentro do Claude, por alguns dias. Assim você descobre se ele vale a instalação.
4. Para instalar, abra o artefato e vá em Share > Install as app. O painel passa a abrir como programa, com ícone e janela próprios.
5. Na hora de dar permissão, deixe o acesso total de fora, a menos que o app seja seu ou da sua empresa. Assim o app não roda programas nem mexe nos seus arquivos sem perguntar.

```
Crie um artefato com três colunas: Hoje, Esta semana e Aguardando cliente. Inclua filtro por responsável e um botão que apenas marca a tarefa como revisada. Não use conectores nem arquivos do computador.
```

Fonte: <https://support.claude.com/en/articles/18516354-install-an-artifact-as-an-app>

## O que conferir

A Anthropic não revisa os apps antes de você instalar. Quem decide se um app é confiável é você.

- Acesso total permite rodar programas e ler, alterar ou apagar arquivos sem pedir licença a cada ação. Reserve esse nível para apps que você criou ou que a sua empresa controla.
- Antes de liberar conectores, veja a quais serviços o app vai se ligar.
- O app instalado só funciona com internet e com você conectado à conta.
- Documentos, apresentações e planilhas do Claude não podem ser instalados como app.
- O recurso está em beta e ainda está sendo liberado. Se a opção não aparecer, confira a versão do aplicativo.

Fonte: <https://claude.com/resources/articles/install-as-app>

## Além do vídeo

- O prompt completo do painel de teste, com as colunas Hoje, Esta semana e Aguardando cliente, filtro por responsável e um botão que só marca a tarefa como revisada.
- Outros usos sugeridos para um artefato instalado: controle de reuniões e de retornos de clientes.
