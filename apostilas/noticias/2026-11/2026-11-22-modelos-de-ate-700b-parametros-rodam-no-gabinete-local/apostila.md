# Modelos de até 700B parâmetros rodam no gabinete local

_2026-11-22 · noticia_

Na SC26, a NVIDIA apresentou o DGX Spark HPC Developer Kit, um cluster de quatro sistemas DGX Spark que leva a experimentação científica e de IA para a mesa do pesquisador. A configuração em anel reúne 512 GB de memória e 16 TB de armazenamento NVMe e permite executar localmente modelos de até 700B parâmetros com NVFP4. Ao longo desta apostila, você vai entender a arquitetura, o papel do HPC SDK, os casos científicos já demonstrados e os limites de cada resultado. Também vai saber como separar experimentação local de produção, escolher um caminho de compra e interpretar os números antes de aplicá-los ao seu projeto.

## O fato

A NVIDIA anunciou na SC26, conferência anual de supercomputação realizada em Chicago, o DGX Spark HPC Developer Kit. O anúncio é dirigido a pesquisadores, acadêmicos e desenvolvedores que precisam construir e testar aplicações científicas, modelos e agentes de IA perto da própria equipe.

O kit reúne quatro sistemas DGX Spark. Cada um usa o GB10 Grace Blackwell Superchip, e os quatro nós são ligados diretamente pela rede NVIDIA ConnectX-7 em anel. A configuração dispensa a compra e a montagem de um switch de rede.

Além do hardware, a NVIDIA anunciou um playbook de instalação do HPC SDK, previsto para chegar em breve. O kit está em exposição na SC26 e já é oferecido para venda.

Fonte: <https://blogs.nvidia.com/blog/dgx-spark-hpc-developer-kit-sc26/>

## Por que isso importa

Em um cluster GPU compartilhado, cada tarefa pode esperar por uma janela de execução. Esse ritmo atrapalha quem está desenvolvendo código, ajustando uma simulação ou investigando um resultado. O kit oferece um ambiente local para essa etapa de experimentação.

Ao desenvolver e depurar no próprio gabinete, a equipe pode reservar as horas do servidor compartilhado para as rodadas de produção. Dados não publicados e conjuntos proprietários também podem permanecer nas instalações da organização.

O cluster compartilhado continua útil para produção e para cargas maiores. A proposta do DGX Spark Developer Kit é testar a distribuição do cálculo e da comunicação em até quatro nós antes de escalar.

Fonte: <https://blogs.nvidia.com/blog/dgx-spark-hpc-developer-kit-sc26/>

## Como o cluster de quatro nós funciona

Um nó é um sistema computacional completo. Neste kit, cada nó é um DGX Spark com GB10. O cluster cresce de um sistema até quatro, e a ligação em anel conecta cada nó aos dois vizinhos. Essa é a topologia usada para que os nós trabalhem em uma mesma carga distribuída.

Com NVIDIA ConnectX-7, os sistemas trocam dados diretamente. Como não há switch, a equipe evita esse equipamento e a respectiva configuração de rede. Isso simplifica a montagem do ambiente descrito para o kit.

A topologia em anel não elimina o trabalho de paralelizar a aplicação. Cálculo e dados ainda precisam ser divididos entre os nós, e a comunicação entre eles precisa ser testada. O playbook do HPC SDK pretende apoiar essa preparação antes da mudança para sistemas maiores.

Fonte: <https://blogs.nvidia.com/blog/dgx-spark-hpc-developer-kit-sc26/>

## Memória e armazenamento para dividir o trabalho

Nos quatro nós, o kit oferece 512 GB de memória combinada e 16 TB de armazenamento NVMe. A memória combinada é a soma da memória disponível nos quatro sistemas; os 16 TB também são o total da configuração de quatro nós.

A memória mantém os dados e as partes do modelo que estão em uso durante a execução. O armazenamento NVMe guarda os arquivos de entrada, os resultados e os demais arquivos de trabalho. Separar os dois ajuda a entender o que cada número representa.

Essa capacidade permite distribuir modelos e cargas científicas entre os nós. O ganho real depende de a aplicação conseguir dividir o trabalho e de o custo de comunicação não consumir o benefício. Mais memória somada não faz qualquer programa usar os quatro sistemas automaticamente.

Fonte: <https://blogs.nvidia.com/blog/dgx-spark-hpc-developer-kit-sc26/>

## Modelos de até 700B parâmetros no gabinete

Com NVFP4, a NVIDIA afirma que os quatro sistemas DGX Spark podem executar localmente modelos com até 700B parâmetros. O exemplo citado é o DeepSeek V4.1. Parâmetros são os valores numéricos que um modelo ajusta durante o treinamento; 700B significa 700 bilhões.

NVFP4 é uma forma de quantização. Ela reduz a precisão numérica usada para representar o modelo, o que ajuda a acomodar modelos grandes na memória disponível. O número de 700B é o limite divulgado para essa configuração de quatro nós com NVFP4.

Para o pesquisador, a execução local permite testar modelos sem esperar por uma alocação no cluster compartilhado. O limite de memória é apenas parte da conta: formato do modelo, divisão entre os nós e tipo de carga influenciam o que cabe e como a execução se comporta.

Fonte: <https://blogs.nvidia.com/blog/dgx-spark-hpc-developer-kit-sc26/>

## HPC SDK: do código científico ao cluster local

O playbook do NVIDIA HPC SDK está previsto para chegar em breve. Ele reúne compiladores com aceleração por GPU para C, C++ e Fortran, bibliotecas e ferramentas de passagem de mensagens. São as mesmas categorias de ferramentas usadas no desenvolvimento para supercomputadores com GPU NVIDIA, agora voltadas ao cluster local.

O SDK dá caminhos para escrever e adaptar código científico. Os compiladores C++ suportam C++17, incluindo paralelismo que pode ser enviado à GPU. O compilador Fortran suporta Fortran 2003 e vários recursos de Fortran 2008. CUDA e OpenACC oferecem formas de indicar paralelismo e aceleração, enquanto bibliotecas como cuBLAS, cuSOLVER, cuFFT e cuSPARSE atendem a operações de álgebra e transformadas.

A comunicação entre GPUs e nós aparece em NCCL, NVSHMEM e no MPI CUDA-aware baseado em Open MPI. O GPUDirect permite enviar e receber buffers de GPU por acesso remoto direto à memória. Essas peças importam quando a aplicação deixa de caber em um único sistema.

Para medir e corrigir gargalos, há Nsight Systems e Nsight Compute. A implantação pode usar contêineres com HPC Container Maker e NVIDIA Container Runtime, inclusive com Docker e Singularity. A página do SDK lista suporte a GPUs NVIDIA e CPUs Arm ou x86-64 executando Linux. A NVIDIA declara portabilidade para mais de 99% dos sistemas atuais da Top500 e cita mais de 200 adaptações de aplicações HPC iniciadas ou habilitadas com OpenACC. Esses números descrevem alcance das ferramentas, não desempenho deste kit em uma aplicação específica.

Fonte: <https://developer.nvidia.com/hpc-sdk>

## Simulações científicas já validadas

Entre as cargas demonstradas nos quatro sistemas estão LAMMPS com Kokkos para simulação de materiais e NAMD para dinâmica molecular. Simular significa calcular o comportamento de um sistema ao longo do tempo ou de condições definidas, em vez de depender apenas de experimentos físicos.

A comunidade mais ampla do DGX Spark validou GROMACS para dinâmica molecular, OpenFOAM para dinâmica de fluidos e WRF para modelagem do tempo. Também foram validados microsserviços NVIDIA NIM, como OpenFold3 e Boltz-2, para previsão de estruturas biomoleculares.

Os casos têm recortes diferentes. LAMMPS com Kokkos e NAMD aparecem como cargas demonstradas em quatro sistemas. GROMACS, OpenFOAM, WRF e os microsserviços aparecem como validações da comunidade mais ampla. Essa distinção evita tratar toda a lista como o mesmo teste de quatro nós.

Fonte: <https://blogs.nvidia.com/blog/dgx-spark-hpc-developer-kit-sc26/>

## IA para química, proteínas e genomas

Para ciências da vida e química, também se destacam um conjunto de dados aberto e receitas de pós-treinamento para o Nemotron 3.5 Super VL. A finalidade é ajudar pesquisadores a adaptar o modelo em fluxos científicos executados em infraestrutura que a organização controla.

Outro caminho é o ajuste fino do OpenFold3 no DGX Spark. O caso apresentado pelo OpenFold mostra como adaptar o modelo para melhorar a previsão de estruturas proteína-ligante, usada na descoberta de medicamentos. OpenFold3 e Boltz-2 também aparecem na lista de validações por microsserviços NVIDIA NIM.

Esses exemplos ligam IA e pesquisa experimental. O modelo ajuda a gerar uma previsão ou uma representação, e o cientista continua responsável por verificar se a configuração do experimento e a conclusão fazem sentido para o problema estudado.

Fonte: <https://blogs.nvidia.com/blog/dgx-spark-hpc-developer-kit-sc26/>

## Berkeley: fila menor, experimentos locais

No Rubin Lab, no IGI da University of California, Berkeley, pesquisadores usam um DGX Spark e o NVIDIA Evo 2 para prever características bacterianas a partir de sequências genômicas. A abordagem compara embeddings de modelos de linguagem genômica e de proteínas com baselines clássicas.

O caso relata a ausência de filas de 11 horas no cluster e resultados que chegaram 15 vezes mais cedo no DGX Spark. Esse resultado pertence ao fluxo de previsão de características bacterianas descrito nesse laboratório.

No Hartwig Group, também da UC Berkeley, o trabalho é outro. O grupo usa um DGX Spark para ajuste fino com LoRA no Nemotron 3 Super 120B-A12B, voltado à aprendizagem de máquina para química. Com quantização NVFP4, o laboratório acomodou um modelo da classe de 120B parâmetros em um único dispositivo, treinou uma cabeça de predição sobre valores experimentais e contornou filas de vários dias. O grupo relata rodadas contínuas de treinamento de 8 a 24 horas, uma após a outra.

Fonte: <https://blogs.nvidia.com/blog/dgx-spark-hpc-developer-kit-sc26/>

## Outros usos já testados

A Kvantify usa NVIDIA cuQuantum e relata simulações tensor-network de circuitos de química quântica com até 70 qubits e 975 gates em um único DGX Spark. O benchmark usa circuitos gerados para cálculos da energia do estado fundamental da penicilina. O recorte é um único sistema e esse tipo de circuito.

A CYRAN AI, empresa derivada do IIT Delhi, usa DGX Spark e a biblioteca PixelFlux para acelerar a decodificação JPEG 2000 de imagens de satélite grandes. O objetivo é permitir análise geoespacial local.

Os dois casos ampliam o uso do hardware além de modelos de linguagem. Um trabalha com simulação quântica e o outro com processamento de imagens. Cada resultado depende da aplicação e da configuração usada no teste.

Fonte: <https://blogs.nvidia.com/blog/dgx-spark-hpc-developer-kit-sc26/>

## Agentes e modelos para encurtar o caminho da simulação

Agentes podem ajudar a preparar entradas de simulação, iniciar execuções e resumir resultados. O cientista valida a configuração e as conclusões. Essa divisão de trabalho usa a IA para organizar tarefas repetitivas e mantém a decisão científica com a pessoa responsável.

Outra possibilidade é treinar modelos de IA que aproximam o comportamento de simulações lentas. Um modelo assim pode ser usado para explorar variações com mais agilidade e, por exemplo, refinar projetos de asas em direção ao arrasto mínimo. Ele funciona como um aproximador do comportamento simulado, sujeito à validação.

Antes de comprometer tempo de supercomputador, a equipe também pode selecionar as dimensões relevantes de uma simulação de 10 milhões de células e trabalhar com um recorte de 50 a 500 dimensões. A ideia é investigar o que mais importa para o problema antes de levar a carga completa à infraestrutura maior.

Fonte: <https://blogs.nvidia.com/blog/dgx-spark-hpc-developer-kit-sc26/>

## Os números

Cada número abaixo precisa ser lido com a configuração e o caso a que pertence. A soma de capacidade do hardware, o limite de um modelo e o resultado de um laboratório medem coisas diferentes.

- Quatro nós: é a configuração completa do kit, com cada sistema ligado diretamente aos dois vizinhos em anel; os totais de memória e armazenamento descritos a seguir se referem a esses quatro nós.
- 512 GB: é a memória combinada dos quatro sistemas, não a memória de um único nó; ela permite distribuir modelos e cargas entre o cluster.
- 16 TB: é o armazenamento NVMe total nos quatro nós, usado para os arquivos das cargas científicas e dos modelos.
- Até 700B parâmetros: é o limite divulgado para modelos executados localmente nos quatro sistemas com NVFP4, como o DeepSeek V4.1; não representa o tamanho de todo modelo.
- 10 milhões de células e 50 a 500 dimensões: selecionam-se as dimensões relevantes antes de comprometer tempo de supercomputador; isso não mede uma aceleração geral.
- 70 qubits e 975 gates: são os limites relatados pela Kvantify para simulações tensor-network em um único DGX Spark, com circuitos de química quântica gerados para cálculos com penicilina.
- 11 horas de fila e resultados 15 vezes mais cedo: o resultado pertence ao Rubin Lab, no fluxo de previsão de características bacterianas com NVIDIA Evo 2; não se aplica a toda aplicação científica.
- Nemotron 3 Super 120B-A12B em um único dispositivo: o Hartwig Group acomodou um modelo da classe de 120B parâmetros com NVFP4 e LoRA; é um caso diferente do limite de 700B nos quatro nós.
- Rodadas de 8 a 24 horas: o Hartwig Group relata treinamentos contínuos nessa faixa de duração, um após o outro, após contornar filas de vários dias.

Fonte: <https://blogs.nvidia.com/blog/dgx-spark-hpc-developer-kit-sc26/>

## O que muda para você

Exemplo: uma equipe de materiais precisa testar ajustes em uma simulação LAMMPS com Kokkos. No fluxo com cluster compartilhado, cada alteração pode ficar esperando por tempo de execução. Com o kit, a equipe prepara os testes no gabinete e distribui a carga entre os nós quando a aplicação permitir.

Se a equipe usar um agente, ele pode preparar as entradas, iniciar as rodadas e resumir os resultados. A pessoa responsável revisa a configuração e verifica se a conclusão corresponde ao experimento. Depois do teste local, a rodada de produção pode seguir para o sistema maior.

Esse fluxo aproveita a autonomia local e preserva o cluster compartilhado para a produção. O kit não garante que toda simulação caiba nos quatro nós; o limite de memória, o formato do modelo e a comunicação entre os sistemas continuam determinando o resultado.

Fonte: <https://blogs.nvidia.com/blog/dgx-spark-hpc-developer-kit-sc26/>

## Onde comprar e o que já está disponível

O DGX Spark Developer Kit está em exposição na SC26 e disponível para venda. Produtos e cabos DGX Spark podem ser comprados por parceiros OEM e pelo NVIDIA Marketplace.

A lista de parceiros inclui Acer, ASUS, Dell Technologies, GIGABYTE, H3C, HP, Lenovo, MSI e xFusion. O playbook de instalação do HPC SDK tem previsão de lançamento separada: no anúncio, ele ainda estava por vir. Para comprar, os canais indicados são os parceiros OEM e o NVIDIA Marketplace; a página oficial do produto serve para conhecer a oferta.

Fonte: <https://blogs.nvidia.com/blog/dgx-spark-hpc-developer-kit-sc26/>

## O que fazer hoje

Uma decisão de compra faz mais sentido depois de definir a carga e o fluxo de trabalho. O caminho abaixo usa os recursos e os casos descritos no anúncio para organizar o primeiro teste.

1. No planejamento do projeto, escolha uma aplicação de simulação, ajuste fino de modelo ou fluxo com agentes que hoje dependa do cluster compartilhado. O resultado esperado é um experimento claro para testar localmente.
2. Compare a aplicação com os casos descritos, como LAMMPS com Kokkos, NAMD, GROMACS, OpenFOAM ou WRF. O resultado esperado é identificar qual caminho de validação serve de referência para o seu caso.
3. Na página oficial do DGX Spark, avalie se o projeto começa em um sistema ou precisa dos quatro nós. O resultado esperado é definir a topologia e conferir se os 512 GB e os 16 TB correspondem à configuração de quatro nós.
4. No fluxo de desenvolvimento, separe uma etapa para construir, executar e depurar a aplicação entre os nós, incluindo a comunicação. O resultado esperado é encontrar problemas de distribuição antes de escalar.
5. Na escolha do fornecedor, use um parceiro OEM ou o NVIDIA Marketplace para adquirir os produtos e cabos. O resultado esperado é selecionar um canal oficial para o kit.
6. Na execução, reserve a validação humana para entradas, configurações e conclusões, sobretudo quando um agente participa. O resultado esperado é manter o cientista responsável pelo experimento.

Fonte: <https://www.nvidia.com/en-us/products/workstations/dgx-spark>

## O que conferir antes de decidir

O kit foi apresentado para experimentação local, e os resultados divulgados têm recortes específicos. Antes de usar um número para planejar capacidade ou prazo, associe-o ao modelo, à configuração e ao laboratório que o produziu.

A ausência de switch simplifica a rede do kit. A aplicação distribuída ainda precisa de paralelização e comunicação entre os nós. Além disso, o playbook do HPC SDK estava previsto para chegar depois do anúncio, então o desenvolvimento deve acompanhar a disponibilidade oficial desse playbook.

- O limite de 700B parâmetros vale para quatro sistemas com NVFP4; ele não descreve a capacidade de um único DGX Spark nem de qualquer formato de modelo.
- O resultado de 15 vezes mais cedo pertence ao Rubin Lab e ao fluxo de características bacterianas com NVIDIA Evo 2; ele não é uma medida geral de velocidade do kit.
- O modelo da classe de 120B parâmetros acomodado em um único dispositivo pertence ao Hartwig Group, com NVFP4 e ajuste fino LoRA; as rodadas de 8 a 24 horas também pertencem a esse caso.
- LAMMPS com Kokkos e NAMD foram demonstrados nos quatro sistemas; GROMACS, OpenFOAM, WRF e os microsserviços NIM aparecem como validações da comunidade mais ampla do DGX Spark.
- A página do HPC SDK lista suporte a GPUs NVIDIA e CPUs Arm ou x86-64 executando Linux; a portabilidade declarada para mais de 99% da Top500 não garante o mesmo desempenho em toda aplicação.
- O suporte técnico pago para os compiladores NVFORTRAN, NVC++ e NVC é uma oferta separada e exclui NVCC, segundo a página do SDK.
- A execução local ajuda a manter dados não publicados e proprietários nas instalações da organização; o controle do ambiente e a validação científica continuam sendo responsabilidades da equipe.
- Quando um agente prepara entradas, inicia execuções ou resume resultados, o cientista deve validar a configuração e as conclusões antes de usar o resultado na pesquisa.

Fonte: <https://developer.nvidia.com/hpc-sdk>

## Glossário

- Nó: um sistema computacional que participa do cluster.
- Cluster: conjunto de sistemas que trabalham juntos em uma carga computacional.
- Anel: topologia de rede em que cada nó se liga aos dois vizinhos.
- GB10 Grace Blackwell Superchip: chip da NVIDIA usado nos sistemas DGX Spark deste kit.
- GPU: processador especializado em executar muitas operações em paralelo.
- HPC: computação de alto desempenho, usada em simulações e cálculos científicos intensivos.
- Parâmetro: valor numérico ajustado pelo modelo durante o treinamento.
- Quantização: redução da precisão numérica usada para representar dados ou um modelo.
- NVFP4: formato de quantização citado para executar modelos grandes no DGX Spark.
- NVMe: interface de armazenamento usada nos 16 TB do kit.
- MPI: padrão para troca de mensagens entre processos em sistemas de memória distribuída.
- OpenACC: conjunto de diretrizes para indicar paralelismo e aceleração por GPU.
- CUDA: plataforma de programação paralela da NVIDIA para GPUs.
- Tensor Cores: unidades de processamento da NVIDIA voltadas a operações adequadas de precisão mista ou dupla.
- Embedding: representação numérica que permite comparar sequências, textos ou outros dados.
- LoRA: técnica de ajuste fino que adapta um modelo com treinamento adicional menor do que o treinamento completo.
- Qubit: unidade básica de informação quântica.
- Baseline: resultado ou método de referência usado para comparar uma nova abordagem.
- OEM: neste contexto, fabricante parceiro que vende sistemas DGX Spark na própria linha de produtos.
- NIM: família de microsserviços da NVIDIA usada para executar modelos.

## Para onde ir depois

A prática seguinte é escolher um caso pequeno o bastante para testar localmente e representativo do seu trabalho. O objetivo é aprender a distribuir a carga, medir a comunicação e validar os resultados antes de pedir uma rodada maior.

- Use a página oficial do DGX Spark para conhecer o produto, os parceiros e a configuração do kit. O próximo passo é decidir se um ou quatro nós atendem ao experimento.
- Acompanhe o playbook do HPC SDK na página oficial do SDK. Quando ele estiver disponível, use o material para preparar o desenvolvimento e a depuração no cluster local.
- Escolha uma aplicação entre LAMMPS com Kokkos, NAMD, GROMACS, OpenFOAM ou WRF para praticar um fluxo de simulação e validar o resultado com a equipe.
- Se o foco for IA, estude o ajuste fino com LoRA e a quantização NVFP4 descritos no caso de química da UC Berkeley. O próximo passo é aplicar o mesmo cuidado de recorte ao seu próprio modelo.
- Reserve o cluster compartilhado para as rodadas de produção depois que o experimento local estiver validado. Isso mantém o fluxo de pesquisa sem transformar toda execução em uma espera por alocação.

Fonte: <https://www.nvidia.com/en-us/products/workstations/dgx-spark>

## Links citados

- https://marketplace.nvidia.com/
- https://www.gromacs.org/
- https://www.ks.uiuc.edu/Research/namd/
- https://www.lammps.org/
- https://www.openfoam.com/
