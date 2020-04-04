
# 懸念
 - ECSサービスでどのコンテナが動いているのかわかりにくい <- まあコンソールを見ればわかる
 - サービスが再起動されると、latestのコンテナが起動してしまう <- これはやばい
 - 巻き戻しの手順が不明
 - 手順が多くかったるい
 - デプロイスクリプトとCFnテンプレートは共存できるのか

# バージョニング

 - コンテナのタグに日付やバージョンを入れておく

# 環境差分

 - リポジトリは同一、タグで分けたい
 - コンテナ定義で参照するイメージのタグが異なるので、

# GitHub <-> ECRの疎通
 - GitHub上での何かのアクションをトリガーにECRにデプロイさせたい
 - CodeBuild & CodePipelineでできる？
 - CircleCIではやりきれないの？

# 各種ツール

何か便利ツールがあるかもしれない

https://qiita.com/naomichi-y/items/d933867127f27524686a

# 参考情報
 - https://developer.hatenastaff.com/entry/2018/09/26/133000
 - https://qiita.com/naomichi-y/items/d933867127f27524686a

# ECS CLIについて

 - イメージのpushができる
 - ecs-cli compose service でECSサービスの操作ができる

同じコンテナの再起動

```
ecs-cli compose service up --force-deployment
```

異なるコンテナの起動

 - わからない
 - 
