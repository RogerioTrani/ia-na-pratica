# Claude escreve e revisa 90% do código do time do Claude Code

_2026-11-23 · noticia_

A Anthropic diz que o Claude escreve e revisa cerca de 90% do código da equipe que constrói o Claude Code, e detalhou como verifica esse trabalho sem que engenheiros inspecionem cada mudança. A verificação combina checagens determinísticas baratas, revisão por modelo e execução real do aplicativo, com regras que impedem o agente de alterar o critério que o julga. Depois de ler, você saberá como montar um fluxo de verificação para código escrito por IA: quais checagens rodar primeiro, como proteger os testes e quando chamar um humano.

## O fato

A Anthropic afirma que o Claude escreve e revisa cerca de 90% do código produzido pela equipe que constrói o Claude Code, o assistente de programação da empresa. O número vale para as duas pontas do fluxo: a mesma IA propõe a alteração e também a revisa.

O que a empresa detalhou não é o número em si, mas o método de conferência. Um post de engenharia da empresa, publicado na segunda-feira anterior a 20 de novembro de 2026, descreve um sistema de verificação pensado para suportar dezenas ou até centenas de agentes rodando ao mesmo tempo, em que checagens automáticas fornecem as evidências de que os engenheiros precisam para julgar o que os agentes produzem.

O método atraiu escrutínio de desenvolvedores, sobretudo sobre o custo da verificação baseada em modelo e sobre se ferramentas determinísticas mais baratas poderiam assumir parte dessa carga. A Anthropic respondeu a perguntas do The New Stack sobre controle de custo de inferência, impedimento de manipulação de testes e avaliação dos revisores automáticos.

Fonte: <https://claude.dev/blog/how-the-claude-code-team-thinks-about-verification/>

## Por que isso importa

Quando a IA escreve e revisa a maior parte do código, a qualidade deixa de depender de leitura humana linha a linha e passa a depender de como o resultado é checado. O gargalo deixa de ser a geração e vira a verificação.

O conceito central é separar checagens baratas e determinísticas, que rodam como software comum, de revisão por modelo, que julga o que um teste não consegue responder, como a abordagem escolhida ou um caso que ninguém escreveu teste para cobrir.

Para quem desenvolve software, a pergunta muda: em vez de ler cada alteração, o engenheiro passa a definir o que significa estar pronto e a revisar as evidências. As regras que julgam a mudança ficam numa branch que a própria mudança não consegue alterar.

Fonte: <https://claude.dev/blog/how-the-claude-code-team-thinks-about-verification/>

## Verificação ao vivo: o Claude roda o aplicativo

Antes de gravar a mudança, o Claude executa o aplicativo de verdade. Para aplicativos web usa automação de navegador; para builds mobile, simuladores conectados via MCP; para trabalho de backend, serviços locais.

As instruções de verificação ficam em skills específicas do repositório, sob .claude/skills/, para que um agente consiga rodar e conferir suas próprias mudanças antes de fazer commit.

Além da execução ao vivo, o post aponta duas técnicas complementares: testes baseados em propriedades (property-based testing) para expor casos de borda, e testes diferenciais (differential testing) para revelar mudanças de comportamento não antecipadas entre uma implementação antiga e a nova.

Fonte: <https://claude.dev/blog/how-the-claude-code-team-thinks-about-verification/>

## Como mantêm o custo de verificação sob controle

O custo de inferência varia bastante de uma mudança para outra. A Anthropic mantém esse custo baixo rodando primeiro as checagens baratas e determinísticas, antes de qualquer modelo entrar em ação.

Build, linters, testes unitários e testes baseados em propriedades vão primeiro, porque uma vez que o Claude os escreve, eles rodam como software comum e custam muito pouco para serem rerodados. A revisão por modelo fica reservada para o que um teste não consegue responder, como se a mudança toma a abordagem certa ou perde um caso para o qual ninguém escreveu teste.

A empresa não forneceu uma cifra específica para o custo adicional da verificação baseada em modelo. Desenvolvedores questionaram se testes reutilizáveis, como testes Playwright, não poderiam cobrir grande parte da verificação sem chamar o modelo repetidamente; a Anthropic sustenta que a revisão por modelo responde perguntas que testes não respondem.

Fonte: <https://claude.dev/blog/how-the-claude-code-team-thinks-about-verification/>

## Como impedem o agente de manipular os testes

O risco levantado por desenvolvedores é o agente reescrever um teste ou adicionar uma gambiarra para fazer um teste falho passar, em vez de corrigir o problema de fundo. A Anthropic responde com uma regra: se uma mudança pode modificar a checagem que a julga, a checagem está quebrada.

Na prática, o Code Review lê o REVIEW.md da branch base, não das mudanças introduzidas no pull request. Qualquer resultado de review vale apenas para o commit exato que foi examinado.

O Claude não pode pular testes flaky, inserir sleeps ou rerodar um teste até passar. Quando não consegue identificar a causa raiz, ele deleta o teste e documenta o motivo. A equipe também registra como cada commit foi verificado, incluindo os casos em que nenhuma verificação ocorreu.

Fonte: <https://claude.dev/blog/how-the-claude-code-team-thinks-about-verification/>

## As 39 checagens e quantas rodam por mudança

A equipe do Claude Code acumulou 39 itens de confiabilidade. O Claude tipicamente roda apenas de 3 a 10 deles em cada mudança, aplicando só os que combinam com a alteração.

Exemplo citado: em mudanças de armazenamento de sessão, o Claude verifica se transcripts mais antigos ainda carregam com o parâmetro --resume.

Commit gates exigem que desenvolvedores verifiquem mudanças por meio de /code-review ou /verify. As equipes podem monitorar a conformidade antes de tornar as checagens obrigatórias, e um desenvolvedor pode contornar um gate se explicar o motivo.

```
/code-review
/verify
```

Fonte: <https://claude.dev/blog/how-the-claude-code-team-thinks-about-verification/>

## O que mudou para os engenheiros

O trabalho deixa de ser ler cada alteração e passa a ser definir o que é "pronto" e revisar as evidências, incluindo resultados de testes e capturas de tela.

As regras que julgam a mudança não estão no próprio pull request. O Code Review lê o REVIEW.md da branch base, ou seja, a alteração não consegue modificar o critério que a julga. A documentação de personalização do Code Review (REVIEW.md) está em code.claude.com/docs/en/code-review-customize.

A responsabilidade não se transfere para a máquina: "A person is accountable for every change that ships, whoever typed it", diz a Anthropic. Se uma checagem ainda falha após três rodadas, o Claude entrega o problema a um engenheiro.

Fonte: <https://claude.dev/blog/how-the-claude-code-team-thinks-about-verification/>

## Como a Anthropic mede seus revisores automáticos

Para checar seus próprios revisores, a Anthropic os avalia contra incidentes históricos e reverts. Ela recria o repositório como ele existia no momento da review e escreve uma resposta-chave de uma frase para cada caso; o revisor ganha crédito apenas quando o achado descreve de fato o bug em questão.

Mudanças previamente mescladas que se mantiveram estáveis servem de controle para detectar falsos positivos. A empresa mantém um conjunto de teste fixo isolado dos exemplos usados para ajustar os revisores.

A Anthropic mede recall em vários estágios do pipeline de review. Mesmo um revisor que captura um bug genuíno é pontuado como falha se o achado nunca chega a um engenheiro. A empresa diz não publicar atualmente as taxas de falso positivo ou falso negativo das avaliações do Code Review.

Fonte: <https://claude.dev/blog/how-the-claude-code-team-thinks-about-verification/>

## Resultados observados

Entre junho e setembro, o número de pull requests mesclados no codebase do Claude Code mais que dobrou, enquanto a proporção de mudanças que precisaram ser revertidas caiu mais de 40%.

A empresa não disse quanto dessa melhoria veio dos loops de verificação, nem forneceu números separados para defeitos de produção e regressões.

Fonte: <https://claude.dev/blog/how-the-claude-code-team-thinks-about-verification/>

## Os números

- Cerca de 90%: parcela do código da equipe do Claude Code que o Claude escreve e revisa, segundo a Anthropic.
- 39: itens de confiabilidade acumulados pela equipe; o Claude roda de 3 a 10 por mudança.
- 3 a 10: quantidade típica de checagens rodadas em cada mudança, entre as 39 disponíveis.
- 3 rodadas: se uma checagem continua falhando depois desse número, o Claude entrega o problema a um engenheiro.
- Mais que dobrou: pull requests mesclados entre junho e setembro.
- Mais de 40%: queda na proporção de mudanças revertidas no mesmo período.
- Dezenas a centenas: agentes concorrentes que o sistema de verificação foi pensado para suportar.

Fonte: <https://claude.dev/blog/how-the-claude-code-team-thinks-about-verification/>

## O que muda para você

Se a IA escreve e revisa, a qualidade passa a depender de como o resultado é checado, não de quanto humanos leem. Isso vale para sua equipe também: quem define as checagens e elas pegariam um erro do Claude?

Exemplo: imagine uma equipe que adota um assistente de código. Em vez de revisar cada alteração, ela define o que é "pronto" (testes passando, app rodando, capturas de tela anexadas) e confere as evidências. As regras de julgamento ficam numa branch que a mudança não consegue alterar, evitando que o agente afrouxe o próprio critério.

A abordagem da Anthropic oferece um quadro para decidir quais checagens exigem inferência de modelo e quais ferramentas determinísticas podem fazer mais barato. Sem taxas de erro publicadas dos revisores nem custos detalhados de inferência, porém, desenvolvedores têm poucos dados para comparar com suas próprias implementações.

Fonte: <https://claude.dev/blog/how-the-claude-code-team-thinks-about-verification/>

## O que fazer hoje

1. Separe checagens determinísticas das que exigem modelo: rode build, linters, testes unitários e testes baseados em propriedades primeiro, porque custam pouco para rerodar.
2. Deixe a revisão por modelo para o que um teste não responde: abordagem escolhida e casos não cobertos por teste.
3. Faça o agente rodar o aplicativo antes de gravar a mudança: use automação de navegador para web, simuladores via MCP para mobile e serviços locais para backend.
4. Coloque as instruções de verificação em skills no repositório, sob .claude/skills/, para que o agente verifique seu próprio trabalho.
5. Inclua testes baseados em propriedades para casos de borda e testes diferenciais para detectar mudanças de comportamento entre implementações antigas e novas.
6. Proteja o critério de julgamento: mantenha o REVIEW.md na branch base, para que a mudança não altere a regra que a julga.
7. Registre como cada commit foi verificado, inclusive os casos em que nenhuma verificação ocorreu.
8. Defina um limite de rodadas: se uma checagem falhar três vezes, entregue o problema a um engenheiro.
9. Use /code-review ou /verify como gate de commit e monitore a conformidade antes de tornar as checagens obrigatórias.
10. Mantenha uma pessoa responsável por cada mudança que é lançada, quem quer que tenha digitado; ela revisa as evidências.

```
/code-review
/verify
```

Fonte: <https://claude.dev/blog/how-the-claude-code-team-thinks-about-verification/>

## O que conferir

- Uma pessoa é responsável por cada mudança que é lançada, mesmo quando a IA digitou o código; a IA não assume a responsabilidade.
- Se uma checagem pode ser modificada pela própria mudança que ela julga, a checagem está quebrada; mantenha o REVIEW.md na branch base.
- O Claude não pode pular testes flaky, inserir sleeps ou rerodar testes até passarem; se não achar a causa raiz, deleta o teste e documenta o motivo.
- Entre as 39 checagens, apenas 3 a 10 costumam rodar por mudança; não assuma que todas rodam sempre.
- A Anthropic não publica taxas de falso positivo ou falso negativo dos revisores, nem o custo adicional de inferência da verificação por modelo.
- A melhoria de junho a setembro (PRs dobrando e reverts caindo mais de 40%) não teve a parcela atribuída aos loops de verificação divulgada; não trate como prova de causa e efeito.
- Desenvolvedores podem contornar um gate de commit se explicarem o motivo; isso é um ponto de atenção em equipes próprias.
- Fato versus hipótese: os números e regras acima vêm do relato da Anthropic e de sua documentação; a eficácia em outros contextos não foi medida nem publicada.

Fonte: <https://claude.dev/blog/how-the-claude-code-team-thinks-about-verification/>

## Glossário

- Claude Code: assistente de programação da Anthropic.
- REVIEW.md: arquivo de regras que o Code Review lê da branch base para julgar uma mudança.
- Branch base: a branch de onde parte a mudança; as regras de review vêm dela e a mudança não a altera.
- Skill de verificação: instruções no repositório, sob .claude/skills/, que permitem ao agente rodar e conferir suas próprias mudanças.
- MCP: protocolo que conecta o agente a simuladores e ferramentas externas, usado aqui para mobile.
- Property-based testing: teste que gera casos automaticamente para expor casos de borda.
- Differential testing: comparação de comportamento entre implementação antiga e nova para revelar mudanças não antecipadas.
- Commit gate: exigência de verificação (/code-review ou /verify) antes de fazer o commit de uma mudança.
- Recall: medida de quantos bugs reais o revisor consegue encontrar.
- Falso positivo: achado do revisor que não corresponde a um bug real.

## Para onde ir depois

- Ler o post da equipe do Claude Code sobre como pensa a verificação: https://claude.dev/blog/how-the-claude-code-team-thinks-about-verification/
- Consultar a documentação de personalização do Code Review (REVIEW.md): https://code.claude.com/docs/en/code-review-customize
- Escolher uma checagem determinística para adicionar ao seu fluxo esta semana e medir se ela pega erros antes da revisão humana.
- Definir, por escrito, o que significa "pronto" no seu time e onde as evidências serão registradas.
- Testar um limite de três rodadas de falha antes de chamar um humano e observar se isso reduz retrabalho.

Fonte: <https://claude.dev/blog/how-the-claude-code-team-thinks-about-verification/>

## Além do vídeo

- A reportagem foi publicada no The New Stack, cuja proprietária (Insight Partners) é também investidora da Anthropic.
