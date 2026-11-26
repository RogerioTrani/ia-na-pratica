# JEV e Claude classificam 17.020 leads em 40 segundos

_2026-11-24 · tutorial_

O JEV é um modelo de IA que não escreve texto: ele classifica. Nesta apostila você aprende o que ele é, como acessá-lo pela API da TypeSafe, como conectá-lo ao Claude Code com uma skill oficial e como usá-lo para classificar dezenas de milhares de leads em segundos. Você também vê três casos de uso reais: priorizar conexões do LinkedIn, mapear objeções em calls de vendas e acompanhar uma call com um copiloto em tempo real. Ao final, você terá um passo a passo completo para reproduzir a classificação na sua própria base.

## O que você terá no fim

JEV é um modelo de inteligência artificial feito para classificar. Ele não gera texto. Ele não substitui o Claude, o ChatGPT ou o Gemini na criação de texto, no raciocínio complexo ou na pesquisa. Ele entra onde esses modelos são lentos e caros: em tarefas repetitivas de classificação sobre grandes volumes de informação.

Esta apostila mostra como preparar o acesso ao JEV pela API da TypeSafe, instalar a skill oficial no Claude Code, exportar suas conexões do LinkedIn e pedir a classificação dos leads. Você também conhece dois outros usos: mapear objeções em dezenas de calls de vendas e acompanhar uma call com um copiloto em tempo real.

O resultado prático é uma lista organizada entre decisores, não decisores e casos para revisão, pronta para orientar sua próxima análise comercial. Os passos, comandos e caminhos abaixo vêm da documentação oficial da TypeSafe e da ajuda do LinkedIn.

## Como o JEV funciona

Uma LLM padrão gera texto token por token. Esse processo é o que torna a resposta lenta e cara. O JEV não gera texto. Ele só devolve classificações em três formatos fixos. Por ser um modelo pequeno e específico, ele processa muito mais rápido e a um custo muito menor.

O JEV foi lançado por Diogo Almeida e sua equipe e é oferecido pela empresa TypeSafe AI. Segundo o anúncio de lançamento, o modelo promete de 20 a 200 vezes mais velocidade e de 40 a 400 vezes menor custo do que os modelos padrão usados habitualmente. Essas cifras são a promessa de lançamento; não as trate como resultado de um benchmark independente.

Fonte: <https://docs.typesafe.ai/introduction/quickstart>

## Os três formatos de classificação

O JEV só responde de três formas. Se você pedir algo fora disso, ele não consegue entregar.

Primeiro formato: sim ou não para uma pergunta. Você envia as características de um lead e pergunta se ele é decisor. O JEV responde sim ou não; no exemplo adiante, o pedido incluiu também a opção revisar.

Segundo formato: escolha a partir de uma lista que você fornece. Você envia a transcrição de uma call e uma lista de objeções possíveis (preço, timing, foi ver com sócio, não teve nenhuma objeção). O JEV escolhe a opção mais adequada.

Terceiro formato: nota de 1 a 10 para uma tarefa. Você envia dados de uso de um software e pede a nota de risco de cancelamento de 1 a 10.

- Sim ou não: para perguntas diretas sobre um registro.
- Escolha em lista: para classificar entre opções que você define.
- Nota de 1 a 10: para risco, prioridade, ICP ou qualquer escala numérica.

## Onde o JEV entra no seu fluxo

O JEV não substitui seu modelo principal. Ele funciona como ferramenta delegada: você o dá ao Claude ou ao ChatGPT, e o agente decide em qual momento usá-lo para economizar tempo e custo. O modelo principal continua responsável por escrever texto, fazer contas, gerar imagem e mídia, raciocinar sobre tarefas complexas e pesquisar.

O melhor fluxo usa os dois: o JEV para classificação em volume, e a LLM de sua escolha para tudo que exige linguagem natural. Assim você gasta créditos de texto apenas sobre os registros que valem a pena, como os leads classificados como decisores.

Existem duas formas de começar a usar o JEV: criar conta direta na TypeSafe AI ou usar o OpenRouter, plataforma que conecta a mais de 600 modelos de inteligência artificial com uma única conta e um único saldo de créditos. Este tutorial segue o caminho direto pelo console da TypeSafe.

Fonte: <https://openrouter.ai/docs/guides/community/jev>

## Antes de começar

- Claude Code instalado no seu computador.
- Conta no console da TypeSafe, a empresa do JEV, com créditos para chamadas à API.
- Conta no LinkedIn com suas conexões.
- Navegador com acesso à internet.
- Planilha de conexões exportada do LinkedIn (veja o passo correspondente).

## Passo a passo: prepare o acesso à API

1. Acesse o console da TypeSafe, a empresa responsável pelo JEV. Ao entrar, deve aparecer o painel de gerenciamento, com a área de chaves. Se essa tela não aparecer, confira se você entrou no console da sua conta antes de continuar.
2. Gere uma chave de API na página de chaves. A chave permite que a integração faça chamadas ao JEV pela sua conta. O resultado esperado é uma nova chave disponível no painel. Se nenhuma chave aparecer, permaneça nessa etapa e confira se a criação foi concluída na conta correta.
3. Guarde o valor da chave em local privado e nunca o exiba na conversa nem em capturas de tela ou gravações.

```
console.typesafe.ai
console.typesafe.ai/keys
```

Fonte: <https://docs.typesafe.ai/introduction/quickstart>

## Passo a passo: instale a skill no Claude

1. No terminal, rode os dois comandos abaixo. O primeiro adiciona o repositório de skills da TypeSafe e o segundo instala o plugin. A função desta etapa é permitir que o Claude delegue a classificação ao serviço, em vez de executar sozinho todo o trabalho.
2. Ao terminar, a skill deve estar disponível no Claude Code. Se isso não acontecer, confira o retorno dos comandos antes de enviar a planilha.
3. Guarde também a chave de API na variável de ambiente TYPESAFE_API_KEY, para a skill usá-la.

```
claude plugin marketplace add typesafe-ai/skills
claude plugin install typesafe@typesafe-ai
```

Fonte: <https://docs.typesafe.ai/agent-skill.md#installation>

## Passo a passo: exporte suas conexões do LinkedIn

1. No LinkedIn, abra o menu do seu perfil, entre em configurações e privacidade, abra privacidade dos dados e procure baixe seus dados. Escolha o download maior e solicite o arquivo.
2. O LinkedIn envia o e-mail em até 24 horas, e o link para baixar fica disponível por 72 horas.
3. Nos dados, localize o arquivo de conexões, que traz nome, perfil, e-mail, empresa, cargo e data de cada conexão. Confira se ele contém os contatos que você pretende analisar.

```
Eu > Configurações e privacidade > Privacidade dos dados > Baixe seus dados
```

Fonte: <https://www.linkedin.com/help/linkedin/answer/a1339364>

## Passo a passo: classifique a planilha com o JEV

1. Forneça a planilha de conexões ao Claude e peça o uso da skill do JEV para identificar se cada lead é decisor. Peça como respostas sim, não e revisar.
2. Se o Claude não acionar a skill sozinho, chame-a pelo comando abaixo.
3. Você deve ver a skill sendo acionada e, ao final, a classificação retornando. Se isso não aparecer, confira se o Claude recebeu a planilha e utilizou a integração.

```
/typesafe:typesafe-ai
```

Fonte: <https://docs.typesafe.ai/agent-skill.md>

## Exemplo completo: classificação de 17.020 conexões

Em um teste relatado, a planilha exportada do LinkedIn tinha 17.020 conexões. Quem fez o teste forneceu a planilha ao Claude e acionou a skill do JEV, com acesso pelo OpenRouter, pedindo a classificação entre sim, não e revisar para a pergunta 'o lead é decisor?'.

Menos de 40 segundos depois, a classificação retornou. O próprio JEV levou 13 segundos; o restante, muito provavelmente, foi o Claude trabalhando na resposta. O resultado: mais de 5.000 conexões classificadas como decisores e mais 2.800 marcadas para revisão, muito provavelmente por falta de informação suficiente na descrição da pessoa. Esses números descrevem aquela execução específica e não garantem o mesmo tempo ou custo em outra conta ou planilha.

A planilha ganhou três novas colunas: classificação (sim, não ou revisar), nota de confiança da resposta e origem JEV, para saber que veio do serviço. O fluxo seguinte sugerido é trabalhar apenas sobre os decisores para gerar mensagens de prospecção personalizadas, economizando créditos de texto.

## Caso de uso: objeções em calls de vendas

O segundo caso analisa 45 calls de vendas. O Claude leu as transcrições e montou uma lista de 16 possíveis objeções. Em seguida, delegou ao JEV a tarefa de escolher, para cada call, qual objeção mais se encaixava, usando o segundo formato de classificação.

Das 45 calls, 41 foram avaliadas (provavelmente quatro vieram sem transcrição). O resultado: a objeção 'vou pensar ou adiar' apareceu em 15 das calls (37%), objeções de integração técnica ou de já possuir algum sistema em 17%, e 'precisa falar com um sócio ou outro decisor' em 17%, entre outras.

A comparação proposta é com pedir ao Claude ou ao ChatGPT que processem sozinhos 41 transcrições longas, o que, segundo quem fez o teste, seria muito mais lento e caro.

- Vou pensar ou adiar (15 calls, 37%).
- Integração técnica ou já possuir sistema (17%).
- Precisa falar com sócio ou outro decisor (17%).
- Já possui solução ou fornecedor, entre outras (percentual não informado).

## Caso de uso: copiloto em tempo real na call

O terceiro caso mostra um software construído com Claude e integração à API do JEV, usado como copiloto durante uma call de vendas. Enquanto o lead fala, o JEV classifica cada frase em tempo real por sinais ao vivo: se o prospect concorda, se há dor identificada, se falou de preço ou orçamento, se criou rapport, se há prazo conhecido e se existe objeção em aberto.

O sistema também atualiza em tempo real a probabilidade de fechamento, mostra o script da call e sugere perguntas e contornos de objeção. Como o JEV não escreve texto, um segundo modelo rápido (no exemplo, Qwen Flash) gera as frases sugeridas.

Os criadores do copiloto anunciaram que deixariam o código aberto, para instalação e modificação local. O endereço do repositório não está entre os links desta apostila; confira a licença antes de usar em produção.

## Teste de pronto

- [ ] Você consegue relacionar cada classificação aos dados da conexão original.
- [ ] Você identifica os casos marcados para revisão e sabe por que exigem avaliação humana.
- [ ] Se o cargo deixar dúvida sobre poder de decisão, o caso permanece para análise humana.
- [ ] Se não conseguir associar registro e resposta, peça ao Claude uma apresentação que permita comparar os registros.

## Erros comuns e cuidados

- Sua conta, base e planilha podem variar; não trate esses números como garantia de desempenho ou precisão.
- A classificação não confirma autoridade comercial. Casos ambíguos, como cargos que não deixam claro o poder de decisão, devem ir para revisão humana.
- O JEV não escreve texto. Não o use para redigir mensagens, resumir reuniões ou gerar conteúdo: use a LLM de sua escolha para isso.
- Confira os nomes dos menus na sua interface do LinkedIn, pois podem variar conforme o idioma. O caminho usado foi: Eu > Configurações e privacidade > Privacidade dos dados > Baixe seus dados, escolhendo o download maior.
- Guarde a chave de API em local privado e nunca a exiba na conversa nem em capturas de tela ou gravações.
- Os números de velocidade e custo do anúncio (20 a 200 vezes mais rápido, 40 a 400 vezes mais barato) são da promessa de lançamento; não há benchmark independente.

## Glossário

- JEV: modelo de IA da TypeSafe que só classifica (sim ou não, escolha em lista, nota de 1 a 10). Não gera texto.
- LLM: modelo de linguagem grande, que gera texto token por token.
- API: interface de programação que permite a um programa chamar um serviço por código.
- Skill: extensão do Claude Code que ensina o agente a usar um serviço externo.
- TypeSafe AI: empresa por trás do JEV.
- OpenRouter: plataforma que conecta a mais de 600 modelos de IA com uma única conta e um único saldo de créditos.
- Decisor: pessoa com poder de decisão de compra em uma empresa.
- ICP: perfil de cliente ideal, usado para pontuar o encaixe de um lead.
- Transcrição: texto gerado a partir do áudio de uma call.
- Claude Code: ferramenta de linha de comando do Claude, usada como agente.

## Plano de 7 dias

- Dia 1: crie a conta no console da TypeSafe e gere a chave de API.
- Dia 2: instale a skill no Claude Code e configure a variável TYPESAFE_API_KEY.
- Dia 3: exporte suas conexões do LinkedIn e aguarde o e-mail.
- Dia 4: baixe o arquivo e confira se contém as conexões esperadas.
- Dia 5: forneça a planilha ao Claude e peça a classificação sim, não ou revisar.
- Dia 6: confira os casos de revisão e relacione cada classificação aos dados originais.
- Dia 7: aplique o mesmo fluxo a outro caso, como mapear objeções em calls de vendas.

## Para onde ir depois

- Teste o JEV em uma tarefa volumosa que você hoje faria com o Claude ou o ChatGPT, pedindo a delegação.
- Experimente o caminho pelo OpenRouter se preferir uma única conta para vários modelos.
- Se você grava calls, use o segundo formato de classificação para mapear objeções recorrentes.
- Se você constrói software, use o exemplo do copiloto para pensar no uso do JEV em tempo real.

## Links citados

- https://docs.typesafe.ai/introduction/quickstart.md
- https://openrouter.ai/docs/guides/community/jev.md

## Além do vídeo

- O JEV não tem interface de chat: o uso é pela API.
- Pelo OpenRouter, o modelo pode ser chamado como typesafe/jev-1.14 ou pelo apelido ~typesafe/jev-latest, com uma chave de API do OpenRouter.
- Nos dois caminhos de acesso é preciso colocar créditos.
- No teste das calls, o JEV avaliou as 41 em 6 segundos, a um custo informado de 0,013, provavelmente em dólar.
- No copiloto, o custo acumulado aparece em tempo real na tela; em um momento da call de exemplo, marcava 0,0083.
