# Goodfire vai examinar o interior dos modelos da OpenAI

_2026-11-23 · noticia_

A OpenAI fechou acordos com quatro avaliadores independentes (Apollo Research, METR, Transluce e Goodfire) para uma primeira fase de avaliações embutidas. Cada um examina uma parte diferente: subversão, o interior dos modelos, as avaliações de alinhamento pós-treino e a maior execução por reforço da empresa. Os relatórios públicos devem trazer os achados e limites de cada trabalho.

## O fato

A OpenAI fechou acordos com quatro avaliadores independentes (Apollo Research, METR, Transluce e Goodfire) para uma primeira fase de avaliações embutidas. Cada um examina uma parte diferente: subversão, o interior dos modelos via interpretabilidade, as avaliações de alinhamento pós-treino e a maior execução por reforço da empresa.

Os relatórios públicos devem trazer os achados e limites de cada trabalho, com possibilidade de redação confidencial e período responsável de espera antes da divulgação. Fonte: https://openai.com/news/our-first-phase-of-embedded-assessments/

Fonte: <https://openai.com/news/our-first-phase-of-embedded-assessments/>

## O que são avaliações embutidas

A OpenAI assinou acordos com quatro avaliadores independentes para a primeira fase de avaliações embutidas. O modelo é dar a especialistas acesso interno profundo (modelos, checkpoints, dados e sistemas de monitoramento) por um período estendido, para examinar alinhamento e salvaguardas de forma independente.

Essa estrutura complementa os safety cases da OpenAI e atende a compromissos assumidos no White House Accord on Super Intelligence. A ideia é que o trabalho gere padrões compartilhados de avaliação independente e mais transparência sobre como os riscos são identificados e tratados.

Fonte: <https://openai.com/news/our-first-phase-of-embedded-assessments/>

## Apollo Research: subversão em duas etapas

A Apollo Research vai avaliar se modelos poderiam trabalhar de forma oculta contra as intenções dos desenvolvedores e se as salvaguardas detectariam esse comportamento. A avaliação tem duas fases.

Na primeira fase, a OpenAI fornece os insumos: modelos públicos e não lançados selecionados, checkpoints de treino, dados de treino e resultados de avaliação, registros de intervenções no treino, sistemas de monitoramento, comportamentos sinalizados e pesquisadores que dão contexto. Na segunda, a Apollo testa quatro afirmações com base no que encontrou. Fonte: https://openai.com/news/apollo-research-pilot-assessment/

- Treino não incentivou subversão.
- Avaliações fortes e red teaming não eliciam subversão.
- Modelos não tentaram subversão durante o uso interno.
- Raciocínio por trás da subversão seria detectável.

Fonte: <https://openai.com/news/apollo-research-pilot-assessment/>

## METR: a maior execução por reforço

A METR vai avaliar comportamento desalinhado na maior execução por aprendizado por reforço da OpenAI até hoje. O foco é falhas que testes e monitores existentes podem ter deixado passar.

Dentro do escopo acordado, de recursos e dos arranjos de segurança, a METR define sozinha as prioridades e pode iterar sobre buscas, análises e experimentos de elicitação. O acesso inclui checkpoints relevantes, rollouts de treino e avaliação, e registros de monitoramento de desalinhamento. Fonte: https://openai.com/news/metr-assessment/

- Fase 1: alinhamento na maior execução RL da OpenAI.
- Fase 2 (monitor): depende de acordo mútuo sobre o escopo, ainda pendente.

Fonte: <https://openai.com/news/metr-assessment/>

## Transluce: qualidade das avaliações pós-treino

A Transluce vai examinar a qualidade e a cobertura das avaliações de alinhamento pós-treino da OpenAI. Recebe modelos públicos e não lançados selecionados, as próprias avaliações de alinhamento pós-treino e resultados relevantes, dados de comportamento do modelo, documentação dos casos de segurança e pesquisadores que dão contexto.

Transluce e OpenAI compartilham a intenção de fazer uma avaliação complementar de cerca de oito semanas no início de 2027, com acesso mais amplo a modelos, às avaliações de alinhamento e informações sobre como os resultados influenciam decisões de release. Fonte: https://openai.com/news/transluce-assessment/

Fonte: <https://openai.com/news/transluce-assessment/>

## Goodfire: o interior dos modelos

Pesquisadores de interpretabilidade vão usar a plataforma da Goodfire para analisar os internos do modelo. O objetivo principal é monitorar, depurar e alinhar o treino. O público principal são pesquisadores internos da OpenAI, que usam os achados para melhorar a segurança. A Goodfire também publica aprendizados e descobertas conforme a colaboração avança. Fonte: https://openai.com/news/goodfire-platform-assessment/

Fonte: <https://openai.com/news/goodfire-platform-assessment/>

## Publicação, confidencialidade e supervisão

Os relatórios públicos devem mostrar o que cada avaliador encontrou e os limites do trabalho. A OpenAI pode redigir trechos confidenciais e pedir um período responsável de espera antes de divulgar riscos que representem ameaça à segurança ou que ainda exijam remediação.

A supervisão fica com o Safety and Security Committee (SSC), comitê independente do conselho da OpenAI Foundation, que tem visibilidade sobre as avaliações. Divergências entre a OpenAI e qualquer avaliador são escaladas ao Safety Advisory Group e a executivos, com prazo definido para resolução; o SSC é notificado prontamente. Avaliadores trabalham em ambiente on-site quando precisam de informação sensível e seguem os mesmos padrões de segurança dos funcionários. Fonte: https://openai.com/news/our-first-phase-of-embedded-assessments/

- Relatórios públicos: achados e limites.
- Informação confidencial: pode ser redigida pela OpenAI.
- Período responsável de espera antes da divulgação de riscos.
- Divergências escaladas ao Safety Advisory Group e executivos, com notificação ao SSC.

Fonte: <https://openai.com/news/our-first-phase-of-embedded-assessments/>

## Próximos passos e fontes oficiais

A primeira fase é o começo de um trabalho que a OpenAI espera evoluir para engajamentos embutidos mais longos e consistentes ao longo do tempo. A empresa pretende apoiar avaliações externas sobre uma gama mais ampla de questões de segurança nos próximos meses e também estuda avaliações futuras sobre conformidade com os próprios frameworks de segurança, cultura organizacional e processos.

Fontes oficiais: OpenAI, Our first phase of embedded assessments, https://openai.com/news/our-first-phase-of-embedded-assessments/; Apollo Research, https://openai.com/news/apollo-research-pilot-assessment/; METR, https://openai.com/news/metr-assessment/; Transluce, https://openai.com/news/transluce-assessment/; Goodfire, https://openai.com/news/goodfire-platform-assessment/

- Avaliação complementar da Transluce: cerca de oito semanas no início de 2027, com acesso mais amplo.
- Segunda avaliação da METR focada em monitores: depende de acordo mútuo sobre o escopo.
- Expansão futura para avaliações externas e novos tipos de avaliação embutida.

Fonte: <https://openai.com/news/our-first-phase-of-embedded-assessments/>
