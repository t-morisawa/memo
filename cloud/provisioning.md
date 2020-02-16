# memo
AWSのプロビジョニングツールの比較

## terraform
 - 状態管理をローカルディスク、またはS3に保存する
 - HCL（独自言語）

## cloudformation
 - 状態管理をスタック(out-of-the-box)として保存する
 - yaml or json 

## aws cdk
 - CloudFormationの開発者向けのラッパーであるCDK
 - 2019/07リリースで新しい

## 比較
 - モジュール化の容易さ
    - terraform優位？
 - ロールバック
    - CFn優位？
    - terrafromは失敗時にロールバックする機能がない
 - dry-run
    - terraform planコマンドでできるらしい
 - 書きやすさ
    - HCLはyamlより書きやすい。pythonもyamlより書きやすい。
 - コードの行数
    - CDK優位
 - 学習コスト
    - どれも同じくらいでは？
    - CDKはCFnと合わせて覚えなければならないが、CFnの文法を覚えてなくていいかもしれない
    - Condition, Mappingsなど独自の表現を覚える必要がある

## CDK選定のポイント
 - 削除保護
 - コード行数
 - テンプレートの分割の方法
 - CFnの知識がどれくらい必要かどうか
 - エディタによるLintがきくか
 - CFnと同等の機能を実現できるか
 - 開発者による実装差分は大きくないか
