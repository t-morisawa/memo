
# タスクキュー

キューとワーカーがいる。

Redis, RabbitMQ, Kafka, SQSはキューやブローカーと呼ばれる。

Celery, SidekiqなどはWebフレームワークに組み込んでキューとワーカーをまとめて面倒見てくれるもの。

CeleryはブローカーとしてRedis, RabbitMQを参考に構築できる。

## ストリーム処理

 - 終わりがない、いつどれくらい来るかわからない入力データの処理のこと
 - この処理にキューのシステムが使われる。
 - ログ処理や通知

## ジョブキュー/タスクキュー

 - ストリーム処理でプログラムを実行できるようにするもの
 - メール送信など