# Tencent libera pesos do Hy4 flash para uso local

_2026-11-19 · noticia_

A Tencent liberou os pesos do Hy4 flash para implantação local dois dias depois de lançar o modelo por aplicativos e API em nuvem. São cerca de 220 bilhões de parâmetros no total, com cerca de 12 bilhões ativados por token, além de entrada por texto e imagem e janela de contexto de até 1 milhão de tokens. A publicação inclui o Hy4 flash, o Hy4 flash-FP8 e o Hy4 flash-base sob a licença Tencent Hy, com materiais de implantação. Ao terminar a leitura, você vai entender as diferenças entre as versões, o significado dos números e como avaliar uma implantação local. Também vai saber quais documentos oficiais abrir, o que conferir antes de baixar e como montar um teste de comparação.

## O fato

A Tencent liberou os pesos do Hy4 flash para implantação local na quarta-feira, dois dias depois de lançar o modelo por aplicativos e API em nuvem. A publicação cumpre o anúncio anterior da empresa de disponibilizar os pesos e veio acompanhada de materiais de implantação.

Desenvolvedores podem baixar o Hy4 flash, o Hy4 flash-FP8 e o Hy4 flash-base. As três versões estão sob a licença Tencent Hy, e os pesos do Hy4 flash foram publicados em https://huggingface.co/tencent/Hy4-flash.

O modelo aceita entradas de texto e imagem, tem janela de contexto de até 1 milhão de tokens e mira pesquisa, preparação de documentos e trabalho com planilhas. Esses elementos tornam o lançamento relevante para quem quer avaliar o Hy4 flash em um ambiente próprio.

Fonte: <https://github.com/Tencent-Hunyuan/Hy4-flash>

## Por que isso importa

Pesos são os valores numéricos aprendidos durante o treinamento de um modelo. Eles carregam o comportamento do modelo e permitem que ele seja carregado em um ambiente de execução. Liberar esses arquivos acrescenta um caminho de acesso: o desenvolvedor pode hospedar o Hy4 flash por conta própria.

O lançamento por aplicativos e API em nuvem é a outra forma de acesso descrita. Com os pesos disponíveis, quem desenvolve pode baixar o modelo, escolher onde executá-lo e avaliar adaptações. Isso interessa tanto a quem quer fazer um teste local quanto a quem pretende preparar uma implantação própria.

Implantação local descreve onde o modelo roda. Ela dá mais controle sobre a infraestrutura escolhida, mas custo e desempenho dependem da configuração usada. O porte do modelo e os requisitos de execução precisam entrar na decisão.

Fonte: <https://github.com/Tencent-Hunyuan/Hy4-flash>

## As três versões liberadas

A Tencent publicou três versões sob a licença Tencent Hy. A escolha entre elas depende do objetivo: executar o modelo publicado, avaliar uma variante em formato FP8 ou começar um trabalho de treinamento adicional.

FP8 é um formato de ponto flutuante de 8 bits usado para representar valores com precisão reduzida. Formatos desse tipo podem reduzir exigências de armazenamento e processamento, mas eventuais diferenças de qualidade e compatibilidade precisam ser testadas na configuração escolhida.

- Hy4 flash: é a versão padrão publicada e serve como ponto de partida para baixar os pesos e avaliar o modelo.
- Hy4 flash-FP8: é a variante FP8, indicada para quem quer testar esse formato no próprio ambiente antes de adotá-lo.
- Hy4 flash-base: é o modelo base apresentado para treinamento adicional, destinado a quem quer continuar o ajuste do modelo para um objetivo definido.

Fonte: <https://github.com/Tencent-Hunyuan/Hy4-flash>

## Entrada por texto e imagem

O Hy4 flash aceita entradas de texto e de imagem. Isso permite colocar no teste diferentes tipos de conteúdo, em vez de limitar a avaliação a material escrito. O anúncio posiciona o modelo para tarefas de produtividade, com foco em pesquisa, preparação de documentos e trabalho com planilhas.

Para aprender a usar essa capacidade, escolha uma tarefa cujo resultado você consiga conferir. Uma pesquisa pode começar com um trecho escrito, e uma imagem pode ser usada como entrada em um teste separado. Observe o que o modelo retorna e relacione cada resposta ao que foi apresentado.

Exemplo: Imagine que você precisa organizar uma pesquisa e recebeu um documento com trechos de referência. Você pode usar o texto como entrada, anotar os pontos que o modelo identificou e conferir cada um no documento. Depois, pode testar uma imagem de referência e verificar se a resposta descreve apenas o que está visível. Esse procedimento ajuda a medir utilidade e erros sem presumir um resultado.

Fonte: <https://github.com/Tencent-Hunyuan/Hy4-flash>

## Parâmetros e ativação por token

Parâmetros são os valores ajustáveis que um modelo usa no processamento. O total de parâmetros indica a dimensão do modelo, mas não mostra quantos desses valores participam de cada etapa. Por isso, tamanho total e quantidade de trabalho por token são medidas diferentes.

O Hy4 flash tem cerca de 220 bilhões de parâmetros no total e cerca de 12 bilhões ativados por token. O segundo número descreve a parcela acionada no processamento de cada token. Ele ajuda a explicar por que um modelo com muitos parâmetros pode manter custo de uso relativamente baixo.

Esse número sustenta uma expectativa de custo menor, mas não define o orçamento de uma implantação local. Memória, processamento, duração das tarefas e infraestrutura também entram na conta. A qualidade da resposta também precisa ser avaliada separadamente.

Fonte: <https://github.com/Tencent-Hunyuan/Hy4-flash>

## Janela de contexto de até 1 milhão de tokens

Token é uma unidade usada no processamento de texto. Ele pode representar uma palavra inteira ou uma parte dela, por isso a contagem de tokens não equivale diretamente à contagem de palavras. A janela de contexto é o limite de tokens que o modelo consegue considerar em uma interação.

O Hy4 flash tem uma janela de contexto de até 1 milhão de tokens. O termo até indica o máximo declarado. Uma janela maior permite incluir mais informação na mesma solicitação, o que pode ajudar em pesquisas e documentos extensos.

O limite de contexto não garante que toda essa extensão será usada em cada tarefa. Também não comprova qualidade automática em todas as respostas. Para testar, comece com um material que você conhece, aumente o volume aos poucos e verifique se o modelo mantém os pontos importantes e evita conclusões sem apoio no conteúdo.

Fonte: <https://github.com/Tencent-Hunyuan/Hy4-flash>

## Materiais de implantação e execução local

Materiais de implantação são os recursos publicados para orientar a preparação do ambiente e a colocação do modelo em funcionamento. A Tencent publicou esses materiais junto com os pesos, sob a licença Tencent Hy.

Uma implantação local reúne os pesos, o ambiente de execução e a forma de disponibilizar o modelo para a tarefa. Os materiais publicados servem para reduzir a distância entre baixar os arquivos e executar o Hy4 flash. Quem vai montar o ambiente deve seguir as orientações do projeto e conferir os requisitos antes de começar.

Para uma adaptação, o Hy4 flash-base é a versão apresentada para treinamento adicional. O trabalho exige um objetivo claro e uma forma de avaliar o resultado. Baixar uma versão e ajustar outra são caminhos distintos, por isso a escolha deve acontecer antes da configuração.

Fonte: <https://github.com/Tencent-Hunyuan/Hy4-flash>

## Os números

Os números do anúncio descrevem porte, processamento, capacidade de contexto e velocidade de disponibilização. Cada um responde a uma pergunta diferente.

- Cerca de 220 bilhões de parâmetros no total: indica a dimensão do Hy4 flash. Esse valor não informa, sozinho, a memória necessária nem o tempo de execução.
- Cerca de 12 bilhões ativados por token: indica a parcela de parâmetros usada no processamento de cada token. O valor não mede a qualidade das respostas nem calcula o custo total da implantação.
- Até 1 milhão de tokens de contexto: é o limite máximo declarado para a janela de contexto. O valor não equivale a 1 milhão de palavras nem garante desempenho em toda essa extensão.
- Dois dias entre o lançamento por aplicativos e API e a liberação dos pesos: mostra a rapidez desta disponibilização. O intervalo não estabelece um prazo para futuros lançamentos.
- Três versões publicadas: Hy4 flash, Hy4 flash-FP8 e Hy4 flash-base. A quantidade indica opções de formato e de ponto de partida para uso ou treinamento adicional.

Fonte: <https://github.com/Tencent-Hunyuan/Hy4-flash>

## O que muda para você

Quem já conhecia o acesso por aplicativos e API agora tem mais um caminho para avaliar o Hy4 flash. Os pesos permitem que desenvolvedores preparem uma execução local e trabalhem a hospedagem por conta própria. Isso muda quem controla o ambiente e como a adaptação pode ser conduzida.

Para uma pessoa que está começando, o melhor uso do lançamento é montar uma avaliação com uma tarefa conhecida. Pesquisa, documento e planilha são os exemplos de trabalho citados no anúncio. A comparação deve considerar qualidade da resposta, recursos usados e esforço de configuração.

Exemplo: uma equipe recebe um documento de referência e quer testar o modelo em uma tarefa de revisão. Ela pode preparar o mesmo documento no fluxo baseado em API e em uma execução local, aplicar os mesmos critérios de conferência e registrar as diferenças. O exemplo não presume que uma variante vença; ele mostra como tomar uma decisão com evidência do próprio caso.

Fonte: <https://github.com/Tencent-Hunyuan/Hy4-flash>

## O que fazer hoje

Comece pela documentação oficial e deixe a escolha da versão para depois de definir a tarefa. O caminho abaixo organiza a primeira avaliação sem exigir um comando específico de instalação.

1. Abra o repositório oficial em https://github.com/Tencent-Hunyuan/Hy4-flash e localize a visão geral do modelo e os materiais de implantação. O resultado esperado é identificar as versões publicadas e o caminho de configuração indicado pela Tencent.
2. Leia a licença Tencent Hy antes de baixar ou adaptar o modelo. O resultado esperado é registrar as condições que se aplicam ao uso escolhido.
3. Compare o Hy4 flash, o Hy4 flash-FP8 e o Hy4 flash-base conforme seu objetivo: executar a versão padrão, avaliar uma variante FP8 ou começar treinamento adicional. O resultado esperado é escolher uma versão com uma justificativa clara.
4. Baixe os pesos em https://huggingface.co/tencent/Hy4-flash e siga os materiais de implantação do repositório. O resultado esperado é reunir os arquivos e as instruções no ambiente de trabalho.
5. Prepare uma tarefa de pesquisa, documento ou planilha que você já saiba conferir. O resultado esperado é ter um caso de teste com critérios objetivos de checagem.
6. Execute o teste e compare o resultado com o fluxo que você já usa, considerando qualidade, tempo e recursos. O resultado esperado é uma decisão baseada no seu caso, além do porte do modelo.

Fonte: <https://github.com/Tencent-Hunyuan/Hy4-flash>

## O que conferir

O tamanho do Hy4 flash torna os requisitos de execução um ponto central da avaliação. Ter os pesos disponíveis não significa que qualquer computador consiga rodá-los. Antes de instalar, confira os requisitos de memória, processamento e compatibilidade indicados nos materiais de implantação.

A licença e a versão também mudam o que você pode fazer. O uso do modelo publicado, a avaliação do FP8 e o treinamento adicional têm objetivos diferentes. A escolha precisa combinar com a tarefa e com as condições da licença.

- Licença: leia a Tencent Hy e identifique as condições de uso, modificação e distribuição que se aplicam ao seu projeto.
- Hardware: confira requisitos de memória e processamento antes de baixar ou configurar o ambiente.
- Versão: relacione cada opção ao seu objetivo para evitar começar com um modelo base quando você quer apenas testar a versão padrão.
- FP8: avalie compatibilidade e qualidade no seu ambiente. A sigla, sozinha, não comprova economia de memória ou velocidade na sua configuração.
- Contexto: teste o volume de material que a tarefa realmente exige. O máximo de 1 milhão de tokens não precisa ser usado em toda solicitação.
- Treinamento adicional: defina o objetivo e a forma de medir o resultado antes de trabalhar sobre o Hy4 flash-base.
- Custos: compare infraestrutura, tempo de execução e manutenção com o fluxo por API antes de concluir qual caminho é mais barato.
- Respostas: revise fatos, cálculos e conclusões geradas, principalmente quando a entrada vier de documentos extensos ou imagens.

Fonte: <https://github.com/Tencent-Hunyuan/Hy4-flash>

## Glossário

- Pesos: valores numéricos aprendidos durante o treinamento que carregam o comportamento do modelo e permitem carregá-lo para execução.
- Parâmetro: cada um dos valores ajustáveis usados pelo modelo no processamento. O total descreve a dimensão do modelo.
- Token: unidade de processamento de texto que pode representar uma palavra inteira ou uma parte dela.
- Ativação por token: quantidade de parâmetros usada no processamento de um token.
- FP8: formato de ponto flutuante de 8 bits usado para representar valores com precisão reduzida.
- Modelo base: versão usada como ponto de partida para treinamento adicional.
- Janela de contexto: limite de tokens que o modelo consegue considerar em uma interação.
- API: interface de programação que permite a um aplicativo enviar solicitações e receber respostas de um serviço ou modelo.
- Implantação local: execução do modelo em um ambiente de infraestrutura própria ou escolhido por quem hospeda.
- Licença Tencent Hy: licença anunciada para as versões do Hy4 flash e para os materiais de implantação publicados pela Tencent.
- Treinamento adicional: processo de continuar ajustando um modelo a partir de uma base para atingir um objetivo definido.

## Para onde ir depois

O próximo passo é transformar a leitura em uma avaliação pequena e verificável. Escolha uma tarefa que você já domina, defina como conferir a resposta e teste uma versão do Hy4 flash. Depois, compare o resultado com o acesso por aplicativo ou API.

- Abra o repositório oficial para consultar o projeto e os materiais de implantação: https://github.com/Tencent-Hunyuan/Hy4-flash.
- Acesse a página dos pesos no Hugging Face para localizar as versões publicadas: https://huggingface.co/tencent/Hy4-flash.
- Consulte a página oficial do produto para acompanhar as informações do Hy4 flash: https://hy.tencent.ai/research/hy4-flash.
- Pratique com uma pesquisa, um documento ou uma planilha cujo resultado você consiga revisar. Registre a versão usada, o material de entrada, os recursos necessários e os erros encontrados.

Fonte: <https://github.com/Tencent-Hunyuan/Hy4-flash>

## Além do vídeo

- Os pesos também foram publicados no ModelScope: https://modelscope.cn/models/Tencent-Hunyuan/Hy4-flash.
- Os pesos também foram publicados no GitCode: https://ai.gitcode.com/tencent_hunyuan/Hy4-flash.
