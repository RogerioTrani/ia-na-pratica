# Claude analisa a Apple em 5 etapas com plugin grátis

_2026-11-23 · noticia_

A Anthropic liberou de graça o pacote de plugins Financial Services para o Claude, que permite montar um relatório de análise de ações em cinco etapas, do estudo do negócio a um documento de 30 a 50 páginas. Esta apostila explica o que é o pacote, como instalar no Claude Code, como funciona cada etapa e o que conferir antes de confiar nos números. Ao final, você saberá instalar o pacote, pedir ao Claude um relatório para a empresa que escolher e validar os resultados. O código é aberto e está no repositório github.com/anthropics/financial-services, com mais de 41.000 estrelas.

## Como usar esta lista

O pacote Financial Services é um conjunto de plugins da Anthropic para fluxos de trabalho financeiros: pesquisa de ações, modelagem, fusões e aquisições, private equity, administração de fundos e operações. Tudo é código aberto, em markdown e JSON, sem etapa de build, e está disponível a partir da mesma fonte como plugin no Claude Cowork ou implantado pela API Claude Managed Agents; os plugins também podem ser instalados no Claude Code.

A lista abaixo cobre os plugins verticais que compõem o pacote. Cada item traz o que o plugin faz, para que serve, quando escolher e como começar. O pacote é ferramenta de estudo e de trabalho de analista: não faz recomendação de investimento, não executa transações e não lança nada no razão contábil. Toda saída fica à espera de revisão e aprovação humana, por um profissional qualificado.

- Por onde começar: instale primeiro financial-analysis, que carrega as habilidades compartilhadas e todos os conectores de dados, e depois equity-research, que traz a habilidade Initiating Coverage.
- Para cada item: leia o que faz, veja a tecnologia que usa e siga o caminho de instalação no repositório oficial.
- Se o objetivo é só o relatório de ações, o par financial-analysis + equity-research basta; os demais plugins são opcionais conforme o fluxo de trabalho.

Fonte: <https://github.com/anthropics/financial-services>

## O fato

A Anthropic, empresa americana criadora do assistente de inteligência artificial Claude, liberou de graça um pacote de plugins financeiros. Dentro dele está a habilidade Initiating Coverage, que monta um relatório de análise de ações em cinco etapas para a empresa que você escolher, por exemplo a Apple.

O repositório é aberto e já passou de 41.000 estrelas no GitHub. O pacote se chama Financial Services, é da Anthropic e fica no GitHub no endereço github.com/anthropics/financial-services.

Fonte: <https://github.com/anthropics/financial-services>

## O que é a habilidade Initiating Coverage

Initiating Coverage é o nome do relatório que o analista escreve ao começar a acompanhar uma empresa. A habilidade que produz esse relatório vem no plugin equity-research, um dos plugins verticais do pacote.

Você escolhe a ação, como a Apple, e pede uma etapa de cada vez. Cada etapa entrega o seu arquivo. O Claude conduz o trabalho em cinco etapas, e cada uma se apoia no que foi levantado na anterior.

Fonte: <https://github.com/anthropics/financial-services/tree/main/plugins/vertical-plugins/equity-research>

## Por que isso importa

Relatório de análise de ações costuma ser trabalho de banco, cobrado caro. Ter um fluxo desse tipo disponível de graça, em código aberto, permite estudar uma empresa com mais profundidade.

Fonte: <https://github.com/anthropics/financial-services>

## Os números

Os números abaixo vêm do fluxo Initiating Coverage e do repositório. O que cada um significa e o que não dá para concluir dele está anotado.

- 41.000 estrelas no GitHub: medida de popularidade do repositório, não de qualidade ou segurança do código.
- 30 a 50 páginas: tamanho do relatório final que reúne pesquisa, planilha, avaliação e gráficos.
- 25 a 35 gráficos: quantidade gerada para ilustrar a análise da ação.
- 6 abas: planilha Excel montada a partir dos balanços oficiais da empresa.
- 5 etapas: sequência do fluxo, pedida uma por vez, cada uma entregando seu arquivo.
- 11 conectores de dados: quantidade que o repositório informa para o plugin core financial-analysis, embora a tabela de integrações liste 12 provedores.
- 9 plugins verticais: total de bundles por vertical financeira no pacote.
- 10 agentes end-to-end: quantidade de agentes nomeados para fluxos completos.

Fonte: <https://github.com/anthropics/financial-services>

## Instalação no Claude Code

A instalação é feita em três comandos no Claude Code. Os comandos são copiados exatamente como aparecem no repositório oficial.

1. Adicione o marketplace com o primeiro comando. Resultado esperado: o repositório anthropics/financial-services fica disponível como fonte de plugins.
2. Instale o plugin core financial-analysis. Resultado esperado: habilidades de modelagem e os 11 conectores de dados passam a estar disponíveis.
3. Instale o plugin equity-research. Resultado esperado: a habilidade Initiating Coverage e os comandos de pesquisa de ações ficam disponíveis.
4. Diga ao Claude qual ação quer estudar, por exemplo a Apple, e peça a primeira etapa. Resultado esperado: o Claude conduz o trabalho em cinco etapas, uma por vez, cada uma entregando seu arquivo.

```
claude plugin marketplace add anthropics/financial-services
claude plugin install financial-analysis@claude-for-financial-services
claude plugin install equity-research@claude-for-financial-services
```

Fonte: <https://github.com/anthropics/financial-services>

## Como isso funciona: as cinco etapas

O fluxo Initiating Coverage roda em cinco etapas. Você pede uma por vez e cada uma entrega o seu arquivo. A primeira etapa é o ponto de partida: entender a empresa como um todo. Só depois dessa pesquisa vêm os números, e cada etapa seguinte se apoia no que foi levantado antes.

O relatório final, de 30 a 50 páginas, reúne pesquisa, planilha, avaliação e gráficos no formato que um analista usa para começar a cobrir uma empresa.

Fonte: <https://raw.githubusercontent.com/anthropics/financial-services/main/plugins/vertical-plugins/equity-research/skills/initiating-coverage/SKILL.md>

## Etapa 1: pesquisa do negócio inteiro

O Claude começa estudando a empresa por inteiro. O ponto de partida é entender o negócio como um todo, antes de qualquer número. Só depois dessa pesquisa vêm os números, e cada etapa seguinte se apoia no que foi levantado aqui.

Exemplo: se a ação escolhida for a Apple, o Claude pesquisa o negócio inteiro antes de montar qualquer planilha.

Fonte: <https://raw.githubusercontent.com/anthropics/financial-services/main/plugins/vertical-plugins/equity-research/skills/initiating-coverage/SKILL.md>

## Etapa 2: modelo financeiro no Excel

O Claude transforma os balanços oficiais em uma planilha de Excel com seis abas. Os números do relatório saem dali, e você pode abrir o arquivo e conferir.

Exemplo: ao abrir a planilha, você confere cada aba contra o balanço publicado pela empresa, linha por linha, antes de avançar para a avaliação.

Fonte: <https://github.com/anthropics/financial-services>

## Etapa 3: avaliação por fluxo de caixa descontado

Aqui sai o valor da empresa. O cálculo usa fluxo de caixa descontado, que projeta o dinheiro futuro, e confronta o resultado com o das concorrentes.

Exemplo: o valor calculado é comparado com o das concorrentes, para que você veja onde a empresa se posiciona, não apenas um número isolado.

Fonte: <https://github.com/anthropics/financial-services>

## Etapa 4: de 25 a 35 gráficos

Os números ganham forma visual. São de 25 a 35 gráficos gerados para a ação analisada, que depois entram no texto do relatório.

Exemplo: os gráficos gerados ilustram a análise da Apple, se essa for a ação escolhida, e entram no texto do relatório final.

Fonte: <https://github.com/anthropics/financial-services>

## Etapa 5: relatório final de 30 a 50 páginas

No fim, tudo é juntado em um relatório de 30 a 50 páginas, no formato que um analista usa para começar a cobrir uma empresa. Pesquisa, planilha, avaliação e gráficos reunidos em um único documento.

Exemplo: o documento final serve como material de estudo para você entender a empresa, seus números e sua posição frente aos concorrentes.

Fonte: <https://github.com/anthropics/financial-services>

## O que muda para você

Imagine que você quer entender a Apple antes de decidir se estuda a empresa com mais profundidade. Em vez de depender de um relatório de banco, você instala o pacote, pede as cinco etapas e recebe pesquisa, planilha de seis abas, avaliação por fluxo de caixa descontado, de 25 a 35 gráficos e um relatório de 30 a 50 páginas. O ganho é o método e a transparência: você abre a planilha e confere cada número.

O limite é que o resultado é material de estudo. Não é recomendação de investimento, e os números precisam ser conferidos antes de qualquer decisão.

Fonte: <https://github.com/anthropics/financial-services>

## O que fazer hoje

Sequência prática para começar a usar o fluxo Initiating Coverage hoje.

1. Escolha uma empresa que você conhece e que publique balanços oficiais, por exemplo a Apple.
2. Instale o pacote com os três comandos no Claude Code.
3. Peça a etapa 1 e leia a pesquisa do negócio inteiro antes de avançar.
4. Abra a planilha de seis abas e confira os números contra os balanços oficiais.
5. Use o relatório final como material de estudo, não como recomendação de compra ou venda.

Fonte: <https://github.com/anthropics/financial-services>

## O que conferir

Armadilhas e limites que valem antes de confiar no resultado.

- É ferramenta de estudo, não recomendação de investimento. Não execute transação com base no relatório.
- Confira sempre os números: abra a planilha e compare com os balanços oficiais da empresa.
- O repositório traz aviso legal: nada constitui aconselhamento de investimento, jurídico, tributário ou contábil; os outputs são rascunhos de trabalho de analista para revisão por profissional qualificado.
- Os conectores MCP podem exigir assinatura ou chave de API do provedor.
- No Claude Managed Agents, a delegação a subagentes é capacidade em Research Preview.
- Você é responsável por verificar os outputs e pela conformidade com as leis e regulamentos aplicáveis à sua firma.

Fonte: <https://github.com/anthropics/financial-services>

## financial-analysis

Plugin core do pacote. Carrega as habilidades compartilhadas de modelagem e todos os conectores de dados. Inclui análise de comparáveis, modelo de fluxo de caixa descontado, modelo de aquisição alavancada (LBO), modelo de três demonstrações, controle de qualidade de apresentações e auditoria de planilhas Excel.

Serve como base para os demais plugins verticais. Comece por aqui antes de instalar qualquer outro.

- Tecnologia: habilidades de modelagem, comandos slash /comps, /dcf, /lbo, /3-statement-model, /debug-model, auditoria de Excel e 11 conectores MCP.
- Como começar: claude plugin install financial-analysis@claude-for-financial-services

Fonte: <https://github.com/anthropics/financial-services>

## investment-banking

Plugin vertical para fluxos de investment banking. Cobre memorandos de informação, teasers, cartas de processo, listas de compradores, modelos de fusão e acompanhamento de deals.

Escolha quando o trabalho envolve preparação de material de transação e gestão de processos de M&A.

- Tecnologia: habilidades e comandos para CIMs, teasers, process letters, buyer lists, merger models e deal tracking.
- Como começar: claude plugin install investment-banking@claude-for-financial-services

Fonte: <https://github.com/anthropics/financial-services>

## equity-research

Plugin vertical para pesquisa de ações. Cobre notas de resultados, iniciações de cobertura, atualizações de modelo e acompanhamento de tese e catalisadores. É aqui que está a habilidade Initiating Coverage, que monta o relatório de análise de ações em cinco etapas.

Escolha quando o trabalho é acompanhar empresas listadas e produzir pesquisa acionária.

- Tecnologia: habilidades de equity research, comandos de earnings e iniciações, incluindo a habilidade Initiating Coverage.
- Como começar: claude plugin install equity-research@claude-for-financial-services

Fonte: <https://github.com/anthropics/financial-services/tree/main/plugins/vertical-plugins/equity-research>

## private-equity

Plugin vertical para private equity. Cobre sourcing, triagem, checklists de diligência, memorandos de comitê de investimento e monitoramento de portfólio.

Escolha quando o trabalho envolve avaliação de ativos não listados e gestão de portfólio.

- Tecnologia: habilidades e comandos para sourcing, screening, diligence checklists, IC memos e portfolio monitoring.
- Como começar: instale primeiro o financial-analysis e consulte no repositório oficial como adicionar este plugin.

Fonte: <https://github.com/anthropics/financial-services>

## fund-admin

Plugin vertical para administração de fundos. Cobre reconciliação de razão contábil, rastreamento de quebras, accruals, roll-forwards, comentários de variação e conferência de valor patrimonial líquido.

Escolha quando o trabalho envolve operações de fundo e fechamento contábil.

- Tecnologia: habilidades e comandos para GL recon, break tracing, accruals, roll-forwards, variance commentary e NAV tie-out.
- Como começar: instale primeiro o financial-analysis e consulte no repositório oficial como adicionar este plugin.

Fonte: <https://github.com/anthropics/financial-services>

## operations

Plugin vertical para operações. Cobre análise de documentos de conheça seu cliente e avaliação em grade de regras.

Escolha quando o trabalho envolve onboarding e conformidade operacional.

- Tecnologia: habilidades para KYC document parsing e rules-grid evaluation.
- Como começar: instale primeiro o financial-analysis e consulte no repositório oficial como adicionar este plugin.

Fonte: <https://github.com/anthropics/financial-services>

## claude-for-financial-advisors

Plugin para fluxos de consultoria financeira. Cobre preparação e acompanhamento de reuniões, pré-checagem de conformidade, captação de prospectos, revisão de rebalanceamento e briefings de alternativos e sucessão, sobre dados ao vivo do CRM, portfólio, planejamento e plataformas de sucessão do consultor.

Escolha quando o trabalho é consultoria a clientes, não pesquisa de ações nem M&A.

- Tecnologia: habilidades de advisor workflows sobre dados ao vivo de CRM, portfólio, planning e estate platforms.
- Como começar: instale primeiro o financial-analysis e consulte no repositório oficial como adicionar este plugin.

Fonte: <https://github.com/anthropics/financial-services>

## lseg

Plugin parceiro construído pela LSEG. Cobre valor relativo de títulos, curvas de swap, carry em câmbio, volatilidade de opções e monitoramento macro de taxas sobre dados da LSEG.

Escolha quando o trabalho envolve taxas, câmbio e derivativos sobre dados LSEG.

- Tecnologia: habilidades e comandos para bond RV, swap curves, FX carry, options vol e macro-rates monitoring.
- Como começar: instale primeiro o financial-analysis e consulte no repositório oficial como adicionar este plugin.

Fonte: <https://github.com/anthropics/financial-services>

## sp-global

Plugin parceiro construído pela S&P Global. Cobre tear sheets, prévias de resultados e resumos de financiamento sobre dados do S&P Capital IQ.

Escolha quando o trabalho envolve pesquisa rápida de empresas sobre dados S&P.

- Tecnologia: habilidades e comandos para tear sheets, earnings previews e funding digests.
- Como começar: instale primeiro o financial-analysis e consulte no repositório oficial como adicionar este plugin.

Fonte: <https://github.com/anthropics/financial-services>

## Agentes end-to-end do pacote

Além dos plugins verticais, o pacote traz agentes nomeados que possuem um fluxo completo de ponta a ponta, com prompt de sistema mais as habilidades que usam. Cada agente é um plugin autocontido.

Os agentes aparecem no Cowork dispatch e também podem ser implantados de forma headless via Claude Managed Agents.

- Pitch Agent: comps, precedentes e LBO até pitch deck com marca, de ponta a ponta.
- Meeting Prep Agent: pacote de preparação antes de cada reunião com cliente.
- Market Researcher: setor ou tema até visão geral de indústria, paisagem competitiva, comps de pares e lista curta de ideias.
- Earnings Reviewer: call de resultados e filings até atualização de modelo e rascunho de nota.
- Model Builder: DCF, LBO, três demonstrações e comps ao vivo no Excel.
- Valuation Reviewer: ingestão de pacotes de GP, execução de template de avaliação e preparação de relatórios para LPs.
- GL Reconciler: encontra quebras, rastreia causa raiz e encaminha para aprovação.
- Month-End Closer: accruals, roll-forwards e comentários de variação.
- Statement Auditor: audita extratos LP antes da distribuição.
- KYC Screener: análise de documentos de onboarding, execução do motor de regras e sinalização de lacunas.

Fonte: <https://github.com/anthropics/financial-services>

## Conectores de dados (MCP)

Todos os conectores ficam centralizados no plugin core financial-analysis e são compartilhados pelos demais. Eles ligam o Claude aos seus dados via servidores MCP.

O acesso MCP pode exigir assinatura ou chave de API do provedor.

- Daloopa: https://mcp.daloopa.com/server/mcp
- Morningstar: https://mcp.morningstar.com/mcp
- S&P Global: https://kfinance.kensho.com/integrations/mcp
- FactSet: https://mcp.factset.com/mcp
- Moody's: https://api.moodys.com/genai-ready-data/m1/mcp
- MT Newswires: https://vast-mcp.blueskyapi.com/mtnewswires
- Aiera: https://mcp-pub.aiera.com
- LSEG: https://api.analytics.lseg.com/lfa/mcp
- PitchBook: https://premium.mcp.pitchbook.com/mcp
- Chronograph: https://ai.chronograph.pe/mcp
- Egnyte: https://mcp-server.egnyte.com/mcp
- Box: https://mcp.box.com

Fonte: <https://github.com/anthropics/financial-services>

## Formas de usar: Cowork, Claude Code e Managed Agents

Tudo no repositório está disponível de duas formas a partir da mesma fonte: como plugin no Claude Cowork ou implantado via Claude Managed Agents API por trás do seu próprio motor de fluxo de trabalho. Mesmo prompt de sistema, mesmas habilidades; você escolhe onde roda.

No Cowork, abra Configurações, Plugins, Adicionar plugin e cole a URL do repositório ou faça upload de um zip de qualquer diretório sob plugins/. No Claude Code, use os comandos de marketplace e install mostrados na seção de instalação.

- Cowork: Settings, Plugins, Add plugin, depois cole https://github.com/anthropics/financial-services ou faça upload de zip.
- Claude Code: claude plugin marketplace add e claude plugin install, conforme a seção de instalação.
- Managed Agents: export ANTHROPIC_API_KEY e rode scripts/deploy-managed-agent.sh com o slug do agente.

Fonte: <https://github.com/anthropics/financial-services>

## Microsoft 365: ferramenta de instalação para administradores

Se a firma roda o Claude dentro do Excel, PowerPoint, Word e Outlook via add-in do Microsoft 365, o repositório traz uma ferramenta de administração para provisionar o add-in contra a própria nuvem da firma, Vertex AI, Bedrock ou gateway interno de LLM, em vez da API da Anthropic.

É um plugin do Claude Code, não um plugin do Cowork, que guia o administrador de TI pela geração do manifesto customizado, consentimento de administrador no Azure e configuração de roteamento por usuário via Microsoft Graph.

- Instalação: claude plugin install claude-for-msft-365-install@claude-for-financial-services
- Uso: /claude-for-msft-365-install:setup
- Observação: é a porta de entrada que implanta o add-in no tenant; depois são os agentes e habilidades que rodam dentro dele.

Fonte: <https://github.com/anthropics/financial-services>

## Glossário

Termos técnicos que podem não ser familiares, com definição curta em linguagem simples.

- Anthropic: empresa americana criadora do assistente de inteligência artificial Claude.
- Claude: assistente de inteligência artificial da Anthropic.
- Claude Code: interface de linha de comando para usar o Claude e instalar plugins.
- Claude Cowork: ambiente da Anthropic onde plugins são adicionados via configurações.
- Plugin: pacote que adiciona habilidades, comandos e conectores ao Claude.
- Marketplace: fonte de plugins registrada no Claude Code.
- MCP (Model Context Protocol): protocolo que liga o Claude a servidores de dados externos.
- Conector: servidor MCP que conecta o Claude a uma plataforma de dados.
- Vertical plugin: bundle de habilidades e comandos por vertical financeira.
- Agente: plugin autocontido que possui um fluxo de trabalho de ponta a ponta.
- Slash command: ação disparada com barra, como /comps ou /dcf.
- Managed Agents: implantação headless de agentes via API da Anthropic.
- Initiating Coverage: relatório que o analista escreve ao começar a acompanhar uma empresa.
- Fluxo de caixa descontado (DCF): método que projeta o dinheiro futuro para calcular o valor da empresa.
- Comps: análise de empresas comparáveis com múltiplos de mercado.
- LBO: modelo de aquisição alavancada.
- Modelo de três demonstrações: balanço, demonstração de resultados e fluxo de caixa integrados.
- KYC: conheça seu cliente, processo de verificação de identidade e conformidade.
- NAV: valor patrimonial líquido de um fundo.
- GL recon: reconciliação do razão contábil.
- IC memo: memorando de comitê de investimento.
- CIM: memorando de informação para venda de empresa.
- Research Preview: capacidade em fase de pré-visualização, sujeita a mudanças.

## Para onde ir depois

Próximos passos para continuar.

- Leia o README completo no repositório oficial para ver agentes, verticals e managed-agent-cookbooks.
- Instale o pacote e teste a etapa 1 com uma empresa que você conheça.
- Explore os comandos slash /comps, /dcf, /earnings e /ic-memo após instalar os plugins correspondentes.
- Se a firma usa Microsoft 365, avalie o claude-for-msft-365-install para provisionar o add-in.
- Para deploy sem interface, consulte os cookbooks em managed-agent-cookbooks no repositório.
- Sempre confira os números na planilha contra os balanços oficiais antes de usar o relatório.

Fonte: <https://github.com/anthropics/financial-services>

## Links citados

- https://raw.githubusercontent.com/anthropics/financial-services/main/README.md

## Além do vídeo

- O repositório traz os scripts deploy-managed-agent.sh, check.py, validate.py, orchestrate.py e sync-agent-skills.py.
- No Cowork, também é possível compactar em zip um diretório sob plugins/ e fazer o upload.
- Você pode apontar o arquivo .mcp.json para seus próprios provedores de dados e adicionar contexto da sua firma aos arquivos de habilidade.
- O comando /ppt-template ensina ao Claude os layouts de PowerPoint da sua marca.
- Os agentes são plugins autocontidos; os wrappers de agentes gerenciados reúnem agent.yaml, subagentes e exemplos para implantação sem interface.
