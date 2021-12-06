# 概要  

- やらんと終わらんので手を動かす、必要最低限をHTMLとCSSでまず作る  
- キャッシュ周りちゃんとやれば早々内容更新しないものなのでいけるかも？  
- ただSPAにはしてみたいので、ある程度形になったら分解してパーツにしていく  

## 要件定義  
- すぐ開けて、プレイ中でも確認できること  
→加えて、プレイ中ギリギリ操作できること(次へ、戻るなど最低限の操作)  
- 動かしながら見るので、とにかく見やすいこと(マクロメモで動かしながらだと4〜5行が限界だった)
→となるとスマホでタッチ操作前提のレイアウトが良さそう  

## 技術的なやりたい事  
- 立ち上げ重くなってもいいから、操作始まったらサクサクにしたい  
→どのルレかは決めてから申請するので、分岐前の総合TOPもしくは各ルレTOPでコンテンツをまるっと読み込みたい  
- テキストデータはjsonとかで持たせて読み込ませる、選択によって読み込む内容を変更したい  
→htmlだとデータがバラけてしまい管理が大変になるので1箇所に集約したい  

## UI・UX関連  
- 近づく、離れる、頭割り(集まる)、隕石(すてる)、視線(うしろ向く)、のような汎用ギミックは説明文に背景色とアイコンを添える  
→アイコンはここが良さそう [https://boxicons.com/](https://boxicons.com/)  
- 赤マークや青範囲のように色の付いたギミックがあるので最低限背景色を変えられるようにしたい  
- ボタンを押下して分岐していき最終的に、コンテンツ攻略詳細メモが表示(ex: レベルレTOP → 紅蓮(61〜69) → 65:バルダム→詳細メモ)  
- 次へをタップする毎に、(1道中)1ボス → (2道中)2ボス → (3道中)3ボス → (4道中)4ボスと切り替わる  
→最後まで行ってさらに次へ押下すると終了する(総合TOPへ戻る要素)  
- 表示に関係なく、攻略メモ表示中は画面右半分が「次へ」、左半分が「前へ」でもいいかもしれない(間違った分岐をしてしまった場合の前に戻るも欲しい、これはヘッダーもしくはフッターをうまく浮かして対応したい)  
- 討滅戦は履行技の時に次へを押して、前半・後半でメモを分ける事はできそうかも  
- 差し色は各拡張にそれらしいカラーリングにして色も判断材料にする事で少しでも決定までの時間を短縮させたい  
- 新生(水色)、蒼天(濃蒼)、紅蓮(濃紅)、漆黒(深紫)、暁月(青〜赤グラデ？)  
- 新生は数が多いので2列にした方がいい(レベルレで15、50で17もあるから2列で9行必要)  
- 基本0層と1層は1列、2層は2列とし、2層でもレベルレの蒼天〜暁月は1列とする(5個のみなので)、3層は個別のレイアウト  

## 構成の大枠  
**総合TOP(第0層):**  
- レベルレ(1_01)、50607080ルレ(1_02)、90ルレ(1_03)、アラルレ(1_04)  
- エキルレは90で代用できるので不要、ノマレはまだ無理なので一旦不要、討滅ルレも一旦不要  
---

**レベルレTOP(第1層A):**  
- 新生15-49(2_01_01)、蒼天51-59(2_01_02)、紅蓮61-69(2_01_03)、漆黒71-79(2_01_04)、暁月81-89(2_01_05)  
**50607080ルレTOP(第1層B):**  
- 新生50(2_02_01)、蒼天60(2_02_02)、紅蓮70(2_02_03)、漆黒80(2_02_04)  
**90ルレTOP(第1層C):**  
- 暁月90(2_02_05)の中身へ直接  
**アラルレTOP(第1層D):**  
- 新生クリタワ(2_04_01)、蒼天マハ(2_04_02)、紅蓮RtI(2_04_03)、漆黒ヨルハDA(2_04_04)、暁月ミソロ(2_04_05)  
---

**レベルレ新生15-49(第2層A-1)**  
- サスタシャ15(3_01_01_001)、、、オーラム47(3_01_01_0XX)  
**レベルレ蒼天51-59(第2層A-2)**  
- ダスク51(3_01_02_001)、、、グブラ59(3_01_02_005)  
**レベルレ紅蓮61-69(第2層A-3)**  
- セイレーン海61(3_01_03_001)、、、アバニア69(3_01_03_005)  
**レベルレ漆黒71-79(第2層A-4)**  
- ホルミン61(3_01_04_001)、、、グルグ79(3_01_04_005)  

以下略  
---

サスタシャ**15(第3層A1-001)**  
- ここがいわゆる詳細ページ  
---

## 他、思った事メモ  
高さは10vhで1vh分でフッターパネルをつくる  
最大数が確か新生x0IDが確か17コンテンツなので2x9=18でギリいける、横2列で高さ1vhで9行かな  
ボタン同士の隙間が全くないと誤タップ誘発しそうだと思った  
思ったけどヘッダーいらないかも？スマホ操作的にフッター部分に操作系を集約したい、かつ普段は縮めてて押すと展開するみたいな  
ヘッダーフッターは浮かせてるものにしてコンテンツの中身はスクロールさせる感じもいいかも？あーでもそれだと一番下のコンテンツがちょっと被っちゃうか、何か考えないといけないな