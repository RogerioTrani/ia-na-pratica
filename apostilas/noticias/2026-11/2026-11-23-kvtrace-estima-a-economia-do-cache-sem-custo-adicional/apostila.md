# KVTrace estima a economia do cache sem custo adicional

_2026-11-23 · noticia_

O cache distribuído de KV com Amazon ElastiCache pode cortar o custo de inferência em até 40% e o tempo até o primeiro token em até 80%. A skill de cache distribuído de KV, do Agent Toolkit for AWS, testa o seu tráfego com o KVTrace antes de qualquer gasto. Se a economia estimada não cobrir o preço do cache, ela para e nada é criado.

## O fato

Quem hospeda o próprio LLM em GPU paga para recalcular o mesmo contexto a cada turno. O cache distribuído de KV com Amazon ElastiCache pode cortar o custo de inferência em até 40% e o tempo até o primeiro token em até 80%.

A skill de cache distribuído de KV, do Agent Toolkit for AWS, testa o seu tráfego com o KVTrace antes de qualquer gasto. Se a economia estimada não cobrir o preço do cache, ela para e nada é criado. Fonte: https://aws.amazon.com/blogs/machine-learning/cut-self-hosted-llm-cost-and-latency-with-the-distributed-kv-caching-agent-skill/

Fonte: <https://aws.amazon.com/blogs/machine-learning/cut-self-hosted-llm-cost-and-latency-with-the-distributed-kv-caching-agent-skill/>

## O problema: a GPU refaz o contexto a cada turno

Com LLM hospedado em GPU própria, cada servidor tem um cache pequeno e isolado. Ele não guarda nem compartilha o histórico que agentes e chats reenviam a cada turno.

Exemplo: um assistente jurídico acumula centenas de milhares de tokens de histórico por conversa. Quando o advogado volta à conversa depois do almoço, o servidor que pega o pedido não tem nada disso na memória. A GPU recalcula os estados de atenção KV de todos os tokens (etapa chamada prefill) antes de escrever a primeira palavra, e a resposta pode levar minutos. O mesmo padrão atrasa agentes de código retomados, assistentes agênticos e assistentes de perguntas sobre documentos.

Fonte: <https://aws.amazon.com/blogs/machine-learning/cut-self-hosted-llm-cost-and-latency-with-the-distributed-kv-caching-agent-skill/>

## O que o cache distribuído entrega

O cache distribuído de KV com Amazon ElastiCache estende os caches locais das GPUs com uma camada compartilhada ao lado da sua frota. Qualquer servidor pode reaproveitar o estado KV por dias, entre sessões, mudanças de roteamento e falhas de servidor.

Os tetos citados são até 40% de redução no custo de inferência e até 80% no tempo até o primeiro token (TTFT). O resultado real varia com o modelo, o padrão de tráfego e o roteamento dos prompts. Fonte: https://aws.amazon.com/blogs/database/announcing-distributed-kv-caching-for-self-hosted-llms-with-amazon-elasticache/

Fonte: <https://aws.amazon.com/blogs/database/announcing-distributed-kv-caching-for-self-hosted-llms-with-amazon-elasticache/>

## Etapa 1: o agente lê a sua frota de GPUs

A skill funciona com Kiro, Claude Code, OpenAI Codex e outros agentes de código que suportam Agent Skills. Antes de gastar qualquer coisa, o agente faz uma checagem de encaixe. Se algo não encaixar, ele para e explica. Repositório do Agent Toolkit: https://github.com/aws/agent-toolkit-for-aws

1. uma chamada somente leitura, describe-instances, lista as instâncias. Resultado: o agente vê a frota.
2. o agente conta as interfaces Elastic Fabric Adapter (EFA). Resultado: fica claro se a rede comporta o cache.
3. ele só pergunta o que não consegue ver: engine, modelo, tamanho de tensor-parallel (TP), tipo de dado do KV, preço do servidor e com que frequência os prompts se repetem. Resultado: a estimativa usa só o que você informou.

Fonte: <https://github.com/aws/agent-toolkit-for-aws>

## Etapas 2 e 3: estimativa com o KVTrace

O KVTrace grava os eventos de cache do vLLM ou do SGLang e os reproduz offline contra caches compartilhados de vários tamanhos. A estimativa sai do seu tráfego real, antes de existir qualquer infraestrutura, e o uso não tem custo adicional. Repositório: https://github.com/aws-samples/amazon-elasticache-samples/tree/main/kvtrace

A gravação acontece em cada servidor de GPU, durante uma janela representativa, como um dia útil completo. O registro guarda hashes de blocos e contagem de tokens. Ele nunca grava IDs de tokens nem texto de prompt. Os hashes vêm do conteúdo dos tokens. Com prompts sensíveis, use a opção de anonimização da ferramenta, com o comando abaixo.

Em prompts curtos, ler o cache pode demorar mais que recalcular. Acima de certo tamanho de prompt (o ponto de virada), a leitura ganha. Esse ponto e a repetição dos prompts decidem se o cache compensa o preço.

```
--anonymize-key-file
```

Fonte: <https://github.com/aws-samples/amazon-elasticache-samples/tree/main/kvtrace>

## A regra e a montagem do cache

Se a economia estimada não paga o custo do cache, nada é criado. Tempo de GPU liberado só vira dinheiro se você rodar menos servidores ou atender mais tráfego nos mesmos. A skill pede aprovação explícita antes de criar, alterar ou apagar recursos. Fonte: https://aws.amazon.com/blogs/machine-learning/cut-self-hosted-llm-cost-and-latency-with-the-distributed-kv-caching-agent-skill/

Depois da sua confirmação, o agente cria o grupo de segurança com permissões de EFA e um cluster Valkey 9.1 com grupo de parâmetros próprio. Ele prepara os servidores de GPU e sobe um servidor LMCache por servidor de GPU. Em seguida, testa o cluster com um objeto pequeno e confirma que prompts repetidos carregam o KV do cache por RDMA.

- Agente de código com suporte a Agent Skills, como Kiro ou Claude Code.
- Instâncias de GPU com suporte a EFA RDMA write, como p5.
- LMCache 0.5.8rc1 ou superior e vLLM 0.11.1 ou superior (SGLang 0.5.13 ou superior).
- ElastiCache for Valkey 9.1 ou superior, em nós cache.i8ge.48xlarge (se for montar o cache).

Fonte: <https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/distributed-kv-caching-getting-started.html>

## Se a transferência falhar

Sintoma: o servidor LMCache conecta ao cluster ElastiCache e BLOB.RDMA_HELLO funciona, mas as transferências de dados falham e rdma_write_errors sobe em INFO largeobj. A causa provável é um grupo de segurança que bloqueia o tráfego EFA entre os próprios membros. O agente segue o guia de diagnóstico da skill e entrega os comandos para checar e corrigir a regra. Fonte: https://aws.amazon.com/blogs/machine-learning/cut-self-hosted-llm-cost-and-latency-with-the-distributed-kv-caching-agent-skill/

```
INFO largeobj
```

Fonte: <https://aws.amazon.com/blogs/machine-learning/cut-self-hosted-llm-cost-and-latency-with-the-distributed-kv-caching-agent-skill/>

## O que conferir

Antes de pensar em cache compartilhado, a skill checa correções sem infraestrutura nova: se o prefix caching estiver desligado, religá-lo acelera turnos seguidos. Se a taxa de acerto do cache de prefixo da GPU já passa de 90% com afinidade de sessão, talvez o cache compartilhado não seja necessário.

Isolamento entre clientes: um cache compartilhado pode deixar um cliente descobrir, pelo tempo de resposta, se outro enviou o mesmo texto. Casos que exigem isolamento ganham caches separados.

Antes do tráfego de produção, o agente esvazia as camadas locais e confere se duas execuções carregadas do cache dão a mesma saída. Documentação oficial: https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/distributed-kv-caching-getting-started.html

Fonte: <https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/distributed-kv-caching-getting-started.html>
