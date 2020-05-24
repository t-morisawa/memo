
# GraphQL

## 目的
 - RESTのより深い理解
 - GatsbyにおけるGraphQLの理解
 
## GraphQLとは
 - 

## GraphQL vs REST
 - GraphQLはレスポンスのフィールドを明示的に指定する
   - RESTの場合はクエリパラメータなどを使うしかない。
   - これによりRESTは設計がクライアントサイドの仕様に依存しやすかったが、GraphQLはその問題を解消している
 - GraphQLはキャッシュが最適化されている
   - RESTはパス単位でキャッシュする
   - GraphQLはオブジェクト単位でキャッシュする
 - GraphQLには型がある
