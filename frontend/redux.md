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

