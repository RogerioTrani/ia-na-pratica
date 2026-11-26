# Siri AI abre prévia para todos os desenvolvedores

_2026-11-22 · noticia_

A Siri AI abre uma Developer Preview para todos os desenvolvedores integrarem conteúdo e ações de seus aplicativos por meio de App Intents. Você vai entender como pedidos em linguagem natural acionam operações do app, como skills combinam várias ações e quais recursos de contexto e de busca fazem parte dessa integração. Também vai conhecer os requisitos de aparelho, idioma, região e idade, os limites diários e o calendário de testes e envio à App Store. Ao final, terá um caminho para escolher uma ação, construir a integração e avaliar a experiência na prévia.

## O fato

Em 3 de novembro de 2026, a Apple anunciou a abertura da Developer Preview da Siri AI para todos os desenvolvedores. O acesso começa nas versões beta de iOS 27.3, iPadOS 27.3, macOS 27.3 e visionOS 27.3.

A prévia permite que um aplicativo leve seu conteúdo e suas ações para a assistente. A Apple descreve a Siri AI como uma nova versão da Siri, mais conversacional e pessoal, pensada para integração com os sistemas operacionais e os apps usados no dia a dia.

Fonte: <https://developer.apple.com/news/?id=gdk2umrf>

## Por que isso importa

Milhares de desenvolvedores já criaram integrações com a Siri, segundo o anúncio. Essas integrações permitem pedir direções, gerenciar uma lista de tarefas, enviar uma mensagem ou retomar um audiolivro. A prévia da Siri AI amplia esse caminho ao aproximar o conteúdo e as ações dos aplicativos da assistente.

Para o usuário, a proposta é poder descrever o que precisa com suas próprias palavras. A assistente passa a receber operações construídas pelo desenvolvedor e pode executá-las durante o atendimento ao pedido. Isso muda a forma de acessar uma função do app, que pode ser acionada por uma solicitação em linguagem natural.

Para empresas e desenvolvedores, a integração cria uma nova maneira de alcançar e atender clientes. Uma pessoa pode descobrir e usar um aplicativo apenas fazendo um pedido à Siri AI, desde que o app ofereça a ação correspondente.

Fonte: <https://developer.apple.com/news/?id=gdk2umrf>

## App Intents: conteúdo e ações dentro da Siri AI

App Intents é o mecanismo que permite ao aplicativo expor seu conteúdo e suas ações para a Siri AI. Em termos práticos, o desenvolvedor define as operações que o app sabe executar e as disponibiliza para a assistente.

A pessoa descreve o que precisa com suas palavras, e a Siri AI executa a ação personalizada construída no aplicativo. O anúncio cita consultar uma entrega, fazer uma reserva e realizar um pedido como exemplos dessas operações.

Esses casos mostram a divisão do trabalho. O aplicativo oferece a ação por meio de App Intents, enquanto a assistente recebe o pedido em linguagem natural. Para começar uma integração, o desenvolvedor precisa identificar qual conteúdo ou operação do app será exposto e consultar a documentação das novas interfaces de programação.

Fonte: <https://developer.apple.com/documentation/appintents/siri-ai-developer-preview>

## Skills: várias ações em uma experiência

Uma solicitação complexa pode exigir várias operações. A Apple introduz skills para permitir que o desenvolvedor ensine a Siri AI a combinar diferentes ações em uma única experiência.

Exemplo: Imagine que um aplicativo exponha as ações de consultar uma entrega e fazer uma reserva. Uma skill pode ensinar a assistente a reunir essas operações para atender a um pedido que envolva as duas. A skill descreve a composição das ações dentro dessa experiência.

O trabalho do desenvolvedor passa a incluir a organização do fluxo. Além de disponibilizar cada ação, ele pode ensinar como várias delas se relacionam para responder a um pedido mais amplo.

Fonte: <https://developer.apple.com/news/?id=gdk2umrf>

## Contexto pessoal e informação na tela

A prévia também dá acesso a recursos de compreensão do contexto pessoal, consciência das informações na tela e linguagem natural. Juntos, eles permitem que a Siri AI considere o contexto da pessoa e o que está visível durante a interação.

Compreender contexto pessoal significa usar informações do contexto da pessoa para interpretar melhor o pedido. A consciência da tela permite considerar o conteúdo que está sendo exibido. A linguagem natural é o que permite que a pessoa fale ou escreva de maneira comum, sem seguir uma fórmula rígida.

Para quem desenvolve, a avaliação da experiência precisa observar mais do que a execução da ação. Também é importante verificar se a assistente compreende o pedido no contexto em que ele foi feito e quais informações da tela ajudam a atender à solicitação.

Fonte: <https://developer.apple.com/news/?id=gdk2umrf>

## Spotlight semantic index

Outra novidade do anúncio é que a Siri AI pode apresentar qualquer entidade no Spotlight semantic index. Em linguagem simples, o índice semântico organiza informações para que possam ser encontradas pelo significado, e não apenas por uma estrutura fixa de campos.

Um schema é uma estrutura predefinida que especifica como determinados dados devem ser organizados. Antes dessa ampliação, a superfície de resultados da Siri AI ficava limitada às entidades compatíveis com schemas existentes.

Com a mudança descrita, a assistente pode apresentar entidades do índice que não se encaixem nesses schemas. Para o desenvolvedor, isso amplia o conjunto de informações que a Siri AI pode mostrar ao interagir com o aplicativo.

Fonte: <https://developer.apple.com/news/?id=gdk2umrf>

## O que já chega nos aplicativos da Apple

A Apple começou a distribuir essas capacidades em vários aplicativos próprios. A lista inclui Calendar, Files, Finder, Journal, Mail, Maps, Messages, Music, Notes, Photos, Preview, Reminders, Safari, Shortcuts e Weather.

Entre os exemplos citados estão encontrar uma cafeteria visitada na semana anterior e arquivar arquivos que não foram abertos há mais de um ano. Esses casos mostram como os pedidos podem envolver tanto a busca de informações quanto a execução de ações.

O anúncio informa que há mais ações disponíveis e que os aplicativos da Apple servem como exemplos para consulta. Em um ambiente compatível, basta perguntar à Siri AI o que é possível fazer em cada aplicativo.

Fonte: <https://developer.apple.com/news/?id=gdk2umrf>

## Idiomas e requisitos de acesso

A Siri AI está disponível em beta em iOS 27.3, iPadOS 27.3, macOS 27.3, watchOS 27.3 e visionOS 27.3. O uso requer um dispositivo compatível com Apple Intelligence, configurado para um idioma suportado.

Os idiomas disponíveis são inglês, francês, japonês, coreano, português e espanhol. A expansão prevista inclui chinês tradicional, norueguês, turco e vietnamita. Alguns recursos podem não estar disponíveis em todas as regiões ou idiomas.

O suporte ao português não elimina os demais requisitos. O aparelho precisa ser compatível, o idioma precisa estar entre os suportados e a pessoa precisa atender à restrição etária. Usuários menores de 13 anos não têm acesso à Siri AI.

Fonte: <https://developer.apple.com/news/?id=gdk2umrf>

## A restrição na União Europeia

Na União Europeia, a Siri AI está indisponível em iOS, iPadOS e watchOS. A Apple afirma que está trabalhando de forma construtiva com a União Europeia para encontrar um caminho para a disponibilidade.

O recorte por sistema operacional importa. A restrição citada no anúncio se refere a iOS, iPadOS e watchOS; o anúncio não informa a mesma restrição para macOS ou visionOS.

Fonte: <https://developer.apple.com/news/?id=gdk2umrf>

## Os números

Os valores do anúncio indicam datas, versões e condições de acesso. Cada um deve ser lido com seu escopo específico.

- 3 de novembro de 2026: data do anúncio que abriu a Developer Preview a todos os desenvolvedores.
- iOS 27.3, iPadOS 27.3, macOS 27.3 e visionOS 27.3: versões beta em que o acesso inicial à prévia foi anunciado.
- watchOS 27.3: sistema também listado para a Siri AI em beta, separadamente da lista inicial específica da Developer Preview.
- 6 idiomas disponíveis: inglês, francês, japonês, coreano, português e espanhol. O número indica o conjunto de idiomas citados no anúncio, sujeito aos requisitos de aparelho e região.
- 13 anos: limite etário; usuários abaixo dessa idade não têm acesso à Siri AI.
- Poucos meses: prazo indicado para o primeiro envio da Siri AI aos clientes, contado a partir do anúncio. É uma previsão de distribuição, não uma data exata.
- Primavera: estação prevista para a abertura dos envios à App Store, dando aos desenvolvedores tempo para explorar e construir antes do lançamento.

Fonte: <https://developer.apple.com/news/?id=gdk2umrf>

## Limites diários e acesso ampliado mediante pagamento

Certos recursos do Apple Intelligence que dependem de modelos no servidor têm limites diários de uso. A lista inclui a Siri AI, ferramentas de edição inteligente de fotos, Image Playground e modelos AFM 3 Cloud no Shortcuts.

Os limites podem variar conforme o recurso, a complexidade da solicitação, a demanda do sistema, as políticas do sistema e outros fatores. Por isso, o volume de uso permitido não deve ser tratado como uma quantidade fixa para todos os pedidos.

Modelo no servidor é um modelo processado na infraestrutura do serviço. O uso desses recursos está sujeito aos termos e condições do Apple Intelligence. O anúncio informa que o acesso ampliado a eles terá uma taxa no futuro.

Fonte: <https://support.apple.com/148587>

## O calendário da prévia ao lançamento

A Developer Preview oferece acesso antecipado antes do primeiro envio da Siri AI aos clientes, previsto para os próximos meses. Nessa fase, os desenvolvedores podem explorar as novas integrações, construir experiências e compartilhar feedback.

A abertura dos envios à App Store está prevista para a primavera. Esse período separa a experimentação inicial da preparação para distribuição e dá tempo para testar as experiências antes do lançamento.

A Apple também informa que divulgará mais detalhes sobre os termos e as políticas de uso das experiências habilitadas pela Siri AI. O acompanhamento dessas regras faz parte da preparação para o envio.

Fonte: <https://developer.apple.com/news/?id=gdk2umrf>

## O que muda para você

Quando um aplicativo oferecer a integração, a pessoa poderá pedir uma operação em suas próprias palavras. O caminho de uso deixa de depender apenas de abrir o app e localizar a função, e passa a incluir a assistente como ponto de acesso à ação.

Para o desenvolvedor, a mudança está em expor conteúdo e ações para a Siri AI e avaliar como a assistente interpreta os pedidos. Em solicitações mais complexas, uma skill pode organizar a combinação de várias operações.

Exemplo: Imagine que um aplicativo exponha a ação de consultar uma entrega. A pessoa faz o pedido em linguagem natural, e a Siri AI usa a ação construída pelo desenvolvedor para realizar a consulta. O desenvolvedor é responsável por disponibilizar essa operação; a assistente recebe e executa o pedido.

Fonte: <https://developer.apple.com/news/?id=gdk2umrf>

## O que fazer hoje

Use a prévia para transformar uma operação real do aplicativo em uma experiência testável com a Siri AI.

1. Confirme o ambiente de teste usando uma das versões beta indicadas, em dispositivo compatível com Apple Intelligence e com idioma suportado. O resultado esperado é ter acesso à Siri AI nas condições anunciadas.
2. Leia a documentação Siri AI Developer Preview (App Intents) para conhecer as novas interfaces de programação, como usá-las e como avaliar a experiência. O resultado esperado é ter a especificação técnica oficial antes de implementar.
3. Escolha uma ação concreta do aplicativo, como consultar uma entrega, fazer uma reserva ou realizar um pedido. O resultado esperado é definir a operação que será exposta à assistente.
4. Use App Intents para levar o conteúdo e a ação escolhida à Siri AI. O resultado esperado é permitir que a pessoa solicite essa operação em linguagem natural.
5. Se o fluxo exigir várias operações, use uma skill para ensinar a combinação. O resultado esperado é uma experiência que reúne essas ações em um único pedido.
6. Avalie a experiência seguindo a documentação e registre o feedback da prévia. O resultado esperado é verificar o comportamento da integração e reunir observações para compartilhar com a Apple.
7. Prepare o envio à App Store para quando a abertura ocorrer na primavera, acompanhando os termos e as políticas que serão divulgados. O resultado esperado é chegar ao lançamento com a integração testada e alinhada às regras publicadas.

Fonte: <https://developer.apple.com/documentation/appintents/siri-ai-developer-preview>

## O que conferir

Antes de confiar em uma integração ou planejar seu lançamento, confira as condições que afetam acesso, uso e distribuição.

- Status da versão: a integração está em Developer Preview. Trate os resultados como teste de uma prévia e acompanhe a abertura dos envios à App Store na primavera.
- Requisitos de acesso: confirme se o dispositivo é compatível com Apple Intelligence e está configurado para um idioma suportado.
- Região e idioma: alguns recursos podem não estar disponíveis em todas as regiões ou idiomas, mesmo quando o idioma aparece na lista de suporte.
- Idade: usuários menores de 13 anos não têm acesso à Siri AI.
- União Europeia: a Siri AI está indisponível em iOS, iPadOS e watchOS nessa região, conforme o recorte do anúncio.
- Limites de uso: recursos com modelos no servidor têm limites diários que variam conforme recurso, complexidade do pedido, demanda e políticas do sistema.
- Cobrança futura: o acesso ampliado aos recursos com modelos no servidor terá uma taxa no futuro. Leve essa previsão em conta ao planejar a experiência.
- Termos e políticas: a Apple divulgará mais detalhes sobre as regras das experiências habilitadas pela Siri AI. Revise a integração quando essas regras forem publicadas.

Fonte: <https://developer.apple.com/news/?id=gdk2umrf>

## Glossário

- App Intents: mecanismo usado pelo aplicativo para expor conteúdo e ações à Siri AI.
- Siri AI: nova versão da Siri descrita pela Apple como mais conversacional e pessoal, integrada aos sistemas operacionais e aos aplicativos.
- Developer Preview: prévia inicial para desenvolvedores, com acesso antes da distribuição aos clientes.
- Beta: versão de teste disponível antes do lançamento para o público em geral.
- Apple Intelligence: conjunto de recursos de IA da Apple; a Siri AI requer um dispositivo compatível com ele.
- Skill: experiência que ensina a Siri AI a combinar várias ações para atender a uma solicitação mais complexa.
- Linguagem natural: maneira comum de falar ou escrever, sem exigir uma fórmula rígida de comandos.
- Contexto pessoal: informações do contexto da pessoa que ajudam a assistente a interpretar o pedido.
- Consciência da tela (onscreen awareness): capacidade de considerar as informações visíveis durante a interação.
- Spotlight semantic index: índice semântico associado ao Spotlight, usado para organizar e encontrar entidades pelo significado.
- Entidade: item ou objeto de informação que pode ser apresentado no índice semântico.
- Schema: estrutura predefinida que organiza os campos e o formato de determinados dados.
- API: conjunto de regras e interfaces que permite a um software usar funcionalidades de outro software.
- Modelo no servidor: modelo processado na infraestrutura do serviço, associado neste anúncio a limites diários de uso.
- Limite diário de uso: quantidade máxima de uso permitida em um dia, que pode variar conforme o recurso e as condições do sistema.
- App Store: loja de aplicativos da Apple; a abertura dos envios de experiências com Siri AI está prevista para a primavera.

Fonte: <https://developer.apple.com/documentation/appintents/siri-ai-developer-preview>

## Para onde ir depois

O próximo passo é aplicar o conceito a uma ação real do seu aplicativo e avaliar a experiência com a documentação oficial.

- Leia a documentação Siri AI Developer Preview (App Intents) para conhecer as interfaces de programação, o uso e os critérios de avaliação.
- Escolha uma ação simples do aplicativo para praticar a exposição por meio de App Intents.
- Use os aplicativos da Apple como referência e observe, em um ambiente compatível, quais ações a Siri AI consegue realizar.
- Depois de testar uma ação isolada, pratique a composição de várias operações com uma skill.
- Acompanhe o anúncio oficial e os termos do Apple Intelligence para receber as próximas orientações sobre políticas, envio à App Store e acesso ampliado.

Fonte: <https://developer.apple.com/documentation/appintents/siri-ai-developer-preview>
