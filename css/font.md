# CSS のカスタムフォントを使う例

## 実装例

```
@import url('https://fonts.googleapis.com/css?family=Sawarabi+Mincho');
$font-family-base: 'Sawarabi Mincho', sans-serif;
```

## @規則
 - メタデータ情報、条件情報、記述的情報を伝えるのに使う
 - @charset => スタイルシートで使用される文字セットを定義します
 - @import => 外部のスタイルシートを読み込むよう CSS エンジンに指示します
 - @media => メディアクエリの条件を満たすデバイスで読み込まれた場合にこれの中身が適用される、条件付きグループ規則です。
 - @font-face => ダウンロードすべき外部フォントに関する指定を記述します。
 - @keyframes => CSS アニメーションシーケンスの中間ステップに関する指定を記述します。

## @import

記述例は以下の通り。

```
@import url("fineprint.css") print;
@import url("bluish.css") speech;
@import 'custom.css';
```

## url型

string型とは別にurl型というのがある。以下のように使われる

```
background: url("topbanner.png") #00D no-repeat fixed;
```
