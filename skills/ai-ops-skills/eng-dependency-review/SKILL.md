---
name: eng-dependency-review
description: "Levanta bibliotecas desatualizadas ou vulneráveis e planeja atualizações com testes e reversão. Use quando as dependências estiverem antigas ou surgir um alerta de segurança."
---

# Revisão de dependências

Levanta bibliotecas desatualizadas ou vulneráveis e planeja atualizações com testes e reversão. Use quando as dependências estiverem antigas ou surgir um alerta de segurança.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Arquivos de dependências e de travamento de versões
- Versão da linguagem e da plataforma
- Alertas de vulnerabilidade e notas de versão acessíveis
- Cobertura de testes do projeto

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Liste dependências diretas e relevantes indiretas, com versão atual e onde são usadas.
2. Consulte fontes oficiais para versões, fim de suporte e falhas, marcando o que não puder confirmar.
3. Aponte mudanças incompatíveis que atingem o uso real do código e dependências que podem ser removidas.
4. Agrupe atualizações em lotes pequenos, começando por segurança e baixo risco e isolando as versões principais.
5. Defina os testes de cada lote e como restaurar o arquivo de travamento anterior.

## O que entregar

Plano de atualização por lotes, com riscos, testes e reversão.

## Conferência antes de entregar

- [ ] Nenhuma versão ou vulnerabilidade foi citada de memória sem aviso.
- [ ] Pacotes novos têm origem e nome conferidos.
- [ ] Instalações e alterações aguardam aprovação quando afetam o ambiente.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
