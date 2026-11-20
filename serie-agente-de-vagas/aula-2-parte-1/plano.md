# Plano: orquestrador de busca de vagas (versão da Aula 2, parte 1)

> Exemplo do plano depois de completado com as diretrizes para modelos mais baratos e o desenho da arquitetura. O seu pode sair diferente.

## Diretrizes para modelos gratuitos e baratos

Modelos gratuitos seguem o texto ao pé da letra e percebem menos nuances. Por isso:

- Escreva instruções claras, explícitas e sem subjetividade.
- Diga o que fazer **e o que não fazer**.
- Uma tarefa por vez, com a saída esperada descrita.
- Quando faltar informação, pergunte ou avise; nunca invente.

## Arquitetura

```text
Camada do usuário
      |
   Regente  (interface principal: conversa com a pessoa, coordena os agentes e consolida o resultado)
      |
      +-- Agente de vagas   (missão única: buscar vagas; ainda não criado)
```

Cada agente tem uma única missão e começa com a janela de contexto limpa. Isso reduz erros, principalmente em modelos mais baratos.

## Estrutura de pastas

- `personas/`: um arquivo por agente (o Regente fica em `personas/regente.md`).
- `skills/`: as habilidades dos agentes, uma por arquivo.
- `data/`: o que o Regente guarda da conversa, como o quiz e o perfil da pessoa.
- `AGENTS.md`: manda a IA ler e adotar a persona do Regente ao abrir o projeto.

## Regente

- Único agente com quem a pessoa conversa.
- Habilidade (skill) de **delegar trabalho** usando a ferramenta nativa de despacho de agentes.
- Rotina: saudar; conferir se existe quiz em `data/`; se não existir, enviar as sete perguntas do quiz e salvar o perfil; mostrar o menu.

### Quiz (ampliado para sete perguntas)

1. Área de interesse.
2. Nível de experiência.
3. Modelo de trabalho preferido (remoto, híbrido ou presencial).
4. Localização.
5. Soft skills mais fortes.
6. Objetivo de carreira (primeiro emprego, crescimento técnico ou transição de carreira).
7. Habilidades técnicas.

O Regente envia as sete perguntas de uma vez, numeradas, e grava o perfil em `data/perfil-do-usuario.md`.

### Menu

- **A)** Responder o quiz.
- **B)** Buscar vagas de emprego (futuramente).

## Limites

- O Regente não executa buscas nem avalia vagas: ele delega.
- Nada de acessar arquivos fora da pasta do projeto.
