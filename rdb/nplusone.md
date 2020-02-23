
# N+1問題
## 概要

https://qiita.com/massaaaaan/items/4eb770f20e636f7a1361 とか読んでみればOK

## 解決方法
 - `.all` する前に `preload` しておく
 - `.all` したあとループに入る前に `include` しておく
