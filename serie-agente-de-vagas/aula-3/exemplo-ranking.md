# Exemplo de ranking do Prumo

> **Exemplo fictício**, para mostrar o formato. Empresas, links e notas são inventados. O seu ranking sai das vagas reais que o Faro encontrou.

**Ranking de vagas para:** front-end júnior, híbrido, São Paulo

## 1. Desenvolvedor(a) Front-end Júnior, Empresa A: 88/100

- **Link:** https://exemplo.invalid/vaga-a
- **Pontos fortes:** pede HTML, CSS, JavaScript e React, e a pessoa tem os quatro. Nível júnior e modelo híbrido em São Paulo, exatamente o que ela declarou.
- **Lacunas:** pede noções de testes automatizados, que a pessoa não listou.
- **Por que entrou:** combina em habilidades, nível, modelo de trabalho e cidade. A única lacuna é desejável, não obrigatória.

## 2. Desenvolvedor(a) Web Júnior, Empresa B: 79/100

- **Link:** https://exemplo.invalid/vaga-b
- **Pontos fortes:** HTML, CSS e JavaScript batem; nível júnior; localização em São Paulo.
- **Lacunas:** pede Node.js como obrigatório, que a pessoa ainda não tem.
- **Por que entrou:** a aderência técnica é boa, mas o Node.js obrigatório tira pontos. O modelo de trabalho não foi informado pela vaga.

## 3. Desenvolvedor(a) Front-end Pleno, Empresa C: 61/100

- **Link:** https://exemplo.invalid/vaga-c
- **Pontos fortes:** React e JavaScript batem; vaga remota.
- **Lacunas:** pede três anos de experiência, acima do nível declarado, e TypeScript.
- **Por que entrou:** as habilidades são parecidas, mas o nível pedido pesa contra. Serve como vaga de médio prazo.

## 4. Analista de Interface, Empresa D: 47/100

- **Link:** https://exemplo.invalid/vaga-d
- **Pontos fortes:** CSS e HTML.
- **Lacunas:** presencial fora de São Paulo e foco em design de produto.
- **Por que entrou:** aparece no fim por completude; o modelo de trabalho e a localidade derrubaram a nota.

## Vaga sem nota completa

A vaga da Empresa E teve a extração falha e ficou fora do ranking, com o aviso de que faltaram dados. O Prumo não chuta.

## Teste de sensibilidade

Se o perfil trocar "híbrido" por "remoto", a vaga 3 deve subir e a vaga 4 deve cair mais. Se o ranking não reagir, o plano não está pesando direito o modelo de trabalho: ajuste o plano e rode de novo.
