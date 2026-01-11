# advanced_vision
本リポジトリは、アドバンスドビジョンの講義の課題として作成したものです。

## 概要
- 多層パーセプトロンによるニューラルネットワークを用いて、MNIST (手書き数字の画像データセット)の分類をおこなっています。
- 学習をした結果、train accuracyが0.882、test accuracyは0.886を記録しました。

## 実装
このパッケージのコードは、以下のリポジトリを基に作成しています。
- [deep-learning-from-scratch](https://github.com/oreilly-japan/deep-learning-from-scratch)

### 既存パッケージからの変更点
- 既存のパッケージとと本パッケージの変更点は以下のようになっています。
    - 変更前 : 隠れ層が1個のニューラルネットワーク
    - 変更後 : 隠れ層が2個のニューラルネットワーク

### 必要なソフトウェア
- 本リポジトリでは以下のソフトウェアを必要とするため、使用する際は事前のインストールをお願いいたします。
    - Python 3.x
    - NumPy
    - Matplotlib

### 本リポジトリのインストール方法
```
$ git clone https://github.com/TetsushiKawabata/advansed_vision.git
$ cd advansed_vision
```

### 実行方法と実行結果
実行後、以下の学習曲線がresult.pngとして保存されます。
```
$ python train.py
train acc, test acc | 0.09736666666666667, 0.0982
train acc, test acc | 0.10218333333333333, 0.101
train acc, test acc | 0.11236666666666667, 0.1135
(以下略)
```

![学習曲線](./result.png)

## 理論
### モデルの構造
モデルの構造図は以下のようになっています。

<img src="./img/model.png" width="25%">

#### 入力
784次元(28 × 28)の画像データ

#### 第一層 (隠れ層)
第一層は、全結合層であり活性化関数にはシグモイド関数を使用しています。この際、 $\mathbf{W}^{(i)}$ は $\mathbf{i}$ 層目の重みを指し、 $\mathbf{b}^{(i)}$ は $\mathbf{i}$ 層目のバイアスを示しています。また、 $\mathbf{x}$ は入力の画像データを指します。
```math
\mathbf{a}^{(1)} = \mathbf{x}\mathbf{W}^{(1)} + \mathbf{b}^{(1)}
```
```math
\mathbf{z}^{(1)} = \mathrm{sigmoid}\left(\mathbf{a}^{(1)}\right)
```

シグモイド関数の式は、以下のようになっています。
```math
\mathrm{sigmoid}(x) = \frac{1}{1 + e^{-x}}
```

#### 第二層 (隠れ層)
第二層も第一層と同様に、全結合層であり活性化関数にはシグモイド関数を使用しています。
```math
\mathbf{a}^{(2)} = \mathbf{z}^{(1)}\mathbf{W}^{(2)} + \mathbf{b}^{(2)}
```
```math
\mathbf{z}^{(2)} = \mathrm{sigmoid}\left(\mathbf{a}^{(2)}\right)
```

#### 第三層 (出力層)
第三層は、全結合層であり活性化関数にはソフトマックス関数を使用しています。
```math
\mathbf{a}^{(3)} = \mathbf{z}^{(2)}\mathbf{W}^{(3)} + \mathbf{b}^{(3)}
```
```math
\mathbf{y} = \mathrm{softmax}\left(\mathbf{a}^{(3)}\right)
```

ソフトマックス関数の式は、以下のようになっています。
```math
\mathrm{softmax}(x_i) = \frac{e^{x_i}}{\sum_{j=1}^{n} e^{x_k}}
```

#### 出力
0～9の各数字の確率が算出されます。

### 損失関数
損失関数には、交差エントロピー誤差を使用しています。 $\mathbf{t}$ は教師ラベルであり、ワンホットベクトル (1つの要素のみ1となり、それ以外の要素はすべて0となるベクトル)で表されたものです。また、 $\mathbf{K}$ はクラス数を指します。
```math
\mathrm{L}(\mathbf{y}, \mathbf{t}) = - \sum_{k=1}^{K} t_k \log y_k
```

## ライセンス
- 本リポジトリは、MITライセンスの下、公開されています。
- このパッケージのコードは、以下のリポジトリ (MIT License) を基に作成しています。
    - [deep-learning-from-scratch](https://github.com/oreilly-japan/deep-learning-from-scratch)
- © 2026 Tetsushi Kawabata