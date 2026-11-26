# Google Research lança StreetReaderAI para pessoas cegas

_2026-11-23 · noticia_

O Google Research lançou o StreetReaderAI, um aplicativo de mapas para explorar imagens de rua sem depender da visão. Ele permite navegar por teclado ou voz e ouvir descrições em tempo real do entorno, e foi construído com e para pessoas cegas e com baixa visão. O código é aberto sob licença Apache 2.0 e pode ser testado no computador com Node.js 18 ou mais, uma chave da API Gemini e dois comandos. Depois de ler, você saberá o que o projeto faz, como instalá-lo e o que conferir antes de testar.

## O fato

O Google Research lançou o StreetReaderAI, um aplicativo de mapas para explorar imagens de rua sem depender da visão. Ele foi construído com e para pessoas cegas e com baixa visão, grupo chamado BLV, e permite navegar por imagens de rua usando teclado ou voz, ouvindo descrições em tempo real do entorno.

O código é aberto e está disponível sob licença Apache 2.0 no repositório oficial, em https://github.com/research-ground/streetreaderAI. O anúncio oficial do Google Research está em https://research.google/blog/streetreaderai-towards-making-street-view-accessible-via-context-aware-multimodal-ai/.

Fonte: <https://research.google/blog/streetreaderai-towards-making-street-view-accessible-via-context-aware-multimodal-ai/>

## Por que isso importa

Mapas de rua costumam depender de imagem. O StreetReaderAI muda esse ponto de partida: a exploração das imagens de rua é não visual, ou seja, a pessoa percorre o lugar e recebe informação por áudio, sem precisar enxergar a tela.

Isso importa porque a informação de rua deixa de ficar presa a quem vê. A proposta é transformar imagens de rua em descrições que podem ser ouvidas, comandadas por quem está explorando. Por ser multimodal, o aplicativo trabalha com mais de um tipo de informação ao mesmo tempo: a imagem de rua, os comandos por teclado ou voz e as descrições em áudio.

Fonte: <https://research.google/blog/streetreaderai-towards-making-street-view-accessible-via-context-aware-multimodal-ai/>

## Como a exploração funciona

A pessoa controla o passeio. Ela escolhe o caminho digitando comandos ou falando, e o aplicativo responde descrevendo o que aparece em cada ponto, em tempo real.

Assim, a navegação não é apenas uma lista de instruções: ela acompanha o deslocamento e descreve o entorno enquanto a pessoa se move.

Fonte: <https://github.com/research-ground/streetreaderAI>

## Construído com o público BLV

BLV reúne pessoas cegas e com baixa visão. O aplicativo foi construído com esse público e pensado para o uso dele.

Isso significa que o público a quem a ferramenta se destina participou da construção da experiência de uso não visual.

Fonte: <https://research.google/blog/streetreaderai-towards-making-street-view-accessible-via-context-aware-multimodal-ai/>

## Código aberto e licença

O projeto é aberto. Qualquer pessoa pode baixar, testar e inspecionar o código. A licença informada é Apache 2.0.

Antes de reutilizar o código em outro projeto, confira os termos da licença no repositório oficial.

Fonte: <https://github.com/research-ground/streetreaderAI>

## Como rodar no computador

1. Confira se o computador tem Node.js 18 ou mais instalado. É o requisito mínimo informado para rodar o aplicativo.
2. Obtenha uma chave da API Gemini. O Google AI Studio é o endereço oficial para isso: https://aistudio.google.com/.
3. No terminal, dentro da pasta do projeto, rode make setup para instalar o aplicativo.
4. Depois rode make start para abrir o aplicativo no navegador.
5. Use teclado ou voz para navegar pelas imagens e ouça as descrições em tempo real.

```
make setup
make start
```

Fonte: <https://github.com/research-ground/streetreaderAI>

## Exemplo divulgado

No exemplo divulgado, a voz descreve uma calçada com mesas de restaurante diante de um prédio de tijolos de vários andares. À esquerda, uma loja tem a placa Corridor 44 acima de grandes janelas de vidro.

A narração também acompanha o deslocamento: avança 21 metros, depois mais 19 metros, gira para a direita rumo ao noroeste e lê a placa verde da rua, que indica W Market.

Fonte: <https://research.google/blog/streetreaderai-towards-making-street-view-accessible-via-context-aware-multimodal-ai/>

## Os números

- 21 m: distância do primeiro avanço no exemplo divulgado, dita pela narração.
- 19 m: distância do segundo avanço no mesmo exemplo.
- Node.js 18: versão mínima para rodar o aplicativo no computador.
- 2 comandos: make setup instala e make start abre o aplicativo no navegador.
- Apache 2.0: licença do código aberto.

Fonte: <https://github.com/research-ground/streetreaderAI>

## O que muda para você

Para quem não enxerga ou enxerga pouco, a mudança é direta: uma imagem de rua pode ser explorada por áudio, comandando o percurso por teclado ou voz.

Para quem quer testar ou estudar acessibilidade, o projeto oferece um exemplo concreto de aplicação multimodal com código aberto, que pode ser instalado no computador com dois comandos. No exemplo divulgado, a narração descreve uma loja com a placa Corridor 44 e uma placa de rua W Market enquanto a pessoa avança 21 m e depois 19 m.

Fonte: <https://github.com/research-ground/streetreaderAI>

## O que fazer hoje

1. Abra o repositório oficial e leia a documentação inicial.
2. Verifique se o Node.js 18 ou mais está instalado.
3. Crie ou localize sua chave da API Gemini no Google AI Studio.
4. Clone ou baixe o projeto e rode make setup.
5. Rode make start e abra o aplicativo no navegador.
6. Navegue por teclado ou voz e confira se as descrições aparecem em tempo real.
7. Compare sua experiência com o exemplo divulgado, que descreve a loja Corridor 44 e a placa W Market.

Fonte: <https://github.com/research-ground/streetreaderAI>

## O que conferir

- O aplicativo exige Node.js 18 ou mais e uma chave da API Gemini; sem esses dois itens, o teste local não funciona.
- O exemplo divulgado é um caso concreto. Outras imagens de rua terão outras descrições, e as distâncias de 21 m e 19 m pertencem a esse exemplo.
- A licença Apache 2.0 não substitui a leitura dos termos oficiais antes de reutilizar ou redistribuir o código.
- As instruções de instalação desta apostila são para rodar o aplicativo no computador.
- A chave da API Gemini é obtida no Google AI Studio; confira lá as condições de uso do serviço.

Fonte: <https://github.com/research-ground/streetreaderAI>

## Glossário

- BLV: pessoas cegas e com baixa visão.
- Street-level imagery: imagens capturadas no nível da rua, como fotos de calçadas e fachadas.
- Multimodal: que combina mais de um tipo de informação, como imagem e voz ou texto.
- Apache 2.0: licença de software aberto que permite uso e modificação, com condições próprias.
- Node.js: ambiente para executar JavaScript fora do navegador.
- API key: chave usada para autenticar o acesso a um serviço, neste caso a API Gemini.
- Gemini API: serviço de IA do Google, cuja chave é obtida no Google AI Studio.

## Para onde ir depois

- Repositório oficial do StreetReaderAI: https://github.com/research-ground/streetreaderAI
- Post do Google Research sobre o projeto: https://research.google/blog/streetreaderai-towards-making-street-view-accessible-via-context-aware-multimodal-ai/
- Google AI Studio, para obter a chave da API Gemini: https://aistudio.google.com/
- Instale o projeto localmente e teste a navegação por teclado ou voz.

Fonte: <https://github.com/research-ground/streetreaderAI>
