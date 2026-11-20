# Habilidade do Prumo: ranquear vagas

## Entrada

- `data/perfil-do-usuario.md`: o perfil completo.
- `data/resultados-da-busca.md`: para cada vaga, título, empresa, localização, modelo de trabalho (se informado), link, habilidades pedidas e a contagem de correspondência do Faro.

## Critério da nota (ajustável)

| Critério | Pontos |
| --- | --- |
| Habilidades técnicas (mais peso para as obrigatórias do que para as desejáveis) | 40 |
| Nível de experiência: vaga acima ou abaixo do nível declarado perde pontos | 20 |
| Modelo de trabalho e localidade: remoto pedido e vaga presencial em outra cidade perde quase tudo | 20 |
| Área de interesse e preferências declaradas no quiz | 20 |
| **Total** | **100** |

Toda nota vem com o motivo, em uma ou duas frases.

## Passos

1. Leia o perfil e os resultados.
2. Descarte da avaliação as vagas com extração falha; liste-as no fim com o aviso de que faltaram dados.
3. Para cada vaga restante, calcule a nota pelos quatro critérios. Se uma informação não estiver na vaga, escreva "não informado" e não chute.
4. Ordene da maior nota para a menor e fique com as 5 melhores.
5. Grave `data/ranking.md` com, para cada vaga, sempre os mesmos campos:
   1. posição no ranking
   2. título da vaga
   3. empresa
   4. link
   5. nota de aderência
   6. pontos fortes (o que a pessoa já tem e a vaga pede)
   7. lacunas (o que a vaga pede e a pessoa ainda não tem)
   8. por que entrou no ranking

## Teste

Mude o modelo de trabalho do perfil de híbrido para remoto e rode de novo. Uma vaga remota deve subir e uma presencial deve cair. Se o ranking não reagir, ajuste os pesos neste arquivo e teste de novo.
