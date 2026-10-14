# Acervo do perfil @militar.64 no TikTok — conjunto de dados

Conjunto de dados descritivo das **273 publicações** do perfil `@militar.64` do TikTok,
dedicado à circulação de registros audiovisuais do período da ditadura brasileira
(1964-1985) em chave apologética.

Os dados foram reunidos no âmbito de uma pesquisa sobre arquivos informais digitais e
história pública. São publicados para que outros pesquisadores possam conferir,
reaproveitar e estender a análise.

> **Como citar:** a preencher após a publicação do artigo.
>
> **DOI:** https://doi.org/10.5281/zenodo.23367305
> permanente e preserva o conteúdo mesmo que este repositório seja movido ou removido.

---

## Arquivos

| Arquivo | Conteúdo |
|---|---|
| `militar64_publicacoes.csv` | Uma linha por publicação, 273 linhas, 24 colunas, UTF-8 |
| `militar64_publicacoes.xlsx` | Os mesmos dados em planilha, com oito abas de agregados |
| `DICIONARIO.md` | Descrição de cada coluna |
| `CITATION.cff` | Metadados de citação |

---

## Percurso da pesquisa

O conjunto é um subproduto de uma investigação qualitativa mais ampla, e não o seu ponto
de partida. A ordem importa para quem for reutilizá-lo.

**Fase etnográfica, de novembro de 2024 em diante.** O acompanhamento do perfil começou com
a observação direta: assistir a todas as publicações, ler suas descrições, acompanhar os
comentários do criador e seguir consumindo as novas postagens à medida que apareciam. A
interpretação do acervo — suas operações de seleção, ordenação e recontextualização — vem
dessa fase, não dos números.

**Consolidação do banco, entre 5 e 7 de outubro de 2026.** Só então os dados descritivos
foram sistematizados, para tornar verificável o que a observação já havia identificado e
para documentar a trajetória do perfil em um segundo momento.

Essa diferença de datas tem uma consequência que o leitor precisa ter em conta: as
**métricas descrevem o estado do perfil em outubro de 2026**, enquanto a análise qualitativa
que as acompanha no artigo se apoia na observação de 2024 e 2025.

---

## Como os dados foram reunidos

A coleta combinou duas fontes, identificadas na coluna `origem`.

**Raspagem automatizada (268 publicações).** Executada em 6 de outubro de 2026 com o ator
`clockworks/tiktok-profile-scraper`, na plataforma Apify.

**Coleta manual (5 publicações).** O raspador omitiu cinco publicações, descobertas ao se
comparar o resultado com a contagem manual do perfil — 273 publicações, número confirmado
também pelo contador exibido pela própria plataforma. As cinco foram registradas à mão a
partir da interface do TikTok. Entre elas estava a **segunda publicação mais curtida de todo
o acervo**, o que mostra que a perda do raspador não é proporcional à relevância do item.

### Ferramentas e verificação

A organização e a conferência cruzada dos dados contaram com o apoio de um assistente de
inteligência artificial (Claude, da Anthropic), empregado para consolidar os registros das
duas fontes em uma única tabela, recalcular agregados e cruzar campos em busca de
inconsistências. Nenhum valor foi aceito sem conferência humana contra a interface do
TikTok, e a revisão final dos registros foi feita manualmente em planilha.

A verificação não foi formalidade. Ela corrigiu três erros que teriam passado:

1. A raspagem descartou cinco publicações de 273, entre elas a segunda mais curtida. Só
   apareceu na contagem manual do perfil.
2. O campo `musicOriginal` devolvido pela API classifica como "som original" também áudios
   pertencentes a outras contas. A reclassificação exigiu cruzar esse campo com o de autoria.
3. As datas vinham em UTC. Como o perfil publica sobretudo à noite, 99 das 273 publicações
   caíam no dia seguinte. A correção veio da decodificação do carimbo de tempo contido no
   próprio identificador de cada publicação.

Para pesquisas semelhantes, recomenda-se executar ao menos duas raspagens independentes,
conferir o total contra a contagem manual e validar as datas pelos identificadores.

---

## Limites conhecidos

**Precisão dos contadores.** As **visualizações são arredondadas**: a interface do TikTok
exibe valores como "689.4K" e 63% dos registros acima de mil são múltiplos de cem. Já
curtidas, comentários, salvamentos e compartilhamentos vêm **exatos** da raspagem — valores
como 8.398 ou 7.761 são números reais. A exceção são as cinco publicações de coleta manual,
lidas da interface e portanto arredondadas também nesses campos. Nenhuma das observações
abaixo depende de precisão maior que essa.

**As datas estão em horário de Brasília.** A raspagem devolve o carimbo de tempo em UTC, e
como o perfil publica sobretudo à noite, 99 das 273 publicações mudam de dia na conversão.
A coluna `data_brasilia` é a que corresponde ao que a interface do TikTok exibe e deve ser
usada nas análises; `data_utc` fica registrada para rastreabilidade. Todas as datas foram
recalculadas a partir do identificador numérico da publicação, cujos 32 bits mais altos
codificam o carimbo de tempo Unix.

**As métricas são de um instante.** Refletem o estado do perfil em 6 de outubro de 2026.
Curtidas, visualizações e demais contadores mudam continuamente.

**Campos ausentes nas publicações manuais.** Nome do áudio em quatro delas e presença de
legenda automática em todas as cinco. A coluna `observacao` registra o que falta em cada
caso.

**`presidente_na_descricao` é resultado de busca textual** pelo nome do presidente apenas na
descrição da publicação, antes da primeira hashtag. Não usa as hashtags, porque estas repetem
os nomes de todos os ditadores em quase todas as publicações. O campo portanto *subestima*:
não capta publicações que mostram um presidente sem o nomear por escrito.

**`audio_do_perfil` exigiu reclassificação.** O campo `musicOriginal` devolvido pela API
marca como "som original" também áudios de outros usuários. Aqui, o valor 1 foi atribuído
somente quando o áudio é original *e* creditado ao próprio perfil.

**Limite de hashtags imposto pela plataforma.** Entre 17 de julho e 2 de setembro de 2025 o
TikTok passou a limitar as publicações a cinco hashtags — o intervalo é o que os próprios
dados permitem delimitar, já que não houve publicação em agosto. Antes dessa mudança, a
mediana mensal varia entre 17 e 40 etiquetas; a partir de setembro de 2025, toda publicação
tem exatamente cinco. A queda **não** reflete uma mudança de estratégia do criador, e
comparações de indexação ao longo do tempo precisam considerar esse corte.

**A recepção não foi coletada.** O conteúdo dos comentários dos usuários está fora do
conjunto, por decisão metodológica. A coluna `comentarios` registra apenas a quantidade.

---

## Observações sobre o acervo

Alguns traços que os dados tornam verificáveis:

- **273 publicações**, somando cerca de 8,89 milhões de visualizações e 445,7 mil curtidas.
- **Publicação concentrada no início:** 115 publicações no segundo semestre de 2023 e 85 no
  primeiro de 2024, contra 4 no segundo semestre de 2025 e 3 em 2026. A última publicação
  registrada é de 27 de fevereiro de 2026.
- **201 publicações nomeiam presidentes do regime na descrição, contra 8 que nomeiam
  presidentes civis.** Ernesto Geisel aparece em 71.
- **Indexação massiva e indiscriminada:** 26 hashtags por publicação em média, 987 distintas
  no conjunto. A etiqueta `#ernestogeisel` aparece em 92,9% das publicações raspadas,
  independentemente do conteúdo.
- **Duração mediana de 102 segundos**, mas de 340 segundos entre as dez mais curtidas: as
  publicações que mais circularam são as mais longas.
- **Som original é a regra nos vídeos e a exceção nas imagens:** 70% dos vídeos usam áudio
  do próprio perfil, contra 5% dos posts de imagem. Entre os vídeos, os de som original
  têm mediana de 850 curtidas, contra 403 dos de som tomado da plataforma.
- **Legendas geradas pela plataforma:** 60% dos vídeos raspados têm legendas automáticas, por
  reconhecimento de fala e tradução de máquina para o inglês, não produzidas pelo criador.
- **Uma publicação republicada:** a de 2 de fevereiro de 2025 reapresenta a de 8 de outubro
  de 2023, com a legenda corrigida e menos hashtags.

---

## Uso, ética e licença

O perfil é uma conta pública e os conteúdos aqui descritos são de acesso aberto. Ainda
assim, o conjunto descreve a atividade de uma pessoa identificável, e sua recontextualização
acadêmica pede cuidado.

Nenhum dado de usuários que interagiram com o perfil foi coletado: não há comentários,
identificadores nem qualquer informação sobre terceiros neste conjunto.

Este conjunto é disponibilizado para fins de pesquisa, documentação e verificação. Não
constitui endosso ao conteúdo descrito, cujo teor é apologético a um regime autoritário.

**Licença sugerida:** CC BY 4.0 para os campos descritivos e analíticos produzidos pela
pesquisa. As descrições e hashtags transcritas são de autoria do criador do perfil e estão
reproduzidas aqui a título de citação para fins de pesquisa.

---

## Reprodução

Para refazer a coleta:

1. Execute `clockworks/tiktok-profile-scraper` sobre `https://www.tiktok.com/@militar.64`.
2. Compare o total obtido com a contagem manual das publicações no perfil.
3. Para cada publicação ausente, registre à mão os campos deste dicionário.
4. Observe que a aba "Populares" do TikTok ordena por **curtidas**, embora o número exibido
   sobre cada miniatura seja o de **visualizações**.
5. Na página de uma publicação, a coluna de métricas segue a ordem: curtidas, comentários,
   salvamentos, compartilhamentos.
6. Valide as datas pelos identificadores, e não pelo campo devolvido pela raspagem.

A data de publicação pode ser obtida do próprio identificador: os 32 bits mais altos do `id`
numérico do TikTok são o carimbo de tempo Unix da publicação. Em Python:

```python
import datetime
from zoneinfo import ZoneInfo
ts = int("7352532220206435590") >> 32
print(datetime.datetime.fromtimestamp(ts, datetime.UTC).astimezone(ZoneInfo("America/Sao_Paulo")))
# 2024-03-31 11:20:21-03:00
```
