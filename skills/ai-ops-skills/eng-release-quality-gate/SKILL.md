---
name: eng-release-quality-gate
description: "Confere testes, mudanças, migrações, telemetria e reversão para decidir se a versão pode sair. Use quando for preciso um parecer de liberação com bloqueadores claros."
---

# Verificação final de qualidade da versão

Confere testes, mudanças, migrações, telemetria e reversão para decidir se a versão pode sair. Use quando for preciso um parecer de liberação com bloqueadores claros.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Lista de mudanças e critérios de aceite
- Resultados de testes e defeitos abertos
- Migrações e configurações da versão
- Responsáveis por aprovar e reverter

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Relacione cada mudança à evidência de que foi testada e destaque as que não têm.
2. Examine defeitos abertos e classifique-os em bloqueadores ou riscos aceitáveis com dono.
3. Verifique se as migrações foram ensaiadas e se há métricas e alertas para o que mudou.
4. Confirme com nome quem decide e quem executa a reversão.
5. Emita parecer de liberar, liberar com ressalvas ou segurar, justificando.

## O que entregar

Relatório de prontidão com parecer, bloqueadores, pendências e responsáveis.

## Conferência antes de entregar

- [ ] Nenhum teste é dado como aprovado sem registro de execução.
- [ ] Todo bloqueador tem condição objetiva de resolução.
- [ ] A decisão final de publicar fica com o responsável humano.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
