# QuemSou-Baralhos — catálogo estático

Conteúdo pronto para publicar no repositório público `Fehhhh94/QuemSou-Baralhos`
(gerado pelo app QuemSou, 5A parte 2). O app lê tudo via GitHub raw — sem
servidor, sem chave de API.

## Estrutura

```
indice.json          ← o que a tela de catálogo lista (uma entrada por baralho)
baralhos/<id>.json   ← um arquivo por baralho (apontado pela url do índice)
```

O formato completo (campos, regras de conteúdo, teto de 100 cards, ciclo de
vida) é documentado em `docs/CATALOG_FORMAT.md` do repositório do app — este
repositório DEVE segui-lo. O app valida tudo no download: baralho inválido
não entra no aparelho.

## Como publicar

1. Criar o repositório público `Fehhhh94/QuemSou-Baralhos` no GitHub.
2. Copiar `indice.json`, a pasta `baralhos/` e este README para a raiz,
   branch `main`, e fazer push.
3. Conferir se a URL bate com a constante do app
   (`HttpFonteDoCatalogo.URL_DO_INDICE`):
   `https://raw.githubusercontent.com/Fehhhh94/QuemSou-Baralhos/main/indice.json`

## Como publicar um baralho novo

1. Criar `baralhos/<id>.json` no formato do `CATALOG_FORMAT.md` (o card
   **herda a categoria do baralho**; ids são para sempre).
2. Adicionar a entrada correspondente no `indice.json` (com
   `quantidadeDeCards`, `url` e `tamanhoEmBytes` do arquivo).
3. Push — o app vê a novidade na próxima abertura do catálogo.

## Como atualizar um baralho `EM_DESENVOLVIMENTO`

1. Editar `baralhos/<id>.json` **incrementando `versao`**.
2. Atualizar `versao`, `quantidadeDeCards` e `tamanhoEmBytes` no `indice.json`.
3. Push — quem já baixou vê o botão "Atualizar".

Um baralho `FINALIZADO` é imutável para sempre: evolução só via baralho novo
("… — Edição 2").

## Baralho de teste

`baralho-de-teste-1` (coleção 🧪 "Baralho de Teste", `EM_DESENVOLVIMENTO`,
6 cards) existe para validar download e atualização no aparelho sem tocar
nos baralhos reais — dá para testar o fluxo de update bumpando a `versao`
dele. Não é conteúdo de jogo; pode ser removido do índice quando não servir
mais.
