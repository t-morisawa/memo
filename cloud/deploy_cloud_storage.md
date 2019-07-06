# Cloud Storageにファイルをアップロードするまでの手順

1. サービスアカウントを作る

要するにIAMユーザを作る。利用サービスに応じて適当に権限を割り当てる

2. 秘密鍵を生成してダウンロードする

3. 鍵とSDKを紐付ける

```
gcloud auth activate-service-account --key-file ~/[PATH].json
```

4. ファイルをアップロードする

```
gsutil cp [FILENAME] gs://[BUCKET_NAME]/[FILENAME]
```

うまくいかなかったらサービスアカウントの権限設定が間違っているのでGCPコンソールから修正する。
