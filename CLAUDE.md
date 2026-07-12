# QuemSou-Baralhos — Guia da fábrica interna para o Claude

> Este repositório é o **catálogo de conteúdo** do app QuemSou e a linha de
> produção da fábrica interna (5B). O formato dos JSONs, as regras
> editoriais e o guia de criação de cards têm dono no repositório do app
> (`docs/CATALOG_FORMAT.md`, `docs/CARDS_GUIDE.md`) — este arquivo só rege
> **como trabalhar aqui**.

## Ritual de início (todo prompt)

- `cd C:\Dev\QuemSou-Baralhos` + `git remote -v`; só seguir se o remoto for
  `Fehhhh94/QuemSou-Baralhos`.
- **Nunca fazer `git push`.** Push é sempre manual do Felipe — e aqui push
  **publica conteúdo de verdade** para todos os aparelhos.

## Uma sessão, um repo

- Nunca editar `C:\Dev\QuemSou` a partir daqui. Aprendizado que mexe em
  docs do app (ex.: regra editorial nova no `CARDS_GUIDE.md`) vira prompt
  separado no outro repo.

## Estrutura

- `baralhos/` — **publicado**: servido ao app via GitHub raw; baralho
  `FINALIZADO` é imutável para sempre (evolução só via "… — Edição 2").
- `drafts/` — rascunhos em revisão/playtest.
- `feedback/` — exports de playtest, commitados como histórico
  (matéria-prima das sessões de análise).
- `indice.json` — a vitrine: o app só enxerga o que está listado nele.

## Regra do índice

- `indice.json` **NUNCA** referencia arquivos de `drafts/`.

## Pipeline de um baralho

1. Ler `docs/CARDS_GUIDE.md` do repo QuemSou antes de gerar.
2. Gerar o rascunho em `drafts/` no formato de `docs/CATALOG_FORMAT.md`
   (repo QuemSou).
3. **PORTÃO 1** — validar o draft: informar ao Felipe o comando pronto para
   rodar no repo do app (a task vive no QuemSou):
   `./gradlew validarBaralho -Parquivo=C:\Dev\QuemSou-Baralhos\drafts\<id>.json`
4. Triagem conversacional.
5. Playtest.
6. Análise do feedback.
7. Publicação (abaixo).

## Formato de revisão

- Cards SEMPRE apresentados em formato legível na conversa (resposta +
  dicas numeradas). NUNCA pedir revisão de JSON cru.

## Publicação atômica

- Mover o arquivo de `drafts/` para `baralhos/` + adicionar/atualizar a
  entrada no `indice.json` + bump de versão — tudo em **UM commit**.
- **PORTÃO 2** antes do commit: `validarCatalogo` aprovando a pasta
  `baralhos/` (`./gradlew validarCatalogo -Ppasta=C:\Dev\QuemSou-Baralhos`,
  no repo do app).

## Análise de feedback

- Além de corrigir cards mal avaliados, procurar **padrões** no conjunto e
  propor regras editoriais novas.
- Regra nova só entra no `CARDS_GUIDE.md` com aval explícito do Felipe — e
  nunca reescreve baralho `FINALIZADO`.

## Commits

- Em português, formato `tipo: descrição`.
