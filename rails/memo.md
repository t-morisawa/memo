
# キーワード
## mixin
 - 多重継承のかわり
 - メソッドのみをもつクラスで、インスタンス化できないもの
 - DjangoやVueのMixinと同じようなもの
 - include, extendなどで定義

## Action Cable
 - WebSocketヘルパ
 - チャット機能などで利用されるっぽい。

https://railsguides.jp/action_cable_overview.html

## @
 - インスタンス変数の頭につける。
 - クラス変数には@@をつける。

http://www.tohoho-web.com/ruby/variables.html

## シンボル
 - https://www.ruby-lang.org/ja/documentation/ruby-from-other-languages/
 - 値のキーとして文字列を扱うより軽量
 - コロン一つをつけたもの
 - railsでは、before_actionで実行するメソッド名を指定するのにシンボルを使う

## ActiveJob
 - Active Jobは、ジョブを宣言し、それによってバックエンドでさまざまな方法によるキュー操作を実行するためのフレームワーク
 - https://railsguides.jp/active_job_basics.html
 - メール配信などに利用
 - AWSでは「ELB + Webサーバ」ではなく「SQS + Workerサーバ」のような形で実現する
 - ジョブキュー・メッセージキューのジョブキューの方。
 - Pythonはceleryというものがある
 - RubyならResqueやsidekiqなど
 
## View
 - テンプレートが配置される。
 - ただしSPAにおいては、jbuilderというのを使う感じになる。

# TODO
 - Railsのルーティングファイルの読み方
 - JBuilder(viewファイル)
