
# REST

 - Web APIの仕様の一種。
 - リソース指向
 - ステートレス

## メリット
 - 軽量性
 - 透明性
 - 使いやすさ

## Enterprise Integration Patterns

異なるアプリケーション間を連携する手法。

- File Transfer
- Shared Database
- Remote Procedure Invocation
- Messaging

このうち多くのWeb APIはRemote Procedure Invocationに分類される。

これはネットワーク上の同期的な関数呼び出しによってデータをやりとりする形式。

## RPC

 - クライアントからサーバーへのアクセスには、HTTPのPOSTを用いる。
 - サービス指向（動詞、コマンド名、メソッド名単位でAPIを整理）
 - 公開するURLが http://ホスト名/サービス名/メソッド名 みたいな形になり、ここにPOSTでXMLにまとめた引数を渡す

### SOAP

 - XMLベースのRPCプロトコル
 - RESTでは不特定多数を対象にした、入力パラメータが少ない情報配信や検索サービス等での利用に向いている。
 - SOAPでは複雑な入力を必要としたり、入出力に対してチェックを必要とするようなサービス等での利用に向いている。
 - SOAPはHTTPだけでなく、他のプロトコルも使うことが出来る。
