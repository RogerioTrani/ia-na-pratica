# Meituan abre pesos do LongCat-2.5 sob licença MIT

_2026-11-19 · noticia_

A Meituan publicou no Hugging Face, em 9 de novembro, os pesos do LongCat-2.5 sob licença MIT. É um modelo com visão que lê screenshots e vídeo e escreve código em várias etapas. Ele tem 48 bi de parâmetros ativos por token (1,6 tri no total), avança muito sobre o LongCat-2.0 e custa uma fração dos modelos premium na API hospedada, em tarifa por tempo limitado. Esta apostila traz os números, os passos para criar a chave da API e o comando de download.

## O que saiu e com que licença

A Meituan, empresa chinesa de entrega de comida e e-commerce, publicou o checkpoint do LongCat-2.5 em 9 de novembro, uma semana depois de apresentar o modelo. A licença é MIT: uso comercial, modificação e redistribuição liberados, respeitando as exigências de aviso da licença.

O modelo inspeciona screenshots e vídeo, trabalha sobre um repositório de código e escreve ou revisa software em várias etapas. A interface de vídeo documentada recebe uma URL, o que pesa para equipes que têm gravações de tela internas.

Fonte: <https://huggingface.co/meituan-longcat/LongCat-2.5>

## Tamanho do modelo

O LongCat-2.5 é um modelo de mistura de especialistas. Cada token passa por um subconjunto de especialistas: 48 bilhões de parâmetros ativos por token, de 1,6 trilhão no total. Isso ajuda no custo de inferência, mas servir o modelo ainda exige o checkpoint completo.

Fonte: <https://huggingface.co/meituan-longcat/LongCat-2.5>

## Ganho sobre o LongCat-2.0

A comparação mais clara da avaliação da Meituan é com o antecessor. Em tarefas de repositório o salto é grande, e vale refazer os testes de quem descartou o 2.0.

- Terminal Bench v2.1: 88,4 contra 70,8
- DeepSWE v1.1: 64,6 contra 9,7

Fonte: <https://venturebeat.com/technology/meituan-releases-the-open-weights-of-its-longcat-2-5-llm-with-vision-under-a-permissive-mit-license>

## Contra os rivais pagos

O quadro é misto. No Terminal Bench v2.1, o LongCat-2.5 (88,4) fica a menos de um ponto do GPT-5.6 Sol (88,8) e do Claude Opus 5 (89,1). No Terminal Bench v4.0, marca 38,5 contra 53,9 do Opus 5.

A Meituan escolheu GPT-5.6 Sol e Claude Opus 5 como referência, mas os sucessores GPT-6.1 Sol (29 de setembro) e Claude Opus 5.5 (22 de setembro) já existiam. A leitura plausível é de um modelo competitivo com a geração anterior dos premium em tarefas selecionadas, por um preço bem menor. No leaderboard do v4.0, GPT-6.1 Sol marca 58,2 e Opus 5.5 marca 64,8, com configurações de teste diferentes (esforço máximo, Codex e Claude Code), então o confronto direto não é limpo.

Fonte: <https://venturebeat.com/technology/meituan-releases-the-open-weights-of-its-longcat-2-5-llm-with-vision-under-a-permissive-mit-license>

## API hospedada: preço e chave

Tarifa por milhão de tokens, em dólares: US$ 0,30 de entrada, US$ 1,20 de saída e US$ 0,006 de entrada em cache. A tarifa é por tempo limitado e não há data de término divulgada. O cache pesa para agentes que reenviam o mesmo contexto de repositório várias vezes.

- Crie uma conta na plataforma de API da LongCat.
- Abra a página API Keys.
- Crie a chave e guarde o valor: ele aparece uma só vez.
- Use o nome do modelo LongCat-2.5.

Fonte: <https://longcat.chat/platform/docs/pricing/longcat-2.5>

## Quanto custa uma rodada

Exemplo com volume fixo: 200 mil tokens de entrada sem cache e 100 mil de saída, em dólares. O cálculo fica abaixo do limite em que a OpenAI cobra mais pelo GPT-6.1 Sol. Na prática, retentativas, chamadas repetidas de ferramenta e raciocínio mais longo mudam a conta.

- DeepSeek-V4.1-Flash (fora de pico): US$ 0,09
- LongCat-2.5: US$ 0,18
- GPT-6.1 Sol: US$ 1,40
- Claude Opus 5.5: US$ 2,80
- Claude Fable 5.2: US$ 5,60

Fonte: <https://venturebeat.com/technology/meituan-releases-the-open-weights-of-its-longcat-2-5-llm-with-vision-under-a-permissive-mit-license>

## Como comparar antes de adotar

Meça o custo por resultado aceito: some retentativas, tempo de navegador ou sandbox, chamadas de reserva a outro modelo e o tempo de revisão dos patches. Meça também a taxa real de acerto de cache na ferramenta que o time usa.

- Dê a cada modelo o mesmo estado de repositório, navegador, suíte de testes, permissões de ferramenta e limite de tempo.
- Repita algumas tarefas para ver com que frequência cada modelo acerta.
- Em screenshot para código, pontue o resultado renderizado e o código separadamente.
- Em correção de bug, verifique se o patch ataca a causa e se o revisor precisou refazer.
- Antes de enviar código ou screenshots proprietários à API hospedada, veja como o serviço trata retenção, acesso e exclusão. Um sandbox com artefatos públicos ou sintéticos basta para a primeira avaliação.

Fonte: <https://venturebeat.com/technology/meituan-releases-the-open-weights-of-its-longcat-2-5-llm-with-vision-under-a-permissive-mit-license>

## Rodar localmente

O download são 208 arquivos, 3,56 TB. Só 48 bilhões de parâmetros ativam por token, mas todos os pesos precisam estar disponíveis.

O guia oficial de serviço, SGLang-FluentLLM, é para NPU, e não há comando oficial para GPU. As otimizações da Meituan, como expert weights e ativações em quatro bits, foram testadas em aceleradores chineses. Em outra infraestrutura, valide se o runtime carrega o checkpoint e preserva a visão e o uso de ferramentas. O README do repositório informa que o suporte multimodal foi removido dele.

```
hf download meituan-longcat/LongCat-2.5
```

Fonte: <https://huggingface.co/meituan-longcat/LongCat-2.5/tree/main>

## Além do vídeo

- No SWE Atlas (perguntas e respostas sobre código), o LongCat-2.5 marca 58,3 contra 33,1 do LongCat-2.0.
- O DeepSeek-V4.1-Flash lidera o grupo no DeepSWE (74,2), e o LongCat lidera no 3DCodeBench (55,4), enquanto o Claude Opus 5 lidera no Vision2Web (80,2).
- A API do DeepSeek-V4.1-Flash custa US$ 0,15 de entrada e US$ 0,60 de saída fora de pico, e US$ 0,30 e US$ 1,20 no pico. O checkpoint aberto dele é MIT.
- Em outubro, o Departamento de Segurança Interna dos EUA ordenou que agências civis federais excluíssem o DeepSeek de compras e sistemas. A VentureBeat não encontrou restrição federal que cite a Meituan ou o LongCat-2.5 até 9 de novembro.
- Os metadados do Hugging Face mostram 1,8T, enquanto a descrição técnica da Meituan fala em 1,6T. Para dimensionar a implantação, use os arquivos e o formato de serviço reais.
