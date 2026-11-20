# Habilidade do Faro: buscar vagas

## Ferramentas

1. **Firecrawl, como linha de comando** (já instalado no computador). Ferramenta principal.
   - Buscar: `firecrawl search "<consulta>" --limit 10`
   - Ler uma página: `firecrawl scrape <url> --only-main-content`
2. **Ferramenta de acesso web nativa do agente**: use só se o Firecrawl falhar.

## Sites

InfoJobs, Vagas, Indeed e Catho. Não use sites que exigem login (por exemplo, o LinkedIn).

## Passos

1. Leia o perfil em `data/perfil-do-usuario.md`.
2. Monte de 3 a 5 consultas a partir do perfil, juntando área, nível, localização e o nome do site. Exemplo: `vaga desenvolvedor front-end júnior São Paulo indeed`.
3. Para cada consulta, rode `firecrawl search` e junte os links de vagas.
4. Para cada vaga promissora, rode `firecrawl scrape` e extraia: título, empresa, localização, modelo de trabalho (se informado), link e as habilidades pedidas.
5. Compare as habilidades pedidas com as do perfil e calcule a contagem de correspondência (por exemplo, 3 de 4).
6. Grave tudo em `data/resultados-da-busca.md`, uma seção por vaga, com estes campos: título, empresa, localização, modelo de trabalho, link, habilidades pedidas, habilidades que faltam, correspondência.

## Regras

- Toda vaga precisa ter link.
- Se a extração de uma vaga falhar, registre a vaga com a situação "extração falhou" em vez de inventar dados.
- Se o Firecrawl pedir login ou não estiver configurado, avise o Regente: o comando é `firecrawl login`.
