# Redux

## 概要
https://redux.js.org/

### 特長

 - 状態を把握しやすい
 - テストしやすい
 - Undo/Redoがしやすい
 - デバッグしやすい

### 三原則

 - Single source of truth
 - State is read-only
 - Changes are made with pure functions

## API

### Top Level API

```
createStore(reducer, [preloadedState], [enhancer])
combineReducers(reducers)
applyMiddleware(...middlewares)
bindActionCreators(actionCreators, dispatch)
compose(...functions)
```

 - まずはcreateStoreだけ知っておけば良さそう
 - SCAMPERのアプリでも、createStoreとcombineReducersしか使っていない

### Store API

```
getState()
dispatch(action)
subscribe(listener)
replaceReducer(nextReducer)
```

 - createStore APIにReducerを渡して初期化する
 - Storeは状態を持たず、いくつかのメソッド(API)を提供するオブジェクトである
 - react-reduxのconnectを利用すると、propsとしてstore apiが渡される
   - 生のReduxでコンポーネントがstore apiを利用する方法はよくわからなかった（createStoreの戻り値をバケツリレーするのかな？）
 - subscribeは、dispatchに対するイベントリスナを追加するメソッド
   - react-reduxでは、コンテナコンポーネントを定義(connectメソッドを利用)した場合に内部的に利用されている

## Reduxを利用するメリット/タイミング

 - 状態をpredictibleにしたい場合（テストやデバッグ、あるいは状態の永続化や復元をしやすくする）
 - すべてをトップレベルのReactコンポーネントの状態に保つようなアプローチではもはや十分でないくらいアプリが巨大化した場合

## react-reduxとの関係

 - 公式では「ほとんどの場合、Reactバインディングと開発者ツールも必要になります。」という扱いになっている。
 - 組み込みサンプルでもreact-reduxが使われたものが紹介されている。
 - ReduxをReactで使う場合のヘルパというイメージなのかな