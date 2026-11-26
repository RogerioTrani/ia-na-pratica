# Karpathy recomenda esforço médio como padrão no Claude Code

_2026-11-22 · reportagem_

Andrej Karpathy, cofundador da OpenAI e ex-líder de direção autônoma da Tesla, publicou conselhos práticos para usar agentes de IA com menos token e menos erro. Esta apostila organiza oito dicas aplicáveis no Claude Code: esforço médio como padrão, objetivo claro em vez de listas longas, skill criada depois do trabalho, respostas no padrão ASD-STE100, filtros antes da IA, desconfiança de benchmarks, testes rigorosos como critério de aprovação e compreensão do sistema construído. Ao final, você saberá ajustar esforço e modelo, dar um objetivo claro ao agente, filtrar dados antes da análise, consultar o ECI da Epoch e instalar o Playwright MCP para testes automatizados.

## Como usar esta lista

As oito dicas a seguir partem dos conselhos de Andrej Karpathy para quem usa agentes de IA no dia a dia, com recomendações práticas de aplicação. O ponto em comum é simples: gastar menos token, errar menos e entender o que foi construído. Nenhuma dica exige mudar de ferramenta. Elas mudam a forma de pedir, filtrar, medir e testar.

A lista serve para quem já usa Claude Code, ou outro agente, e sente que gasta token demais, recebe respostas longas demais ou não sabe por que algo quebrou. Não serve para quem busca um modelo novo ou uma plataforma nova. Isto cobre método, não produto.

Por onde começar: rode a tarefa do dia no esforço médio e veja se ela passa. Se passar, mantenha. Se falhar, suba para o alto. Depois disso, dê um objetivo claro com /goal em vez de uma lista longa de regras.

- Por onde começar, passo 1: rode a tarefa recorrente no esforço médio e confira se o resultado está bom.
- Por onde começar, passo 2: se falhar, suba para o esforço alto e anote o nível mínimo que funcionou.
- Por onde começar, passo 3: troque a lista longa de instruções por um objetivo claro usando /goal.
- Por onde começar, passo 4: adicione um filtro simples antes da IA quando a base de dados for grande.
- Por onde começar, passo 5: exija testes rigorosos e dê ao agente uma ferramenta para verificar, como o Playwright MCP.

## Esforço médio como padrão

Usar sempre o modelo mais forte e o esforço máximo gasta token rápido e pode render resposta pensada demais, mais lenta e além do que você pediu. O conselho é começar no esforço médio, que oferece velocidade e conclui a tarefa de forma adequada. Só suba para o esforço alto quando existir uma tarefa que o médio não dê conta.

A mesma lógica vale para os modelos. Se uma tarefa roda bem com um modelo mais barato em esforço baixo, não faz sentido rodá-la com o modelo mais forte em esforço máximo. Para tarefas e skills que você usa todos os dias, teste qual é o nível de esforço ideal e qual é o modelo ideal. Depois de descobrir, você não precisa pensar nisso de novo.

Exemplo: uma tarefa que leva meia hora a uma hora por dia pode ser testada no esforço médio ou baixo. Se funcionar, você economiza token e tempo todos os dias. Se não funcionar, você sobe para o alto apenas nesse caso.

- Tecnologia: comandos /effort e /model do Claude Code.
- Como começar: rode a tarefa no esforço médio; se falhar, suba para o alto e troque o modelo com /model quando um mais barato bastar.
- Recorte: o ajuste de esforço vai de low até xhigh, além de max e auto, conforme a documentação oficial.

```
/effort
/model
```

Fonte: <https://code.claude.com/docs/en/commands>

## Objetivo claro, não lista longa

Listas longas de instruções podem se contradizer e deixar o agente em dúvida, com ambiguidade na tomada de decisão. O ideal é ter um pedido, um objetivo claro: o resultado final que você quer construir. O agente então trabalha para atingir esse objetivo, com liberdade para decidir o caminho.

Isso não significa nunca criar skills ou nunca escrever instruções. Significa evitar complexidade desnecessária. Quem não consegue escrever instruções muito longas e muito boas acaba criando regras que atrapalham a coerência. A recomendação é criar a skill depois de executar o trabalho do início ao fim, e não tentar prever todos os caminhos.

Exemplo: em vez de vinte regras sobre estilo, formato e ordem, peça o resultado final e deixe o agente buscar o caminho. Se faltar clareza, adicione uma regra por vez, depois de testar.

- Tecnologia: comando /goal do Claude Code.
- Como começar: escreva o resultado final desejado em uma frase e use /goal para defini-lo como meta do agente.

```
/goal
```

Fonte: <https://code.claude.com/docs/en/commands>

## Crie a skill depois do trabalho

Skill não precisa prever todos os caminhos. Faça o trabalho do início ao fim e, quando o resultado estiver bom, peça a skill com base no histórico da conversa. A skill nasce da experiência real, não de uma tentativa de prever o futuro.

Se vários agentes diferentes trabalharem na mesma skill, colete as informações necessárias e crie a skill com base na experiência de todos. Isso evita regras contraditórias e caminhos que nunca serão usados.

Exemplo: você pede passo a passo para o agente executar algo até o resultado final ficar muito bom. Quando estiver pronto, fala: crie uma skill baseada no histórico deste chat. A skill então reflete o que funcionou, não o que poderia funcionar.

- Tecnologia: criação de skill a partir do histórico da conversa no Claude Code.
- Como começar: execute a tarefa até o resultado ficar bom; depois peça ao agente para criar a skill baseada no histórico da conversa.

## ASD-STE100 para respostas diretas

Respostas em parágrafos enormes cansam, principalmente quando você aprova e reprova cada etapa. O padrão ASD-STE100, criado para manuais de manutenção de aviões, força frases curtas e claras. Quem escreve manuais de reparo de aeronaves percebeu que frases complexas podem levar a erros com consequências graves, e criou um protocolo de escrita concisa e direta.

Se a sua IA devolve respostas complexas demais, com palavras fora de contexto e parágrafos sofisticados para coisas banais, pedir respostas no padrão ASD-STE100 é um excelente recurso. Faz mais sentido quando você dialoga com a IA em tarefas longas e complexas, aprovando e reprovando etapas. Se a IA faz todo o trabalho sozinha, a forma de comunicar importa menos.

Exemplo: em vez de um parágrafo de cinco linhas explicando um passo, a resposta vem em frases curtas que você bate o olho e entende.

- Tecnologia: padrão ASD-STE100, protocolo de escrita para manuais de manutenção de aeronaves.
- Como começar: peça ao modelo para responder no padrão ASD-STE100 quando sentir que as respostas estão complexas demais.
- Mais informações: asd-ste100.org

Fonte: <https://asd-ste100.org>

## Filtros antes da IA

Muita gente manda base de dados inteira para a IA quando um filtro simples bastaria. Exportar um banco inteiro e analisar tudo com IA custa muito mais do que criar um filtro que traga exatamente as informações que você quer analisar. Muito raramente você precisa analisar 100% de um banco imenso.

Exemplo concreto: você pesquisa mil, mil e quinhentos ou dois mil vídeos com scraping para postar algo similar. Transcrever e analisar cada frase e cada frame desses vídeos, mesmo com modelos baratos, tem custo significativo. Um filtro simples que barre vídeos com menos de um milhão de visualizações reduz três mil análises a trinta, quarenta ou cinquenta vídeos.

O filtro roda antes da IA entrar no pipeline. Pode ser um script simples em Python ou qualquer código. O modelo entra só com os dados que valem a análise. Isso economiza token em pipelines recorrentes.

- Tecnologia: script ou filtro antes do modelo, em qualquer linguagem.
- Como começar: identifique o critério que descarta o que não importa e aplique antes de chamar a IA.
- Recorte: o exemplo usa o corte de um milhão de visualizações; ajuste o critério ao seu caso.

## Desconfie dos benchmarks

Notas de lançamento de modelos novos costumam vir da própria empresa que oferece o modelo. Algumas vezes o próprio modelo foi treinado para ir bem em determinados benchmarks. Por isso, não confie só na nota do lançamento.

A recomendação é consultar o ECI da Epoch, uma espécie de meta-benchmark. Ele combina vários benchmarks dentro de uma lógica matemática coerente e produz uma escala de capacidade geral dos modelos de IA. As informações tendem a ser mais confiáveis do que as divulgadas na página do modelo no lançamento.

Exemplo: em vez de escolher um modelo pela nota que a empresa publicou, compare os modelos no ECI da Epoch, veja qual tem capacidade geral maior e depois teste no seu caso.

- Tecnologia: Epoch Capabilities Index (ECI).
- Como começar: acesse epoch.ai/eci e compare os modelos pela capacidade geral combinada.
- Recorte: o ECI combina vários benchmarks; não é um benchmark único.

Fonte: <https://epoch.ai/eci>

## Testes rigorosos como critério de aprovação

Um pedido simples funciona se o ciclo só termina quando os testes passam. O segredo não está mais no prompt, está na metodologia de avaliação. Testes rigorosos e um loop que inclui os testes como requisito de aprovação reduzem a chance de problemas no futuro.

Não basta definir testes perfeitos. É preciso fornecer as ferramentas adequadas para o agente executar os testes de verdade. Se o agente não consegue acessar o ambiente correto, os testes não têm valor. Exemplo clássico: um navegador automatizado ligado à IA, que confere o site ou o app web depois de pronto, fingindo ser o usuário.

O Playwright MCP é uma ferramenta de automação de navegador ligada à IA. Ele testa o app no navegador usando a árvore de acessibilidade do Playwright, sem depender de modelos de visão. Requer Node.js 20 ou mais novo e um cliente MCP, como o Claude Code.

- Tecnologia: Playwright MCP, servidor MCP de automação de navegador.
- Como começar: instale com o comando oficial e peça ao agente para testar o app no navegador.
- Requisito: Node.js 20 ou mais novo.

```
claude mcp add playwright npx @playwright/mcp@latest
```

Fonte: <https://github.com/microsoft/playwright-mcp>

## Não terceirize a sua compreensão

Criar sistemas extremamente complexos com linguagem natural sem entender o que acontece cobra o preço depois. Quando o sistema quebra ou para de obedecer, você não sabe por quê. A compreensão do que a IA constrói é o que permite saber o que fazer quando algo falha.

Você não precisa saber programar, mas precisa entender system design: como uma coisa se relaciona com a outra. Quanto mais complexos os pipelines ou as ambições de construção com IA, mais você precisa identificar onde a IA está vacilando.

Exemplo: você dita para a IA e vai encontrando problemas. Se não acompanha a arquitetura, quando algo quebra você reclama que a IA não obedece mais. Com o hábito de entender o que a IA cria, você evolui mais rápido e gosta mais de usar a IA, porque entende a lógica por trás do que foi construído.

- Tecnologia: compreensão de system design e supervisão da IA.
- Como começar: peça à IA que explique a arquitetura do que construiu e confira antes de avançar.

## Os princípios por trás dos conselhos

Um repositório público reúne os conselhos de Karpathy em um único arquivo CLAUDE.md, derivado das observações dele sobre falhas comuns de LLMs em código. O arquivo organiza quatro princípios que endereçam problemas específicos.

Pensar antes de codar: não assumir, não esconder confusão, explicitar trade-offs. Simplicidade primeiro: código mínimo que resolve o problema, sem abstração especulativa. Mudanças cirúrgicas: tocar só o necessário, limpar só a própria bagunça. Execução orientada por objetivo: definir critérios de sucesso e iterar até verificar.

O insight central é que LLMs são bons em iterar até atingir objetivos específicos. Não diga o que fazer, dê critérios de sucesso e observe. As diretrizes tendem à cautela em vez de velocidade; para tarefas triviais, use julgamento.

- Tecnologia: arquivo CLAUDE.md com os quatro princípios.
- Como começar: adicione os princípios ao CLAUDE.md do projeto ou instale como plugin do Claude Code.
- Recorte: licença MIT; pode ser mesclado com instruções específicas do projeto.

Fonte: <https://github.com/multica-ai/andrej-karpathy-skills>

## Cuidados

Antes de confiar em um conselho, confira a fonte. Digite comandos, links e nomes exatamente como aparecem: um comando alterado pode falhar ou fazer outra coisa na sua máquina.

Os links oficiais são: comandos do Claude Code em code.claude.com/docs/en/commands, ASD-STE100 em asd-ste100.org, ECI da Epoch em epoch.ai/eci e Playwright MCP em github.com/microsoft/playwright-mcp. O Playwright MCP exige Node.js 20 ou mais novo e um cliente MCP.

O que é fato e o que é hipótese: os números do exemplo de filtros (um milhão de visualizações, três mil vídeos reduzidos a trinta ou cinquenta) são ilustrativos, não medição de um estudo. O ECI combina benchmarks, mas não substitui avaliação no seu caso. A recomendação de esforço médio como padrão é conselho, não regra absoluta: tarefas difíceis ainda exigem esforço alto.

Onde entra revisão humana: na criação de skills, na definição de testes e na compreensão da arquitetura. A IA executa, mas o julgamento sobre o que vale a pena construir e manter é seu.

- Confira os comandos /effort, /model e /goal na documentação oficial antes de usar em produção.
- Confira a versão do Node.js (20 ou mais) antes de instalar o Playwright MCP.
- Não trate benchmarks de lançamento como prova; consulte o ECI da Epoch e teste no seu caso.
- Revise skills criadas a partir do histórico antes de reutilizá-las em outros projetos.

## Glossário

- Agente: programa de IA que executa tarefas de forma autônoma, usando ferramentas e código.
- ASD-STE100: padrão de escrita criado para manuais de manutenção de aeronaves, com frases curtas e claras.
- Benchmark: teste padronizado para medir o desempenho de um modelo de IA.
- ECI (Epoch Capabilities Index): meta-benchmark da Epoch que combina vários benchmarks com lógica matemática para medir capacidade geral de modelos.
- MCP (Model Context Protocol): protocolo que conecta modelos de IA a ferramentas externas, como navegadores.
- Playwright MCP: servidor MCP que automatiza navegador usando a árvore de acessibilidade do Playwright.
- Skill: conjunto de instruções reutilizável que orienta o agente em uma tarefa específica.
- System design: forma como as partes de um sistema se relacionam entre si.
- Token: unidade de texto processada pelo modelo; mede custo e consumo.
- Scraping: coleta automatizada de dados de páginas ou plataformas.
- PR (pull request): proposta de mudança de código para revisão.

## Para onde ir depois

Aplique as dicas em uma tarefa recorrente esta semana. Comece pelo esforço médio, dê um objetivo claro, filtre antes da IA e exija testes. Depois, crie uma skill a partir do histórico quando o resultado estiver bom.

Consulte o ECI da Epoch antes de trocar de modelo. Instale o Playwright MCP se você constrói apps web. Peça respostas no padrão ASD-STE100 quando sentir que a IA está complexa demais.

- Praticar: rode uma tarefa diária no esforço médio e anote o nível mínimo que funciona.
- Praticar: substitua uma lista longa de regras por um objetivo claro com /goal.
- Praticar: adicione um filtro simples antes da IA em um pipeline existente.
- Praticar: instale o Playwright MCP e peça ao agente para testar seu app no navegador.
- Praticar: peça ao agente para criar uma skill a partir do histórico de uma tarefa bem-sucedida.
- Aprofundar: leia os quatro princípios de Karpathy no repositório multica-ai/andrej-karpathy-skills.

## Além do vídeo

- Consultar vários modelos e fazê-los debater entre si antes de tomar uma decisão, em vez de consultar um só.
- Criar aplicativos nativos para agentes, com APIs fáceis para que o agente faça tudo por linguagem natural.
- Skill Lightspeed Learning para aprender conceitos com texto, diálogo por voz, vídeo narrado com diagrama e teste final.
- Expandir horizontes: a IA torna possível o que antes era impossível ou inviável, não só automatiza trabalho.
- Compreensão de system design mesmo sem saber programar, para identificar onde a IA vacila.
- Paperclip como ferramenta para debate multimodelos de forma simples.
