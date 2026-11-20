# Pedidos e comandos: Aula 3: crie o Prumo, o agente que ranqueia as vagas

Os textos abaixo são os que aparecem na tela do vídeo, na ordem. Copie, cole e adapte ao seu caso.

## PASSO 1: Abra uma conversa nova

```text
Painel do agente > + (nova conversa)
```

**Você deve ver:** Um painel limpo, sem mensagens, pronto para o primeiro pedido.

## PASSO 2: Aponte os planos que já existem

```text
Vamos construir o terceiro plano. @plano.md @plano-aula-2.md
```

**Você deve ver:** Os dois arquivos aparecem como referências na mensagem.

## PASSO 3: Peça para planejar, não para criar

```text
Dessa vez, planeje um terceiro agente chamado Prumo, que vai fazer o ranking das vagas encontradas pelo Faro. Ele deve ler o arquivo de resultados da busca e comparar cada vaga com o perfil da pessoa, que fica no arquivo do perfil. Faça parecido com o que fizemos para o Faro, olhando como ele foi estruturado, mas sem copiar igual, porque este agente tem outra função. Salve o plano no arquivo plano-aula-3.md.
```

**Você deve ver:** O agente lê os arquivos e escreve texto, sem criar código.

**Se não deu certo:** Se mandar criar em vez de planejar, o agente sai implementando; interrompa e repita o pedido com a palavra planeje.

## PASSO 4: Escreva as regras de negócio

```text
Regras do Prumo: não busca nada na internet (quem busca é o Faro); lê o perfil inteiro (habilidades, nível, modelo de trabalho, localidade, área de interesse e preferências do quiz); dá a cada vaga uma nota de aderência de 0 a 100 e explica de onde ela veio; entrega o ranking ordenado, só com as melhores e com um limite definido no plano; diz, para cada vaga, o que a pessoa já tem de forte e o que falta; se uma informação não estiver na vaga, como o modelo de trabalho, diz que não foi informada e não inventa.
```

**Você deve ver:** As regras entram no plano do Prumo.

## PASSO 5: Defina os pesos e o formato

```text
Pesos (exemplo, pode ajustar): habilidades técnicas, 40 pontos (mais peso para as obrigatórias do que para as desejáveis); nível de experiência, 20; modelo de trabalho e localidade, 20; área de interesse e preferências, 20. Toda nota vem com o motivo. Campos de cada vaga: posição, título da vaga, empresa, link, nota de aderência, pontos fortes, lacunas e motivo de a vaga ter entrado no ranking.
```

**Você deve ver:** Os pesos e a lista de campos aparecem escritos no plano.

**Se não deu certo:** Se a soma dos pesos não fechar em 100, peça a correção ao agente.

## PASSO 6: Envie e revise o plano

```text
Enviar a mensagem e abrir plano-aula-3.md
```

**Você deve ver:** Um arquivo novo com o plano: o Prumo ao lado do Faro, abaixo do Regente, com a skill de ranking, a entrada, os pesos e o formato.

**Se não deu certo:** Se algo faltar, escreva o ajuste na conversa e peça ao agente que atualize o plano.

## PASSO 7: Mande implementar o plano

```text
Muito obrigado, agora por favor implemente o plano @plano-aula-3.md
```

**Você deve ver:** O agente cria e edita arquivos no projeto: o Prumo, a skill de ranking e a atualização do Regente.

## PASSO 8: Reinicie o Regente

```text
Leia e siga o @AGENTS.md
```

**Você deve ver:** O menu oferece buscar vagas, ver o ranking das melhores vagas para o seu perfil, treinar uma entrevista simulada (funcionalidade futura) e refazer o quiz.

**Se não deu certo:** Se o ranking não aparecer no menu, confira se a implementação terminou.

## PASSO 9: Refaça o quiz com perfil de teste

```text
Perfil de teste: front-end, júnior, modelo de trabalho híbrido, São Paulo, comunicação e resolução de problemas, transição de carreira, habilidades HTML, CSS, JavaScript, React e Git
```

**Você deve ver:** O perfil de teste fica salvo na pasta data.

**Se não deu certo:** Com dados de verdade, não envie nome completo, documento, telefone ou endereço ao modelo.

## PASSO 10: Rode a busca e depois o ranking

```text
Menu > buscar vagas; depois Menu > ver o ranking das melhores vagas
```

**Você deve ver:** O Faro entrega vagas com extração completa e registra a que falhou; o Prumo monta a lista ordenada.

**Se não deu certo:** Se o arquivo de resultados estiver vazio, rode a busca de novo antes de pedir o ranking.

## TESTE: Confira o ranking e mude o perfil

```text
Refazer o quiz com modelo de trabalho remoto, depois pedir o ranking
```

**Você deve ver:** Ranking ordenado com os mesmos campos em todas as vagas; a vaga com extração falha fica fora, com aviso. Com o perfil remoto, a vaga 3 sobe e a 4 cai mais.

**Se não deu certo:** Se o ranking não reagir, ajuste o plano, mande o agente comparar com o que está implementado e rode tudo de novo.
