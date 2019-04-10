# App Engine

## こちらを実施
```
App Engine スタンダード環境での Django の実行
https://cloud.google.com/python/django/appengine?hl=ja
```

## 料金
無料枠あり。インスタンスがスケールされないのであれば無料で運用可能

```
F1	$0.05
F2	$0.10
F4	$0.20
無料枠 1 日あたり 28 インスタンス時間
```

（参考） Beanstalk
```
t2.micro    1    1 GiB    EBS     0.0152USD/h
```

## デプロイ
SDKをインストールするとCLIからデプロイできる

```
gcloud app deploy
```

## 監視
### ログ（例）
脱Elasticできそう？
```
Stackdriver Logging + Cloud Storage + Data Portal
```

### アラート（例）
```
Stackdriver -> Pagerduty, Slack
```
