# Code Storage seguirá disponível após a aquisição

_2026-11-21 · noticia_

A OpenAI anunciou em 4 de novembro de 2026 um acordo para adquirir a Pierre Computer Company, empresa por trás do Code Storage e das ferramentas open-source Trees, Diffs e Highlights. O objetivo é ampliar o Codex, agente de programação da OpenAI, com recursos para construir, entender e revisar código. Os clientes do Code Storage poderão continuar usando o serviço após o fechamento, enquanto a OpenAI trabalha para levar suas funcionalidades ao Codex. Os projetos open-source da Pierre permanecerão abertos, com contribuições contínuas da OpenAI. A transação ainda depende de condições habituais de fechamento, incluindo aprovações regulatórias.

## O fato

Em 4 de novembro de 2026, a OpenAI divulgou que vai adquirir a Pierre Computer Company. A empresa é responsável pelo Code Storage e por um conjunto de ferramentas open-source para desenvolvimento, incluindo Trees, Diffs e Highlights. O anúncio liga a operação à expansão das ferramentas do Codex para construir, entender e revisar código.

A compra ainda não está concluída. O fechamento depende de condições habituais, incluindo a obtenção de aprovações regulatórias. Até lá, OpenAI e Pierre continuam sendo empresas separadas e independentes. Por isso, a data do anúncio marca a comunicação pública da operação, não a conclusão da aquisição.

Para quem desenvolve com agentes de IA, o fato mostra uma mudança de foco. A discussão inclui o armazenamento de código, seu histórico, a navegação pelos arquivos e a revisão de alterações. São partes do trabalho que ficam ao redor da geração de código e influenciam a forma como uma equipe acompanha o que foi produzido.

Fonte: <https://openai.com/index/openai-to-acquire-pierre/>

## Por que isso importa

O Codex é o agente de programação da OpenAI. Quando um agente participa do desenvolvimento, o fluxo de trabalho precisa acomodar código escrito por pessoas e por máquinas. O anúncio da aquisição trata justamente das ferramentas que ajudam a organizar esse trabalho e a revisar seus resultados.

Revisar código significa examinar o que mudou e decidir se a alteração atende ao objetivo do projeto. Em um volume grande de arquivos e modificações, localizar um trecho e entender uma mudança consomem atenção. Trees ajuda na navegação; Diffs ajuda a visualizar e editar alterações. O Code Storage trata do armazenamento e do histórico usando Git.

A ambição declarada pela OpenAI é conectar, no Codex, o código que uma empresa entrega às decisões tomadas pelas pessoas. Na prática, isso aproxima funções que hoje aparecem em ferramentas diferentes: guardar código, acompanhar branches, revisar mudanças e acompanhar a entrega. A aquisição reúne peças desse percurso, da primeira branch criada por um agente até o código publicado no mundo.

Fonte: <https://openai.com/index/openai-to-acquire-pierre/>

## Git, agentes e trabalho em paralelo

Git é um sistema de controle de versão. Ele registra alterações ao longo do tempo e permite que diferentes linhas de trabalho, chamadas branches, avancem antes de serem reunidas. Esse histórico ajuda a responder quem mudou o quê e dá base para comparar versões do código.

A OpenAI afirma que os sistemas ao redor do Git precisam evoluir à medida que mais trabalho acontece em paralelo. O anúncio também menciona Pando, seu backend interno de controle de código-fonte para engenheiros e agentes, como parte do trabalho de escalar Git na empresa. Pando é apresentado como uma solução interna da OpenAI; a aquisição da Pierre é outro movimento voltado às ferramentas usadas no desenvolvimento com agentes.

Imagine que uma equipe use agentes para produzir alterações em paralelo. Pessoas precisam encontrar os arquivos certos, comparar o que mudou e revisar o resultado de cada branch. Trees e Diffs atendem às duas primeiras necessidades. O Code Storage oferece armazenamento e histórico baseados em Git. Juntas, essas peças mostram por que o trabalho com agentes exige atenção para toda a estrutura ao redor do código.

Fonte: <https://openai.com/index/openai-to-acquire-pierre/>

## A Pierre e seu conjunto de ferramentas

A Pierre Computer Company reúne um serviço e bibliotecas que cobrem etapas diferentes do desenvolvimento. O Code Storage armazena código e acompanha seu histórico. Trees permite navegar pelos arquivos de um projeto. Diffs mostra alterações e oferece edição dentro da revisão. Highlights realça a sintaxe enquanto o código é digitado ou recebido de um agente.

O anúncio da OpenAI destaca que Trees e Diffs já são usadas no aplicativo Codex. Quem navegou por arquivos ou revisou uma alteração nesse aplicativo já teve contato com o trabalho da Pierre. Isso diferencia essas bibliotecas do Code Storage: as primeiras já aparecem na experiência do Codex, enquanto as funcionalidades do serviço são objeto do trabalho de integração anunciado.

A própria composição da equipe também explica a ligação entre as ferramentas. Segundo o anúncio, a mesma pequena equipe que colocou um editor dentro de um diff desenhou a API do Code Storage. O portfólio nasceu da atenção a partes concretas do trabalho com Git, especialmente a navegação e a revisão de código.

Fonte: <https://openai.com/index/openai-to-acquire-pierre/>

## Code Storage: código e histórico com Git

O Code Storage é um serviço que permite que aplicativos armazenem código e acompanhem seu histórico usando Git. Sua API foi desenhada pela equipe da Pierre para fornecer essa estrutura a outros produtos. API é a interface que um programa usa para solicitar serviços e trocar informações com outro sistema.

O valor desse desenho está em juntar duas necessidades: guardar o conteúdo do código e preservar a sequência de alterações. Um aplicativo pode usar o serviço como infraestrutura de armazenamento e histórico, em vez de tratar essas duas funções como problemas isolados. O Git continua sendo a base para registrar as mudanças.

O anúncio tranquiliza os clientes atuais ao afirmar que eles poderão continuar usando o Code Storage depois que a aquisição fechar. Ao mesmo tempo, a OpenAI diz que trabalha para levar os recursos e as funcionalidades do serviço para dentro do Codex. São dois compromissos distintos: manter o serviço disponível para seus clientes e desenvolver a integração com o agente.

Exemplo: Imagine um aplicativo que precisa guardar o código de seus usuários e mostrar o histórico das alterações. O Code Storage foi desenhado para esse tipo de necessidade. A integração anunciada com o Codex é um passo separado e não altera a possibilidade de continuar usando o serviço após o fechamento.

Fonte: <https://code.storage>

## Trees: navegação em projetos de código

Trees é a biblioteca da Pierre voltada à navegação pelos arquivos de um projeto. Ela permite que uma pessoa encontre e percorra a estrutura do código com rapidez. O anúncio da OpenAI destaca o desempenho de Trees e Diffs para trabalhar com grandes volumes de código.

Navegar é uma etapa necessária da revisão. Antes de avaliar uma alteração, o revisor precisa localizar o arquivo, entender onde ele fica no projeto e chegar ao trecho relevante. Uma árvore de arquivos organiza essa busca e reduz o esforço de abrir caminhos manualmente em uma estrutura extensa.

Trees já é usada no aplicativo Codex, segundo o anúncio. Para estudar a ferramenta, o leitor pode consultar a página oficial ou o repositório open-source da Pierre, em https://github.com/pierrecomputer/pierre.

Exemplo: Imagine um projeto com muitos arquivos espalhados por pastas. Durante uma revisão, você precisa encontrar o arquivo alterado e ver os arquivos próximos. Trees organiza esse percurso para que a atenção fique na análise do código.

Fonte: <https://trees.software>

## Diffs: visualização e edição de alterações

Diffs é uma biblioteca open-source para renderização de diferenças e de código. Uma diferença, ou diff, mostra o que mudou entre duas versões. Em uma revisão, ela ajuda a identificar trechos acrescentados, removidos ou modificados sem exigir a leitura integral do arquivo.

A ferramenta também possui o modo Edit. Esse recurso permite que o revisor corrija uma linha de código no mesmo lugar em que encontra o problema. A edição dentro da visualização da alteração aproxima a descoberta da correção e evita a troca constante entre ler o diff e procurar o arquivo original em outra parte da interface.

Diffs já é usada no aplicativo Codex, e sua página oficial cita o pacote @pierre/diffs. Para quem está aprendendo a revisar código, vale observar como a ferramenta organiza as mudanças e como o modo Edit mantém o contexto da revisão.

Exemplo: Imagine que um revisor encontre uma linha incorreta em uma alteração. Com o modo Edit, ele pode corrigir esse trecho enquanto ainda examina o diff. O benefício é manter o problema e a ação de corrigir na mesma tela.

Fonte: <https://diffs.com>

## Highlights: sintaxe durante a digitação e o streaming

Highlights é um realçador de sintaxe. Ele reconhece elementos do código, como palavras reservadas, strings e comentários, e aplica cores para facilitar a leitura. A característica destacada no anúncio é a velocidade: o realce acompanha a digitação de uma pessoa ou o código que chega por streaming de um agente.

Streaming significa receber o conteúdo em partes, conforme ele é produzido. Quando um agente escreve código dessa forma, a visualização precisa acompanhar a chegada de novos trechos. O anúncio descreve Highlights como uma ferramenta muito rápida que atualiza o realce durante esse processo.

O projeto é open-source, com o pacote identificado como @pierre/highlights e o código no repositório github.com/pierrecomputer/pierre. Sua página oficial está em diffs.com/highlights.

Exemplo: Imagine que um agente comece a enviar uma função e continue acrescentando linhas. O Highlights atualiza as cores conforme o código chega. Isso ajuda o leitor a reconhecer a estrutura do trecho enquanto a geração ainda está em andamento.

Fonte: <https://diffs.com/highlights>

## A integração planejada no Codex

A OpenAI quer levar o trabalho da Pierre para dentro do Codex. A ambição declarada é avançar o futuro do controle de código-fonte e conectar o código entregue por uma empresa às decisões de suas pessoas. O anúncio descreve esse percurso desde a primeira branch criada por um agente até o momento em que o código é implantado no mundo.

Parte desse trabalho já aparece no Codex: Trees e Diffs são usadas no aplicativo para navegação e revisão. O Code Storage ocupa outro ponto do plano. Seus clientes poderão continuar usando o serviço após o fechamento, e a OpenAI trabalha para incorporar seus recursos ao Codex.

A OpenAI apresenta sua ambição para depois do fechamento, e a aquisição está sujeita a condições de fechamento e aprovações regulatórias. Até lá, as duas empresas operam de forma independente. Ao ler novidades sobre o Codex, é importante separar o que já está no aplicativo, o que está em desenvolvimento e o que só passa a valer depois do fechamento.

Exemplo: Imagine o fluxo completo de uma alteração produzida com ajuda de um agente. Uma branch guarda a linha de trabalho, Trees ajuda a localizar arquivos, Diffs mostra as mudanças e o histórico registra a evolução do código. O plano da OpenAI é reunir essas partes no Codex, aproximando o trabalho de desenvolvimento da entrega.

Fonte: <https://openai.com/index/openai-to-acquire-pierre/>

## Open-source e licenças depois da aquisição

A OpenAI afirma que os projetos open-source da Pierre continuarão open-source e que seguirá contribuindo com eles. O compromisso inclui o ecossistema formado por Trees, Diffs e Highlights. Para quem usa ou contribui com essas bibliotecas, a declaração mantém o caráter aberto dos projetos depois da operação.

Open-source significa que o código-fonte é disponibilizado sob uma licença que estabelece as condições de uso, modificação e distribuição. O repositório open-source da Pierre reúne os projetos em um monorepo e usa a licença Apache-2.0. Essa licença é a referência para entender as condições aplicáveis ao código distribuído ali.

A abertura do código e a continuidade das contribuições são pontos separados da conclusão da compra. O anúncio trata dos três ao mesmo tempo: a aquisição está condicionada ao fechamento, o Code Storage continuará disponível para clientes e os projetos open-source permanecerão abertos. Cada afirmação vale no escopo indicado pela OpenAI.

Fonte: <https://github.com/pierrecomputer/pierre>

## Os números

- 4 de novembro de 2026: data em que a OpenAI divulgou o anúncio da aquisição. Essa data não representa a conclusão da compra, que depende das condições de fechamento.
- 3 bibliotecas open-source nomeadas no anúncio: Trees, Diffs e Highlights. Elas cobrem navegação de arquivos, visualização e edição de alterações e realce de sintaxe. A quantidade indica o conjunto citado, não uma medida de adoção ou desempenho.
- 2 empresas independentes até o fechamento: OpenAI e Pierre. Essa separação vale enquanto a transação não cumpre as condições necessárias para ser concluída.

Fonte: <https://openai.com/index/openai-to-acquire-pierre/>

## O que muda para você

Se você é cliente do Code Storage, o ponto principal é a continuidade. O anúncio permite que o serviço continue sendo usado depois do fechamento. Enquanto isso, a OpenAI trabalha para levar os recursos do serviço ao Codex, sem prazo divulgado.

Se você desenvolve no Codex, já pode encontrar Trees e Diffs no aplicativo. Elas ajudam na navegação por arquivos e na revisão de alterações. A aquisição indica que a OpenAI pretende ampliar esse conjunto com o trabalho da Pierre, incluindo os recursos do Code Storage.

Se você contribui com open-source, o repositório da Pierre continua sendo a referência dos projetos. A OpenAI afirma que eles permanecerão abertos e que seguirá contribuindo. Ao trabalhar com o código, siga os termos da licença Apache-2.0 conforme aparecem no repositório.

Exemplo: Imagine uma equipe que usa Code Storage em seu aplicativo e também desenvolve com o Codex. Ela pode manter o serviço para armazenamento e histórico enquanto acompanha a integração anunciada. Ao mesmo tempo, pode usar Trees e Diffs para entender melhor a navegação e a revisão que já existem no aplicativo.

Fonte: <https://openai.com/index/openai-to-acquire-pierre/>

## O que fazer hoje

1. Se você usa o Code Storage, continue seu fluxo no serviço disponível em https://code.storage. O resultado esperado é manter o armazenamento de código e o histórico após o fechamento, conforme o anúncio da OpenAI.
2. Se você desenvolve no Codex, acesse https://chatgpt.com/codex e observe a navegação de arquivos e a visualização de alterações. O resultado esperado é reconhecer o trabalho de Trees e Diffs, que o anúncio diz já serem usados no aplicativo.
3. Se quiser estudar as ferramentas da Pierre, abra https://github.com/pierrecomputer/pierre e localize os projetos Trees, Diffs e Highlights. O resultado esperado é encontrar o código de cada projeto no monorepo.
4. Se você contribui com open-source, use o repositório da Pierre como referência para os projetos e para a licença Apache-2.0. O resultado esperado é trabalhar com os nomes, a estrutura e as condições de distribuição adotados pelo projeto.
5. Use o anúncio oficial da OpenAI como referência para o status da operação. O resultado esperado é distinguir a data do anúncio, a continuidade do Code Storage e as condições que ainda regem o fechamento.

Fonte: <https://openai.com/index/openai-to-acquire-pierre/>

## O que conferir

- Status da transação: a operação foi anunciada e o fechamento depende de condições habituais, incluindo aprovações regulatórias.
- Data: 4 de novembro de 2026 é a data do anúncio. Ela não deve ser usada como data de conclusão da aquisição.
- Code Storage: os clientes podem continuar usando o serviço após o fechamento. O trabalho para levar suas funcionalidades ao Codex é uma integração separada.
- Trees e Diffs: o anúncio afirma que essas bibliotecas já são usadas no aplicativo Codex. Essa informação pertence a elas e não deve ser transferida ao Code Storage.
- Highlights: a característica descrita é atualizar o realce de sintaxe durante a digitação ou o streaming de código. Ao avaliar a experiência, observe esse comportamento no contexto em que a biblioteca for usada.
- Licença: o repositório open-source da Pierre usa Apache-2.0. Aplique os termos dessa licença ao usar, modificar ou distribuir o código.
- Independência das empresas: até o fechamento, OpenAI e Pierre permanecem separadas e independentes.

Fonte: <https://openai.com/index/openai-to-acquire-pierre/>

## Glossário

- Agente de código: sistema de IA que participa de tarefas de programação, como escrever, entender e revisar código.
- API: interface que permite a um programa solicitar serviços e trocar informações com outro sistema.
- Apache-2.0: licença open-source adotada pelo repositório da Pierre, com condições para uso, modificação e distribuição do código.
- Branch: linha separada de trabalho no Git, onde alterações podem ser desenvolvidas antes de serem reunidas ao restante do projeto.
- Codex: agente de programação da OpenAI que recebe as ferramentas e integrações descritas no anúncio.
- Controle de versão: sistema que registra alterações de arquivos ao longo do tempo e permite comparar versões.
- Diff: representação das diferenças entre duas versões de código ou de um arquivo.
- Git: sistema de controle de versão distribuído usado para registrar o histórico de alterações e organizar branches.
- Monorepo: repositório que reúne vários projetos ou pacotes de código em um único lugar.
- Open-source: modelo de disponibilização de código-fonte sob uma licença que define as condições de uso e distribuição.
- Pando: backend interno de controle de código-fonte da OpenAI para engenheiros e agentes, mencionado no trabalho de escalar Git.
- Realce de sintaxe: recurso que identifica elementos da linguagem de programação e aplica cores para facilitar a leitura.
- Streaming: recebimento de conteúdo em partes, conforme ele é produzido, sem esperar a entrega completa de uma vez.
- Trees: biblioteca open-source da Pierre para navegar pelos arquivos de um projeto.
- Diffs: biblioteca open-source da Pierre para visualizar diferenças e renderizar código, com modo de edição para revisores.
- Highlights: realçador de sintaxe open-source da Pierre que acompanha a digitação ou o streaming de código.

Fonte: <https://openai.com/index/openai-to-acquire-pierre/>

## Para onde ir depois

O próximo passo depende do seu papel. Clientes do Code Storage podem revisar como o serviço é usado em seus aplicativos. Quem desenvolve no Codex pode praticar a navegação e a revisão com Trees e Diffs. Contribuidores podem estudar o monorepo da Pierre e trabalhar com os projetos sob a licença Apache-2.0.

Para fixar os conceitos, explique com suas próprias palavras a diferença entre armazenar código, registrar seu histórico, navegar por arquivos e revisar alterações. Esse exercício ajuda a entender por que a aquisição reúne ferramentas que resolvem problemas diferentes dentro do mesmo fluxo de desenvolvimento.

- Clientes do Code Storage: revise onde o armazenamento e o histórico baseados em Git aparecem no seu aplicativo e mantenha esse fluxo no serviço.
- Quem usa o Codex: pratique localizar arquivos e interpretar alterações no aplicativo para reconhecer as funções de Trees e Diffs.
- Contribuidores open-source: leia o repositório https://github.com/pierrecomputer/pierre e identifique os projetos e a licença antes de contribuir.
- Quem acompanha a notícia: use o anúncio oficial da OpenAI para separar o que já existe no Codex do que depende do fechamento da aquisição.

Fonte: <https://openai.com/index/openai-to-acquire-pierre/>

## Links citados

- https://github.com/openai/codex
- https://pierre.computer
