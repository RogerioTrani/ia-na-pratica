# Coco Robotics é o primeiro cliente do mapa do Pokémon GO

_2026-11-24 · filme_

Fotos feitas por jogadores em tarefas do Pokémon GO viraram a base de um mapa usado por robôs de entrega da Coco Robotics. Esta apostila explica como o mapeamento foi coletado, como o Large Geospatial Model transforma imagens em referência espacial e por que a câmera pode ser mais precisa que o GPS entre prédios altos. Você também vai entender os números do projeto, a linha do tempo, a licença concedida sobre as imagens e as críticas éticas sobre o uso posterior desse acervo. Ao final, terá critérios para avaliar alegações de localização e para conferir termos, condições e fontes antes de confiar em uma tecnologia semelhante.

## O contexto

Em 2016, o Pokémon GO alcançou 500 milhões de downloads em 60 dias. O número mostra a velocidade de adoção do jogo nesse período. Ele não representa a quantidade de fotos coletadas nem o total de jogadores ativos.

Quem ativava o escaneamento levava uma câmera andando pela cidade. O jogo combinava o ambiente visto pela tela com elementos digitais. Essa combinação é chamada de realidade aumentada: a câmera mostra o mundo físico enquanto o aplicativo acrescenta informações ou objetos a essa imagem.

O mesmo tipo de cena fotografada durante o jogo passou a servir de referência para localizar robôs. A história do mapa começa como uma aventura de realidade aumentada e termina como um problema de posicionamento no mundo real. Entender essa passagem ajuda a enxergar como dados criados em uma atividade cotidiana podem ganhar outro uso anos depois.

Fonte: <https://nianticspatial.com/blog/largegeospatialmodel>

## Como nasceu o mapeamento no Pokémon GO

Em 2020 surgiram as tarefas de mapeamento. A participação era opcional. Quem escolhesse fazer a tarefa filmava um Pokéstop de vários ângulos, e a localização exata ficava gravada junto com as imagens.

Em troca, o jogador recebia recompensas dentro do jogo. O uso das imagens em robôs de entrega veio em uma etapa posterior.

As imagens se concentravam em ginásios, Pokéstops e lugares que o jogo incentivava os jogadores a visitar. Isso ajuda a explicar a cobertura do acervo: ela acompanhou os destinos dados pelo jogo. Um escaneamento também não era uma foto isolada. Vários ângulos do mesmo ponto formavam um conjunto de observações sobre a aparência do lugar.

Fonte: <https://pokemongo.com/en/post/armapping-researchtask?hl=en>

## A escala do mapa

Em 2024, a Niantic divulgou 10 milhões de locais escaneados e cerca de 1 milhão de novos escaneamentos por semana. Os números medem coisas diferentes. Locais são pontos do mundo que foram registrados; escaneamentos são capturas de imagens. A taxa semanal indica o ritmo da coleta, não a quantidade de lugares únicos nem de pessoas participantes.

O mapa reúne 30 bilhões de imagens e mais de 1 milhão de pontos. Cada ponto foi fotografado milhares de vezes, de dia, de noite, no sol e na chuva. O volume de 30 bilhões de imagens não significa 30 bilhões de lugares diferentes.

A repetição das visitas dá ao sistema diferentes vistas e condições de iluminação do mesmo ambiente. Isso é importante porque uma fachada pode parecer diferente ao longo do dia ou sob chuva. A variedade ajuda a construir uma referência visual mais ampla, embora o número de imagens, por si só, não garanta precisão em qualquer situação.

Fonte: <https://nianticspatial.com/blog/largegeospatialmodel>

## O Large Geospatial Model

Para transformar as imagens em mapa, a Niantic Spatial treinou mais de 50 milhões de redes neurais. Juntas, elas somam mais de 150 trilhões de parâmetros. Uma rede neural é um modelo computacional que aprende padrões com exemplos. Parâmetros são os valores internos ajustados durante esse aprendizado.

O projeto recebeu o nome de Large Geospatial Model. O termo geospatial se refere à relação entre lugares, posições e espaço físico. Aqui, os exemplos de treinamento são fotos do mundo real, e o objetivo é usar essas imagens para representar e localizar ambientes.

Um modelo de linguagem como o ChatGPT aprende com texto. O Large Geospatial Model aprendeu o mundo físico olhando fotos. A escala do treinamento mostra o tamanho do sistema, mas o número de redes e parâmetros não é uma medida direta de precisão. O desempenho precisa ser avaliado pela tarefa, pelo ambiente e pela forma de medição.

Fonte: <https://nianticspatial.com/blog/largegeospatialmodel>

## GPS, câmera e precisão

O GPS é um sistema de posicionamento por satélite que estima a posição de um dispositivo. Em áreas com prédios altos, os sinais podem chegar enfraquecidos ou por caminhos indiretos, o que dificulta a estimativa. O erro de cerca de 50 metros citado no caso se refere a esse cenário entre prédios altos. Ele não descreve o erro do GPS em todo lugar.

A câmera oferece outra pista: a aparência do local. O sistema da Niantic Spatial compara o que a câmera vê com as fotos dos jogadores. Em vez de depender apenas do sinal de satélite, ele procura uma correspondência visual entre a cena atual e o acervo do mapa.

A formulação oficial para o resultado é precisão de nível centimétrico. Isso indica que o erro estaria na casa dos centímetros no sistema descrito. A expressão não fixa um valor exato. A comparação útil é entre o GPS e o mapa no mesmo tipo de ambiente, mantendo as condições do teste.

Fonte: <https://www.nianticspatial.com/blog/largegeospatialmodel>

## Coco Robotics e o primeiro cliente

Em 2026, a Coco Robotics foi a primeira cliente da Niantic Spatial. A empresa opera robôs de entrega nos Estados Unidos e na Europa. O anúncio liga esses robôs ao mapa espacial para enfrentar um problema conhecido de navegação: a posição imprecisa do GPS.

Nessa aplicação, a câmera do robô compara o que vê com as fotos dos jogadores. O mapa funciona como uma referência visual do ambiente. Para a Coco Robotics, o interesse está em usar essa referência para localizar o robô com mais precisão.

Para quem acompanha IA, a mudança está na origem dos dados. Imagens coletadas durante um jogo passaram a apoiar uma operação comercial de robótica. O primeiro cliente confirma uma aplicação do mapa em entrega, mas não demonstra, sozinho, efeitos sobre o tempo ou o custo das entregas.

Fonte: <https://nianticspatial.com/blog/coco-robotics>

## A licença das imagens e a crítica ética

Os termos descritos no caso dão à Niantic uma licença mundial, perpétua e gratuita sobre as imagens. Em linguagem simples, essa permissão vale em qualquer país, não tem prazo de expiração e não exige pagamento por seu uso.

Não houve pagamento em dinheiro pelos escaneamentos. A contrapartida recebida pelos jogadores foram recompensas dentro do jogo. A licença autoriza o uso das imagens; ela não transforma a recompensa do jogo em uma participação financeira nos resultados do projeto.

Um professor de ética da Universidade de Delft diz que os jogadores contribuíram sem saber. A crítica gira em torno da distância entre a atividade feita no jogo e o uso posterior das imagens. O escaneamento era opcional e trazia uma recompensa imediata. A discussão ética trata do quanto os participantes compreenderam o destino da contribuição.

## O mapa depois da venda dos jogos

Em 2025, a Niantic vendeu a divisão de jogos por 3,5 bilhões de dólares. O Pokémon GO deixou a empresa, e o mapa continuou com a Niantic Spatial. A separação muda o contexto da história: o jogo que ajudou a coletar imagens e a empresa que passou a explorar o acervo não são mais a mesma operação.

Esse valor se refere à divisão de jogos. Ele não é o valor atribuído ao mapa, nem a receita da Niantic Spatial. Por isso, o número da venda não serve para estimar o tamanho financeiro do projeto espacial.

A mudança de propriedade ajuda a explicar a trajetória do mapa. O acervo começou dentro de uma experiência de jogo e depois passou a ser apresentado como infraestrutura para localização de máquinas. A linha do tempo da apostila mantém esses dois momentos separados para evitar atribuir ao jogo um uso comercial que veio depois.

## A parceria com software usado em drones militares

Em dezembro de 2025, a Niantic Spatial fechou uma parceria com uma empresa cujo software é usado em drones militares. O anúncio dessa parceria ampliou a discussão sobre o destino dos dados espaciais para além da entrega de robôs.

A empresa afirma que os dados do Pokémon GO não fazem parte do acordo. Também afirma que só escaneou imagens de quem ativou o recurso. Essas declarações devem ser apresentadas como a versão da empresa, sem transformar a existência da parceria em prova de que imagens do jogo foram incluídas.

Para avaliar o caso, é preciso separar três elementos: a parceria, os dados usados nela e a licença sobre as imagens. A licença ampla explica a permissão de uso descrita nos termos. Ela não mostra, por si só, como cada imagem foi usada em cada produto ou acordo.

## Como funciona na prática

Imagine que um robô de entrega precisa saber sua posição em um trecho entre prédios altos. O GPS oferece uma estimativa que pode errar cerca de 50 metros nesse cenário. Essa distância é grande para um robô que precisa interpretar o espaço ao redor.

A câmera do robô captura a cena do local. O sistema compara essa cena com as fotos dos jogadores e procura a correspondência no mapa. A referência visual permite chegar à precisão de nível centimétrico descrita pela Niantic Spatial. O resultado esperado é uma posição mais exata que a fornecida apenas pelo GPS nesse tipo de ambiente.

O CEO resumiu o caso: fazer o Pikachu correr de forma realista e fazer o robô andar na calçada são o mesmo problema. Os dois exigem entender como o mundo físico aparece para uma câmera. O jogo usou essa ideia para criar uma experiência digital; o robô usa a mesma ideia para se localizar.

Fonte: <https://nianticspatial.com/blog/coco-robotics>

## Linha do tempo

A sequência mostra a passagem do jogo para o mapa e do mapa para uma aplicação comercial. Cada data marca uma etapa diferente dessa transformação.

- 2016: o Pokémon GO alcança 500 milhões de downloads em 60 dias, mostrando a adoção rápida do jogo.
- 2020: começam as tarefas opcionais de mapeamento, com filmagens de vários ângulos, localização exata e recompensas no jogo.
- 2024: a Niantic divulga 10 milhões de locais escaneados e cerca de 1 milhão de novos escaneamentos por semana.
- Dezembro de 2025: a Niantic Spatial anuncia uma parceria com uma empresa cujo software é usado em drones militares.
- 2026: a Coco Robotics se torna a primeira cliente e passa a usar o mapa em robôs de entrega nos Estados Unidos e na Europa.

## Quem ganha e quem perde

A Niantic Spatial ganhou um uso comercial anunciado para o mapa. A Coco Robotics ganhou uma referência visual para enfrentar a imprecisão do GPS. Os jogadores receberam recompensas dentro do jogo quando participaram das tarefas de mapeamento.

O lado desfavorável para os jogadores aparece na combinação de uma licença ampla com a ausência de pagamento em dinheiro pelas imagens. A recompensa no jogo é concreta, mas ela não equivale a uma remuneração pelo uso posterior do acervo.

A avaliação sobre quem ganha e quem perde depende do ponto de vista. Para a operação dos robôs, a localização mais precisa tem valor prático. Para os jogadores, a questão ética é outra: a atividade tinha uma finalidade visível no jogo, enquanto o aproveitamento das imagens como infraestrutura espacial aconteceu depois.

## O que ainda não se sabe

Os números e anúncios permitem explicar o projeto, mas cada alegação precisa manter seu recorte. Estes são os pontos que exigem cuidado antes de formar uma conclusão.

- A Niantic Spatial descreve a precisão como de nível centimétrico. Essa formulação não fixa um valor exato.
- O erro de cerca de 50 metros do GPS foi descrito entre prédios altos. Ele não pode ser tratado como média universal nem aplicado automaticamente a qualquer rua.
- Mais de 50 milhões de redes neurais e mais de 150 trilhões de parâmetros mostram a escala do treinamento. Eles não comprovam, sozinhos, precisão ou desempenho em todos os ambientes.
- As imagens se concentraram em ginásios, Pokéstops e lugares incentivados pelo jogo. A cobertura de um ponto não permite presumir cobertura equivalente em toda a cidade.
- A empresa diz que os dados do Pokémon GO não fazem parte da parceria militar. Essa informação precisa ser atribuída à empresa e mantida separada da existência da parceria.
- O uso pela Coco Robotics confirma uma aplicação em robôs de entrega. Os números apresentados não permitem concluir efeitos sobre o tempo ou o custo das entregas.
- A licença mundial, perpétua e gratuita está descrita no caso. A crítica ética citada afirma que os jogadores contribuíram sem saber, o que deve ser preservado como avaliação crítica, não como fato jurídico.

Fonte: <https://nianticspatial.com/blog/largegeospatialmodel>

## O que muda para você

Se você participou das tarefas do Pokémon GO, suas imagens podem ter entrado em um acervo usado depois para localização espacial. Se não participou, o caso ainda serve para entender como uma contribuição feita em um aplicativo pode ganhar um uso diferente daquele visto no momento da coleta.

Para qualquer aplicativo que peça fotos, localização ou gravações, a leitura dos termos muda a forma de decidir. O ponto não é apenas saber qual recompensa aparece na tela. Também importa entender que licença será concedida, onde ela vale e por quanto tempo.

Para quem trabalha com IA, o projeto mostra o valor de dados do mundo real e a importância do contexto de coleta. Uma imagem não carrega sozinha toda a informação necessária para ensinar um sistema. O local, os ângulos, as condições e a finalidade da captura fazem parte do que o modelo consegue aprender.

## O que você pode fazer

Você pode aplicar o mesmo raciocínio ao avaliar jogos, aplicativos de mapeamento e sistemas de localização. Cada ação abaixo tem um resultado verificável.

1. Nos termos de uso do jogo ou do aplicativo, localize a licença sobre fotos e localização antes de ativar o envio de imagens. O resultado esperado é identificar quem recebe a permissão, onde ela vale, se é gratuita e quanto tempo dura.
2. Ao ler uma página ou anúncio sobre localização, anote o cenário, a unidade e o método de medição. O resultado esperado é distinguir o erro aproximado do GPS entre prédios altos da precisão de nível centimétrico atribuída ao mapa.
3. Na descrição técnica do sistema, identifique a fonte da posição: satélite, câmera ou combinação dos dois. O resultado esperado é entender qual informação sustenta a estimativa de localização.
4. No site oficial da Niantic Spatial, leia o anúncio do Large Geospatial Model e o texto sobre a Coco Robotics. O resultado esperado é conferir a escala do modelo, a formulação da precisão e o recorte do primeiro cliente.
5. Em uma explicação própria, reconstrua o exemplo do robô sem consultar a apostila. O resultado esperado é conseguir relacionar fotos de referência, comparação visual e posição no mundo real.

Fonte: <https://nianticspatial.com/>

## Glossário

- GPS: sistema de posicionamento por satélite que estima a posição de um dispositivo.
- Realidade aumentada: combinação de elementos digitais com o ambiente físico visto pela câmera.
- Pokéstop: ponto do jogo que podia ser filmado nas tarefas de mapeamento.
- Escaneamento: captura de imagens de um lugar, com localização, para construir uma referência espacial.
- Mapa espacial: representação de lugares e da aparência do mundo usada para localizar algo.
- Rede neural: modelo computacional que aprende padrões a partir de exemplos.
- Parâmetro: valor interno ajustado durante o treinamento de uma rede neural.
- Large Geospatial Model: nome do modelo da Niantic Spatial treinado com fotos para representar o mundo físico.
- Precisão de nível centimétrico: formulação que indica erro na casa dos centímetros no sistema descrito, sem fixar um valor exato.
- Licença mundial, perpétua e gratuita: permissão de uso sem fronteiras, sem prazo de expiração e sem pagamento por essa permissão.

## Para onde ir depois

O próximo passo é revisar os anúncios oficiais e separar os números de escala das alegações de desempenho. O Large Geospatial Model explica o treinamento e a precisão; o texto sobre a Coco Robotics mostra a aplicação em robôs de entrega; o anúncio das tarefas do Pokémon GO ajuda a entender a coleta do ponto de vista do jogador.

Pratique explicar o caso em uma conversa curta. Comece pela tarefa de mapeamento, passe pela formação do acervo e termine na comparação entre a câmera e o GPS. Depois, repita a explicação incluindo a licença das imagens e a crítica ética.

- Leia o anúncio oficial do Large Geospatial Model e destaque o que cada número mede.
- Consulte o anúncio oficial das tarefas de mapeamento do Pokémon GO para entender a participação opcional e as recompensas no jogo.
- Leia o anúncio da Niantic Spatial sobre a Coco Robotics para ligar o mapa ao problema de localização dos robôs.
- Antes de contribuir com imagens em outro aplicativo, revise a licença e compare a recompensa oferecida com o uso que os termos permitem.

Fonte: <https://nianticspatial.com/>

## Links citados

- https://www.nianticspatial.com/blog/coco-robotics
- https://www.technologyreview.com/2026/03/10/1134099/how-pokemon-go-is-helping-robots-deliver-pizza-on-time/
