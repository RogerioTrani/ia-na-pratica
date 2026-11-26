# n8n passa de 200 mil estrelas e lidera lista de IAs grátis

_2026-11-25 · reportagem_

Esta apostila apresenta 25 projetos de IA do GitHub que podem ser usados gratuitamente, do menos estrelado ao n8n, que passou de 200 mil estrelas. Você vai entender o que cada projeto faz, para quem ele serve e como começar pelo endereço oficial. Também vai aprender a escolher entre ferramentas locais, interfaces de chat, agentes, geração de conteúdo e automações. Ao final, terá critérios para testar uma ferramenta com uma tarefa real e reconhecer os cuidados com arquivos, vozes e ações automáticas.

## Como usar esta lista

Os 25 projetos cobrem trabalhos diferentes: criar apresentações e imagens, conversar com documentos, transcrever áudio, executar tarefas no computador, desenvolver software e conectar serviços. Alguns rodam no seu computador ou servidor. Outros reúnem modelos e ferramentas em uma interface para você usar do seu jeito.

A ordem vai do menos estrelado ao mais estrelado no GitHub. Uma estrela indica popularidade na plataforma. Ela ajuda a entender a repercussão do projeto, mas não mede se ele é adequado para a sua tarefa, nem substitui a leitura das condições de uso e dos requisitos.

1. Por onde começar: escolha uma tarefa que você já precisa fazer, como gerar uma apresentação, conversar com PDFs, transcrever áudio ou automatizar atendimento; o resultado é uma escolha ligada a um problema concreto.
2. Para experimentar IA local, comece por Ollama, indicado na lista como porta de entrada; o resultado esperado é um modelo funcionando no seu computador.
3. Para trabalhar com documentos, compare AnythingLLM, RAGFlow e MarkItDown; o resultado é perceber a diferença entre conversar com arquivos locais, receber respostas com origem e preparar texto para a IA.
4. Para montar agentes ou automações, compare Flowise, Dify, OpenHands e n8n; o resultado é distinguir montagem visual, desenvolvimento de software e ligação entre serviços.
5. Use o endereço oficial de cada seção para chegar ao projeto e teste primeiro com uma tarefa pequena; o resultado esperado é verificar se o fluxo resolve o problema antes de ampliar o uso.

## Presenton

Presenton gera uma apresentação inteira com IA a partir de um tema ou documento. A lista o apresenta como alternativa aberta ao Gamma, com execução no seu próprio servidor. A proposta é transformar uma pauta de reunião em slides sem precisar montar cada página manualmente.

Ele serve a quem precisa preparar apresentações com frequência e quer controlar a hospedagem. Exemplo: você tem um documento para a reunião e usa o Presenton para gerar a apresentação inicial; depois revisa o conteúdo e a ordem dos slides.

- Tecnologia: geração de apresentações com IA e auto-hospedagem.
- Como começar: leve um tema ou documento ao projeto e gere a primeira apresentação; o resultado esperado é um conjunto de slides para revisão.

Fonte: <https://presenton.ai>

## Jan

Jan é uma alternativa ao ChatGPT que roda 100% offline no computador. Você baixa um modelo, desliga a internet e continua conversando. Para quem trabalha com dado sensível, esse desenho mantém a conversa no próprio equipamento.

A ferramenta serve a quem quer conversar com IA sem depender de uma conexão durante o uso. Imagine que um relatório não pode sair da máquina: depois de baixar o modelo, você conversa com Jan e mantém a interação local.

- Tecnologia: chat com modelos de IA executados localmente.
- Como começar: baixe um modelo, abra o Jan e converse; para testar o uso offline, desligue a internet depois do download e verifique se a conversa continua.

Fonte: <https://jan.ai>

## LibreChat

LibreChat reúne GPT, Claude, Gemini e DeepSeek numa tela parecida com a do ChatGPT. A interface permite trocar de modelo no meio da conversa e pode ser hospedada pela própria equipe. Isso concentra o acesso a diferentes modelos em um só lugar.

Para uma equipe, a proposta é sair bem mais barato do que pagar uma assinatura de cada IA para cada pessoa, ao reunir os modelos numa interface própria. Exemplo: uma pessoa começa uma conversa com um modelo e muda para outro quando precisa de outra resposta, usando a mesma tela hospedada pela equipe.

- Tecnologia: interface de chat com múltiplos modelos e auto-hospedagem.
- Como começar: hospede a interface e escolha entre os modelos disponíveis; o resultado esperado é uma conversa que permite alternar entre eles.

Fonte: <https://librechat.ai>

## LocalAI

LocalAI roda modelos de texto, imagem, voz e vídeo em praticamente qualquer máquina. O detalhe é que ele não precisa de placa de vídeo. Um computador parado em casa ou no escritório pode assumir o papel de servidor de IA.

A ferramenta serve a quem quer aproveitar uma máquina existente para executar modelos. Exemplo: um computador do escritório sem placa de vídeo pode ser usado para rodar as modalidades de IA que a equipe precisa, no próprio ambiente.

- Tecnologia: execução local de modelos de texto, imagem, voz e vídeo.
- Como começar: separe uma máquina e use o LocalAI como servidor; o resultado esperado é ter os modelos disponíveis nesse computador.

Fonte: <https://localai.io>

## Fooocus

Fooocus gera imagens com IA sem exigir que você mexa em muitas configurações. Você escreve o que quer e a ferramenta cuida do restante. É uma porta de entrada para quem está começando e quer um processo direto.

Ele serve para produzir capas, thumbnails e imagens de posts sem depender de uma ferramenta paga. Exemplo: para ilustrar uma publicação, você descreve a imagem desejada e usa o resultado como ponto de partida para a arte.

- Tecnologia: geração de imagens com configuração simplificada.
- Como começar: escreva a descrição de uma capa, thumbnail ou imagem de post; o resultado esperado é a imagem gerada para revisão.

Fonte: <https://github.com/lllyasviel/Fooocus>

## Flowise

Flowise monta agentes de IA ligando blocos na tela, como um fluxograma. Cada bloco representa uma parte do trabalho e pode conectar documentos, ferramentas e o modelo escolhido. A montagem visual mostra como as partes do agente se encaixam.

A ferramenta serve para criar assistentes que usam informações e recursos específicos. Exemplo: um assistente de atendimento pode receber os documentos da empresa e responder às dúvidas dos clientes com base nesse conteúdo.

- Tecnologia: construção visual de agentes e fluxos de IA.
- Como começar: monte um fluxo com blocos que conectem modelo, documentos e ferramentas; o resultado esperado é um agente que usa esses elementos para responder.

Fonte: <https://flowiseai.com>

## GPT-SoVITS

GPT-SoVITS clona uma voz com um minuto de áudio e transforma texto em fala. O minuto se refere à amostra usada na clonagem; ele descreve a entrada do processo, não o tamanho do texto que pode ser narrado. O uso exige permissão para trabalhar com a voz escolhida.

A ferramenta serve para narrar vídeos e aulas sem regravar tudo. Exemplo: você usa a própria voz, com autorização, para gerar a fala de um roteiro e aproveita essa gravação na produção do conteúdo.

- Tecnologia: clonagem de voz e conversão de texto em fala.
- Como começar: separe um minuto de áudio de uma voz autorizada, faça a clonagem e envie o texto; o resultado esperado é a fala gerada com essa voz.

Fonte: <https://github.com/RVC-Boss/GPT-SoVITS>

## AnythingLLM

AnythingLLM permite colocar PDFs, contratos e planilhas na ferramenta e conversar com esses arquivos. A execução é local, então os documentos não são enviados para outra pessoa. Isso aproxima a IA de arquivos que já fazem parte do seu trabalho.

Ele serve para localizar informações dentro de materiais extensos. Exemplo: você pergunta onde está uma cláusula de um contrato ou um número de um relatório gigante e usa a resposta para chegar ao trecho correspondente.

- Tecnologia: conversa com documentos executada localmente.
- Como começar: carregue PDFs, contratos ou planilhas e faça perguntas sobre eles; o resultado esperado é uma resposta baseada nos arquivos locais.

Fonte: <https://anythingllm.com>

## Open Interpreter

Open Interpreter é um agente que escreve e roda código no computador para cumprir uma tarefa. Você pode pedir em português, e ele trabalha com modelos abertos. A diferença de um chat comum é que o pedido pode resultar em ações reais sobre arquivos e programas.

Ele serve para organizar pastas, converter arquivos ou gerar gráficos a partir de planilhas. Exemplo: você pede um gráfico com base nos dados de uma planilha e acompanha o código que o agente escreve e executa para produzir o resultado.

- Tecnologia: agente local com execução de código e modelos abertos.
- Como começar: peça uma tarefa concreta em português e acompanhe a execução; o resultado pode ser uma pasta organizada, um arquivo convertido ou um gráfico.

Fonte: <https://openinterpreter.com>

## Cline

Cline é um agente de programação dentro do editor de código. Ele lê o projeto, escreve arquivos, roda comandos e pede aprovação a cada passo. Essa sequência de aprovações dá ao usuário um ponto de controle durante o trabalho.

A ferramenta serve mesmo para quem programa pouco e quer tirar uma ideia do papel. Exemplo: você descreve a alteração desejada, revisa o que Cline propõe e aprova cada etapa da edição e da execução dos comandos.

- Tecnologia: agente de programação integrado ao editor de código.
- Como começar: abra o projeto com Cline e acompanhe as propostas; o resultado esperado são arquivos e comandos trabalhados com a sua aprovação.

Fonte: <https://cline.bot>

## LobeHub

LobeHub organiza um time de agentes de IA com tarefas, horários e relatórios. A proposta é ter agentes trabalhando o dia inteiro enquanto você acompanha os resultados. Cada agente pode assumir uma função dentro desse conjunto.

A ferramenta serve para dividir atividades entre pesquisa, conteúdo e atendimento. Exemplo: um agente pesquisa assuntos do mercado, outro produz conteúdo e outro atende demandas, com tarefas e horários organizados e relatórios para acompanhamento.

- Tecnologia: organização de múltiplos agentes com tarefas, horários e relatórios.
- Como começar: defina as funções e os horários dos agentes; o resultado esperado é um time de IA acompanhado pelos relatórios.

Fonte: <https://lobehub.com>

## OpenHands

OpenHands é um agente que desenvolve software. Ele abre o projeto, escreve o código, roda os testes e corrige o que quebrou. O ciclo inclui a escrita e a verificação, então a entrega passa por um processo de desenvolvimento.

A lista o compara a um desenvolvedor júnior trabalhando enquanto você faz outra coisa. Exemplo: você entrega um projeto e acompanha o agente pelas etapas de código e testes; a revisão do trabalho continua sendo parte do processo.

- Tecnologia: agente de desenvolvimento de software com escrita de código e testes.
- Como começar: entregue um projeto e acompanhe o ciclo de código e testes; o resultado esperado é software com as falhas encontradas corrigidas.

Fonte: <https://openhands.dev>

## RAGFlow

RAGFlow entende documentos complicados, como PDFs cheios de tabelas, e responde com base neles. Ele também mostra de onde tirou cada resposta. A origem permite que o leitor acompanhe a informação até o documento consultado.

A ferramenta serve a empresas com manuais, políticas e catálogos extensos. Exemplo: um funcionário pergunta sobre uma regra interna e recebe uma resposta acompanhada da origem, o que ajuda a localizar o trecho usado.

- Tecnologia: leitura de documentos complexos e respostas com origem.
- Como começar: leve manuais, políticas, catálogos ou PDFs com tabelas e faça perguntas; o resultado esperado é uma resposta com a origem indicada.

Fonte: <https://ragflow.io>

## Whisper

Whisper, da OpenAI, é um modelo aberto de transcrição que entende dezenas de idiomas, inclusive português. Ele está por trás de muitas ferramentas de legenda e permite transcrever reuniões, podcasts e vídeos sem pagar por minuto.

O modelo serve para transformar áudio em texto que pode ser consultado ou reaproveitado. Exemplo: você transcreve uma reunião e usa o texto para localizar decisões, revisar conteúdos ou preparar um resumo.

- Tecnologia: transcrição automática de áudio com modelo aberto.
- Como começar: use o Whisper para processar o áudio de uma reunião, podcast ou vídeo; o resultado esperado é a transcrição em português ou em outro idioma suportado.

Fonte: <https://github.com/openai/whisper>

## Browser Use

Browser Use é um agente que usa o navegador por você. A partir de um pedido em texto, ele clica, preenche formulários e pesquisa. A tarefa é executada como uma sequência de ações no navegador.

A ferramenta serve para buscar preços, preencher cadastros ou coletar dados de sites. Exemplo: você pede a coleta de preços e acompanha as pesquisas e visitas do agente para obter o conteúdo organizado.

- Tecnologia: automação de navegador por meio de pedidos em texto.
- Como começar: descreva a tarefa e acompanhe cliques, formulários e pesquisas; o resultado esperado é a ação ou a coleta solicitada.

Fonte: <https://browser-use.com>

## llama.cpp

llama.cpp é o motor que faz modelos de IA rodarem rápido, até em um notebook comum. Muitas ferramentas da lista usam esse motor por baixo. Ele fornece a base de execução para que o modelo funcione no equipamento.

A proposta é permitir uma IA local sem pagar API e sem enviar dados para fora. Exemplo: uma ferramenta que conversa com um modelo no notebook pode usar essa base para executar o modelo, enquanto a interface aparece em outro programa.

- Tecnologia: motor de execução local para modelos de IA.
- Como começar: use essa base para executar modelos em um notebook comum; o resultado esperado é IA funcionando localmente, sem API e sem envio de dados para fora.

Fonte: <https://github.com/ggml-org/llama.cpp>

## ComfyUI

ComfyUI gera imagem e vídeo com IA montando um fluxo visual, bloco por bloco. O usuário controla as etapas da geração e pode ajustar o processo para buscar um resultado específico. É uma opção para quem quer mais controle sobre a produção.

A ferramenta é usada por profissionais e serve para trabalhar consistência visual em campanhas. Exemplo: você monta um fluxo com o estilo desejado e usa a mesma estrutura para produzir imagens de uma campanha.

- Tecnologia: geração de imagem e vídeo com fluxo visual por blocos.
- Como começar: monte o fluxo bloco por bloco; o resultado esperado é uma geração com controle sobre as etapas do processo.

Fonte: <https://github.com/Comfy-Org/ComfyUI>

## Open WebUI

Open WebUI oferece uma tela parecida com a do ChatGPT, ligada aos modelos que você escolher, inclusive os locais. Ele também permite criar uma conta para cada pessoa da equipe e controlar quem usa o quê.

A interface serve para dar acesso organizado a diferentes modelos. Exemplo: uma equipe conecta os modelos que vai usar, cria as contas dos integrantes e acompanha o acesso de cada pessoa pela mesma interface.

- Tecnologia: interface de chat com modelos escolhidos e contas de equipe.
- Como começar: conecte os modelos e crie as contas da equipe; o resultado esperado é acesso individual com controle de uso.

Fonte: <https://openwebui.com>

## Dify

Dify permite montar aplicativos e agentes de IA arrastando blocos. A plataforma inclui base de conhecimento e dispensa programar tudo do zero. A montagem visual reúne as partes do aplicativo em um fluxo que pode ser ajustado.

Ela serve para criar chatbots internos e automações de atendimento. Exemplo: uma empresa monta um assistente com blocos e inclui os documentos internos na base de conhecimento para responder às dúvidas dos funcionários.

- Tecnologia: criação visual de aplicativos e agentes com base de conhecimento.
- Como começar: arraste os blocos e inclua a base de conhecimento; o resultado esperado é um chatbot interno ou uma automação de atendimento.

Fonte: <https://dify.ai>

## Stable Diffusion WebUI

Stable Diffusion WebUI é a interface mais conhecida para gerar imagens com Stable Diffusion no computador, segundo a lista. A comunidade criou centenas de extensões para ampliar o que a interface faz. Isso combina geração local com recursos adicionais.

Ela é apresentada como uma das formas mais completas de gerar imagens sem pagar pela ferramenta. Exemplo: você gera imagens no próprio computador e usa extensões da comunidade para ampliar os recursos disponíveis na interface.

- Tecnologia: interface local para Stable Diffusion com extensões da comunidade.
- Como começar: use a interface no computador para gerar imagens; o resultado esperado é a imagem produzida, com extensões disponíveis para ampliar funções.

Fonte: <https://github.com/AUTOMATIC1111/stable-diffusion-webui>

## Ollama

Ollama é a porta de entrada para a IA local na lista. Com um comando, você roda modelos como DeepSeek, Qwen e Gemma no computador. A lista recomenda começar por ele quando a ideia é experimentar um único projeto.

O comando abaixo baixa e abre o Gemma4 para uso local. Depois disso, você pode conversar com o modelo no seu computador.

- Tecnologia: execução local de modelos por linha de comando.
- Como começar: rode o comando desta seção para baixar e abrir o Gemma4; o resultado esperado é uma conversa com o modelo local.

```
ollama run gemma4
```

Fonte: <https://ollama.com>

## AutoGPT

AutoGPT foi um dos primeiros agentes autônomos a viralizar. Hoje é uma plataforma para criar agentes que trabalham sozinhos, sem você enviar um prompt a cada etapa. A proposta é transformar uma tarefa contínua em um trabalho acompanhado pelo agente.

Ele serve para atividades que se repetem. Exemplo: você cria um agente que pesquisa notícias do seu mercado e manda um resumo todos os dias, reduzindo a necessidade de conduzir cada etapa manualmente.

- Tecnologia: plataforma para criação de agentes autônomos.
- Como começar: crie um agente com uma tarefa recorrente, como pesquisar notícias e enviar um resumo diário; o resultado esperado é a execução dessa rotina.

Fonte: <https://github.com/Significant-Gravitas/AutoGPT>

## MarkItDown

MarkItDown, da Microsoft, transforma PDF, Word, Excel e PowerPoint em texto limpo. Esse texto é preparado no formato que a IA costuma entender melhor. O trabalho da ferramenta é organizar o conteúdo antes de ele chegar ao modelo.

Ela serve como etapa anterior ao uso de um documento com IA. Exemplo: antes de enviar um relatório para um assistente, você passa o arquivo pelo MarkItDown e usa o texto resultante como entrada para as perguntas.

- Tecnologia: conversão de documentos para texto limpo.
- Como começar: passe PDFs, Word, Excel ou PowerPoint pela ferramenta; o resultado esperado é um texto preparado para ser usado pela IA.

Fonte: <https://github.com/microsoft/markitdown>

## Firecrawl

Firecrawl pega o conteúdo de um site e devolve esse conteúdo organizado para a IA usar. O resultado pode alimentar pesquisas, comparativos, monitoramento de concorrente e agentes. Assim, a IA recebe uma versão estruturada do conteúdo da página.

A ferramenta serve quando você precisa trabalhar com informações publicadas na web. Exemplo: você aponta o site de um concorrente, recebe o conteúdo organizado e usa esse material para resumir ou comparar informações.

- Tecnologia: extração e organização de conteúdo de sites para IA.
- Como começar: aponte um site e receba o conteúdo preparado; o resultado esperado é material para resumir, comparar ou alimentar um agente.

Fonte: <https://firecrawl.dev>

## n8n

n8n é a automação com IA que lidera a lista, com mais de 200 mil estrelas no GitHub. Ele se conecta a mais de 1.500 integrações e roda no seu próprio servidor. O número de integrações descreve as ligações disponíveis para montar fluxos entre ferramentas.

A proposta é criar um funcionário digital que trabalha 24 horas. Exemplo: um lead chega, a planilha é atualizada e mensagens de WhatsApp e e-mail saem automaticamente. As etapas ficam ligadas no fluxo para que a automação execute a sequência.

- Tecnologia: automação com IA, integrações e execução no próprio servidor.
- Como começar: monte um fluxo que ligue a chegada de um lead à atualização da planilha e ao envio das mensagens; o resultado esperado é a sequência executada automaticamente.

Fonte: <https://n8n.io>

## Cuidados

A lista apresenta os 25 projetos como gratuitos. Quando a ferramenta roda no seu computador ou servidor, a execução depende da infraestrutura que você usa. Antes de adotar um projeto, leia as condições e os requisitos no repositório oficial, especialmente para uso profissional ou distribuição.

Os projetos têm desenhos diferentes. Jan e AnythingLLM são descritos como locais. LibreChat reúne vários modelos em uma interface. n8n roda no seu servidor e conecta integrações. Para arquivos sensíveis, escolha a configuração que corresponde ao uso local descrito e mantenha essa característica durante a instalação.

Agentes executam ações. Open Interpreter roda código, Browser Use clica e preenche formulários, e Cline pede aprovação a cada passo. Acompanhe os pedidos e os resultados. Em automações, revise o fluxo e as integrações antes de ampliar o alcance das ações.

- Voz: use GPT-SoVITS somente com vozes que você tem permissão para clonar; um minuto de áudio é uma amostra de entrada, não uma autorização de uso.
- Documentos: AnythingLLM processa os arquivos localmente; use essa característica para escolher a ferramenta no cenário de dados sensíveis.
- Respostas com documentos: RAGFlow mostra a origem da resposta; use essa informação para revisar o trecho consultado.
- Código e testes: OpenHands escreve código, roda testes e corrige falhas; acompanhe os testes e revise o resultado antes de levar o software adiante.
- Navegador: Browser Use pode clicar, preencher formulários e pesquisar; descreva a tarefa com clareza e acompanhe as ações realizadas.
- Requisitos: LocalAI dispensa placa de vídeo e llama.cpp roda até em notebook comum; os requisitos variam conforme o modelo e a tarefa escolhida.
- Popularidade: as estrelas do GitHub medem repercussão, não garantia de adequação, segurança ou resultado para o seu uso.

## Glossário

Estes termos aparecem ao longo da lista e ajudam a entender a diferença entre os projetos.

- GitHub: plataforma onde ficam os repositórios dos projetos e onde as estrelas indicam popularidade.
- Estrela no GitHub: marca dada por um usuário a um projeto na plataforma.
- Modelo de IA: sistema que processa entradas e produz resultados como texto, imagem, voz ou vídeo.
- Modelo aberto: modelo disponibilizado segundo as condições de uso do projeto que o publica.
- IA local: IA executada no seu próprio computador ou servidor.
- Auto-hospedagem: execução de um software na infraestrutura que você administra.
- API: interface usada por um programa para solicitar serviços de outro sistema.
- Agente de IA: sistema que recebe uma tarefa e realiza ações usando modelos, ferramentas ou código.
- Fluxo visual: representação de um processo por blocos conectados na tela.
- Base de conhecimento: conjunto de documentos usado para fundamentar as respostas de um assistente.
- Prompt: instrução escrita enviada à IA para orientar uma tarefa ou conversa.
- Integração: ligação que permite a uma ferramenta trocar dados ou acionar outra.
- Transcrição: conversão de áudio em texto.
- Texto para fala: conversão de um texto em uma voz gerada.
- Placa de vídeo ou GPU: hardware usado para processar tarefas gráficas e de IA.
- Extensão: recurso adicional que amplia as funções de uma interface.

## Para onde ir depois

O próximo passo é escolher uma tarefa real e testar o projeto que combina com ela. Use o endereço oficial da seção, faça um primeiro teste e observe se o resultado ajuda no trabalho. Um teste pequeno mostra onde você precisa ajustar o processo.

Se quiser começar pela IA local, use o comando de Ollama. Se o interesse for conteúdo, compare Fooocus, ComfyUI e Stable Diffusion WebUI. Para documentos, prepare o texto e pratique perguntas. Para automação, desenhe primeiro as etapas e as conexões necessárias.

- Pratique IA local com Ollama: rode o comando da seção e confirme que consegue conversar com o modelo baixado.
- Pratique leitura de documentos: use MarkItDown para preparar o texto e faça perguntas com AnythingLLM ou RAGFlow, observando a resposta e a origem quando ela for apresentada.
- Pratique geração de imagem: comece por Fooocus se quiser simplicidade; use ComfyUI ou Stable Diffusion WebUI se quiser controlar o fluxo ou ampliar a interface com extensões.
- Pratique automação: escreva a sequência de tarefas e escolha Flowise, Dify ou n8n conforme o trabalho exigir blocos visuais, aplicativo com conhecimento ou integrações entre serviços.
