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

よくわからないのでこのチュートリアルをやってみるといいのでは。

https://docs.aws.amazon.com/ja_jp/apigateway/latest/developerguide/api-gateway-tutorials.html
