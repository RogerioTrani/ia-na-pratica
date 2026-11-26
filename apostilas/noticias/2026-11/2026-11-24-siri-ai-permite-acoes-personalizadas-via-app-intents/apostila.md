# Siri AI permite ações personalizadas via App Intents

_2026-11-24 · noticia_

A Apple liberou em 3 de novembro de 2026 o Siri AI Developer Preview, uma prévia que permite à Siri entender contexto, encontrar conteúdo e executar ações personalizadas dos aplicativos. A integração passa pelo framework App Intents e pela macro @AppIntent(.tool), e cobre desde pedidos que dispensam o nome do app até ações que cruzam dois aplicativos. A documentação oficial inclui guias, exemplos de código, pacotes de skills, snippets visuais e ferramentas de avaliação no Xcode 27.3 beta. Para testar, são necessários dispositivo físico com Apple Intelligence, versão 27.3 beta do sistema, conta com 13 anos ou mais e um dos seis idiomas suportados. A submissão pública na App Store abre na primavera de 2027.

## O fato

A Apple liberou em 3 de novembro de 2026 (3/11/2026) o Siri AI Developer Preview, uma prévia para desenvolvedores que permite integrar ações e conteúdos de qualquer aplicativo à nova Siri impulsionada pela Apple Intelligence. A documentação da prévia está em developer.apple.com/documentation/appintents/siri-ai-developer-preview e o anúncio da Apple está em developer.apple.com/news/?id=gdk2umrf.

A prévia vai além dos domínios de esquema definidos pelo sistema. A Siri passa a entender contexto, encontrar conteúdo personalizado e executar ações que o próprio aplicativo disponibiliza explicitamente por meio de App Intents. O framework App Intents está documentado em developer.apple.com/documentation/appintents.

Fonte: <https://developer.apple.com/documentation/appintents/siri-ai-developer-preview>

## Por que isso importa

A diferença central é de controle. A Siri só encontra conteúdo e executa ações que o app declara de forma explícita. O desenvolvedor descreve o que pode ser feito, e a Siri decide quando chamar essa ação a partir do pedido em linguagem natural.

Para quem usa o app, a promessa é continuar uma tarefa sem repetir o nome do aplicativo em contextos específicos e até pedir que a Siri pegue algo em um app e aja em outro. Para quem desenvolve, a exigência é descrever bem as ações, porque a Siri usa título e descrição para escolher a ferramenta certa.

Fonte: <https://developer.apple.com/documentation/appintents/siri-ai-developer-preview>

## App Intents como ferramentas da Siri

O caminho oficial é o guia Bringing custom actions and content to Siri, em developer.apple.com/documentation/appintents/bringing-custom-actions-and-content-to-siri. A ideia é atualizar o código de App Intents existente para que a Siri possa chamar as ações como ferramentas.

Para expor um App Intent, o código precisa ter title, description e perform(). A marcação que transforma o intent em ferramenta invocável pela Siri é @AppIntent(.tool). O framework App Intents está em developer.apple.com/documentation/appintents.

Fonte: <https://developer.apple.com/documentation/appintents/bringing-custom-actions-and-content-to-siri>

## App Intent mínimo: código Swift

O exemplo mínimo tem três peças: uma entidade de pedido, uma consulta e um intent marcado como ferramenta. O trecho abaixo mostra a entidade PedidoEntity e o intent ConsultarPedidoIntent. A consulta, PedidoQuery, você declara à parte: ela adota o protocolo EntityQuery e implementa entities(for:), que recebe identificadores e devolve as entidades correspondentes.

```
import AppIntents

struct PedidoEntity: AppEntity {
    static var typeDisplayRepresentation: TypeDisplayRepresentation = "Pedido"
    static var defaultQuery = PedidoQuery()
    var id: String
    var status: String
    var displayRepresentation: DisplayRepresentation { DisplayRepresentation(title: "\(id) - \(status)") }
}

@AppIntent(.tool)
struct ConsultarPedidoIntent: AppIntent {
    static let title: LocalizedStringResource = "Consultar pedido"
    static let description = IntentDescription("Consulta o status de um pedido pelo código.")
    @Parameter(title: "Pedido") var pedido: PedidoEntity
    func perform() async throws -> some IntentResult & ReturnsValue<PedidoEntity> {
        .result(value: pedido)
    }
}
```

Fonte: <https://developer.apple.com/documentation/appintents/bringing-custom-actions-and-content-to-siri>

## Quando o pedido pode dispensar o nome do app

Com o aplicativo em primeiro plano, com uma Live Activity ativa via ActivityKit ou ao continuar uma conversa na Siri que já mencionou o app, a pessoa não precisa repetir o nome do aplicativo. A documentação do ActivityKit está em developer.apple.com/documentation/activitykit. O exemplo da documentação é pedir uma corrida, acompanhar a Live Activity e depois pedir a mudança do local de embarque sem repetir o nome do app.

Se o app estiver em segundo plano sem atividade ativa, a solicitação precisa mencionar o nome do app. A Siri entende que o item foi curtido no app citado e responde com a informação correspondente, como no exemplo de perguntar se os tênis curtidos estão em promoção.

Fonte: <https://developer.apple.com/documentation/appintents/siri-ai-developer-preview>

## Ações entre apps: buscar em um, agir em outro

A Siri pode encontrar conteúdo personalizado em um app, transferir para outro e executar uma ação. O exemplo oficial é pedir o envio do tênis favorito para o parceiro em um app de mensagens: a Siri localiza o item nos favoritos, identifica o parceiro nos Contatos e envia a informação pelo app de mensagens.

O app de origem precisa indexar a entidade no Spotlight com IndexedEntity e conformar a AppEntity ao protocolo Transferable. O app de destino precisa adotar o domínio de esquema correspondente, como sendMessage. A documentação da integração entre apps está em developer.apple.com/documentation/appintents/apple-intelligence-and-siri-ai.

Fonte: <https://developer.apple.com/documentation/appintents/apple-intelligence-and-siri-ai>

## App de origem: indexação e transferência

O app que fornece o conteúdo indexa a entidade no Spotlight e permite a transferência para outro app.

```
import AppIntents
import CoreSpotlight

struct TenisEntity: AppEntity, IndexedEntity, Transferable {
    static var typeDisplayRepresentation: TypeDisplayRepresentation = "Tênis"
    static var defaultQuery = TenisQuery()
    var id: String
    var nome: String
    var displayRepresentation: DisplayRepresentation { DisplayRepresentation(title: "\(nome)") }
    static var transferRepresentation: some TransferRepresentation {
        ProxyRepresentation(exporting: \.nome)
    }
}
```

Fonte: <https://developer.apple.com/documentation/appintents/apple-intelligence-and-siri-ai>

## App de destino: esquema de mensagens

O app que recebe o conteúdo adota o esquema de envio de mensagem para concluir a ação.

```
import AppIntents

@AssistantIntent(schema: .messages.sendMessage)
struct EnviarMensagemIntent: AppIntent {
    var target: [PersonEntity]
    var content: String
    func perform() async throws -> some IntentResult { .result() }
}
```

Fonte: <https://developer.apple.com/documentation/appintents/apple-intelligence-and-siri-ai>

## App skills para tarefas com várias ações

Para tarefas com várias etapas, a Siri pode precisar de orientação extra sobre o domínio do app. A solução oficial é criar um pacote de skills no Xcode.

Crie no Xcode o caminho File > New > File from Template > Skills Bundle, que gera Skills.skillsbundle. Dentro dele fica um arquivo SKILL.md com name e description no cabeçalho YAML e as instruções em Markdown. O guia está em developer.apple.com/documentation/appintents/orchestrating-complex-actions-with-app-skills.

Fonte: <https://developer.apple.com/documentation/appintents/orchestrating-complex-actions-with-app-skills>

## App skill: arquivo SKILL.md

O arquivo SKILL.md associa intents e descreve a sequência de ações que a Siri deve seguir.

```
---
name: consultar-e-compartilhar-pedido
description: Consulta o status do pedido no app e envia o resultado por mensagem.
---
1. Execute `ConsultarPedidoIntent` passando o código do pedido informado pelo usuário.
2. Retorne o status obtido e encadeie com a ação de envio caso o usuário peça para compartilhar.
```

Fonte: <https://developer.apple.com/documentation/appintents/orchestrating-complex-actions-with-app-skills>

## Card snippets: resultado com o visual do app

A Siri exibe o conteúdo personalizado solicitado em card snippets fornecidos pelo app. Os snippets incluem a informação pedida e usam views próprias para mostrar marca e personalidade do aplicativo. A documentação está em developer.apple.com/documentation/appintents/cardsnippet.

Fonte: <https://developer.apple.com/documentation/appintents/cardsnippet>

## Card snippet: código Swift

O exemplo implementa CardSnippet retornando uma view SwiftUI para a entidade.

```
import AppIntents
import SwiftUI

struct PedidoCardSnippet: CardSnippet {
static let families: [CardSnippetFamily] = [.standard]
    func body(for entity: PedidoEntity, context: CardSnippetContext) -> some View {
        VStack(alignment: .leading) {
            Text(entity.id).font(.headline)
            Text(entity.status).font(.subheadline)
        }
    }
}
```

Fonte: <https://developer.apple.com/documentation/appintents/cardsnippet>

## Ferramentas no Xcode 27.3 beta

No Xcode 27.3 beta, o Siri Integration Advisor analisa a implementação de App Intents e sugere melhorias nas descrições e parâmetros. O download está em developer.apple.com/download/applications e as notas de versão estão em developer.apple.com/go/?id=xcode-27_3-sdk-rn.

O Siri Evaluations permite criar testes de conversa em linguagem natural, rodar pedidos em targets de UI Test e verificar quais intents e skills a Siri aciona a cada atualização. A documentação está em developer.apple.com/documentation/sirievaluations.

Fonte: <https://developer.apple.com/documentation/sirievaluations>

## Disponibilidade e como testar

A prévia está disponível em iOS, iPadOS, macOS e visionOS, em versão 27.3 beta, em dispositivos que suportam Apple Intelligence e em regiões onde Apple Intelligence e a Siri AI estão disponíveis.

O teste exige dispositivo físico; o Simulador não executa a integração. A conta Apple precisa ter 13 anos ou mais. Os idiomas suportados são inglês, francês, japonês, coreano, português e espanhol. No iOS e no iPadOS, a prévia não está disponível na União Europeia.

Para testar, compile o app no Xcode 27.3 beta, assine com perfil de desenvolvimento e instale no dispositivo. A alternativa é enviar o build ao App Store Connect para testadores internos no TestFlight. A prévia não está disponível para testadores externos nem para versões publicadas na App Store. Os links oficiais são appstoreconnect.apple.com, developer.apple.com/testflight e a ajuda do App Store Connect sobre testadores internos.

Fonte: <https://developer.apple.com/documentation/appintents/siri-ai-developer-preview>

## Os números

- 3 de novembro de 2026: data de liberação do Siri AI Developer Preview.
- 27.3 beta: versão mínima do iOS, iPadOS, macOS e visionOS para testar a integração.
- 13 anos: idade mínima da conta Apple para usar a prévia.
- 6 idiomas: inglês, francês, japonês, coreano, português e espanhol.
- Xcode 27.3 beta: versão da ferramenta usada para compilar, analisar e avaliar a integração.
- Primavera de 2027: previsão de abertura da submissão pública na App Store para apps com a integração.

Fonte: <https://developer.apple.com/news/?id=gdk2umrf>

## O que muda para você

Para um app de pedidos, a mudança aparece quando a pessoa pode consultar o status sem abrir o aplicativo, desde que a ação tenha sido declarada como ferramenta. O intent de consulta carrega título e descrição, e a Siri escolhe a ação certa com base no pedido.

Em um fluxo entre apps, a pessoa pode pedir o envio do tênis favorito para o parceiro em um app de mensagens. A Siri encontra o item no app de origem, identifica o contato e executa o envio no app de destino, desde que os dois apps implementem indexação, transferência e esquema.

Fonte: <https://developer.apple.com/documentation/appintents/apple-intelligence-and-siri-ai>

## O que fazer hoje

1. Leia a página Siri AI Developer Preview e o guia Bringing custom actions and content to Siri para entender o fluxo oficial.
2. Identifique as ações e entidades do app que devem ficar disponíveis para a Siri.
3. Adicione @AppIntent(.tool) aos App Intents existentes, com title, description e perform().
4. Para contexto entre apps, indexe entidades no Spotlight com IndexedEntity e conforme AppEntity ao protocolo Transferable no app de origem.
5. Adote o domínio de esquema correspondente, como sendMessage, no app de destino.
6. Para tarefas com várias etapas, crie Skills.skillsbundle no Xcode e escreva SKILL.md com name e description no YAML e instruções em Markdown.
7. Implemente CardSnippet para mostrar o resultado com o visual do app.
8. Abra o projeto no Xcode 27.3 beta e use o Siri Integration Advisor para revisar descrições.
9. Crie testes com Siri Evaluations em um target de UI Test.
10. Compile com perfil de desenvolvimento e instale em dispositivo físico compatível, ou envie ao App Store Connect para testadores internos no TestFlight.

Fonte: <https://developer.apple.com/documentation/appintents/bringing-custom-actions-and-content-to-siri>

## O que conferir

- A prévia exige dispositivo físico com Apple Intelligence; o Simulador não executa a integração.
- No iOS e no iPadOS, a prévia não está disponível na União Europeia.
- A conta Apple precisa ter 13 anos ou mais.
- O idioma do dispositivo deve ser um dos seis suportados: inglês, francês, japonês, coreano, português ou espanhol.
- Testadores externos e versões publicadas na App Store não recebem a funcionalidade da prévia.
- A API e o comportamento da Siri podem mudar durante a prévia.
- Nenhum entitlement especial é exigido durante a prévia, mas isso vale para o período de prévia.
- A submissão pública na App Store abre apenas na primavera de 2027.
- O app de origem e o de destino precisam implementar os requisitos de indexação, transferência e esquema; a Siri não infere a conexão sozinha.

Fonte: <https://developer.apple.com/documentation/appintents/siri-ai-developer-preview>

## Glossário

- App Intents: framework da Apple para declarar ações e entidades de um app que sistemas como a Siri podem usar.
- AppIntent: protocolo que define uma ação do app, com título, descrição e função perform().
- @AppIntent(.tool): macro que marca um App Intent como ferramenta invocável pela Siri na prévia.
- Entity: representação de um item do app que a Siri pode encontrar e manipular.
- EntityQuery: protocolo que busca entidades por identificadores.
- IndexedEntity: conformidade que indexa uma entidade no Spotlight para busca.
- Transferable: protocolo que permite transferir conteúdo entre apps.
- sendMessage: domínio de esquema de mensagens adotado pelo app de destino.
- Skills.skillsbundle: pacote criado no Xcode com instruções para tarefas complexas.
- SKILL.md: arquivo Markdown com cabeçalho YAML (name e description) e instruções para a Siri.
- CardSnippet: protocolo para exibir o resultado com views próprias do app.
- Siri Integration Advisor: recurso do Xcode 27.3 beta que sugere melhorias nas descrições de App Intents.
- Siri Evaluations: framework para rodar pedidos em targets de UI Test e ver quais intents a Siri aciona.
- TestFlight: serviço da Apple para distribuir builds a testadores internos.
- Apple Intelligence: conjunto de recursos de IA da Apple exigido pelos dispositivos da prévia.
- Live Activity: atividade em andamento mostrada na tela, usada como contexto pela Siri.
- ActivityKit: framework para criar Live Activities.

## Para onde ir depois

- Leia a documentação Siri AI Developer Preview e o guia Bringing custom actions and content to Siri.
- Atualize um App Intent existente com @AppIntent(.tool) e teste a invocação.
- Implemente o fluxo entre apps com IndexedEntity, Transferable e o esquema do app de destino.
- Crie um Skills.skillsbundle e um SKILL.md para uma tarefa com várias etapas.
- Implemente um CardSnippet para mostrar o resultado com a identidade visual do app.
- Use o Siri Integration Advisor e o Siri Evaluations no Xcode 27.3 beta antes de distribuir.

## Links citados

- https://developer.apple.com/documentation/activitykit

## Além do vídeo

- A documentação da API da prévia lista macros e protocolos adicionais, como GenerableEntity e ToolIntent, além da macro @AppIntent(.tool).
- As notas de versão do Xcode 27.3 estão em developer.apple.com/go/?id=xcode-27_3-sdk-rn.
- A ajuda do App Store Connect sobre testadores internos está em developer.apple.com/help/app-store-connect/test-a-beta-version/add-internal-testers.
