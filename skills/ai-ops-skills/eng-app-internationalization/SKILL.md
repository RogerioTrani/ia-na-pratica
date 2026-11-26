---
name: eng-app-internationalization
description: "Prepara o sistema para vários idiomas e formatos regionais de texto, plural, moeda, números e datas. Use quando o produto for atender outro idioma ou país."
---

# Internacionalização da interface

Prepara o sistema para vários idiomas e formatos regionais de texto, plural, moeda, números e datas. Use quando o produto for atender outro idioma ou país.

## Antes de começar

Reúna, a partir do pedido e do arquivo de instruções do projeto (se houver):

- Idiomas e regiões previstos
- Framework da interface e biblioteca de tradução, se houver
- Origem dos textos, incluindo servidor e e-mails
- Quem traduz e revisa

Se faltar algo decisivo, pergunte só o necessário. Se der para avançar, marque a lacuna e siga sem inventar dado.

## Passo a passo

1. Localize textos fixos e mova-os para arquivos de idioma com chaves que descrevam o contexto.
2. Use frases completas com variáveis nomeadas, sem montar sentenças por concatenação.
3. Formate plural, números, moedas, datas e fusos por recursos que respeitem a região.
4. Defina escolha do idioma, idioma de reserva e aviso para chave ausente.
5. Teste textos mais longos, acentos e, quando previsto, escrita da direita para a esquerda.

## O que entregar

Plano de internacionalização, estrutura de arquivos e exemplos convertidos.

## Conferência antes de entregar

- [ ] Não restam textos visíveis fixos nas telas do escopo.
- [ ] Mudar o idioma não converte valor monetário por engano.
- [ ] Traduções não revisadas estão marcadas.

## Limites

Só diga que publicou, enviou, testou ou alterou algo se isso aconteceu. Peça aprovação antes de ação externa, com custo ou que não dê para desfazer.
