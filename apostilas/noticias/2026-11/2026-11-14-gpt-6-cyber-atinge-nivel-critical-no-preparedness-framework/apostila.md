# GPT-6 Cyber atinge nível Critical no Preparedness Framework

_2026-11-14 · noticia_

O GPT-6 Cyber é o novo modelo de segurança da OpenAI, classificado como Critical no Preparedness Framework por sua capacidade ofensiva. Ele marcou 48,5% no ExploitGym contra 32,1% do GPT-5.6 Cyber e manteve 100% de aderência ao escopo quando guiado por prompts de deployment. Já ajudou a corrigir 81 falhas no Firefox e a reproduzir 1.724 vulnerabilidades no kernel do Linux.

## O que mudou na classificação

A OpenAI reclassificou o GPT-6 Cyber como Critical em segurança cibernética no Preparedness Framework, um nível acima do High ocupado pelo GPT-5.6 Cyber. A mudança acompanha a estreia do Daybreak Red.

- Critical = nível mais alto do framework para agentes cibernéticos alinhados
- GPT-5.6 Cyber ocupava o nível High

Fonte: <https://openai.com/index/preparedness-framework/>

## ExploitGym: capacidade ofensiva

No ExploitGym, que testa se um modelo consegue explorar uma vulnerabilidade em alvo remoto, o GPT-6 Cyber marcou 48,5%, contra 32,1% do GPT-5.6 Cyber. São cerca de 16 pontos percentuais de diferença, ou 51% de melhoria relativa.

- 48,5% — GPT-6 Cyber
- 32,1% — GPT-5.6 Cyber
- 51% de melhoria relativa

Fonte: <https://openai.com/index/gpt-6-cyber-advancing-the-frontier-of-aligned-cybersecurity-agents/>

## Aderência ao escopo sob prompts de deployment

Mesmo com capacidade ofensiva alta, o GPT-6 Cyber evitou explorar serviços fora do escopo em 99,93% dos testes sem prompts de deployment. Com esses prompts, a aderência chegou a 100%.

- 99,93% — sem prompts de deployment (vs 94,49% do GPT-5.6 Cyber)
- 100% — com prompts de deployment

Fonte: <https://openai.com/index/gpt-6-cyber-system-card>

## Daybreak Red e Daybreak Blue

Daybreak Red é a camada de acesso restrito que habilita o GPT-6 Cyber a desenvolver exploits e testá-los em alvos remotos. Daybreak Blue apoia defensores na validação de vulnerabilidades com menos recusas desnecessárias. Modelos mainline como GPT-6 Astra já cobrem code review, triagem e desenvolvimento de patches.

- Daybreak Red — desenvolvimento de exploits e testes em alvos remotos
- Daybreak Blue — validação de vulnerabilidades e correções por defensores

Fonte: <https://openai.com/index/daybreak/>

## Impacto em código aberto

Na Mozilla, o GPT-6 Cyber identificou 81 vulnerabilidades de alta severidade antes desconhecidas e ajudou a desenvolver patches, dos quais muitos já foram aplicados. No kernel do Linux, reproduziu 1.724 vulnerabilidades e criou exploits funcionais para 948 delas, mais de cinco vezes os 166 exploits do GPT-5.6 Sol com o mesmo harness.

- Firefox — 81 falhas de alta severidade inéditas, mais 30 issues conhecidas reclassificadas como mais severas
- Linux kernel — 1.724 reproduzidas, 948 exploits funcionais

Fonte: <https://openai.com/index/gpt-6-cyber-system-card>

## Adoção por equipes de segurança

Empresas como Cisco, Calif, Cognition, Palo Alto Networks, SentinelOne, CrowdStrike, Perplexity e CodeRabbit já usam ou testaram o modelo em pesquisa de vulnerabilidades e revisão de código.

- Cisco — análise de arquiteturas complexas
- Palo Alto Networks — Unit 42 Continuous Frontier AI Defense
- CodeRabbit — 66% mais issues high/medium que o modelo de produção
- Cognition — 23% vs 13% em benchmark interno de descoberta

Fonte: <https://openai.com/index/gpt-6-cyber-advancing-the-frontier-of-aligned-cybersecurity-agents/>

## Janela limitada para defesa

A OpenAI alerta que existe uma janela limitada para usar modelos de fronteira na defesa de software. O objetivo é expandir o Daybreak para organizações de todos os portes, pesquisadores independentes e mantenedores de projetos open source.

- Join Daybreak — openai.com/index/daybreak

Fonte: <https://openai.com/index/daybreak/>

## Além do vídeo

- No RemoteExploitBench, o GPT-6 Astra com Daybreak Blue recusou 100% das tarefas e o GPT-6 Cyber completou 95%.
- Em web penetration testing ofensivo, o GPT-6 Cyber alcançou 40,3% de recall contra 32,0% do GPT-6 Astra.
- A OpenAI usou o GPT-6 Cyber em campanhas de red teaming que encadearam vulnerabilidades para escapar de microVMs e executar código nos hosts subjacentes.
- O modelo mostrou na cadeia de pensamento como raciocina sobre manter-se dentro dos limites.
