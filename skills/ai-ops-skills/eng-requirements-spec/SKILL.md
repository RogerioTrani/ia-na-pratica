---
name: eng-requirements-spec
description: "Transforma uma ideia vaga em requisitos claros, com fluxos, exceções, requisitos não funcionais e recorte de primeira versão. Use quando for preciso decidir o que construir antes de escrever código."
---

# Da ideia à especificação implementável

Transforma uma ideia vaga em requisitos claros, com fluxos, exceções, requisitos não funcionais e recorte de primeira versão. Use quando for preciso decidir o que construir antes de escrever código.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Descrição da ideia e o problema que ela resolve
- Quem vai usar e o que essas pessoas fazem hoje
- Sistema existente, stack e restrições conhecidas
- Prazo e o que define sucesso para quem pediu
- Exemplos, telas ou documentos já produzidos

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Liste os perfis de usuário e, para cada um, a ação que ele quer concluir, com os dados que entram e saem.
2. Descreva o fluxo principal passo a passo e depois os desvios: dado inválido, falta de permissão, serviço fora do ar e ação repetida.
3. Registre os requisitos não funcionais que mudam o projeto, como volume esperado, tempo de resposta, segurança e privacidade, perguntando o que não souber.
4. Separe a primeira versão das evoluções, justificando cada corte pelo valor e pelo esforço.
5. Escreva critérios de aceite no formato situação, ação e resultado esperado, e liste as perguntas em aberto.

## O que entregar

Documento de especificação com fluxos, exceções, requisitos, escopo da primeira versão, critérios de aceite e dúvidas pendentes.

## Conferência antes de entregar

- [ ] Todo requisito do escopo inicial tem ao menos um critério de aceite.
- [ ] Suposições aparecem marcadas como suposições, sem se passar por fato confirmado.
- [ ] O que ficou para depois está listado, para ninguém presumir que está incluído.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
