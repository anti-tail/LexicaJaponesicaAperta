# 言島 Kätö nö Sıma — ONCOJ の上代語検索

<https://anti-tail.github.io/LexicaJaponesicaAperta/> で公開している検索画面．`index.html` 1 ファイルにデータを埋め込んであり，サーバーは要らない．
スマートフォンでも使える．英語版は <https://anti-tail.github.io/LexicaJaponesicaAperta/en/>．

転写の読み方と，ONCOJ と中納言のちがいは解説のページにまとめた：<https://anti-tail.github.io/LexicaJaponesicaAperta/guide.html>

意見・要望・不具合・データの誤りは，画面右上の「意見を送る」から送れる．GitHub の Issue になる．

- 用例検索：`pos#VB in#REL`，`lemma:-ki-`，`ka *{0,3} mo` のような語の並び，`IP-REL <- #VB+ADN` のような TGrep2 風の構造，転写，万葉仮名の原文で探せる
- 検索式の読み下しと，条件に当たるタグ・見出しの数をその場で表示する．属性・タグ・見出しは入力の途中で候補が出る
- ことばで探す：「関係節の中の動詞の連体形」「係助詞を含む主節で連体形で終わる」のような日本語や，pito no／ヒとのコ のような上代語の語形で探せる．英語版では verb inside relative clause のような英語も使える．読み取った構造検索の式も出る．資料は複数選べる
- 見出し語の用例：「見出し語で用例」欄に語形・語釈・番号を打って選ぶと，その見出しの用例だけを出す．複合語の見出しでもよく，語形・品詞・単独か複合語の部分かで絞れる．`#lem=L050083` のような URL で直接開ける
- 構造の型と範列：具体的な語の並びが ONCOJ の木で `PP-SBJ{NP{N} P-CASE-GEN}` のようにどう書かれているかを数え，各位置に立つ品詞・見出しの分布を示す．型はそのまま構造検索の式になり，同じ形の箇所を過不足なく当てる．「例から式を作る」で語ごとに残す条件を選べる
- 「タグを調べる」：成分ごとのタグの意味，親・子の分布，内部構造の型，見出し語を示し，そこから検索式にタグや関係を入れられる
- タグの一覧，成分，親 × 子の出現数を数えた入れ子の表，データの形の説明
- 活用型・自他・地域・関連語つきの見出し語一覧

非公開側の言島 `build_corpus_search.py --public` が作る．権利上公開できない資料は，データも画面のコードも含めない．書き出すときに自動で検査し，痕跡があれば書き出さない．

## ONCOJ からの変更

- 構文木は ONCOJ 2021.12 の psd ファイルから読み，見出し番号のノードを上の品詞ノードにたたみ，PHON・LOG などの表記ノードを語の属性にした．
  ラベル・見出し・音形・表記といった注釈の中身は変えていない．
- 有杼 aredo＝LOG are＋PHON do のように一語が表語表記と表音表記にまたがるものは 1 語とし，音形をつないだ．
- タグの日本語の説明は ONCOJ の凡例，つまり Grep/TGrep2 ページの一覧の訳．N-DVB の DVB，CFX，PFX-RCP のような凡例にない成分は用例からの推定で，画面でその旨を示す．

## 出典とライセンス

ONCOJ の注釈は CC BY 4.0．この画面とデータも CC BY 4.0 とする．

> National Institute for Japanese Language and Linguistics (2021) “Oxford-NINJAL Corpus of Old Japanese” http://oncoj.ninjal.ac.jp/

変体仮名の表示のため，Noto Serif Hentaigana の必要な字だけを画面に埋め込んでいる．このフォントは SIL Open Font License 1.1 で，© The Noto Project Authors．
