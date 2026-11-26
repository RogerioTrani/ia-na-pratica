# Meta libera a Astryx, biblioteca usada em 13 mil apps

_2026-11-22 · noticia_

A Meta abriu ao público a Astryx, o sistema de design que a empresa usa nos seus próprios aplicativos. A biblioteca é gratuita, tem licença MIT e traz mais de 150 componentes React prontos para uso, com temas, modo escuro e modelos prontos para publicação. Quem lê esta apostila entende o que a Astryx é, por que importa para quem constrói interfaces e como começar a usá-la num projeto React. Também vê os números por trás da biblioteca, o que conferir antes de adotar e para onde ir depois.

## O fato

A Meta abriu ao público a Astryx, o sistema de design que a empresa usa nos seus próprios aplicativos. A biblioteca, até então usada internamente, passa a estar disponível para qualquer pessoa que queira construir interfaces com os mesmos padrões visuais da empresa.

A Astryx tem repositório oficial no GitHub (github.com/meta/astryx) e documentação em astryx.atmeta.com. A biblioteca é gratuita e tem licença MIT, o que permite usar, modificar e distribuir em projetos próprios ou comerciais.

Fonte: <https://github.com/meta/astryx>

## Por que isso importa

A Astryx cresceu dentro da Meta ao longo de oito anos e se tornou o maior e mais usado sistema de design da empresa, alimentando mais de 13.000 aplicativos. Quem moldou a biblioteca foram engenheiros, designers e times de produto que dependem dela no trabalho diário.

Um sistema de design é um conjunto de componentes reutilizáveis, padrões visuais e regras de uso que garantem consistência em todas as telas de um produto. Quando uma biblioteca desse porte, testada em produção em milhares de apps, fica disponível de graça, quem constrói interfaces ganha um ponto de partida que já provou funcionar em escala.

Fonte: <https://github.com/meta/astryx>

## O que é a Astryx

A Astryx é um sistema de design de código aberto, totalmente personalizável e pronto para uso por pessoas e por agentes de IA. Ela entrega mais de 150 componentes acessíveis, temas no nível de marca, modo escuro, modelos prontos para publicação e uma ferramenta de linha de comando (CLI), tudo como um sistema coeso.

A biblioteca está em fase Beta e é construída sobre React 19 ou superior e StyleX. Quem usa importa CSS pré-construído e usa componentes React com tipagem: não exige plugin de build nem configuração de PostCSS ou Babel. Tanto pessoas quanto assistentes de IA constroem com as mesmas ferramentas.

Fonte: <https://github.com/meta/astryx>

## Como funciona

O consumo é direto: você importa o CSS pronto e usa os componentes React tipados no seu projeto. Não exige plugin de build nem configuração de PostCSS ou Babel. A biblioteca não impõe uma ferramenta de estilos: quem já usa Tailwind, CSS modules ou CSS puro pode sobrescrever com className.

Os componentes são construídos para serem compostos em qualquer nível, não trancados atrás de uma API fechada. Os blocos de construção que você procuraria são exportados diretamente, e quando precisa ir mais fundo, o comando swizzle ejeta o código-fonte completo de um componente para o seu projeto, que passa a ser seu.

Fonte: <https://github.com/meta/astryx>

## O que torna a Astryx diferente

Quatro características definem a proposta da biblioteca e a separam de alternativas fechadas.

- Internos abertos: componentes feitos para compor em qualquer nível, com exportação direta dos blocos de construção e swizzle para assumir o código-fonte quando preciso.
- Sem travamento de estilos: a Astryx escreve seus estilos com StyleX, mas isso é invisível para quem consome. A sobrescrita acontece com className usando Tailwind, CSS modules ou CSS puro.
- Personalização sem envolver componentes: um tema é um conjunto de sobrescritas de propriedades CSS personalizadas, então um designer pode deixar a Astryx com a cara da marca sem fazer fork nem envolver o código-fonte dos componentes.
- Feita para pessoas e agentes: a API, a documentação e a CLI são desenhadas juntas, para que pessoa e assistente de IA construam do mesmo jeito, a partir da mesma referência.

Fonte: <https://github.com/meta/astryx>

## Temas prontos

A biblioteca traz sete temas prontos e totalmente personalizáveis: neutral, butter, chocolate, matcha, stone, gothic e y2k. Cada tema é um conjunto de sobrescritas de propriedades CSS, o que permite ajustar a aparência sem tocar no código dos componentes.

Fonte: <https://github.com/meta/astryx>

## Pacotes publicados

A Astryx é organizada em pacotes no npm. O pacote principal é o @astryxdesign/core, que contém componentes, sistema de temas e utilitários. O @astryxdesign/cli traz ferramentas de linha de comando: documentação de componentes, modelos, scaffolding, temas e codemods. O @astryxdesign/build oferece plugins de build para compilação de fontes StyleX. Os temas ficam em @astryxdesign/theme-*.

Fonte: <https://github.com/meta/astryx>

## A Astryx no GitHub

No momento da gravação, a Astryx ocupava a segunda posição entre os repositórios em alta no GitHub. O interesse dos desenvolvedores aparece nesse ranking. O repositório oficial fica em github.com/meta/astryx.

Fonte: <https://github.com/meta/astryx>

## Licença MIT: grátis e open source

A biblioteca é gratuita e de código aberto, com licença MIT. Qualquer pessoa pode usar a Astryx nos próprios projetos, sejam apps pessoais ou produtos com usuários reais, sem pagar.

Fonte: <https://github.com/meta/astryx>

## Os números

- 13.000+ aplicativos: quantidade de apps dentro da Meta que já usam a Astryx em produção.
- 8 anos: tempo de uso interno da biblioteca na Meta antes de ser aberta ao público.
- 150+ componentes: quantidade de componentes acessíveis que a biblioteca entrega.
- 7 temas: neutral, butter, chocolate, matcha, stone, gothic e y2k.
- 2º lugar: posição da Astryx entre os repositórios em alta no GitHub no momento da gravação.
- React 19 ou superior: versão mínima exigida, já que react e react-dom são dependências pares do @astryxdesign/core.
- Beta: fase atual da biblioteca.

Fonte: <https://github.com/meta/astryx>

## O que muda para você

Quem cria apps e bate cabeça com a interface encontra na Astryx um ponto de partida. Os componentes React agrupados por família ajudam a ajustar tela e experiência de uso, e o projeto precisa estar no React 19 ou mais novo.

Exemplo: imagine que você está construindo um app e precisa de uma tela de configurações. Em vez de montar cada botão, campo e modal do zero, você importa os componentes da Astryx, aplica um dos sete temas e ajusta as propriedades CSS para combinar com a sua marca. A IA do seu editor, com o índice de componentes gravado no AGENTS.md ou CLAUDE.md, pode sugerir quais peças usar.

Fonte: <https://github.com/meta/astryx>

## O que fazer hoje

Siga os passos abaixo para começar a usar a Astryx num projeto React.

1. Confirme que seu projeto usa React 19 ou superior, já que react e react-dom são dependências pares do @astryxdesign/core.
2. Instale a biblioteca e as dependências. Rode npm install @astryxdesign/core @astryxdesign/theme-neutral @stylexjs/stylex e npm install -D @astryxdesign/cli. Quem usa pnpm ou yarn pode usar pnpm add ou yarn add com os mesmos pacotes.
3. Rode npx @astryxdesign/cli init uma vez, antes de escrever UI. O comando não faz perguntas, imprime os passos de início (estilos, tema) e grava o guia da Astryx em AGENTS.md ou CLAUDE.md, para que você e seus agentes construam com a biblioteca em vez de adivinhar.
4. Siga o guia de início rápido no README do core para o setup completo, com exemplos para Next.js, Tailwind, Vite e CDN.
5. Opcional: instale a CLI globalmente com npm i -g @astryxdesign/cli, para que o comando astryx funcione em qualquer pasta e todo agente de código conheça a Astryx.

```
npm install @astryxdesign/core @astryxdesign/theme-neutral @stylexjs/stylex
npm install -D @astryxdesign/cli
npx @astryxdesign/cli init
```

Fonte: <https://github.com/meta/astryx/blob/main/packages/core/README.md>

## O que conferir

Antes de adotar a Astryx, confira os pontos abaixo.

- A biblioteca está em fase Beta. Espere mudanças e verifique a documentação antes de adotar em produção.
- O projeto precisa estar no React 19 ou superior. Em versões anteriores, a biblioteca não funciona.
- A CLI exige Node.js 22.13.0 ou superior quando usada em projetos consumidores.
- O guia de início rápido no README do core cobre Next.js, Tailwind, Vite e CDN. Confira o caminho certo para a sua stack.
- Para acesso confiável à CLI, adicione um script no package.json: "astryx": "node node_modules/@astryxdesign/cli/clients/cli/bin/astryx.mjs". Isso evita erros de caminho quando assistentes de IA ou novos desenvolvedores invocam a CLI diretamente.
- Os pacotes @astryxdesign/vega e @astryxdesign/charts são publicados apenas sob a dist-tag @canary, sem release estável. Não conte com eles em produção.

Fonte: <https://github.com/meta/astryx>

## Glossário

- Sistema de design: conjunto de componentes reutilizáveis, padrões visuais e regras de uso que garantem consistência em todas as telas de um produto.
- Componente: peça de interface reutilizável, como botão, campo ou modal, que pode ser combinada com outras para montar telas.
- CLI (Command Line Interface): ferramenta de linha de comando usada no terminal para automatizar tarefas como instalação, inicialização e consulta de documentação.
- AGENTS.md / CLAUDE.md: arquivos de instruções que agentes de código leem para saber como construir com a Astryx. O comando init grava neles o índice de componentes.
- StyleX: biblioteca de estilos usada internamente pela Astryx para escrever CSS. É invisível para quem consome a biblioteca.
- Swizzle: comando que ejeta o código-fonte completo de um componente para o seu projeto, para que você assuma a manutenção.
- Tema: conjunto de sobrescritas de propriedades CSS personalizadas que define a aparência visual da biblioteca.
- Licença MIT: licença de código aberto permissiva que permite usar, modificar e distribuir o software, inclusive em projetos comerciais, sem pagar.
- Dependência par: pacote que o seu projeto precisa ter, em versão compatível, para que a biblioteca funcione, como react e react-dom no caso do @astryxdesign/core.
- Beta: fase de desenvolvimento em que o software está disponível para uso mas pode mudar.

Fonte: <https://github.com/meta/astryx>

## Para onde ir depois

- Leia a documentação oficial em astryx.atmeta.com.
- Explore os componentes no Storybook em astryx.atmeta.com/storybook/.
- Teste a biblioteca no sandbox em astryx.atmeta.com/sandbox/.
- Acesse o repositório oficial em github.com/meta/astryx para código-fonte, issues e contribuições.
- Consulte o pacote no npm em npmjs.com/package/@astryxdesign/core.
- Entre no Discord da comunidade em discord.com/invite/XnsUcFykEP para perguntas e suporte.

Fonte: <https://github.com/meta/astryx>

## Links citados

- https://astryx.atmeta.com
- https://www.npmjs.com/package/@astryxdesign/core

## Além do vídeo

- O repositório tem uma pasta apps/ com apps de exemplo, o site de documentação e o Storybook; packages/ com os pacotes publicados; e internal/ com ferramentas internas de teste e lint.
- Para desenvolvimento local, o projeto exige a versão de Node.js fixada em .nvmrc e o pnpm 11. O comando corepack enable instala o pnpm automaticamente.
- A contribuição segue o guia em CONTRIBUTING.md, com convenções de API e de design, ciclo de vida de componentes e rubricas de revisão de PR documentados no wiki.
- O pacote @astryxdesign/lab (componentes experimentais) é usado internamente para Storybook e sandbox e não é publicado no npm.
- Os pacotes @astryxdesign/vega e @astryxdesign/charts são publicados no npm apenas sob a dist-tag @canary, sem release estável.
- Os princípios da biblioteca são: orientação em vez de imposição, convenções fortes e documentadas, um sistema único para pessoas e IA, e decisões baseadas em medição.
- A arquitetura se divide em três camadas: Foundations (tipografia, cor, layout, acessibilidade), Components (150+ blocos de UI com suporte a TypeScript) e Patterns (soluções de design para interações comuns).
