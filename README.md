# Cartório — Interface de Revisão de Transcrições

Interface single-page para transcrição automatizada de registros manuscritos via Claude API (vision) com aprovação humana ponto-a-ponto.

**Acessível em:** https://henriquesimoessilva3-png.github.io/cartorio-revisao/

## Como usar

1. Abrir o link acima.
2. Colar sua API key da Anthropic no campo no topo da página e clicar "Salvar chave". A chave fica apenas no `localStorage` do seu navegador — nunca sobe pro servidor.
3. Arrastar imagens ou PDFs de registros pra zona de drop à esquerda. PDFs com várias páginas são separados automaticamente.
4. Cada documento passa por uma transcrição em **dupla passagem** (double-pass) — duas leituras independentes. Divergências viram "dúvidas" destacadas em amarelo.
5. Resolver cada dúvida na coluna direita: aceitar leitura A, B, ou digitar outra.
6. Aprovar o documento quando todas as dúvidas estiverem resolvidas.
7. Baixar o ZIP com tudo aprovado (HTML + JSON + imagens + index).

## Onde tudo é armazenado

| Dado | Onde |
|---|---|
| Chave da API | `localStorage` do seu navegador |
| Glossário (editável) | `localStorage` |
| Fila de documentos + transcrições + aprovações | IndexedDB do seu navegador |
| Documentos aprovados (saída) | Baixados como ZIP por você |

**Nada sai do seu computador exceto chamadas pra api.anthropic.com.**

## Modelos

- `claude-sonnet-4-6` (padrão) — equilibrado
- `claude-opus-4-7` — mais preciso, ~3x mais caro
- `claude-haiku-4-5` — mais barato/rápido, pior em caligrafia complexa

## Origem

Código-fonte completo no repo de pesquisa: `henriquesimoessilva3-png/matemagica-kids`, branch `claude/document-transcription-analysis-aMGt6`, em `documentos_cartorio/`.

Quando estabilizar, migrar a fonte para este repo.
