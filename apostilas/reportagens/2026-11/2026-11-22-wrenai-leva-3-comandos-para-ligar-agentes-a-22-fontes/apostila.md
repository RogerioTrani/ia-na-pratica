# WrenAI leva 3 comandos para ligar agentes a 22 fontes

_2026-11-22 · reportagem_

O WrenAI, da Canner, é um motor de BI generativo de código aberto que dá a agentes como Claude Code, Cursor e clientes MCP uma camada semântica governada. Com ela, o agente gera SQL a partir do significado das métricas, não só do esquema do banco. A instalação leva três comandos: instalar a CLI, ensinar o agente sobre o Wren e fazer um pedido em linguagem comum. A mesma camada atende 22+ fontes de dados.

## O que é o WrenAI

O WrenAI é um motor de BI generativo (GenBI) de código aberto. Ele funciona dentro dos agentes que você já usa, como Claude Code, Cursor, Cline, Codex e clientes MCP.

O esquema diz ao agente onde o dado está. O Wren diz o que ele significa: métricas aprovadas, enums, unidades, junções e exemplos. Essas definições ficam em YAML e Markdown, num repositório seu, e passam por revisão como qualquer código.

Fonte: <https://github.com/Canner/WrenAI>

## Passo 1: instalar a CLI

Instale o pacote wrenai. Os extras de conexão entram por banco, conforme a sua necessidade. O exemplo abaixo traz o conector do Postgres e a memória.

Fonte: <https://pypi.org/project/wrenai/>

## Passo 2: ensinar o agente sobre o Wren

O comando instala só um pequeno roteiro de descoberta, de cerca de 50 linhas. O agente busca os guias completos na CLI quando precisar, então as instruções sempre batem com a versão instalada.

Funciona com Claude Code, Cursor, Cline, Codex e outros agentes.

```
npx skills add Canner/WrenAI
```

Fonte: <https://github.com/Canner/WrenAI>

## Passo 3: peça ao agente

Abra o agente numa pasta de projeto e faça o pedido abaixo. O agente verifica o ambiente, cria o perfil de conexão, monta o projeto e roda uma primeira consulta.

Sem banco à mão, use o exemplo de loja que acompanha o projeto.

- Com Postgres: "Use Wren to set up my Postgres database."
- Sem banco: "Use Wren with the bundled jaffle_shop sample."

Fonte: <https://docs.getwren.ai/oss/get_started/quickstart>

## Depois da conexão

Três pedidos cobrem o ciclo completo do GenBI.

- Contexto: "Enrich my Wren project with the business context in raw/." O agente roda wren skills get enrich-context e grava definições, exemplos e memória como arquivos revisáveis.
- Consulta: "Who are our top 10 customers by sales this quarter?" O agente recupera o contexto do MDL e as consultas anteriores, escreve o SQL governado e executa com wren query.
- Dashboard: "Turn that into a dashboard I can filter and share, deployed to Vercel." O agente roda wren skills get genbi e devolve uma URL no seu Vercel ou Cloudflare Pages.

Fonte: <https://github.com/Canner/WrenAI>

## Por que o agente erra menos

Tudo é planejado contra a camada semântica, escrita em MDL (Modeling Definition Language). Antes de executar, o SQL passa por validação de plano (dry-plan), com limite de linhas e erros estruturados com dicas.

O motor roda sobre Apache DataFusion e atende BigQuery, Snowflake, PostgreSQL, ClickHouse, Amazon Redshift, Databricks, DuckDB e outras fontes, 22+ no total.

Fonte: <https://github.com/Canner/WrenAI>

## Licença: o que é aberto e o que é comercial

Motor, SDK e skills usam a licença Apache-2.0. Podem ser hospedados por você.

- Comercial: controle de acesso por linha e coluna, com usuários e grupos
- Comercial: interface de GenBI e dashboards, embutidos e via APIs
- Comercial: segurança avançada, auditoria, suporte e SLAs

Fonte: <https://github.com/Canner/WrenAI>

## Links oficiais

- Repositório: https://github.com/Canner/WrenAI
- Pacote no PyPI: https://pypi.org/project/wrenai/
- Documentação: https://docs.getwren.ai
- Quickstart: https://docs.getwren.ai/oss/get_started/quickstart

## Além do vídeo

- Git Sync: com wren cloud create ou wren cloud link, o git push e o git pull levam o projeto para um deploy de GenBI da equipe, no Wren Cloud ou autohospedado.
- Cada push usa um token novo que expira em 600 segundos; a chave durável fica em ~/.wren/cloud.yml e nunca vai para o git.
- Os comandos wren ask "<question>" --guided e --direct embrulham uma pergunta para um agente mais fraco ou mais forte.
- Os SDKs de agentes wren-langchain (LangChain e LangGraph) e wren-pydantic.
- O Wren GenBI Classic, o app antigo com Docker, ficou na branch legacy/v1 e não recebe novos recursos nem correções de segurança.
