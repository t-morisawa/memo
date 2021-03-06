
# ディープラーニング

## 概要

 - 基本的にはディープラーニング = 深層学習 = DNNと考えて良い
 - NN（教師あり学習）の現代版。層数・ニューロン数が大きくなったもの。
 - ポイントになるのは入出力の定義とデータ集め。

## 畳み込みニューラルネットワーク(CNN)とは

 - 従来のNNに畳み込み層とプーリング層が追加されたもの
 - 従来のNNは各層が全結合関数・活性化関数で構成されるが、CNNは畳み込み関数・プーリング関数・活性化関数で構成される
 - 現代のDLは基本的にCNNを利用している

## オートエンコーダとは

 - 3層ニューラルネットにおいて、入力層と出力層に同じデータを用いて教師あり学習させたものである。

## オートエンコーダとDeep Learningの関係
 - DLの歴史的な背景として、単純に層を増やして誤差逆伝播するだけでは精度が上がらなかった。
 - そこでDLの中間層を学習ずみのオートエンコーダとして設定することでこの問題を解決した（事前学習）
 - 現在は事前学習なしでも精度の高い学習ができるようになっている。
 - 一方でオートエンコーダの中間層〜出力層を「出力モデル」と呼び、適切な中間層入力から出力を生成するのに使われたりもする。
   - DLによる画像生成・音声生成などの話はこれが関係している。
 - https://deepage.net/deep_learning/2016/10/09/deeplearning_autoencoder.html

## 教師なし学習
 - データの背後に存在する本質的な構造を抽出するために用いる学習。「出力すべきもの」があらかじめ決まっていない。
 - キーワード: クラスタリング、オートエンコーダ、データマイニング、主成分分析、自己組織化マップ
