# GPT-6 Astra edita pesos do Qwen 0.8B e melhora de 8% para 48% indicadores

_2026-11-21 · noticia_

Pesquisadores do MIT deixaram o GPT-6 Astra editar os pesos do modelo pequeno Qwen3.5-0.8B. Sem treinar nada, a edição alterou só 0,016% dos pesos e levou a nota em matemática de 7,9% para 48,1%. O modelo sabia resolver as questões, mas ficava preso repetindo o próprio raciocínio, e a edição destravou isso. Esta apostila reúne os números e os links oficiais do estudo, dos pesos editados e dos modelos.

## O que os pesquisadores fizeram

Pesquisadores do MIT deixaram o GPT-6 Astra editar o Qwen3.5-0.8B, um modelo pequeno. A edição foi feita direto nos pesos, sem treino e sem dados novos.

O estudo completo está publicado pelo MIT CSAIL e traz o método. Os pesos editados também estão disponíveis no Hugging Face.

Fonte: <https://rikiyat.github.io/blog/weight-space-programming/>

## Os números

- Pesos alterados: 0,016% do modelo.
- Nota em matemática antes da edição: 7,9%.
- Nota em matemática depois da edição: 48,1%.
- Resultado: cerca de seis vezes mais acertos, sem treinar nada.

Fonte: <https://rikiyat.github.io/blog/weight-space-programming/>

## Por que funcionou

O modelo não sofria de falta de conhecimento. Ele sabia resolver as questões, mas vivia repetindo o próprio raciocínio e não chegava à resposta.

A edição destravou esse ciclo de repetição. Com menos de dois centésimos de por cento dos parâmetros alterados, a nota subiu de 7,9% para 48,1%.

Fonte: <https://rikiyat.github.io/blog/weight-space-programming/>

## Quem fez a edição

A mudança nos pesos do Qwen foi feita pelo GPT-6 Astra, da OpenAI. Ou seja, um modelo de IA alterou o outro.

A página oficial do GPT-6 Astra está em openai.com/index/gpt-6-astra.

Fonte: <https://openai.com/index/gpt-6-astra/>

## Links oficiais

- Estudo completo (MIT CSAIL): https://rikiyat.github.io/blog/weight-space-programming/
- Pesos editados do estudo (Hugging Face): https://huggingface.co/RikiyaT/Qwen3.5-0.8B-weight-space-programming
- Qwen3.5-0.8B original (Hugging Face): https://huggingface.co/Qwen/Qwen3.5-0.8B
- GPT-6 Astra (OpenAI): https://openai.com/index/gpt-6-astra/

## Além do vídeo

- Uma deputada americana pediu para pausar as IAs mais avançadas. Quem é contra diz que, se os Estados Unidos pararem, a China passa na frente.
- A OpenAI lançou o GPT 6.2 Astra.
- A OpenAI tem um modelo que quase ninguém pode usar, o GPT6 Cyber. Segundo a empresa, ele achou 81 falhas graves no Firefox que ninguém tinha visto.
- Claude Code no terminal: os subagentes em segundo plano agora gastam bem menos do limite, e cada atualização de status ficou cerca de 99% mais barata. Vale atualizar.
