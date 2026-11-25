# Google Research lança StreetReaderAI para pessoas cegas

_2026-11-23 · noticia_

O Google Research lançou o StreetReaderAI, um aplicativo de mapas multimodal para explorar imagens de rua sem usar a visão. A pessoa se move pelo teclado ou pela voz e ouve descrições do que há ao redor. O código é aberto, com licença Apache 2.0.

## O fato

O Google Research lançou o StreetReaderAI, um aplicativo de mapas multimodal para explorar imagens de rua de forma não visual.

Foi construído com e para pessoas cegas e com baixa visão, o público BLV.

Fonte: <https://research.google/blog/streetreaderai-towards-making-street-view-accessible-via-context-aware-multimodal-ai/>

## Os números

- Licença Apache 2.0.
- Node.js 18 ou mais para rodar no computador.
- Dois comandos para instalar e iniciar: make setup e make start.

Fonte: <https://github.com/research-ground/streetreaderAI>

## O que muda para você

A pessoa navega pelas imagens de rua digitando comandos ou falando. O aplicativo responde descrevendo, em tempo real, o que aparece em cada ponto do trajeto.

No exemplo divulgado, a voz descreve uma área de mesas de restaurante na calçada e lê a placa verde da rua, W Market, além de acompanhar avanços de 21 metros e depois 19 metros.

## O que fazer hoje

1. Instale o Node.js 18 ou mais e tenha uma chave da API Gemini, que sai do Google AI Studio. Resultado: o ambiente fica pronto para rodar o aplicativo.
2. Rode make setup para instalar o aplicativo. Resultado: a instalação fica concluída.
3. Rode make start para iniciá-lo. Resultado: o aplicativo abre para uso pelo teclado ou pela voz.

```
make setup
```

Fonte: <https://github.com/research-ground/streetreaderAI>

## O que conferir

O uso exige uma chave da API Gemini.

A descrição da voz segue o que o aplicativo lê nas imagens. Confira o resultado com a sua situação real antes de confiar nele.

Fonte: <https://aistudio.google.com/>
