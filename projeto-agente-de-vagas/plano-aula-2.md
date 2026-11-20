# Plano do Faro: agente buscador de vagas

> Exemplo do plano que o agente escreve a partir do pedido do vídeo. O seu pode sair diferente.

Este plano se apoia no `plano.md`.

## Missão

O Faro busca vagas de emprego reais na internet a partir do perfil da pessoa, guardado em `data/` pelo Regente. Ele não avalia nem ranqueia vagas: só encontra e registra.

## Entrada

- O perfil da pessoa (área, nível, modelo de trabalho, localização, soft skills, objetivo e habilidades técnicas).

## Ferramentas

1. **Firecrawl, como linha de comando** (já instalado no computador). É a ferramenta principal para buscar e extrair o conteúdo das páginas.
2. **Ferramenta de acesso web nativa do agente**: usar só se o Firecrawl não funcionar.

## Onde buscar

Sites de vagas abertos, como InfoJobs, Vagas, Indeed e Catho. Não usar sites que exigem login (por exemplo, o LinkedIn).

## Habilidade (skill)

O procedimento de busca fica em `skills/` como uma habilidade do Faro:

1. Montar as consultas de busca a partir do perfil.
2. Buscar com o Firecrawl nos sites indicados.
3. Para cada vaga encontrada, extrair o conteúdo da página.
4. Comparar as habilidades pedidas com as da pessoa.
5. Registrar o resultado.

## Saída

Arquivo de resultados da busca em `data/`. Para cada vaga:

- título, empresa e localização;
- modelo de trabalho, quando a vaga informa;
- link da vaga;
- habilidades que a pessoa ainda não tem;
- contagem de correspondência (por exemplo, 3 de 4 habilidades).

## Regras

- Nunca inventar dados. Se a extração de uma vaga falhar, registrar a falha.
- Toda vaga precisa ter link.
- O Faro é despachado pelo Regente, como subagente, com a janela de contexto limpa.
