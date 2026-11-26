# OpenAI lança BioBasicsBench com 100 tarefas de laboratório

_2026-11-15 · noticia_

O BioBasicsBench, anunciado pela OpenAI em 6 de novembro de 2026, reúne 100 tarefas de análises rotineiras de laboratório para medir como agentes de IA interpretam dados experimentais brutos. Desenvolvido com a Ligo Biosciences, o teste exige leitura de imagens, tabelas, protocolos e outros registros, além de identificação de erros e reconhecimento de evidências insuficientes. A avaliação compara sete modelos e mostra avanço da GPT‑6 Astra, mas também expõe falhas na interpretação de controles e do contexto experimental. Depois de ler, você vai entender como as tarefas e as notas são construídas, o que os resultados permitem concluir e como revisar uma análise de bancada.

## O fato

Em 6 de novembro de 2026, a OpenAI anunciou o BioBasicsBench, um benchmark com 100 tarefas baseadas em experimentos reais. O objetivo é medir como agentes de IA analisam o trabalho cotidiano de um wet lab, incluindo a interpretação de dados brutos, a identificação de erros e o reconhecimento de situações em que a evidência sustenta apenas uma conclusão limitada.

O benchmark foi desenvolvido com a Ligo Biosciences, empresa de biotecnologia focada em design de enzimas. As tarefas colocam os agentes diante de situações parecidas com as enfrentadas por cientistas na bancada, com registros que incluem imagens, arquivos de instrumentos, protocolos e anotações.

Fonte: <https://openai.com/index/measuring-how-ai-agents-handle-wet-lab-science/>

## Por que isso importa

O trabalho rotineiro de um laboratório biológico traz experimentos que falham, imagens ambíguas e observações conflitantes. Uma análise útil precisa lidar com essas condições e descobrir se um problema no procedimento, no equipamento ou nos controles mudou o resultado. Um agente que apenas reconhece o assunto da imagem ainda pode chegar à conclusão errada.

A OpenAI explica que benchmarks construídos com gráficos e imagens selecionados de artigos científicos podem deixar de lado essa ambiguidade. O BioBasicsBench usa evidências experimentais brutas para aproximar a avaliação do trabalho que os cientistas realmente precisam fazer, inclusive identificar falhas e decidir quando os dados não permitem concluir.

Essa precisão tem consequência prática. Interpretar mal uma imagem ou ignorar um problema nos controles pode levar o cientista a tirar uma conclusão errada e dedicar tempo a experimentos que não respondem à pergunta original. A OpenAI também pretende usar o benchmark para acompanhar o que os avanços nessa análise significam para o progresso científico, a biossegurança (biosafety) e a biosseguridade (biosecurity).

Fonte: <https://openai.com/index/measuring-how-ai-agents-handle-wet-lab-science/>

## As cinco áreas da rotina de bancada

As 100 tarefas cobrem cinco áreas de trabalho rotineiro em wet lab. Elas variam de pedidos simples, como ler a massa molecular de uma amostra de DNA em um gel, até análises detalhadas de ensaios. Em todas elas, o agente precisa trabalhar com evidências experimentais e produzir uma resposta que possa ser avaliada.

A maioria das tarefas combina várias habilidades. Conhecimento biológico, interpretação de imagens e outros dados, detecção de erros e compreensão de protocolos aparecem juntos na mesma atividade. Uma tarefa também pode receber várias etiquetas de habilidade; por isso, os números dessas categorias não devem ser somados para obter o total de tarefas.

- Métodos de proteínas: tarefas que envolvem a análise de materiais e resultados ligados a proteínas.
- Imagem e citometria: interpretação de imagens e de dados usados para medir características de células.
- Quantificação e ensaios: leitura e análise de resultados de ensaios laboratoriais.
- Métodos de ácidos nucleicos: interpretação de evidências relacionadas a DNA e RNA.
- Clonagem molecular: análise de experimentos de montagem e seleção de material genético.

Fonte: <https://openai.com/index/measuring-how-ai-agents-handle-wet-lab-science/>

## Como os cientistas construíram e revisaram as tarefas

Cientistas escreveram as tarefas usando dados de experimentos próprios. Cada questão foi acompanhada da evidência experimental e de uma rubrica de correção escrita por especialistas. A rubrica define quais partes da resposta recebem crédito e permite avaliar a conclusão, os resultados numéricos, o raciocínio ou o reconhecimento de que a evidência é insuficiente.

O processo teve revisões internas e externas. Os revisores examinaram o prompt, a evidência, a rubrica, as notas do autor e uma tentativa de modelo já corrigida. Essa sequência procura verificar se a pergunta, os dados e os critérios de avaliação estão coerentes antes de usar o resultado para comparar agentes.

- Criação: um cientista seleciona dados de um experimento real e escreve a pergunta com critérios especializados de correção.
- Revisão interna: um cientista da Ligo que não escreveu a tarefa examina o conjunto.
- Revisão externa: um cientista com doutorado e atuação em wet lab faz uma avaliação independente.
- Revisão interna final: uma última revisão interna encerra o processo.

Fonte: <https://openai.com/index/measuring-how-ai-agents-handle-wet-lab-science/>

## Os dados que o agente recebe

O BioBasicsBench preserva diferentes formas de evidência usadas no laboratório. Uma tarefa pode combinar vários tipos de dado, como uma fotografia da bancada, um protocolo e uma exportação de equipamento. As referências de apoio, incluindo gráficos de escada molecular e mapas de plasmídeos, ajudam a interpretar essas evidências.

Os números abaixo contam tarefas que incluem cada tipo de dado. Como as categorias se sobrepõem, a mesma tarefa pode aparecer em mais de uma linha. As folhas de referência, presentes em 21 tarefas, são materiais de apoio.

- Géis e blots: 31 tarefas, com géis de DNA em agarose, géis SDS-PAGE e Western blots.
- Protocolos, notas e especificações: 27 tarefas, com protocolos e SOPs, cadernos de laboratório, registros de execução, notas manuscritas fotografadas, catálogos, especificações de instrumentos e métodos publicados.
- Tabelas e exportações de instrumentos: 20 tarefas, com arquivos CSV e Excel, mapas de distribuição de amostras, inventários e arquivos brutos de citometria de fluxo no formato FCS.
- Fotos de bancada, equipamentos e reagentes: 18 tarefas, com bancadas, equipamentos de gel, tubos de reagentes e culturas, placas de PCR, suportes de tubos, fitas de pH, concentrador, freezer e plataforma de manipulação de líquidos.
- Microscopia: 14 tarefas, com imagens brutas de brightfield e fluorescência, conjuntos multicanal, z-stacks e filmes de time-lapse.
- Telas de instrumentos e gráficos: 13 tarefas, com fotos de telas de citômetro de fluxo, microscópio, NanoDrop, leitor de placas e balança, além de curvas padrão, cromatogramas e gráficos exportados.
- Arquivos de sequenciamento: 12 tarefas, com FASTQs brutos de leitura longa, sequências FASTA e mapas GenBank.
- Vídeos de protocolos: 7 tarefas, com estriamento, inoculação, diluição seriada, montagem de tanque de SDS-PAGE e de incubadora, e pesagem em balança.
- Placas de ágar e colônias: 7 tarefas, com placas de transformação, triagens azul/branco e placas com discos de antibiótico.
- Folhas de referência: 21 tarefas com gráficos de escada molecular, mapas de plasmídeos e gráficos de pH como material de apoio.

Fonte: <https://openai.com/index/measuring-how-ai-agents-handle-wet-lab-science/>

## Como o agente responde e como a nota é calculada

O agente devolve uma resposta estruturada com a conclusão, a medição ou a recomendação solicitada. Quando a tarefa exige, ele também apresenta o raciocínio que sustenta a resposta. A estrutura facilita a comparação, mas o conteúdo ainda precisa ser julgado pelos critérios da tarefa.

A correção é feita por rubrica. Cada critério recebe crédito, o que permite distinguir uma conclusão correta com análise incompleta de uma resposta que acerta apenas parte do raciocínio. O benchmark também pode reconhecer respostas que identificam corretamente a falta de evidência para concluir.

A medida principal é a recompensa média, ou mean reward. Ela representa a pontuação média das tarefas em porcentagem do crédito disponível. Uma nota alta significa que o modelo obteve mais crédito dentro dos critérios definidos para aquele conjunto de tarefas.

Fonte: <https://openai.com/index/measuring-how-ai-agents-handle-wet-lab-science/>

## Os números

A avaliação envolveu sete modelos, 37 configurações de modelo e esforço de raciocínio, cinco tentativas por tarefa e 100 tarefas por configuração. O total de 18.500 resultados corresponde às respostas avaliadas nessas repetições. O conjunto continua tendo 100 tarefas distintas.

Os intervalos de confiança de 95% foram calculados por reamostragem de tarefas inteiras, mantendo juntas as cinco tentativas de cada tarefa. Eles expressam a incerteza estimada da média dentro do procedimento usado. Os bigodes finos do gráfico mostram essa faixa.

O gráfico relaciona recompensa média e número médio de tokens de saída por tarefa. O eixo de tokens usa escala logarítmica e dobra a cada marcação. Linhas tracejadas laranjas representam os modelos GPT‑5; linhas azuis contínuas representam os GPT‑6. Cada ponto é uma configuração de esforço testada, e os níveis de esforço variam entre os modelos.

- Tarefas: 100, todas presentes em cada configuração avaliada.
- Modelos: GPT‑5.2, GPT‑5.4, GPT‑5.5, GPT‑5.6 Sol, GPT‑6.1 Sol, GPT‑6 Luna e GPT‑6 Astra.
- Configurações: 37 combinações entre modelo e nível de esforço de raciocínio.
- Tentativas: cinco por tarefa em cada configuração.
- Resultados avaliados: 18.500 respostas, obtidas de 37 configurações, 100 tarefas e cinco tentativas por tarefa.

Fonte: <https://openai.com/index/measuring-how-ai-agents-handle-wet-lab-science/>

## O resultado em xhigh

Xhigh é o maior nível de esforço de raciocínio reportado na tabela para os sete modelos. Cada linha inclui as 100 tarefas e cinco tentativas por tarefa. A recompensa média é a porcentagem do crédito disponível; o intervalo entre parênteses é o intervalo de confiança de 95%; os tokens indicam a saída média gerada por tarefa.

A GPT‑6 Astra obteve 66,7% de recompensa média, à frente da GPT‑6.1 Sol, com 62,0%, e da GPT‑5.6 Sol, com 43,8%. A OpenAI registra ganhos substanciais da Astra sobre a GPT‑5.6 Sol mesmo em níveis baixos de esforço e afirma que capacidades multimodais nativas mais fortes podem ajudar a explicar a melhora. O resultado sugere essa explicação, sem estabelecer sozinho uma relação de causa.

- GPT‑6 Astra: 66,7% de recompensa média, com intervalo de confiança de 95% entre 60,3% e 73,1%, e 4.704 tokens de saída por tarefa.
- GPT‑6.1 Sol: 62,0% de recompensa média, com intervalo de confiança de 95% entre 55,6% e 68,4%, e 5.238 tokens de saída por tarefa.
- GPT‑5.6 Sol: 43,8% de recompensa média, com intervalo de confiança de 95% entre 37,6% e 50,0%, e 9.099 tokens de saída por tarefa.
- GPT‑6 Luna: 38,3% de recompensa média, com intervalo de confiança de 95% entre 32,3% e 44,5%, e 13.120 tokens de saída por tarefa.
- GPT‑5.5: 35,4% de recompensa média, com intervalo de confiança de 95% entre 29,7% e 41,0%, e 11.135 tokens de saída por tarefa.
- GPT‑5.4: 33,2% de recompensa média, com intervalo de confiança de 95% entre 28,3% e 38,4%, e 13.717 tokens de saída por tarefa.
- GPT‑5.2: 31,2% de recompensa média, com intervalo de confiança de 95% entre 26,2% e 36,3%, e 27.620 tokens de saída por tarefa.

Fonte: <https://openai.com/index/measuring-how-ai-agents-handle-wet-lab-science/>

## Exemplo: células, corantes e janelas de detecção

Uma tarefa pedia que os agentes classificassem células como mortas ou vivas a partir de imagens. A GPT‑5.6 Sol usou o sinal de um corante empregado para detectar células mortas. O problema é que o detector também captava luz de um segundo corante, então o brilho da imagem não bastava para sustentar a classificação.

As mesmas regiões celulares aparecem em três canais: brightfield, com luz transmitida; canal 2, com células marcadas por SYTOX e detecção entre 470 e 540 nm; e canal 3, com FUN-1 green e detecção entre 525 e 580 nm. As janelas dos canais 2 e 3 se sobrepõem entre 525 e 540 nm. A extensão dessa interferência não foi medida.

Cada canal usa uma escala linear de intensidade própria, fixa entre as regiões comparadas. Por isso, o brilho não pode ser comparado quantitativamente entre canais. A GPT‑6 Astra reconheceu a ambiguidade e pediu controles melhores para separar os sinais. O exemplo mostra por que um sinal visível precisa ser interpretado junto com o funcionamento do detector e os limites da comparação.

Fonte: <https://openai.com/index/measuring-how-ai-agents-handle-wet-lab-science/>

## Exemplo: o controle com antibiótico errado

Em uma tarefa de clonagem de DNA, os controles eram essenciais para validar as colônias observadas. A GPT‑5.6 Sol viu que a placa de controle negativo não tinha colônias e usou essa observação para apoiar sua conclusão.

A GPT‑6 Astra examinou o rótulo na borda da placa e encontrou LB Kan50. Essa identificação aponta para kanamycin, um antibiótico diferente da ampicillin usado no experimento. Com o antibiótico errado, a placa não podia funcionar como controle confiável, e a Astra rejeitou essa evidência.

Um controle só cumpre sua função quando as condições do teste correspondem ao que ele pretende verificar. Nesse caso, o rótulo da placa fazia parte da evidência e contradizia o papel que o modelo havia atribuído a ela. Ler o dado antes de aceitar a função esperada do controle mudou a análise.

Fonte: <https://openai.com/index/measuring-how-ai-agents-handle-wet-lab-science/>

## Exemplo: imagens em profundidade

Outra tarefa mostrou células entrando e saindo de foco em uma sequência de imagens ao microscópio. A GPT‑5.6 Sol procurou uma explicação biológica para o desaparecimento aparente das células. A GPT‑6 Astra reconheceu um z-stack, uma série de imagens obtidas em diferentes profundidades.

Seis quadros extraídos da gravação original correspondem às posições de reprodução 0 s, 3 s, 6 s, 9 s, 12 s e 15 s. As caixas tracejadas acompanham a mesma região enquanto o microscópio percorre a profundidade. Uma célula pode sair do foco durante essa varredura sem desaparecer biologicamente. O contexto de aquisição da imagem muda a interpretação do que aparece e do que deixa de aparecer.

Fonte: <https://openai.com/index/measuring-how-ai-agents-handle-wet-lab-science/>

## Onde a GPT‑6 Astra ainda errou

A OpenAI alerta que notas mais altas no benchmark ainda não significam julgamentos confiáveis no laboratório. Nos exemplos da Astra, uma suposição, uma resposta esperada ou um rótulo fornecido pode se sobrepor à evidência. Uma observação intermediária correta também pode deixar de orientar a decisão final.

No erro de PCR, a Astra distinguiu corretamente dois grupos de bandas de colônias. Depois, assumiu que o produto de PCR maior identificaria a clonagem bem-sucedida e propôs as lanes 4, 6, 7 e 8. A interpretação de referência, baseada na comparação com os controles, seleciona as lanes 5, 9 e 10.

A lane 1 contém o marcador; a lane 2, a mistura de clonagem; a lane 3, o plasmídeo original; e as lanes 4 a 10, amostras de colônias. A lane 3 contém apenas o PCR do plasmídeo original e fornece a posição de referência do plasmídeo antigo. Na lane 2, a montagem incompleta deixou o molde ou backbone antigo junto do produto novo, produzindo os dois padrões. As colônias podem carregar o plasmídeo antigo ou o novo, então as bandas precisam ser comparadas com essas referências.

A Astra acertou o agrupamento visual, mas atribuiu as identidades experimentais aos grupos de forma invertida. O erro ocorreu entre perceber as bandas e interpretar o que elas representavam.

- Confira se a conclusão usa os controles como referência ou apenas como confirmação de uma expectativa.
- Separe a observação visual da identidade experimental atribuída a ela.
- Procure pontos em que uma premissa tenha substituído a comparação entre evidências.

Fonte: <https://openai.com/index/measuring-how-ai-agents-handle-wet-lab-science/>

## O que muda para você

Os exemplos oferecem uma forma prática de revisar respostas de IA sobre dados de laboratório. Primeiro, identifique o que foi observado. Depois, separe a interpretação e a conclusão. Por último, verifique quais controles, condições de imagem e informações do experimento sustentam essa passagem.

Exemplo: imagine que uma placa de controle negativo não apresenta colônias. Antes de tratar essa ausência como validação, leia o rótulo da placa e confira se o antibiótico corresponde ao experimento. Foi essa conferência que permitiu à Astra rejeitar o controle com LB Kan50. A mesma revisão ajuda a perceber quando uma imagem ambígua ou uma banda maior está sendo interpretada além do que os dados permitem.

Fonte: <https://openai.com/index/measuring-how-ai-agents-handle-wet-lab-science/>

## O que fazer hoje

Use o relatório técnico e os exemplos comentados para praticar a leitura crítica das respostas. O conjunto das 100 tarefas e o código de avaliação não foram publicados em repositório aberto; o caminho disponível é o relatório oficial.

1. Abra o relatório técnico da OpenAI em https://openai.com/index/measuring-how-ai-agents-handle-wet-lab-science/ e leia a descrição do benchmark. O resultado esperado é conhecer o escopo, as cinco áreas e os critérios de correção.
2. Estude os exemplos comentados de células, clonagem e z-stack no relatório. O resultado esperado é associar cada conclusão ao dado, ao controle e ao contexto experimental que a sustentam.
3. Escolha um dos exemplos e escreva separadamente a observação, a interpretação e a conclusão. O resultado esperado é identificar onde começa a inferência e quais evidências a justificam.
4. Ao revisar uma resposta de IA, confira os controles e as limitações antes de aceitar a conclusão. O resultado esperado é detectar uma suposição que substituiu um dado ou uma evidência que foi usada fora do seu contexto.

Fonte: <https://openai.com/index/measuring-how-ai-agents-handle-wet-lab-science/>

## O que conferir

O conjunto das 100 tarefas e o código de avaliação não foram publicados em repositório aberto. O relatório técnico completo, com exemplos comentados, está em https://openai.com/index/measuring-how-ai-agents-handle-wet-lab-science/.

Os resultados descrevem o desempenho nesse benchmark e nas configurações testadas. Eles mostram progresso na análise rotineira de laboratório e também deixam claros os pontos em que os modelos ainda falham. A leitura responsável combina a pontuação com os exemplos de acerto e erro.

- Disponibilidade: as 100 tarefas e o código de avaliação não estão em repositório aberto; os exemplos e a metodologia estão no relatório oficial.
- Contagem de dados: os tipos de evidência se sobrepõem e não devem ser somados para obter 100 tarefas; as folhas de referência são materiais de apoio.
- Comparação entre modelos: xhigh é o maior esforço reportado na tabela para os sete modelos, mas os níveis disponíveis variam entre eles. Resultados de esforço máximo, quando disponíveis, aparecem no gráfico.
- Tokens de saída: o número médio por tarefa descreve a extensão da resposta gerada; não mede sozinho velocidade, custo ou qualidade.
- Incerteza: o intervalo de confiança de 95% expressa uma faixa estimada para a média e não transforma o resultado em garantia de desempenho em qualquer laboratório.
- Revisão humana: uma conclusão precisa ser confrontada com controles, evidências e contexto antes de orientar uma decisão experimental.

Fonte: <https://openai.com/index/measuring-how-ai-agents-handle-wet-lab-science/>

## Glossário

- Agente de IA: sistema que recebe uma tarefa e produz uma resposta ou recomendação a partir dos dados fornecidos.
- Benchmark: teste padronizado usado para medir e comparar o desempenho de sistemas em um conjunto definido de atividades.
- Wet lab: laboratório que realiza experimentos com amostras biológicas.
- Dados experimentais brutos: registros produzidos diretamente pelo experimento ou pelos instrumentos, antes de uma apresentação selecionada.
- Controle experimental: referência usada para verificar se o resultado observado pode ser atribuído à condição que está sendo testada.
- Rubrica: conjunto de critérios que define quais partes de uma resposta recebem crédito.
- Recompensa média, ou mean reward: pontuação média das tarefas expressa em porcentagem do crédito disponível.
- Intervalo de confiança de 95%: faixa calculada para expressar a incerteza estimada de uma medida. No benchmark, o cálculo reamostra tarefas inteiras e mantém juntas as cinco tentativas de cada uma.
- Raciocínio xhigh: maior nível de esforço de raciocínio reportado na tabela para os sete modelos avaliados.
- Multimodal: capacidade de trabalhar com diferentes tipos de dado, como imagens, vídeos, textos e arquivos de instrumentos.
- Citometria de fluxo: técnica que mede características de células em suspensão; o benchmark inclui arquivos brutos no formato FCS.
- Z-stack: série de imagens do mesmo campo obtidas em diferentes profundidades.
- PCR: reação usada para amplificar trechos de DNA, produzindo fragmentos que podem ser analisados e comparados em gel.
- SOP: procedimento operacional padrão que descreve como executar uma atividade de laboratório.
- FASTQ: formato de arquivo usado para leituras de sequenciamento e informações de qualidade.
- FASTA: formato de arquivo usado para representar sequências biológicas.
- GenBank: formato de arquivo usado para representar sequências e suas anotações.
- Biossegurança (biosafety): conjunto de práticas e condições voltado a reduzir riscos no trabalho biológico.
- Biosseguridade (biosecurity): proteção contra uso, acesso ou liberação indevida de agentes e materiais biológicos.

## Para onde ir depois

O próximo passo é transformar os exemplos do relatório em exercícios de leitura crítica. Para cada resposta, registre a observação feita pelo modelo, a interpretação escolhida, a conclusão e o limite da evidência. Depois, repita a análise prestando atenção aos controles e ao contexto de aquisição dos dados.

Use o site oficial da Ligo Biosciences, https://ligo.bio/, para conhecer a empresa que desenvolveu o benchmark com a OpenAI e cuja especialidade declarada é design de enzimas. Para acompanhar o BioBasicsBench, o relatório técnico reúne a metodologia, os resultados e os exemplos comentados.

- Pratique a separação entre observação e interpretação nos exemplos de células e z-stack.
- Refaça a comparação entre bandas e controles no exemplo de clonagem molecular.
- Ao encontrar uma nova análise de IA para wet lab, procure os mesmos elementos: evidência bruta, controles, contexto e limites da conclusão.

Fonte: <https://openai.com/index/measuring-how-ai-agents-handle-wet-lab-science/>
