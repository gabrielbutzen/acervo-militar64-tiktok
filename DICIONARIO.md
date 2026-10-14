# Dicionário de dados

`militar64_publicacoes.csv` — 273 linhas, 24 colunas, UTF-8, separador vírgula.
Ordenado por `data_brasilia` e `hora_brasilia`, da mais antiga à mais recente.

| Coluna | Tipo | Descrição |
|---|---|---|
| `id` | texto | Identificador numérico da publicação no TikTok, preenchido nas 273. Os 32 bits mais altos codificam o carimbo de tempo Unix da publicação. |
| `origem` | texto | `raspagem` (268) ou `coleta manual` (5). |
| `data_brasilia` | data | Data de publicação em horário de Brasília (America/Sao_Paulo), `AAAA-MM-DD`. **É a coluna a usar nas análises** — corresponde ao que a interface do TikTok exibe. |
| `hora_brasilia` | hora | Hora da publicação em horário de Brasília, `HH:MM`. |
| `data_utc` | data | A mesma data em UTC, como vem da raspagem. Difere de `data_brasilia` em 99 das 273 publicações, porque o perfil publica sobretudo à noite. |
| `curtidas` | inteiro | Curtidas no momento da coleta. É o critério de ordenação da aba "Populares" do TikTok. |
| `visualizacoes` | inteiro | Visualizações. É o número exibido sobre a miniatura na grade do perfil. |
| `comentarios` | inteiro | Comentários recebidos. O conteúdo dos comentários não foi coletado. |
| `salvamentos` | inteiro | Vezes em que a publicação foi salva por usuários. |
| `compartilhamentos` | inteiro | Compartilhamentos. |
| `duracao_seg` | inteiro | Duração em segundos. |
| `post_de_imagem` | 0/1 | 1 quando a publicação é uma sequência de imagens, e não um vídeo. |
| `fixado` | 0/1 | 1 quando a publicação estava fixada no topo do perfil na data da coleta. |
| `audio_nome` | texto | Nome do áudio conforme exibido pela plataforma. |
| `audio_autor` | texto | Conta a que a plataforma credita o áudio. |
| `audio_do_perfil` | 0/1 | 1 somente quando o áudio é original **e** creditado ao próprio perfil. Ver a ressalva no README: o campo `musicOriginal` da API, sozinho, não distingue isso. Vazio nas publicações manuais. |
| `legenda_automatica` | 0/1 | 1 quando a plataforma gerou legendas automáticas para a publicação, por reconhecimento de fala e tradução de máquina. Vazio nas publicações manuais. |
| `n_hashtags` | inteiro | Quantidade de hashtags na descrição. Atenção ao limite de cinco imposto pela plataforma a partir de meados de 2025. |
| `local_marcado` | texto | Marcação de local escolhida pelo criador, quando houver. Nem sempre corresponde ao conteúdo. |
| `presidente_na_descricao` | texto | Presidentes nomeados **na descrição**, antes da primeira hashtag, separados por `; `. Vazio quando nenhum é nomeado. Campo derivado por busca textual; ver limites no README. |
| `descricao` | texto | Texto da publicação até a primeira hashtag, com quebras de linha substituídas por espaço. |
| `hashtags` | texto | Hashtags da publicação, separadas por espaço, na ordem original. |
| `url` | texto | Endereço da publicação. Preenchido nas 273. |
| `observacao` | texto | Notas sobre a coleta de cada linha, sobretudo nas publicações manuais. Vazio nas raspadas. |

## Campos presentes na raspagem e não incorporados

A raspagem devolve outros campos que foram examinados e descartados por estarem vazios ou
não serem informativos neste caso: `mentions` e `detailedMentions` (nenhuma publicação
menciona outra conta), `repostCount` (zero em todas), `effectStickers` (apenas o rótulo
"High Quality", em 31 publicações), `aiVideoDescription`, `aiVideoSummary` e
`transcriptionLink` (vazios em todas), `isAd`, `isSponsored`, `isStory` e
`hasTikTokShopProduct` (sem variação).

Permanecem disponíveis na raspagem original, caso sejam úteis a outra investigação:
`mediaUrls` e `videoMeta.coverUrl` (endereços das mídias e das capas, de validade temporária),
`videoMeta.subtitleLinks` (arquivos das legendas automáticas, com idioma e método de geração),
`videoMeta.height`/`width`/`definition`/`format`, `textLanguage` e os dados do perfil em
`authorMeta`.
