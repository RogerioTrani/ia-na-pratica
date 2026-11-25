# Siri AI permite ações personalizadas via App Intents

_2026-11-24 · noticia_

A Apple liberou em 3/11/2026 a prévia para desenvolvedores do Siri AI. Com ela, a Siri encontra conteúdo e executa ações personalizadas de apps que usam App Intents. Para isso, o app marca as ações com @AppIntent(.tool). A prévia vale para iOS, iPadOS, macOS e visionOS, em aparelhos com Apple Intelligence e não roda no Simulador.

## O fato

A Apple liberou em 3/11/2026 a prévia para desenvolvedores do Siri AI. Com ela, a Siri encontra conteúdo e executa ações personalizadas de apps que usam App Intents.

A Siri passa a entender contexto, achar conteúdo e executar ações que vão além dos modelos definidos pelo sistema. Ela só encontra conteúdo personalizado e executa ações personalizadas que o app disponibiliza de forma explícita, por meio de App Intents. Fonte: https://developer.apple.com/documentation/appintents/siri-ai-developer-preview

Fonte: <https://developer.apple.com/documentation/appintents/siri-ai-developer-preview>

## Como expor uma ação para a Siri

Para a Siri chamar uma ação, o App Intent precisa de title, description e perform(), e recebe a marcação abaixo. Guia: https://developer.apple.com/documentation/appintents/bringing-custom-actions-and-content-to-siri

1. escreva o App Intent com title, description e perform(). Resultado: a ação fica completa para a Siri.
2. marque o App Intent com a anotação abaixo. Resultado: a Siri pode chamar a ação como ferramenta.
3. siga o guia Bringing custom actions and content to Siri. Resultado: a integração segue o caminho oficial.

```
@AppIntent(.tool)
```

Fonte: <https://developer.apple.com/documentation/appintents/bringing-custom-actions-and-content-to-siri>

## Quando o pedido dispensa o nome do app

O usuário não precisa citar o app quando ele está aberto, quando há uma Live Activity ativa ou quando a conversa na Siri já mencionou o app. Exemplo: depois de pedir uma corrida num app de transporte e acompanhar a Live Activity, a pessoa diz "Hey Siri, change my ride pickup to <a new address>".

Com o app em segundo plano, o pedido precisa citar o app. Exemplo: "Hey Siri, are the sneakers I liked in <app name> on sale?". Live Activities usam o ActivityKit: https://developer.apple.com/documentation/activitykit

Fonte: <https://developer.apple.com/documentation/activitykit>

## Buscar em um app e agir em outro

A Siri acha o conteúdo em um app, transfere para outro e executa a ação. Exemplo: "Hey Siri, send my favorite sneakers to my partner in <name of a messaging app>". Ela encontra os tênis favoritos, descobre quem é o parceiro nos Contatos e envia a informação pelo app de mensagens. Fonte: https://developer.apple.com/documentation/appintents/apple-intelligence-and-siri-ai

- App de origem: indexe a entidade no Spotlight (IndexedEntity) e conforme-a a Transferable.
- App de destino: adote o esquema sendMessage.

Fonte: <https://developer.apple.com/documentation/appintents/apple-intelligence-and-siri-ai>

## Tarefas com várias ações: app skills e card snippets

Em tarefas complexas, a Siri pode precisar de orientação extra sobre o domínio do seu app. Para isso, crie um pacote de skills no Xcode. Dentro dele, o arquivo SKILL.md leva name e description no cabeçalho YAML e as instruções em Markdown. Os card snippets exibem o conteúdo pedido com as suas views, no visual do app. Guia: https://developer.apple.com/documentation/appintents/orchestrating-complex-actions-with-app-skills. Card snippets: developer.apple.com/documentation/appintents/cardsnippet

1. no Xcode, abra o caminho de criação abaixo e escolha Skills Bundle (Skills.skillsbundle). Resultado: o pacote de skills é criado.
2. escreva o SKILL.md com name e description no cabeçalho YAML e as instruções em Markdown. Resultado: a Siri recebe a orientação do domínio do app.

```
File > New > File from Template > Skills Bundle
```

Fonte: <https://developer.apple.com/documentation/appintents/orchestrating-complex-actions-with-app-skills>

## Ferramentas para avaliar a integração

No Xcode 27.3 beta, o Siri Integration Advisor sugere melhorias nas descrições dos App Intents. O Siri Evaluations roda pedidos em targets de UI Test e mostra quais intents a Siri aciona. Download do Xcode 27.3 beta: developer.apple.com/download/applications. Documentação do Siri Evaluations: https://developer.apple.com/documentation/sirievaluations

Fonte: <https://developer.apple.com/documentation/sirievaluations>

## Requisitos e como testar

A prévia não roda no Simulador. Não é exigida nenhuma autorização especial, e a submissão pública na App Store abre na primavera de 2027. Fonte: https://developer.apple.com/news/?id=gdk2umrf

- Sistema: iOS, iPadOS, macOS ou visionOS 27.3 beta.
- Aparelho físico com Apple Intelligence.
- Conta com 13 anos ou mais.
- Idioma: inglês, francês, japonês, coreano, português ou espanhol.
- No iOS e no iPadOS, fora da União Europeia.
- Teste pelo Xcode, com perfil de desenvolvimento.
- Ou envie o build ao App Store Connect (appstoreconnect.apple.com) para testadores internos no TestFlight (developer.apple.com/testflight).

Fonte: <https://developer.apple.com/news/?id=gdk2umrf>
