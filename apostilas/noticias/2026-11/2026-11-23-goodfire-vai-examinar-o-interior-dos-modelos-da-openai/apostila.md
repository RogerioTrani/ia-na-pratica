# Goodfire vai examinar o interior dos modelos da OpenAI

_2026-11-23 · noticia_

A OpenAI firmou acordos com quatro avaliadores independentes para examinar alinhamento, salvaguardas e monitoramento de seus modelos com acesso interno. Apollo Research, METR, Transluce e Goodfire têm escopos diferentes, que vão da subversão durante o treinamento à qualidade dos testes e à análise dos internos dos modelos. Ao ler esta apostila, você vai entender o que cada avaliação pretende verificar, como o acesso e a supervisão funcionam e quais limites devem ser considerados antes de tirar conclusões dos relatórios.

## O fato

Em 16 de novembro de 2026, a OpenAI anunciou acordos com quatro avaliadores independentes: Apollo Research, METR, Transluce e Goodfire. Eles fazem parte da primeira fase de avaliações incorporadas da empresa, com acesso a modelos, dados e sistemas internos conforme a necessidade de cada trabalho.

O foco inicial é o alinhamento e as salvaguardas de modelos durante o treinamento e o uso interno. Cada avaliador examina uma parte diferente desse problema. O anúncio apresenta os escopos e as condições de acesso, ainda sem resultados das avaliações.

Fonte: <https://openai.com/news/our-first-phase-of-embedded-assessments/>

## Por que isso importa

Uma avaliação externa costuma depender do que a empresa disponibiliza. A avaliação incorporada vai além: o avaliador recebe acesso profundo a recursos internos durante um período prolongado. Isso permite examinar evidências que não aparecem em demonstrações públicas ou testes superficiais.

A proposta é obter sinais independentes sobre riscos e sobre a eficácia dos controles usados para reduzi-los. Os relatórios públicos podem mostrar ao público como a OpenAI avalia e gerencia esses riscos, incluindo os limites de cada investigação. Relatórios confidenciais mais detalhados fornecem evidências aos órgãos de supervisão.

Essas avaliações complementam os casos de segurança, documentos que organizam alegações, evidências e controles. Elas não substituem o trabalho interno de segurança. A função delas é acrescentar uma perspectiva externa e ajudar a identificar falhas que a própria empresa talvez não tenha previsto.

Fonte: <https://openai.com/news/our-first-phase-of-embedded-assessments/>

## O que é uma avaliação incorporada

Uma avaliação incorporada é uma investigação independente conduzida com acesso a modelos e sistemas internos de uma empresa. Dependendo do escopo, o avaliador pode receber checkpoints, código-fonte, dados de treinamento e avaliação, sistemas de monitoramento, documentação técnica e conversas com os responsáveis pelo trabalho.

Cada engajamento começa com um escopo acordado, acompanhado das condições de acesso, dos recursos e dos arranjos de segurança. Alguns trabalhos testam afirmações específicas. Outros permitem que o avaliador procure modos de falha inesperados dentro de um sistema ou de uma execução de treinamento definida.

A independência não exige que o avaliador siga um roteiro fixo. Os protocolos preveem liberdade para acompanhar as evidências, refinar métodos e propor avaliações adicionais quando os achados justificarem. Também existe um processo para tratar novos pedidos de acesso.

Fonte: <https://openai.com/news/our-first-phase-of-embedded-assessments/>

## Apollo Research: quatro afirmações sobre subversão

A Apollo Research vai examinar se modelos poderiam trabalhar secretamente contra as intenções de seus desenvolvedores e se as salvaguardas detectariam esse comportamento. A investigação usa evidências do treinamento, de testes de segurança e do uso interno.

As quatro afirmações serão avaliadas em duas etapas. Na primeira, a OpenAI fornece modelos públicos e não lançados selecionados, checkpoints de treinamento, dados e resultados de avaliação, registros de intervenções no treinamento, sistemas de monitoramento, comportamentos sinalizados e pesquisadores que dão contexto. A Apollo também recebe ferramentas e capacidade computacional para realizar testes independentes. O anúncio não detalha o que acontece na segunda etapa.

Cada afirmação cobre uma frente diferente. O treinamento pode criar incentivos para subversão; um teste pode deixar de provocar esse comportamento; o uso interno pode registrar tentativas; e o raciocínio que levaria à subversão pode ou não ser detectável. Separar essas questões evita tratar um único resultado como prova de segurança geral.

- O treinamento não incentivou subversão.
- Avaliações rigorosas e exercícios de red teaming não provocam subversão.
- Os modelos não tentaram agir de forma subversiva durante o uso interno.
- O raciocínio por trás da subversão seria detectável.

Fonte: <https://openai.com/news/apollo-research-pilot-assessment/>

## METR: alinhamento e monitoramento

A METR pretende realizar duas avaliações. A primeira examina comportamento desalinhado na maior execução de aprendizado por reforço, ou RL, de fronteira da OpenAI até a data do anúncio. O objetivo inclui encontrar falhas que os testes e monitores existentes possam ter deixado passar.

Dentro da execução selecionada e das condições acordadas de acesso, recursos e segurança, a METR define as prioridades da avaliação. Ela pode iterar sobre buscas, análises e experimentos de elicitação. O acesso inclui checkpoints relevantes, rollouts de treinamento e avaliação e registros de monitoramento de desalinhamento dessa execução.

O escopo dessa primeira fase é menos amplo do que a proposta de avaliação de alinhamento da METR, que prevê um levantamento amplo de desalinhamento. O recorte anunciado deve ser mantido ao interpretar qualquer conclusão: um resultado dentro dessa execução não cobre automaticamente todos os modelos e situações de uso.

A segunda avaliação seria dedicada aos monitores. A OpenAI e a METR concordaram preliminarmente em realizá-la, e a OpenAI pretende que ela seja mais ampla que o exercício anterior, mas a execução ainda depende de acordo mútuo sobre o escopo. Por isso, ela deve ser tratada como plano, não como avaliação concluída.

Fonte: <https://openai.com/news/metr-assessment/>

## Transluce: a qualidade das avaliações de alinhamento

A Transluce vai examinar as avaliações de alinhamento pós-treino da própria OpenAI. A pergunta central é se esses testes medem bem o que propõem e se cobrem o que importa. Qualidade refere-se à capacidade de produzir evidências confiáveis; cobertura refere-se aos comportamentos e riscos incluídos na análise.

Para a avaliação inicial, a Transluce recebe modelos públicos e não lançados selecionados, as avaliações de alinhamento pós-treino e resultados relevantes, dados de comportamento do modelo, documentação dos casos de segurança e pesquisadores que fornecem contexto. Também recebe ferramentas e capacidade computacional para testes independentes.

As duas organizações compartilham a intenção de fazer um acompanhamento de cerca de oito semanas no início de 2027. Esse trabalho teria acesso mais amplo a modelos adicionais, acesso mais profundo às avaliações de alinhamento e informações sobre como os resultados influenciam decisões de lançamento. A intenção e a duração estão anunciadas; a realização depende da continuidade do trabalho.

Fonte: <https://openai.com/news/transluce-assessment/>

## Goodfire: analisar os internos dos modelos

A Goodfire vai incorporar pesquisadores de interpretabilidade e usar sua plataforma para analisar os internos dos modelos. Interpretabilidade é o esforço para entender mecanismos internos que ajudam a explicar o comportamento do modelo. Essa perspectiva complementa testes que observam apenas entradas e saídas.

O objetivo principal é monitorar, depurar e alinhar execuções de treinamento. O público principal dos resultados são os pesquisadores internos da OpenAI, que usarão os achados para melhorar a segurança. A Goodfire também publicará aprendizados e descobertas ao longo da colaboração.

Há uma diferença prática entre esse trabalho e uma auditoria voltada apenas ao público. Parte do valor esperado chega primeiro às equipes internas, sob a forma de diagnóstico e orientação para melhorias. A publicação progressiva permite acompanhar o que foi aprendido, mas o anúncio não promete divulgar todos os detalhes internos.

Fonte: <https://openai.com/news/goodfire-platform-assessment/>

## Acesso, segurança e escopo

O acesso profundo precisa conciliar evidência suficiente com proteção de informações sensíveis. Quando um avaliador precisa trabalhar com dados confidenciais, o previsto é que ele atue nas dependências da OpenAI, usando dispositivos fornecidos pela empresa. Essa medida tem como objetivo proteger a segurança das informações acessadas.

No local, os avaliadores podem contar com equipes dedicadas para entender permissões e obter contexto. Espera-se que sigam, no mínimo, os mesmos padrões de segurança dos funcionários da OpenAI. Alguns experimentos podem exigir padrões mais rigorosos, conforme as condições de segurança.

Nem todo recurso sensível precisa ser acessado diretamente. Quando o acesso direto pudesse expor propriedade intelectual especialmente sensível, como pesos ou arquitetura do modelo, a OpenAI considera alternativas. Uma delas é juntar avaliadores e pesquisadores da OpenAI para executar análises sem entregar o ativo sensível ao avaliador.

Fonte: <https://openai.com/news/our-first-phase-of-embedded-assessments/>

## Quem fiscaliza e como divergências são tratadas

O Safety and Security Committee (SSC) é um comitê independente de supervisão ligado ao conselho da OpenAI Foundation. Ele terá visibilidade das avaliações incorporadas antes, durante e ao final delas, além de receber relatórios sem redações. O SSC e os avaliadores poderão conversar durante o trabalho, inclusive em particular.

Divergências entre a OpenAI e um avaliador serão encaminhadas ao Safety Advisory Group e à direção executiva da OpenAI, que terão um período especificado para resolvê-las. O SSC será avisado prontamente quando a divergência for escalada. Se ela permanecer, a decisão será encaminhada ao SSC.

Fonte: <https://openai.com/news/our-first-phase-of-embedded-assessments/>

## Conversas, conflitos e independência

As conversas com funcionários ajudam os avaliadores a entender informações internas e o contexto do trabalho. A OpenAI autoriza e orienta quem pode falar com eles. Por privacidade, essas discussões são off the record: podem informar a avaliação, mas não podem ser publicadas nem atribuídas a funcionários.

Existe um caminho separado de atestado. O avaliador pode pedir uma declaração atestada pela OpenAI para verificar, corrigir ou esclarecer algo aprendido nas conversas. A declaração não leva o nome de uma pessoa. O avaliador pode publicá-la ou informar que a OpenAI se recusou a atestá-la.

A remuneração também é divulgada. Apollo Research e Goodfire recebem pagamento, cujo valor não depende dos resultados. METR e Transluce não recebem pagamento financeiro pelas avaliações, mas podem aceitar créditos de API ou capacidade computacional. Os protocolos incluem ainda processos para conflitos de interesse, pedidos de afastamento e um breve período de espera antes de um participante se incorporar a outro desenvolvedor de IA.

Fonte: <https://openai.com/news/our-first-phase-of-embedded-assessments/>

## Publicação dos resultados e limites

Os avaliadores mantêm independência para publicar suas avaliações. A OpenAI reserva o direito de retirar informações confidenciais e pode pedir prazos de divulgação responsável para agir sobre riscos de segurança ou corrigir problemas. Os relatórios públicos devem apresentar achados e limitações; versões confidenciais mais detalhadas ficam com os órgãos de supervisão.

A própria OpenAI prevê desafios técnicos de acesso, restrições de espaço, mudanças nos protocolos de segurança e outros problemas inesperados. Os procedimentos para avaliações incorporadas ainda não estão padronizados no setor e devem evoluir com a experiência.

Para interpretar um relatório, é necessário olhar o escopo, os métodos, o acesso efetivamente obtido e as restrições de publicação. Redações e atrasos podem limitar o que o público consegue verificar. O anúncio desta primeira fase descreve planos e condições de trabalho, não conclusões de segurança.

Fonte: <https://openai.com/news/our-first-phase-of-embedded-assessments/>

## Os números

- 16 de novembro de 2026 é a data do anúncio da primeira fase. Ela não representa a data de conclusão das avaliações.
- Quatro avaliadores independentes participam desta fase. Esse número mostra a divisão do trabalho entre especialidades diferentes e não indica que quatro conclusões já estejam disponíveis.
- Duas etapas organizam a avaliação da Apollo Research. O anúncio detalha apenas os acessos da primeira e não informa a duração de nenhuma delas.
- Quatro afirmações são examinadas pela Apollo Research. Elas cobrem treinamento, testes, uso interno e detectabilidade do raciocínio, sem formar uma única medida geral de segurança.
- Duas avaliações são pretendidas com a METR. A primeira trata de alinhamento em uma execução de RL; a segunda trata de monitores e ainda depende de acordo sobre o escopo.
- Cerca de oito semanas é a duração prevista para o acompanhamento da Transluce no início de 2027. É uma estimativa de trabalho futuro, não um resultado nem a duração da avaliação inicial.
- Três semanas foi a duração de um exercício anterior de red teaming de monitores com a METR. Esse trabalho passado não define a duração da nova avaliação de monitores.

Fonte: <https://openai.com/news/our-first-phase-of-embedded-assessments/>

## O que muda para você

Para quem acompanha IA, a mudança está na possibilidade de examinar evidências independentes sobre segurança. Os quatro avaliadores olham para pontos distintos: comportamento subversivo, desalinhamento em treinamento, qualidade dos testes e mecanismos internos. Ler os relatórios com esses recortes separados ajuda a entender o que cada conclusão cobre.

Exemplo: imagine que um avaliador encontre, nos checkpoints de uma execução de treinamento, um comportamento que os testes atuais não sinalizaram. Esse achado mostraria por que acesso a registros internos e liberdade para refinar a busca podem acrescentar evidências. Ainda assim, seria necessário verificar o escopo do experimento antes de aplicar a conclusão a outros modelos.

Nem todo detalhe terá o mesmo nível de exposição pública. Os achados da Goodfire têm como público principal os pesquisadores internos, e a OpenAI pode retirar informações confidenciais dos relatórios públicos. O leitor deve distinguir o que foi efetivamente testado do que permanece como plano ou informação confidencial.

Fonte: <https://openai.com/news/our-first-phase-of-embedded-assessments/>

## O que fazer hoje

Use o anúncio e as páginas das avaliações como mapa. O objetivo é acompanhar os trabalhos sem confundir escopo, intenção e resultado.

1. Abra o anúncio da OpenAI e identifique o objetivo comum e os quatro avaliadores. O resultado esperado é uma lista clara de quem examina o quê.
2. Leia a página de cada avaliador e separe objetivo, recursos acessíveis e condições do trabalho. O resultado esperado é conseguir explicar a diferença entre Apollo Research, METR, Transluce e Goodfire sem misturar os recortes.
3. Acompanhe os relatórios públicos e compare afirmação testada, método, evidência e limitações. O resultado esperado é conseguir verificar se a conclusão corresponde ao escopo realizado.
4. Marque os trabalhos ainda condicionados, especialmente a segunda avaliação da METR e o acompanhamento da Transluce. O resultado esperado é não tratá-los como concluídos antes do anúncio de execução.
5. Para praticar, escolha uma das quatro afirmações da Apollo Research e liste as evidências necessárias para testá-la. O resultado esperado é transformar uma frase ampla em uma pergunta verificável.

Fonte: <https://openai.com/news/our-first-phase-of-embedded-assessments/>

## O que conferir

Os relatórios terão valor diferente conforme o acesso, o método e o recorte. Estes pontos ajudam a separar evidência de promessa.

- Confira o escopo antes de generalizar. A primeira fase da METR é menos abrangente do que a proposta ampla de levantamento de desalinhamento citada no anúncio.
- Separe intenção de execução. O acompanhamento da Transluce e a segunda avaliação da METR ainda dependem de continuidade ou de acordo mútuo.
- Verifique quais modelos, checkpoints, dados e registros estavam disponíveis. Uma limitação de acesso altera o alcance do que pode ser concluído.
- Examine qualidade e cobertura dos testes. A Transluce avalia justamente se as avaliações de alinhamento medem bem e cobrem o necessário.
- Considere os incentivos e salvaguardas de independência. O anúncio divulga remuneração, créditos de computação, conflitos de interesse e períodos de espera.
- Leia as limitações de publicação. Redações de confidencialidade e prazos de divulgação responsável podem reduzir o detalhe disponível ao público.
- Não conclua que um modelo é seguro ou inseguro apenas pelo anúncio dos trabalhos. A primeira fase apresenta escopos e protocolos; as conclusões dependem dos relatórios.

Fonte: <https://openai.com/news/our-first-phase-of-embedded-assessments/>

## Glossário

- Alinhamento: comportamento do modelo compatível com as intenções dos desenvolvedores e com as expectativas de segurança.
- Avaliação incorporada: investigação independente com acesso profundo a modelos e sistemas internos durante um período prolongado.
- Caso de segurança: documento que organiza alegações de segurança, evidências e controles usados para sustentá-las.
- Checkpoint: estado salvo do modelo em um ponto do treinamento, usado para análise ou continuação do trabalho.
- Aprendizado por reforço (RL): método de treinamento em que o modelo aprende a partir de recompensas ou penalidades.
- Rollout: sequência de ações ou saídas gerada pelo modelo durante treinamento ou avaliação.
- Elicitação: experimento destinado a provocar um comportamento para observá-lo e testá-lo.
- Red teaming: teste adversarial que procura falhas, comportamentos indesejados ou limites de segurança.
- Subversão: trabalho encoberto de um modelo contra as intenções de seus desenvolvedores.
- Interpretabilidade: esforço para entender mecanismos internos que explicam o comportamento de um modelo.
- Monitor: sistema ou processo que observa sinais de comportamento, incluindo possíveis sinais de desalinhamento.
- Pós-treino: etapa posterior ao treinamento principal, na qual são feitas avaliações e ajustes de alinhamento.
- Salvaguarda: controle usado para detectar, impedir ou reduzir um comportamento de risco.
- Safety and Security Committee (SSC): comitê independente de supervisão ligado ao conselho da OpenAI Foundation.

Fonte: <https://openai.com/news/our-first-phase-of-embedded-assessments/>

## Para onde ir depois

O próximo passo é acompanhar a passagem dos escopos anunciados para relatórios com métodos, achados e limitações. Pratique a leitura crítica usando as quatro afirmações da Apollo Research como referência.

- Leia o anúncio principal e as páginas específicas de Apollo Research, METR, Transluce e Goodfire para manter os recortes separados.
- Quando os relatórios públicos forem divulgados, compare o que foi prometido com o que foi efetivamente acessado e testado.
- Verifique se o acompanhamento da Transluce e a segunda avaliação da METR saem da intenção e passam a ter escopo acordado.
- Aplique o glossário ao ler os relatórios e anote quais termos técnicos mudam a interpretação de uma conclusão.

Fonte: <https://openai.com/news/our-first-phase-of-embedded-assessments/>

## Além do vídeo

- A colaboração também apoia compromissos assumidos no White House Accord on Super Intelligence.
- O trabalho se apoia em avaliações anteriores de terceiros, incluindo uma investigação do incidente do Hugging Face.
- A expectativa é contribuir para padrões compartilhados de avaliação independente e transparência pública no setor.
- A OpenAI explora avaliações incorporadas futuras sobre conformidade com seus frameworks de segurança e sobre cultura e processos organizacionais.
