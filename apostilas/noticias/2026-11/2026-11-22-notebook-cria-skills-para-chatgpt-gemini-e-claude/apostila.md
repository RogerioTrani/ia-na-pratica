# Notebook cria skills para ChatGPT, Gemini e Claude

_2026-11-22 · noticia_

Um notebook no Gemini Notebook (antigo NotebookLM), alimentado com as páginas oficiais de skills do ChatGPT, do Gemini e do Claude, gera o arquivo SKILL.md pronto. A apostila mostra como montar o notebook, criar a skill de thumbnail no ChatGPT, acionar com a barra e levar a mesma skill para o Gemini. O mesmo caminho serve para outras skills, como análise de contratos em PDF.

## Monte o notebook que fabrica skills

No Gemini Notebook, crie um notebook novo. No vídeo ele se chama fábrica de skills. Em Adicionar fontes > Sites, inclua as páginas oficiais sobre skills das três plataformas.

- Skills no ChatGPT (OpenAI): https://help.openai.com/en/articles/20001066-skills-in-chatgpt
- Habilidades no Gemini (Google): https://support.google.com/gemini/answer/17094296
- Agent Skills no Claude (Anthropic): https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview

Fonte: <https://notebook.google.com/>

## Configure o prompt do notebook

Com as três fontes carregadas, abra os três pontos do notebook, vá em Configurar bate-papo e clique em Personalizar. Cole ali o prompt que transforma o notebook em gerador de skills e salve.

O prompt manda o notebook atuar como engenheiro sênior de prompt e arquiteto de skill. A cada pedido, ele pergunta a plataforma (ChatGPT, Gemini, Claude ou outra) e a tarefa repetitiva a automatizar. Ele só usa as fontes oficiais carregadas e segue o padrão delas, sem inventar nada.

- O notebook entrega uma análise técnica.
- Entrega a skill completa, no formato SKILL.md, com metadados YAML: name em minúsculas com hifens e description, mais instruções passo a passo.
- Explica a instalação e a configuração.
- Traz um teste prático.
- Aponta quais partes das fontes foram usadas.

Fonte: <https://notebook.google.com/>

## Peça a skill de thumbnail

No chat do notebook, descreva o que quer automatizar e a plataforma de destino. No vídeo, o pedido foi uma skill que ajude a criar thumbnail no ChatGPT. O notebook devolve o nome, a descrição e a instrução da habilidade, prontos para copiar.

Fonte: <https://notebook.google.com/>

## Crie a skill no ChatGPT

Com o texto do notebook em mãos, cadastre a habilidade no ChatGPT.

- Abra Plugins e escolha a aba Habilidades.
- Clique em adicionar habilidades e escolha criar com o editor.
- Preencha nome (no vídeo, Criador de thumbnail), descrição e instrução com o que o notebook entregou.
- Clique em criar. A skill fica salva e aparece na lista.

Fonte: <https://help.openai.com/en/articles/20001066-skills-in-chatgpt>

## Acione a skill com a barra

Abra uma conversa nova e digite / para listar suas skills. Escolha Criador de thumbnail, anexe uma foto sua e cole a legenda do vídeo. Só isso já basta para a skill começar.

A skill leu a foto e a legenda e montou a miniatura. Pedindo outra estrutura, ou mudança de cor de fundo, ela gera uma segunda versão. No teste, a nova versão manteve a qualidade da foto e a ideia da legenda.

Fonte: <https://help.openai.com/en/articles/20001066-skills-in-chatgpt>

## Leve a skill do ChatGPT para o Gemini

A mesma habilidade passa a funcionar no Gemini sem ser refeita.

- No ChatGPT, abra o menu de três pontos da skill e baixe o arquivo.
- No Gemini, abra Habilidades e clique em Criar.
- Clique em Upload e envie o arquivo zip.

Fonte: <https://support.google.com/gemini/answer/17094296>

## Outras skills pelo mesmo notebook

O notebook serve de ponto de partida para qualquer tarefa repetitiva. No teste do vídeo saiu uma skill para analisar contratos em PDF. A ideia vale para edição de vídeo, orçamento e ofícios: basta pedir ao notebook a skill, informando a plataforma e a tarefa.

Fonte: <https://notebook.google.com/>

## Além do vídeo

- O pedido de skill de análise de contratos pedia que ela identificasse cláusulas importantes, prazos, obrigações, riscos e possíveis inconsistências, com um relatório estruturado e referência ao documento.
- No teste com um contrato de venda de carro, o relatório apontou cláusulas abusivas, prazos e obrigações, matriz de avaliação de risco, rescisões e penalidades, e inconsistências e dúvidas.
- A resposta do notebook segue uma ordem fixa: análise técnica (com a viabilidade de recursos da plataforma), skill completa, instalação e configuração, uso no dia a dia e ideias de teste.
