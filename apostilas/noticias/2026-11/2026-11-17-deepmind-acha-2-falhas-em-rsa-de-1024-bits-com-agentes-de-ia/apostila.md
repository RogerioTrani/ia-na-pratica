# DeepMind acha 2 falhas em RSA de 1024 bits com agentes de IA

_2026-11-17 · noticia_

O Google DeepMind usou agentes de IA, com supervisão humana, para testar sistemas legados de criptografia RSA de 1024 bits. Os pesquisadores encontraram duas fraquezas: uma em assinaturas digitais e outra na fatoração de várias chaves em lote. Os ganhos de eficiência são estimativas teóricas dos autores. Protocolos modernos com chaves de 2048 bits ou mais seguem seguros.

## O fato

Em 6 de novembro de 2026, o Google DeepMind divulgou uma pesquisa com dois artigos técnicos. Um trata de assinaturas digitais e o outro de fatoração de chaves.

Agentes de IA, acompanhados por pessoas, mostraram que sistemas legados baseados em RSA de 1024 bits podem ser comprometidos com um orçamento computacional menor do que se supunha. Fonte: https://www.linkedin.com/pulse/advancing-frontier-cryptanalysis-pushmeet-kohli-5itie

Fonte: <https://www.linkedin.com/pulse/advancing-frontier-cryptanalysis-pushmeet-kohli-5itie>

## Falha 1: preenchimento não protege se o atacante controla metade

Assinaturas digitais confirmam que um update, documento ou site é autêntico e vem de quem diz vir. Antes de assinar, muitos padrões completam a mensagem com dados predefinidos (o padding) até formar um bloco de tamanho fixo.

A pesquisa mostra que o que importa é quanto do bloco assinado o atacante controla. Quando ele controla cerca de metade ou mais, o padding não oferece proteção nenhuma contra forja.

Quando o atacante controla menos do bloco, como no caso de um resumo de 32 bytes, forjar é mais difícil. Mesmo assim, o novo algoritmo melhora o melhor método anterior em cerca de 1.600 vezes para chaves de 1024 bits. Esse número é uma estimativa teórica dos autores e não foi executado na prática.

Para testar a primeira parte, os agentes reproduziram o resultado em simulação, numa chave de 1024 bits de referência já resolvida anteriormente. Usaram 3,5 vezes menos tempo de CPU: 391 anos-núcleo em 3,2 dias.

Fonte: <https://storage.googleapis.com/deepmind-media/papers/Faster_Affine_Root_and_a_1024bit%20Computation.pdf>

## Falha 2: quebrar muitas chaves em lote sai mais barato

Quem tenta quebrar muitas chaves do mesmo tamanho divide um grande custo inicial entre todas elas. Chaves RSA costumam seguir tamanhos padrão, como 1024 ou 2048 bits, então esse cenário é realista para o método.

Depois de uma pré-computação inicial equivalente a uma fatoração completa, o novo algoritmo reduz em cerca de 30 vezes o custo médio teórico de cada chave adicional de 1024 bits. O método ainda não foi implementado na prática.

Fonte: <https://storage.googleapis.com/deepmind-media/papers/Fan_Factories_Multiple_Number_Fields_in_Factorization_Factories_and_Batch_NFS.pdf>

## Os números

Todos os ganhos abaixo são estimativas ou resultados de simulação, não ataques executados em sistemas reais.

- Assinaturas: cerca de 1.600 vezes sobre o melhor método anterior, para chaves de 1024 bits (estimativa).
- Assinaturas: 3,5 vezes menos tempo de CPU, 391 anos-núcleo em 3,2 dias.
- Fatoração em lote: cerca de 30 vezes menos custo médio teórico por chave adicional de 1024 bits.
- Padding: resumo de 32 bytes.

Fonte: <https://storage.googleapis.com/deepmind-media/papers/Faster_Affine_Root_and_a_1024bit%20Computation.pdf>

## O que fazer hoje

Se você ainda mantém chaves antigas, dois comandos mostram o tamanho delas. Documentação do openssl x509: https://docs.openssl.org/3.1/man1/openssl-x509/. Manual do ssh-keygen: https://man7.org/linux/man-pages/man1/ssh-keygen.1.html

1. certificado TLS: rode o comando de leitura de certificado (openssl x509) apontando para o seu arquivo de certificado. Resultado: a linha Public-Key mostra o tamanho da chave.
2. chave SSH: rode o comando de tamanho de chave (ssh-keygen) apontando para a sua chave pública. Resultado: você vê o tamanho da chave SSH.

Fonte: <https://docs.openssl.org/3.1/man1/openssl-x509/>

## O recado da pesquisa

Avanços desse tipo levavam anos ou décadas, e quem defende sistemas assumia que as margens de segurança mudavam devagar. Agentes de IA testam esses limites bem mais rápido, o que torna o teste proativo da força criptográfica mais importante.

A dificuldade matemática que sustenta a segurança digital não pode ser tratada como suposição fixa.

Fonte: <https://www.linkedin.com/pulse/advancing-frontier-cryptanalysis-pushmeet-kohli-5itie>

## O que conferir

Fato: na prática, os resultados afetam apenas sistemas legados com chaves RSA de 1024 bits. Protocolos modernos com chaves de 2048 bits ou mais seguem seguros depois dessa pesquisa.

Os dois ganhos de eficiência são estimativas teóricas dos autores. Anúncio no X: https://x.com/pushmeet/status/2118752095859794390

Artigos: https://storage.googleapis.com/deepmind-media/papers/Faster_Affine_Root_and_a_1024bit%20Computation.pdf e https://storage.googleapis.com/deepmind-media/papers/Fan_Factories_Multiple_Number_Fields_in_Factorization_Factories_and_Batch_NFS.pdf

Fonte: <https://x.com/pushmeet/status/2118752095859794390>
