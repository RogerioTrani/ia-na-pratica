# App feito com IA pode somar US$ 100 mil em processos

_2026-11-23 · reportagem_

Seis configurações comuns em app gerado por IA criam multas e indenizações antes da primeira venda. Nas leis citadas, o valor é cobrado por unidade de violação (visitante, e-mail, obra) e não por percentual do faturamento. Cada risco tem a regra, a correção e um prompt pronto para colar na sua IA antes do deploy.

## O contexto

Em muitas leis digitais dos EUA e da Europa, a penalidade não depende da receita da empresa. O cálculo é por unidade de violação: cada visitante, sessão ou e-mail pode contar como uma violação separada. Por isso o passivo nasce com o primeiro usuário.

As seções abaixo trazem seis pontos que as ferramentas de IA costumam deixar passar, o valor em jogo em cada um e o que ajustar.

Fonte: <https://www.ftc.gov/business-guidance/resources/complying-coppa-frequently-asked-questions>

## Cadastro e fontes externas (COPPA e GDPR)

Cadastro sem filtro de idade: a COPPA (16 CFR Part 312) vale para quem coleta dados de menores de 13 anos. A multa chega a US$ 53.088 por violação. Peça a data de nascimento no cadastro antes de salvar qualquer dado e bloqueie o registro de menores de 13 anos. Fonte: https://www.ftc.gov/business-guidance/resources/complying-coppa-frequently-asked-questions

Fontes carregadas de servidor externo: carregar fontes direto do Google envia o IP do visitante aos servidores deles sem consentimento prévio. Precedente: o tribunal de Munique, em 20/01/2022 (processo 3 O 17493/20), fixou € 100 por visitante com base no Art. 6º do GDPR. Hospede as fontes no seu próprio servidor. Se usar Next.js, carregue localmente com arquivos estáticos ou next/font. Fonte: https://dejure.org/dienste/vernetzung/rechtsprechung?Text=3+O+17493%2F20

Fonte: <https://dejure.org/dienste/vernetzung/rechtsprechung?Text=3+O+17493%2F20>

## Analytics e e-mail (CIPA e CAN-SPAM)

Analytics com session replay: PostHog e Clarity gravam a sessão do visitante. Na Califórnia, rastrear com terceiros sem aviso prévio pode ser tratado como interceptação ilegal. Dispare o analytics só depois do aceite de cookies e mantenha o mascaramento de todos os campos de input ligado. No PostHog, a opção está em session_recording. Guia oficial: posthog.com/docs/session-replay/privacy. Fonte: https://law.justia.com/codes/california/code-pen/part-1/title-15/chapter-1-5/section-637-2/

E-mail sem opção de descadastro: pelo CAN-SPAM Act, cada e-mail que viola a lei pode custar até US$ 53.088. Vale para o e-mail de lançamento enviado à lista de espera. Ponha no rodapé um link de descadastro que funcione, um endereço postal físico válido, e atenda os pedidos de saída em até 10 dias úteis. Fonte: https://www.ftc.gov/business-guidance/resources/can-spam-act-compliance-guide-business

```
maskAllInputs: true
```

Fonte: <https://law.justia.com/codes/california/code-pen/part-1/title-15/chapter-1-5/section-637-2/>

## Checkout e uploads (ARL e DMCA)

Checkout sem termos de renovação: a lei de renovação automática da Califórnia (Cal. Bus. & Prof. Code § 17602 e § 17603) exige termos de renovação perto do pedido de consentimento. Sem consentimento expresso, a cobrança fica nula. Na tela de assinatura (Stripe, por exemplo), mostre um resumo da cobrança logo acima do botão de assinar, com valor, frequência da renovação e a regra de cancelamento. Fonte: https://www.leginfo.ca.gov/pub/09-10/bill/sen/sb_0301-0350/sb_340_bill_20091011_chaptered.html

Uploads sem proteção DMCA: sem agente DMCA registrado, o dono do app responde por imagens que usuários postam. O registro do agente é feito no U.S. Copyright Office: taxa de US$ 6 por designação, com validade de três anos. Diretório: copyright.gov/dmca-directory. Publique uma página com a política de remoção de conteúdo e o formulário de denúncia, com link no rodapé. Fonte: https://www.law.cornell.edu/uscode/text/17/504

Fonte: <https://www.law.cornell.edu/uscode/text/17/504>

## O prompt de blindagem

Cole o texto abaixo na IA que escreve o seu código (Cursor, Windsurf, Lovable, Bolt ou Claude) e peça a auditoria antes de publicar o app.

```
Audite e refatore este projeto para conformidade legal internacional (COPPA, GDPR, CIPA, CAN-SPAM, ARL e DMCA) antes do deploy, aplicando obrigatoriamente estas 6 implementações:
1. Age Gate (COPPA): Adicione validação obrigatória de data de nascimento no fluxo de cadastro antes de persistir qualquer dado no banco. Bloqueie o registro de usuários menores de 13 anos.
2. Fontes Locais (GDPR): Remova todas as chamadas externas para ://googleapis.com e ://gstatic.com. Configure o carregamento local via arquivos estáticos ou next/font.
3. Consentimento de Analytics (CIPA/GDPR): Condicione a inicialização de qualquer script de analytics ou session replay (PostHog, Hotjar, Clarity, GA4) ao consentimento explícito em um banner de cookies, e ative o mascaramento padrão de todos os campos de input.
4. Templates de E-mail (CAN-SPAM): Atualize todos os templates de e-mail transacional/marketing para incluir no rodapé um placeholder obrigatório de endereço físico postal e um link funcional de descadastro (unsubscribe) em um clique.
5. Tela de Checkout (ARL): Nos componentes de assinatura/Stripe, adicione um bloco de texto claro imediatamente acima do botão de pagamento informando valor, periodicidade da renovação automática e instruções simples de cancelamento.
6. Fluxo DMCA: Crie uma rota pública /dmca com formulário/instruções de contato para denúncia de violação de direitos autorais e adicione o link no rodapé global da aplicação.
```

Fonte: <https://www.ftc.gov/business-guidance/resources/complying-coppa-frequently-asked-questions>

## O que conferir

Os valores são os citados na reportagem para cada lei. Regra COPPA na íntegra, no site da FTC: https://www.ftc.gov/legal-library/browse/rules/childrens-online-privacy-protection-rule-coppa

Guia oficial do Microsoft Clarity sobre mascaramento de conteúdo: https://learn.microsoft.com/en-us/clarity/setup-and-installation/clarity-masking. Tabela de taxas do U.S. Copyright Office: https://www.copyright.gov/about/fees.html

Fonte: <https://www.ftc.gov/business-guidance/resources/complying-coppa-frequently-asked-questions>
