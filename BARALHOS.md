# BARALHOS.md — Roadmap editorial da fábrica

> Quadro de gestão dos baralhos: funil pré-publicação, fila de produção e
> banco de ideias. Para baralhos publicados, a fonte da verdade de versão,
> contagem e ciclo de vida é o `indice.json` — este quadro só aponta.
> Mantido pelo Claude Code a cada sessão que altera o estado de algum
> baralho.

## Funil de estados

IDEIA → EM PRODUÇÃO → EM REVISÃO → PUBLICADO (EM_DESENVOLVIMENTO) →
FINALIZADO. Estado lateral: OCULTO (publicado removido do índice,
reversível — o JSON do baralho nunca é deletado).

## Publicados

- Cinema Clássico — Edição 1 · 🎬 · PERSONAGEM_FILME · FINALIZADO (embarcado no app)
- Mundo da Música — Edição 1 · 🎸 · MUNDO_DA_MUSICA · FINALIZADO (embarcado no app)

## Fila de produção (ordem = prioridade; Felipe decide a pauta, Claude executa)

1. Mundo Pop — Edição 1 · 🌟 Mundo Pop · MUNDO_DA_MUSICA · EM REVISÃO
   (2026-07-12) Recorte: ícones da música pop (internacional + Brasil).
   Coleção nova. Gerado como `baralhos/mundo-pop-1.json` (30 cards,
   EM_DESENVOLVIMENTO v1, já no índice); régua aprovada; revisão humana
   das dicas pendente.
2. Mundo dos Bruxos — Edição 1 · 🎬 Cinema Clássico · PERSONAGEM_FILME ·
   EM PRODUÇÃO (2026-08-01) Recorte: universo bruxo — 45 personagens, 13
   criaturas, 12 objetos (70 cards no total). Gerado como
   `baralhos/mundo-dos-bruxos-1.json` (EM_DESENVOLVIMENTO v2, já no
   índice); expandido de 30→70 cards em 2026-08-01 (`mb_031`–`mb_070`
   novos: 25 personagens, 8 criaturas, 7 objetos; `mb_001`–`mb_030`
   intocados, ids imutáveis); régua aprovada (`validarCatalogo` exit 0);
   revisão humana das dicas pendente (dos 40 cards novos).
   Restrições editoriais próprias deste baralho, decididas pelo Felipe:
   nenhuma dica, nem o nome, nem a descrição citam a marca registrada ou
   o título da obra, e não há citação literal de fala dos livros ou
   filmes — as dicas são descrições originais.
   **Exceção deliberada à regra de unicidade de respostas** (decidida
   pelo Felipe em 2026-07-26, depois de a colisão ter sido reportada):
   duas respostas deste baralho já existem em `cinema-classico-1`
   (cards `pf_001` e `pf_012`), que é FINALIZADO e imutável. As dicas
   aqui são inteiramente novas; o baralho finalizado não foi tocado.
   Consequência conhecida: as duas coleções são a mesma, então uma
   partida que combine os dois baralhos pode repetir essas respostas.
   **Não "corrigir" isso em sessão futura sem falar com o Felipe.**
3. Mundo Pop — Edição 2 · 🌟 Mundo Pop · MUNDO_POP · BLOQUEADO
   Recorte: séries, memes, celebridades. Depende de categoria nova
   MUNDO_POP no app (tarefa do repositório Fehhhh94/QuemSou).

## Banco de ideias (sem ordem, sem compromisso)

- (vazio — adicionar conforme surgirem)

## Insumos para próximas edições

- (vazio — feedback sobre baralhos FINALIZADOS que não pode virar edição
  in-place é registrado aqui)
