# JEV e Claude classificam 17.020 leads em 40 segundos

_2026-11-24 · tutorial_

Esta apostila mostra como usar o JEV, o modelo da TypeSafe que só classifica, junto com o Claude Code para separar suas conexões do LinkedIn em sim, não e revisar. Você vai criar a chave de API, instalar a skill, exportar as conexões e pedir a classificação. No vídeo, 17.020 conexões foram classificadas em menos de 40 segundos, um relato da demonstração que pode variar na sua conta.

## O que você terá no fim

Ao final, você terá as conexões do seu LinkedIn classificadas pelo JEV, com a resposta sim, não ou revisar para cada lead, e os casos de revisão separados para análise humana. O JEV é um modelo de IA que não escreve texto. Ele só responde com classificações, e por isso é pequeno, rápido e barato. Ele trabalha em três formatos: sim ou não, escolha de uma lista que você fornece, e nota de 1 a 10. Fonte: https://docs.typesafe.ai/introduction/quickstart

Antes de começar: Claude Code instalado; conta no console da TypeSafe (console.typesafe.ai); créditos para usar a API; conta no LinkedIn com conexões (linkedin.com); e navegador com acesso à internet. O tempo de 40 segundos é o relato da demonstração e pode variar na sua conta ou planilha.

Fonte: <https://docs.typesafe.ai/introduction/quickstart>

## Passo a passo

Siga os passos na ordem. Os endereços e caminhos ficam em seções próprias.

1. abra o console e crie a chave. O JEV não tem chat. Abra o console da TypeSafe, gere uma chave de API na página de chaves e guarde o valor em local privado. Resultado esperado: a chave de API está gerada e guardada.
2. instale a skill no Claude Code. No terminal, rode os dois comandos do bloco de instalação. O primeiro adiciona o repositório de skills da TypeSafe e o segundo instala o plugin. Guarde a chave na variável de ambiente TYPESAFE_API_KEY. Resultado esperado: o Claude tem uma skill para usar o JEV pela API. O repositório é github.com/typesafe-ai/skills.
3. exporte suas conexões do LinkedIn. Siga o caminho do LinkedIn, escolha o download maior e solicite o arquivo. O e-mail com o link chega em até 24 horas, e o link fica disponível por 72 horas. Resultado esperado: o arquivo de conexões traz nome, URL do perfil, e-mail, empresa, cargo e data de cada conexão.
4. peça a classificação. No Claude, forneça a planilha de conexões e peça à skill do JEV que responda, para cada lead, se ele é decisor, com as respostas sim, não ou revisar. Resultado esperado: a classificação das conexões volta no formato sim, não e revisar.
5. confira os casos para revisão. Compare os dados de algumas conexões com a classificação recebida e examine os registros marcados para revisar. Resultado esperado: você consegue ligar cada contato à resposta e avaliar se os dados sustentam a decisão.

Fonte: <https://docs.typesafe.ai/agent-skill.md#installation>

## Chave de API no console

Abra o console da TypeSafe e gere a chave na página de chaves. Não mostre o valor na conversa nem em gravações. Console: console.typesafe.ai. Fonte: https://docs.typesafe.ai/introduction/quickstart.md

```
console.typesafe.ai/keys
```

Fonte: <https://docs.typesafe.ai/introduction/quickstart.md>

## Exportar as conexões do LinkedIn

No LinkedIn, siga o caminho abaixo, escolha o download maior e solicite o arquivo. O e-mail com o link chega em até 24 horas, e o link fica disponível por 72 horas. Entre os dados baixados, localize o arquivo de conexões. Fonte: https://www.linkedin.com/help/linkedin/answer/a1339364

```
Eu > Configurações e privacidade > Privacidade dos dados > Baixe seus dados
```

Fonte: <https://www.linkedin.com/help/linkedin/answer/a1339364>

## Chamar a skill do JEV

O Claude coordena a tarefa e delega a classificação ao JEV. Se o Claude não acionar a skill sozinho, chame-a pelo comando abaixo. Fonte: https://docs.typesafe.ai/agent-skill.md

```
/typesafe:typesafe-ai
```

Fonte: <https://docs.typesafe.ai/agent-skill.md>

## Teste de pronto

Execução concluída não garante classificação útil. Você deve conseguir ligar cada contato à resposta e avaliar se os dados sustentam aquela decisão.

- [ ] Você compara os dados de algumas conexões com a classificação recebida.
- [ ] Se não conseguir associar contato e resposta, peça ao Claude uma apresentação que permita comparar os registros.
- [ ] Se o cargo deixar dúvida sobre poder de decisão, o caso fica para análise humana.

Fonte: <https://docs.typesafe.ai/agent-skill.md>

## Cuidados e outras opções

Trate a classificação como triagem, não como confirmação de autoridade comercial. O JEV também pode ser usado com uma chave do OpenRouter. Este roteiro segue o caminho direto pelo console da TypeSafe. Fonte: https://openrouter.ai/docs/guides/community/jev.md

Use o JEV para classificar respostas de leads, tickets de suporte e objeções de venda, dar notas de ICP, risco ou prioridade, rotear leads para vendedores e processar volumes grandes de texto ou planilha. Resumir reunião, escrever post, fazer conta e pesquisar continuam com o Claude, o GPT ou o Gemini.

Fonte: <https://openrouter.ai/docs/guides/community/jev.md>
