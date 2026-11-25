# Qubic evolui milhões de cérebros de IA em 500 CPUs

_2026-11-21 · reportagem_

A Qubic evoluiu milhões de cérebros de IA em cerca de 500 núcleos de CPU, sem GPU e sem modelo pré-treinado, para jogar o ARC-AGI-3. A melhor nota offline foi 0,38 e a última submissão no Kaggle marcou 0,41, números da própria equipe. O resultado oficial sai em 4 de dezembro de 2026.

## O contexto

A Qubic evoluiu milhões de cérebros de IA em cerca de 500 núcleos de CPU, sem GPU e sem modelo pré-treinado, para jogar o ARC-AGI-3, o teste interativo do Prêmio ARC 2026. A melhor nota offline foi 0,38 e a última submissão no Kaggle marcou 0,41, números da própria equipe.

O resultado oficial sai em 4 de dezembro de 2026. Fonte: https://arcprize.org/competitions/2026

Fonte: <https://arcprize.org/competitions/2026>

## Linha do tempo

Os prazos citados na reportagem, em ordem.

- 25 de março de 2026: o ARC-AGI-3 foi lançado.
- 2 de novembro: fecharam as submissões do Prêmio ARC 2026.
- 4 de dezembro de 2026: a ARC Prize Foundation anuncia os resultados, e então dá para ver onde o 0,41 fica no ranking.

Fonte: <https://arcprize.org/competitions/2026>

## Evolução escolhe o desenho do cérebro

Treinar uma rede ajusta a força das conexões dentro de um desenho fixo. A busca por arquitetura neural decide o próprio desenho: quantas unidades existem e como elas se ligam.

No método da Qubic, os cérebros herdam parâmetros, sofrem mutações e os melhores se reproduzem. A escala foi de mais de 110 configurações e milhões de cérebros, em cerca de 500 núcleos de CPU, sem GPU.

Fonte: <https://github.com/DavidVivancos/Neuraxon>

## O que é o Neuraxon

O Neuraxon é uma unidade computacional inspirada no cérebro, criada por conselheiros científicos da Qubic. Cada neurônio funciona em tempo contínuo e assume um de três estados. As sinapses mudam em velocidades diferentes.

- Estados do neurônio: excitatório (+1), neutro (0) ou inibitório (-1).
- Cada sinapse tem três pesos.
- Código aberto, com o núcleo em licença MIT.

```
github.com/DavidVivancos/Neuraxon
```

Fonte: <https://github.com/DavidVivancos/Neuraxon>

## ARC-AGI-3: jogos sem manual

O ARC-AGI-3 foi lançado em 25 de março de 2026. O jogador vê uma grade de cores, age e precisa descobrir sozinho o que é vencer. O conjunto público tem 25 jogos.

No lançamento, humanos pontuaram 100% e a IA de ponta, 0,51%. A nota premia eficiência: quem precisa de dez vezes mais ações que uma pessoa marca 1% naquele nível. Fonte: https://arcprize.org/competitions/2026

Fonte: <https://arcprize.org/competitions/2026>

## A pontuação e como lê-la

Os números abaixo são da equipe da Qubic. O resultado oficial da avaliação privada no Kaggle sai em 4 de dezembro de 2026.

As melhores entradas usam modelos de linguagem de 27 a 31 bilhões de parâmetros. Os cérebros Neuraxon começam sem conhecimento pré-treinado, então o 0,41 mede só o que a evolução consegue sozinha. Uma nota alta, sozinha, não prova que o cérebro aprendeu durante o jogo.

- Melhor nota offline: 0,38.
- Última submissão no Kaggle: 0,41.

Fonte: <https://arcprize.org/competitions/2026>

## O que deu errado: a maldição do vencedor

Um grupo de cérebros venceu um jogo em todas as sementes usadas na seleção e falhou nas sementes novas. É o aluno que decorou a prova do ano passado.

Os sucessos também se concentraram no primeiro nível.

Fonte: <https://github.com/DavidVivancos/Neuraxon>

## Próximo passo: Neuraxon 3.0

O Neuraxon 3.0 vai selecionar cérebros pela velocidade com que aprendem jogos inéditos, com protocolo fixado antes da coleta de dados.

O núcleo do código tem licença MIT no GitHub. Os cérebros evoluídos estão no Hugging Face, em 82,7 GB de arquivos Parquet. Fonte: https://huggingface.co/datasets/DavidVivancos/Nxon2ArcAGI3Brains

```
huggingface.co/datasets/DavidVivancos/Nxon2ArcAGI3Brains
```

Fonte: <https://huggingface.co/datasets/DavidVivancos/Nxon2ArcAGI3Brains>
