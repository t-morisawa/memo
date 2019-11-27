# CORB
- CORBはレスポンスをブロックする制約なので、リクエストがブロックされる心配はない
  - 例えばimg要素経由のリクエストで画像でないデータが返された時にブラウザを保護する目的でブロックする
- sendBeaconによるリクエストのみで発生し、XHRでは発生しない
- Chromeでのみ発生し、Firefoxでは発生しない

# sendBeacon

 - Content-Type: text/plain; となっているので Content-Type: application/json;charset=UTF-8 などにした方が良さそう
 - Sec-Fetch-Mode: no-cors になっている
   - XHRでリクエストした場合は Sec-Fetch-Mode: cors

# 次のアクション
 - Beacon APIの仕様を確認
 - Sec-Fetch-Modeの仕様を確認
