# N8N lança o NOD, agente pessoal fantástico!

_2026-11-23 · noticia_

O Nod é o agente pessoal lançado pelos criadores do N8N para rodar com o modelo de IA que você escolher. Ele reúne rotinas automáticas, conexões com ferramentas e canais de comunicação, autorização para ações não solicitadas e um cofre para senhas. Nesta apostila, você vai entender a diferença entre um chatbot e um agente pessoal, conhecer o funcionamento do Nod e aprender a configurar o primeiro acesso e uma rotina de e-mail. Também vai conferir os custos que continuam existindo, os limites das versões em prévia e os cuidados antes de delegar tarefas.

## O fato

Os criadores do N8N lançaram o Nod, um agente pessoal aberto e gratuito. A proposta é dar ao usuário um ambiente com navegador, conexões e rotinas, ligado ao modelo de IA que ele escolher.

O anúncio oficial está no blog do n8n. O download e as informações do produto estão em https://nod.n8n.io/, e o código público está em https://github.com/n8n-io/nod.

- Quem lançou: os criadores do N8N.
- O que foi lançado: Nod, um agente pessoal.
- Licença: Apache 2.0.
- Página oficial: https://nod.n8n.io/.

Fonte: <https://blog.n8n.io/meet-nod/>

## Por que isso importa

Num chatbot, o trabalho começa com um pedido seu. Você pede um e-mail, envia um arquivo ou faz uma pergunta e espera a resposta. O agente pessoal tem um ambiente próprio e pode incorporar tarefas recorrentes à sua rotina.

O Nod pode manter essas tarefas registradas e agendá-las. Imagine que você queira receber um resumo das prioridades de e-mail toda manhã. Num chatbot, você abre a conversa e pede o resumo. No Nod, essa atividade pode virar um schedule com horário definido, enquanto a máquina que executa o Nod estiver ligada.

A mudança prática está em passar de solicitações isoladas para um fluxo que continua configurado. Isso exige escolher bem as conexões, os horários e as autorizações, porque o agente deixa de depender de um novo pedido a cada tarefa.

Fonte: <https://blog.n8n.io/meet-nod/>

## Como o Nod age pela sua rotina

O Nod reúne o modelo de IA e o ambiente em que as tarefas acontecem. O modelo interpreta a linguagem e participa das respostas e decisões. O ambiente do Nod concentra o navegador, as conexões com ferramentas, as rotinas e o cofre de senhas.

Na configuração inicial, você informa como quer começar e escolhe o provedor e o modelo. Depois, o chat permite conversar com o agente e criar schedules. A área de apps reúne as ferramentas conectadas, enquanto channels reúne os canais de conversa, como Telegram e WhatsApp.

Aprender a rotina aparece na prática nas atividades que você registra e nos horários que define. O Nod também apresenta uma área de memórias entre suas configurações. Você acompanha o que está programado em Schedule e o uso na área Usage.

Fonte: <https://blog.n8n.io/meet-nod/>

## Modelos de IA: liberdade de escolha

O Nod aceita OpenAI, Anthropic, Gemini e mais de 30 provedores. Também permite usar um modelo rodando no próprio computador. Essa variedade permite escolher o modelo conforme a necessidade, sem ficar restrito ao portfólio de uma única empresa.

Na demonstração, o assistente mostra OpenAI e OpenRouter entre as opções. No passo do modelo, é possível entrar com a conta do ChatGPT ou usar uma chave API. Depois da configuração, a área de modelos do painel permite consultar e trocar a seleção.

A escolha do modelo também entra na conta de custo. Como o gasto está no uso do modelo escolhido, provedor, modelo e frequência das rotinas fazem parte da decisão. A liberdade de troca não significa que todos os modelos tenham o mesmo preço ou comportamento.

- OpenAI, Anthropic e Gemini aparecem entre os provedores aceitos.
- São mais de 30 provedores disponíveis.
- Um modelo executado no próprio computador também pode ser usado.
- OpenRouter aparece como opção no assistente de configuração.
- A conta do ChatGPT e a chave API surgem como caminhos no passo do modelo da demonstração.

Fonte: <https://nod.n8n.io/>

## Código aberto e ferramenta sem assinatura

O código do Nod está público no GitHub sob a licença Apache 2.0. Isso permite que qualquer pessoa examine o código e altere funcionalidades ao baixar a ferramenta. A personalização é uma possibilidade, não um requisito para começar.

Gratuito, neste caso, significa que o Nod não exige assinatura da ferramenta. O gasto continua no uso do modelo escolhido. Se você optar por manter o Nod num servidor, também existe o custo da infraestrutura contratada.

Por isso, vale separar o preço da ferramenta do custo de operação. O repositório oficial é https://github.com/n8n-io/nod. A estimativa de uma rotina pode ajudar a planejar o uso, mas representa apenas a configuração mostrada naquele momento.

- Licença do código: Apache 2.0.
- Repositório oficial: https://github.com/n8n-io/nod.
- Assinatura da ferramenta: não exigida.
- Custo que permanece: uso do modelo escolhido.
- Custo adicional possível: servidor usado para manter o Nod em execução.

Fonte: <https://github.com/n8n-io/nod>

## Onde o Nod roda

O download oficial está em https://nod.n8n.io/. A página oferece a versão para Mac e marca Windows 11 e Linux como prévia. Considere essas indicações ao escolher o ambiente de instalação.

Você pode executar o Nod no seu computador ou num servidor ligado 24 horas. As tarefas agendadas só rodam enquanto a máquina do Nod estiver ligada. Se o computador local estiver desligado, uma rotina programada não continua executando por causa dele.

Uma VPS é um computador virtual que fica em servidores na nuvem. Nesse formato, o Nod roda na máquina remota, e você pode acessá-lo pelo navegador mesmo com o seu computador desligado. A VPS é a infraestrutura que hospeda o agente; o modelo de IA continua sendo uma escolha separada.

- Mac: download disponível na página oficial.
- Windows 11: download indicado como prévia.
- Linux: download indicado como prévia.
- Servidor: opção para manter o Nod disponível 24 horas.
- Condição das rotinas: a máquina que executa o Nod precisa estar ligada.

Fonte: <https://nod.n8n.io/>

## Segurança: autorização e cofre de senhas

Antes de enviar, pagar, postar ou apagar algo que você não pediu, o Nod pede autorização. Esse ponto separa uma tarefa delegada de uma ação que depende de uma nova decisão sua.

Exemplo: o Nod pode pesquisar um produto, colocá-lo no carrinho e chegar ao checkout com o endereço. A compra só acontece depois da sua aprovação. O mesmo princípio vale para outras ações não solicitadas que estejam no fluxo.

As senhas ficam num cofre próprio, chamado Vault no painel. No fluxo descrito, quando uma senha é usada num site, ela sai do cofre e segue diretamente para o computador, sem ser processada pelo modelo de IA.

A empresa relata testes próprios envolvendo decisões críticas e afirma que todos passaram. Esse é um resultado relatado pela empresa. A autorização e o cofre reduzem os riscos descritos, mas você continua responsável por revisar permissões e rotinas.

- Ações não pedidas exigem o seu aval.
- Compras dependem de aprovação.
- Senhas ficam no Vault.
- A senha não passa pelo modelo no fluxo apresentado.
- Os testes citados são da própria empresa e não substituem a sua revisão.

Fonte: <https://blog.n8n.io/meet-nod/>

## WhatsApp e Telegram no mesmo fluxo

O Nod pode se conectar ao WhatsApp e ao Telegram. Esses canais permitem conversar com o agente a partir dos aplicativos que você já usa no dia a dia.

Na prática, você configura a conexão em channels e passa a ter o Nod junto das suas conversas. Isso facilita o acesso quando você está fora do computador principal, desde que o ambiente que executa o Nod continue ligado.

Para manter essa disponibilidade, o servidor 24 horas é uma opção. A conexão com um canal não altera o custo do modelo escolhido nem dispensa a autorização em ações que você não pediu.

- Telegram: canal de conversa compatível com o Nod.
- WhatsApp: canal de conversa compatível com o Nod.
- Onde configurar: área channels do painel.
- Condição para acesso remoto: o Nod precisa continuar rodando no ambiente escolhido.

Fonte: <https://nod.n8n.io/>

## O painel do Nod

O painel reúne os controles que você vai usar depois da configuração inicial. O chat é o espaço de conversa e criação de rotinas. Schedule mostra as atividades programadas, enquanto apps reúne as ferramentas conectadas.

Channels concentra as integrações com Telegram e WhatsApp. Usage permite acompanhar o uso, Vault guarda as senhas e a área de modelos permite consultar ou trocar o modelo selecionado. O painel também apresenta configurações de memórias.

Conhecer essas áreas ajuda a conferir o que está ativo antes de deixar uma rotina trabalhando. Você consegue localizar o horário em Schedule, verificar o uso em Usage e revisar o modelo sem precisar refazer toda a configuração.

- Chat: conversa com o agente e criação de rotinas.
- Schedule: rotinas programadas e horários.
- Apps: ferramentas conectadas.
- Channels: integrações com Telegram e WhatsApp.
- Usage: acompanhamento do uso.
- Vault: local das senhas guardadas.
- Modelos: consulta e troca do modelo selecionado.
- Memórias: área de configuração apresentada no painel.

Fonte: <https://nod.n8n.io/docs/>

## Exemplo completo: resumo de e-mail às 8h

Na demonstração, depois de conectar uma conta Gmail ou Outlook, o Nod sugeriu algumas rotinas. A opção escolhida foi resumir as prioridades de e-mail. O agente perguntou o horário desejado, recebeu 8 da manhã e mostrou o pedido em forma de resumo antes da criação.

Depois de confirmar, a rotina apareceu em Schedule com a ação programada para 8 horas. A mesma tela exibiu uma estimativa de cerca de R$ 3,50 por mês para aquela atividade.

Essa estimativa pertence à rotina e à configuração demonstradas. Ela serve como referência para aquele exemplo, não como preço fixo do Nod ou de qualquer rotina. O uso do modelo escolhido continua sendo cobrado. Se o Nod estiver num computador local, a rotina depende desse computador ligado no horário; num servidor 24 horas, depende do servidor permanecer ativo.

## Os números

- Mais de 30 provedores: é a variedade de provedores aceita pelo Nod, incluindo OpenAI, Anthropic e Gemini. O número não indica preço ou desempenho igual entre eles.
- 5 passos: é a quantidade de etapas de onboarding mostrada na demonstração. O passo do modelo inclui a escolha do provedor e o acesso pela conta do ChatGPT ou por chave API.
- 8 da manhã: foi o horário escolhido na demonstração para o resumo de prioridades de e-mail. Não é um horário obrigatório do Nod.
- R$ 3,50 por mês: foi a estimativa exibida para a rotina de resumo de e-mail criada no exemplo. Não é uma assinatura nem um valor válido para todas as rotinas.
- 24 horas: é o tempo de disponibilidade buscado ao manter o Nod num servidor ligado continuamente. A execução ainda depende desse servidor ativo.
- Windows 11: é a versão do Windows indicada para download em prévia. Linux também aparece como prévia.
- Apache 2.0: é a licença do código público do Nod.

## O que muda para você

Você passa a configurar um ambiente de trabalho, e não apenas um chat. Isso envolve escolher o modelo, definir onde o Nod vai rodar, conectar as ferramentas e transformar tarefas repetitivas em schedules.

Imagine que seu objetivo seja receber prioridades de e-mail pela manhã e conversar com o agente pelo Telegram. O caminho é conectar o e-mail, selecionar o modelo, criar o schedule às 8h e ativar o canal em channels. Um servidor 24 horas mantém o Nod disponível para essa rotina e para o acesso remoto.

Você continua no controle das ações não pedidas, porque elas exigem autorização. A rotina automatiza a repetição; a decisão de enviar, pagar, postar ou apagar permanece com você.

## O que fazer hoje

Comece pela página oficial e termine com uma rotina visível em Schedule. O caminho abaixo mantém a escolha do modelo e do ambiente sob seu controle.

1. Acesse https://nod.n8n.io/ e escolha o download para o seu sistema. No Windows 11 e no Linux, observe a indicação de prévia. Você terá o download oficial para iniciar a configuração.
2. Se quiser manter rotinas com o seu computador desligado, defina um servidor que fique ligado 24 horas. A documentação oficial está em https://nod.n8n.io/docs/. Você terá o local de execução escolhido.
3. Abra o Nod e clique em get started para entrar no assistente. A tela de configuração inicial deve abrir.
4. No onboarding, conecte Gmail ou Outlook e conceda as permissões solicitadas. A conta de e-mail escolhida ficará ligada ao Nod.
5. No passo do modelo, selecione o provedor e o modelo. Use a conta do ChatGPT ou a chave API, conforme a opção apresentada. O modelo escolhido ficará configurado.
6. Abra o chat e escolha a sugestão de resumir prioridades de e-mail, como na demonstração. O Nod vai perguntar o horário e mostrar o pedido resumido.
7. Defina o horário, revise a descrição e crie o schedule. A rotina deverá aparecer em Schedule com o horário e a estimativa de custo.
8. Em channels, conecte Telegram ou WhatsApp se quiser usar o agente por esses aplicativos. O canal escolhido ficará disponível para conversa.
9. Consulte Usage, Vault e a área de modelos para localizar o acompanhamento de uso, as senhas guardadas e a seleção do modelo. Você saberá onde revisar cada controle.

Fonte: <https://nod.n8n.io/docs/>

## Teste de pronto

Use estas verificações para confirmar que a configuração terminou. Elas acompanham as áreas e os passos que aparecem na demonstração.

- [ ] Abra o endereço do seu ambiente e faça login. A tela inicial do Nod deve abrir.
- [ ] Na área de modelos, confirme se o provedor e o modelo escolhidos aparecem na configuração.
- [ ] Em apps, confirme se a conta Gmail ou Outlook conectada está disponível.
- [ ] Em Schedule, compare a rotina criada com a atividade e o horário que você definiu.
- [ ] Confira se a estimativa de custo aparece junto da rotina, como no exemplo.
- [ ] Em Vault, confirme se a senha guardada não aparece na conversa com o modelo.
- [ ] Se você conectou um canal, abra channels e confirme se Telegram ou WhatsApp está disponível.

## O que conferir

O desenho com autorização e cofre reduz riscos concretos, como compras sem aprovação e senhas processadas pelo modelo. Esses controles não transformam o Nod em garantia de segurança absoluta. Revise as conexões e as rotinas que ficam ativas no seu ambiente.

A estimativa de custo mostrada numa rotina também merece contexto. Ela ajuda a planejar aquela atividade, mas o gasto depende do uso do modelo escolhido. Manter um servidor 24 horas envolve uma contratação separada da ferramenta.

- Autorização: enviar, pagar, postar ou apagar algo que você não pediu depende do seu aval.
- Senhas: use o cofre e preserve o fluxo em que a senha não passa pelo modelo.
- Custo: não trate R$ 3,50 como preço geral; o valor pertence à rotina demonstrada.
- Disponibilidade: tarefas agendadas só rodam enquanto a máquina do Nod estiver ligada.
- Prévia: Windows 11 e Linux aparecem marcados como prévia na página oficial.
- Testes da empresa: o relato de que todos passaram é uma informação da própria empresa e não substitui sua revisão.
- Comparações: autorização e cofre são controles concretos; eles não comprovam superioridade sobre todos os outros agentes.

## Glossário

- Agente pessoal: sistema com ambiente próprio que acompanha rotinas e pode executar tarefas automaticamente, além de responder a pedidos.
- Chatbot: interface que responde a partir de um pedido do usuário.
- Modelo de IA: componente que interpreta linguagem e gera respostas ou participa de decisões. No Nod, o modelo é escolhido pelo usuário.
- Provedor de modelos: serviço que oferece acesso a modelos de IA. O Nod aceita mais de 30 provedores.
- Modelo local: modelo de IA executado no próprio computador.
- API: interface usada para integrar sistemas. No passo do modelo da demonstração, aparece como uma forma de acesso ao serviço escolhido.
- Chave API: credencial usada para autenticar o acesso a um serviço de IA.
- Schedule: nome usado no Nod para uma rotina agendada.
- Onboarding: configuração inicial guiada. A demonstração mostra cinco passos.
- VPS: computador virtual em servidores na nuvem, usado para manter o Nod rodando continuamente.
- Vault: cofre do Nod onde ficam guardadas as senhas que não passam pelo modelo no fluxo apresentado.
- Canal: integração que permite conversar com o Nod pelo Telegram ou WhatsApp.
- Memória: informação de contexto que pode ser reutilizada em interações futuras. O Nod apresenta uma área de memórias no painel.
- Prévia: versão disponibilizada antes da versão final. Windows 11 e Linux aparecem assim na página de download.
- Apache 2.0: licença de código aberto usada pelo Nod.

Fonte: <https://nod.n8n.io/docs/>

## Para onde ir depois

Comece por uma rotina que você já conhece. O resumo de prioridades de e-mail é o exemplo completo: conecte a conta, defina o horário e confira a atividade em Schedule. Depois, acompanhe o uso e revise a estimativa de custo.

Quando quiser usar o Nod fora do computador principal, conecte Telegram ou WhatsApp e teste o acesso pelo canal. Se precisar trocar de provedor ou modelo, use a área de modelos do painel.

- Baixe o Nod pela página oficial: https://nod.n8n.io/.
- Consulte a documentação oficial: https://nod.n8n.io/docs/.
- Examine o código e a licença no repositório: https://github.com/n8n-io/nod.
- Leia o anúncio oficial: https://blog.n8n.io/meet-nod/.
- Pratique criando um schedule e conferindo o horário, a estimativa de custo e a conexão usada.
- Revise as autorizações antes de manter uma rotina com ações de envio, pagamento, publicação ou exclusão.

Fonte: <https://nod.n8n.io/docs/>
