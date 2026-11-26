# WrenAI leva 3 comandos para ligar agentes a 22 fontes

_2026-11-22 · reportagem_

O WrenAI é um motor de BI generativo (GenBI) de código aberto, mantido pela Canner, que dá aos agentes de IA uma camada semântica governada em MDL e uma camada de contexto, para transformar perguntas em linguagem natural em SQL correto e publicar a resposta como dashboard compartilhável. A instalação leva três comandos (pip install wrenai, npx skills add Canner/WrenAI e um pedido em linguagem natural ao agente) e funciona com mais de 50 agentes e mais de 22 fontes de dados sobre um único motor baseado em Apache DataFusion. Definições de métricas, enums, unidades e junções ficam em arquivos YAML e Markdown versionados em um repositório seu. O motor, o SDK e as skills usam a licença Apache-2.0; controle de acesso por linha e coluna, interface de dashboards e suporte são comerciais. Depois de ler, você saberá o que o projeto é, como começar, como ele se compara a alternativas e o que conferir antes de adotar.

## O fato

O WrenAI é um motor de BI generativo (GenBI) de código aberto, mantido pela Canner. Ele dá aos agentes de IA que você já usa (Claude Code, Cursor, clientes MCP, LangChain, Cline, Codex e mais de 50 outros) uma camada semântica governada e uma camada de contexto de IA. O resultado: perguntas em linguagem natural viram SQL correto, a resposta vira um dashboard compartilhável e tudo fica dentro dos limites que você definiu.

O projeto está no GitHub em github.com/Canner/WrenAI e o pacote está no PyPI em pypi.org/project/wrenai. A documentação oficial fica em docs.getwren.ai.

Fonte: <https://github.com/Canner/WrenAI>

## Por que isso importa

Agentes de IA escrevem SQL, mas muitas vezes erram o que cada métrica significa. Um esquema de banco diz onde o dado está. O Wren diz o que ele significa: definições aprovadas de métricas, enums, unidades, junções, exemplos e o conhecimento informal que fica em docs e threads de chat.

Essas definições vivem como arquivos YAML e Markdown versionados em um repositório que você controla. Você revisa em pull request, compara versões e leva com você se mudar de ferramenta.

Fonte: <https://github.com/Canner/WrenAI/blob/main/README.md>

## Como a camada semântica funciona

A camada semântica do Wren se expressa em MDL (Modeling Definition Language): uma definição em Git do que os dados significam, não apenas de onde vivem. Cada resposta e cada dashboard é planejado contra essa definição.

Modelos, colunas, relacionamentos e views descrevem a forma dos dados, separados de um warehouse específico. Cubos e métricas guardam definições aprovadas e reutilizáveis, para que "receita" signifique a mesma coisa em todo lugar. Contexto além do esquema (enums, unidades, junções aprovadas, definições) fica em instructions.md e queries.yml.

Fonte: <https://github.com/Canner/WrenAI/blob/main/README.md>

## 22+ fontes em um único motor

A mesma camada vale para mais de 22 fontes de dados, todas rodando sobre um único motor baseado no Apache DataFusion: BigQuery, Snowflake, PostgreSQL, ClickHouse, Amazon Redshift, Databricks, DuckDB e outros.

Isso evita um conector diferente por banco e um significado diferente por ferramenta.

Fonte: <https://github.com/Canner/WrenAI/blob/main/README.md>

## Três comandos para começar

O quickstart oficial promete três comandos; depois deles, o agente faz o resto.

1. instale a CLI com pip install wrenai. Para cada banco, acrescente extras de conexão, como o do Postgres.
2. ensine o agente sobre o Wren com npx skills add Canner/WrenAI. Isso instala um stub de descoberta de cerca de 50 linhas; o agente busca os guias completos na CLI quando precisar, para que as instruções sempre batam com a versão instalada.
3. abra o agente em uma pasta de projeto e peça: "Use Wren to set up my Postgres database." O agente verifica o ambiente, cria o perfil de conexão, monta o projeto e roda uma primeira consulta.
4. Sem banco à mão, peça: "Use Wren with the bundled jaffle_shop sample" e rode o mesmo fluxo contra um warehouse de exemplo real.
5. Instalação lenta do pip na China continental: aponte o pip para um espelho com a opção -i; o README do projeto indica o endereço.

```
pip install wrenai
pip install "wrenai[postgres,memory]"
npx skills add Canner/WrenAI
```

Fonte: <https://github.com/Canner/WrenAI/blob/main/README.md>

## O loop GenBI: três prompts depois de conectado

Depois de conectado, três prompts cobrem o ciclo GenBI inteiro.

- Enriquecer: "Enrich my Wren project with the business context in raw/." Roda `wren skills get enrich-context`. Escreve definições, exemplos e memória como arquivos revisáveis.
- Perguntar: "Who are our top 10 customers by sales this quarter?" Recupera o contexto MDL e consultas anteriores, escreve SQL governado e executa via `wren query`.
- Publicar: "Turn that into a dashboard I can filter and share, deployed to Vercel." Roda `wren skills get genbi`. Monta um app no navegador e devolve uma URL ao vivo na sua conta Vercel ou Cloudflare Pages.

Fonte: <https://github.com/Canner/WrenAI/blob/main/README.md>

## Memória e conhecimento

O Wren guarda conhecimento e memória versionados: instructions.md e queries.yml, mais um índice de memória local em LanceDB com busca híbrida.

Isso permite que o agente recupere contexto passado e exemplos aprovados antes de escrever SQL.

Fonte: <https://github.com/Canner/WrenAI/blob/main/README.md>

## SDKs e integração com agentes

O Wren oferece SDKs para os principais frameworks de agentes: wren-langchain (LangChain/LangGraph) e wren-pydantic (Pydantic AI), além de uma integração Python de referência. O motor é wren-core (Rust, baseado em Apache DataFusion), com bindings Python (wren-core-py, PyPI wren-core) e uma build WebAssembly (wren-core-wasm, npm).

O motor expõe primitivas de execução governada: funções, validação de plano a seco (dry-plan), limites de linha e erros estruturados com dicas.

Fonte: <https://github.com/Canner/WrenAI/blob/main/README.md>

## Dashboards no navegador

Os dashboards do GenBI são apps montados pelo agente, rodando no navegador, powered by wren-core-wasm, e podem ser publicados na Vercel ou no Cloudflare Pages.

A resposta deixa de ser só SQL e vira um dashboard filtrável e compartilhável, com URL ao vivo.

Fonte: <https://github.com/Canner/WrenAI/blob/main/README.md>

## Git Sync: do laptop ao time

Tudo o que o Wren escreve no seu laptop são arquivos YAML e Markdown em um repositório seu. O Git Sync transforma esse mesmo repositório em uma implantação GenBI governada para o time, na Wren Cloud ou auto-hospedada, inclusive em ambiente isolado (air-gapped).

Vincule o diretório uma vez com `wren cloud create` ou `wren cloud link` (no bloco abaixo, use um dos dois primeiros comandos). Depois, `git push` e `git pull` são a interface inteira. Uma mudança em net_revenue aparece como diff legível em um pull request no GitHub, GitLab, Bitbucket ou no seu remoto. Você roda CI e promove staging para produção como código de aplicação.

Você mantém o repositório sempre: pode clonar, fazer backup, alimentar outra ferramenta ou sair com ele. Nenhuma credencial reutilizável fica em disco. Cada push autentica com um token novo que expira em 600 segundos. A chave durável fica em ~/.wren/cloud.yml (modo 0600) e nunca é entregue ao git.

```
wren cloud create
wren cloud link
git push
```

Fonte: <https://github.com/Canner/WrenAI/blob/main/README.md>

## Linha do tempo do projeto

- 2026-05-07: o Wren Engine foi fundido neste repositório, sob core/. O repositório anterior Canner/wren-engine foi arquivado.
- O produto anterior, baseado em chat, virou Wren GenBI Classic, preservado no branch legacy/v1 (tag v1-final), sem novas funcionalidades nem correções de segurança.
- Para uma versão hospedada e mantida dessa experiência, existe o Wren AI Commercial.

Fonte: <https://github.com/Canner/WrenAI/blob/main/README.md>

## O que é open-source e o que é comercial

O motor neste repositório (camada semântica MDL, text-to-SQL governado, servidor MCP, CLI, mais de 22 conectores) é Apache-2.0, gratuito para sempre e auto-hospedável.

Os seguintes itens são comerciais, entregues como Wren AI Cloud ou Enterprise Plus auto-hospedado:

- Controle de acesso por linha e coluna, com usuários e grupos.
- Interface GenBI, dashboards, embedded e APIs.
- Cenários de IA (harnesses): GenBI Apps, Agentic Mode, preparação de contexto assistida por IA.
- Segurança e auditoria avançadas, suporte e SLAs, além de implantação em nuvem, VPC e ambiente isolado (air-gapped).
- O mesmo motor por baixo. Seu MDL fica no seu Git de qualquer forma.

Fonte: <https://github.com/Canner/WrenAI/blob/main/README.md>

## Como o Wren se compara

A comparação oficial coloca quatro opções lado a lado.

- Agente LLM puro: escreve SQL (muitas vezes errado), não conhece definições de negócio, não gera nem publica dashboards, funciona nos seus agentes, contexto não é aberto nem versionável, execução não governada.
- BI tradicional: não escreve SQL, conhece definições parcialmente e dentro da ferramenta, gera dashboards manualmente dentro da ferramenta, não funciona nos seus agentes, contexto não é aberto nem amigável ao Git, execução governada por conector.
- Camada semântica pura: não escreve SQL, conhece o esquema, não gera dashboards, não funciona nos seus agentes, contexto apenas parcialmente aberto e revisável, execução governada só das definições.
- WrenAI: escreve SQL governado, conhece definições de negócio mais conhecimento não esquemático, gera e publica dashboards pelo agente, funciona nos seus agentes (Claude Code, Cursor, MCP), contexto aberto, revisável e amigável ao Git, execução governada em mais de 22 fontes.

Fonte: <https://github.com/Canner/WrenAI/blob/main/README.md>

## Para quem é (e para quem não é)

- Para você se quer que agentes de IA produzam BI confiável, respostas e dashboards, e não só SQL plausível.
- Para você se a lógica de negócio (definições, enums, unidades, junções aprovadas) vive fora do banco e seus agentes erram.
- Para você se quer uma camada de contexto aberta, revisável e versionada, usável por todo agente e toda pessoa, sem ficar atrás da interface de um fornecedor.
- Pule o Wren se precisar apenas de um gráfico pontual de um único CSV, ou se estiver satisfeito em deixar o agente chutar SQL sem governança.

Fonte: <https://github.com/Canner/WrenAI/blob/main/README.md>

## Números do projeto

- 102 observadores (watchers).
- 2.775 commits.
- Mais de 50 agentes suportados.
- Mais de 22 fontes de dados.
- Stub de descoberta de cerca de 50 linhas.

Fonte: <https://github.com/Canner/WrenAI/blob/main/README.md>

## O que conferir antes de confiar

- A licença Apache-2.0 cobre o motor, o SDK e as skills. Controle de acesso por linha e coluna, interface de dashboards e suporte são comerciais. Confira o limite publicado antes de assumir que um recurso está incluído.
- O Git Sync exige vincular o diretório uma vez (`wren cloud create` ou `wren cloud link`) e depende da Wren Cloud ou de instalação auto-hospedada para o deploy governado do time.
- O token de push expira em 600 segundos. A chave durável fica em ~/.wren/cloud.yml com modo 0600. Não compartilhe esse arquivo.
- O produto anterior (chat-first) não recebe mais funcionalidades nem correções de segurança. Se você depende dele, planeje a migração.
- Confirme versão, disponibilidade e preço na documentação oficial antes de adotar em produção.

Fonte: <https://github.com/Canner/WrenAI/blob/main/README.md>

## Glossário

- GenBI (Generative BI): BI produzido por agentes de IA. Em vez de uma pessoa montar gráficos à mão, um agente gera SQL governado, publica um dashboard e compartilha, com base em uma camada de contexto de IA para que a saída seja confiável e não apenas plausível.
- Camada semântica: definição governada do que os dados significam, expressa em MDL, com modelos, métricas e relacionamentos.
- Camada de contexto de IA: conhecimento revisável e versionado que agentes precisam e que o esquema não fornece: semântica de negócio, definições aprovadas, exemplos, memória e governança.
- MDL (Modeling Definition Language): linguagem de definição de modelagem do Wren, em arquivos YAML e Markdown versionados em Git.
- Text-to-SQL governado: pergunta vira SQL planejado contra a camada semântica (MDL) e validado a seco antes da execução.
- Apache DataFusion: motor de consulta em Rust sobre o qual o Wren roda suas mais de 22 fontes.
- Dry-plan validation: validação do plano de consulta antes de executar, para manter o SQL dentro dos limites.
- Git Sync: fluxo em que o repositório local de definições é publicado e sincronizado com a Wren Cloud ou instalação auto-hospedada via git push/pull.
- wren-core-wasm: build WebAssembly do motor, que roda os dashboards no navegador.
- LanceDB: tecnologia do índice de memória local do Wren, com busca híbrida.
- jaffle_shop: amostra de warehouse que acompanha o projeto, para testar sem banco próprio.

Fonte: <https://github.com/Canner/WrenAI/blob/main/README.md>

## Para onde ir depois

- Ler o quickstart oficial em docs.getwren.ai/oss/get_started/quickstart.
- Ver o guia de build e deploy de um app GenBI.
- Conectar seu banco: Postgres, BigQuery, Snowflake, DuckDB e outros.
- Explorar os SDKs de agentes (wren-langchain, wren-pydantic).
- Entrar no Discord ou nas GitHub Discussions para dúvidas e votação de roadmap.
- Praticar: instalar a CLI, rodar o fluxo com a amostra jaffle_shop e fazer uma pergunta em linguagem natural.

Fonte: <https://github.com/Canner/WrenAI/blob/main/README.md>

## Links citados

- https://docs.getwren.ai
- https://docs.getwren.ai/oss/get_started/quickstart
- https://pypi.org/project/wrenai/

## Além do vídeo

- Comandos do dia a dia: `wren skills get onboarding`, `wren query --sql '...'`, `wren ask "<pergunta>" --guided` ou `--direct`.
- Estrutura do repositório: core/, sdk/, skills/, docs/, examples/, misc/, scripts/, evals/.
- Contribuição aberta: issues, PRs, conectores, integrações de SDK e correções de docs; existe guia de contribuidor e mapa de arquitetura; issues marcadas como good first issue.
- Comunidade: Discord, GitHub Discussions, Twitter/X e blog, além de releases e roadmap votável.
- Roadmap declarado: primitivas de correção ponta a ponta (profiling de valores, recuperação rica, erros estruturados, executor de eval dourado) e SDKs de primeira classe para os principais frameworks de agentes.
- Licenças no repositório além da Apache-2.0: AGPL-3.0 e CC-BY-4.0.
- Topics do repositório incluem context-engineering, rag, mcp, text-to-sql, text2sql e genbi.
