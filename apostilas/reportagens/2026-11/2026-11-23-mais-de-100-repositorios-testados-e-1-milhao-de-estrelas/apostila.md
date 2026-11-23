# Mais de 100 repositórios testados e 1 milhão de estrelas

_2026-11-23 · reportagem_

Seis repositórios do GitHub para vídeo, voz, agentes, programação e estudo de aplicativos, escolhidos entre mais de cem testados com IA. Juntos passam de 1 milhão de estrelas, a curtida do GitHub. Cada seção traz o que a ferramenta faz, o comando pronto e o endereço do repositório.

## Antes de baixar

Qualquer pessoa sobe qualquer coisa no GitHub, inclusive arquivos maliciosos feitos para rodar no seu computador com IA. Já houve quem baixasse tudo e acabasse instalando código malicioso.

Confira a origem de cada repositório antes de rodar qualquer coisa com a sua IA. Os endereços desta apostila são os repositórios oficiais de cada projeto.

## Remotion: vídeo com React e TypeScript

Transforma código em vídeo usando React e TypeScript. Tem recursos voltados também para edição. Por usar React e TypeScript, é mais pesado e gasta mais tokens que o Hyperframes.

```
npx create-video@latest
```

Fonte: <https://github.com/remotion-dev/remotion>

## Hyperframes: vídeo com HTML, CSS e JavaScript

Transforma código em vídeo com HTML, CSS e JavaScript. Gasta menos tokens que o Remotion e serve melhor para gerar motion do que para cortar e limpar um vídeo gravado.

- Instale antes o Node.js 22 ou mais.
- Instale também o FFmpeg.
- Rode o comando abaixo para criar o projeto.

```
npx hyperframes init my-video
```

Fonte: <https://github.com/heygen-com/hyperframes>

## Voice Studio: voz clonada e dublagem grátis

Alternativa gratuita e open source ao ElevenLabs. Clona a sua voz, gera áudios com ela e dubla vídeos para outro idioma. Roda no seu computador, com instaladores para Windows, Mac e Linux.

No teste do canal, funcionou melhor que o esperado, inclusive em português. Não supera as opções pagas, mas atende quem quer algo gratuito e ilimitado, rodando num servidor.

Fonte: <https://github.com/debpalash/VoiceStudio>

## Paperclip: um time de agentes

Monta um time de agentes que trabalham juntos, cada um com contexto e tarefas próprios. É gratuito e se usa pela interface. Também permite montar um conselho de modelos que debatem um tema até chegar a um resultado refinado.

- Instale antes o Node.js 24.11 ou mais.
- Rode o comando abaixo e siga o onboarding pela interface.

```
npx paperclipai@latest onboard --yes
```

Fonte: <https://github.com/paperclipai/paperclip>

## Superpowers: o ciclo do projeto, do plano ao teste

Ajuda programadores a planejar, construir, revisar e testar projetos.

A v7.0.2, de 3 de novembro de 2026, cortou as perguntas de enchimento do brainstorming de 41 para 23 nos testes do projeto.

- No Claude Code, rode o comando abaixo.

```
/plugin install superpowers@claude-plugins-official
```

Fonte: <https://github.com/obra/superpowers>

## Reverse Engineer Anything: estudar um aplicativo

Dá a agentes de IA um jeito de estudar um aplicativo e recriar suas funções. Reúne informações de várias fontes e, a partir delas, começa o desenvolvimento.

Nos testes do canal, a coleta de informações foi o ponto forte. A etapa de desenvolvimento do aplicativo ficou abaixo disso, principalmente para quem já trabalha com IA agêntica mais sofisticada.

```
npx rea-agents setup
```

Fonte: <https://github.com/morluto/rea>

## Além do vídeo

- Voice Studio: o canal ainda usa opções pagas, com assinaturas em torno de 100 dólares, nos projetos sérios.
- Voice Studio: dá para rodá-lo numa VPS, num pipeline 24 horas por dia, para postar 100 vídeos por dia.
- Motion com JavaScript e Claude Code: os modelos novos já entregam bons resultados de cara, e ferramentas adicionais podem ser desnecessárias, dependendo do que você quer fazer.
- Superpowers v7.0.2: a versão também corrige problemas de inicialização em seis ambientes.
