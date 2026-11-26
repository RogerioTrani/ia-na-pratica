# GPT-6 Astra projeta placa de circuito.

_2026-11-18 · noticia_

A OpenAI mostrou o GPT-6 Astra projetando uma placa de circuito física, que voltou montada depois de ajustes com a fábrica. O projeto combina uso de computador, engenharia física e um assistente de voz do Codex em um pequeno display. A apresentação também abre espaço para entender como modelos avaliados em projeto de chips podem melhorar circuitos existentes ou criar núcleos a partir de especificações. Ao fim, você vai saber distinguir resultados de hardware, testes em simulação e pontuações normalizadas, além de aplicar o ciclo de proposta, validação e revisão aos seus projetos.

## O fato

Justin Lin, da equipe de pesquisa da OpenAI, apresentou um projeto em que o GPT-6 Astra projetou uma placa de circuito. Ele descreveu o que queria, forneceu planos e recebeu o projeto da placa. Depois de algumas rodadas com a fábrica, a placa voltou montada.

O objeto da demonstração é um PCB, a placa de circuito impresso que acomoda e liga os componentes eletrônicos de um dispositivo. A novidade está na passagem concreta de uma placa vazia para um hardware montado, com o modelo envolvido no processo de projeto.

O anúncio também tem contexto temporal. A página de pesquisa da OpenAI registra o lançamento de GPT-6.2 Astra e Sol em 17 de novembro de 2026. Em 18 de novembro de 2026, a empresa publicou o trabalho que detalha melhorias em projeto de chips.

Fonte: <https://openai.com/index/gpt-6-astra/>

## Por que isso importa

Um circuito reúne decisões que precisam funcionar juntas. Desempenho, consumo de energia e área ocupada mudam quando a estrutura do circuito muda. Por isso, uma proposta de hardware precisa ser avaliada como um conjunto.

Quando um modelo trabalha com texto, a resposta pode ser lida e revisada na tela. O caminho até um objeto físico acrescenta etapas como fabricação e montagem. No caso dos chips, a validação também aparece em simulação. Cada etapa devolve informações que podem mudar a solução.

No projeto da placa, a iteração incluiu candidatos de projeto em paralelo e versões da carcaça. A fábrica participou das rodadas de ajuste. Para Justin Lin, poder iterar em hardware amplia o que ele se sente capaz de tentar e o leva a pensar projetos maiores.

Fonte: <https://openai.com/research/index/>

## Um Codex num display

Justin Lin queria conversar com o Codex sem abrir o notebook. A solução foi um bichinho do Codex em um display, com um botão de apertar para falar. O assistente responde em voz, e a interação por botão dá ao usuário um controle direto sobre quando iniciar a fala.

Esse arranjo reúne duas funções. O display apresenta o assistente, e a voz permite ouvir respostas e acompanhar informações sem depender da leitura de uma tela. Na demonstração, o usuário pergunta sobre agentes ativos e recebe a resposta falada.

O uso de computador permite ao modelo interagir com um ambiente de software. A engenharia física entra no projeto da placa. O assistente de voz é a interface por onde Justin Lin conversa com o Codex. Cada parte tem uma função distinta no mesmo projeto.

Fonte: <https://developers.openai.com/codex>

## Da placa vazia à placa montada

Era a primeira vez de Justin Lin percorrendo o caminho de uma placa vazia até um PCB montado. Ele contou ao modelo o que queria e entregou planos. O Astra projetou a placa, e o resultado seguiu para a fábrica.

O processo não terminou na primeira proposta. Houve algumas rodadas de ajuste com a fábrica até a placa voltar montada. A equipe também produziu vários candidatos de projeto em paralelo e muitas versões da carcaça, o invólucro externo que acomoda e protege a montagem.

O exemplo ensina uma sequência prática: descrever o objeto desejado, trabalhar com os planos, comparar alternativas e incorporar o retorno da fabricação. A existência de várias candidatas e versões de carcaça mostra que a revisão fez parte do caminho até o resultado final.

Fonte: <https://openai.com/index/gpt-6-astra/>

## A demonstração por voz

Na demonstração, Justin Lin perguntou ao Codex se havia agentes ativos. A resposta veio em voz: cinco agentes ativos. O assistente também se ofereceu para ler a lista em voz alta.

Um agente, nesse contexto, é uma execução que usa o modelo para conduzir uma tarefa com ferramentas. A contagem indica quantas execuções estavam ativas naquele momento. Ela é uma fotografia do estado do Codex durante a conversa.

O número não mede a complexidade da placa nem a quantidade de trabalho concluído. Ele mostra a interface informando o estado dos agentes por voz, enquanto o usuário mantém a conversa no display.

Fonte: <https://developers.openai.com/codex>

## O contexto do projeto de chips

A pesquisa de 18 de novembro de 2026 examina o uso de modelos para melhorar circuitos existentes e explorar novas arquiteturas de processadores. A OpenAI conta que, em agosto, seus engenheiros usaram modelos de fronteira para acelerar o desenvolvimento do primeiro chip de inferência personalizado da empresa, o Jalapeño.

O trabalho com Jalapeño começou com o GPT-o3 mini no início de 2025. Mesmo esse modelo inicial já encontrou melhorias relevantes de PPA, sigla para potência, desempenho e área. Potência indica a energia usada por unidade de tempo; desempenho descreve quanto trabalho o circuito executa; área mede o espaço físico ocupado no chip.

Essas grandezas precisam ser avaliadas juntas. Uma mudança pode reduzir a área e melhorar o desempenho, mas também pode afetar outra dimensão.

Fonte: <https://openai.com/index/advancing-chip-design-with-our-models/>

## As melhorias no Jalapeño

No Jalapeño, a unidade vetorial cuida de tarefas de computação paralela. As melhorias vieram de somadores e multiplicadores de ponto flutuante, funções de conversão, lógica de redução e uma unidade de função especial. Os modelos exploraram outras implementações de lógica e novas divisões do trabalho entre etapas do pipeline. Também encontraram oportunidades para compartilhar hardware e reduzir armazenamento intermediário.

Na unidade matricial, as melhorias se acumularam em somadores, multiplicadores e circuitos de produto interno de baixa precisão. Um multiplicador redesenhado usou cerca de 15% menos área de célula na síntese e reduziu a latência de dois ciclos de clock para um. Um somador separado reduziu a área em cerca de 15% e manteve a latência de dois ciclos.

Em toda a iniciativa do Jalapeño, a equipe estima que as mudanças propostas pelos modelos reduziram a área de células padrão em cerca de 13% na unidade vetorial e 10% na unidade matricial. A OpenAI afirma que essas otimizações foram comprovadas em silício durante o bring-up, a etapa de primeiros testes do chip.

Fonte: <https://openai.com/index/advancing-chip-design-with-our-models/>

## A colaboração com a AMD

Na colaboração com a AMD, o foco foram melhorias de PPA em hardware de terceiros. A OpenAI relata até 14% de melhoria em relação a linhas de base fortemente otimizadas na propriedade intelectual da GPU carro-chefe da AMD. O modelo reescreveu código SystemVerilog RTL que descreve os circuitos.

O modelo usou ferramentas da Synopsys para verificar se cada reescrita preservava o comportamento do bloco e avaliar os compromissos entre potência, desempenho e área. A OpenAI observou que o modelo raciocinava sobre RTL como um projetista especialista na estrutura interna de processadores. Parte das mudanças já entrou em um projeto enviado para fabricação; outras foram adicionadas aos arquivos de produção para versões futuras.

O recorte muda quando o assunto é a CPU. A AMD verificou ganhos percentuais de um dígito em PPA em blocos-chave de sua futura CPU carro-chefe de próxima geração. Já sobre o resultado na GPU, a OpenAI afirma que ele representa cerca de um ano de progresso alcançado em menos de 5 meses. O número de 14% pertence à GPU, e os ganhos da CPU têm outro recorte.

Fonte: <https://openai.com/index/advancing-chip-design-with-our-models/>

## Como funciona o teste RISC-V

Para medir a evolução entre gerações de modelos, a OpenAI testou dois núcleos RISC-V de 32 bits e de código aberto. O PicoRV32 é compacto e foi feito para FPGAs, chips reprogramáveis. O Ibex é o processador embarcado usado no chip de segurança OpenTitan. Cada um é um núcleo de processador completo para cargas de trabalho embarcadas, da classe dos microcontroladores.

A primeira tarefa dava ao modelo a descrição original do hardware e pedia mais throughput, ou seja, mais instruções executadas por segundo. Reduzir os ciclos de uma instrução não basta se cada ciclo ficar mais longo. A métrica de throughput considera os dois efeitos.

Cada saída passou por simulação. Um projeto recebia zero se falhasse em uma verificação ou usasse mais de 16 vezes a área do núcleo original. Nos projetos aprovados, a equipe mediu instruções por ciclo de clock em cargas ocultas. Calculou a média geométrica dessas cargas e multiplicou pela frequência máxima de clock estimada com Yosys para obter uma estimativa de instruções por segundo.

O melhor throughput observado para cada núcleo, sob as mesmas restrições, recebeu pontuação 1,0. Os gráficos mostram a média das execuções, incluindo as que tiraram zero. A comparação usa orçamentos de tokens, que medem a quantidade de texto processada, e não uma medida de tempo de execução.

Fonte: <https://openai.com/index/advancing-chip-design-with-our-models/>

## Otimizar um núcleo existente

Com orçamento comparável de cerca de 112.000 tokens por execução, o GPT-6.2 Astra teve a maior pontuação média nos dois núcleos. O GPT-6.1 Sol também superou o GPT-5.6 Sol nos dois.

No PicoRV32 existente, o GPT-6.2 Astra alcançou a maior média nos orçamentos maiores. Perto de 112.000 tokens, sua pontuação foi cerca de duas vezes a do GPT-6 Astra. A comparação é entre pontuações normalizadas daquele núcleo e daquele teste, não uma afirmação de que todo projeto ficou duas vezes mais rápido.

No Ibex existente, a média do GPT-6.2 Astra continuou subindo nos orçamentos mais altos alcançados. O GPT-6 Astra e o GPT-6.1 Sol ficaram mais próximos. O resultado depende do núcleo, do orçamento e das restrições usadas.

Fonte: <https://openai.com/index/advancing-chip-design-with-our-models/>

## Projetar um núcleo a partir de uma especificação

A segunda tarefa partia de requisitos escritos e de gabaritos tirados do código aberto que mostravam como o núcleo se conecta ao restante do sistema. O modelo escolhia como os dados circulariam e como dividiria o trabalho em etapas. As verificações de correção, as configurações de memória e cache e os objetivos de throughput foram mantidos iguais aos da tarefa de otimização.

Perto de 112.000 tokens por execução, os cinco modelos tiveram pontuação maior ao projetar do zero do que ao melhorar o desenho existente, tanto no PicoRV32 quanto no Ibex. O GPT-6.2 Astra ganhou mais no Ibex. A avaliação completa somou 9.881 execuções pontuadas entre as duas tarefas, os dois núcleos e todos os orçamentos.

Partindo da especificação do PicoRV32, o GPT-6.2 Astra passou da média 0,7 perto de 112.000 tokens e pontuou mais alto nos dois próximos orçamentos observados. No Ibex, a média foi cerca de 0,75 no mesmo ponto, e a curva permaneceu acima das outras em orçamentos maiores compartilhados.

Projetar a partir de requisitos permitiu omitir recursos presentes nos núcleos originais, como contadores de desempenho e instruções adicionais. Esses recursos podem contribuir pouco para o throughput nas cargas do teste, o que pode explicar parte da vantagem. Exigi-los, limitar mais a área e conferir os limites de tempo depois da síntese física tornaria a avaliação mais próxima de um projeto de chip de produção.

Fonte: <https://openai.com/index/advancing-chip-design-with-our-models/>

## Os números

- 5 agentes ativos: número informado pelo Codex na demonstração por voz; indica o estado da interface no momento da pergunta e não mede o trabalho feito na placa.
- Cerca de 15% menos área de célula: redução de um multiplicador no Jalapeño durante a síntese; a latência passou de dois ciclos de clock para um.
- Cerca de 15% menos área: redução de um somador separado no Jalapeño; a latência permaneceu em dois ciclos.
- 13% na unidade vetorial e 10% na unidade matricial: estimativa da equipe para a redução de área de células padrão no Jalapeño; a OpenAI informa que essas otimizações foram comprovadas em silício.
- Até 14% de melhoria de PPA: resultado da colaboração com a AMD na GPU carro-chefe, comparado a linhas de base fortemente otimizadas; não se aplica automaticamente à CPU.
- Ganhos percentuais de um dígito em PPA: o que a AMD verificou em blocos-chave da futura CPU carro-chefe; é um recorte diferente do resultado da GPU.
- Cerca de 112.000 tokens por execução: orçamento comparável usado nos testes RISC-V; tokens medem a quantidade de texto processada, não horas, preço ou número de peças.
- Mais de 16 vezes a área original: limite que zera a pontuação de um projeto RISC-V; funciona como restrição de área dentro da avaliação.
- Cerca de duas vezes a pontuação do GPT-6 Astra: comparação do GPT-6.2 Astra no PicoRV32 existente, perto de 112.000 tokens; a pontuação é normalizada pelo melhor resultado do mesmo núcleo.
- Acima de 0,7 no PicoRV32 e cerca de 0,75 no Ibex: médias do GPT-6.2 Astra ao projetar a partir da especificação, perto de 112.000 tokens; não são porcentagens nem instruções por segundo absolutas.
- 9.881 execuções pontuadas: total da avaliação completa nas duas tarefas, nos dois núcleos e em todos os orçamentos; mostra a amplitude do teste.
- Menos de 5 meses para cerca de um ano de progresso: estimativa apresentada na colaboração com a AMD; descreve aquele trabalho e não estabelece uma taxa universal.

Fonte: <https://openai.com/index/advancing-chip-design-with-our-models/>

## O que muda para você

Exemplo: uma equipe quer criar um dispositivo com uma placa própria. Ela começa escrevendo o que o dispositivo precisa fazer e reunindo os planos da placa. Em seguida, leva essa base ao modelo e compara mais de uma proposta de projeto.

Se houver carcaça, a equipe também pode testar versões diferentes antes de fechar a montagem. O retorno da fábrica orienta os ajustes. O resultado esperado é uma placa montada que passou pelas rodadas de fabricação, como no projeto apresentado.

Para um circuito integrado, o raciocínio é parecido, mas a validação muda. A equipe define o núcleo, simula as saídas e verifica área e throughput. Uma melhora em uma métrica precisa preservar as verificações de correção.

O hábito que vale levar é separar proposta de resultado comprovado. Um desenho gerado é uma candidata. A simulação e a fabricação fornecem evidências sobre ela. Essa separação impede de confundir uma resposta plausível com hardware que funciona.

Fonte: <https://openai.com/index/advancing-chip-design-with-our-models/>

## O que fazer hoje

O caminho abaixo reúne ações presentes nos projetos de placa e de chips. Ele começa pela definição do objeto e termina na validação do resultado.

1. Escreva o resultado físico desejado e reúna os planos ou requisitos disponíveis. Faça isso antes de enviar ao modelo; o resultado esperado é uma descrição clara que permita propor a placa ou o núcleo.
2. Apresente ao modelo o objetivo e os planos e peça o projeto. O resultado esperado é uma proposta inicial para avaliar.
3. Crie candidatos de projeto em paralelo e versões da carcaça quando houver carcaça. O resultado esperado é um conjunto de alternativas para comparar antes da escolha.
4. Para hardware físico, encaminhe a proposta à fabricação e use cada retorno para ajustar. O resultado esperado é chegar a uma placa montada depois das rodadas necessárias.
5. Para um núcleo RISC-V, simule a saída e confira as verificações de correção e o limite de área. O resultado esperado é aprovar ou descartar cada candidata antes de medir o desempenho.
6. Meça o throughput nas condições definidas e mantenha o registro do orçamento de tokens e das restrições. O resultado esperado é uma comparação que possa ser repetida e interpretada.

Fonte: <https://openai.com/index/advancing-chip-design-with-our-models/>

## O que conferir

Os resultados têm recortes diferentes. Para usá-los sem exagerar, acompanhe o hardware, a métrica, a comparação e a etapa de validação de cada número.

- A placa montada passou por ajustes com a fábrica. Trate o projeto como um ciclo de fabricação e revisão.
- Os cinco agentes ativos são o estado informado pelo Codex naquele momento. A contagem não representa a complexidade da placa nem o total de trabalho concluído.
- PPA reúne potência, desempenho e área. Uma melhora em uma dimensão precisa ser examinada junto das outras.
- O valor de até 14% pertence à colaboração com a AMD na GPU carro-chefe. Os ganhos da CPU foram de um dígito percentual em blocos-chave, e o Jalapeño tem estimativas próprias de área.
- As pontuações 1,0, 0,7 e 0,75 são normalizadas dentro da avaliação. Elas não são porcentagens nem medidas absolutas de velocidade.
- Projetar do zero permitiu omitir contadores de desempenho e instruções adicionais. Exigir esses recursos e apertar os limites de área muda o teste.
- As otimizações do Jalapeño foram comprovadas em silício. Os resultados RISC-V descritos vêm de simulação e de estimativas feitas com Yosys.
- Cerca de 112.000 tokens por execução é um orçamento de processamento. Esse valor não informa horas de trabalho, custo ou tempo de fabricação.
- O GPT-Synopsys é um novo modelo que a OpenAI está treinando em parceria com a Synopsys para usar ferramentas EDA. Ele faz parte dos próximos passos anunciados para o trabalho em chips.

Fonte: <https://openai.com/index/advancing-chip-design-with-our-models/>

## Glossário

- Agente: execução que usa um modelo para conduzir uma tarefa com ferramentas.
- Uso de computador: capacidade de o modelo interagir com um ambiente de software para executar ações.
- PCB: placa de circuito impresso que acomoda e liga componentes eletrônicos.
- Carcaça: invólucro externo que acomoda e protege a montagem da placa.
- Modelo de fronteira: modelo de IA com capacidades na linha de frente do desenvolvimento da empresa.
- Chip de inferência: chip dedicado a executar modelos de IA.
- PPA: potência, desempenho e área, as três dimensões acompanhadas nas melhorias de circuito.
- Pipeline: divisão do processamento em etapas que trabalham em sequência.
- Unidades vetorial e matricial: a vetorial executa tarefas de computação paralela; a matricial reúne circuitos aritméticos usados em operações de matriz.
- Célula padrão: bloco básico de circuito usado na implementação de um chip.
- Latência e ciclo de clock: latência é o tempo de espera medido em ciclos; um ciclo de clock é o intervalo de um pulso do relógio do circuito.
- Throughput e IPC: throughput é a quantidade de instruções executadas por segundo; IPC é a quantidade de instruções executadas por ciclo de clock.
- Média geométrica: forma de combinar resultados multiplicando-os e extraindo a raiz correspondente à quantidade de valores.
- RTL e SystemVerilog: RTL descreve um circuito em nível de registradores e transferências; SystemVerilog é a linguagem usada para escrever essa descrição no trabalho da OpenAI.
- Núcleos RISC-V, PicoRV32 e Ibex: são processadores compactos. O PicoRV32 foi feito para FPGAs; o Ibex é usado como processador embarcado no chip de segurança OpenTitan.
- Microcontrolador: processador compacto usado para controlar funções de um dispositivo.
- Token: unidade de texto processada pelo modelo; o orçamento de tokens limita a quantidade usada em uma execução.
- Simulação: execução de um modelo do circuito para verificar seu comportamento sem fabricar o chip.
- Síntese e síntese física: a síntese transforma a descrição do circuito em uma implementação com células e área; a síntese física considera também a disposição no chip.
- Yosys: ferramenta usada no teste para estimar a frequência máxima de clock a partir do projeto.
- FPGA: chip reprogramável que permite implementar diferentes circuitos.
- EDA: conjunto de ferramentas de automação usadas para projetar e verificar circuitos eletrônicos.
- IP de GPU: bloco de circuito de GPU tratado como propriedade intelectual.
- Bring-up: etapa de primeiros testes de um chip depois da fabricação.

Fonte: <https://openai.com/index/advancing-chip-design-with-our-models/>

## Para onde ir depois

A OpenAI também anunciou uma parceria com a Synopsys para treinar o GPT-Synopsys, um novo modelo, a usar ferramentas EDA como projetistas especialistas. O objetivo é integrar o modelo às ferramentas que engenheiros já usam para projetar e verificar chips.

Comece pelo projeto que você quer entender e mantenha o recorte de cada resultado ao estudar as fontes oficiais.

- Leia a documentação do Codex para conhecer a ferramenta usada no display: https://developers.openai.com/codex.
- Consulte a página do GPT-6 Astra para acompanhar o contexto do modelo: https://openai.com/index/gpt-6-astra/.
- Estude o artigo de projeto de chips e escolha uma comparação para explicar com suas palavras, mantendo o núcleo, o orçamento e as restrições: https://openai.com/index/advancing-chip-design-with-our-models/.
- Pratique o ciclo de definição, proposta e validação em um exemplo de placa. Depois, pratique a leitura de uma pontuação normalizada no teste RISC-V.
- Use o índice de pesquisa da OpenAI para localizar os outros trabalhos citados nesta apostila: https://openai.com/research/index/.

Fonte: <https://openai.com/research/index/>

## Links citados

- https://openai.com/index/expanding-chatgpt-for-academic-researchers/

## Além do vídeo

- A OpenAI anunciou a ampliação do ChatGPT for Academic Researchers, com a meta de dar acesso gratuito a até 200.000 pesquisadores no mundo. Para a rodada com inscrições previstas a partir de 23 de novembro de 2026, anunciou 50.000 novas bolsas por ordem de chegada entre os candidatos elegíveis, cada uma com ChatGPT Plus para o contemplado e até dois colaboradores.
- O piloto reuniu 20.000 pesquisadores em 33 países. Um estudo da OpenAI examinou como mais de 1.800 pesquisadores usaram o ChatGPT no piloto; os participantes consultados estimaram que, sem IA, o mesmo trabalho, na mesma qualidade, teria levado quase o dobro do tempo.
- A OpenAI publicou que modelos GPT-6 projetaram estruturas e sequências de proteínas usando raciocínio e código. Testes de laboratório encontraram evidência de ligação em cinco alvos.
- O MedChemBench avalia como modelos de IA interpretam estruturas moleculares, raciocinam sobre evidências experimentais e selecionam compostos na descoberta inicial de fármacos.
- O BioBasicsBench reúne 100 tarefas para medir como agentes de IA interpretam dados experimentais brutos e conduzem atividades cotidianas de ciência de laboratório.
- A OpenAI descreveu um pipeline autônomo que encontrou, validou e gerou correções para 948 vulnerabilidades locais de escalada de privilégio no kernel Linux.
- A pesquisa Research acceleration: the jagged frontier mede como agentes de código aceleram a pesquisa em IA e onde o desempenho deles permanece desigual.
- Outras frentes de acesso científico citadas pela OpenAI incluem o ChatGPT Edu para comunidades universitárias e o GPT-Rosalind, com raciocínio biológico especializado e acesso a ferramentas e bases científicas.
