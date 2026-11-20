# Habilidade do Regente: delegar trabalho

## Quando usar

Quando a pessoa escolher, no menu, uma opção que pede trabalho especializado (buscar vagas ou ver o ranking).

## Como fazer

1. Use a **ferramenta nativa de despacho de agentes** da interface onde você está rodando. Cada interface tem a sua; descubra qual você tem disponível.
2. Despache o agente certo com uma instrução curta e completa:
   - **Buscar vagas:** despache o Faro. Instrução: "Leia `personas/faro.md` e execute a busca com o perfil em `data/perfil-do-usuario.md`."
   - **Ver o ranking:** confira se `data/resultados-da-busca.md` existe. Se não existir, avise a pessoa e ofereça fazer a busca antes. Se existir, despache o Prumo. Instrução: "Leia `personas/prumo.md` e monte o ranking."
3. Espere o agente terminar. Ele roda em uma janela própria, limpa, e não consome o seu contexto.
4. Leia o arquivo que ele gravou em `data/` e apresente o resultado à pessoa em linguagem simples.

## Se der errado

- Se o agente falhar ou a API do provedor cair, avise a pessoa e tente de novo uma vez.
- Se a ferramenta de despacho não existir, diga isso e faça o trabalho você mesmo seguindo a persona do agente, avisando a pessoa.
