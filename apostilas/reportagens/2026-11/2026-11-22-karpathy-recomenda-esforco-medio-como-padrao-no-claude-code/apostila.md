# Karpathy recomenda esforço médio como padrão no Claude Code

_2026-11-22 · reportagem_

Andrej Karpathy ajudou a fundar a OpenAI e liderou a direção autônoma da Tesla. Esta apostila reúne os oito conselhos dele que o vídeo cobre, com os comandos prontos para usar no Claude Code. O foco é gastar menos token, receber respostas mais diretas e saber o que você construiu.

## Esforço médio como padrão

Rodar tudo no máximo gasta token rápido e pode render uma resposta pensada demais. Comece cada tarefa no esforço médio. Suba para o alto só quando o médio falhar.

Vale também para o modelo: se um modelo mais barato resolve, não há motivo para usar o mais caro. Faça o teste uma vez para cada tarefa ou skill que você roda todo dia e guarde o resultado.

- Rode a tarefa no esforço médio.
- Se falhar, suba para o esforço alto.
- Ajuste o esforço com /effort.
- Troque por um modelo mais barato com /model.

Fonte: <https://code.claude.com/docs/en/commands>

## Objetivo claro e skill criada depois do trabalho

Instruções longas podem se contradizer e deixar o agente em dúvida. Peça o resultado final com /goal e deixe o agente buscar o caminho. Isso não elimina skills nem instruções, só evita a lista enorme.

Com a skill é a mesma lógica: não tente prever todos os caminhos. Execute a tarefa do início ao fim, passo a passo, até o resultado ficar bom. Depois peça: crie uma skill baseada no histórico desta conversa.

Fonte: <https://code.claude.com/docs/en/commands>

## Respostas diretas com ASD-STE100

O ASD-STE100 é um padrão de escrita criado para manuais de manutenção de aviões. Ele força frases curtas e claras. Peça ao modelo para responder nesse padrão quando as respostas vierem longas demais.

Ajuda mais quando você dialoga com a IA, aprovando e reprovando cada etapa de uma tarefa longa.

Fonte: <https://asd-ste100.org>

## Filtros antes da IA

Use um script simples para descartar o que não importa e deixe o modelo só com os dados que valem a análise. Raramente você precisa analisar 100% de uma base grande.

Exemplo do vídeo: numa pesquisa de vídeos virais, um filtro de mais de um milhão de visualizações reduz três mil análises a dezenas.

## Desconfie dos benchmarks

As notas de lançamento costumam vir da própria empresa, e o modelo pode ter sido treinado para ir bem nesses testes. Consulte o ECI da Epoch, que combina vários benchmarks com lógica matemática.

Fonte: <https://epoch.ai/eci>

## Testes rigorosos e ferramentas para verificar

O ciclo só termina quando os testes passam. Isso vale para código e para qualquer tarefa longa com loops. Os critérios só funcionam se o agente tiver ferramentas para verificá-los.

O Playwright MCP liga um navegador automatizado à IA e testa seu app no navegador. O comando abaixo o instala no Claude Code.

```
claude mcp add playwright npx @playwright/mcp@latest
```

Fonte: <https://github.com/microsoft/playwright-mcp>

## Não terceirize a sua compreensão

Descrever um sistema complexo em linguagem natural sem entender o que ele faz cobra o preço depois. Quando ele quebra ou para de obedecer, você não sabe por quê. Entenda o que a IA constrói.

- Comece pelo esforço médio.
- Dê um objetivo claro.
- Filtre antes da IA.
- Exija testes que o agente consiga executar.

## Além do vídeo

- Com vários agentes trabalhando na mesma skill, dá para juntar a experiência de todos e criar a skill a partir dela.
- Para tarefas que rodam todo dia e levam de meia hora a uma hora, vale testar também o esforço baixo.
- O exemplo de modelo barato no esforço mais baixo: se o Sonnet resolve, não faz sentido usar o Fable no máximo.
- Até modelos baratos servem para a parte dos dados que realmente importa depois do filtro.
