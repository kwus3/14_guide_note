# 概要  

- できることから進めていかないとずっと未完成のままなので、まず必要なものを普通にHTMLとCSSで作る
- ある程度体系が見えてきたら分解してパーツにしていく
- SPAに作り替える

## 要件定義

- 短時間で開けてプレイ中でも確認できること
- プレイ中でもギリ操作できること(次へ、戻るなど最低限の操作)
- となるとスマホでタッチ操作前提の作りが良さそうか

## 技術的なやりたい事

- 立ち上がり重くなってもいいから操作始まったらサクサクにしたい
- どのルレかは決まってるので総合TOP選択後に申請するので、総合TOPで全部読み込むか、各ルレTOPで各ルレまるっと読むかにしたい
- テキストデータはjsonとかで持たせて読み込ませる、選択によって読み込む内容を変更する

## UI・UX関連

- 近づく、離れる、頭割り(集まる)、隕石(すてる)、視線(うしろ向く)、のような汎用ギミックはアイコンを説明文に添える
- アイコンはここが良さそう [https://boxicons.com/](https://boxicons.com/)
- 赤マークや青範囲のように色の付いたギミックがあるので最低限文字色を変えられるようにしたい
- ボタンを押下して分岐していき最終的に、コンテンツ攻略詳細メモが表示(ex: レベルレTOP → 紅蓮(61〜69) → 65:バルダム→詳細メモ)
- 次へをタップする毎に、(1道中)1ボス → (2道中)2ボス → (3道中)3ボス → (4道中)4ボスと切り替わる
- 最後まで行ってさらに次へ押下すると終了する(総合TOPへ戻る要素)
- 詳細前の大枠で選択していく時はカード形式で表示とかの方が視覚的に見やすい？
- 表示に関係なく、攻略メモ表示中は画面右半分が「次へ」、左半分が「前へ」でもいいかもしれない
- マクロ攻略メモで分かったのは、動かしながらだと4〜5行が限界なのが分かったので、とにかく視認性を重視したい
- 履行技の時に次へを押して、前半・後半でメモを分ける事はできそうかも
- 差し色は各拡張にそれらしいカラーリングにして色も判断材料にする事で少しでも決定までの時間を短縮させたい
- 新生(水色)、蒼天(濃蒼#395a61 #2f3850)、紅蓮(濃紅#8e2018 #7a231e)、漆黒(深紫#8681f6 #212123)、暁月(青〜銀〜赤？)
- the HUNTのサイトのタブにそれっぽいのあるから色指定参考にしてもいいかも
- 暁月 linear-gradient(to right, #3d4d99 0%,#3689b3 50%,#cc7a29 100%)
- 新生は数が多いので2列にした方がいい(レベルレで15、50で17もあるから2列で9行必要)
- 基本0層と1層は1列、2層は2列とし、2層でもレベルレの蒼天〜暁月は1列とする(5個のみなので)、3層は個別のレイアウト

## 構成の大枠

**総合TOP(第0層):**

- レベルレ(1-A)、50607080ルレ(1-B)、90ルレ(1-C)、アラルレ(1-D)
- エキルレは90で代用できるので不要、ノマレはまだ無理なので一旦不要、討滅ルレも一旦不要

---

**レベルレTOP(第1層A):** 

- 新生15-49(2A-01)、蒼天51-59(2A-02)、紅蓮61-69(2A-03)、漆黒71-79(2A-04)、暁月81-89(2A-05)

**50607080ルレTOP(第1層B):**

- 新生50(2B-01)、蒼天60(2B-02)、紅蓮70(2B-03)、漆黒80(2B-04)

**90ルレTOP(第1層C):**

- 暁月90(2C-01)

**アラルレTOP(第1層D):**

- 新生クリタワ(2D-01)、蒼天マハ(2D-02)、紅蓮RtI(2D-03)、漆黒ヨルハDA(2D-04)、暁月ミソロ(2D-05)

---

**レベルレ新生15-49(第2層A-1)**

- サスタシャ15(3A1-001)、、、オーラム47(3A1-0XX)

**レベルレ蒼天51-59(第2層A-2)**

- ダスク51(3A2-001)、、、グブラ59(3A2-005)

以下略

---

サスタシャ**15(第3層A1-001)**

- ここがいわゆる詳細ページ

---
