# Firefox for iOS 160.0 ganha aviso de segurança em 9/11/2026

_2026-11-19 · noticia_

A Mozilla publicou dois avisos que precisam ser lidos separadamente: o MFSA 2026-124, de 9 de novembro de 2026, corrige três falhas no Firefox for iOS 160.0; o MFSA 2026-125, de 10 de novembro, corrige 99 falhas no Firefox 160. Ao ler esta apostila, você vai entender os impactos, identificar o produto e a versão de cada aviso e atualizar o Firefox no iPhone até a versão 160.0 ou superior. Também vai aprender a consultar o índice oficial e o repositório de avisos sem misturar dados de plataformas diferentes.

## O fato

Em 9 de novembro de 2026, a Mozilla publicou o MFSA 2026-124, com correções de segurança para o Firefox for iOS 160.0. O aviso corrige três vulnerabilidades: duas de impacto alto e uma de impacto moderado. As duas falhas de impacto alto permitiam escalonamento de privilégios, e uma delas está no Reader View, o modo de leitura do navegador.

No dia seguinte, 10 de novembro de 2026, a Mozilla publicou o MFSA 2026-125 para o Firefox 160. Esse registro corrige 99 vulnerabilidades e tem impacto geral alto. A mesma rodada trouxe avisos próprios para Firefox ESR e Thunderbird.

Os dois avisos principais têm números, datas, produtos e versões diferentes. O MFSA 2026-124 trata do Firefox no iPhone. O MFSA 2026-125 trata do Firefox 160. Manter essa separação é o primeiro passo para interpretar corretamente a notícia.

Fonte: <https://www.mozilla.org/en-US/security/advisories/mfsa2026-124/>

## Por que isso importa

A segurança do navegador também depende do celular. O Firefox for iOS abre páginas, executa conteúdo web e acessa recursos do iPhone. Uma falha nesse contexto pode afetar a forma como o aplicativo lida com dados, permissões ou funções de leitura.

Uma correção de segurança altera o código do aplicativo para eliminar uma vulnerabilidade. Quando a versão corrigida fica disponível na App Store, a atualização instala esse código no aparelho. Por isso, a informação prática deste anúncio termina em uma ação: atualizar o Firefox no iPhone.

A quantidade de falhas e o nível de impacto respondem a perguntas diferentes. O total mostra quantas vulnerabilidades foram corrigidas naquele registro. O impacto descreve a gravidade e as condições associadas a cada falha. Um aviso com muitas correções não informa, por si só, quantos aparelhos sofreram ataques.

Fonte: <https://www.mozilla.org/en-US/security/advisories/>

## Como funciona um aviso MFSA

MFSA significa Mozilla Foundation Security Advisory, um aviso de segurança da Mozilla Foundation. Cada registro tem um número próprio e reúne as vulnerabilidades corrigidas em um produto e em uma versão específica. O número do MFSA identifica o aviso; ele não é o número da versão do aplicativo.

A Mozilla mantém um índice com as publicações e um repositório oficial dos avisos. O repositório foundation-security-advisories é a fonte canônica desses registros. Segundo a documentação do repositório, os avisos são escritos e atribuídos conforme o processo de ciclo de vida de bugs de segurança da Mozilla.

Cada vulnerabilidade também pode ter um identificador CVE. O CVE permite localizar um caso específico, enquanto o MFSA mostra o conjunto de correções de um produto e versão. O repositório oficial informa que os dados são publicados automaticamente em serviços CVE e recomenda obter dados de avisos desses serviços.

Fonte: <https://github.com/mozilla/foundation-security-advisories>

## Firefox for iOS 160.0: as três correções

O MFSA 2026-124 é específico do Firefox for iOS 160.0. Ele corrige duas vulnerabilidades de impacto alto e uma de impacto moderado. As duas de impacto alto são casos de escalonamento de privilégios: uma no Reader View e outra no Firefox para iOS.

Os identificadores CVE permitem acompanhar cada falha separadamente. Eles ajudam a distinguir os registros dentro do mesmo aviso e evitam que uma vulnerabilidade seja descrita com as características de outra. A classificação de impacto acompanha cada caso.

- CVE-2026-121842: escalonamento de privilégios no Reader View, classificado como impacto alto.
- CVE-2026-121843: escalonamento de privilégios no Firefox para iOS, classificado como impacto alto.
- CVE-2026-121841: vulnerabilidade corrigida no Firefox for iOS 160.0, classificada como impacto moderado.

Fonte: <https://www.mozilla.org/en-US/security/advisories/mfsa2026-124/>

## Impacto alto e escalonamento de privilégios

Escalonamento de privilégios ocorre quando uma falha permite obter permissões além daquelas previstas para aquele contexto. Em um navegador, o assunto importa porque o aplicativo trabalha com páginas, dados do usuário e recursos do sistema. A correção busca fechar o caminho que permitiria esse aumento de acesso.

A menção ao Reader View situa uma das falhas no modo de leitura. Esse recurso apresenta o conteúdo de uma página de uma forma própria. A indicação de que a falha estava nesse modo ajuda a entender que o escopo do aviso inclui uma função específica do Firefox, além do aplicativo como um todo.

Na chave de impacto publicada pela Mozilla, o nível alto descreve vulnerabilidades que podem coletar dados sensíveis de sites em outras janelas ou injetar dados ou código nesses sites, exigindo no máximo ações normais de navegação. No caso do iOS, os dois registros altos são identificados como escalonamento de privilégios.

O total de três correções é um inventário do que foi resolvido na versão 160.0. Ele não mede a frequência de tentativas de ataque nem a quantidade de usuários afetados.

Fonte: <https://www.mozilla.org/en-US/security/advisories/mfsa2026-124/>

## A rodada do Firefox 160

Em 10 de novembro de 2026, o MFSA 2026-125 corrigiu 99 vulnerabilidades no Firefox 160. A distribuição é de 57 falhas de impacto alto, 24 moderadas e 18 baixas. A soma das três categorias resulta nas 99 correções do aviso.

O conjunto abrange os identificadores de CVE-2026-124852 a CVE-2026-124951, exceto CVE-2026-124916. Essa faixa com exceção corresponde ao conjunto de 99 vulnerabilidades indicado no registro.

A data coloca o aviso do Firefox 160 um dia depois do aviso do Firefox for iOS 160.0. A proximidade das publicações não une os dois produtos: cada MFSA conserva seu próprio escopo, versão e lista de correções.

Fonte: <https://www.mozilla.org/en-US/security/advisories/mfsa2026-125/>

## Quais tipos de falha o Firefox 160 corrigiu

As correções do Firefox 160 incluem escape de sandbox, escalonamento de privilégios, contorno da política de mesma origem, vazamento de informações, spoofing e falhas críticas de memória. Os módulos citados incluem DOM, WebGL, WebRender, WebGPU, JavaScript JIT/GC, Áudio/Vídeo e Rede.

Algumas categorias tratam de barreiras de isolamento. O sandbox restringe o que um componente pode fazer. A política de mesma origem separa conteúdos de origens diferentes. Um escape de sandbox ou um contorno dessa política pode romper uma dessas barreiras.

Outras categorias envolvem confidencialidade e confiança. O vazamento de informações expõe dados que deveriam permanecer protegidos. O spoofing cria uma falsificação que pode enganar o usuário sobre identidade, origem ou interface.

As falhas de memória formam outro grupo. Use-after-free, ponteiros inválidos e limites incorretos descrevem acessos problemáticos a áreas de memória. A lista ampla mostra a variedade de componentes corrigidos, mas cada vulnerabilidade mantém seu próprio impacto e suas condições.

Fonte: <https://www.mozilla.org/en-US/security/advisories/mfsa2026-125/>

## Firefox ESR e Thunderbird na mesma rodada

A publicação de 10 de novembro de 2026 também trouxe avisos para Firefox ESR e Thunderbird. Esses produtos têm registros próprios. O número do aviso e a versão indicada no título são os elementos que ligam cada correção ao produto correspondente.

Quem consulta o índice precisa prestar atenção nos nomes semelhantes. Firefox 160 e Thunderbird 160, por exemplo, aparecem em registros diferentes. Firefox ESR 153.7 e Firefox ESR 115.45 também têm avisos separados.

- MFSA 2026-127: Security Vulnerabilities fixed in Firefox ESR 153.7.
- MFSA 2026-126: Security Vulnerabilities fixed in Firefox ESR 115.45.
- MFSA 2026-129: Security Vulnerabilities fixed in Thunderbird 153.7.
- MFSA 2026-128: Security Vulnerabilities fixed in Thunderbird 160.

Fonte: <https://www.mozilla.org/en-US/security/advisories/>

## Os números

Os números abaixo descrevem correções agrupadas por produto, versão e nível de impacto. Eles organizam o anúncio e ajudam a comparar os registros sem transferir dados de um para o outro.

- 3 vulnerabilidades: total corrigido no Firefox for iOS 160.0 pelo MFSA 2026-124.
- 2 de impacto alto: no iOS, as duas permitiam escalonamento de privilégios, sendo uma no Reader View e outra no Firefox para iOS.
- 1 de impacto moderado: terceira correção do aviso do iOS, identificada como CVE-2026-121841.
- 99 vulnerabilidades: total corrigido no Firefox 160 pelo MFSA 2026-125.
- 57 altas, 24 moderadas e 18 baixas: distribuição das 99 correções do Firefox 160; a soma das categorias é 57 + 24 + 18 = 99.
- CVE-2026-124852 a CVE-2026-124951, exceto 124916: faixa de identificadores do conjunto corrigido no Firefox 160.
- 160.0 ou superior: versão que os passos oficiais indicam instalar no Firefox for iOS.

Fonte: <https://www.mozilla.org/en-US/security/advisories/>

## O que muda para você

Se você usa o Firefox no iPhone, o aviso do iOS leva a uma ação direta: abrir a App Store e atualizar o aplicativo até a versão 160.0 ou superior. A atualização instala as correções incluídas no MFSA 2026-124.

Exemplo: imagine que você usa o modo de leitura no iPhone e encontra um aviso que menciona escalonamento de privilégios nesse recurso. A informação útil é ligar o aviso ao produto correto, reconhecer a versão corrigida e seguir o caminho de atualização pela App Store. O número de falhas ajuda a dimensionar o conjunto corrigido, mas não substitui essa verificação.

Se o assunto for o Firefox 160, o registro a consultar é o MFSA 2026-125. Ele informa as categorias de falha e os módulos corrigidos naquela versão. Os dados do Firefox 160 não devem ser usados como instrução de atualização para o iPhone.

Fonte: <https://support.mozilla.org/pt-BR/products/ios/installation-and-updates>

## O que fazer hoje

O suporte da Mozilla descreve o caminho de atualização do Firefox no iOS pela App Store. Os passos abaixo mantêm a sequência oficial e indicam o resultado esperado em cada etapa.

1. Abra a App Store no iPhone. O resultado esperado é chegar à loja de aplicativos do sistema.
2. Toque em Buscar e pesquise por "Firefox". Como alternativa, toque no ícone do seu perfil no canto superior direito para abrir as atualizações pendentes. O resultado esperado é localizar o Firefox e a opção de atualização.
3. Toque no botão "Atualizar" ao lado do Firefox para instalar a versão 160.0 ou superior. O resultado esperado é concluir a instalação da versão indicada.

```
App Store > Buscar "Firefox" > Atualizar (160.0 ou superior)
```

Fonte: <https://support.mozilla.org/pt-BR/products/ios/installation-and-updates>

## O que conferir

Antes de seguir uma instrução de atualização ou interpretar um número do aviso, confira o recorte. Produtos com nomes parecidos podem ter versões, datas e listas de vulnerabilidades diferentes.

- Produto e versão: o MFSA 2026-124 se refere ao Firefox for iOS 160.0; o MFSA 2026-125 se refere ao Firefox 160.
- Número do aviso: 2026-124 identifica as três correções do iOS; 2026-125 identifica as 99 correções do Firefox 160.
- Data de publicação: o aviso do iOS é de 9 de novembro de 2026; o aviso do Firefox 160 é de 10 de novembro de 2026.
- Nível de impacto: não transfira as contagens de altas, moderadas ou baixas de um produto para o outro.
- Fonte oficial: use os avisos no domínio mozilla.org e o repositório foundation-security-advisories para localizar os registros.
- Identificador CVE: use o código da vulnerabilidade para distinguir um caso específico dentro do aviso.
- Ação no iPhone: siga o caminho pela App Store e confirme se a versão instalada é 160.0 ou superior.

Fonte: <https://www.mozilla.org/en-US/security/advisories/>

## Glossário

- App Store: loja de aplicativos do iPhone usada nos passos oficiais para atualizar o Firefox.
- CVE: identificador público de uma vulnerabilidade específica.
- Critical: vulnerabilidade que permite executar código do atacante e instalar software, sem interação além da navegação normal.
- DOM: estrutura que representa os elementos de um documento web para o navegador.
- ESR: versão de suporte estendido do Firefox.
- Firefox for iOS: versão do Firefox para iPhone, tratada neste anúncio na versão 160.0.
- GC: coleta de lixo, processo que gerencia a liberação de memória no JavaScript.
- High: vulnerabilidade que pode coletar dados sensíveis de sites em outras janelas ou injetar dados ou código neles, exigindo no máximo ações normais de navegação.
- JIT: compilação just-in-time, que transforma código em instruções executadas durante o uso do programa.
- Low: vulnerabilidades menores, como negação de serviço, pequenos vazamentos de dados ou falsificações; falsificações de indicadores de SSL indetectáveis são tratadas como alto impacto.
- MFSA: Mozilla Foundation Security Advisory, aviso de segurança da Mozilla Foundation.
- Moderate: vulnerabilidade que seria alta ou crítica, mas só funciona em configurações incomuns ou não padrão, ou exige passos complexos ou pouco prováveis.
- Reader View: modo de leitura que apresenta o conteúdo de uma página de uma forma própria.
- Sandbox: ambiente restrito que limita o que um componente pode acessar ou executar.
- Same-origin policy: regra que separa conteúdos de origens web diferentes.
- Escalonamento de privilégios: obtenção de permissões além daquelas previstas para um contexto.
- Spoofing: falsificação usada para enganar o usuário sobre identidade, origem ou interface.
- Use-after-free: uso de uma área de memória depois de ela ter sido liberada.
- Ponteiros inválidos: referências de memória que não apontam para uma área válida.
- Limites incorretos: acessos que ultrapassam os limites de uma área de memória.
- WebGL, WebRender e WebGPU: tecnologias de gráficos citadas entre os módulos afetados pelas correções do Firefox 160.

Fonte: <https://www.mozilla.org/en-US/security/advisories/>

## Para onde ir depois

- Atualize o Firefox no iPhone pela App Store até a versão 160.0 ou superior.
- Consulte o MFSA 2026-124 para revisar as três vulnerabilidades do Firefox for iOS e seus identificadores CVE.
- Consulte o MFSA 2026-125 quando o assunto for o Firefox 160, mantendo esse aviso separado do iOS.
- Acompanhe o índice oficial de avisos para localizar publicações por data, produto e versão.
- Para dados de consultoria sobre vulnerabilidades, use serviços CVE, conforme a recomendação do repositório oficial dos avisos.
- Pratique a leitura de um aviso: separe produto, versão, data, quantidade de correções e nível de impacto antes de definir a próxima ação.

Fonte: <https://www.mozilla.org/en-US/security/advisories/>

## Outros avisos no índice

- Em 26 de outubro de 2026, o MFSA 2026-117 registrou correções no Firefox for iOS 156.1.
- Em 21 de outubro de 2026, o MFSA 2026-116 registrou correções no Firefox for Android 158.0.2.
- Em 27 de outubro de 2026, o MFSA 2026-122 registrou correções no Thunderbird 153.6.
- Em 27 de outubro de 2026, o MFSA 2026-121 registrou correções no Thunderbird 159.
- Em 3 de novembro de 2026, o MFSA 2026-123 registrou correções no Firefox 159.0.1.
- Em 9 de junho de 2026, o MFSA 2026-55 registrou uma correção no Focus for iOS / Klar 151.3.1.
- O índice oficial reúne publicações de 2015 a 2026 e inclui produtos como Firefox for Android, Firefox Focus, Klar e Mozilla VPN.
