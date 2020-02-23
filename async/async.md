
# async/await

## async/awaitとは

- Futureパターンを綺麗に実装するためのAPI
- FutureパターンではPromiseオブジェクトを利用する
  複数のパイプライン処理を実装しようとするとコールバックがネストされてコードの可読性が下がる
 - なので、async/awaitというAPIを利用する

## async 使い方

 - 非同期処理（別スレッドで実行）したい関数について頭にasyncをつけて定義する（スレッドという言い方であってる？）
 - その関数を通常の関数のように呼ぶと非同期処理が別スレッドで始まり、元々の処理はブロックされずに進んでいく

## await 使い方

 - ``await Promise` という形で使う。Promiseの解決を待って、解決された値を返す
 - 大抵はPromiseを返す関数を呼ぶ際につける
 - async function(別プロセス)の中でのみ利用可能

## async/awaitにおけるPromise
 - async functionをawaitを付けずに呼び出すと、Promiseが返されて非同期処理を待たずに先に進む
 - async functionをawaitを付けて呼び出すと、Promiseの解決を待って、解決された値を返される

## サンプル
 - JSのfetch apiはpromiseを返すので、async/awaitと合わせて利用可能

```js
async function callApi() {
  console.log('calling');
  const response = await fetch('https://dummy.restapiexample.com/api/v1/employees')
  const data = await response.json()
  console.log(JSON.stringify(data));
}

callApi()
```

# asyncio

 - Pythonでasync/awaitを使うためのライブラリ
 - JSのものとは名称が異なる
    - Promise <=> Future
    - async function <=> コルーチン
 - Taskという、コルーチンを並列で実装するためのオブジェクト
 - asyncio自体はこれ以外にも多様な機能を持つが、async/awaitを普通に使うには一旦ここまでの理解で良さそう

# ASGI

## 背景
 - WSGI互換で非同期処理を用いるアプリケーションを実装できるインターフェース
 - WebSocketアプリケーションを構築できる

## WSGIとの違い
 - WSGIとは異なり、アプリケーションは単純な呼び出し可能オブジェクトではなくイベントが供給され、asyncio互換性のあるコルーチンとして実行する必要があります
 - ほかHTTPで使う分には大きくは変わらないが、アプリケーションで使える情報とかは細かい違いがあるかも

# responder

 - 普通のWSGIアプリと同じような感じで書ける
 - 一方でWebSocketやGraphQLにも対応している
 - バックグラウンドタスク: ジョブキューでやっているようなことを標準でできるっぽい
 - 
# aiohttp

 - Pythonでfetch(asyncio対応の非同期なHTTPリクエスト)するためのライブラリ
