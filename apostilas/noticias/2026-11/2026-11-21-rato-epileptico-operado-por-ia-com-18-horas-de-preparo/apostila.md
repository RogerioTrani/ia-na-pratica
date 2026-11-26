# Camundongo epiléptico operado por IA com 18 horas de preparo

_2026-11-21 · noticia_

Uma equipe da Exin Therapeutics usou um agente de IA para escolher uma terapia gênica, definir o alvo cerebral e controlar um rig cirúrgico em um camundongo com modelo de epilepsia. O procedimento contou com craniotomia prévia feita por um cirurgião veterinário, aprovação humana de cada passo irreversível e um botão físico de parada de emergência. Ao ler esta apostila, você vai entender como o agente escolheu a terapia e as coordenadas, como funcionaram a visão por câmera e as barreiras de segurança, e como modelos diferentes tomaram decisões distintas. Também vai aprender a separar o sucesso de executar a injeção da comprovação de que a terapia reduziu convulsões.

## O fato

Em 27 de outubro de 2026, uma equipe da Exin Therapeutics usou um agente de IA em um procedimento cerebral de um camundongo com modelo de epilepsia. Um cirurgião veterinário abriu o crânio antes da atuação do agente. Depois disso, o agente controlou braços estereotáxicos e injetou 250 nanolitros no cérebro do animal, com supervisão de uma veterinária licenciada.

O relato foi publicado em 28 de outubro de 2026, e a WIRED publicou sua cobertura em 31 de outubro. A equipe informou cerca de 18 horas de programação e coordenação para preparar o experimento. O objetivo dado ao agente era reduzir convulsões, escolhendo uma terapia e operando o equipamento de laboratório.

O camundongo se recuperou bem da cirurgia. Ainda não há medição que comprove redução das convulsões, comprovação independente desse efeito ou publicação do caso em periódico revisado por pares. O procedimento executado e o resultado terapêutico precisam ser avaliados separadamente.

Fonte: <https://www.wired.com/story/an-ai-agent-did-brain-surgery-on-live-mouse/>

## Por que isso importa

O relato compara este experimento com robôs cirúrgicos em que uma pessoa decide qual operação realizar e o robô executa os movimentos, e reconhece que esses robôs são melhores na parte mecânica do que a bancada da equipe. Aqui, o agente recebeu um objetivo e participou das decisões científicas. Ele escolheu a terapia, definiu a região cerebral e calculou as coordenadas antes de acionar o equipamento.

A mudança está na ligação entre decisão e ação. Um sistema que apenas produz um plano deixa a execução para outra pessoa ou máquina. Um agente conectado a instrumentos pode transformar o plano em movimentos e observar o que acontece pelo caminho. Isso aproxima a IA de tarefas físicas, mas também exige controle sobre cada ação que possa causar dano.

Por isso, a parte mais útil de estudar o caso é a arquitetura de segurança. A equipe combinou conhecimento científico, câmeras, validações automáticas, autorização humana e um interruptor físico. O experimento mostra essa combinação em um único procedimento, sem estabelecer que o método está pronto para uso humano.

Fonte: <https://x.com/OcanaSantero/status/2115442964574908902>

## O que o agente recebeu

O agente recebeu quatro elementos principais: uma planilha com 19 vetores candidatos de terapia gênica, um camundongo com modelo de epilepsia, acesso a um rig cirúrgico motorizado com câmeras e o objetivo de reduzir convulsões. Cada elemento tinha uma função. A planilha apresentava as opções disponíveis, o animal era o objeto do experimento, o rig permitia agir e as câmeras permitiam observar.

A equipe não indicou previamente qual vetor aplicar nem em qual região do cérebro injetar. O agente trabalhou com essas entradas para escolher a terapia, selecionar o córtex entorrinal lateral e derivar coordenadas a partir de três artigos científicos fornecidos pela equipe. A autonomia descrita está nessas escolhas e no controle do equipamento, dentro das permissões e dos limites estabelecidos.

Fonte: <https://x.com/OcanaSantero/status/2115442964574908902>

## Como a terapia gênica foi escolhida

A escolha descrita pela equipe partiu do mecanismo que conduz as convulsões naquele modelo. O agente propôs uma terapia que aumenta a sinalização GABA, o principal neurotransmissor inibitório do cérebro. GABA ajuda a reduzir a atividade de neurônios, por isso a estratégia buscava reforçar esse sinal no tecido ligado ao problema.

A terapia selecionada tinha expressão restrita a neurônios GABAérgicos do córtex entorrinal lateral. Esse recorte importa porque o efeito pretendido não era espalhar uma intervenção por qualquer região cerebral. O agente ligou o mecanismo bioquímico, o tipo de célula e a localização anatômica. O agente também descartou o alvo padrão de epilepsia por ele falhar nesse modelo.

A informação central é a estratégia terapêutica: aumentar a sinalização inibitória GABA em uma região específica. Essa escolha explica o raciocínio científico do agente, mas não demonstra que a terapia reduziu convulsões. A eficácia depende de resultado medido depois da intervenção.

Fonte: <https://x.com/OcanaSantero/status/2115442964574908902>

## Como as coordenadas foram calculadas

Coordenadas estereotáxicas são valores usados para localizar um ponto no cérebro em relação a referências anatômicas. Elas orientam o posicionamento de instrumentos com precisão espacial. Para definir o ponto de injeção, o agente consultou três artigos científicos fornecidos pela equipe e cruzou os referenciais anatômicos descritos nesses estudos.

O agente calculou a média das coordenadas estereotáxicas para o córtex entorrinal lateral. A média reúne em um único ponto as estimativas presentes nas fontes usadas. Em seguida, o equipamento aplicou 250 nanolitros ao longo de 5 minutos. O volume, a duração e a região formam o conjunto de parâmetros da injeção.

Calcular uma média é um método para consolidar referências. Ele não substitui a validação experimental nem comprova que o ponto escolhido produz o efeito desejado. No caso, as coordenadas orientaram a execução do procedimento, enquanto a redução das convulsões continuou depender de observação posterior.

Fonte: <https://x.com/OcanaSantero/status/2115442964574908902>

## Como a cirurgia aconteceu

A divisão de trabalho começou antes da injeção. Um cirurgião veterinário realizou a craniotomia, que é a abertura do crânio para acessar o cérebro. O agente observou essa etapa pela câmera, mas não tinha permissão para executá-la. Depois da abertura, ele passou a controlar os braços estereotáxicos e a injeção.

A equipe construiu um rig cirúrgico motorizado em Arduino. Para conectar o agente ao equipamento, expôs a câmera e os motores por soluções próprias de integração. O agente podia requisitar imagens do campo cirúrgico e acionar movimentos dentro das condições autorizadas.

Durante a injeção de 250 nanolitros, o agente observou o local de entrada pela câmera para verificar sangramentos. A veterinária licenciada aprovava cada passo irreversível. O procedimento, portanto, combinou ação robótica, percepção visual e decisão humana nos pontos críticos.

Fonte: <https://x.com/OcanaSantero/status/2115442964574908902>

## O que o agente viu pela câmera

O rig tinha uma câmera voltada para o campo cirúrgico. O agente podia solicitar quadros sempre que quisesse e fez 32 observações na sessão. Entre elas, acompanhou o trabalho do cirurgião veterinário na craniotomia e monitorou o ponto de entrada da agulha durante a injeção.

Essas imagens alimentavam um ciclo de percepção e ação. O agente obtinha uma visão do equipamento e do tecido, avaliava o que aparecia na imagem e decidia o próximo movimento. A observação de sangramento era parte desse ciclo, porque o equipamento não agia apenas com base em coordenadas previamente calculadas.

O número de observações mostra quantas vezes o agente consultou a câmera. Ele não mede a precisão do diagnóstico visual nem garante que todos os riscos foram percebidos. A câmera ampliava a informação disponível para o agente, enquanto a supervisão humana e os limites de execução continuavam presentes.

Fonte: <https://x.com/OcanaSantero/status/2115442964574908902>

## Camadas de segurança

A segurança do experimento foi dividida em camadas com funções diferentes. A aprovação humana tratava das decisões irreversíveis. Os validadores fixos conferiam limites automáticos. A aprovação vinculada por hash impedia que uma autorização fosse usada para um plano diferente. O botão físico de emergência oferecia uma forma de interromper os motores sem depender do software.

Essas camadas se complementam. Uma regra automática pode barrar um volume acima do limite, mas não substitui a avaliação de uma pessoa sobre o contexto. Uma pessoa pode autorizar uma etapa, mas ainda precisa de um meio de parar o equipamento imediatamente. A combinação reduz a dependência de um único controle.

- Aprovação humana: a veterinária licenciada autorizava manualmente cada etapa irreversível.
- Validador fixo: regras automáticas verificavam limites, incluindo o volume injetado.
- Aprovação vinculada por hash: a autorização ficava ligada à identificação do plano aprovado, de modo que uma alteração no plano não herdava a aprovação anterior.
- Kill switch físico: a veterinária mantinha o dedo sobre um botão capaz de cortar a energia de todos os motores.

Fonte: <https://x.com/OcanaSantero/status/2115442964574908902>

## Três modelos, três decisões

A equipe testou três modelos da Anthropic no mesmo contexto. O comportamento deles mudou ao longo do processo. Um recusou, outro completou o ensaio seguro e parou no início da cirurgia ao vivo, e o terceiro conduziu a injeção.

O Claude Sonnet 5 também interrompeu um movimento durante um erro de calibração no eixo Y de 34 mm em um equipamento de 30 mm. O modelo se recusou a continuar até que a equipe corrigisse o código manualmente. Esse episódio concreto mostra uma parada diante de um erro de calibração.

Os três casos descrevem o comportamento dos modelos neste experimento. Eles não permitem concluir que um modelo será seguro em qualquer situação, nem que a recusa de dois modelos e a execução de um revelem uma regra geral de confiabilidade. O resultado observado depende do contexto, das instruções, das ferramentas e das barreiras impostas pela equipe.

- Claude Opus 5.5 (claude-opus-5-5): recusou.
- Claude Opus 5 (claude-opus-5): completou o dry run com água e papel milimetrado e parou no início da cirurgia ao vivo.
- Claude Sonnet 5 (claude-sonnet-5): conduziu a injeção ao vivo e interrompeu o movimento problemático até a correção manual do código.

Fonte: <https://www.wired.com/story/an-ai-agent-did-brain-surgery-on-live-mouse/>

## O resultado do experimento

O camundongo se recuperou bem do procedimento cirúrgico. Isso informa como o animal respondeu à intervenção física. Ainda não existe medição que mostre se a terapia gênica reduziu as convulsões, e o caso não tem comprovação independente desse efeito.

O experimento também não foi publicado em periódico revisado por pares. A execução da escolha terapêutica, o cálculo das coordenadas e a aplicação da injeção são fatos observados. A eficácia contra a epilepsia permanece uma questão aberta até a medição do resultado clínico no modelo animal.

Essa distinção evita duas leituras incorretas. A recuperação da cirurgia não comprova efeito terapêutico. A atuação do agente não comprova que o método está pronto para humanos. O caso documenta uma forma de conectar IA, equipamento e supervisão em um experimento específico.

Fonte: <https://x.com/OcanaSantero/status/2115442964574908902>

## Os números

- Cerca de 18 horas: tempo de programação e coordenação para preparar o experimento, não duração da cirurgia.
- 19 vetores: quantidade de candidatos de terapia gênica apresentados na planilha, não quantidade de terapias aplicadas no animal.
- Três artigos: fontes usadas para derivar as coordenadas estereotáxicas, não três tratamentos testados no camundongo.
- 250 nanolitros: volume injetado no cérebro do camundongo, não uma dose humana nem uma medida de eficácia.
- 5 minutos: duração da injeção, não tempo total do procedimento.
- 32 observações: vezes que o agente consultou imagens da câmera na sessão, não número de validações independentes.
- Três modelos: Claude Opus 5.5, Claude Opus 5 e Claude Sonnet 5; somente o Claude Sonnet 5 conduziu a cirurgia ao vivo.
- 34 mm em um equipamento de 30 mm: erro de calibração no eixo Y, durante o qual o Claude Sonnet 5 interrompeu o movimento e se recusou a continuar até a correção manual do código.

Fonte: <https://www.wired.com/story/an-ai-agent-did-brain-surgery-on-live-mouse/>

## O que muda para você

Para quem acompanha IA, o caso oferece um modelo de como avaliar agentes que atuam fora da tela. A pergunta útil não é apenas se o sistema consegue produzir um plano. É preciso verificar como ele escolhe, quais ferramentas usa, o que observa durante a ação, quem autoriza os passos críticos e como o sistema pode ser interrompido.

Exemplo: imagine que um agente de laboratório recebe uma lista de terapias, artigos científicos e acesso a equipamentos motorizados. Ele escolhe o alvo e calcula as coordenadas. Um validador confere o volume, uma pessoa autoriza a etapa irreversível, a câmera mostra o campo cirúrgico e um botão físico corta a energia dos motores se houver necessidade. Cada parte responde a um risco diferente.

Esse arranjo ajuda a separar autonomia de ausência de controle. O agente pode tomar decisões dentro do problema, enquanto a equipe mantém pontos de aprovação e parada. A lição serve para analisar sistemas de IA com hardware, sem transformar este experimento animal em recomendação para procedimentos humanos.

## O que fazer hoje

Você pode aplicar o caso como um exercício de leitura de notícias e de avaliação de sistemas autônomos. O objetivo é sair com critérios claros para interpretar anúncios semelhantes.

1. Liste os fatos executados: escolha da terapia, definição do córtex entorrinal lateral, cálculo das coordenadas, injeção de 250 nanolitros e recuperação do animal. O resultado é uma separação clara entre execução e eficácia terapêutica.
2. Monte um quadro das barreiras de segurança com aprovação humana, validador de volume, aprovação vinculada por hash e kill switch físico. O resultado é um checklist que mostra qual risco cada camada pretende controlar.
3. Compare o comportamento de Claude Opus 5.5, Claude Opus 5 e Claude Sonnet 5: a recusa, o dry run e a cirurgia ao vivo. O resultado é uma leitura que preserva as diferenças entre os modelos.
4. Ao avaliar outro agente conectado a hardware, pergunte quem aprova as ações irreversíveis, quais limites são automáticos, o que o sistema observa e como interromper os motores. O resultado é uma avaliação baseada em controles concretos.
5. Acompanhe a publicação científica e a comprovação independente antes de usar o caso como evidência de redução de convulsões. O resultado é uma conclusão limitada ao que foi demonstrado.

Fonte: <https://www.wired.com/story/an-ai-agent-did-brain-surgery-on-live-mouse/>

## O que conferir

Antes de repetir ou compartilhar o resultado, confira os pontos que mudam o sentido da notícia. Eles ajudam a evitar exagero sobre autonomia, segurança e eficácia.

- Confira se a craniotomia aparece como etapa feita previamente por um cirurgião veterinário, e não pelo agente.
- Confira se as cerca de 18 horas se referem à programação e à coordenação do experimento, não à duração da operação.
- Confira se os 250 nanolitros foram injetados ao longo de 5 minutos no córtex entorrinal lateral.
- Confira se Claude Opus 5.5 recusou, se Claude Opus 5 parou no início da cirurgia ao vivo, depois do dry run, e se Claude Sonnet 5 foi quem executou a injeção.
- Confira se a segurança inclui aprovação humana de cada passo irreversível, validadores fixos, aprovação vinculada por hash e um kill switch físico.
- Confira se a recuperação do camundongo está separada da redução das convulsões, que ainda não foi medida.
- Confira se o caso está descrito como sem comprovação independente e sem publicação em periódico revisado por pares.
- Trate a média das coordenadas como método para consolidar referências anatômicas, não como comprovação de eficácia.

Fonte: <https://www.wired.com/story/an-ai-agent-did-brain-surgery-on-live-mouse/>

## Glossário

- Agente de IA: sistema que recebe um objetivo, toma decisões e executa ações com as ferramentas disponíveis.
- Terapia gênica: abordagem que usa material genético para alterar a atividade de células.
- Vetor de terapia gênica: veículo usado para entregar material genético às células.
- GABA: ácido gama-aminobutírico, principal neurotransmissor inibitório do cérebro.
- Neurônio GABAérgico: neurônio que usa GABA para sinalizar.
- Promotor: sequência de DNA que controla a expressão de um gene em determinadas células ou condições.
- Córtex entorrinal lateral: região cerebral escolhida como alvo da injeção neste experimento.
- Coordenadas estereotáxicas: valores que localizam um ponto no cérebro em relação a referências anatômicas.
- Rig cirúrgico: conjunto de equipamentos motorizados usado para posicionar instrumentos e aplicar a injeção.
- Craniotomia: abertura do crânio para acesso ao cérebro.
- Dry run: ensaio em condições seguras, com água e papel milimetrado, antes da operação ao vivo.
- Validador fixo: regra automática que confere limites, como o volume máximo de injeção.
- Aprovação vinculada por hash: autorização ligada à identificação do plano aprovado, de modo que uma alteração exige nova aprovação.
- Kill switch: botão físico que corta a energia dos motores.
- Nanolitro: unidade de volume usada para medir a injeção.
- Revisão por pares: avaliação do trabalho por outros especialistas antes da publicação científica.

## Para onde ir depois

- Releia O fato e O resultado do experimento e explique a diferença entre executar uma terapia e comprovar seu efeito.
- Pratique descrever o fluxo completo do agente: entradas, escolha da terapia, cálculo das coordenadas, movimento do equipamento, observação pela câmera e autorização humana.
- Use o Glossário para revisar GABA, coordenadas estereotáxicas, dry run, validador fixo e kill switch antes de discutir outros casos de IA com hardware.
- Acompanhe os próximos resultados científicos do experimento e mantenha a distinção entre recuperação cirúrgica, redução de convulsões e validação independente.

## Links citados

- https://anthropic.com
- https://exintherapeutics.com

## Outros detalhes

- A thread original cita dois artigos da equipe sobre outros projetos, com identificadores arXiv 2610.11222 e 2610.09643.
- A publicação original no X chegou a registrar 1,6 milhão de visualizações.
- O relato anuncia um relatório técnico com mais detalhes sobre a conexão entre agentes e equipamento.
- O relato menciona um momento em que o agente se recusou a deixar que quem o relata passasse por cima dele.
- O Claude Opus 5 também foi acionado em separado para ajudar a corrigir um bug de coordenadas.
