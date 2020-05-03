# Redux

## 概要
https://redux.js.org/

 - 状態を把握しやすい
 - テストしやすい
 - Undo/Redoがしやすい
 - デバッグしやすい

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

