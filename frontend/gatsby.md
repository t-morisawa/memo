# Babel
## Babelとは
 - JSを後方互換性のある形にコンパイルするツールチェーン
 - 設定ファイル `.babelrc` `babel.config.js`
 - 2019年現在はBabel7
 
## BabelでReactのコンパイル

モジュールインストール
```
npm install --save-dev @babel/preset-react
```

設定ファイルに記述を追加

```
{
  "presets": ["@babel/preset-react"]
}
```

## Babelのプラグイン
 - Reactの解釈ができるようになるようにいろんなプラグインがある
 - FlowとかTypeScriptの変換とか

## セットアップ

```
npm install --save-dev @babel/core @babel/cli @babel/preset-env
npm install --save @babel/polyfill
```

```
babel-core
Babelのコアなんでしょう。これだけだと特に何もしてくれない。

babel-polyfill
コンパイラが頑張っても、補いきれない機能(Promiseとか)をポリフィルで足す。

babel-cli
名前からわかりそうですが、babelコマンドを使えるようにしてくれます。
```


## SCAMPERの実装

以下のような実装になっている。

```
{
  "presets": ["es2015", "react"]
}
```

ただし `@babel/preset-es2015` はbabel v6ですでに古くなっており、 `@babel/preset-env` に置き換えられている。

```
"babel-core": "^6.25.0",
"babel-loader": "^7.0.0",
"babel-preset-es2015": "^6.24.1",
"babel-preset-react": "^6.24.1",
```

`babel-loader` はwebpackからbabelを利用するのに使う。

## Gatsbyでの実装

 - package-lock.json` に実装あり
 - https://www.gatsbyjs.org/docs/babel/
 - デフォルトでほぼ全てのブラウザに対して対応があるとのこと

# Webpack

