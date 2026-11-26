# Alibaba abre o código do Open Code Review

_2026-11-22 · noticia_

A Alibaba abriu o código do Open Code Review, ferramenta de revisão de código com IA que nasceu como assistente interno do grupo e agora está disponível para a comunidade. A apostila explica como ela funciona, como se instala, como rodar a primeira revisão e quais números do benchmark considerar antes de adotá-la. Ao final, você terá os comandos prontos para copiar e saberá avaliar se ela substitui sua ferramenta atual.

## O fato

A Alibaba abriu o código do Open Code Review (OCR), uma ferramenta de linha de comando que revisa código com inteligência artificial. O repositório oficial é github.com/alibaba/open-code-review, publicado sob licença Apache-2.0.

Antes de ser aberto, o OCR foi o assistente oficial de revisão de código com IA do Grupo Alibaba. Ao longo de dois anos, atendeu dezenas de milhares de desenvolvedores e identificou milhões de defeitos de código. A abertura ao público veio depois dessa validação em escala grande.

A ferramenta lê diffs do Git, envia os arquivos alterados a um modelo de linguagem configurável por meio de um agente com capacidade de uso de ferramentas, e gera comentários estruturados com precisão de linha. O agente pode ler o conteúdo completo dos arquivos, buscar no código-base, inspecionar outros arquivos alterados para contexto e produzir revisões profundas, não apenas feedback superficial de diff. Além da revisão de diff, o comando `ocr scan` revisa arquivos inteiros, útil para auditar bases de código desconhecidas ou diretórios sem diff significativo.

Fonte: <https://github.com/alibaba/open-code-review>

## Por que isso importa

Segundo o projeto, agentes de uso geral, como o Claude Code quando usado para revisão de código via Skills, sofrem de três problemas recorrentes. Cobertura incompleta: em mudanças grandes, o agente tende a cortar caminho, revisando apenas alguns arquivos e perdendo outros. Deriva de posição: os problemas reportados frequentemente não batem com a localização real do código, com números de linha ou referências de arquivo que se desviam do alvo. Qualidade instável: Skills baseadas em linguagem natural são difíceis de depurar, e a qualidade da revisão flutua significativamente com pequenas variações no prompt.

A causa raiz, segundo o projeto, é que uma arquitetura puramente orientada a linguagem carece de restrições rígidas sobre o processo de revisão. O OCR propõe combinar engenharia determinística com um agente, cada parte fazendo o que faz melhor.

A promessa é menos ruído: precisão e F1 maiores que os de agentes genéricos com o mesmo modelo, usando cerca de 1/9 dos tokens. O custo dessa escolha é um recall menor, uma troca deliberada que favorece precisão sobre alarmes falsos.

Fonte: <https://github.com/alibaba/open-code-review>

## Engenharia determinística: as regras fixas

Para as etapas que não podem falhar, a lógica de engenharia, e não o modelo de linguagem, garante a correção. A seleção precisa de arquivos determina exatamente quais arquivos precisam de revisão e quais devem ser filtrados, garantindo que nenhuma mudança importante seja perdida.

O agrupamento inteligente de arquivos reúne arquivos relacionados em uma única unidade de revisão. O exemplo do projeto: `message_en.properties` e `message_zh.properties` são agrupados. Cada grupo executa como um sub-agente com contexto isolado, uma estratégia de dividir para conquistar que se mantém estável em mudanças muito grandes e suporta naturalmente revisão concorrente.

A correspondência fina de regras combina regras de revisão com as características de cada arquivo, mantendo a atenção do modelo focada e eliminando ruído de informação na fonte. Comparada à orientação por linguagem natural, a correspondência baseada em motor de templates é mais estável e previsível.

Módulos externos de posicionamento e reflexão atuam de forma independente para melhorar sistematicamente a precisão de localização e a precisão de conteúdo do feedback da IA.

Fonte: <https://github.com/alibaba/open-code-review>

## O agente: decisão dinâmica

As forças do agente se concentram onde importam mais: decisões dinâmicas e recuperação dinâmica de contexto. Os prompts são ajustados ao cenário, com templates profundamente otimizados para revisão de código, melhorando a efetividade enquanto reduzem o consumo de tokens.

O conjunto de ferramentas também é ajustado ao cenário. Ele foi destilado de análise profunda de traces de chamadas de ferramentas em dados de produção em larga escala, incluindo distribuições de frequência de chamada, taxas de repetição por ferramenta e o impacto de novas ferramentas na cadeia de chamadas. O resultado é um conjunto feito para esse propósito, mais estável e previsível para revisão de código que um toolkit de agente genérico.

Fonte: <https://github.com/alibaba/open-code-review>

## O conjunto de regras embutido

O OCR traz um conjunto de regras embutido que cobre erros como NPE, segurança de threads, XSS e injeção de SQL, em várias linguagens. O guia de regras está em open-codereview.ai/docs.

Você pode personalizar as regras por caminho, conforme a documentação do projeto. Isso mantém o modelo focado no que importa para cada parte do código.

Fonte: <https://github.com/alibaba/open-code-review>

## Compatibilidade com modelos de linguagem

O OCR funciona com serviços compatíveis com OpenAI e com Anthropic. A configuração é feita com `ocr config provider`, para selecionar um provider embutido ou adicionar um customizado, e `ocr config model`, para escolher o modelo do provider ativo. A interface interativa guia a seleção do provider, a entrada da chave de API e a configuração do modelo, e então testa a conectividade automaticamente.

Em modo padrão, o OCR chama o modelo usando sua própria configuração de provider, não a assinatura Team ou Pro do Claude Code. Em Delegation Mode, o agente host chama o modelo com sua própria autenticação, e nenhuma configuração separada de LLM ou credenciais é necessária no OCR.

Fonte: <https://github.com/alibaba/open-code-review>

## Modos de revisão disponíveis

O OCR oferece vários modos de revisão para se adaptar ao fluxo de trabalho. O modo workspace revisa todas as mudanças staged, unstaged e untracked do repositório atual. O modo de faixa de branches revisa as mudanças de uma branch desde que ela divergiu da base, usando merge-base. O modo de commit único revisa um commit específico. O scan de arquivo completo revisa arquivos inteiros em vez de um diff, sem precisar de histórico Git, útil para auditar bases desconhecidas.

Revisões interrompidas podem ser retomadas. Use `ocr session list` para listar sessões e `--resume` para continuar de onde parou. Os resultados podem ser salvos em arquivo com `--format json --output result.json`, recomendado para agentes de código IA que consomem a saída.

Em Delegation Mode, o OCR cuida da seleção de arquivos e da resolução de regras, e o agente de código do usuário executa a revisão com seu próprio modelo. Os comandos `ocr delegate preview` e `ocr delegate rule` iniciam esse fluxo.

Fonte: <https://github.com/alibaba/open-code-review>

## Integrações, CI/CD e observabilidade

O projeto oferece integrações com vários agentes de código: Claude Code, Codex, Cursor, Kimi Code, OpenCode, QCA Forward e agentes compatíveis com skills. Também expõe um servidor MCP para estender o agente de revisão com ferramentas externas.

Para pipelines, há integração com GitHub Actions, GitLab CI, GitFlic CI e Gerrit. O Session Viewer permite navegar e reproduzir sessões de revisão no navegador, marcar comentários como corrigidos ou ignorados e ocultá-los enquanto você trabalha nas descobertas. A telemetria via OpenTelemetry oferece observabilidade sobre as execuções.

Fonte: <https://github.com/alibaba/open-code-review>

## Os números

Cada número abaixo vem do repositório ou do benchmark publicado pelo projeto. Mantenha o recorte: são métricas do OCR comparado a agentes genéricos, não uma garantia para qualquer repositório.

- 51,1 mil estrelas no GitHub, medida de interesse da comunidade pelo repositório.
- 3,8 mil forks, cópias do repositório feitas por outros usuários.
- 860 commits no histórico do repositório.
- 145 watchers acompanhando o repositório.
- 2 anos de uso interno no Grupo Alibaba antes da abertura ao público.
- Dezenas de milhares de desenvolvedores atendidos internamente.
- Milhões de defeitos de código identificados internamente.
- Cerca de 1/9 dos tokens consumidos em comparação com agentes genéricos, com o mesmo modelo.
- 50 repositórios open source populares no benchmark.
- 200 pull requests reais no benchmark.
- 10 linguagens de programação cobertas no benchmark.
- 80 ou mais engenheiros seniores na validação cruzada.
- 1.505 problemas anotados como verdade de base no benchmark.
- Git 2.41 ou superior como pré-requisito para funcionar.

Fonte: <https://github.com/alibaba/open-code-review>

## O que muda para você

Em mudanças grandes, um agente genérico pode revisar só parte dos arquivos e errar a linha de um problema. A proposta do OCR é selecionar os arquivos com regras determinísticas, para que nenhuma mudança importante fique de fora, e usar um módulo de posicionamento para melhorar a precisão de linha. No benchmark do projeto, o consumo de tokens ficou em torno de um nono do de um agente genérico com o mesmo modelo.

Exemplo: você configura o OCR com um provider compatível com OpenAI, roda `ocr review` no seu repositório e recebe comentários linha a linha sobre as mudanças. Depois, compara com a ferramenta que já usa e decide se o ganho de precisão compensa o recall menor.

Fonte: <https://github.com/alibaba/open-code-review>

## O que fazer hoje

Siga os passos abaixo para instalar, configurar e rodar sua primeira revisão. Cada item indica a ação e o resultado esperado.

1. Verifique se o Git instalado é 2.41 ou superior. Resultado esperado: o comando de versão mostra 2.41 ou mais.
2. Instale o OCR globalmente. Resultado esperado: o comando `ocr` fica disponível no terminal.
3. Entre no diretório do projeto que você quer revisar. Resultado esperado: o terminal está na raiz do repositório.
4. Configure o provider de modelo. Resultado esperado: provider selecionado e chave de API informada.
5. Escolha o modelo do provider ativo. Resultado esperado: modelo configurado e conectividade testada.
6. Rode a primeira revisão no workspace. Resultado esperado: comentários linha a linha sobre as mudanças staged, unstaged e untracked.
7. Para revisar uma faixa de branches, use o modo de faixa. Resultado esperado: revisão das mudanças da branch desde a divergência da base.
8. Para revisar um commit específico, use o modo de commit. Resultado esperado: revisão apenas daquele commit.
9. Para auditar arquivos inteiros sem diff, use o scan. Resultado esperado: revisão de arquivos completos, sem precisar de histórico Git.
10. Para salvar o resultado em arquivo, use o formato JSON. Resultado esperado: arquivo com as descobertas para consumo posterior.

```
npm install -g @alibaba-group/open-code-review
cd your-project
ocr config provider
ocr config model
ocr review
ocr review --from main --to feature-branch
ocr review --commit abc123
ocr scan
ocr scan --path internal/agent
ocr review --format json --output result.json
```

Fonte: <https://github.com/alibaba/open-code-review>

## O que conferir antes de adotar

Antes de substituir sua ferramenta atual, considere os pontos abaixo.

- O recall é menor que o de agentes genéricos: a ferramenta pode deixar passar defeitos que um agente genérico encontraria. Se sua prioridade é capturar o máximo de problemas, compare os dois lado a lado.
- A precisão e o F1 maiores vêm do benchmark do próprio projeto, o AACR-Bench, com 200 pull requests de 50 repositórios e 10 linguagens, validado por 80 ou mais engenheiros seniores. São números do projeto; teste no seu repositório antes de decidir.
- A configuração de LLM é obrigatória, exceto em Delegation Mode. Sem provider configurado, `ocr review` não roda.
- Git 2.41 ou superior é pré-requisito; versões anteriores não são suportadas.
- Em Delegation Mode, o OCR não usa sua chave de API; o agente host executa a revisão com seu próprio modelo e autenticação.
- A personalização de regras por caminho é feita conforme a documentação do projeto; não invente sintaxe de regra.
- A licença Apache-2.0 permite uso e adaptação livres, mas verifique os termos e a configuração de telemetria se for usar em ambiente corporativo.
- O benchmark compara ao Claude Code como agente genérico; não generalize os números para todos os agentes ou modelos.

Fonte: <https://github.com/alibaba/open-code-review>

## Glossário

- Open Code Review (OCR): ferramenta de linha de comando que revisa código com IA, de arquitetura híbrida.
- Agente de LLM: modelo de linguagem com capacidade de usar ferramentas para ler arquivos, buscar no código e gerar comentários.
- Pipeline determinístico: sequência de etapas com regras fixas de engenharia, sem decisão do modelo.
- Diff: diferença entre versões de código, base da revisão padrão do OCR.
- Recall: proporção de defeitos reais encontrados pela ferramenta.
- Precision (precisão): proporção de problemas reportados que são defeitos reais.
- F1: média harmônica de precisão e recall, usada como número único de qualidade.
- NPE: NullPointerException, erro de referência nula em linguagens como Java.
- XSS: cross-site scripting, vulnerabilidade de injeção de script em aplicações web.
- SQL injection: injeção de comandos SQL maliciosos em consultas.
- Thread-safety: segurança de acesso concorrente a recursos compartilhados.
- Apache-2.0: licença de software livre que permite uso, modificação e distribuição.
- Delegation Mode: modo em que o agente de código do usuário executa a revisão, sem configuração de LLM no OCR.
- AACR-Bench: benchmark de revisão de código do projeto, com pull requests reais anotados.
- MCP Server: mecanismo para estender o agente de revisão com ferramentas externas.
- Session Viewer: interface web para navegar e reproduzir sessões de revisão.

Fonte: <https://github.com/alibaba/open-code-review>

## Para onde ir depois

Sugestões de próximos passos para aprofundar.

- Leia a documentação completa em open-codereview.ai/docs.
- Teste o OCR no seu repositório e compare os resultados com a ferramenta de revisão que você já usa.
- Explore o dataset AACR-Bench em huggingface.co/datasets/Alibaba-Aone/aacr-bench.
- Consulte o repositório oficial em github.com/alibaba/open-code-review para código-fonte e issues.
- Acompanhe o canal para mais notícias de IA.

Fonte: <https://github.com/alibaba/open-code-review>

## Comandos e blocos para copiar

```
ocr delegate preview
ocr delegate rule src/main.go src/handler.go
```

## Links citados

- https://huggingface.co/datasets/Alibaba-Aone/aacr-bench
- https://open-codereview.ai/docs
- https://www.npmjs.com/package/@alibaba-group/open-code-review

## Além do vídeo

- A documentação oficial inclui seções como Quickstart, Installation, CLI Reference, Review Rules, Configuration, MCP Server e FAQ.
- Além do npm, o projeto oferece instalação por script e binário do GitHub Release, além de compilação a partir do código-fonte.
- O benchmark mede também tempo médio por revisão (Avg Time) e tokens médios por revisão (Avg Token), além de F1, precisão e recall.
- A licença Apache-2.0 do projeto tem copyright 2026 Alibaba.
- Revisões interrompidas podem ser retomadas com `ocr session list` e o parâmetro `--resume`.
