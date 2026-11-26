# DeepSeek lança Super-Agent que corrige bug e abre PR sozinho

_2026-11-23 · noticia_

A DeepSeek apresentou duas novidades de código aberto: um Super-Agent que corrige bugs a partir de um pedido no chat e abre o pull request sozinho, e um Creator Mode que transforma uma frase em aplicativo. Esta apostila explica como cada um funciona, o que muda no fluxo de um time e como rodar o DeepSeek Harness na sua máquina. Os dois ainda estão em fase inicial, o código é gratuito e o modelo se paga à parte ou roda local. Ao final, você sabe por onde começar a testar sem apostar o fluxo do time.

## O fato

A DeepSeek apresentou duas novidades de código aberto. A primeira é o Super-Agent, um agente que fica de olho no repositório do time e age quando alguém pede ou quando uma regra do time permite: um bug cai no chat e ele reproduz o problema, corrige e abre o pull request sozinho. A segunda é o Creator Mode, um modo que transforma uma frase em aplicativo, com exemplos que vão de um mural de post-its a um editor de vídeo.

O Super-Agent é um protótipo de pesquisa publicado como referência, não um produto oficial da DeepSeek. O DeepSeek Harness, a base que o executa, está em developer preview e pode ter mudanças incompatíveis.

Fonte: <https://github.com/deepseek-ai/dsh-superagent-prototype>

## Por que isso importa

A ideia é inverter o fluxo de trabalho com agentes. Em vez de esperar um comando, o agente acompanha o código do time e age quando alguém pede ou quando uma regra do time permite. Quem reportou o erro no chat já encontra a correção pronta para revisão; o time só precisa olhar o pull request e decidir se aceita.

A filosofia por trás é tomar o mínimo de atenção humana possível e dar o máximo de valor possível. Um agente que age por um time inteiro também pode desperdiçar a atenção de um time inteiro, por isso ele age apenas quando é pedido ou quando uma regra escrita pelo time permite, e fala apenas quando alguém precisa agir ou pode usar o resultado.

Fonte: <https://github.com/deepseek-ai/dsh-superagent-prototype>

## Super-Agent: como um bug vira pull request

O Super-Agent é um agente de programação proativo para um repositório GitHub, empacotado como bundle para o DeepSeek Harness. Ele escuta o GitHub e, opcionalmente, o Feishu. Quando alguém autorizado pede trabalho ao agente, ele abre um item de trabalho, executa em sua própria sessão e diretório de agente, e responde na conversa original, por exemplo com um pull request. Um painel web mostra o que precisa de uma pessoa.

Na prática, o time reporta o bug no chat e o agente faz o resto: reproduz, corrige e abre o pull request. O humano entra na revisão, não na execução.

Fonte: <https://github.com/deepseek-ai/dsh-superagent-prototype>

## Roteador e funcionários digitais

Pense numa equipe de funcionários digitais. Um roteador distribui o trabalho e cada funcionário guarda o próprio contexto. O trabalho continua mesmo com o notebook fechado.

Fonte: <https://github.com/deepseek-ai/dsh-superagent-prototype>

## Creator Mode: uma frase vira um app

Você descreve a ideia em uma frase e o modo de criação monta o aplicativo. Os exemplos mostrados vão de um mural de post-its a um jogo de voxels, passando por um editor de vídeo e um guia de viagem em 3D.

O Creator Mode também cria plugins por chat. O exemplo oficial mostra um plugin de timer Pomodoro construído, instalado e verificado em 5 minutos e 24 segundos, a partir de um pedido em linguagem natural.

Fonte: <https://www.deepseek.com/en/harness/>

## Plugin da comunidade: dsh-claude-design

Há um plugin da comunidade que roda o fluxo do Claude Design dentro do DeepSeek Harness. Ele está publicado no npm e disponível no mercado de plugins aberto.

- Pacote no npm: dsh-claude-design
- Repositório do plugin: https://github.com/JimLiu/baoyu-design
- Página no mercado aberto: https://dshopen.org/plugins/dsh-claude-design

```
dsh plugin --profile desktop add dsh-claude-design
```

Fonte: <https://www.npmjs.com/package/dsh-claude-design>

## DeepSeek Harness: a base de tudo

O DeepSeek Harness (dsh) é um harness de agentes de código aberto desenvolvido pela DeepSeek AI. É construído sobre a arquitetura 'tudo é um plugin' e usa o Cordis, cujo design é descrito no artigo 'A Programming Paradigm for Spatiotemporal Composability'.

Ele está em developer preview e itera rápido; haverá mudanças incompatíveis. Leia o aviso de segurança (SAFETY.md) antes de rodar o projeto.

Fonte: <https://github.com/deepseek-ai/deepseek-harness>

## Como rodar o DeepSeek Harness

Com o Node.js instalado, o caminho mais rápido é rodar direto do npm. O comando sobe a interface web em http://127.0.0.1:3080 por padrão e abre o navegador numa execução local. Em SSH, apenas imprime a URL do host. Use --no-open para rodar o servidor sem abrir navegador.

- Instale o Node.js
- Execute npx @deepseek-ai/dsh web
- Acesse http://127.0.0.1:3080 no navegador
- Opcional: adicione --no-open para não abrir o navegador

```
npx @deepseek-ai/dsh web
```

Fonte: <https://github.com/deepseek-ai/deepseek-harness>

## Os números

Alguns valores que ajudam a dimensionar o que a DeepSeek mostrou.

- http://127.0.0.1:3080: endereço padrão da interface web do DeepSeek Harness numa execução local.
- macOS 13 ou posterior: requisito para a versão desktop no Apple silicon; também há versão para Windows.
- 25:00: tempo de foco do exemplo de timer Pomodoro criado no Creator Mode.
- 5m 24s: tempo que levou para construir, instalar e verificar o plugin Pomodoro no exemplo oficial.
- Developer preview: estado do DeepSeek Harness, com mudanças incompatíveis previstas.
- Protótipo de pesquisa: estado do Super-Agent, não é produto oficial.

Fonte: <https://github.com/deepseek-ai/deepseek-harness>

## O que muda para você

Para um time de desenvolvimento, o fluxo muda de reportar e esperar para reportar e revisar. Quem viu o bug no chat já encontra a correção pronta para revisão; o humano decide se aceita o pull request, não executa a correção.

Para quem cria, o Creator Mode reduz a barreira de entrada: descrever a ideia em uma frase e obter um aplicativo, de um mural de post-its a um editor de vídeo. Imagine descrever 'um timer Pomodoro flutuante' e receber o plugin construído, instalado e verificado em poucos minutos.

Fonte: <https://github.com/deepseek-ai/dsh-superagent-prototype>

## O que fazer hoje

1. Instale o Node.js e rode 'npx @deepseek-ai/dsh web' para subir o DeepSeek Harness localmente; confirme que a interface abre em http://127.0.0.1:3080.
2. Se preferir compilar do código, clone https://github.com/deepseek-ai/deepseek-harness.git, entre na pasta, rode 'pnpm install', 'pnpm run build' e depois 'pnpm dsh web'.
3. Para o Super-Agent, peça ao seu agente de programação que leia o SETUP.md do repositório https://github.com/deepseek-ai/dsh-superagent-prototype e configure junto com você; ele faz uma pergunta por vez e mostra o plano completo antes de instalar.
4. Aponte o Super-Agent para um repositório de experimento, não para o fluxo principal do time, e teste com bugs reais antes de confiar.
5. Para experimentar o Creator Mode, use a interface do Harness e descreva um aplicativo em uma frase; comece por algo pequeno, como um timer ou um mural de post-its.
6. Para o plugin Claude Design, execute 'dsh plugin --profile desktop add dsh-claude-design' e confira a instalação pelo gerenciador de plugins do Harness.

Fonte: <https://github.com/deepseek-ai/dsh-superagent-prototype>

## O que conferir

- O Super-Agent é protótipo de pesquisa, não produto oficial: pode conter bugs e estilo de código inconsistente. Revise e adapte antes de usar no seu ambiente.
- Não é idêntico à versão interna da DeepSeek nem ao que o artigo 'Exploring Super-agent Design' descreve; parte do que o artigo propõe é direção futura, não está implementado.
- O DeepSeek Harness está em developer preview, com mudanças incompatíveis previstas. Leia SAFETY.md antes de rodar.
- O software é gratuito e licenciado sob MIT; o custo vem do modelo, pago à parte ou rodado na sua própria máquina.
- O comando de instalação do plugin dsh-claude-design pode variar: a documentação oficial mostra instalação pelo gerenciador de plugins ou pelo mercado. Confirme no seu ambiente.
- O agente age apenas quando é pedido ou quando uma regra do time permite; não espere ação totalmente autônoma sem regra escrita.
- Teste em projeto de experimento antes de apostar o fluxo do time.

Fonte: <https://github.com/deepseek-ai/dsh-superagent-prototype>

## Glossário

- Agente: programa que executa tarefas de forma autônoma a partir de instruções.
- Pull request: proposta de mudança de código para revisão antes de entrar no projeto.
- Repositório: pasta versionada do código de um projeto.
- Roteador: componente que distribui tarefas entre os funcionários digitais.
- Contexto: informações que um funcionário digital guarda sobre o seu trabalho.
- Creator Mode: modo do Harness que monta um aplicativo a partir de uma descrição em uma frase.
- Plugin: extensão que adiciona ferramentas, habilidades ou interface ao Harness.
- Harness: estrutura que executa e coordena agentes.
- Developer preview: versão em desenvolvimento com mudanças incompatíveis possíveis.
- Protótipo de pesquisa: código publicado para referência, não produto oficial.
- MIT: licença de software livre que permite uso e modificação.
- Cordis: biblioteca sobre a qual o Harness é construído.
- Feishu: mensageiro opcional que o Super-Agent pode escutar.
- npx: executor de pacotes do Node.js usado para rodar o Harness sem instalar.
- pnpm: gerenciador de pacotes usado para rodar o Harness a partir do código.

## Para onde ir depois

- Repositório do Super-Agent: https://github.com/deepseek-ai/dsh-superagent-prototype
- Repositório do DeepSeek Harness: https://github.com/deepseek-ai/deepseek-harness
- Documentação do Harness: https://deepseek-harness.github.io/deepseek-harness/
- Página oficial do Harness: https://www.deepseek.com/en/harness/
- Download do Harness (desktop): https://www.deepseek.com/en/download/
- Pacote dsh-claude-design no npm: https://www.npmjs.com/package/dsh-claude-design
- Plugin no mercado aberto: https://dshopen.org/plugins/dsh-claude-design
- Repositório do plugin: https://github.com/JimLiu/baoyu-design
- Pacote @deepseek-ai/dsh no npm: https://www.npmjs.com/package/@deepseek-ai/dsh
- Discussões no GitHub para feedback e bugs do Harness.
- Comunidade no Discord do DeepSeek Harness.

Fonte: <https://github.com/deepseek-ai/deepseek-harness>

## Links citados

- https://registry.npmjs.org/dsh-claude-design

## Além do vídeo

- Download do Harness para desktop no macOS (Apple silicon, macOS 13+) e Windows.
- Aplicativo DeepSeek para iOS e Android, com chat gratuito e o modelo principal mais recente.
- Tarefas agendadas, como o resumo semanal toda sexta às 17:00 no horário de Pequim.
- Equipes de agentes, revisão automática de aprovações e entrada por voz, todos marcados como experimentais.
- Ferramentas de desenvolvedor para inspecionar execuções e chamadas de ferramentas.
- Arquitetura Cordis e o artigo sobre composabilidade espaço-temporal.
- Aviso de segurança (SAFETY.md) a revisar antes de rodar.
- Feedback e relato de bugs via GitHub Discussions e comunidade no Discord.
- Modelo DeepSeek-V41-Flash High usado na interface.
- Exemplo de plugin Pomodoro criado por chat em 5 minutos e 24 segundos.
