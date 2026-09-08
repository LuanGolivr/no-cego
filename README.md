# Nó Cego

Jogo mobile de detetive onde o jogador resolve assassinatos **gerados por IA**,
interrogando suspeitos em linguagem natural e deduzindo o culpado, a arma, o
local e o horário do crime. Cada caso é único e sempre tem solução.

Trabalho Interdisciplinar IV — Ciência da Computação, PUC Minas · 2º semestre 2026.

## Sobre o projeto

O núcleo do jogo é um **grafo de conhecimento**: os nós são as entidades do caso
(pessoas, locais, armas, horários) e as arestas são as relações entre elas
(motivo, paradeiro, testemunho...). Resolver o caso é reconstruir esse grafo a
partir das pistas; pegar um suspeito na mentira é achar duas informações que se
contradizem.

A **Inteligência Artificial** atua em três camadas:

1. **Gerador de casos** — algoritmo de satisfação de restrições (CSP) que cria
   cada mistério e garante que ele tem uma única solução.
2. **Classificador de intenção** — modelo de NLP (treinado pela equipe) que
   entende as perguntas do jogador no interrogatório.
3. **LLM** — dá voz e personalidade às respostas dos suspeitos (camada de
   linguagem, sobre a lógica definida pelo sistema).

## Objetivo de Desenvolvimento Sustentável (ODS)

**ODS 4 — Educação de Qualidade.** O jogo desenvolve raciocínio lógico-dedutivo
e pensamento crítico por meio de casos infinitos e sempre solucionáveis.

## Arquitetura

Monorepo com três componentes:

| Pasta     | Componente            | Stack                         |
|-----------|-----------------------|-------------------------------|
| `mobile/` | Aplicativo            | Flutter (Dart)                |
| `api/`    | API principal         | Node.js + TypeScript          |
| `ai/`     | Serviço de IA         | Python (classificador de NLP) |

- **Armazenamento:** PostgreSQL (nuvem) + SQLite/SharedPreferences (local, no app).
- **Autenticação:** Firebase Auth (o backend valida o token; nunca guarda senha).
- **Recursos do dispositivo:** biometria e GPS.

O grafo completo do caso (com a solução) vive apenas no backend; o app recebe só
os dados visíveis e monta, localmente, o grafo do que o jogador foi descobrindo.

## Como rodar (em construção)

> As instruções detalhadas de cada serviço estão nos READMEs de `mobile/`,
> `api/` e `ai/`.

```bash
# subir os serviços de apoio (banco etc.)
docker compose up -d

# variáveis de ambiente
cp .env.example .env   # e preencha os valores
```

## Documentação

Requisitos, fluxos e diagramas do projeto estão em [`docs/`](./docs).

## Equipe

- <!-- Nome — função -->
- <!-- ... -->

## Licença

<!-- definir (ex.: MIT) ou remover -->
