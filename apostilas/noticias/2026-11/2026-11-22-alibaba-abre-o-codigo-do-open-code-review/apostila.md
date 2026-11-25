# Alibaba abre o código do Open Code Review

_2026-11-22 · noticia_

A Alibaba abriu o código do Open Code Review, ferramenta de revisão de código com IA que era o assistente oficial interno do grupo. Em dois anos, atendeu dezenas de milhares de desenvolvedores e apontou milhões de defeitos. Combina etapas fixas de engenharia com um agente de LLM. Instala por npm e funciona com modelos compatíveis com OpenAI e Anthropic.

## O fato

O Open Code Review foi o assistente oficial de revisão de código com IA do Alibaba Group. Em dois anos, atendeu dezenas de milhares de desenvolvedores e identificou milhões de defeitos de código. Depois dessa validação em escala, virou projeto aberto para a comunidade.

A ferramenta lê os diffs do Git, envia os arquivos alterados a um LLM configurável por meio de um agente com acesso a ferramentas e gera comentários estruturados, com precisão de linha. O agente lê o conteúdo completo dos arquivos, busca no código e consulta outros arquivos alterados para ter contexto. Fonte: https://github.com/alibaba/open-code-review

Fonte: <https://github.com/alibaba/open-code-review>

## Como funciona e quais regras vêm embutidas

O projeto aponta três problemas de agentes genéricos em revisão de código: cobertura incompleta em mudanças grandes, comentários que não batem com a linha real e qualidade instável conforme pequenas variações no prompt. A resposta é dividir o trabalho: o que não pode falhar fica com engenharia determinística, e a decisão dinâmica fica com o agente.

O conjunto embutido cobre erros como NPE, segurança de threads, XSS e injeção de SQL, em várias linguagens. Dá para personalizar as regras com filtro e direcionamento por caminho. O guia de regras está em https://open-codereview.ai/docs

- Seleção de arquivos: define quais arquivos entram na revisão e quais são filtrados.
- Agrupamento: arquivos relacionados viram uma unidade de revisão (por exemplo, message_en.properties e message_zh.properties juntos). Cada grupo roda em um subagente com contexto isolado, o que mantém a estabilidade em mudanças muito grandes e permite revisão concorrente.
- Regras por arquivo: as regras são associadas às características de cada arquivo, o que mantém o modelo focado.
- Posicionamento e reflexão: módulos externos melhoram a precisão do local e do conteúdo dos comentários.
- Agente: usa prompts e um conjunto de ferramentas ajustados para revisão de código, com busca dinâmica de contexto.

Fonte: <https://open-codereview.ai/docs>

## Benchmark: precisão e tokens

Com o mesmo modelo, o projeto diz que o Open Code Review alcança precisão e F1 bem maiores que os do Claude Code, gastando cerca de 1/9 dos tokens e terminando as revisões mais rápido. O recall é menor que o de agentes genéricos, uma troca deliberada: a ferramenta prefere menos alarmes falsos.

O teste usou o AACR-Bench: 50 repositórios open source populares, 200 pull requests reais e 10 linguagens de programação, validados de forma cruzada por mais de 80 engenheiros seniores, com 1.505 problemas anotados. Dataset: https://huggingface.co/datasets/Alibaba-Aone/aacr-bench

- F1: média harmônica entre precisão e recall.
- Precisão: proporção dos problemas reportados que são defeitos reais. Quanto maior, menos alarmes falsos para triar.
- Recall: proporção dos defeitos reais que foram encontrados.
- Tempo médio e tokens médios por revisão: pesam na latência do CI e no custo de API.

Fonte: <https://github.com/alibaba/open-code-review>

## Instalação e configuração

O requisito é Git 2.41 ou superior, porque a ferramenta usa o Git para gerar diffs, buscar no código e operar no repositório. Pacote npm: https://www.npmjs.com/package/@alibaba-group/open-code-review

É preciso configurar um LLM antes de revisar, a menos que você use o modo de delegação. A ferramenta funciona com serviços compatíveis com OpenAI e com Anthropic. A interface interativa guia a escolha do provedor, a chave de API e o modelo, e testa a conexão no fim. A configuração do OCR é própria: não usa o login da sua assinatura do Claude Code.

1. instale com npm install -g @alibaba-group/open-code-review. Resultado: o comando ocr fica disponível globalmente.
2. rode o primeiro comando para escolher um provedor embutido ou adicionar um personalizado. Resultado: o provedor fica configurado.
3. rode o segundo para escolher o modelo do provedor ativo. Resultado: o modelo fica pronto para a revisão.

```
npm install -g @alibaba-group/open-code-review
```

Fonte: <https://www.npmjs.com/package/@alibaba-group/open-code-review>

## Rodar a revisão

Entre na pasta do projeto e escolha o modo que serve ao seu caso. Documentação e repositório: https://github.com/alibaba/open-code-review

- Alterações no workspace (staged, unstaged e não rastreadas): ocr review
- Intervalo de branches: ocr review --from main --to feature-branch
- Um commit: ocr review --commit abc123
- Arquivos inteiros, sem diff: ocr scan (ou ocr scan --path internal/agent para uma pasta)
- Salvar o resultado em arquivo: ocr review --format json --output result.json
- Retomar revisão interrompida: ocr session list e depois ocr review --from main --to feature-branch --resume <session-id>

Fonte: <https://github.com/alibaba/open-code-review>

## Modo de delegação

No modo de delegação, o seu agente de código faz a revisão com o próprio modelo, sem chave de API no OCR. O OCR cuida da seleção de arquivos e das regras. Exemplos de comandos:

```
ocr delegate preview
ocr delegate rule src/main.go src/handler.go
```

Fonte: <https://github.com/alibaba/open-code-review>

## O que conferir

O projeto está no GitHub sob licença Apache-2.0, com 51,1 mil estrelas e 3,8 mil forks.

Repositório: https://github.com/alibaba/open-code-review. Site e documentação: https://open-codereview.ai/docs

Além do modo de delegação, o projeto cita integrações com Claude Code, Codex, Cursor, Kimi Code e OpenCode, além de CI/CD com GitHub Actions, GitLab CI, GitFlic CI e Gerrit.

Fonte: <https://github.com/alibaba/open-code-review>
