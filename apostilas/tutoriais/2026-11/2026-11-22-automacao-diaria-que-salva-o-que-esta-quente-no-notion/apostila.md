# Como construir um segundo cérebro automático com IA e Markdown

_2026-11-22 · tutorial_

Este tutorial mostra como construir um segundo cérebro automático com IA e Markdown, mantendo os arquivos definitivos no GitHub e usando o Notion apenas como fonte de leitura. Você vai montar uma pasta com mapa.md, conectar suas fontes por MCP e n8n e fazer o Claude Code produzir um log bruto diário. Uma skill com Claude Haiku ou GPT-4o mini extrai decisões, tarefas pendentes e insights, atualiza os arquivos permanentes e registra as mudanças no GitHub. O fluxo inclui uma lista de pessoas aprovadas, testes de funcionamento e cuidados com custos e privacidade. Depois da base funcionar, você pode evoluir para busca por assunto, memória de preferências e rastreamento da origem das informações.

## O que você terá no fim

Você terá uma pasta própria, sincronizada com o GitHub, com arquivos Markdown que guardam o contexto do seu trabalho e da sua vida. O Claude Code vai ler essa estrutura localmente e usar as fontes conectadas para manter as informações permanentes atualizadas.

O ciclo diário tem duas etapas. A coleta reúne o que chegou de novo em um log bruto. A digestão interpreta esse log, separa decisões, tarefas e insights, e salva cada informação no lugar adequado.

A lista de pessoas aprovadas funciona como um filtro de entrada. Ela impede que qualquer mensagem recebida passe automaticamente para people, pendências ou hot.

- Uma base de arquivos Markdown que você pode abrir em diferentes agentes de IA.
- Uma rotina diária de coleta que reduz o trabalho de copiar informações manualmente.
- Uma skill de digestão que atualiza os arquivos permanentes e faz o commit no GitHub.
- Um caminho de evolução para busca por assunto e memória de preferências.

Fonte: <https://github.com>

## Como isso funciona

Segundo cérebro é o nome dado a uma pasta organizada com arquivos de texto e ferramentas conectadas. A maior parte desses arquivos pode estar em Markdown, um formato simples que registra texto, títulos, listas e links. A pasta guarda o que você já sabe e o que acontece no seu dia a dia.

O contexto cresce quando você registra projetos, ferramentas, decisões, pessoas e pendências. Com esse contexto, a IA consegue localizar informações e trabalhar com dados específicos da sua rotina. Uma pasta parada limita essa ajuda porque o agente precisa procurar ou receber tudo a cada conversa.

O mapa.md funciona como a entrada da estrutura. Ele informa quais pastas existem, o que cada arquivo faz e onde o agente deve procurar. A coleta diária alimenta um log bruto; a digestão transforma esse log em conhecimento permanente.

A mesma base pode ser usada em diferentes ferramentas. Essa portabilidade vem dos arquivos e da organização, enquanto o GitHub mantém a sincronização e o histórico das alterações.

Fonte: <https://github.com>

## Antes de começar

O fluxo local começa com uma pasta no computador, uma conta no GitHub e o Claude Code apontando para ela. Você também precisa ter acesso às fontes que pretende conectar e decidir quais merecem entrar no segundo cérebro.

O Notion entra como fonte de leitura. A base definitiva fica nos arquivos Markdown sincronizados com o GitHub. As integrações usam servidores MCP e o n8n para levar as informações novas ao agente.

A VPS é um requisito do segundo degrau, quando você acrescenta o Gbrain. O exemplo de planos apresenta opções de R$ 29 e R$ 43, com 50 GB ou 100 GB, e a versão 2604, recomendada na criação do servidor. O custo total também inclui indexação e uso de API.

O exemplo pessoal de indexação cita R$ 1,00 a R$ 2,00 por mês. A combinação de Gbrain e Roncho na mesma VPS aparece na faixa de R$ 40 a R$ 50 por mês. Esses valores têm o recorte dos usos descritos e não servem como orçamento fixo para qualquer instalação.

- Crie a pasta que será a base do segundo cérebro e sincronize essa pasta com o GitHub.
- Instale ou prepare o Claude Code para rodar localmente sobre a pasta sincronizada.
- Separe as áreas que terão pastas próprias, como empresa e pessoal.
- Defina quais fontes serão lidas: e-mail, calendário, CRM, Notion ou WhatsApp.
- Prepare as integrações com servidores MCP e o n8n.
- Reserve uma VPS apenas se for seguir para o degrau de busca com Gbrain.

Fonte: <https://github.com>

## Crie a pasta, o mapa e os arquivos permanentes

Comece pela pasta no computador. Dentro dela, crie áreas como empresa e pessoal e use subpastas para projetos, conteúdos, materiais, finanças ou ferramentas que você usa. Depois, sincronize essa estrutura com o GitHub para manter os arquivos armazenados e versionados.

Na raiz, crie o mapa.md. Ele é um índice com instruções para o agente: descreva o que existe em cada pasta, qual é a função dos arquivos principais e onde encontrar cada assunto. O Claude Code deve ler esse mapa primeiro ao abrir a pasta ou iniciar uma sessão.

Os arquivos canônicos são os arquivos permanentes que organizam o contexto. O hot.md concentra o que está vivo, como compromissos e coisas que precisam de ação. O people funciona como um pequeno CRM das pessoas com quem você interagiu. Pendências guarda o que falta fazer, e decisões registra o que já foi resolvido ou combinado.

Você também pode criar mapas dentro das pastas. Um mapa de skills, por exemplo, pode explicar o que cada skill faz e quando foi atualizada. Esses índices locais ajudam o agente a navegar sem precisar examinar a estrutura inteira.

- mapa.md: descreva as pastas e os arquivos principais na raiz do segundo cérebro.
- hot.md: mantenha ali o contexto atual que merece atenção imediata.
- people: registre as pessoas aprovadas que fazem parte do seu contexto.
- pendências: organize tarefas e compromissos que ainda estão em aberto.
- decisões: preserve o que foi decidido para que a IA não precise reconstruir a conversa.

Fonte: <https://github.com>

## Conecte as fontes e defina quem pode entrar

E-mail, calendário, CRM, Notion e WhatsApp podem entrar no agente por servidores MCP e integrações via n8n. Um servidor MCP funciona como uma ponte entre o agente e uma fonte, expondo as informações que ele pode consultar. O n8n participa das integrações que levam esses dados ao fluxo.

A conexão permite que a IA leia o que chegou de novo sem você copiar e colar manualmente. O Notion permanece como fonte de leitura; os arquivos permanentes do segundo cérebro ficam no GitHub.

Crie uma lista de pessoas aprovadas antes de liberar mensagens para a digestão. O agente pode enviar essa lista todos os dias pelo Telegram para você autorizar. Só depois da autorização, o conteúdo dessa pessoa pode cair em people, pendências ou hot.

- Configure as fontes que você quer que o agente leia.
- Use MCP e n8n para conectar essas fontes ao Claude Code.
- Mantenha o Notion em modo de leitura neste fluxo.
- Crie a lista de pessoas aprovadas e revise as autorizações diárias.

Fonte: <https://n8n.io>

## Passo a passo

A ordem evita que o agente misture dados soltos com conclusões. Primeiro, ele coleta. Depois, uma skill interpreta o log e atualiza os arquivos permanentes.

Use o Claude Code rodando localmente sobre a pasta sincronizada. Os prompts das próximas seções entram nas etapas de coleta e digestão.

1. No computador, crie a pasta do segundo cérebro e sincronize-a com o GitHub. O resultado é uma base de arquivos que pode ser versionada.
2. Dentro da pasta, crie as áreas empresa e pessoal, acrescente as subpastas necessárias e escreva o mapa.md na raiz. O resultado é um índice que orienta o agente.
3. No Claude Code, abra a pasta sincronizada e peça para o agente ler o mapa.md. O resultado é o conhecimento inicial da estrutura.
4. Na configuração das integrações, conecte e-mail, calendário, CRM, Notion e WhatsApp por MCP e n8n. O resultado é a leitura das informações novas sem cópia manual.
5. Na rotina do agente, crie a lista de pessoas aprovadas e o envio diário dessa lista pelo Telegram. O resultado é um filtro antes de qualquer conteúdo entrar em people, pendências ou hot.
6. No Claude Code, peça a rotina diária de coleta usando o prompt indicado. O resultado esperado é o arquivo /logs/hoje.md com um log bruto em Markdown, sem interpretação.
7. Execute a skill de digestão com Claude Haiku ou GPT-4o mini. O resultado esperado é a extração de decisões, tarefas pendentes e insights para os arquivos permanentes.
8. Revise as alterações e faça o commit no GitHub. O resultado é uma versão registrada das mudanças no segundo cérebro.

Fonte: <https://claude.com>

## Exemplo completo: da mensagem ao arquivo permanente

Exemplo: Ana está na lista de pessoas aprovadas e envia pelo WhatsApp uma mensagem sobre o que vocês combinaram, com prazo até sexta e uma cláusula de saída. A coleta também consulta as tarefas do Notion e os eventos do calendário.

Na primeira etapa, o Claude Code reúne as informações novas no arquivo /logs/hoje.md. O log preserva a origem e o conteúdo coletado. Nessa parte, o agente registra o que recebeu e ainda não decide onde cada trecho deve ficar.

Na segunda etapa, a skill lê o log com um modelo leve. Ela pode reconhecer a mensagem de Ana como uma decisão ou uma tarefa pendente, atualizar os arquivos permanentes correspondentes e fazer o commit no GitHub. O people pode registrar a interação autorizada, e hot pode receber o ponto que ainda precisa de atenção.

Quando alguém procurar o acordo depois, o mapa indica onde as informações foram salvas. Se houver busca por assunto, o Gbrain poderá localizar os trechos e levar ao arquivo de origem.

- Ana entra no fluxo porque está na lista de pessoas aprovadas.
- A mensagem do WhatsApp é coletada junto com as demais fontes.
- A digestão separa o que é decisão, tarefa e insight.
- Os arquivos permanentes recebem a informação e o GitHub registra a alteração.

## Prompt de coleta

Use este texto no Claude Code para pedir a coleta diária. Ele define as fontes consultadas e o destino do log bruto.

O arquivo /logs/hoje.md reúne o que chegou. Nesta etapa, o objetivo é registrar, sem resumir nem distribuir o conteúdo pelos arquivos permanentes. O Notion é consultado como fonte de leitura.

```
Acesse minhas tarefas do Notion, eventos de hoje no calendário e mensagens importantes. Crie um log bruto em Markdown na pasta /logs/hoje.md.
```

Fonte: <https://claude.com>

## Prompt de digestão

Depois da coleta, execute a skill com Claude Haiku ou GPT-4o mini. Esses modelos leves são indicados no fluxo para processar o volume diário gastando poucos centavos.

A skill lê o log, extrai decisões tomadas, tarefas pendentes e insights principais, e usa os arquivos permanentes que você já criou. O commit no GitHub registra essa atualização.

A separação entre coleta e digestão ajuda a conferir o resultado. Você pode comparar o log bruto com as alterações feitas nos arquivos antes de considerar o ciclo concluído.

```
Leia o arquivo /logs/hoje.md, extraia decisões tomadas, tarefas pendentes e insights principais. Atualize os arquivos permanentes do meu segundo cérebro e faça o commit no GitHub.
```

Fonte: <https://github.com>

## Teste de pronto

Faça um ciclo completo e examine os arquivos, e não apenas a resposta do agente. Cada verificação abaixo mostra se uma parte do fluxo está funcionando.

- [ ] Confirme se o mapa.md está na raiz e descreve as pastas e os arquivos principais.
- [ ] Abra o arquivo /logs/hoje.md e confirme se ele reúne informações das fontes conectadas em um log bruto Markdown.
- [ ] Compare algumas mensagens do log com as fontes de origem e confirme se a coleta preservou o conteúdo sem antecipar a interpretação.
- [ ] Confirme se o Notion está sendo usado como fonte de leitura e se a base definitiva permanece nos arquivos Markdown do GitHub.
- [ ] Envie uma mensagem de uma pessoa aprovada e confirme se o conteúdo pode chegar a people, pendências ou hot após a digestão.
- [ ] Envie uma mensagem de uma pessoa fora da lista e confirme se ela não entra automaticamente nesses arquivos.
- [ ] Compare o log com os arquivos permanentes e confirme se decisões, tarefas pendentes e insights foram separados.
- [ ] Abra o GitHub e confirme se o commit registrou as alterações feitas pela skill.

Fonte: <https://github.com>

## Preserve sessões e memória do agente

A rotina diária não é a única fonte de contexto. Você também pode criar uma skill para guardar o conteúdo das sessões de conversa. No exemplo descrito, o Hermes compacta automaticamente a sessão ao atingir 75% do limite. No Claude Code, uma skill chamada salve pode registrar a sessão ao final.

A propagação semântica distribui o aprendizado da conversa por pendências, decisões, people, projetos, métricas, skills e mapas. No exemplo, a skill também envia as alterações para o cérebro da empresa, separando o que é pessoal do que pertence ao trabalho.

O memory guarda automaticamente informações sobre o usuário e as notas do dia a dia. Ele complementa os arquivos canônicos porque preserva preferências e histórico que ajudam o agente a continuar as próximas conversas.

- Crie uma skill para salvar a sessão quando o trabalho terminar.
- Revise quais informações devem ir para pendências, decisões, people, projetos ou métricas.
- Mantenha separados o contexto pessoal e o contexto da empresa.
- Use o memory para registrar preferências e notas recorrentes sobre o usuário.

## Gbrain: encontre informações por assunto

O segundo degrau acrescenta uma VPS e o Gbrain. Ele indexa os arquivos e permite procurar por assunto dentro do acervo. A pesquisa funciona de forma parecida com uma busca na web: você informa o tema, o Gbrain localiza os arquivos relacionados e apresenta os resultados por relevância.

O mapa continua sendo a bússola da estrutura. Ele aponta para as pastas e explica o conteúdo de cada uma. O Gbrain entra na busca mais profunda, quando a pasta já tem muitos arquivos e você precisa encontrar um trecho específico.

A instalação descrita parte do repositório da ferramenta, com um pedido para instalar e testar o funcionamento. A indexação usa API, e o exemplo de custo cita um valor baixo para manter a busca no servidor.

No exemplo com Ana, a busca consulta a nota diária e encontra o combinado com prazo até sexta e cláusula de saída. Depois, o resultado leva ao people e aos demais arquivos onde o acordo aparece. O Gbrain trabalha sob demanda: procura quando recebe uma consulta.

- Faça uma consulta por assunto e confirme se o Gbrain aponta para o arquivo correto.
- Abra o arquivo indicado e compare o trecho encontrado com a informação original.
- Use mapas dentro das pastas para dar contexto adicional aos resultados.
- Considere a VPS e a API como custos desse degrau.

## Roncho: injete preferências nas sessões

O Roncho guarda uma memória sobre o usuário. Enquanto o Gbrain organiza assuntos, pessoas e decisões, o Roncho registra preferências, tom de voz e padrões de comportamento, como preferir respostas curtas ou mais elaboradas.

Ele pode funcionar em uso individual ou compartilhado. No modo multiplayer, o uso ocorre no Teams ou no Slack da empresa, com identificação por telefone, ID de usuário ou e-mail. Cada pessoa pode ter traços próprios preservados.

O Gbrain pesquisa sob demanda. O Roncho também pode ingerir contexto no início de cada sessão e injetar esse contexto na conversa. Um arquivo agents.md define quando o agente deve consultá-lo. Consultar com frequência demais aumenta a quantidade de contexto injetada e reduz o espaço disponível na sessão.

No plugin do Hermes citado, há três modos. O híbrido injeta contexto automaticamente e libera ferramentas. O context faz apenas a injeção automática. O tools disponibiliza somente as ferramentas. A injeção pode ocorrer em todos os turnos ou apenas no primeiro, e o exemplo de cadência aparece em 8.

O Roncho tem versão open source e uma conta que oferece 5 dólares iniciais no exemplo apresentado. Esse crédito pode acabar com uso contínuo ou maior volume. Instalá-lo na mesma VPS do Gbrain evita acrescentar outro servidor.

- Defina no agents.md quando o agente deve consultar o Roncho.
- Escolha entre injeção automática, ferramentas ou a combinação das duas.
- Ajuste a frequência para não consumir o contexto da sessão sem necessidade.
- Use a identificação da pessoa no modo multiplayer para manter preferências separadas.

## Context Ledger: rastreie a origem dos sinais

O Context Ledger é um registro dos sinais que chegam ao segundo cérebro. Ele anota a fonte, a referência da conversa e palavras-chave que indicam ação ou mudança. Entre as fontes citadas estão WhatsApp, e-mail e Granola.

Os sinais podem incluir tags como próximo passo, contador e nota fiscal. O objetivo é deixar claro de onde veio cada informação e onde o agente pode encontrar a conversa original.

O ciclo descrito mantém 90 dias de registro. Quando atinge esse período, arquiva os últimos 30 dias e continua com 60 dias de contexto. O Gbrain pode procurar no Ledger, e o agents.md orienta o agente a carregá-lo para localizar as coisas mais rápido.

Essa estrutura é apresentada como uma tese. Ela pode ajudar em cérebros grandes, com muitas pessoas e arquivos, mas o ganho precisa ser observado no uso antes de virar regra fixa.

- Fonte: registre se o sinal veio de WhatsApp, e-mail ou Granola.
- Referência: guarde a data e a origem da conversa para voltar ao trecho original.
- Sinal: use palavras-chave como próximo passo, contador ou nota fiscal.
- Ciclo: mantenha a janela de contexto e o arquivamento descritos.

## Erros comuns e cuidados

Um erro a evitar é misturar as etapas. Se a coleta já interpreta tudo, você perde a chance de comparar o dado bruto com a digestão. Se a digestão não atualiza os arquivos permanentes, o log cresce sem virar contexto útil.

Outro cuidado é abrir a entrada de qualquer pessoa sem autorização. A lista de aprovados existe para controlar quem pode influenciar people, pendências e hot.

Custos, capacidades e resultados têm o recorte de cada exemplo. Os valores de VPS e API não são uma cotação geral, e o Context Ledger continua sendo uma proposta a ser testada.

- Não use o log bruto como substituto dos arquivos permanentes.
- Não transforme o Notion na base definitiva deste fluxo; ele entra como fonte de leitura.
- Não deixe pessoas fora da lista de aprovados caírem automaticamente em people, pendências ou hot.
- Não instale Gbrain ou Roncho por links de terceiros; a instalação deve partir do repositório oficial da ferramenta.
- Não confunda o mapa.md com o Gbrain: o mapa orienta a navegação, e o Gbrain faz a busca por assunto.
- Não injete contexto do Roncho em todos os turnos sem avaliar o espaço que isso consome na sessão.
- Não trate o Context Ledger como uma solução validada antes de observar se ele melhora a localização das informações.
- Não prometa que a automação conhece todo o contexto: ela só trabalha com o que foi conectado, autorizado e salvo.

## Glossário

- Segundo cérebro: pasta organizada com arquivos de texto e ferramentas que preservam contexto para consulta e trabalho com IA.
- Markdown: formato de texto simples que permite registrar títulos, listas, links e comandos.
- mapa.md: índice lido primeiro pelo agente para localizar pastas e entender os arquivos.
- Arquivo canônico: arquivo permanente que guarda uma categoria importante do contexto.
- Log bruto: registro inicial das informações coletadas, antes da interpretação.
- Digestão: leitura do log para extrair decisões, tarefas e insights e atualizar os arquivos permanentes.
- Skill: instrução ou rotina especializada que orienta o agente a executar uma tarefa.
- MCP: Model Context Protocol, usado para conectar o agente a fontes e ferramentas por servidores.
- n8n: ferramenta de integração usada no fluxo para conectar as fontes ao agente.
- Commit: registro de uma versão das alterações no GitHub.
- VPS: servidor alugado onde rodam serviços como Gbrain e Roncho.
- Indexação: preparação dos arquivos para que uma ferramenta consiga encontrá-los por assunto.
- Gbrain: sistema de busca que localiza informações no acervo quando recebe uma consulta.
- Roncho: memória de preferências, tom de voz e padrões do usuário.
- Injeção de contexto: entrada de informações da memória em uma sessão do agente.
- Context Ledger: registro da origem e das palavras-chave dos sinais recebidos.
- Single player: uso da estrutura por uma pessoa.
- Multiplayer: uso compartilhado, com preferências e contexto separados por integrante da equipe.
- LLM: modelo de linguagem usado para ler, interpretar e gerar texto.

## Plano de 7 dias

O plano reparte os passos que já existem. Cada dia termina com uma parte do fluxo pronta para o próximo.

- Dia 1: crie a pasta, sincronize com o GitHub e organize as áreas empresa e pessoal.
- Dia 2: escreva o mapa.md e prepare os arquivos permanentes hot, people, pendências e decisões.
- Dia 3: conecte as fontes por MCP e n8n, mantendo o Notion como fonte de leitura.
- Dia 4: crie a lista de pessoas aprovadas e a rotina de autorização diária pelo Telegram.
- Dia 5: execute o prompt de coleta e verifique o arquivo /logs/hoje.md.
- Dia 6: execute a skill de digestão com Claude Haiku ou GPT-4o mini e faça o commit no GitHub.
- Dia 7: rode o teste de pronto, corrija os pontos que falharam e decida se precisa de busca com Gbrain, memória com Roncho ou rastreamento com Context Ledger.

## Para onde ir depois

O próximo passo é repetir o ciclo de coleta, digestão e commit até que ele faça parte da rotina. Pratique consultar o mapa antes de pedir qualquer informação e comparar o log com os arquivos permanentes para reconhecer erros de classificação.

Quando o acervo crescer, avalie o Gbrain para busca por assunto. Se o agente precisar conhecer melhor suas preferências, teste o Roncho. O Context Ledger entra como experimento para rastrear sinais e origens.

- Mantenha o mapa.md atualizado sempre que criar ou mudar uma pasta.
- Revise a lista de pessoas aprovadas antes de ampliar as fontes conectadas.
- Teste uma consulta por assunto no Gbrain e confira se o resultado leva ao arquivo correto.
- Defina no agents.md quando o Roncho deve entrar na sessão.
- Observe se o Context Ledger reduz o tempo de localização antes de adotá-lo como regra.

## Links citados

- https://www.notion.com

## Além do vídeo

- Também é possível conectar a leitura do extrato bancário para automatizar as finanças pessoais.
