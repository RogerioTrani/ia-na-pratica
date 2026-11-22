# Qubic evolui milhões de cérebros de IA em 500 CPUs

_2026-11-21 · reportagem_

A Qubic evoluiu milhões de cérebros de IA em cerca de 500 núcleos de CPU, sem GPU e sem modelo pré-treinado, para jogar o ARC-AGI-3, o teste interativo do Prêmio ARC 2026. A melhor nota offline foi 0,38 e a última submissão no Kaggle marcou 0,41, números da própria equipe. O resultado oficial sai em 4 de dezembro de 2026. Esta apostila reúne o método, o teste, as falhas encontradas e os endereços do código e dos cérebros evoluídos.

## Evolução escolhe o desenho do cérebro

Treinar uma rede ajusta a força das conexões dentro de um desenho fixo. A busca por arquitetura neural decide o próprio desenho: quantas unidades existem e como elas se ligam.

No método da Qubic, os cérebros herdam parâmetros, sofrem mutações e os melhores se reproduzem. A escala foi de mais de 110 configurações e milhões de cérebros, em cerca de 500 núcleos de CPU, sem GPU.

## O que é o Neuraxon

O Neuraxon é uma unidade computacional inspirada no cérebro, criada por conselheiros científicos da Qubic. Cada neurônio funciona em tempo contínuo e assume um de três estados. As sinapses mudam em velocidades diferentes.

- Estados do neurônio: excitatório (+1), neutro (0) ou inibitório (-1)
- Cada sinapse tem três pesos
- Código aberto, com o núcleo em licença MIT

```
github.com/DavidVivancos/Neuraxon
```

Fonte: <https://github.com/DavidVivancos/Neuraxon>

## ARC-AGI-3: jogos sem manual

O ARC-AGI-3 foi lançado em 25 de março de 2026. O jogador vê uma grade de cores, age e precisa descobrir sozinho o que é vencer. O conjunto público tem 25 jogos.

No lançamento, humanos pontuaram 100% e a IA de ponta, 0,51%. A nota premia eficiência: quem precisa de dez vezes mais ações que uma pessoa marca 1% naquele nível.

Fonte: <https://arcprize.org/competitions/2026>

## A pontuação e como lê-la

Os números abaixo são da equipe da Qubic. O resultado oficial da avaliação privada no Kaggle sai em 4 de dezembro de 2026.

As melhores entradas usam modelos de linguagem de 27 a 31 bilhões de parâmetros. Os cérebros Neuraxon começam sem conhecimento pré-treinado, então o 0,41 mede só o que a evolução consegue sozinha.

- Melhor nota offline: 0,38
- Última submissão no Kaggle: 0,41

## O que deu errado: a maldição do vencedor

Um grupo de cérebros venceu um jogo em todas as sementes usadas na seleção e falhou nas sementes novas. É o aluno que decorou a prova do ano passado.

Os sucessos também se concentraram no primeiro nível.

## Próximo passo: Neuraxon 3.0

O Neuraxon 3.0 vai selecionar cérebros pela velocidade com que aprendem jogos inéditos, com protocolo fixado antes da coleta de dados.

O núcleo do código tem licença MIT no GitHub. Os cérebros evoluídos estão no Hugging Face, em 82,7 GB de arquivos Parquet.

```
huggingface.co/datasets/DavidVivancos/Nxon2ArcAGI3Brains
```

Fonte: <https://huggingface.co/datasets/DavidVivancos/Nxon2ArcAGI3Brains>

## Prazos

As submissões do Prêmio ARC 2026 fecharam em 2 de novembro. A ARC Prize Foundation anuncia os resultados em 4 de dezembro, e então dá para ver onde o 0,41 fica no ranking.

Fonte: <https://arcprize.org/competitions/2026>

## Além do vídeo

- O protocolo evolutivo tem três fases: evolução para um jogo específico, exame curto com milhares de cérebros em algumas sementes e exame longo com os melhores cérebros nos 25 jogos públicos, em sementes nunca usadas na seleção.
- O Prêmio ARC 2026 oferece US$ 2 milhões em prêmios em três categorias. No Kaggle a avaliação roda sem internet, sistemas baseados em API como GPT ou Claude são barrados e os principais participantes devem liberar o código das soluções.
- Os neurônios do Neuraxon contam com quatro neuromoduladores simulados (dopamina, serotonina, acetilcolina e noradrenalina), células semelhantes a astrócitos que regulam a plasticidade e quatro loops homeostáticos.
- Em jogos simples, uma política fixa com alguma exploração pode passar um nível sem entender as regras. Uma nota alta, sozinha, não prova que o cérebro aprendeu durante o jogo.
- O conjunto de dados dos cérebros evoluídos tem 603.054 linhas.
