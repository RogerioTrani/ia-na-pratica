# Apostila: Aula 3: crie o Prumo, o agente que ranqueia as vagas

Nesta aula você cria o Prumo, o terceiro agente da série. Ele lê as vagas que o Faro encontrou e o perfil montado pelo Regente, e devolve só as melhores, em ordem, com nota de 0 a 100, pontos fortes, lacunas e o motivo da nota. O caminho é planejar, definir pesos e formato, implementar, reiniciar o Regente e testar com um perfil de exemplo.

## O que o Prumo resolve

Depois da busca, o arquivo de resultados do Faro pode ter de dez a vinte vagas. A contagem de habilidades, como 3 de 4, não diz qual disputar primeiro: uma vaga que bate 3 de 4 pode ser presencial em outra cidade, e outra que bate 2 de 4 pode ser remota e no nível certo.

O Prumo aplica um critério explícito a cada vaga e entrega uma lista ordenada, para você decidir onde gastar o tempo. Cada vaga traz os mesmos campos, o que deixa o resultado comparável entre execuções.

Fonte: <https://zed.dev/docs/ai/agent-panel>

## Antes de começar

- Zed aberto na pasta agente-de-vagas (zed.dev)
- OpenRouter com um modelo gratuito (openrouter.ai)
- Regente e Faro funcionando
- Perfil na pasta data
- Resultados da busca preenchidos pelo Faro; se o arquivo ainda está vazio, volte à aula 2, parte 2, e rode a busca
- plano.md e plano-aula-2.md no projeto

Fonte: <https://zed.dev/docs/ai/use-a-gateway>

## Passos 1 a 3: abra a conversa e peça o plano

Tudo de que o agente precisa está nos planos, não na memória da conversa. Por isso a conversa começa nova e aponta os planos que já existem.

- Passo 1. No painel do agente do Zed, clique no sinal de mais para iniciar uma conversa nova. Você deve ver um painel limpo, sem mensagens.
- Passo 2. Escreva a mensagem abaixo e digite @ para escolher os dois arquivos de plano. Se a lista não abrir, apague o caractere e digite @ de novo, sem espaço antes. Mensagem: Vamos construir o terceiro plano. @plano.md @plano-aula-2.md
- Passo 3. Cole o pedido abaixo na mesma conversa e envie. Use a palavra planeje: se mandar criar, o agente sai implementando. Se isso acontecer, interrompa e repita o pedido com planeje.

```
Dessa vez, planeje um terceiro agente chamado Prumo, que vai fazer o ranking das vagas encontradas pelo Faro. Ele deve ler o arquivo de resultados da busca e comparar cada vaga com o perfil da pessoa, que fica no arquivo do perfil. Faça parecido com o que fizemos para o Faro, olhando como ele foi estruturado, mas sem copiar igual, porque este agente tem outra função. Salve o plano no arquivo plano-aula-3.md.
```

Fonte: <https://zed.dev/docs/ai/agent-panel>

## Passo 4: regras de negócio do Prumo

Na mesma conversa, escreva as regras em lista. O Prumo trabalha só com o que o Faro trouxe e, quando a vaga não informa algo, avisa em vez de inventar. Se alguma regra faltar no plano, peça o acréscimo antes de seguir.

## Passos 5 e 6: pesos, formato e revisão do plano

Sem pesos, o modelo dá nota no feeling. Sem o motivo, a nota é só um número, e você não consegue confiar nela nem contestar. Peça que o plano descreva o critério em pesos e que cada vaga tenha sempre os mesmos campos. Se a soma dos pesos não fechar em 100, peça a correção ao agente.

- Cole o texto abaixo, envie a mensagem e abra o plano-aula-3.md que o agente criar.
- Confira se o Prumo aparece ao lado do Faro, abaixo do Regente.
- Confira se a habilidade de ranking é uma skill própria, no mesmo padrão das do Faro.
- Confira a entrada, os pesos e o formato. Se algo faltar, escreva o ajuste na conversa e peça ao agente que atualize o plano.

## Passos 7 e 8: implemente e reinicie o Regente

Com o plano revisado e a conversa ainda curta, basta ser breve. O agente cria o Prumo, a skill de ranking e edita o Regente para conhecer o novo agente. Se ele pedir confirmação de uma edição, leia e aceite. Se tiver dúvida, volte ao plano e ajuste o texto, não o código.

Depois abra uma conversa nova e mande o agente ler as instruções do Regente, porque uma conversa antiga não sabe da edição. No menu devem aparecer: buscar vagas, ver o ranking das melhores vagas para o seu perfil, treinar uma entrevista simulada (funcionalidade futura) e refazer o quiz. Se o ranking não aparecer, confira se a implementação terminou.

- Passo 7: envie a mensagem do bloco abaixo.
- Passo 8: em conversa nova, envie: Leia e siga o @AGENTS.md

Fonte: <https://zed.dev/docs/ai/agent-panel>

## Passos 9 e 10 e teste: quiz, busca e ranking

Refaça o quiz com o perfil abaixo, o mesmo da aula anterior, para comparar antes e depois. Use só dados de exemplo. Com dados de verdade, não envie ao modelo nome completo, documento, telefone ou endereço: o perfil só precisa do que serve para comparar com a vaga.

Depois escolha buscar vagas no menu e espere o Faro terminar. No arquivo de resultados você vê vagas com extração completa e uma cuja extração falhou, que o Faro registra em vez de inventar. Volte ao menu e peça o ranking. Se o arquivo de resultados estiver vazio, rode a busca de novo antes.

Confira se todas as vagas trazem os mesmos campos. A vaga com extração falha fica fora do ranking, com aviso de que faltaram dados. Exemplo do nosso teste, só para ilustrar o formato: 1) Desenvolvedor(a) Front-end Júnior, empresa A, nota 88/100; 2) Desenvolvedor(a) Web Júnior, empresa B, nota 79/100; 3) Desenvolvedor(a) Front-end Pleno, empresa C, nota 61/100; 4) Analista de Interface, empresa D, nota 47/100.

Para o segundo teste, refaça o quiz com modelo de trabalho remoto e peça o ranking de novo. A vaga 3 deve subir e a 4 deve cair mais. Se o ranking não reagir, ajuste o plano, mande o agente comparar com o que está implementado e rode tudo de novo.

## Além do vídeo

- Dica do desafio: use o ranking, pegue a vaga em primeiro lugar e pergunte sobre as lacunas que o Prumo apontou, para treinar o que mais pesa na vaga mais desejada.
- Ao mexer num peso, teste o resto: o topo do ranking e o tamanho das justificativas podem mudar.
- Com o plano como fonte de verdade, trocar de modelo é rápido: rode o mesmo plano no modelo novo e compare.
- Para tarefas de leitura e comparação, como o ranking, teste modelos gratuitos ou baratos primeiro e só suba para um mais caro se o resultado ficar fraco.
- A ideia de um time de agentes, cada um com uma função, serve para outras áreas: um agente para pesquisar leis e outro para elaborar peças, por exemplo.
