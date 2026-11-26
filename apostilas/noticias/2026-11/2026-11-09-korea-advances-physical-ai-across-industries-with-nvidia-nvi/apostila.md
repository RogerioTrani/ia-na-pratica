# De 18 horas para 41 segundos na Samsung

_2026-11-09 · noticia_

A Samsung Electronics ampliou sua colaboração com a NVIDIA para usar computação acelerada e IA física na engenharia de semicondutores. O caso mais concreto é uma simulação térmica e mecânica em escala de chip com NVIDIA PhysicsNeMo: o tempo caiu de cerca de 18 horas para 41 segundos, uma aceleração de aproximadamente 1.600x naquele cenário. Ao longo desta apostila, você vai entender o papel da IA, das malhas mais grossas e da GPU, conhecer as outras ferramentas citadas e aprender a separar resultados medidos de planos futuros. Também verá como os mesmos princípios aparecem em mobilidade autônoma e robótica industrial.

## O fato

A Samsung Electronics está ampliando sua colaboração com a NVIDIA para avançar a inovação em semicondutores com computação acelerada e IA física. O trabalho cobre pesquisa de materiais, desenvolvimento de processo e engenharia de dispositivos. O anúncio situa essas iniciativas dentro de um esforço mais amplo da Coreia para aplicar IA, computação acelerada e simulação à indústria.

O caso mais concreto é uma análise térmica e mecânica em escala de chip com NVIDIA PhysicsNeMo. A combinação de propriedades efetivas de material previstas por IA, malhas mais grossas e aceleração por GPU resultou, nesse cenário, em uma aceleração de aproximadamente 1.600x. O anúncio também reúne planos da Kakao Mobility para direção autônoma e resultados da LG Electronics em robótica industrial.

Fonte: <https://blogs.nvidia.com/blog/korea-physical-ai-ecosystem/>

## Por que isso importa

A engenharia de um chip passa por várias escalas. A pesquisa de materiais investiga as propriedades que poderão ser usadas na fabricação. O desenvolvimento de processo estuda como executar e controlar as etapas de produção. A engenharia de dispositivos analisa como as estruturas projetadas se comportam. A simulação ajuda a examinar essas questões antes de depender de um protótipo físico a cada teste.

O caso da Samsung mostra o valor de atacar o tempo de cálculo em uma etapa específica desse percurso. Quando uma análise leva menos tempo, a equipe pode reservar mais espaço para repetir verificações e comparar alternativas. O resultado anunciado se aplica à resolução descrita no caso. A qualidade da decisão de engenharia continua dependendo da validação do modelo e da precisão adequada ao objetivo do projeto.

A diversidade de ferramentas no anúncio também explica o recorte da parceria. Sistemas lineares esparsos, química quântica, modelos atomísticos e simulações físicas exigem cálculos diferentes. Cada ferramenta atua em uma parte desse conjunto, e a aceleração por GPU aparece em mais de uma frente.

Fonte: <https://blogs.nvidia.com/blog/korea-physical-ai-ecosystem/>

## Como funciona o caso com NVIDIA PhysicsNeMo

A simulação térmica e mecânica estuda como uma estrutura responde ao calor e a forças. Para representar um material com detalhes internos em uma simulação de escala maior, a engenharia pode usar homogeneização. Esse processo busca descrever a peça por propriedades efetivas, que representam seu comportamento na escala adotada pelo modelo. No caso da Samsung, a IA previu essas propriedades efetivas.

A malha divide a região analisada em elementos sobre os quais o cálculo é feito. Uma malha mais grossa reduz a quantidade de elementos e, com isso, reduz o trabalho de resolução. O fluxo descrito combinou as propriedades previstas por IA, essa malha mais grossa e a aceleração por GPU. O resultado foi a queda do tempo de simulação de cerca de 18 horas para 41 segundos.

A linha de base foi uma resolução com malha fina em uma CPU de 32 núcleos. A nova execução foi uma resolução com malha grossa acelerada por GPU. Como três elementos mudaram juntos, a aceleração de aproximadamente 1.600x descreve a combinação completa. O número não isola a contribuição individual da IA, da mudança de malha ou da GPU. Ele também mede o tempo da resolução nesse caso, e não a duração inteira de um projeto de chip.

Fonte: <https://blogs.nvidia.com/blog/korea-physical-ai-ecosystem/>

## cuISS e cuDSS nos sistemas lineares esparsos

O design auxiliado por computador na área de semicondutores transforma problemas físicos em modelos matemáticos. Muitos desses modelos exigem a resolução de sistemas lineares. Um sistema é chamado de esparso quando a maior parte de seus coeficientes é zero. Essa característica permite explorar a estrutura do problema para acelerar o cálculo.

A Samsung trabalha com NVIDIA cuISS e NVIDIA cuDSS para acelerar cálculos envolvendo sistemas lineares esparsos. Essas ferramentas atuam na camada matemática do fluxo. Elas se relacionam com o mesmo esforço de computação acelerada, mas o resultado de aproximadamente 1.600x pertence ao caso de homogeneização com NVIDIA PhysicsNeMo. Para entender uma avaliação, convém separar a preparação do modelo, a resolução do sistema linear e a interpretação do resultado.

Fonte: <https://blogs.nvidia.com/blog/korea-physical-ai-ecosystem/>

## Aceleração por GPU nas simulações de processo e óptica

A colaboração também inclui aceleração por GPU em simulações de processo e óptica. A simulação de processo representa como etapas de fabricação alteram as estruturas de um dispositivo. A simulação óptica estuda o comportamento da luz no contexto do processo de fabricação de semicondutores. As duas ajudam a equipe a examinar condições antes de partir para a produção.

Uma GPU reúne muitas unidades de cálculo que podem trabalhar em paralelo. Isso a torna útil para operações repetidas e volumosas, como as encontradas em simulações. A presença da aceleração por GPU nessas frentes amplia o uso da computação acelerada ao longo do desenvolvimento. Cada tipo de simulação mantém seu próprio modelo, suas exigências de precisão e seu método de validação.

Fonte: <https://blogs.nvidia.com/blog/korea-physical-ai-ecosystem/>

## sMOL e cuEST na química quântica

A plataforma sMOL da Samsung executou cálculos químico-quânticos selecionados até 5x mais rápido, de ponta a ponta, com NVIDIA cuEST. A química quântica usa a mecânica quântica para estudar sistemas químicos. Na pesquisa de materiais, esse tipo de cálculo pode apoiar a compreensão de interações no nível dos átomos.

A expressão de ponta a ponta indica que a aceleração foi considerada ao longo do fluxo completo desses cálculos. O teto de até 5x deve ser lido junto com o recorte de cálculos selecionados. Ele descreve o resultado obtido pela sMOL com cuEST nessa atividade específica. Para aproveitar esse tipo de dado, o leitor deve comparar fluxos equivalentes e manter claro quais cálculos estão sendo medidos.

Fonte: <https://blogs.nvidia.com/blog/korea-physical-ai-ecosystem/>

## cuEquivariance e os modelos atomísticos de IA

A Samsung também explora NVIDIA cuEquivariance para acelerar operações com tensores usadas no treinamento e na inferência de modelos atomísticos de IA. Um tensor é uma estrutura de dados com várias dimensões. Modelos atomísticos de IA trabalham com representações de átomos e de suas interações para apoiar tarefas ligadas à pesquisa de materiais.

As operações com tensores são parte do trabalho matemático executado durante o treinamento e durante a inferência. Acelerar essas operações pode reduzir o tempo dedicado a essa camada dos modelos. No anúncio, cuEquivariance aparece como uma exploração da Samsung. Essa condição deve acompanhar a descrição da ferramenta, junto com sua finalidade de acelerar operações tensoriais em modelos atomísticos.

Fonte: <https://blogs.nvidia.com/blog/korea-physical-ai-ecosystem/>

## NVIDIA Agent Toolkit e a integração futura

Olhando para frente, o NVIDIA Agent Toolkit poderia conectar ferramentas de simulação e modelos de IA. Segundo o anúncio, essa integração ajudaria agentes de engenharia futuros a executar análises e comparar opções de design. A ideia é reunir partes do fluxo que hoje aparecem como ferramentas especializadas.

O anúncio apresenta essa possibilidade em caráter futuro. O valor potencial está em coordenar tarefas e reunir resultados para apoiar comparações. Ainda assim, a automação de uma análise não substitui a definição dos critérios de projeto nem a revisão dos resultados. Quem acompanhar essa frente deve observar como as ferramentas serão conectadas e quais decisões poderão ser tomadas com os resultados gerados.

Fonte: <https://blogs.nvidia.com/blog/korea-physical-ai-ecosystem/>

## Kakao Mobility e a direção autônoma de nível 4

A Kakao Mobility planeja usar tecnologias de computação e segurança para veículos da NVIDIA no desenvolvimento de um sistema de direção autônoma de nível 4. O trabalho combina o software de condução próprio da empresa e sua experiência de operação no distrito de Gangnam, em Seul, com a plataforma de computação veicular da NVIDIA.

A empresa planeja usar NVIDIA Hyperion, uma plataforma de referência para sensores e computação de veículos, alimentada por NVIDIA DRIVE AGX Thor. Também pretende usar NVIDIA Halos para apoiar a segurança durante o desenvolvimento e a validação da tecnologia de direção autônoma. O desenvolvimento inicial está previsto para veículos da Kia construídos para essa finalidade. O objetivo declarado é apoiar futuros serviços de mobilidade de nível 4 na Coreia.

Esses pontos descrevem planos da Kakao Mobility. Eles mostram como software, sensores, computação e validação se combinam no desenvolvimento de um sistema de condução autônoma.

Fonte: <https://blogs.nvidia.com/blog/korea-physical-ai-ecosystem/>

## CLOiD e o ciclo de dados da robótica industrial

A NVIDIA e a LG Electronics demonstraram com sucesso tarefas de manipulação robótica e manufatura com o robô CLOiD da LG, usando NVIDIA Isaac GR00T em um ambiente real de fabricação. As equipes implementaram um ciclo de dados de IA física que conecta coleta no mundo real, treinamento, computação embarcada e avaliação por simulação.

O ciclo descrito no anúncio segue estas etapas:

- Coleta de dados no mundo real: reúne exemplos das tarefas realizadas no ambiente de manufatura.
- Aumento de dados baseado em NVIDIA Cosmos: amplia os dados coletados para apoiar o treinamento.
- Treinamento do modelo NVIDIA Isaac GR00T: usa os dados para desenvolver as capacidades de manipulação do robô.
- Computação embarcada com NVIDIA Jetson AGX Thor: leva o processamento para o robô CLOiD.
- Avaliação baseada em simulação: testa as capacidades do robô e apoia o processo de validação.

Fonte: <https://blogs.nvidia.com/blog/korea-physical-ai-ecosystem/>

## Os números

Os números do anúncio ajudam a entender o alcance de cada resultado quando acompanham suas condições. Eles medem etapas diferentes e não devem ser usados como uma única medida de desempenho para toda a parceria.

- Aproximadamente 1.600x: aceleração do caso de homogeneização por IA, relativa à linha de base descrita e dependente da combinação de propriedades previstas por IA, malha grossa e GPU.
- Cerca de 18 horas: tempo da resolução com malha fina em uma CPU de 32 núcleos, usado como linha de base no caso com NVIDIA PhysicsNeMo.
- 41 segundos: tempo da resolução acelerada por GPU com malha grossa no mesmo caso; representa essa etapa da simulação.
- Até 5x: aceleração de ponta a ponta de cálculos químico-quânticos selecionados executados pela sMOL com NVIDIA cuEST; o valor máximo pertence a esse recorte.

Fonte: <https://blogs.nvidia.com/blog/korea-physical-ai-ecosystem/>

## O que muda para você

Imagine que uma equipe de engenharia precisa avaliar o comportamento térmico e mecânico de uma estrutura de chip. No fluxo da Samsung, a IA prevê propriedades efetivas da peça, a malha fica mais grossa e a GPU acelera a resolução. Essas três mudanças atuam juntas para reduzir o tempo daquele cálculo.

Para usar o caso como referência, comece medindo sua própria linha de base. Depois, altere uma parte do fluxo por vez e verifique se o resultado continua adequado à decisão de engenharia. O tempo de 41 segundos pertence ao exemplo da Samsung. A lição prática é identificar quais partes do seu processo consomem tempo e quais ferramentas podem atuar sobre elas, mantendo a validação no centro da avaliação.

Fonte: <https://blogs.nvidia.com/blog/korea-physical-ai-ecosystem/>

## O que fazer hoje

A avaliação dessas tecnologias começa pelo fluxo de trabalho. Separe as etapas antes de comparar ferramentas, para que cada resultado tenha um objeto claro de medição.

1. Mapeie a etapa que mais consome tempo na sua simulação ou análise. O resultado esperado é uma lista com as operações principais e o tempo gasto em cada uma.
2. No estudo térmico e mecânico, separe propriedades da peça, resolução da malha e resolução do sistema. O resultado esperado é a identificação de qual mudança corresponde a cada parte do fluxo de NVIDIA PhysicsNeMo.
3. Estabeleça uma linha de base com o modelo, a malha e o hardware registrados. O resultado esperado é uma referência que permita comparar a execução acelerada em condições conhecidas.
4. Para sistemas lineares esparsos, avalie NVIDIA cuISS e NVIDIA cuDSS na etapa de resolução. O resultado esperado é saber qual ferramenta corresponde ao cálculo que você precisa acelerar.
5. Para cálculos químico-quânticos selecionados, avalie o fluxo de sMOL com NVIDIA cuEST. O resultado esperado é medir a aceleração de ponta a ponta no conjunto de cálculos escolhido.
6. Para modelos atomísticos de IA, acompanhe NVIDIA cuEquivariance e a integração proposta pelo NVIDIA Agent Toolkit. O resultado esperado é distinguir a aceleração de operações tensoriais da futura conexão entre ferramentas e agentes.

Fonte: <https://blogs.nvidia.com/blog/korea-physical-ai-ecosystem/>

## O que conferir

Os resultados do anúncio têm recortes diferentes. Antes de usar um número ou tratar uma ferramenta como disponível em um fluxo, verifique a condição em que ela foi apresentada.

- Recorte do resultado de aproximadamente 1.600x: ele reúne IA, malha mais grossa e GPU em um caso de homogeneização, sem isolar a contribuição de cada mudança.
- Precisão da malha mais grossa: confira se a representação adotada atende ao objetivo da análise e mantenha a validação do resultado.
- Tempo medido: os 41 segundos correspondem à resolução acelerada no caso descrito, e não à duração total de um projeto de chip.
- Recorte do resultado de até 5x: ele se aplica a cálculos químico-quânticos selecionados, de ponta a ponta, na sMOL com NVIDIA cuEST.
- Status de NVIDIA cuEquivariance: a Samsung está explorando a ferramenta para acelerar operações tensoriais em modelos atomísticos.
- Status do NVIDIA Agent Toolkit: a integração com ferramentas de simulação e modelos de IA aparece como possibilidade futura.
- Planos e demonstrações: a Kakao Mobility apresenta planos para nível 4, enquanto a LG Electronics e a NVIDIA relatam uma demonstração realizada em ambiente real de manufatura.

Fonte: <https://blogs.nvidia.com/blog/korea-physical-ai-ecosystem/>

## Glossário

- IA física: aplicação de IA e simulação a sistemas do mundo real, como dispositivos, robôs e veículos.
- Simulação: representação computacional de um sistema usada para estudar seu comportamento.
- Malha: divisão da região analisada em elementos sobre os quais o cálculo é realizado; uma malha mais grossa tem menos elementos que uma malha fina.
- Homogeneização: representação de um material detalhado por propriedades que descrevem seu comportamento em uma escala maior.
- Propriedade efetiva: valor que descreve o comportamento da peça como um todo na escala usada pela simulação.
- Sistema linear esparso: conjunto de equações lineares em que a maioria dos coeficientes é zero.
- GPU: processador com muitas unidades de cálculo em paralelo, usado no anúncio para acelerar simulações e outros cálculos.
- Tensor: estrutura de dados com várias dimensões usada em operações de modelos de IA.
- Treinamento: etapa em que um modelo ajusta seus parâmetros a partir de dados.
- Inferência: uso de um modelo treinado para produzir um resultado.
- Química quântica: estudo de sistemas químicos com base na mecânica quântica.
- Modelo atomístico de IA: modelo que usa representações de átomos e interações para apoiar tarefas de pesquisa de materiais.
- Ciclo de dados: processo repetível que conecta coleta de dados, treinamento, computação e avaliação para melhorar um sistema.
- NVIDIA Hyperion: plataforma de referência da NVIDIA para sensores e computação de veículos.
- NVIDIA Halos: conjunto de tecnologias da NVIDIA usado para apoiar segurança no desenvolvimento e na validação de direção autônoma.
- Nível 4 de direção autônoma: categoria em que o veículo realiza a condução em condições operacionais definidas, sem depender de uma pessoa para conduzir nessas condições.

Fonte: <https://blogs.nvidia.com/blog/korea-physical-ai-ecosystem/>

## Para onde ir depois

O próximo passo é escolher um único fluxo de cálculo e aplicar nele a leitura feita nesta apostila. Registre a linha de base, identifique a etapa que pode ser acelerada e defina como o resultado será validado. Depois, acompanhe a evolução das ferramentas que aparecem como exploração ou integração futura no anúncio.

- Releia o anúncio oficial e compare as condições de cada resultado, especialmente os casos de NVIDIA PhysicsNeMo e sMOL com cuEST.
- Pratique a separação entre modelo, resolução e hardware usando uma simulação do seu interesse. O objetivo é aprender a medir o efeito de cada mudança.
- Acompanhe os próximos desdobramentos de NVIDIA cuEquivariance e NVIDIA Agent Toolkit para verificar como operações tensoriais e conexões entre ferramentas entram nos fluxos de engenharia.

Fonte: <https://blogs.nvidia.com/blog/korea-physical-ai-ecosystem/>
