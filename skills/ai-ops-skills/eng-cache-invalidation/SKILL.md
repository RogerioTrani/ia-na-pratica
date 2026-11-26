---
name: eng-cache-invalidation
description: "Decide o que guardar em cache, por quanto tempo e como invalidar sem servir dado antigo perigoso. Use quando leituras repetidas estiverem lentas ou caras."
---

# Estratégia de cache e invalidação

Decide o que guardar em cache, por quanto tempo e como invalidar sem servir dado antigo perigoso. Use quando leituras repetidas estiverem lentas ou caras.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Leituras frequentes e seu custo atual
- Com que frequência cada dado muda e quanto atraso é aceitável
- Camadas de cache disponíveis
- Dados específicos de usuário ou cliente

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Selecione candidatos pela medição de uso e descarte os que exigem valor sempre atual, como saldos e permissões.
2. Monte chaves que incluam usuário, cliente, idioma e versão sempre que a resposta variar por eles.
3. Defina o tempo de vida e os eventos de escrita que apagam ou atualizam cada chave.
4. Descreva o comportamento quando o cache falha ou expira sob muita demanda, evitando que todos recalculem juntos.
5. Meça taxa de acerto, latência e ocorrências de dado desatualizado.

## O que entregar

Estratégia de cache por dado, com exemplos de chaves, expiração, invalidação e plano de contingência.

## Conferência antes de entregar

- [ ] Nenhuma chave permite que um usuário receba dados de outro.
- [ ] Toda escrita relevante tem invalidação correspondente.
- [ ] O sistema continua correto com o cache desligado.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
