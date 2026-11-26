# Agente da Perplexity roda local e não gasta créditos

_2026-11-23 · noticia_

A Perplexity levou o Portable Computer para o aplicativo do Windows em PCs com NVIDIA RTX, permitindo executar trabalho de agente na própria máquina. Ao ler esta apostila, você vai entender como o agente divide tarefas em etapas, quando pode pedir ajuda da nuvem e por que essa autorização importa. Também vai conhecer os requisitos de hardware e plano, o modelo local Qwen 3.8 27B, os conectores e três usos práticos. No fim, terá o caminho para instalar o aplicativo e começar uma tarefa local sem confundir o trabalho no PC com o uso de modelos na nuvem.

## O fato

Em 14 de setembro de 2026, o blog da NVIDIA anunciou que o Perplexity Portable Computer passou a estar disponível no aplicativo da Perplexity para Windows. A versão local do Perplexity Computer chega a PCs compatíveis com NVIDIA GeForce RTX e a estações de trabalho NVIDIA RTX PRO, com aceleração pelas GPUs NVIDIA RTX.

O Portable Computer é um agente que planeja e executa tarefas em várias etapas. Nessa versão, ele usa modelos locais para analisar dados, reunir informações de arquivos e realizar trabalhos recorrentes no próprio PC. O aplicativo também mantém a integração com modelos na nuvem para pesquisa e raciocínio mais avançados.

Fonte: <https://blogs.nvidia.com/blog/local-ai-perplexity-windows-pcs/>

## Por que isso importa

A execução local aproxima o agente dos arquivos que ele precisa examinar. Informações sensíveis podem ser processadas no aparelho, e o trabalho concluído no computador não consome créditos do Perplexity Computer. Para quem lida com documentos internos, extratos ou dados de clientes, essa combinação reduz a necessidade de enviar cada arquivo para um serviço externo.

O anúncio também resolve parte da configuração que normalmente acompanha a IA local. O aplicativo inclui um modelo preparado para trabalhar com o Computer e usa ferramentas e conectores para ampliar o que o agente consegue fazer. O leitor pode começar pelo objetivo da tarefa, em vez de montar primeiro toda a pilha de software necessária para executar um modelo local.

Fonte: <https://blogs.nvidia.com/blog/local-ai-perplexity-windows-pcs/>

## Como um agente transforma um pedido em trabalho

Um agente recebe um objetivo e organiza o trabalho em etapas. Ele pode analisar dados, usar ferramentas e encadear ações para chegar ao resultado pedido. O Perplexity Computer já tinha esse formato de trabalho em várias etapas; o Portable Computer passa a executar parte desse fluxo com modelos que rodam no próprio computador.

Imagine que você peça ao agente para reunir informações espalhadas por vários arquivos e tratar uma tarefa recorrente. O modelo local pode fazer a leitura e a análise no PC, enquanto as ferramentas do Computer ajudam o agente a agir sobre esse contexto. A vantagem é ter planejamento e execução no mesmo fluxo, com os arquivos próximos da máquina onde o trabalho acontece.

Fonte: <https://www.perplexity.ai/hub/products/portable-computer>

## Local e nuvem no mesmo aplicativo

O Portable Computer reúne IA local e modelos na nuvem em um único aplicativo. O caminho local serve para trabalhar com arquivos do PC e concluir tarefas na máquina. Quando uma atividade pede pesquisa ou raciocínio mais avançado, o agente pode identificar a necessidade de apoio na nuvem.

Antes de enviar qualquer informação para fora do dispositivo, o agente pede autorização. Esse pedido é o momento em que você decide se as informações podem sair do PC. Se autorizar, a tarefa pode passar a usar modelos na nuvem. Por isso, a existência de um modelo local não significa que toda tarefa terminará obrigatoriamente no computador.

Fonte: <https://blogs.nvidia.com/blog/local-ai-perplexity-windows-pcs/>

## De Linux e DGX Spark ao Windows

O lançamento no Windows amplia uma plataforma que já tinha suporte para sistemas NVIDIA DGX Spark e PCs RTX com Linux. A novidade está em levar essa experiência para mais usuários de Windows por meio do aplicativo da Perplexity.

O anúncio delimita o suporte atual a GPUs NVIDIA GeForce RTX e NVIDIA RTX PRO com pelo menos 24 GB de VRAM. O suporte ao NVIDIA DGX Station é apresentado como expectativa para o futuro. São três recortes diferentes: Windows já anunciado, Linux e DGX Spark já suportados, e DGX Station com suporte esperado.

Fonte: <https://blogs.nvidia.com/blog/local-ai-perplexity-windows-pcs/>

## Instalação e modelo local pronto para usar

Para usar a versão local no Windows, é preciso ter plano Pro ou Max. O caminho descrito começa pelo download do aplicativo na Microsoft Store. Depois de abrir o app, o usuário escolhe o modelo local no menu e faz o download com um clique.

O anúncio cita Qwen 3.8 27B como exemplo de modelo local. Ele passa por pós-treinamento para trabalhar com o Perplexity Computer e é otimizado para GPUs NVIDIA RTX. Esse preparo permite que o usuário coloque o agente para trabalhar sem pesquisar modelos nem configurar manualmente a pilha de software normalmente necessária para a IA local.

Fonte: <https://www.perplexity.ai/hub/blog/portable-computer-for-windows-is-here>

## Ferramentas integradas e conectores

O aplicativo inclui ferramentas do Computer, como o navegador integrado e a sandbox SPACE, que é proprietária. Uma sandbox é um ambiente controlado para executar atividades. No caso do Portable Computer, ela aparece junto das ferramentas internas que permitem ao agente realizar trabalho dentro do aplicativo.

Os conectores levam esse trabalho para os serviços usados no dia a dia: Microsoft Outlook, OneDrive, Word, Google Drive, Gmail, Slack e GitHub. Um conector é a integração que dá ao agente acesso ao contexto de um serviço para executar uma tarefa. A lista importa porque o valor do agente depende de combinar modelo, ferramentas e os arquivos ou aplicativos que já fazem parte do fluxo do usuário.

- Microsoft Outlook, OneDrive e Word integram o fluxo de documentos e comunicação da Microsoft.
- Google Drive e Gmail integram arquivos e mensagens do Google.
- Slack permite levar achados para um canal da equipe, como no exemplo de startups.
- GitHub permite trabalhar com pull requests e documentação de um projeto conectado.

Fonte: <https://blogs.nvidia.com/blog/local-ai-perplexity-windows-pcs/>

## Engenharia: organizar pull requests no GitHub

Em um projeto conectado ao GitHub, o Computer pode revisar os pull requests abertos, organizá-los por status e identificar os próximos passos. Essa é uma tarefa de agentes porque envolve examinar o contexto das solicitações e transformar a análise em uma lista de trabalho.

O agente também pode sinalizar documentação desatualizada e enviar propostas de atualização para revisão. A proposta mantém a revisão no fluxo: o agente aponta o problema e prepara a mudança, que segue para avaliação antes de entrar como atualização do projeto.

- Entrada: um projeto GitHub conectado com pull requests abertos.
- Análise: revisão das solicitações e organização por status.
- Encaminhamento: identificação dos próximos passos e proposta de atualização para documentação desatualizada.

Fonte: <https://blogs.nvidia.com/blog/local-ai-perplexity-windows-pcs/>

## Finanças: rastrear taxas e arrasto fiscal

O exemplo de finanças começa com dois anos de extratos de corretora, formulários 1099 consolidados e declarações de imposto. O objetivo é encontrar as participações recorrentes que geram mais taxas evitáveis e arrasto fiscal. Arrasto fiscal é a redução do retorno causada por custos tributários.

O agente faz essa análise localmente e cita cada número ao arquivo e à página exatos. A citação transforma o achado em algo verificável: o leitor pode voltar ao documento que sustentou aquele valor. No exemplo descrito, os documentos não precisam chegar a um chatbot para que essa análise seja feita.

- Entrada: dois anos de extratos de corretora, formulários 1099 consolidados e declarações de imposto.
- Objetivo: rastrear participações recorrentes ligadas a taxas evitáveis e arrasto fiscal.
- Saída: achados com cada número citado ao arquivo e à página correspondentes.

Fonte: <https://blogs.nvidia.com/blog/local-ai-perplexity-windows-pcs/>

## Startups: investigar a queda de ativação

No cenário de startups, o usuário pergunta ao Computer por que a ativação ficou estagnada. O agente analisa localmente a exportação do funil para encontrar onde novos cadastros deixam de avançar entre a instalação e a primeira tarefa concluída.

O recorte dessa análise é específico: ela observa a passagem entre instalação e primeira tarefa concluída. Depois, o agente publica os principais achados no canal da equipe no Slack. O conector transforma a análise local em informação disponível para quem trabalha com produto, crescimento ou operação.

- Entrada: uma exportação do funil de ativação.
- Pergunta: onde os novos cadastros param entre a instalação e a primeira tarefa concluída.
- Saída: principais achados publicados no canal da equipe no Slack.

Fonte: <https://blogs.nvidia.com/blog/local-ai-perplexity-windows-pcs/>

## Os números

- 24 GB de VRAM: quantidade mínima de memória de vídeo exigida nas GPUs NVIDIA GeForce RTX e RTX PRO compatíveis. É um requisito de hardware, não uma medida de velocidade ou de qualidade da resposta.
- 27B em Qwen 3.8 27B: indica 27 bilhões de parâmetros no nome do modelo. O anúncio cita esse modelo como exemplo local, pós-treinado para o Computer e otimizado para RTX. A quantidade de parâmetros não mede sozinha a qualidade de um resultado.
- Dois anos de extratos de corretora: período dos documentos usado no exemplo de finanças para rastrear participações recorrentes. É o recorte desse caso, não uma duração obrigatória para toda análise financeira.
- 14 de setembro de 2026: data de publicação do anúncio no blog da NVIDIA que apresenta a disponibilidade do Portable Computer no Windows.

Fonte: <https://blogs.nvidia.com/blog/local-ai-perplexity-windows-pcs/>

## O que muda para você

Com o hardware compatível e o plano Pro ou Max, o Portable Computer permite usar um agente com arquivos e serviços do próprio fluxo de trabalho. O modelo local trata a análise na máquina, os conectores aproximam os dados dos aplicativos e o navegador integrado amplia as ferramentas disponíveis.

Exemplo: imagine que você use o Portable Computer para investigar taxas recorrentes em extratos de corretora. O agente pode analisar os documentos no PC e citar cada número ao arquivo e à página. Se a tarefa exigir apoio de nuvem, ele pede autorização antes de enviar informações. Nesse fluxo, você acompanha tanto o achado quanto a decisão de permitir que dados saiam do dispositivo.

Fonte: <https://www.perplexity.ai/hub/products/portable-computer>

## O que fazer hoje

O caminho de instalação começa pela conferência do hardware e do plano. Depois, o aplicativo prepara o modelo local e os conectores dão contexto para a primeira tarefa.

1. Confira se o PC tem uma GPU NVIDIA GeForce RTX ou NVIDIA RTX PRO compatível e pelo menos 24 GB de VRAM. O resultado esperado é enquadrar a máquina no requisito de hardware anunciado.
2. Verifique se você tem plano Pro ou Max. O resultado esperado é atender ao requisito de acesso à versão local.
3. Baixe o aplicativo da Perplexity para Windows na página oficial da Microsoft Store: https://apps.microsoft.com/detail/9P9XG917PWCJ. O resultado esperado é instalar o app no computador.
4. Abra o aplicativo, escolha o modelo local no menu e baixe com um clique. O resultado esperado é deixar o modelo local pronto para o Portable Computer.
5. Escolha uma tarefa compatível com um conector, como revisar pull requests abertos em um projeto GitHub conectado. O resultado esperado é dar ao agente o contexto para planejar e executar as etapas.
6. Se o agente pedir apoio da nuvem, leia a solicitação e decida se autoriza o envio. O resultado esperado é manter sob seu controle a saída de informações do PC.

Fonte: <https://www.perplexity.ai/hub/blog/portable-computer-for-windows-is-here>

## O que conferir

O Portable Computer combina execução local, conectores e apoio de nuvem. Cada parte tem um limite próprio, e vale separar requisito de hardware, acesso ao produto, consumo de créditos e controle sobre informações antes de começar.

- Hardware: 24 GB é o mínimo de VRAM anunciado. Esse valor não garante velocidade nem qualidade do resultado.
- Acesso: ter uma placa compatível não substitui o requisito de plano Pro ou Max.
- Créditos: o trabalho concluído no computador não consome créditos do Perplexity Computer. Tarefas que recorrem à nuvem podem seguir outro caminho e exigem autorização antes do envio de informações.
- Privacidade: o agente pede permissão antes de enviar dados para modelos na nuvem. Se você autorizar, informações podem sair do dispositivo.
- DGX Station: o suporte é apresentado como expectativa futura. Ele não deve ser confundido com o suporte já anunciado para Windows.
- Resultados em finanças: use as citações de arquivo e página para verificar cada número encontrado pelo agente.
- Resultados em engenharia: a atualização de documentação é proposta para revisão. O agente apresenta a mudança, e a revisão faz parte do fluxo descrito.
- Modelo: Qwen 3.8 27B é o exemplo citado no anúncio. Estar pós-treinado para o Computer e otimizado para RTX descreve o preparo do modelo, não um resultado garantido para qualquer tarefa.

Fonte: <https://blogs.nvidia.com/blog/local-ai-perplexity-windows-pcs/>

## Glossário

- Agente: sistema que recebe um objetivo, planeja etapas e usa ferramentas para executar o trabalho.
- IA local: uso de modelos de inteligência artificial que rodam no próprio dispositivo.
- GPU: processador especializado em executar muitos cálculos em paralelo, usado para acelerar cargas de trabalho como as de IA.
- VRAM: memória dedicada da placa de vídeo. O requisito de 24 GB se refere a essa memória.
- Nuvem: infraestrutura externa onde modelos e serviços podem ser executados. No Portable Computer, o envio de informações para a nuvem depende de autorização.
- Créditos do Perplexity Computer: saldo citado pelo serviço. O trabalho concluído localmente não o consome.
- Conector: integração que permite ao agente trabalhar com o contexto de um aplicativo ou serviço, como GitHub ou Slack.
- Sandbox: ambiente controlado para executar atividades. A SPACE é a sandbox proprietária citada entre as ferramentas do Computer.
- Pull request: proposta de mudanças em um projeto que pode ser revisada antes de ser incorporada.
- Funil de ativação: sequência de passos entre o cadastro ou a instalação e a primeira tarefa concluída pelo usuário.
- Arrasto fiscal: redução do retorno de um investimento causada por custos tributários.
- Parâmetro: valor interno aprendido por um modelo durante o treinamento. A sigla B em 27B indica bilhões de parâmetros.
- Pós-treinamento: treinamento adicional usado para adaptar um modelo a uma tarefa ou ferramenta específica.

Fonte: <https://blogs.nvidia.com/blog/local-ai-perplexity-windows-pcs/>

## Para onde ir depois

Comece com uma tarefa que tenha arquivos e um objetivo claros. Observe quais etapas o agente conclui no PC, quais conectores usa e se ele pede autorização para recorrer à nuvem.

- Se você trabalha com engenharia, pratique com um projeto GitHub conectado e peça a revisão dos pull requests abertos. Acompanhe a organização por status e os próximos passos apresentados.
- Se você trabalha com finanças, use o cenário dos extratos, formulários 1099 e declarações para praticar a conferência das citações de arquivo e página.
- Se você trabalha com uma startup, pratique a análise da passagem entre instalação e primeira tarefa concluída e acompanhe os achados publicados no Slack.
- Use a página oficial do Portable Computer como referência do produto: https://www.perplexity.ai/hub/products/portable-computer.
- Acompanhe o anúncio da Perplexity sobre a versão para Windows: https://www.perplexity.ai/hub/blog/portable-computer-for-windows-is-here.
- Faça uma tarefa por vez e registre se ela terminou localmente ou precisou de apoio de nuvem. Esse registro ajuda a entender onde o agente usa cada caminho.

Fonte: <https://www.perplexity.ai/hub/products/portable-computer>

## Além do vídeo

- A coluna de atualizações do blog cita o Z.ai GLM 5.3 Flash, descrito com desempenho e inteligência visual impressionantes a baixo custo e otimização para DGX Station e sistemas com dois DGX Spark.
- A mesma coluna diz que o DeepSeek-v4.1 Flash reduz de forma significativa a demanda de memória do cache chave-valor e os custos operacionais em cargas complexas de agentes.
- O blog apresenta o Qwen3.8-Flash-Next, um modelo multimodal de mistura de especialistas com pesos abertos e prévia inicial do Qwen4, que pode rodar localmente em um único DGX Spark usando NVFP4.
- O blog apresenta o GLM 5.3, da Z.ai, como um modelo de 744 bilhões de parâmetros ajustado para sessões de agentes de longa duração em DGX Station e em um cluster com quatro DGX Spark.
