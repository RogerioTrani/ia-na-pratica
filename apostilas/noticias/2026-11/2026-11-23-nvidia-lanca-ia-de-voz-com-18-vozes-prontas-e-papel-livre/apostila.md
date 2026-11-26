# Nvidia lança IA de voz com 18 vozes prontas e papel livre

_2026-11-23 · noticia_

A NVIDIA liberou o PersonaPlex, um modelo de voz aberto e gratuito que conversa em tempo real e pode rodar no computador da pessoa. Ele tem 7 bilhões de parâmetros, 18 vozes prontas e permite definir um papel para a IA durante a conversa. O modelo foi treinado para conversar em inglês, exige placa de vídeo e oferece uma opção para transferir parte do trabalho ao processador quando falta memória na placa. Ao ler esta apostila, você vai entender o anúncio, reconhecer seus limites e começar o teste pelo repositório oficial.

## O fato

A NVIDIA disponibilizou de graça o PersonaPlex, um modelo de voz com código aberto que conversa em tempo real e pode ser executado no próprio computador. O projeto está no repositório oficial da NVIDIA no GitHub, onde qualquer pessoa pode baixar o modelo, examinar o código e fazer seus próprios testes.

O anúncio reúne conversa simultânea, interrupção no meio da fala, 18 vozes prontas e personalização por papel. O modelo recebeu o nome de personaplex-7b-v1 no Hugging Face e tem 7 bilhões de parâmetros. Essas características fazem do projeto uma opção para quem quer experimentar uma voz de IA localmente.

Fonte: <https://github.com/NVIDIA/personaplex>

## Por que isso importa

Uma conversa humana depende de timing. A pessoa percebe quando pode falar, reconhece pausas e interrompe quando quer corrigir um caminho. Um sistema de voz que só alterna entre escutar e falar tende a exigir que o usuário espere cada resposta terminar. O PersonaPlex foi apresentado com escuta e fala simultâneas, além de reação a interrupções.

Essa forma de conversar aproxima a interação de um diálogo. Você pode responder enquanto a IA fala, e ela para quando você toma a palavra. Também pode escolher a voz e descrever o comportamento esperado. Como o projeto é aberto e pode rodar no seu computador, o teste fica disponível para quem quer observar esses comportamentos por conta própria.

Fonte: <https://research.nvidia.com/labs/adlr/personaplex/>

## Código aberto e 7 bilhões de parâmetros

Parâmetros são os valores internos que um modelo ajusta durante o treinamento. Eles participam do processamento que transforma a entrada em uma resposta. No caso do PersonaPlex, o modelo personaplex-7b-v1 tem 7 bilhões de parâmetros. Esse número indica a escala do modelo, mas não mede sozinho a naturalidade da voz, a velocidade da resposta ou o desempenho em cada computador.

O código aberto permite que a pessoa baixe o projeto, olhe como ele funciona e teste sem pagar pelo acesso. Essa disponibilidade torna possível investigar a instalação e o comportamento do modelo. As condições de reutilização continuam ligadas à licença do projeto, que deve ser lida antes de usar o código ou o modelo em um trabalho próprio.

Fonte: <https://huggingface.co/nvidia/personaplex-7b-v1>

## Ouve e fala ao mesmo tempo

O PersonaPlex acompanha a fala da pessoa enquanto produz a própria resposta. Essa escuta simultânea permite que a conversa avance sem depender apenas de turnos completamente separados. Se a pessoa começa a falar no meio de uma resposta, o modelo aceita a interrupção e para.

Tempo real descreve essa interação durante a conversa. A IA responde no momento da fala e reage ao que está acontecendo. Para quem vai testar, o importante é observar o comportamento no próprio computador: se a resposta acompanha a conversa, se a IA para ao ser interrompida e se as pausas fazem parte do fluxo. Uma impressão de resposta imediata não substitui uma medida de latência.

Fonte: <https://research.nvidia.com/labs/adlr/personaplex/>

## Interrupções, pausas e o som de escuta

Interromper significa começar a falar enquanto a IA ainda está respondendo. No PersonaPlex, essa entrada da pessoa faz a resposta parar. Esse comportamento serve para corrigir uma informação, mudar de assunto ou responder antes que a IA termine o raciocínio.

O modelo também emite um som curto, descrito como um "uhum", enquanto a pessoa fala. Na conversa, esse som funciona como um sinal de que a IA está acompanhando. Além disso, o PersonaPlex reconhece pausas na fala. Pausa e interrupção têm papéis diferentes: a primeira é um intervalo no que a pessoa está dizendo; a segunda é uma nova fala que entra sobre a resposta da IA.

Exemplo: você está explicando uma ideia e a IA começa a responder antes de você terminar. Ao retomar a fala, ela para. Se você fizer uma pausa para organizar o pensamento, o comportamento observado deve acompanhar essa pausa como parte da conversa.

Fonte: <https://research.nvidia.com/labs/adlr/personaplex/>

## As 18 vozes e o papel livre

O PersonaPlex oferece 18 vozes prontas. A voz é o timbre que você escolhe para ouvir a IA. O papel é uma descrição de como ela deve se comportar na conversa. Essas duas escolhas podem ser combinadas: uma voz definida acompanha a personalidade escrita por você.

Os exemplos apresentados são um professor simpático, a atendente de um restaurante e um astronauta a caminho de Marte. Em cada caso, o papel orienta a conversa para uma situação diferente. Isso permite testar a mesma capacidade de voz em contextos distintos, sempre dentro do idioma para o qual o modelo foi treinado.

Imagine que você escolhe uma das vozes prontas e define o papel de professor simpático. A conversa passa a acontecer com essa orientação de comportamento. O papel não é uma gravação da sua voz; ele descreve quem a IA deve representar naquela interação.

Fonte: <https://research.nvidia.com/labs/adlr/personaplex/>

## Placa de vídeo e memória

O PersonaPlex precisa de uma placa de vídeo para rodar. A GPU, ou placa de vídeo, realiza parte do processamento usado pelo modelo. A memória dessa placa é um dos pontos a observar antes de iniciar o servidor, porque o trabalho de voz exige recursos durante a execução.

Se faltar memória da placa, o repositório orienta rodar o servidor com a opção --cpu-offload. Ela transfere parte do trabalho para o processador. A opção redistribui o processamento e não aumenta a memória da placa. O requisito de placa de vídeo continua valendo, e o resultado da transferência deve ser observado no teste.

```
--cpu-offload
```

Fonte: <https://github.com/NVIDIA/personaplex>

## Os números

- 7 bilhões de parâmetros: quantidade de valores internos ajustados no treinamento do modelo. O número descreve a escala do PersonaPlex e não mede, sozinho, qualidade da voz, velocidade ou facilidade de instalação.
- Mais de 12 mil estrelas no GitHub: sinal de interesse da comunidade no repositório. Estrelas não representam downloads, testes aprovados ou uma nota de qualidade.
- 18 vozes prontas: opções de voz disponíveis para escolher. O número indica a quantidade de vozes oferecidas, não a quantidade de papéis ou situações que o modelo consegue representar.
- Inglês: idioma para o qual o modelo foi treinado a conversar. O teste descrito nesta apostila parte dessa condição em inglês.

Fonte: <https://github.com/NVIDIA/personaplex>

## O que muda para você

O projeto permite montar um teste de conversa com três escolhas: a voz, o papel e a forma de interagir. Você seleciona uma das 18 vozes, descreve o comportamento desejado e conversa em inglês. Durante a fala, pode fazer pausas e interromper a resposta para observar como o modelo acompanha a conversa.

Exemplo: uma pessoa escolhe uma voz pronta e define o papel de professor simpático. Depois, faz uma pergunta em inglês, deixa uma pausa e retoma a fala enquanto a IA responde. O objetivo é verificar a combinação entre voz e papel e observar a parada diante da interrupção.

Fonte: <https://research.nvidia.com/labs/adlr/personaplex/>

## O que fazer hoje

O caminho para o primeiro teste começa no repositório oficial. Siga a sequência de instalação fornecida pela NVIDIA e observe cada resultado antes de avançar para a conversa.

1. Abra o repositório oficial em https://github.com/NVIDIA/personaplex e localize a instalação passo a passo. O resultado esperado é ter a sequência oficial para preparar o ambiente.
2. Confira a placa de vídeo e a memória disponível antes de iniciar. O resultado esperado é saber se a execução poderá usar a placa normalmente ou precisará da opção de transferência de parte do trabalho para o processador.
3. Siga a instalação indicada no repositório e inicie o servidor. O resultado esperado é o servidor em execução, conforme as instruções oficiais.
4. Escolha uma das 18 vozes e escreva um papel simples, como professor simpático. O resultado esperado é começar a conversa com a voz e o papel escolhidos.
5. Converse em inglês, faça uma pausa e interrompa no meio de uma resposta. O resultado esperado é observar a escuta simultânea, o reconhecimento das pausas e a parada diante da interrupção.

Fonte: <https://github.com/NVIDIA/personaplex>

## O que conferir

Antes de confiar no resultado, separe o que o anúncio descreve do que o seu teste mostra. O PersonaPlex foi treinado para conversar em inglês e precisa de placa de vídeo. A conversa em tempo real, as pausas e as interrupções devem ser observadas na execução do seu computador.

A abertura do código facilita a inspeção, mas as condições de uso vêm da licença. Leia essa licença antes de reutilizar o projeto. Verifique também se a voz e o papel escolhidos correspondem ao teste que você quer fazer.

- Idioma: faça a conversa em inglês, que é o idioma de conversa para o qual o modelo foi treinado.
- Hardware: confira a placa de vídeo e a memória. A transferência para o processador atende a parte do processamento e não substitui o requisito de placa de vídeo.
- Desempenho: trate o tempo real como um comportamento a observar no seu computador. Uma resposta que parece imediata não fornece, sozinha, uma medida de latência.
- Licença: leia as condições do repositório antes de reutilizar o código ou o modelo em um projeto. O acesso gratuito e o código aberto devem ser avaliados junto da licença.
- Voz e papel: escolha a voz separadamente da descrição do papel. O papel define comportamento na conversa e não representa uma gravação da sua voz.
- Comunidade: use as estrelas do GitHub como sinal de interesse. O resultado do seu teste depende da execução e dos comportamentos observados.

Fonte: <https://github.com/NVIDIA/personaplex>

## Glossário

- PersonaPlex: modelo de voz da NVIDIA, com código aberto, que conversa em tempo real e aceita voz e papel escolhidos pela pessoa.
- Modelo de voz: sistema de IA que recebe fala e produz respostas faladas.
- Parâmetro: valor interno ajustado durante o treinamento de um modelo.
- Código aberto: código disponibilizado para inspeção e uso conforme a licença do projeto.
- GitHub: plataforma onde fica o repositório oficial do PersonaPlex.
- Estrela: marca de interesse que um usuário do GitHub pode dar a um repositório.
- Tempo real: conversa em que ouvir, responder e reagir a interrupções acontece durante a interação.
- Escuta simultânea: capacidade de acompanhar a fala da pessoa enquanto o modelo também fala.
- Interrupção: fala da pessoa que entra no meio da resposta e faz o modelo parar.
- Uhum: som curto que o modelo emite enquanto a pessoa fala.
- Pausa: intervalo na fala que o modelo reconhece no decorrer da conversa.
- Voz: timbre escolhido entre as opções prontas do modelo.
- Papel: descrição do comportamento que a pessoa define para a IA na conversa.
- GPU: placa de vídeo usada para executar parte do processamento do modelo.
- CPU: processador do computador, que recebe parte do trabalho quando a opção de transferência é usada.
- Offload: transferência de parte do processamento para outro componente, no caso o processador.
- Servidor: programa que mantém o PersonaPlex disponível para a conversa no computador.
- Hugging Face: plataforma onde está a página oficial do modelo personaplex-7b-v1.

## Para onde ir depois

Depois do primeiro teste, pratique com papéis diferentes e observe quais comportamentos aparecem em cada conversa. Mantenha o teste em inglês e use o repositório oficial como referência para instalação e configuração.

- Repositório oficial: https://github.com/NVIDIA/personaplex. Use a documentação de instalação e leia as condições do projeto antes de ampliar o teste.
- Modelo no Hugging Face: https://huggingface.co/nvidia/personaplex-7b-v1. Use a página oficial para localizar o modelo personaplex-7b-v1.
- Página de pesquisa da NVIDIA: https://research.nvidia.com/labs/adlr/personaplex/. Veja a apresentação do PersonaPlex feita pela NVIDIA.
- Pratique com um papel de cada vez. Comece pelo professor simpático e depois experimente a atendente de restaurante ou o astronauta a caminho de Marte, observando a voz, as pausas e as interrupções.

Fonte: <https://github.com/NVIDIA/personaplex>
