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

# react-redux

## 概要

 - Reduxチームによって管理されている

## API

```
connect
Provider
```

### connect

 - 要するにReactコンポーネントをReduxストアにconnectしている
 - 具体的には、接続されたコンポーネントに、ストアから必要なデータの一部と、アクションをストアにディスパッチするために使用できる関数を提供する
 - 任意引数として、 `mapStateToProps` `mapDispatchToProps` などをとる

#### mapStateToProps

 - state => Objectな関数
 - 戻り値のObjectがコンポーネントのpropsとして渡される
 - 内部的には、Reduxの `store.subscribe` にこの関数が渡されている。よってdispatchされるごとにこの関数が呼び出される

#### mapDispatchToProps

 - dispatch => Objectな関数（ただし実際は後述の短縮形として利用することも多い）
 - 戻り値のObjectがコンポーネントのpropsとして渡される
 - Objectの各要素はactionをdispatchするような関数となる
    - 例: `increment: () => dispatch({ type: 'INCREMENT' })`

#### mapDispatchToProps（短縮形）

 - 各要素がactionCreatorであるオブジェクト

#### connectの特殊な使い方

以下のようにconnectを引数なしで呼び出すと、propsとしてdispatchが関数が渡される

```
export default connect()(TodoApp)
```

## Why react-redux?
 
 - 任意のFWでReduxを使用している場合、通常、UIコードからReduxストアと直接対話するのではなく、「UIバインディング」ライブラリを使用して、ReduxをUIフレームワークと結び付けます。
 - react-reduxを使用する理由を理解するには、「UIバインディングライブラリ」の機能を理解することが役立つ場合があります。
 - ReduxとReactを統合するには、ストアのアップデートを購読する必要などがあるが、それを手動で作成するのが面倒なので、こういったバインディングアプリがあると考えればOK。
 - また、パフォーマンスも最適化されている

# React State復習

 - コンポーネントの持つ状態
 - React.Componentを継承したクラスが持つAPIとして、state(コンストラクタ以外ではRead Only), setStateが提供されている
 - setStateが呼び出されるとDOMが更新される
 - stateはコンポーネント毎に定義される。よって、stateは一つではない
 - よってコンポーネント間でstateを共有したい場合は、祖先コンポーネントでstateを定義して、それらにpropsとして渡してやる
   - その場合、setStateはstateを利用するコンポーネントでは利用できなくなるので、一緒にイベントハンドラを渡してやる必要がある
 - Redux Store内のstateと、Reactのstateはなんとなく似て非なるものという感じがする
