# DeepMind acha 2 falhas em RSA de 1024 bits com agentes de IA

_2026-11-17 · noticia_

Esta apostila explica como agentes de IA, com supervisão humana, encontraram duas fraquezas em sistemas legados baseados em RSA de 1024 bits e por que os protocolos modernos com chaves de 2048 bits ou mais seguem seguros depois desta pesquisa. Você vai entender o papel das assinaturas digitais e do padding, o efeito de controlar parte de um bloco assinado e como a fatoração em lote divide custos entre várias chaves. Também vai aprender a separar estimativas teóricas de testes em simulação e a verificar o tamanho de chaves em certificados TLS e chaves SSH. Ao final, terá um caminho para reconhecer sistemas legados e interpretar os números sem confundir um ganho estimado com um ataque executado na prática.

## O fato

Em 6 de novembro de 2026, o Google DeepMind divulgou uma pesquisa com dois artigos técnicos sobre criptanálise. A equipe usou agentes de IA com supervisão humana para investigar sistemas legados baseados em RSA de 1024 bits. O resultado foi a descoberta de duas fraquezas que podem comprometer esses sistemas com um orçamento computacional menor do que se supunha.

Um artigo trata de assinaturas digitais e do padding acrescentado antes da assinatura. O outro trata da fatoração de muitas chaves do mesmo tamanho. O trabalho reúne a equipe de ciência do Google DeepMind e colaboradores da UC San Diego e do Inria.

A delimitação do anúncio é importante: os resultados afetam sistemas obsoletos com RSA de 1024 bits. Protocolos modernos com chaves de 2048 bits ou mais seguem seguros depois desta pesquisa. Essa condição acompanha cada resultado descrito nesta apostila.

Fonte: <https://x.com/pushmeet/status/2118752095859794390>

## Por que isso importa

A segurança discutida na pesquisa depende de dureza computacional, isto é, da existência de problemas fáceis de montar e difíceis de resolver dentro de um orçamento de processamento. No RSA, multiplicar dois números primos grandes é fácil. Recuperar esses primos a partir do produto, processo chamado de fatoração, é computacionalmente muito mais difícil.

Durante décadas, sistemas como o RSA se apoiaram nessa dificuldade. A comunidade de criptanálise testa essas suposições para que os padrões de segurança fiquem à frente de possíveis ameaças. Sistemas aposentados, como o RSA de 1024 bits, servem como campos de prova para esse trabalho porque já não representam o padrão moderno.

Historicamente, avanços desse tipo levavam anos ou décadas. Os defensores podiam tratar as margens de segurança como algo que mudava devagar. A pesquisa mostra que agentes de IA podem investigar essas suposições com mais rapidez. Comunicações criptografadas e moedas digitais estão entre os usos de sistemas que dependem dessa dureza, por isso o teste antecipado de hipóteses matemáticas tem valor prático.

Fonte: <https://x.com/pushmeet/status/2118752095859794390>

## Assinaturas digitais: o que está sendo protegido

Uma assinatura digital permite verificar que uma mensagem é autêntica e veio da fonte indicada. Essa mensagem pode ser uma atualização de software, um documento ou um site. Quando o sistema confirma a assinatura, está avaliando a autenticidade dos dados apresentados.

Muitos padrões de assinatura acrescentam dados predefinidos, chamados de padding, para completar a mensagem e formar um bloco de tamanho fixo. Esse preenchimento ajuda a impedir falsificações. A pesquisa examina quanto dessa proteção sobra quando um atacante consegue enviar entradas escolhidas a um dispositivo que assina mensagens.

A pergunta central é a parcela do bloco assinado que o atacante controla. O tamanho da chave continua sendo o recorte do estudo, mas a proteção do padding também depende dessa parcela controlada. Por isso, o resultado sobre assinaturas precisa ser lido junto com a condição em que o ataque foi analisado.

Fonte: <https://storage.googleapis.com/deepmind-media/papers/Faster_Affine_Root_and_a_1024bit%20Computation.pdf>

## A primeira fraqueza: o controle do bloco assinado

O padding transforma a mensagem em um bloco de tamanho fixo antes da assinatura. Quando o atacante controla uma parte pequena desse bloco, ainda existe trabalho matemático a mais para tentar falsificar a assinatura. A pesquisa mede essa proteção conforme cresce o controle do atacante sobre o conteúdo.

Os autores chegaram a um limite claro: quando o atacante controla cerca de metade do bloco ou mais, o padding deixa de acrescentar proteção. Nesse cenário, falsificar a assinatura fica tão vulnerável a atalhos matemáticos quanto no caso em que não haveria padding.

Exemplo: Imagine que um atacante consiga escolher as entradas enviadas a um dispositivo que assina mensagens. A pesquisa considera quanta parte do bloco final essas escolhas permitem controlar. Cerca de metade ou mais basta para retirar a proteção adicional do padding no cenário estudado. A conclusão depende desse controle e das entradas escolhidas; ela não se aplica automaticamente a toda assinatura digital.

Fonte: <https://storage.googleapis.com/deepmind-media/papers/Faster_Affine_Root_and_a_1024bit%20Computation.pdf>

## O teste em simulação: reprodução de um resultado conhecido

Para testar o resultado sobre assinaturas, os agentes trabalharam em uma simulação em ambiente isolado, sem acesso a sistemas ativos. Eles usaram uma chave de referência de 1024 bits de um estudo acadêmico anterior. Essa chave já tinha sido resolvida antes, então o experimento tratou da reprodução do resultado com uma implementação construída pelos agentes.

Nessa reprodução, o tempo de CPU foi 3,5 vezes menor. Os agentes também usaram menos de um milésimo do poder computacional necessário para quebrar a própria chave. São duas comparações diferentes: uma com o tempo de processamento do trabalho anterior e outra com o custo de quebrar a chave em si.

Na chave de referência, o trabalho consumiu 391 anos-núcleo em 3,2 dias. Anos-núcleo expressam a soma do tempo de processamento, enquanto os dias indicam a duração da simulação. Esses valores descrevem o experimento realizado; não são uma previsão de quanto tempo um ataque levaria em um computador pessoal.

Fonte: <https://storage.googleapis.com/deepmind-media/papers/Faster_Affine_Root_and_a_1024bit%20Computation.pdf>

## O resultado teórico com resumo de 32 bytes

Quando o atacante controla menos do bloco, como no caso de um resumo digital curto, falsificar a assinatura continua mais difícil. A pesquisa usa o exemplo de uma impressão digital da mensagem com 32 bytes. Nessa condição, os autores encontraram um algoritmo novo.

Segundo as estimativas teóricas deles, o algoritmo melhora o melhor método anterior em cerca de 1.600 vezes para chaves de 1024 bits. O número representa um ganho de eficiência no método para esse cenário específico. Ele foi estimado pelos autores e não foi executado na prática.

O valor de 1.600 vezes precisa permanecer acompanhado do tamanho do resumo, do tamanho da chave e da natureza teórica da estimativa. A conclusão não é que qualquer assinatura possa ser falsificada com esse ganho. Ela indica um caminho matemático mais eficiente sob as condições analisadas.

Fonte: <https://storage.googleapis.com/deepmind-media/papers/Faster_Affine_Root_and_a_1024bit%20Computation.pdf>

## A segunda fraqueza: fatoração em lote

O segundo resultado trata de fatorar muitos números do mesmo tamanho. Isso interessa ao RSA porque chaves costumam compartilhar comprimentos padrão, como 1024 ou 2048 bits. Quando várias chaves estão no mesmo lote, o atacante pode dividir um cálculo inicial grande entre todas elas.

Na teoria, uma pré-computação inicial prepara parte do trabalho. Depois dela, cada chave adicional pode exigir menos processamento do que exigiria isoladamente. O custo médio por chave cai porque a despesa inicial é distribuída pelo lote.

Exemplo: Imagine que um grande cálculo inicial possa ser reaproveitado em várias chaves do mesmo tamanho. Esse trabalho é feito uma vez e beneficia o conjunto. É por isso que o custo de cada chave adicional pode diminuir, embora a conta inicial continue existindo.

Fonte: <https://storage.googleapis.com/deepmind-media/papers/Fan_Factories_Multiple_Number_Fields_in_Factorization_Factories_and_Batch_NFS.pdf>

## O que os 30 vezes significam

Os agentes descobriram um algoritmo com complexidade assintótica melhor do que os métodos anteriores conhecidos. Em comparação com métodos de fatoração em lote, ele reduz em cerca de 30 vezes o custo médio teórico de fatorar cada chave adicional de 1024 bits.

A comparação inclui uma pré-computação inicial equivalente a uma fatoração completa. O ganho de 30 vezes se refere ao custo médio das chaves adicionais, depois desse preparo. Ele não elimina o custo inicial nem descreve o custo total de um lote inteiro.

O método ainda não foi implementado na prática, e a tabela de pré-computação não foi construída. O resultado é teórico e permanece no recorte de chaves adicionais de 1024 bits processadas em lote. Estender o número para uma única chave ou para chaves de 2048 bits mudaria as condições da análise.

Fonte: <https://storage.googleapis.com/deepmind-media/papers/Fan_Factories_Multiple_Number_Fields_in_Factorization_Factories_and_Batch_NFS.pdf>

## Os números

Cada número da pesquisa mede uma coisa específica. Ler a unidade, a comparação e a condição evita transformar um resultado limitado em uma conclusão geral.

- 1.600 vezes: melhora estimada no melhor método anterior para falsificar assinaturas com resumo de 32 bytes em chaves de 1024 bits; é uma estimativa teórica, não uma execução prática.
- 32 bytes: tamanho do resumo digital curto usado no cenário teórico das assinaturas; não é o tamanho total da mensagem nem da chave.
- 3,5 vezes: redução do tempo de CPU na reprodução, em simulação, de um resultado já obtido em uma chave de referência de 1024 bits.
- 391 anos-núcleo: soma do tempo de processamento usado nessa reprodução; não correspondem a 391 anos de duração real.
- 3,2 dias: duração da simulação que consumiu 391 anos-núcleo; não indicam o tempo de ataque em um computador comum.
- Menos de um milésimo: fração do poder computacional necessário para quebrar a própria chave, usada pelos agentes na reprodução do resultado.
- 30 vezes: redução do custo médio teórico de cada chave adicional de 1024 bits em lote, comparada aos métodos anteriores de lote e após uma pré-computação inicial.
- Cerca de metade: parcela do bloco assinado que, quando controlada pelo atacante ou superada, retira a proteção adicional do padding no cenário estudado.
- 1024 e 2048 bits: tamanhos de chave que separam o grupo legado afetado na prática do grupo de protocolos modernos que seguem seguros depois desta pesquisa.

Fonte: <https://x.com/pushmeet/status/2118752095859794390>

## O que muda para você

Na prática, a pesquisa direciona a atenção para sistemas legados com RSA de 1024 bits. Protocolos modernos com chaves de 2048 bits ou mais seguem seguros no recorte deste trabalho. Quem administra certificados ou chaves pode usar essa diferença para separar o que merece revisão do que permanece no padrão moderno citado.

A atitude prática é verificar o tipo e o tamanho das chaves sob sua responsabilidade. A leitura não executa um ataque. Ela fornece a informação necessária para identificar itens legados e tratar a pesquisa como um estímulo à revisão preventiva.

Exemplo: Imagine que uma equipe administre um site com certificado TLS e uma chave SSH. Se a leitura do certificado mostrar RSA de 1024 bits, esse item entra no grupo legado descrito pela pesquisa e merece atenção. Se mostrar RSA de 2048 bits ou mais, permanece no grupo dos protocolos modernos citados. A mesma comparação pode ser feita na chave SSH.

Fonte: <https://x.com/pushmeet/status/2118752095859794390>

## O que fazer hoje

A verificação começa pelos arquivos de certificados TLS e chaves SSH que você administra. Os dois comandos abaixo leem essas informações e permitem localizar o tamanho da chave.

1. Reúna os certificados TLS e as chaves SSH sob sua responsabilidade. O resultado é uma lista de arquivos para conferir, incluindo o arquivo certificado.crt usado no primeiro comando.
2. No terminal, execute o comando da seção sobre certificados TLS apontando para o certificado que está sendo verificado. O resultado esperado é uma saída com a linha Public-Key, que mostra o tamanho da chave em bits.
3. No terminal, execute o comando da seção sobre chaves SSH para o arquivo de chave pública indicado. O resultado esperado é a informação do tamanho da chave SSH.
4. Confirme que a chave é RSA (a linha filtrada do certificado pode não informar o algoritmo) e compare o número de bits de cada saída com o recorte da pesquisa. O resultado é a separação entre itens RSA de 1024 bits, que entram no grupo legado, e itens RSA de 2048 bits ou mais, que permanecem no grupo moderno citado.
5. Registre os itens RSA de 1024 bits para revisão de segurança. O resultado é uma lista concreta do que merece atenção, sem tratar uma estimativa teórica como evidência de comprometimento.

## Verificar a chave de um certificado TLS

No terminal, execute o comando abaixo no diretório em que está o arquivo certificado.crt. Ele lê o certificado e filtra a saída para a linha Public-Key, que permite conferir o tamanho da chave.

Use o número de bits dessa linha para aplicar o recorte da pesquisa. Um certificado com chave RSA de 1024 bits cai no grupo legado; um com RSA de 2048 bits ou mais fica no grupo dos protocolos modernos citados no anúncio. O comando faz a leitura do arquivo e não testa um ataque.

```
openssl x509 -in certificado.crt -text -noout | grep "Public-Key"
```

Fonte: <https://docs.openssl.org/3.1/man1/openssl-x509/>

## Verificar o tamanho de uma chave SSH

No terminal, execute o comando abaixo para ler a chave pública indicada em ~/.ssh/id_rsa.pub. O resultado esperado é a informação do tamanho da chave SSH.

Confira o valor em bits para identificar se a chave está no grupo legado de 1024 bits ou no grupo de 2048 bits ou mais. O caminho do comando aponta para o arquivo id_rsa.pub; a verificação usa exatamente esse arquivo.

```
ssh-keygen -l -f ~/.ssh/id_rsa.pub
```

Fonte: <https://man7.org/linux/man-pages/man1/ssh-keygen.1.html>

## O que conferir

Os resultados têm limites que mudam a interpretação. Confira essas condições antes de usar os números para tomar uma decisão.

- Confira o algoritmo antes do tamanho: o recorte da pesquisa é sobre RSA. Uma chave de 1024 bits de outro tipo não entra automaticamente nas conclusões sobre RSA.
- No caso do resumo de 32 bytes, mantenha o ganho de 1.600 vezes acompanhado da condição e da estimativa teórica. O valor não descreve uma execução prática nem outro tamanho de resumo.
- No caso do bloco assinado, a perda da proteção do padding depende de o atacante controlar cerca de metade do bloco ou mais e conseguir alimentar o dispositivo de assinatura com entradas escolhidas.
- Na simulação, diferencie a reprodução de um resultado conhecido da descoberta de uma nova quebra. A chave de referência de 1024 bits já tinha sido resolvida em estudo anterior.
- Ao ler 391 anos-núcleo e 3,2 dias, separe a soma do tempo de processamento da duração da simulação. Esses valores não fornecem uma previsão para um computador pessoal.
- Na fatoração em lote, inclua a pré-computação inicial na conta. O ganho de 30 vezes se refere ao custo médio teórico de cada chave adicional de 1024 bits, depois desse preparo.
- O método de fatoração em lote ainda não foi implementado na prática, e a tabela de pré-computação não foi construída. Trate o resultado como teórico.
- A simulação das assinaturas ocorreu em ambiente isolado, sem sistemas ativos. Isso delimita o que foi executado e o que permaneceu como estimativa.
- Protocolos modernos com chaves de 2048 bits ou mais seguem seguros depois desta pesquisa. Essa conclusão pertence ao recorte do trabalho divulgado.
- A supervisão humana fez parte do método dos agentes. Os comandos de verificação ajudam a conferir o tamanho da chave; não avaliam sozinhos a segurança completa de um sistema.

Fonte: <https://storage.googleapis.com/deepmind-media/papers/Faster_Affine_Root_and_a_1024bit%20Computation.pdf>

## Glossário

- Agente de IA: sistema automatizado usado para explorar um problema e propor ou testar soluções; nesta pesquisa, trabalhou com supervisão humana.
- Ano-núcleo: medida que soma o tempo de processamento de um núcleo de CPU durante um ano e expressa custo computacional.
- Bit: unidade de informação usada para indicar o tamanho da chave; a pesquisa contrasta chaves de 1024 bits com as de 2048 bits ou mais.
- Complexidade assintótica: maneira como o custo de um algoritmo cresce conforme o tamanho do problema aumenta.
- CPU: unidade de processamento do computador; o tempo de CPU mede o esforço de processamento consumido por uma tarefa.
- Criptanálise: estudo e teste de sistemas criptográficos para avaliar sua resistência e encontrar fraquezas.
- Dureza computacional: dificuldade de resolver um problema dentro de um orçamento de processamento, mesmo quando montar o problema é fácil.
- Fatoração: decomposição de um número em fatores; no RSA, o desafio é recuperar os primos que formam o produto.
- Padding: dados predefinidos acrescentados à mensagem para formar um bloco de tamanho fixo antes da assinatura.
- Pré-computação: cálculo inicial feito antes da operação principal e aproveitado depois; no lote, seu custo é dividido entre várias chaves.
- Resumo digital: representação curta de uma mensagem, também chamada de impressão digital; o cenário teórico das assinaturas usa um resumo de 32 bytes.
- RSA: sistema criptográfico cuja segurança depende da dificuldade de fatorar o produto de dois números primos grandes.
- Sandbox: ambiente controlado e isolado usado para testes; a pesquisa realizou a simulação sem acessar sistemas ativos.
- SSH: protocolo usado para acesso remoto seguro; nesta apostila, aparece na verificação do tamanho de uma chave.
- TLS: protocolo usado para proteger comunicações; nesta apostila, aparece na verificação do certificado.

## Para onde ir depois

O próximo passo é praticar a leitura do tamanho das chaves em certificados TLS e chaves SSH que você administra. Depois, separe os itens RSA de 1024 bits dos itens com 2048 bits ou mais e use essa lista para orientar uma revisão preventiva.

Para aprofundar o método, leia o artigo técnico sobre assinaturas digitais e o artigo sobre fatoração em lote. Eles mostram os dois caminhos da pesquisa: a proteção do padding diante do controle do bloco e a divisão da pré-computação entre várias chaves.

- Pratique os dois comandos em arquivos que você administra e localize o tamanho da chave na saída.
- Compare cada resultado com as condições da pesquisa, mantendo separados os valores teóricos e os obtidos em simulação.
- Se encontrar RSA de 1024 bits, inclua o item na lista de sistemas legados que merecem atenção.
