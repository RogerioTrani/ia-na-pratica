# Meituan abre pesos do LongCat-2.5 sob licença MIT

_2026-11-19 · noticia_

A Meituan publicou no Hugging Face, em 9 de novembro, os pesos do LongCat-2.5 sob licença MIT. O modelo tem visão, lê screenshots e vídeo e escreve código em várias etapas. Na API hospedada, a tarifa é por tempo limitado.

## O fato

A Meituan publicou no Hugging Face, em 9 de novembro, o checkpoint do LongCat-2.5 sob licença MIT, uma semana depois de apresentar o modelo.

O modelo inspeciona screenshots e vídeo, trabalha sobre um repositório de código e escreve ou revisa software em várias etapas.

Fonte: <https://huggingface.co/meituan-longcat/LongCat-2.5>

## Os números

- 48 bilhões de parâmetros ativos por token, de 1,6 trilhão no total.
- Terminal Bench v2.1: 88,4 contra 70,8 do LongCat-2.0.
- DeepSWE v1.1: 64,6 contra 9,7 do LongCat-2.0.
- US$ 0,30 de entrada, US$ 1,20 de saída e US$ 0,006 de entrada em cache, por milhão de tokens.

Fonte: <https://venturebeat.com/technology/meituan-releases-the-open-weights-of-its-longcat-2-5-llm-with-vision-under-a-permissive-mit-license>

## O que muda para você

A licença MIT libera uso comercial, modificação e redistribuição, respeitando as exigências de aviso da licença.

No Terminal Bench v2.1, o LongCat-2.5 (88,4) fica a menos de um ponto do GPT-5.6 Sol (88,8) e do Claude Opus 5 (89,1). No Terminal Bench v4.0, marca 38,5 contra 53,9 do Opus 5.

Em screenshot e em correção de bug, o texto recomenda medir o resultado e o tempo de revisão, não só a nota.

## O que fazer hoje

1. Crie uma conta na plataforma de API da LongCat e abra a página API Keys. Resultado: você tem acesso à área de chaves.
2. Crie a chave e guarde o valor, que aparece uma só vez. Resultado: a chave fica pronta para uso.
3. Use o nome do modelo LongCat-2.5 no seu cliente. Resultado: o modelo responde às chamadas.
4. Para baixar o checkpoint, rode o comando de download. Resultado: os 208 arquivos, de 3,56 TB, são baixados.

```
hf download meituan-longcat/LongCat-2.5
```

Fonte: <https://longcat.chat/platform/docs/pricing/longcat-2.5>

## O que conferir

A tarifa é por tempo limitado e não há data de término divulgada. Os benchmarks rivais foram rodados com configurações diferentes, então o confronto direto não é limpo.

Os metadados do Hugging Face mostram 1,8T, enquanto a descrição técnica da Meituan fala em 1,6T. Para dimensionar a implantação, use os arquivos reais.

O guia oficial de serviço é para NPU, e o texto não traz comando oficial para GPU. Em outra infraestrutura, valide se o runtime preserva a visão e o uso de ferramentas.

Fonte: <https://huggingface.co/meituan-longcat/LongCat-2.5/tree/main>
