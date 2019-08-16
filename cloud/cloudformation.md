# CloudFormation

目的: CloudFormationでAPI Gatewayを使おうとしたらエラーが出るのでなんとかする

SAMがまずわからない。

## 使っているコマンド

3行目でエラー

```
sam build --use-container --template cloudformation.yaml
sam package --template-file .aws-sam/build/template.yaml --output-template-file packaged.yml --s3-bucket $npm_package_config_s3BucketName
sam deploy --template-file packaged.yml --stack-name $npm_package_config_cloudFormationStackName --region $npm_package_config_region --capabilities CAPABILITY_IAM --parameter-overrides
```

まずそれぞれのコマンドの意味を確認する

## sam build 

sam build: cfnテンプレートから、パッケージを作っているっぽい

```
Built Artifacts  : .aws-sam/build
Built Template   : .aws-sam/build/template.yaml
```

### sam package

S3にパッケージをアップデートするコマンドっぽい？

### sam deploy

Lambdaにデプロイ
