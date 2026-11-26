---
name: design-responsive-layouts
description: "Define como uma interface se reorganiza do celular ao monitor largo, componente por componente. Use quando um layout quebrar em telas pequenas ou antes de implementar uma tela que precise funcionar em vários tamanhos."
---

# Adaptação a diferentes telas

Define como uma interface se reorganiza do celular ao monitor largo, componente por componente. Use quando um layout quebrar em telas pequenas ou antes de implementar uma tela que precise funcionar em vários tamanhos.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Telas ou wireframes atuais.
- Dispositivos e larguras mais usados pelo público, se houver dados.
- Tarefa principal de cada tela.
- Framework de estilo e pontos de quebra já existentes no projeto.

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Classifique o conteúdo em essencial, secundário e dispensável conforme a tarefa de cada tela.
2. Estabeleça pontos de quebra onde o conteúdo deixa de caber bem, reaproveitando os do projeto quando existirem.
3. Descreva em cada faixa a ordem de leitura, o número de colunas, a navegação e o tamanho das áreas de toque.
4. Escolha para tabelas uma estratégia explícita (rolagem contida, colunas prioritárias ou cartões) e ajuste formulários quanto a empilhamento, teclado adequado e posição dos botões.
5. Simule extremos como largura mínima, texto ampliado, palavras longas, orientação horizontal e listas vazias.

## O que entregar

Regras de adaptação por componente e por faixa de largura, com os casos extremos tratados.

## Conferência antes de entregar

- [ ] A página não ganha rolagem horizontal na menor largura prevista.
- [ ] Nenhuma função essencial desaparece no celular.
- [ ] Fica claro o que foi testado em tela e o que é apenas especificação.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
