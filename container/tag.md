
# Dockerイメージのタグについて

## docker tagコマンド

```
docker tag <イメージid> <リポジトリアカウント名>/<リポジトリ名>:<タグ>
```

開発用イメージにproductionタグをつけるという運用もあるらしい。

```
docker tag app:development app:production
```

### 参考資料

http://docs.docker.jp/linux/step_six.html

## ECRでイメージタグを変更不可にする設定

### メリット
 
 - 上書き可能の場合、イメージを一意に識別するには手作業による識別が必要でした。

### デメリット
 - タグの変更が不可能に設定されたECRでは、イメージタグのlatestを利用した運用が事実上できなくなります。また、一度イメージに付与したタグの変更もできません。例えばECSにおいては、コンテナ定義でのリポジトリのlatest指定も使えないので、新しいイメージがビルドされるたびにタスク定義の変更とサービス定義の変更が必須となります。

### 参考資料

 - https://aws.amazon.com/jp/about-aws/whats-new/2019/07/amazon-ecr-now-supports-immutable-image-tags/
 - https://docs.aws.amazon.com/ja_jp/AmazonECR/latest/userguide/image-tag-mutability.html
