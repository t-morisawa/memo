# API Gateway

目的: CloudFormationでAPI Gatewayを使おうとしたらエラーが出るのでなんとかする

出ていたエラー

```
Errors found during import: 
Unable to put integration on 'ANY' for resource at path '/': Invalid function ARN or invalid uri 
Unable to put integration on 'ANY' for resource at path '/{proxy+}': Invalid function ARN or invalid uri 
(Service: AmazonApiGateway; Status Code: 400; Error Code: BadRequestException; Request ID: xxx)
```

## 調査

### インポートとは

 - インポートとは、REST API を API Gateway にインポートすること。
 - API のインポート機能では OpenAPI v2.0 および OpenAPI v3.0 定義ファイルがサポートされています。
 - Swaggerとは、OpenAPIを用いてREST APIを設計する際に使用するツールセットのこと。

### Integration(統合)とは

よくわからないのでこのチュートリアルをやってみる。

https://docs.aws.amazon.com/ja_jp/apigateway/latest/developerguide/api-gateway-tutorials.html

ANYとは、HTTP methodのことをさすっぽい。

API Gatewayが受け取ったリクエストをどこに流すか。それをどこと統合するかと呼ぶらしい。

HTTPプロキシはHTTPエンドポイントに流し、LambdaプロキシはLambdaに流す

### HTTPプロキシのチュートリアル

デプロイするとこんなエンドポイントが発行される。

https://xxxxxx.execute-api.ap-northeast-1.amazonaws.com/test/

ここにパラメータを付与するとそれに基づいてプロキシへリクエストされる

### 残件

色んなチュートリアルが残っているのでそれも試してみると良いかもしれない

https://docs.aws.amazon.com/ja_jp/apigateway/latest/developerguide/api-gateway-tutorials.html
