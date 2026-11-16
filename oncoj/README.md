# ONCOJ 由来の上代語データ（Old Japanese data derived from ONCOJ）

Oxford-NINJAL Corpus of Old Japanese（ONCOJ）2021.12 の `oncoj.csv` と `lexicon.xml` を，
[CLDF](https://cldf.clld.org/)（Dictionary モジュール）の表に書き換えたもの．Lexica Japonesica の `tools/export_aperta.py` が作る．

| 表 | 行数 | 中身 |
| --- | --- | --- |
| `cldf/languages.csv` | 1 | 上代語（OJ8，Glottocode oldj1239） |
| `cldf/entries.csv` | 5871 | ONCOJ の見出し語（番号，表記，品詞，用例数） |
| `cldf/senses.csv` | 6190 | 見出し語の語釈（英語） |
| `cldf/examples.csv` | 4992 | 歌・文（MYS.1.1 など）．万葉仮名の原文，転写，語ごとの音形と品詞 |
| `cldf/tokens.csv` | 117388 | 語（トークン）．音形，品詞，見出し語，複合語，表記の種類（音仮名・訓仮名・正訓字など），句構造 |

資料別の歌の数：萬葉集 4694，日本書紀歌謡 133，古事記歌謡 112，仏足石歌 21，風土記歌謡 20，続日本紀歌謡 8，上宮聖徳法王帝説 4

## ONCOJ からの変更

- 表の形を CSV（ONCOJ の木構造の行）から CLDF の表に変えた．注釈の中身（音形，品詞，見出し語，語釈，表記の種類，句構造のラベル）は変えていない．
- 句構造は語ごとに上位のラベルの列（`Path`）として持たせた．`;@n` の指標は品詞の列からは外したが，`Path` には残した．
- 複合語は，構成要素の見出し語を `Entry_ID`，複合語全体の見出し語を `Compound_Entry_ID` に分けた．
- `lexicon.xml` の語釈は，sense ごとに `senses.csv` の 1 行にした（ID は「見出し番号-通し番号」）．
- `lexicon.xml` で同じ番号が二つの見出しに使われているもの：L090819（L090819 と L090819_2）．二つ目以降の ID に `_2` を付け，トークンは語形で振り分けた．
- `oncoj.csv` にあって `lexicon.xml` にない見出し番号：L000058（1 語），L004122（9 語），L007139（1 語），L031111b（6 語），L031317b（1 語），L031475b（1 語），L031511b（1 語），L050149b（1 語），L080426（1 語）．これらの語は `Entry_ID` を空にし，元の番号を `ONCOJ_Lemma` に残した．

## 出典とライセンス

ONCOJ の注釈は [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) で公開されている．この表も CC BY 4.0 とする．
使うときは ONCOJ を次の形で引用し，あわせてこの書き換え（Lexica Japonesica Aperta）を示すこと．

> National Institute for Japanese Language and Linguistics (2021) “Oxford-NINJAL Corpus of Old Japanese” http://oncoj.ninjal.ac.jp/

元にしたファイル：`oncoj.csv`（sha256 24d7f28fec2e92d87eccfbeb776cc966a0eeacd153dac3b1b843dee8c37166b4），`lexicon.xml`（sha256 b6c06d00e61c53325217b5494e64130297ad1f30aa9c9dd1347472b8a23b6d2f）．
