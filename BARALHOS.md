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
2. Mundo Pop — Edição 2 · 🌟 Mundo Pop · MUNDO_POP · BLOQUEADO
   Recorte: séries, memes, celebridades. Depende de categoria nova
   MUNDO_POP no app (tarefa do repositório Fehhhh94/QuemSou).

## Banco de ideias (sem ordem, sem compromisso)

- (vazio — adicionar conforme surgirem)

## Insumos para próximas edições

- (vazio — feedback sobre baralhos FINALIZADOS que não pode virar edição
  in-place é registrado aqui)
