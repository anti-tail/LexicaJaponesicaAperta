# 言島 Kätö nö Sıma — 上代語（ONCOJ）検索

<https://anti-tail.github.io/LexicaJaponesicaAperta/> で公開している検索画面（`index.html` 1 ファイル，データ埋め込み，サーバー不要）．
スマートフォンでも使える．

- 用例検索：語の並び（`pos#VB in#REL`，`lemma:-ki-`，`ka *{0,3} mo` など），構造（TGrep2 の一部：`IP-REL <- #VB+ADN`），転写，万葉仮名の原文
- 検索式の読み下しと，条件に当たるタグ・見出しの数をその場で表示．属性・タグ・見出しの入力候補
- 構造の型と範列：具体的な語の並びが ONCOJ の木でどう書かれているか（例 `PP-SBJ{NP{N} P-CASE-GEN}`）を数え，各位置に立つ品詞・見出しの分布を示す．型はそのまま構造検索の式になり，同じ形の箇所を過不足なく当てる．「例から式を作る」で語ごとに残す条件を選べる
- 「タグを調べる」：タグの意味（成分ごと），親・子の分布，内部構造の型，見出し語．そこから検索式にタグや関係を入れられる
- タグの一覧・成分・入れ子の表（親 × 子の出現数）・データの形の説明
- 見出し語（活用型・自他・地域・関連語つき）

非公開側（言島 `build_corpus_search.py --public`）が作る．おもろさうしなど，権利上公開できない資料のデータは含まない．

## ONCOJ からの変更

- 構文木は ONCOJ 2021.12 の psd ファイルから読み，見出し番号のノードを上の品詞ノードにたたみ，表記ノード（PHON・LOG など）を語の属性にした．
  注釈の中身（ラベル・見出し・音形・表記）は変えていない．
- 一語が表語表記と表音表記にまたがるもの（例 有杼 aredo：LOG are＋PHON do）は 1 語とし，音形をつないだ．
- タグの日本語の説明は ONCOJ の凡例（Grep/TGrep2 ページの一覧）の訳．凡例にない成分（N-DVB の DVB，CFX，PFX-RCP など）は用例からの推定で，画面でその旨を示す．

## 出典とライセンス

ONCOJ の注釈は CC BY 4.0．この画面とデータも CC BY 4.0 とする．

> National Institute for Japanese Language and Linguistics (2021) “Oxford-NINJAL Corpus of Old Japanese” http://oncoj.ninjal.ac.jp/
