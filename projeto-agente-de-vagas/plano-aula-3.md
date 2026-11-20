# Plano do Prumo: agente que ranqueia vagas

> Exemplo do plano que o agente escreve a partir do pedido do vídeo. O seu pode sair diferente.

Este plano se apoia no `plano.md` e no `plano-aula-2.md`, e segue o mesmo padrão de pastas e de skills do Faro, sem copiá-lo: a função é outra.

## Missão

O Prumo lê as vagas que o Faro encontrou e o perfil da pessoa e devolve só as melhores, em ordem, cada uma com nota de aderência, pontos fortes, lacunas e o motivo da nota.

## Regras de negócio

- Não busca nada na internet: quem busca é o Faro. O Prumo só trabalha com o que o Faro trouxe.
- Lê o perfil inteiro: habilidades, nível, modelo de trabalho, localidade, área de interesse e preferências do quiz.
- Dá a cada vaga uma nota de aderência de 0 a 100 e explica de onde ela veio.
- Entrega o ranking ordenado, das mais aderentes para as menos, com um limite de vagas (por exemplo, as 5 melhores).
- Para cada vaga, diz o que a pessoa já tem de forte e o que falta.
- Se uma informação não estiver na vaga (por exemplo, o modelo de trabalho), diz que **não foi informada** e não inventa.
- Vaga com extração falha fica fora do ranking, com aviso.

## Entrada

Para cada vaga do arquivo de resultados da busca: título, empresa, localização, modelo de trabalho (quando informado), link, habilidades pedidas e a contagem de correspondência calculada pelo Faro. Mais o perfil completo da pessoa.

## Critério da nota (exemplo, ajustável)

| Critério | Pontos |
| --- | --- |
| Habilidades técnicas (mais peso para as obrigatórias) | 40 |
| Nível de experiência | 20 |
| Modelo de trabalho e localidade | 20 |
| Área de interesse e preferências | 20 |
| **Total** | **100** |

Toda nota vem acompanhada do motivo.

## Formato da resposta

Cada vaga do ranking traz sempre os mesmos campos:

1. posição no ranking
2. título da vaga
3. empresa
4. link
5. nota de aderência
6. pontos fortes
7. lacunas
8. por que entrou no ranking

## Habilidade (skill)

A habilidade de ranking é um arquivo próprio em `skills/`, no mesmo padrão das do Faro.

## Regente

O Regente passa a oferecer, no menu, a opção de ver o ranking das melhores vagas. A entrevista simulada continua como funcionalidade futura.
