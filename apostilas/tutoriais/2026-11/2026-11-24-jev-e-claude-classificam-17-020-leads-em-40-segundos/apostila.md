# JEV e Claude classificam 17.020 leads em 40 segundos

_2026-11-24 · tutorial_

Esta apostila mostra como usar o JEV, o modelo da TypeSafe que só classifica, junto com o Claude Code para separar suas conexões do LinkedIn em sim, não e revisar. Você vai criar a chave de API, instalar a skill, exportar as conexões e pedir a classificação. No vídeo, 17.020 conexões foram classificadas em menos de 40 segundos. O tempo é o relato da demonstração e pode variar na sua conta ou planilha.

## O que o JEV faz

O JEV é um modelo de IA que não escreve texto. Ele só responde com classificações, e por isso é pequeno, rápido e barato. A promessa de lançamento é de 20 a 200 vezes mais velocidade e de 40 a 400 vezes menos custo que os modelos padrão.

Ele trabalha em três formatos: responder sim ou não a uma pergunta, escolher uma opção dentro de uma lista que você fornece, e dar uma nota de 1 a 10. Resumir reunião, escrever post, fazer conta e pesquisar continuam com o Claude, o GPT ou o Gemini. O melhor fluxo usa os dois, cada um no que faz melhor.

Use o JEV para classificar respostas de leads, tickets de suporte e objeções de venda, dar notas de ICP, risco ou prioridade, rotear leads para vendedores e processar volumes grandes de texto ou planilha.

## O que você precisa

- Claude Code instalado
- Conta no console da TypeSafe (console.typesafe.ai)
- Créditos para usar a API
- Conta no LinkedIn com conexões (linkedin.com)
- Navegador com acesso à internet

Fonte: <https://docs.typesafe.ai/introduction/quickstart>

## Passo 1: abra o console e crie a chave

O JEV não tem chat. Ele só funciona pela API, e o Claude usa a sua chave para chamá-lo. Abra o console da TypeSafe, empresa do JEV. O painel de gerenciamento da API deve abrir.

Na página de chaves, gere uma chave de API. Guarde o valor em local privado e não o mostre na conversa nem em gravações.

- Console: console.typesafe.ai
- Chaves: console.typesafe.ai/keys

```
console.typesafe.ai/keys
```

Fonte: <https://docs.typesafe.ai/introduction/quickstart.md>

## Passo 2: instale a skill no Claude Code

No terminal, rode os dois comandos abaixo. O primeiro adiciona o repositório de skills da TypeSafe e o segundo instala o plugin. Depois, guarde a chave de API na variável de ambiente TYPESAFE_API_KEY para a skill usá-la.

Ao terminar, o Claude passa a ter uma skill para usar o JEV pela API. Se ela não aparecer, revise o retorno dos comandos antes de enviar a planilha. O repositório é github.com/typesafe-ai/skills.

Fonte: <https://docs.typesafe.ai/agent-skill.md#installation>

## Passo 3: exporte suas conexões do LinkedIn

No LinkedIn, siga o caminho abaixo, escolha o download maior e solicite o arquivo. O e-mail com o link chega em até 24 horas, e o link fica disponível por 72 horas.

Entre os dados baixados, localize o arquivo de conexões. Ele traz nome, URL do perfil, e-mail, empresa, cargo e data de cada conexão.

```
Eu > Configurações e privacidade > Privacidade dos dados > Baixe seus dados
```

Fonte: <https://www.linkedin.com/help/linkedin/answer/a1339364>

## Passo 4: peça a classificação

No Claude, forneça a planilha de conexões e peça à skill do JEV que responda, para cada lead, se ele é decisor, com as respostas sim, não ou revisar. O Claude coordena a tarefa e delega a classificação ao JEV.

Se o Claude não acionar a skill sozinho, chame-a pelo comando abaixo. Ao final, a classificação das conexões volta no formato sim, não e revisar.

```
/typesafe:typesafe-ai
```

Fonte: <https://docs.typesafe.ai/agent-skill.md>

## Passo 5: confira os casos para revisão

Execução concluída não garante classificação útil. Compare os dados de algumas conexões com a classificação recebida e examine os registros marcados para revisar. Você deve conseguir ligar cada contato à resposta e avaliar se os dados sustentam aquela decisão.

- Se não conseguir associar contato e resposta, peça ao Claude uma apresentação que permita comparar os registros.
- Se o cargo deixar dúvida sobre poder de decisão, mantenha o caso para análise humana.
- Trate a classificação como triagem, não como confirmação de autoridade comercial.

## Alternativa pelo OpenRouter

O JEV também pode ser usado com uma chave do OpenRouter. Este roteiro segue o caminho direto pelo console da TypeSafe.

Fonte: <https://openrouter.ai/docs/guides/community/jev.md>

## Além do vídeo

- O JEV pode servir a software que precisa de resposta imediata, como sugerir perguntas durante uma call de vendas ou analisar o sentimento do lead em tempo real.
- Outro uso apresentado é classificar transcrições de vendas para listar as objeções que mais aparecem, escolhendo numa lista como preço, timing, falar com sócio ou nenhuma objeção.
- A nota de 1 a 10 também serve para estimar o risco de cancelamento de um cliente a partir dos dados de uso do software.
