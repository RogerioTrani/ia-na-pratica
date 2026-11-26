# Gemini Notebook cria skills para ChatGPT, Gemini e Claude

_2026-11-22 · noticia_

Você vai aprender a usar o Gemini Notebook para transformar documentações oficiais em skills reutilizáveis no ChatGPT, no Gemini e no Claude. A apostila explica como montar as fontes, orientar a geração do arquivo SKILL.md, instalar a habilidade e testar o resultado. Você verá exemplos com miniatura de vídeo, análise de contratos em PDF e planilha com dashboard. Também saberá quais cuidados tomar antes de reutilizar uma skill em outra plataforma.

## O fato

O teste usa o Gemini Notebook, antigo NotebookLM, como uma mesa de trabalho para produzir skills. O caderno recebe as páginas oficiais de skills do ChatGPT, do Gemini e do Claude. Em Configurar bate-papo > Personalizar, um prompt orienta a leitura dessas fontes e pede a geração do arquivo SKILL.md, com metadados YAML e instruções prontas para uso.

O arquivo gerado pode ser instalado em plataformas que aceitam skills. No teste, a habilidade Criador de thumbnail foi criada no ChatGPT e usada com uma foto e a legenda de um vídeo. O mesmo fluxo apareceu na análise de contratos no Gemini e na criação de uma planilha no Claude. O resultado depende da qualidade das fontes, das instruções e da revisão de quem usa a habilidade.

## O que é uma skill e por que isso importa

Uma skill reúne instruções para executar uma tarefa específica. Ela funciona como um procedimento que a inteligência artificial consulta quando você a aciona. Em vez de explicar novamente o contexto, o formato de saída e as etapas a cada conversa, você concentra essas orientações em um único conjunto reutilizável.

Isso ajuda em trabalhos repetitivos, como montar miniaturas, organizar relatórios ou estruturar planilhas. A skill mantém o critério da tarefa mais estável e deixa o pedido de cada execução mais curto. Ela também pode ser baixada ou copiada para outra plataforma compatível. O arquivo transporta as instruções; cada plataforma precisa aceitar e ativar essa habilidade para que o fluxo funcione.

- Contexto: a skill explica qual tarefa deve orientar e quando deve ser usada.
- Procedimento: as instruções descrevem as etapas e os cuidados do trabalho.
- Saída: o resultado esperado fica definido para reduzir respostas soltas ou incompletas.

Fonte: <https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview>

## Como montar o Gemini Notebook

O primeiro passo é criar um caderno dedicado à produção de skills. No Gemini Notebook, escolha um novo notebook e dê a ele um nome que identifique a função, como fábrica de skills. Depois, reúna as documentações oficiais das plataformas nas quais pretende usar as habilidades.

O teste carregou três páginas: a documentação de skills do ChatGPT, a de Habilidades do Gemini e a de Agent Skills do Claude. Elas entram em Adicionar fontes > Sites. Ter as três no mesmo caderno permite que o prompt compare padrões de criação, instalação e uso. O Notebook usa essas páginas como referência para montar a skill.

- Abra o Gemini Notebook e crie um novo notebook; o resultado será um caderno vazio pronto para receber fontes.
- Renomeie o caderno; um nome como fábrica de skills ajudará a localizar esse espaço depois.
- Em Adicionar fontes > Sites, inclua as páginas oficiais de skills do ChatGPT, do Gemini e do Claude; as três documentações deverão aparecer como fontes do caderno.
- Abra o menu de três pontos e entre em Configurar bate-papo > Personalizar; você chegará ao campo onde o prompt de produção será salvo.

## Como orientar o Notebook com um prompt

O prompt funciona como um briefing para o Notebook. Ele define o papel do assistente, quais informações você fornecerá em cada pedido e como a resposta deve ser organizada. No fluxo apresentado, cada solicitação de skill informa a plataforma de destino e a tarefa repetitiva que se quer automatizar.

O prompt também limita a pesquisa às documentações oficiais adicionadas como fontes e pede que a skill siga os padrões dessas páginas. A entrega inclui análise técnica, skill completa, instruções de instalação e configuração, sugestões de teste prático e a indicação das partes das fontes usadas. Assim, você recebe o material para instalar e verificar a habilidade, além de rastrear a origem das regras.

- Informe a plataforma de destino, como ChatGPT, Gemini, Claude ou outra que aceite skills.
- Descreva a tarefa repetitiva e o resultado esperado com frases específicas.
- Peça que o Notebook consulte somente as fontes oficiais do caderno.
- Solicite o arquivo SKILL.md completo, com metadados e instruções passo a passo.
- Peça as orientações de instalação, configuração e teste prático.
- Exija a indicação das partes das documentações usadas para montar a skill.

## A anatomia do SKILL.md

O SKILL.md é o arquivo de texto que reúne os metadados e as instruções da habilidade. Os metadados ficam em YAML e incluem name e description. O name identifica a skill; no formato exigido pelo fluxo apresentado, ele usa letras minúsculas e hifens. A description explica o que a habilidade faz e ajuda a reconhecer quando usá-la.

O restante do arquivo orienta a execução da tarefa. Ele pode definir etapas, formato de saída, referências ao documento e critérios de teste. Antes de instalar, leia o conteúdo gerado e confira se ele corresponde ao pedido. Um arquivo bem formatado ainda precisa passar por um teste real na plataforma escolhida.

- name: use letras minúsculas e hifens, como em criador-de-thumbnail.
- description: descreva a função da skill de forma clara e específica.
- Instruções: organize a tarefa em passos que a inteligência artificial consiga seguir.
- Formato de saída: defina como o relatório, a miniatura ou a planilha deverá ser apresentado.
- Referências: peça que a skill indique as partes das fontes usadas quando essa rastreabilidade for necessária.

Fonte: <https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview>

## Exemplo: skill de análise de contratos

O primeiro pedido do teste foi uma skill para o Gemini que lesse contratos em PDF e produzisse um relatório estruturado. A solicitação definiu o que deveria ser procurado: cláusulas importantes, prazos, obrigações, riscos e possíveis inconsistências. Também pediu referências ao documento, para que cada achado pudesse ser relacionado ao contrato original.

No teste, um contrato de venda de carro foi enviado ao Gemini com a skill ativa. O relatório organizou cláusulas abusivas, prazos, obrigações, matriz de risco, rescisões, penalidades, inconsistências e dúvidas. A habilidade reuniu e classificou as informações; a decisão sobre o significado jurídico de cada trecho continua exigindo revisão humana.

```
quero a skill que analise contratos em PDF, identifique cláusulas importantes, prazos, obrigações, riscos e possíveis inconsistências, produzindo um relatório estruturado com referência do documento.
```

Fonte: <https://support.google.com/gemini/answer/17094296>

## Como instalar e testar a skill no Gemini

O Gemini aceita a criação manual da habilidade e o upload de um arquivo compactado. Na criação manual, você copia o nome, a descrição e as instruções produzidas pelo Notebook. Para transferir uma skill, entre em Habilidades, clique em Criar e depois em Upload para enviar o arquivo zip.

1. Abra Configurações > Habilidades; o resultado será a lista das habilidades disponíveis na conta.
2. Para criar manualmente, selecione Criar manualmente, preencha nome, descrição e instrução com o conteúdo do SKILL.md e clique em Criar; a skill deverá aparecer na lista.
3. Para importar um arquivo, escolha Criar > Upload e envie o zip; a habilidade importada deverá ficar disponível em Habilidades.
4. Abra o menu de três pontos da skill e escolha Usar, ou, em uma conversa, digite @ e selecione a habilidade; o resultado será a ativação da skill na conversa.
5. Anexe o contrato em PDF e envie; o resultado esperado será um relatório com cláusulas, prazos, obrigações, riscos e referências ao documento.

Fonte: <https://support.google.com/gemini/answer/17094296>

## Skill de thumbnail no ChatGPT

A habilidade de miniatura foi criada no ChatGPT usando o editor de skills. O caminho confirmado pela documentação é Plugins > Skills > Create > Create with editor. Na interface em português usada no teste, o acesso aparece como Plugins > Habilidades, seguido da opção de criar com o editor.

1. Abra Plugins > Habilidades no ChatGPT; o resultado será a área de gerenciamento das habilidades.
2. Escolha criar com o editor; serão exibidos os campos de nome, descrição e instrução.
3. Use Criador de thumbnail como nome e cole a descrição e as instruções geradas pelo Gemini Notebook.
4. Conclua a criação; a mensagem de salvamento indicará que a habilidade ficou disponível.

Fonte: <https://help.openai.com/en/articles/20001066-skills-in-chatgpt>

## Como pedir a miniatura e ajustar o resultado

Depois de salvar a skill, abra uma conversa nova no ChatGPT e digite /. Selecione Criador de thumbnail na lista. Anexe uma foto e a legenda do vídeo. No teste, esses dois elementos foram suficientes para começar, sem um texto adicional explicando a tarefa.

A foto forneceu a base visual e a legenda informou o tema da composição. A primeira miniatura foi gerada com esse contexto. Um novo pedido pediu outra estrutura e produziu uma segunda versão, mantendo a qualidade da foto no exemplo apresentado. Você também pode pedir mudanças de cor ou de fundo e avaliar qual versão comunica melhor o assunto do vídeo.

- A foto escolhida deve continuar nítida na composição gerada.
- A estrutura da miniatura deve valorizar o assunto indicado na legenda.
- Uma segunda versão deve ser comparada com a primeira antes de escolher.
- Pedidos de ajuste podem mudar a estrutura, a cor ou o fundo sem exigir a recriação da skill.

Fonte: <https://help.openai.com/en/articles/20001066-skills-in-chatgpt>

## Como levar uma skill para outra IA

Uma skill criada em uma plataforma pode ser exportada quando a interface oferece a opção de baixar. No ChatGPT, o download é feito pelo menu de três pontos da habilidade. No Gemini, a importação é feita em Habilidades > Criar > Upload, com o envio do arquivo zip.

No teste, a skill de análise de contratos, criada para o Gemini e baixada, foi levada ao Claude pelo caminho Personalização > Skills, que oferece upload ou criação manual. Ela também foi carregada no ChatGPT, pela opção de carregar do computador. Ao trocar de plataforma, mantenha o name do SKILL.md em letras minúsculas e separado por hifens. Depois da importação, repita um teste para confirmar que a habilidade foi ativada e produziu a saída esperada.

1. No ChatGPT, abra o menu de três pontos da skill e escolha baixar; o resultado será o arquivo compactado da habilidade.
2. No Gemini, abra Habilidades, clique em Criar e depois em Upload; envie o zip para disponibilizar a skill.
3. No Claude, entre em Personalização > Skills e use a opção de upload para trazer o arquivo exportado.
4. Confira o name dentro do SKILL.md antes de subir no Gemini; ele deve estar em minúsculas e com hifens.
5. Abra uma conversa na plataforma de destino e repita o teste com o conteúdo adequado à tarefa.

Fonte: <https://support.google.com/gemini/answer/17094296>

## Exemplo: planilha com dashboard no Claude

Outro exemplo pediu ao Gemini Notebook uma skill para o Claude que criasse planilhas inteligentes com dashboards para análise de dados de uma empresa de produtos agrícolas. A skill foi instalada em Personalização > Skills, em Criar, com nome, instruções e formato de saída definidos pelo arquivo gerado.

Na área de experimentar a habilidade, o pedido foi elaborar um modelo em Excel para acompanhar a produtividade da colheita, os custos e os insumos da fazenda na temporada. O resultado apresentado tinha gráficos, área de análise, colheita, insumos e configurações, além da possibilidade de baixar a planilha. A skill estruturou o trabalho; os dados e as decisões inseridos na planilha ainda precisam ser conferidos por quem vai usá-la.

```
elabore um modelo em Excel para acompanhar a produtividade da colheita e os custos e insumos da minha fazenda nesta temporada
```

Fonte: <https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview>

## Os números do teste

Os exemplos mostram a composição do fluxo e os resultados observados. Eles servem para explicar o processo, sem representar uma medida geral de velocidade, qualidade ou capacidade de automação.

- Três documentações oficiais foram carregadas no Notebook: ChatGPT, Gemini e Claude. Esse conjunto orientou a criação das skills e não indica um limite de fontes.
- Duas versões de miniatura foram mostradas: a primeira composição e uma segunda estrutura pedida depois. O exemplo demonstra ajuste por conversa, sem estabelecer uma nota de qualidade.
- Um contrato em PDF foi usado no teste com a skill de análise. O relatório reuniu vários tipos de achado, mas um documento não valida o desempenho da habilidade em todos os contratos.
- Uma planilha foi gerada no Claude para o exemplo agrícola. O resultado teve gráficos e áreas de acompanhamento, sem servir como referência de tempo ou produtividade.

## O que muda para você

Quem produz vídeo pode transformar a criação de miniaturas em um processo mais curto. A skill guarda o critério de composição e a forma de usar a foto e a legenda. Em cada novo vídeo, resta escolher os materiais, acionar a habilidade e revisar o resultado.

Exemplo: um criador de conteúdo mantém uma foto recorrente e recebe a legenda de um novo vídeo. Ele abre uma conversa, seleciona Criador de thumbnail e envia os dois elementos. Depois compara a primeira versão com um ajuste de estrutura. O ganho está em reutilizar o procedimento já definido, mantendo a decisão visual com o autor.

## O que fazer hoje

Comece por uma tarefa que você já repete e cujo resultado consiga conferir. O caminho abaixo reúne as etapas usadas nos exemplos, da criação do caderno ao teste da skill.

1. Escolha a tarefa repetitiva, a plataforma de destino e o formato de saída desejado; o resultado será um pedido específico para orientar a geração.
2. Crie um notebook no Gemini Notebook e adicione as documentações oficiais das plataformas envolvidas; as fontes deverão aparecer no caderno.
3. Configure o prompt em Configurar bate-papo > Personalizar, definindo fontes permitidas, conteúdo da entrega e necessidade de referências; salve as instruções.
4. Envie o pedido da skill e aguarde a análise técnica e o arquivo SKILL.md; você deverá receber metadados, instruções, orientação de instalação e sugestões de teste.
5. Leia o arquivo e confira name, description, passos, formato de saída e partes das fontes utilizadas.
6. Instale a skill na plataforma escolhida, por criação manual ou upload, conforme a opção disponível.
7. Execute um teste com material real e verifique se o resultado corresponde ao pedido.
8. Baixe ou preserve a skill aprovada para reutilizá-la nas próximas execuções.

## O que conferir

Antes de depender da skill, confirme se a conta e a plataforma oferecem o recurso. No ChatGPT, Skills estão disponíveis para os planos Business, Enterprise, Healthcare e Edu e podem não aparecer em contas pessoais. A interface também pode mudar o rótulo dos menus, então identifique a área de habilidades antes de procurar o caminho exato.

- Planos do ChatGPT: verifique se a sua conta tem acesso a Skills antes de iniciar a criação.
- Compatibilidade: confirme se a plataforma de destino aceita a skill e oferece criação manual ou upload.
- Nome do arquivo: para subir no Gemini, o campo name dentro do SKILL.md precisa estar em letras minúsculas e separado por hifens, como criador-de-thumbnail.
- Fontes: use as documentações oficiais adicionadas ao Notebook e confira quais trechos sustentaram as instruções.
- Ativação: selecione a skill na conversa antes de enviar a foto, o PDF ou o pedido de planilha.
- Miniaturas: compare nitidez da foto, composição e relação com a legenda antes de escolher a versão final.
- Contratos: revise o relatório e os trechos indicados antes de tomar qualquer decisão com base na análise.
- Planilhas: confira os gráficos, as abas e os dados antes de usar o arquivo no trabalho.
- Portabilidade: repita o teste depois de importar a skill, pois cada plataforma precisa carregar e executar as instruções.

Fonte: <https://help.openai.com/en/articles/20001066-skills-in-chatgpt>

## Glossário

- Skill: conjunto reutilizável de instruções para orientar uma tarefa específica.
- SKILL.md: arquivo de texto que reúne metadados e instruções de uma skill.
- YAML: formato de organização dos metadados no início do arquivo.
- Metadados: informações que identificam e descrevem a skill, como name e description.
- Name: campo que define o nome da skill; no formato deste fluxo, usa minúsculas e hifens.
- Description: campo que explica o que a habilidade faz.
- Prompt: conjunto de instruções que orienta a inteligência artificial a realizar um pedido.
- Gemini Notebook: novo nome da ferramenta antes chamada NotebookLM.
- Notebook: caderno que reúne fontes e instruções para um trabalho específico.
- Upload: envio de um arquivo do computador para uma plataforma.
- Arquivo zip: arquivo compactado usado para transportar a skill entre plataformas.
- Barra (/): atalho usado no ChatGPT para abrir a lista de skills em uma conversa nova.
- Arroba (@): atalho usado no Gemini para selecionar uma habilidade na conversa.
- Thumbnail ou miniatura: imagem de apresentação usada para representar um vídeo.
- Dashboard: painel que reúne indicadores e gráficos para acompanhar um conjunto de dados.
- PDF: formato de documento usado no exemplo de análise de contratos.

## Para onde ir depois

O próximo passo é testar uma skill com uma tarefa sua. Escolha um trabalho repetitivo, reúna a documentação oficial necessária e produza a primeira versão do SKILL.md. Use o resultado para descobrir onde as instruções ficaram vagas ou onde a saída precisa de mais detalhes.

- Pratique com a skill de thumbnail usando uma foto e a legenda de um vídeo real.
- Pratique com a análise de contratos e confira se o relatório permite localizar cada achado no PDF.
- Pratique com a planilha com dashboard e revise os gráficos e as áreas de acompanhamento.
- Depois do teste, ajuste a descrição ou as instruções e salve a versão que funcionar para reutilizar.

## Links citados

- https://notebook.google.com/

## Além do vídeo

- Skills para criar receitas na cozinha.
- Skills para criar carrosséis no Instagram.
- Skills para escrever roteiros de vídeo no YouTube.
- Skills para analisar a captação de clientes.
- Gerenciamento das skills nas plataformas, com opções como editar, desativar, desinstalar ou excluir.
