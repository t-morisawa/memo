
# Vueの始め方

 - CDN
 - npm
 - vue-cli

## CDN

 - 小規模プロジェクトでは有効。
 - 各ページについて `new Vue({ el: '#container '})` + コンテナ要素 + `Vue.component` で定義
 - 問題点については https://jp.vuejs.org/v2/guide/single-file-components.html を参照

## npm

 - 単一ファイルコンポーネント(.vueファイル)を作成、コンパイルしてjsファイルを生成する
 - webpack + vue-loader 的ないつものやつが出てくる
   - webpack は commonjs モジュールを require で読み込むことができる
   - loaderはcommonjsモジュールに変換するもの(module.exports <-> require)
   - vueファイルのscriptsタグでES6を使うにはbabel-loaderも必要ぽい
   - css-loaderを使ってCSS Modulesを使ったり、PostCSSを通してSassを書いたりもできる

## vue-cli

 -　

## dev server

 - webpack dev server
 - vue cliも内部でwebpack dev serverを使っている
 - ホットリロード対応
