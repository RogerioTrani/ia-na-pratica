# Siri AI permite ações personalizadas via App Intents

_2026-11-24 · noticia_

A Apple liberou em 3/11/2026 a prévia para desenvolvedores do Siri AI. Com ela, a Siri encontra conteúdo e executa ações personalizadas de apps que usam App Intents. A apostila mostra o que marcar no código, como a Siri entende o pedido, como guiar tarefas complexas, quais ferramentas do Xcode ajudam e quem consegue testar hoje.

## O que a prévia permite

A Siri passa a entender contexto, achar conteúdo e executar ações que vão além dos modelos definidos pelo sistema. Ela só encontra conteúdo personalizado e executa ações personalizadas que o app disponibiliza de forma explícita, por meio de App Intents.

A prévia vale para iOS, iPadOS, macOS e visionOS, em aparelhos com Apple Intelligence.

Fonte: <https://developer.apple.com/documentation/appintents/siri-ai-developer-preview>

## Como expor uma ação para a Siri

Para a Siri chamar uma ação, o App Intent precisa de title, description e perform(), e recebe a marcação abaixo.

- Escreva o App Intent com title, description e perform().
- Marque o App Intent com @AppIntent(.tool).
- Siga o guia Bringing custom actions and content to Siri.

```
@AppIntent(.tool)
```

Fonte: <https://developer.apple.com/documentation/appintents/bringing-custom-actions-and-content-to-siri>

## Quando o pedido dispensa o nome do app

O usuário não precisa citar o app quando ele está aberto, quando há uma Live Activity ativa ou quando a conversa na Siri já mencionou o app. Exemplo: depois de pedir uma corrida num app de transporte e acompanhar a Live Activity, a pessoa diz "Hey Siri, change my ride pickup to <a new address>".

Com o app em segundo plano, o pedido precisa citar o app. Exemplo: "Hey Siri, are the sneakers I liked in <app name> on sale?".

- Live Activities usam o ActivityKit: developer.apple.com/documentation/activitykit

Fonte: <https://developer.apple.com/documentation/activitykit>

## Buscar em um app e agir em outro

A Siri acha o conteúdo em um app, transfere para outro e executa a ação. Exemplo: "Hey Siri, send my favorite sneakers to my partner in <name of a messaging app>". Ela encontra os tênis favoritos, descobre quem é o parceiro nos Contatos e envia a informação pelo app de mensagens.

- App de origem: indexe a entidade no Spotlight (IndexedEntity) e conforme-a a Transferable.
- App de destino: adote o esquema sendMessage.

Fonte: <https://developer.apple.com/documentation/appintents/apple-intelligence-and-siri-ai>

## Tarefas com várias ações: app skills e card snippets

Em tarefas complexas, a Siri pode precisar de orientação extra sobre o domínio do seu app. Para isso, crie um pacote de skills no Xcode. Dentro dele, o arquivo SKILL.md leva name e description no cabeçalho YAML e as instruções em Markdown.

Os card snippets exibem o conteúdo pedido com as suas views, no visual do app.

- No Xcode: File > New > File from Template > Skills Bundle (Skills.skillsbundle).
- Guia: Orchestrating complex actions with app skills.
- Card snippets: developer.apple.com/documentation/appintents/cardsnippet

```
File > New > File from Template > Skills Bundle
```

Fonte: <https://developer.apple.com/documentation/appintents/orchestrating-complex-actions-with-app-skills>

## Ferramentas para avaliar a integração

No Xcode 27.3 beta, o Siri Integration Advisor sugere melhorias nas descrições dos App Intents. O Siri Evaluations roda pedidos em targets de UI Test e mostra quais intents a Siri aciona.

- Download do Xcode 27.3 beta: developer.apple.com/download/applications
- Documentação do Siri Evaluations: developer.apple.com/documentation/sirievaluations

Fonte: <https://developer.apple.com/documentation/sirievaluations>

## Requisitos e como testar

A prévia não roda no Simulador. Não é exigida nenhuma autorização especial, e a submissão pública na App Store abre na primavera de 2027.

- Sistema: iOS, iPadOS, macOS ou visionOS 27.3 beta.
- Aparelho físico com Apple Intelligence.
- Conta com 13 anos ou mais.
- Idioma: inglês, francês, japonês, coreano, português ou espanhol.
- No iOS e no iPadOS, fora da União Europeia.
- Teste pelo Xcode, com perfil de desenvolvimento.
- Ou envie o build ao App Store Connect (appstoreconnect.apple.com) para testadores internos no TestFlight (developer.apple.com/testflight).

Fonte: <https://developer.apple.com/news/?id=gdk2umrf>

## Além do vídeo

- Pedidos ambíguos que pedem app skills, como "Siri, compare shoes on sale that match my style" e "Hey Siri, are prices for sneakers I like lower than usual?".
- O protocolo ToolIntent identifica um app intent que a Siri pode chamar ao tratar um pedido.
- O protocolo GenerableEntity e as macros @AppEntity indicam entidades transitórias cujos valores o modelo pode gerar sozinho.
- O Siri Evaluations também ajuda a detectar mudanças na resposta da Siri conforme você atualiza intents e entidades.
- Notas de versão do Xcode 27.3: developer.apple.com/go/?id=xcode-27_3-sdk-rn. Ajuda do App Store Connect sobre testadores internos: developer.apple.com/help/app-store-connect/test-a-beta-version/add-internal-testers.
