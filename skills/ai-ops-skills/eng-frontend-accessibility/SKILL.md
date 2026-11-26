---
name: eng-frontend-accessibility
description: "Revisa e corrige semântica, teclado, foco, rótulos e estados dinâmicos da interface. Use quando telas ou componentes precisarem funcionar com teclado e leitor de tela."
---

# Acessibilidade no frontend

Revisa e corrige semântica, teclado, foco, rótulos e estados dinâmicos da interface. Use quando telas ou componentes precisarem funcionar com teclado e leitor de tela.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Telas ou componentes a revisar
- Código da interface e biblioteca de componentes
- Nível de conformidade exigido, se houver
- Navegadores e tecnologias assistivas disponíveis para teste

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Troque elementos genéricos por elementos semânticos nativos, recorrendo a ARIA só quando não houver equivalente.
2. Percorra cada fluxo apenas pelo teclado, conferindo ordem, foco visível, ausência de armadilhas e retorno do foco ao fechar janelas.
3. Verifique nomes acessíveis de campos, botões e imagens, ligação das mensagens de erro e contraste.
4. Teste carregamento, erro, menu aberto e conteúdo atualizado, garantindo que a mudança seja anunciada.
5. Registre cada barreira com impacto, correção e forma manual de confirmar.

## O que entregar

Plano de correção priorizado, trechos ajustados e checklist técnico de verificação manual.

## Conferência antes de entregar

- [ ] Os fluxos principais se completam sem mouse.
- [ ] Está claro o que foi testado com leitor de tela e o que ficou pendente.
- [ ] Verificação automática não é apresentada como prova de conformidade completa.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
