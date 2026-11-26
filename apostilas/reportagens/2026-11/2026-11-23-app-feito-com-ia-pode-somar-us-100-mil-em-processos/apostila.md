# App feito com IA pode somar US$ 100 mil em processos

_2026-11-23 · reportagem_

Um app feito com IA pode criar exposição jurídica antes da primeira venda quando o código não trata idade, fontes externas, rastreamento, e-mail comercial, renovação e uploads. Esta apostila reúne os seis pontos do checklist, explica o risco de cada um e apresenta as correções do prompt. Você vai saber onde agir no cadastro, nas dependências de fonte, no analytics, nos templates de e-mail, no checkout e no fluxo DMCA. Também vai aprender a ler os valores por violação, por visitante, por e-mail ou por obra sem confundir um precedente específico com uma regra geral. Ao final, use o prompt exato para auditar o projeto antes do deploy e conferir se cada proteção ficou ativa.

## Como usar esta lista

Uma diferença prática: um projeto pode funcionar em minutos e ainda assim reunir seis configurações que geram risco jurídico. São elas: cadastro sem filtro de idade, fontes carregadas de servidor externo, analytics com session replay, e-mail sem descadastro, checkout sem termos de renovação e uploads sem proteção DMCA. O problema pode aparecer antes da primeira venda.

Muitos valores citados não são percentuais do faturamento. Eles incidem por unidade de violação, e as unidades podem ser visitante, sessão, e-mail ou obra. Por isso, o crescimento do uso pode aumentar a exposição mesmo quando a receita ainda é zero. Cada valor precisa ser lido com a lei, o fato e o recorte que pertencem a ele.

Use a lista como uma auditoria do fluxo do usuário. Comece pelo ponto em que um dado é coletado, siga pelos serviços que recebem esse dado e termine nas mensagens e cobranças que o app envia. A seção do prompt reúne as seis correções para você aplicar antes do deploy.

1. Por onde começar: abra o fluxo de cadastro e confira a ordem entre o pedido de data de nascimento e o salvamento no banco; o resultado esperado é o bloqueio de menores de 13 anos antes de qualquer persistência.
2. Em seguida, examine as chamadas de rede da página e o banner de cookies; o resultado esperado é fonte local e analytics ou session replay iniciados somente após o aceite.
3. Depois, leia um e-mail comercial e a tela de assinatura como um usuário; o resultado esperado é descadastro e endereço postal no rodapé, além de valor, periodicidade e cancelamento acima do botão.
4. Feche a revisão pelos uploads: confira o agente DMCA registrado e a rota /dmca pública; o resultado esperado é um caminho visível para denúncias.

## Cadastro sem filtro de idade

Quando o cadastro não pede idade, o app não tem uma trava que impeça esse grupo de seguir. Pela COPPA (16 CFR Part 312), quem coleta dados de menores de 13 anos sem atender à proteção exigida fica sujeito a multa de até US$ 53.088 por violação.

A correção do prompt é um Age Gate: validação obrigatória de data de nascimento no fluxo de cadastro, antes de persistir qualquer dado no banco. Persistir significa salvar. A ordem importa porque o prompt determina que a verificação ocorra antes do salvamento, e não como uma etapa posterior.

Para o leitor, a mudança está na entrada do produto. O formulário deixa de apenas criar uma conta e passa a decidir se o cadastro pode continuar. O resultado esperado é o bloqueio do registro de usuários menores de 13 anos, com a data validada antes de qualquer persistência.

- Age Gate: bloqueie o registro de usuários menores de 13 anos antes de salvar qualquer dado no banco.

Fonte: <https://www.ftc.gov/business-guidance/resources/complying-coppa-frequently-asked-questions>

## Fontes carregadas de servidor externo

Quando uma fonte vem de fonts.googleapis.com ou fonts.gstatic.com, o navegador faz uma requisição a um servidor externo para buscar o arquivo. Carregar fontes direto do Google envia o IP do visitante aos servidores da empresa sem consentimento prévio.

O Art. 6º da GDPR é a referência usada para discutir a base legal do tratamento de dados. Em 20/01/2022, um tribunal de Munique (processo 3 O 17493/20) mandou um site pagar € 100 a um único visitante por isso. É um caso específico que ilustra o risco da requisição externa; o valor não funciona como um teto geral da GDPR.

A correção remove todas as chamadas para fonts.googleapis.com e fonts.gstatic.com. O carregamento passa a usar arquivos estáticos ou next/font, com a fonte servida pelo próprio projeto. Assim, o navegador deixa de consultar esses servidores do Google para obter o arquivo de fonte.

- GDPR (Art. 6º): retire as chamadas externas para fonts.googleapis.com e fonts.gstatic.com.
- Fontes locais: configure o carregamento por arquivos estáticos ou next/font; o resultado esperado é a fonte vir do próprio app.

Fonte: <https://dejure.org/dienste/vernetzung/rechtsprechung?Text=3+O+17493%2F20>

## Analytics com session replay

Analytics reúne informações sobre o uso do app. Quando inclui session replay, também registra e transmite a sessão de navegação, com cliques e interações, para servidores de terceiros. O risco aparece quando esse envio começa antes de o visitante aceitar os cookies.

Na Califórnia vale a CIPA (Cal. Penal Code § 637.2). Rastrear com terceiros sem aviso prévio pode ser tratado como interceptação ilegal. A referência é indenização de US$ 5.000 por violação, sem precisar provar prejuízo. O recorte é importante: a afirmação se refere ao rastreamento descrito e à lei californiana citada.

A correção condiciona a inicialização de qualquer script de session replay ou analytics comportamental ao consentimento explícito em um banner de cookies. O envio de gravações deve ficar bloqueado no carregamento da página. O leitor passa a controlar o momento em que um serviço externo começa a receber a sessão.

- CIPA (Cal. Penal Code § 637.2): US$ 5.000 por violação, sem precisar provar prejuízo.
- Session replay: bloqueie a inicialização e o envio de gravações até o aceite no banner de cookies.
- Ferramentas citadas no prompt: PostHog, Microsoft Clarity e Hotjar.

Fonte: <https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=PEN&sectionNum=637.2>

## PostHog: mascaramento e consentimento

O PostHog já mascara inputs por padrão com maskAllInputs: true. Essa configuração reduz a exposição do conteúdo digitado nos campos, mas não impede a gravação e a transmissão da sessão. Cliques e interações ainda podem ser enviados a terceiros.

A medida correta é manter o mascaramento ativo e bloquear o início da gravação até o consentimento. As duas medidas trabalham juntas. A máscara cobre campos de input; o bloqueio de inicialização impede que a sessão de navegação saia antes do aceite.

Na implementação, o banner de cookies deve liberar o script somente após o consentimento explícito. No PostHog, mantenha maskAllInputs: true em session_recording. O resultado esperado é que nenhuma gravação de sessão seja enviada no carregamento da página e que a sessão só comece a ser transmitida depois do aceite.

- PostHog: mantenha maskAllInputs: true em session_recording.
- Consentimento: libere qualquer script de session replay ou analytics comportamental somente após o aceite explícito no banner.
- Verificação: confirme se o envio de gravações permanece bloqueado no carregamento da página.

Fonte: <https://posthog.com/docs/session-replay/privacy>

## E-mail sem opção de descadastro

O e-mail comercial de lançamento também faz parte do produto. Para mensagens desse tipo vale o CAN-SPAM Act: cada e-mail que viole a lei pode custar até US$ 53.088.

A correção exige rodapé com link funcional de descadastro, o unsubscribe, em um clique, e endereço físico postal válido. O prompt usa a expressão placeholder obrigatório para o endereço. Na prática, o espaço precisa ser preenchido com o endereço válido antes do envio, para que o rodapé cumpra sua função. Os pedidos de saída precisam ser atendidos em até 10 dias úteis.

Revise todos os templates de e-mail comercial ou de lançamento, porque corrigir uma única mensagem deixa os outros disparos com a mesma falha.

- CAN-SPAM: inclua no rodapé de todos os templates comerciais um endereço físico postal válido.
- Descadastro: ofereça um link funcional de unsubscribe em um clique e atenda os pedidos de saída em até 10 dias úteis.

Fonte: <https://www.ftc.gov/business-guidance/resources/can-spam-act-compliance-guide-business>

## Checkout sem termos de renovação

A ARL (Cal. Bus. & Prof. Code § 17602 e § 17603) é a lei da Califórnia sobre renovação automática. O problema começa quando a assinatura não mostra as condições perto do pedido de consentimento. O usuário pode clicar no botão de pagamento sem ver valor recorrente, frequência e regra de cancelamento.

A correção do prompt é um bloco de texto claro imediatamente acima do botão de pagamento nos componentes de assinatura ou Stripe. Ele deve informar o valor recorrente, a periodicidade da renovação automática e instruções simples de cancelamento. A posição importa porque a lei exige que os termos apareçam perto do pedido de consentimento.

Sem consentimento expresso, a cobrança fica nula e pode exigir reembolso. Para o leitor, a tarefa é revisar a tela de checkout como quem vai assinar: as condições precisam estar visíveis antes do clique, e o consentimento precisa corresponder ao que foi mostrado.

- ARL (Cal. Bus. & Prof. Code § 17602 e § 17603): termos de renovação perto do pedido de consentimento.
- Checkout: coloque valor recorrente, periodicidade e instruções de cancelamento imediatamente acima do botão de pagamento.
- Consentimento expresso: confirme se a cobrança está ligada à aceitação das condições exibidas.

Fonte: <https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=BPC&sectionNum=17603>

## Uploads sem proteção DMCA

Fotos de perfil e outros uploads permitem que usuários publiquem conteúdo no app. Esse fluxo é risco quando não existe um agente DMCA registrado. Sem esse registro, o dono do app fica exposto a responder por imagens postadas por usuários.

Pela lei de direitos autorais dos EUA (17 U.S.C. § 504), a indenização é contada por obra: até US$ 150.000 em infração intencional e de US$ 750 a US$ 30.000 nos demais casos. O teto não é um valor automático para qualquer upload.

A correção tem duas partes: registrar o agente designado e criar um canal público de denúncias. O agente dá ao app um contato registrado para o fluxo DMCA, e a página /dmca oferece o caminho para reportar violações de direitos autorais. O prompt pede a página, e o registro é feito por você no U.S. Copyright Office.

- Uploads: inclua fotos de perfil e outros envios de usuários na revisão do fluxo de direitos autorais.
- DMCA: registre o agente e publique a página de denúncia descritas na próxima seção.

Fonte: <https://www.law.cornell.edu/uscode/text/17/504>

## Agente DMCA e página de denúncia

O cadastro do agente DMCA no U.S. Copyright Office tem taxa de US$ 6 e validade de 3 anos. Esses dois números descrevem o custo e a duração do registro, não uma penalidade.

O diretório oficial fica em https://www.copyright.gov/dmca-directory/. Depois do registro, o prompt pede uma rota pública /dmca com formulário e instruções de contato para denúncia de violação de direitos autorais. O link precisa aparecer no rodapé global da aplicação.

Para quem vai aplicar, o trabalho é conectar as peças: agente registrado, página pública acessível e link visível no rodapé. Uma página sem o registro ou um registro sem canal de denúncia deixa o fluxo incompleto em relação ao prompt.

- Registro: cadastre o agente designado no U.S. Copyright Office e considere a validade de 3 anos.
- Rota /dmca: crie uma página pública com formulário e instruções de contato para denúncias.
- Rodapé global: adicione o link para /dmca em toda a aplicação.

Fonte: <https://www.copyright.gov/dmca-directory/faq.html>

## Os números

Os valores desta apostila têm unidades e condições diferentes. Ler todos como uma multa única esconde o que cada número mede e pode levar a uma conta que não corresponde ao fato.

O título usa US$ 100 mil para ilustrar a soma de exposições antes da primeira venda. Esse valor funciona como enquadramento do risco, e não como uma multa única prevista para qualquer app. A lista apresenta riscos contados por unidade, com valores máximos ou precedentes específicos.

- US$ 53.088 na COPPA: teto por violação citado para a coleta de dados de menores de 13 anos; não é percentual da receita.
- US$ 5.000 na CIPA: indenização por violação citada para o rastreamento com terceiros sem aviso prévio na Califórnia, sem precisar provar prejuízo.
- US$ 53.088 no CAN-SPAM: teto por e-mail que viole a lei, com unidade de contagem diferente da COPPA.
- US$ 6 e 3 anos no DMCA: taxa e validade do registro do agente designado; não são penalidades.
- Até US$ 150.000 no DMCA: valor máximo por obra quando a infração é intencional; o máximo depende dessa condição.

## O que muda para você

Imagine que você vai publicar um app feito com IA com cadastro, fontes, analytics, e-mail de lançamento, assinatura e foto de perfil. O cadastro não pede idade. As fontes vêm do Google. O session replay começa no carregamento da página. O e-mail não tem descadastro nem endereço postal. O checkout não mostra as condições de renovação. O fluxo de uploads não tem /dmca.

Antes do deploy, envie o prompt desta apostila para a IA que escreve o projeto. O pedido é auditar e refatorar as seis frentes. Depois, percorra o fluxo gerado: a data de nascimento deve ser validada antes do salvamento, as fontes devem vir de arquivos locais ou next/font, e o analytics deve esperar o aceite no banner.

Continue pelo conteúdo enviado ao usuário. Os e-mails comerciais precisam ter rodapé com descadastro e endereço postal. A tela de assinatura precisa mostrar valor recorrente, periodicidade e cancelamento acima do botão. Por fim, confira o agente DMCA e a página /dmca. O exemplo serve para ligar cada correção ao ponto do produto em que ela atua.

## O prompt de blindagem jurídica

O prompt abaixo reúne as seis implementações em um único pedido de auditoria e refatoração. Ele foi escrito para ser colado no Cursor, Windsurf, Lovable, Bolt ou Claude antes do deploy.

Copie o texto completo, sem trocar nomes de arquivos, rotas ou configurações. O resultado esperado é uma proposta de alteração que cubra os seis pontos; em seguida, compare o código e o fluxo com a lista desta apostila.

```
Prompt de Blindagem Jurídica (cole no Cursor, Windsurf, Lovable, Bolt ou Claude antes do deploy):

Audite e refatore este projeto para conformidade legal internacional (COPPA, GDPR, CIPA, CAN-SPAM, ARL e DMCA) antes do deploy, aplicando obrigatoriamente estas 6 implementações:
1. Age Gate (COPPA): Adicione validação obrigatória de data de nascimento no fluxo de cadastro antes de persistir qualquer dado no banco. Bloqueie o registro de usuários menores de 13 anos.
2. Fontes Locais (GDPR): Remova todas as chamadas externas para fonts.googleapis.com e fonts.gstatic.com. Configure o carregamento local via arquivos estáticos ou next/font.
3. Consentimento de Session Replay (CIPA/GDPR): Condicione a inicialização de qualquer script de session replay ou analytics comportamental (como PostHog, Microsoft Clarity ou Hotjar) ao consentimento explícito em um banner de cookies, bloqueando o envio de gravações de sessão no carregamento da página.
4. Templates de E-mail (CAN-SPAM): Atualize todos os templates de e-mail comercial/lançamento para incluir no rodapé um placeholder obrigatório de endereço físico postal e um link funcional de descadastro (unsubscribe) em um clique.
5. Tela de Checkout (ARL): Nos componentes de assinatura/Stripe, adicione um bloco de texto claro imediatamente acima do botão de pagamento informando valor recorrente, periodicidade da renovação automática e instruções simples de cancelamento.
6. Fluxo DMCA: Crie uma rota pública /dmca com formulário e instruções de contato para denúncia de violação de direitos autorais e adicione o link no rodapé global da aplicação.
```

## O que fazer hoje

Faça a revisão em ordem, do dado que entra ao conteúdo que sai. Cada passo tem um resultado verificável, para você saber se a alteração ficou no código ou apenas no pedido enviado à IA.

1. Abra o projeto no Cursor, Windsurf, Lovable, Bolt ou Claude e cole o Prompt de Blindagem Jurídica completo; o resultado esperado é uma auditoria que trate COPPA, GDPR, CIPA, CAN-SPAM, ARL e DMCA.
2. No fluxo de cadastro, confira a data de nascimento antes de persistir dados e o bloqueio de menores de 13 anos; o resultado esperado é o Age Gate ativo.
3. Nas dependências da página, confirme a remoção de fonts.googleapis.com e fonts.gstatic.com e o carregamento local; o resultado esperado é que a fonte não dependa desses servidores externos.
4. No analytics, confira maskAllInputs: true no PostHog e o bloqueio da gravação até o aceite; o resultado esperado é nenhum envio de session replay no carregamento.
5. No fluxo de uploads, confira o agente DMCA registrado e a rota /dmca pública com link no rodapé global; o resultado esperado é um caminho de denúncia acessível.

## O que conferir

As correções reduzidas a uma frase podem perder o recorte. Use os pontos abaixo para separar requisito, consequência e limite antes de confiar no resultado.

- Contagem: não trate os valores como percentual do faturamento nem some máximos como se fossem uma cobrança automática; cada número pertence a uma lei e a uma unidade.
- COPPA: a verificação de idade precisa ocorrer antes da persistência, e o prompt determina bloqueio de menores de 13 anos.
- GDPR: o precedente de Munique é um caso específico, com € 100 para um visitante; não o apresente como um teto geral da GDPR.
- CIPA e PostHog: maskAllInputs: true já mascara inputs por padrão. O mascaramento não substitui o bloqueio da gravação e da transmissão até o consentimento.
- ARL: os termos precisam ficar imediatamente acima do botão de pagamento, com valor recorrente, periodicidade e cancelamento.
- DMCA: até US$ 150.000 por obra depende de infração intencional; o registro de US$ 6, válido por 3 anos, e a página /dmca não eliminam a necessidade de revisar o fluxo.
- Revisão humana: compare as alterações geradas pela IA com os seis pontos do prompt e confira o comportamento real do cadastro, do banner, do checkout e do rodapé antes do deploy.

## Glossário

- Age Gate: verificação de idade usada no cadastro para bloquear o registro de usuários menores de 13 anos no fluxo do prompt.
- Analytics: coleta de dados sobre o uso do app.
- Analytics comportamental: análise de cliques e interações durante a navegação.
- Session replay: gravação e transmissão da sessão de navegação para análise.
- Banner de cookies: aviso usado para pedir o consentimento antes de iniciar determinados scripts.
- Consentimento explícito: aceite claro do usuário para a ação ou coleta indicada.
- Input: campo em que o usuário digita dados.
- maskAllInputs: true: configuração do PostHog que mantém o mascaramento dos campos de input.
- Persistir: salvar dados no banco.
- Fonte local: arquivo de fonte servido pelo próprio projeto.
- next/font: recurso citado no prompt para configurar o carregamento local de fontes.
- IP: identificador de rede do visitante citado no precedente de Munique.
- Checkout: tela em que o usuário conclui o pedido ou a assinatura.
- Renovação automática: cobrança recorrente que segue a periodicidade informada na assinatura.
- Descadastro: saída do usuário de uma lista de e-mail, feita pelo link de unsubscribe.
- Upload: envio de um arquivo ou conteúdo pelo usuário.
- Agente DMCA: contato registrado para o fluxo de denúncias de direitos autorais.
- DMCA: lei de direitos autorais dos EUA citada no registro do agente e nas indenizações por obra.
- COPPA: lei federal americana citada para a coleta de dados de menores de 13 anos.
- GDPR: regulamentação europeia de proteção de dados citada no Art. 6º e no caso das fontes externas.
- CIPA: lei da Califórnia citada para o risco de interceptação no rastreamento com terceiros.
- CAN-SPAM: lei americana citada para as regras de e-mail comercial.
- ARL: lei da Califórnia citada para os termos de renovação automática.
- Deploy: publicação da aplicação para uso.
- Stripe: serviço de pagamento citado no prompt para componentes de assinatura.

## Para onde ir depois

Depois de aplicar o prompt, pratique a conferência no fluxo real. O próximo passo é repetir a revisão a cada mudança que mexa em cadastro, fontes, analytics, e-mail, checkout ou uploads.

- Escolha um projeto para publicar e aplique o Prompt de Blindagem Jurídica completo antes do deploy.
- Pratique no cadastro: valide a data antes de salvar e confirme o bloqueio de menores de 13 anos.
- Pratique na comunicação: revise um e-mail comercial e a tela de assinatura como se você fosse o usuário.
- Complete o fluxo DMCA: registre o agente, publique /dmca e coloque o link no rodapé global.
- Use os seis pontos como lista de revisão antes do próximo deploy.

## Links citados

- Precedente de Munique: https://dejure.org/dienste/vernetzung/rechtsprechung?Text=3+O+17493%2F20
- Cal. Penal Code § 637.2: https://law.justia.com/codes/california/code-pen/part-1/title-15/chapter-1-5/section-637-2/
- Mascaramento no Microsoft Clarity: https://learn.microsoft.com/en-us/clarity/setup-and-installation/clarity-masking
- Taxas do U.S. Copyright Office: https://www.copyright.gov/about/fees.html
- Regra COPPA (FTC): https://www.ftc.gov/legal-library/browse/rules/childrens-online-privacy-protection-rule-coppa
