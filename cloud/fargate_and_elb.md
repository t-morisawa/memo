# Fargate <-> ELBの疎通
## とりあえずELBをコマンドラインから作成したい

基本はここを見ていく。
https://docs.aws.amazon.com/ja_jp/elasticloadbalancing/latest/application/tutorial-application-load-balancer-cli.html

## 毎回IPを更新しなくてもよくする設定
先にLBを設定して、それにアタッチされるようにサービスを作成してやれば行けそうな雰囲気
https://docs.aws.amazon.com/AmazonECS/latest/userguide/create-application-load-balancer.html
LBとのアタッチは
Elastic Load Balancing not configured. Load Balancing 設定はサービス作成時にのみ設定できます。
とあるので、LBの設定を先にやらなければいけなかったらしい

ecs-cli compose service up
https://docs.aws.amazon.com/ja_jp/AmazonECS/latest/developerguide/cmd-ecs-cli-compose-service-up.html
ロードバランサを指定することができる

> また、ロードバランサーからの着信トラフィックを許可するコンテナインスタンスのセキュリティグループに、セキュリティグループルールを追加する必要があります。詳細については、「ロードバランサーの作成」を参照してください。
こういう記述もある。

これをecs-params.ymlに書くのは無理なのか？
-> そういう設定はなさそうな雰囲気。

ecs-params.yml
https://docs.aws.amazon.com/ja_jp/AmazonECS/latest/developerguide/cmd-ecs-cli-compose-ecsparams.html
docker-compose
https://docs.aws.amazon.com/ja_jp/AmazonECS/latest/developerguide/cmd-ecs-cli-compose-parameters.html
ecs-paramsというのは、ecs-cli compose serviceのオプション。
https://docs.aws.amazon.com/ja_jp/AmazonECS/latest/developerguide/cmd-ecs-cli-compose-service.html

ロードバランサの指定は、その子コマンドのecs-cli compose service upで利用する。

## Fargateの更新
aws ecs update-service --cluster <cluster name> --service <service name> --force-new-deployment
https://stackoverflow.com/questions/34840137/how-do-i-deploy-updated-docker-images-to-amazon-ecs-tasks

## プライベートサブネットのFargateタスクに接続する方法
セキュリティグループの設定ができていなかったのかもしれないので、そこをいい感じにすればOK
https://docs.aws.amazon.com/ja_jp/AmazonECS/latest/developerguide/create-application-load-balancer.html
