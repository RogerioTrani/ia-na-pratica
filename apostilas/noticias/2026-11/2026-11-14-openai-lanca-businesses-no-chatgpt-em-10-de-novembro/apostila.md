# OpenAI lança Businesses no ChatGPT em 10 de novembro

_2026-11-14 · noticia_

O Businesses in ChatGPT reúne perfil empresarial, catálogo de produtos, agente de atendimento e métricas dentro do ChatGPT. Nesta apostila, você vai entender o lançamento em beta anunciado pela OpenAI em 10 de novembro de 2026 e a atualização de 19 de novembro sobre a ampliação dos agentes. Também vai aprender a diferença entre reivindicar um perfil, verificar a empresa e publicar um Business Agent. O texto explica feeds, privacidade, patrocínio e os limites de cada recurso. Ao final, você terá um caminho para verificar a elegibilidade, preparar os dados e testar o agente.

## O fato

Em 10 de novembro de 2026, a OpenAI anunciou o Businesses in ChatGPT em versão beta. O pacote reúne o Business Hub, onde a empresa gerencia sua presença, e os Business Agents, que conversam com clientes sobre produtos e serviços. O anúncio cita 1,2 bilhão de pessoas usando o ChatGPT por semana.

No lançamento, a reivindicação de perfis alcançava empresas elegíveis em todos os países onde o ChatGPT estava disponível, inclusive o Brasil. Os Business Agents começaram para empresas elegíveis de e-commerce e serviços online nos Estados Unidos.

Uma atualização publicada em 19 de novembro de 2026 ampliou esse quadro. A OpenAI informou que empresas de e-commerce e serviços online sediadas fora dos EUA passaram a ser elegíveis para reivindicar seus negócios e publicar agentes no ChatGPT. A ampliação mantém o recorte por categoria e pelas regras de elegibilidade.

Fonte: <https://openai.com/index/introducing-businesses-chatgpt/>

## Por que isso importa

O ChatGPT passou a fazer parte da maneira como as pessoas descobrem produtos, comparam opções e tomam decisões. Quando uma resposta menciona uma empresa, informações desatualizadas podem atrapalhar essa pesquisa. O perfil empresarial oferece um canal para a empresa manter dados atuais e compartilhar detalhes de produtos, preços e disponibilidade.

O Business Agent acrescenta outra possibilidade. Em vez de depender apenas de uma resposta geral do ChatGPT, o cliente pode abrir uma conversa com a empresa para fazer perguntas de acompanhamento. O agente usa as informações e as diretrizes definidas pela empresa para ajudar a pessoa a entender as opções.

A separação entre a resposta independente do ChatGPT e a conversa com o agente ajuda a mostrar quem está respondendo. O agente aparece em um espaço claramente rotulado, e os formatos patrocinados também recebem identificação. Esses limites permitem ao leitor distinguir informação da empresa, resposta do assistente e publicidade.

Fonte: <https://openai.com/index/introducing-businesses-chatgpt/>

## Quem pode participar

A reivindicação de perfil está aberta a empresas elegíveis com site próprio ativo em locais onde o ChatGPT é oferecido, incluindo o Brasil. A elegibilidade depende de setor, localização e verificações de identidade e integridade. Para gerenciar o perfil, a pessoa precisa ser proprietária da empresa ou ter autorização para representá-la.

Os Business Agents começaram nos Estados Unidos para e-commerce e serviços online. Com a atualização de 19 de novembro de 2026, empresas dessas categorias sediadas fora dos EUA também passaram a ser elegíveis para reivindicar seus negócios e publicar agentes. Cada empresa ainda precisa passar pelas verificações aplicáveis.

Clientes OpenAI Enterprise e anunciantes podem trabalhar diretamente com um representante da OpenAI para reivindicar seus negócios.

Fonte: <https://openai.com/policies/businesses-in-chatgpt/>

## Business Hub: reivindicação e verificação

O Business Hub, chamado de Central de Negócios na página em português, é o ponto de gestão da empresa no ChatGPT. O processo pode começar pelo botão de reivindicação em https://openai.com/business/businesses-in-chatgpt/. Depois do login, o administrador também pode abrir o Business Hub pela barra lateral em https://chatgpt.com. A documentação não indica uma URL pública separada com subcaminho para o painel e também prevê um link pessoal enviado ao administrador do workspace.

A verificação tem duas etapas. Primeiro, a empresa reivindica o perfil e valida a propriedade por telefone comercial, e-mail corporativo, DNS do domínio ou conta Shopify. Esses métodos são alternativas para comprovar o vínculo com o negócio.

Depois, o administrador conclui a verificação de identidade pessoal pela Persona. Somente após essa aprovação ele pode publicar edições, ver métricas e enviar catálogos. Separar propriedade da empresa e identidade do administrador evita tratar o simples preenchimento de um cadastro como liberação para gerir a presença.

Fonte: <https://help.openai.com/en/articles/20001635-setting-up-your-business-on-chatgpt>

## Catálogo de produtos e feeds

Um feed de produtos é um arquivo estruturado que reúne informações comerciais por item. No Businesses in ChatGPT, ele permite que varejistas compartilhem detalhes, preços e disponibilidade para que o ChatGPT use essas informações ao responder perguntas de clientes. Os arquivos aceitos são JSONL.GZ, CSV.GZ, TSV.GZ ou Parquet, e cada item precisa dos nove campos obrigatórios abaixo.

O país de destino é informado além dos nove campos. Ele indica o mercado ao qual o envio se refere. A documentação oficial de feeds traz a especificação completa para preparar e enviar os arquivos.

Lojistas Shopify têm um caminho próprio. Eles podem conectar a loja pelo Business Hub ou pelo painel de administração da Shopify, revisar as informações e sincronizar o catálogo diretamente. Produtos elegíveis de lojistas Shopify já estão integrados ao ChatGPT por meio do Shopify Catalog. Também é possível reivindicar uma empresa sem ter uma loja Shopify.

- item_id: identificador do item no catálogo.
- title: título do produto.
- description: descrição do produto.
- url: endereço da página do produto.
- brand: marca do produto.
- seller_name: nome do vendedor.
- image_url: endereço da imagem do produto.
- availability: informação sobre a disponibilidade do produto.
- price: preço do produto.
- País de destino: mercado informado além dos nove campos obrigatórios.

Fonte: <https://developers.openai.com/commerce/specs/file-upload/products>

## Business Agents: atendimento com limites definidos

Depois da reivindicação e da verificação, uma empresa elegível pode criar um Business Agent no Business Hub. O administrador configura o agente com informações da empresa, segue as diretrizes que controla, testa a configuração e publica. O objetivo é responder dúvidas e ajudar clientes a explorar produtos e serviços.

A conversa com o agente tem rótulo próprio e fica separada da conversa original do cliente com o ChatGPT. Ela também é distinta das respostas independentes do assistente. Quem inicia essa conversa escolhe falar com a empresa depois de encontrar seu perfil ou sua menção em uma resposta.

O agente ajuda na comparação e no entendimento das opções, mas não conclui compras, reservas nem consultas de pedidos. Essa fronteira deve ficar clara na configuração e nos testes para que o cliente não espere uma transação ou um atendimento que o agente não executa.

Fonte: <https://openai.com/policies/business-agents-policy/>

## Como funciona a conversa na prática

Quando uma empresa aparece em uma resposta do modelo, a pessoa pode clicar para ver seu perfil no ChatGPT. Se houver um Business Agent disponível, ela pode escolher iniciar uma conversa com o negócio. A partir daí, faz perguntas de acompanhamento sobre as ofertas em um espaço identificado como conversa com a empresa.

Exemplo: Imagine que alguém está comparando dois produtos e quer entender quais recursos atendem melhor às suas necessidades. A pessoa pode abrir o perfil da empresa e conversar com o agente. Ele usa as informações compartilhadas pelo negócio para explicar diferenças e recursos, mantendo a conversa separada da resposta original do ChatGPT.

Esse percurso permite que o cliente aprofunde a pesquisa com a empresa. A compra ou a reserva não é concluída pelo agente, e a conversa não deve ser apresentada como uma recomendação independente do ChatGPT.

Fonte: <https://openai.com/index/introducing-businesses-chatgpt/>

## Métricas e privacidade

O painel do Business Hub reúne três métricas agregadas dos últimos 28 dias: menções, cliques no site e tópicos de descoberta. Menções indicam as ocorrências da empresa no ChatGPT. Cliques no site registram o acesso ao site a partir dessas interações. Tópicos de descoberta reúnem temas comuns das conversas em que o site da empresa foi citado.

Os números só aparecem quando há volume suficiente de conversas ou interações. A OpenAI não divulga publicamente os valores exatos desses limiares mínimos. Por isso, a ausência de uma métrica no painel não informa, sozinha, se houve pouco interesse ou se o volume ficou abaixo do limite de exibição.

Segundo a OpenAI, as empresas recebem apenas insights agregados. A companhia afirma que não compartilha com elas as conversas dos usuários no ChatGPT nem os chats feitos com os Business Agents. As métricas servem para entender a representação da empresa e encontrar temas para melhorar as informações compartilhadas, sem entregar o conteúdo individual das conversas.

Fonte: <https://openai.com/index/introducing-businesses-chatgpt/>

## Publicidade e Business Agents patrocinados

Reivindicar o perfil, publicar um agente e anunciar são etapas independentes. O patrocínio descrito no lançamento vale para empresas elegíveis nos Estados Unidos que usam o ChatGPT Ads. A empresa precisa ter o negócio verificado no Business Hub, publicar seu Business Agent e vinculá-lo como destino de uma campanha no Ads Manager.

O ChatGPT Ads foi lançado em setembro de 2026. Para montar um agente patrocinado, o fluxo oficial começa pela empresa verificada e pelo agente já publicado. Depois, o anunciante usa o guia do Ads Manager para vincular o agente como destino da campanha.

Todo posicionamento patrocinado recebe rótulo explícito e fica separado das respostas orgânicas do ChatGPT. A OpenAI não publica um preço fixo para patrocinar um Business Agent. O custo segue o orçamento e os lances definidos pelo anunciante na campanha.

Fonte: <https://help.openai.com/en/articles/20001651-setting-up-a-sponsored-business-agent-in-ads-manager>

## O selo azul e os limites da reivindicação

O perfil de uma empresa reivindicada recebe uma marca de verificação azul. O selo indica que aquela presença foi reivindicada. Ele não garante melhor posicionamento, mais vendas ou exclusividade sobre o conteúdo exibido.

O ChatGPT continua fazendo recomendações e comparações de forma independente. Os termos do Businesses in ChatGPT também deixam claro que o perfil não dá exclusividade sobre o conteúdo mostrado. Além disso, o perfil permite desativar chamadas automatizadas do assistente.

Uma empresa pode aparecer em respostas mesmo sem ter um Business Agent. O agente acrescenta a possibilidade de conversa com base nas informações compartilhadas pela empresa, mas sua ausência não significa que o ChatGPT deixará de mencionar o negócio.

Fonte: <https://openai.com/business/businesses-in-chatgpt/>

## Os números

Os números do anúncio têm recortes diferentes. O público semanal do ChatGPT, a data de lançamento, a janela das métricas e a estrutura dos feeds não medem a mesma coisa. Cada valor abaixo vem acompanhado do que representa e do que não permite concluir.

- 1,2 bilhão de pessoas por semana: público semanal citado no anúncio original. O número não representa empresas cadastradas, clientes de um agente ou conversas comerciais.
- 10 de novembro de 2026: data do anúncio do Businesses in ChatGPT em beta. Não é a data de disponibilidade universal de todos os recursos.
- 19 de novembro de 2026: data da atualização que tornou empresas elegíveis de e-commerce e serviços online fora dos EUA aptas a reivindicar seus negócios e publicar agentes.
- 28 dias: período coberto pelas métricas do painel. A janela não representa todo o histórico de interações da empresa.
- 9 campos obrigatórios: quantidade mínima de informações exigidas por item no feed de produtos. O país de destino é informado separadamente.
- 4 métodos de validação da propriedade: telefone comercial, e-mail corporativo, DNS do domínio ou conta Shopify. São alternativas, não uma exigência de usar os quatro.
- 2 etapas de verificação: validação da propriedade da empresa e verificação de identidade do administrador pela Persona.
- 3 métricas agregadas: menções, cliques no site e tópicos de descoberta. Elas não incluem as conversas individuais dos usuários.

Fonte: <https://openai.com/index/introducing-businesses-chatgpt/>

## O que muda para você

Para uma empresa, o beta cria um lugar para manter informações comerciais atuais, oferecer uma conversa com o cliente e acompanhar temas agregados de descoberta. O perfil e o catálogo cuidam dos dados. O agente cuida das perguntas de acompanhamento. O painel mostra como a empresa aparece nas interações, dentro da janela e dos limites de privacidade.

Para o cliente, a mudança é ter mais contexto ao pesquisar. A resposta do ChatGPT continua sendo independente, e a conversa com a empresa acontece em um espaço separado e rotulado. Preços, disponibilidade e diferenças entre produtos podem vir das informações fornecidas pelo negócio.

Exemplo: Imagine que uma empresa elegível tem site próprio e catálogo. O administrador reivindica o perfil, valida a propriedade, conclui a verificação pela Persona e atualiza os dados. Se estiver habilitada para usar agente, ele cria, testa e publica o Business Agent. O painel passa a mostrar métricas agregadas quando o volume mínimo é atingido. Nenhuma etapa garante posicionamento ou vendas.

Fonte: <https://openai.com/pt-BR/business/businesses-in-chatgpt/>

## O que fazer hoje

O caminho começa pela elegibilidade e termina em um agente testado, quando a empresa se qualifica para esse recurso. Faça as etapas nesta ordem para respeitar as verificações e evitar publicar dados antes da liberação.

1. Leia a política de Businesses in ChatGPT para verificar setor, localização, integridade e autorização para representar a empresa. O resultado esperado é saber qual caminho se aplica ao seu negócio.
2. Abra https://openai.com/business/businesses-in-chatgpt/ e clique em reivindicar, ou faça login em https://chatgpt.com/ e abra o Business Hub pela barra lateral. O resultado esperado é chegar ao início da reivindicação.
3. Reivindique o perfil e valide a propriedade por telefone comercial, e-mail corporativo, DNS do domínio ou conta Shopify. O resultado esperado é comprovar o vínculo com a empresa.
4. Conclua a verificação de identidade do administrador pela Persona. Depois da aprovação, o resultado esperado é liberar edições, métricas e envio de catálogos.
5. Atualize as informações da empresa e prepare o catálogo. Conecte a Shopify pelo Business Hub ou pelo painel da Shopify, ou envie um feed em JSONL.GZ, CSV.GZ, TSV.GZ ou Parquet com os nove campos obrigatórios e o país de destino. O resultado esperado é deixar os dados prontos para o ChatGPT usar.
6. Se a empresa for elegível para Business Agent, crie e configure o agente no Business Hub com informações e diretrizes do negócio. Teste as respostas e publique. O resultado esperado é disponibilizar uma conversa rotulada e separada das respostas independentes do ChatGPT.
7. Acompanhe o painel depois que houver volume suficiente de interações. O resultado esperado é visualizar menções, cliques no site e tópicos de descoberta dos últimos 28 dias, sem acesso às conversas individuais.

Fonte: <https://help.openai.com/en/articles/20001635-setting-up-your-business-on-chatgpt>

## O que conferir

Antes de confiar no cadastro ou de planejar uma campanha, confira os limites de cada frente. Perfil, catálogo, agente, métricas e publicidade têm regras próprias, e uma etapa aprovada não libera automaticamente as outras.

- Confirme setor, localização e verificações de integridade antes de presumir elegibilidade. Ter um site próprio é parte do acesso inicial ao perfil, mas não elimina os demais critérios.
- Separe a situação do perfil da situação do agente. A atualização de 19 de novembro ampliou a elegibilidade de agentes fora dos EUA para e-commerce e serviços online, mantendo as condições do produto.
- Guarde a confirmação da validação da propriedade e da identidade pela Persona. Edições, métricas e catálogos dependem da conclusão dessas verificações.
- Revise os nove campos obrigatórios, o formato do arquivo e o país de destino antes de enviar um feed. Dados incompletos ou mercados mal informados prejudicam a preparação do catálogo.
- Teste o Business Agent com informações e diretrizes da empresa antes de publicar. A revisão humana acontece nessa etapa, especialmente para conferir se as respostas respeitam os limites de compra, reserva e consulta de pedidos.
- Leia as métricas como um resumo dos últimos 28 dias. Os limiares mínimos não têm valores exatos divulgados, e os números não dão acesso às conversas individuais.
- Diferencie a resposta independente do ChatGPT, a conversa rotulada com o agente e a publicidade patrocinada. Cada uma tem origem e identificação próprias.
- Não interprete o selo azul como promessa de posicionamento ou vendas. O perfil também não concede exclusividade sobre o conteúdo exibido.
- Verifique se a empresa pode desativar chamadas automatizadas do assistente nos termos do perfil. Essa opção faz parte das condições do Businesses in ChatGPT.
- Para anunciar, confirme a elegibilidade nos EUA, a empresa verificada, o agente publicado e a vinculação da campanha no ChatGPT Ads. O custo depende do orçamento e dos lances, sem preço fixo público.

Fonte: <https://openai.com/policies/businesses-in-chatgpt-terms/>

## Glossário

- Businesses in ChatGPT: conjunto beta que reúne perfil empresarial, informações de produtos, Business Agents e insights no ChatGPT.
- Business Hub: painel usado para reivindicar e gerenciar a presença da empresa, publicar informações e acessar métricas.
- Business Agent: agente criado pela empresa para responder perguntas e ajudar clientes a explorar suas ofertas em uma conversa rotulada.
- Reivindicar perfil: solicitar a gestão da presença de uma empresa no ChatGPT e passar pelo processo de verificação.
- Verificação de propriedade: etapa que comprova o vínculo de quem solicita o perfil com a empresa.
- Persona: serviço usado no fluxo descrito para concluir a verificação de identidade pessoal do administrador.
- Feed de produtos: arquivo estruturado com dados de itens, preços e disponibilidade enviado ao ChatGPT.
- JSONL.GZ: um dos formatos de arquivo aceitos para feeds de produtos.
- CSV.GZ: um dos formatos de arquivo aceitos para feeds de produtos.
- TSV.GZ: um dos formatos de arquivo aceitos para feeds de produtos.
- Parquet: um dos formatos de arquivo aceitos para feeds de produtos.
- DNS: sistema que associa nomes de domínio a informações da internet e pode ser usado para validar a propriedade de um domínio.
- Menções: ocorrências da empresa nas respostas do ChatGPT.
- Cliques no site: acessos ao site da empresa registrados a partir das interações.
- Tópicos de descoberta: temas comuns das conversas em que o site da empresa foi citado.
- Métrica agregada: informação resumida de várias interações, sem entregar cada conversa separadamente.
- Limiar mínimo: volume necessário de conversas ou interações para que um insight seja exibido.
- Resposta orgânica: resposta que não é um posicionamento patrocinado.
- Beta: versão inicial de um produto disponibilizada para evolução e ajustes.

Fonte: <https://openai.com/business/businesses-in-chatgpt/>

## Para onde ir depois

A OpenAI descreve o beta como uma base para ampliar o Businesses in ChatGPT a mais mercados e categorias. Também declarou planos para criar ferramentas voltadas a organizações com necessidades mais complexas. O próximo passo é aplicar o fluxo à realidade da sua empresa e acompanhar as páginas oficiais.

- Use a política de Businesses in ChatGPT para revisar elegibilidade e as condições do perfil antes de reivindicar.
- Pratique organizar as informações de um produto nos nove campos obrigatórios e identifique o país de destino antes de preparar o feed.
- Se a empresa for elegível para agente, crie uma configuração de teste no Business Hub e confira dúvidas, comparações e limites de atendimento antes de publicar.
- Consulte a especificação e o guia de envio de feeds para preparar o catálogo no formato escolhido.
- Se quiser patrocinar o agente, leia o guia oficial de Business Agent patrocinado no Ads Manager e defina orçamento e lances da campanha.
- Acompanhe o anúncio oficial para saber sobre ampliação de mercados, categorias e ferramentas.

Fonte: <https://openai.com/index/introducing-businesses-chatgpt/>

## Links citados

- https://help.openai.com/en/articles/20001651-setting-up-a-sponsored-business-agent-in-ads-manager
