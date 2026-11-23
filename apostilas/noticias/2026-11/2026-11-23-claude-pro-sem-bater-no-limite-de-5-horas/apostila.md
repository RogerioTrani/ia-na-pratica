# Claude Pro sem bater no limite de 5 horas

_2026-11-23 · noticia_

Quem usa o Claude Pro esbarra no limite de 5 horas e no semanal. Um usuário passou a abrir as sessões do Claude Code com o modo opusplan: o Opus planeja e o Sonnet executa. No teste com um Tetris, o opusplan custou 16% menos que o Opus puro e escreveu 239 linhas contra 431. A troca de modelo tem um custo, uma re-leitura de 19,3 mil tokens.

## Os dois limites do Pro

O Pro tem um limite de sessão e um limite semanal. A sessão começa na primeira mensagem e volta a encher cinco horas depois. O semanal tem reset próprio.

Os dois valem para o app Claude e para o Claude Code. Uma sessão longa de código gasta o mesmo saldo que você usaria numa conversa no chat.

A Anthropic não informa quantas mensagens restam, porque cada mensagem custa um valor diferente. Cada plano é medido contra o de baixo: o Pro dá pelo menos 5x o uso do plano grátis, e o Max dá 5x o uso do Pro. O alcance real depende do tamanho da conversa, do modelo e do nível de esforço.

## Como acompanhar o consumo

Os medidores mostram porcentagem, não número de mensagens. Você os vê na página Usage, nas configurações, ou com o comando abaixo dentro do Claude Code.

```
/usage
```

## Por que não ir direto para o Max

O Claude Max custa $100 por mês. Num mês ruim, o autor do teste gastou mais de $300 em créditos de uso para passar do limite.

Nos meses leves, esse valor não se justifica. O Max faz sentido para quem esgota o Pro toda semana. Para quem oscila de mês a mês, o opusplan estica o plano que já está pago.

## Opusplan: Opus planeja, Sonnet executa

O Opus, mais caro, compensa na hora de pensar. O Sonnet executa bem um plano bem feito, por menos. O opusplan, modo do Claude Code, aplica essa divisão: o Opus só entra no planejamento, e quando você aprova o plano o Sonnet assume a execução.

Das três variáveis que definem o alcance do plano (tamanho da conversa, modelo e esforço), o modelo é a mais fácil de controlar. Com a construção feita no Sonnet, cada tarefa tira menos do limite de 5 horas e do semanal do que tiraria no Opus puro.

- Abra o Claude Code.
- Digite o comando abaixo para ativar o modo.
- Aprove o plano feito pelo Opus. Daí em diante o Sonnet executa.

```
/model opusplan
```

Fonte: <https://code.claude.com/docs/en/model-config>

## O teste: Tetris duas vezes

O prompt foi o mesmo nas duas rodadas: construir um Tetris básico em um único arquivo HTML. Uma rodada usou só o Opus, a outra usou opusplan.

As duas começaram em modo de plano, com esforço médio, cada uma numa pasta vazia, uma logo após a outra na mesma janela de cinco horas.

Nas duas, o jogo abre, limpa linhas e termina quando os blocos empilham. O autor preferiu o visual do opusplan nos blocos.

- Custo estimado: 16% menor com opusplan, pela estimativa do Claude Code, que precifica cada rodada a preços de API.
- Linhas escritas: 239 no opusplan contra 431 no Opus puro.

## O custo da troca de modelo

A passagem do plano para o Sonnet causou o único cache miss do teste. O /usage listou a mudança de modelo entre as causas prováveis, com 19,3 mil tokens re-lidos.

Esse custo se repete uma vez por tarefa. O ganho, porém, cresce com o tamanho da obra: quanto maior a construção, maior a parte do trabalho que fica com o Sonnet. Num dia inteiro de builds a diferença pesa mais do que num Tetris pequeno.

## Quando escolher o quê

Se você esgota o Pro toda semana, o Max faz sentido. Se o uso varia muito de mês para mês, o opusplan é o caminho do meio: Opus onde o custo se justifica, Sonnet na execução e limites menos apertados.

O opusplan não elimina os limites. Ele os afasta o bastante para o autor adiar o upgrade de $80 por mês sobre o Pro.

## Além do vídeo

- Pelo preço de API da estimativa do Claude Code, o opusplan custou $0,34 e o Opus puro $0,40.
- Mais da metade dos $0,34 do opusplan foi gasta só no planejamento do Opus.
- As duas rodadas somaram dois pontos à barra de sessão e nada à barra semanal.
- As duas rodadas começaram em modo de plano, com esforço médio.
- O Pro dá pelo menos 5x o uso do plano grátis, e o Max dá 5x o uso do Pro.
