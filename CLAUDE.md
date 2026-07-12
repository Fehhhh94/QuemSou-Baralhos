# QuemSou-Baralhos — Guia da fábrica para o Claude

> **v1 (2026-07-12).** Este repositório é a **fábrica de conteúdo** do
> QuemSou: hospeda o catálogo estático de baralhos (índice + um JSON por
> baralho) servido via GitHub raw. Este arquivo descreve apenas o estado
> atual; histórico vive no repositório do app (`Fehhhh94/QuemSou`,
> `docs/CHANGELOG.md`).

## Regras inegociáveis (ler antes de qualquer coisa)

- **Nunca fazer `git push`.** Push é sempre manual do Felipe.
- **Nunca reescrever histórico sem confirmação explícita do Felipe.**
  Nada de `commit --amend`, `rebase` ou `reset` por conta própria — na
  dúvida, commit novo. Reescrita só quando pedida ou combinada no prompt.
- **Início de todo prompt**: rodar `git remote -v` na raiz. Só seguir se o
  remoto for `Fehhhh94/QuemSou-Baralhos`. Se for outro repo, PARAR.
- **Ids são imutáveis para sempre**: id de baralho e id de card são chave
  da união determinística no app. Nunca renomear, nunca reutilizar.
- **Baralho `FINALIZADO` é imutável para sempre.** Feedback ruim sobre um
  finalizado vira insumo para um baralho novo ("Edição 2" ou subtítulo
  temático) — nunca edição in-place.
- **Este repo não tem regra própria de validação.** A régua executável mora
  no repositório do app (`Fehhhh94/QuemSou`) como tasks Gradle
  (`validarBaralho` / `validarCatalogo`). Nada aqui duplica, reimplementa
  ou "melhora" essas regras.
- **A régua nunca substitui a revisão humana.** Ela pega estrutura e regras
  mecânicas; autossuficiência e força das dicas são julgamento do Felipe.

## Estrutura do catálogo

- Um arquivo **índice** JSON na raiz + **um JSON por baralho**.
- Formato canônico: `docs/CATALOG_FORMAT.md` no repositório do app —
  este repo apenas o obedece, nunca o redefine.
- Todo baralho pertence a uma **categoria existente** no app
  (`PERSONAGEM_FILME`, `MUNDO_DA_MUSICA`) e a uma **coleção** (id, nome,
  emoji). Máximo de **100 cards por baralho**; crescimento além disso vira
  baralho novo.
- Ciclo de vida: `EM_DESENVOLVIMENTO` (versões podem adicionar, remover ou
  melhorar cards) → `FINALIZADO` (imutável).

## Regras editoriais (resumo do inegociável)

Guia completo: `docs/CARDS_GUIDE.md` no repositório do app — em dúvida, o
guia manda. O mínimo que todo card respeita:

1. Exatamente **10 dicas**, resposta não vazia, nenhuma dica vazia.
2. **Nenhuma dica contém a resposta** (ignoreCase) — a régua reprova.
3. Dicas em **ordem decrescente de dificuldade**: a dica 1 é a mais difícil,
   a 10 quase entrega. (Julgamento humano — a régua não mede isso.)
4. Cada dica é **autossuficiente**: faz sentido lida isolada, sem depender
   das anteriores. (Julgamento humano.)

## Ritual de publicação (obrigatório, nesta ordem)

1. **Criar/editar** o JSON do baralho: id imutável, ≤100 cards, categoria e
   coleção existentes, ciclo de vida correto.
2. **Bump de versão** no baralho **e** entrada correspondente no índice —
   a régua checa a consistência cruzada (versão e contagem de cards) e
   reprova divergência. Sem bump, o app nunca vê a mudança.
3. **Rodar a régua** a partir do repositório do app, apontando `-Ppasta=`
   para a raiz deste repositório. Só seguir com **zero violações**.
4. **Revisão humana** do Felipe: força das dicas, ordem de dificuldade,
   autossuficiência, tom. Nada é publicado sem esse passo.
5. **Commit** em português, formato `tipo: descrição`. **Sem push** —
   antes de sugerir push manual, conferir `git log origin/main..HEAD`.
6. Publicado = disponível na URL raw que o índice referencia. O app cruza
   índice × Room e deriva os estados de download sozinho.
   **Atenção ao cache do GitHub raw**: após o push, a URL raw pode servir
   a versão antiga por ~5 minutos. Nunca validar no app imediatamente
   após publicar — esperar o raw refletir o bump antes de qualquer
   veredito, senão o teste produz falso negativo.

## Ingestão de feedback do app

O app exporta JSON `quemsou-feedback` versão 1 (votos 👍/👎 por card, com
comentário opcional, rodada, resultado e dica do acerto). Ritual:

1. Felipe cola o JSON no chat.
2. Cruzar os votos com os cards dos baralhos deste repo (por baralhoId +
   cardId; `resposta` nula = card já removido, ignorar).
3. Priorizar cards com voto FRACO; propor revisões concretas
   (reescrita de dica, reordenação, substituição do card).
4. Propostas só se aplicam a baralhos `EM_DESENVOLVIMENTO`. Para
   `FINALIZADO`, registrar como insumo de próxima edição.
5. Nenhuma revisão entra sem passar pelo ritual de publicação completo.

## Geração de conteúdo novo

- O Claude Code pode gerar baralhos e cards diretamente neste repo
  (não existe mais pipeline Gemini dentro do app).
- Todo lote gerado passa pela régua ANTES da revisão humana — violação
  estrutural deve virar mensagem legível na revisão, nunca exceção.
- Respostas são **surpresa**: nunca listar respostas de um baralho em
  README, descrição de commit ou qualquer texto voltado ao jogador.
