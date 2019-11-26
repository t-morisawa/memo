# 概要
クラウド環境でIP固定する方法を調べる

## AWS
 - Nat Gatewayを使う
 - Global Acceleratorを使う
 - L4ロードバランサをL7ロードバランサの前に置く

## GCP
 - Cloud NATを使う

### そもそもGCPでロードバランシングするには？
 - Cloud Load Balancing を使う

# Cloud NAT
 - GCEの出口のIPを固定できる
   - GCEと言うか、VPC?
 - GAEは不可らしい？

# Nat Gateway
 - Elastic IPと言うサービスで静的IPを取得すること

# AWS Global Accelerator
 - 多分、入り口のIPを固定するサービスで、今回の用件とは異なる感じ
 - AWSのアプリケーションの手前に置くやつ

# Network Load Balancer
 - IPを固定することが可能
 - これも入口のIPのため、用件とは異なる

# メモ
 - 入口をIP固定したいのか、出口をIP固定したいのか？
   - 今回は出口のはず。
 - NATとは
   - プライベートネットからインターネットに接続するためのもの

# TODO
 - https://docs.aws.amazon.com/ja_jp/vpc/latest/userguide/vpc-nat-gateway.html を読む
