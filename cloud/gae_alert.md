# ポリシーと条件
* アラート ポリシーは、サービスが異常とみなされる条件を定義します。その条件が満たされると、ポリシーによって新しいインシデントがトリガーされて開かれます。
* 条件によって、アラート ポリシーがいつトリガーされるかが決まります。

# 条件のタイプ
 * モニタリングするリソース（個々の VM インスタンスまたはインスタンス グループ、サードパーティ アプリケーション、データベース、ロードバランサ、URL エンドポイントなど）。
 * リソースのパフォーマンスを測定する、事前定義された指標。
 * ユーザーが独自に作成したカスタム指標とログベースの指標。

ログベースの指標についてはこちら
https://cloud.google.com/logging/docs/view/logs_based_metrics


# ポリシーの作成と管理

 - Stackdriver Monitoring Console
   Stackdriver Monitoring API
 - Cloud SDK

コードベースでやるなら下の二つのいずれか

https://cloud.google.com/monitoring/alerts/using-alerting-api?hl=ja

## Cloud SDK
todo

## アラートポリシー
 - metric
   -  https://cloud.google.com/monitoring/api/metrics_gcp
 - uptime check（稼働時間チェック）
   - https://cloud.google.com/monitoring/uptime-checks/
 - process health（プロセスの状態）
   - https://cloud.google.com/monitoring/alerts/ui-conditions-ga

### uptime check（稼働時間チェック）
おそらくこれでHTTPで死活監視してくれる。

### process health（プロセスの状態）
特定のパターンと一致するプロセスの数が期間時間枠の間にしきい値を上回るか下回った場合にインシデントをトリガーするよう、このポリシーを構成することができます。

#### 例
たとえば、プロジェクト内のすべての Compute Engine VM インスタンスにおいて、名前に nginx が含まれ、オーナーが root であるプロセスの数を数える
