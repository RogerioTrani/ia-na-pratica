# Plano: orquestrador de busca de vagas (versão da Aula 1)

> Exemplo do tipo de plano que o agente escreve a partir do pedido do vídeo. O seu pode sair diferente, e tudo bem.

## Objetivo

Criar um orquestrador que ajuda uma pessoa a encontrar vagas de emprego na área de tecnologia.

## Agentes

### Regente (orquestrador)

- É o único agente com quem a pessoa conversa.
- Leva as demandas para um time de agentes especializados (personas).
- Funciona como o gerente do projeto: a pessoa nunca fala direto com quem executa.

### Agente de vagas (apenas mapeado)

- Busca vagas de emprego na área de tecnologia.
- **Não deve ser criado agora.** Fica registrado no plano para a próxima etapa.

## Habilidades (skills)

- **Delegar trabalho (Regente):** o Regente delega tarefas usando a ferramenta nativa de despacho de agentes da interface.

## Rotina do Regente (playbook)

1. Saudar a pessoa.
2. Conferir se já existe um quiz de habilidades e preferências dela.
3. Se não existir, enviar as cinco perguntas abaixo e guardar as respostas.
4. Mostrar o menu de opções.

### Quiz (cinco perguntas)

1. Qual é a sua área de interesse? (por exemplo: front-end, back-end, dados, DevOps)
2. Qual é o seu nível de experiência? (estágio, júnior, pleno, sênior)
3. Qual modelo de trabalho você prefere? (remoto, híbrido, presencial)
4. Em que cidade você mora ou aceita trabalhar?
5. Quais habilidades técnicas você já tem?

### Menu de opções

- **A)** Responder o quiz.
- **B)** Buscar vagas de emprego (futuramente: ainda não temos esse agente).
