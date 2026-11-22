# Knowledge factory fecha loop entre agentes e curador

_2026-11-22 · reportagem_

O gargalo de IA nas empresas não é modelo nem contexto: é o conhecimento tácito de como a empresa opera, espalhado e implícito. A knowledge factory coleta, cura e mantém esse conhecimento para os agentes, em um loop onde o trabalho revela o que falta. Comece por um fluxo recorrente, veja onde o agente trava e feche a lacuna.

## O problema: conhecimento tácito e espalhado

O que torna seus melhores funcionários eficientes está na cabeça deles: quem procurar, onde responder, por que fazer de um jeito. Esse conhecimento é tácito e espalhado, às vezes só na mente deles, às vezes em documentos variados. Para a IA funcionar na empresa, é preciso coletar, curar e manter uma representação desse conhecimento para passar aos agentes.

Fonte: <https://www.langchain.com/blog/knowledge-factory>

## Contexto não é conhecimento

Contexto é o que o agente tem disponível durante a tarefa. Conhecimento é o entendimento reutilizável que mantemos para que ele acerte: o que uma métrica significa, qual fonte confiar, como tratar uma situação. A factory transforma documentos e experiência em conhecimento que vira contexto para trabalhos futuros. Conhecimento é uma forma de contexto, mas geralmente não a única.

Fonte: <https://www.langchain.com/blog/knowledge-factory>

## Três tipos de conhecimento

A factory mantém três tipos de conhecimento.

- Skills: procedimentos, instruções e scripts para fazer o trabalho do jeito da empresa.
- Domain knowledge: definições, políticas e fatos sobre produtos, clientes, concorrentes e organização.
- Data access guidance: quais fontes usar, onde os dados estão e como consultá-los.

Fonte: <https://www.langchain.com/blog/knowledge-factory>

## Agentes sinalizam lacunas

Um dos melhores jeitos de descobrir conhecimento faltante é ter o agente sinalizar enquanto trabalha. Quando não acha ou acha errado, marca a falha e sugere a correção.

Fonte: <https://www.langchain.com/blog/knowledge-factory>

## Curator agent

O conhecimento não deve ser mantido manualmente nem pelos agentes que o usam. Um curator agent roda em background, acessa as fontes brutas e as traces, e cura tudo.

Fonte: <https://www.langchain.com/blog/knowledge-factory>

## Armazenamento: o menos importante

O armazenamento é o menos importante. O que importa é o loop entre agentes e curador.

- Skills no GitHub (github.com), Notion (notion.so), Context Hub (docs.langchain.com/langsmith/use-the-context-hub) ou Neo4j (neo4j.com); formato menos importante que o loop.

Fonte: <https://www.langchain.com/blog/knowledge-factory>

## Comece fechando um loop

O objetivo não é documentar tudo antes de começar. É construir um sistema onde fazer o trabalho revela o que falta, e fechar a lacuna melhora o próximo trabalho. Comece por um fluxo recorrente, veja onde o agente trava e feche a lacuna.

Fonte: <https://www.langchain.com/blog/knowledge-factory>

## Além do vídeo

- A ideia de software factory: os melhores engenheiros constroem a fábrica (os sistemas) e os agentes fazem o trabalho; o conhecimento geral segue o mesmo caminho.
- Exemplo ponta a ponta: um agente preparando um relatório de receita, com dados no BigQuery e no Salesforce, coluna renomeada detectada na hora e curator atualizando skills à noite.
- Dados que mudam rápido não precisam de cópia: se a fonte de verdade já é completa e atualizada, ensine o agente a acessá-la (Snowflake, Databricks).
- Memória: a indústria convergiu em skills para memória procedural; memória semântica ainda não tem padrão (OKF?) e não vale prescrever formato agora.
- Os agentes que usam o conhecimento não devem mantê-lo: só o curator mantém, para evitar contradições.
