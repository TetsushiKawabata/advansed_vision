# advanced_vision
本リポジトリは、アドバンスドビジョンの講義の課題として作成したものです。

## 概要
- 多層パーセプトロンによるニューラルネットワークを用いて、MNIST (手書き数字の画像データセット)の分類をおこなっています。
- 学習をした結果、train accuracyが0.882、test accuracyは0.886を記録しました。

## 実装
このパッケージのコードは、以下のリポジトリを基に作成しています。
- [deep-learning-from-scratch](https://github.com/oreilly-japan/deep-learning-from-scratch)

### 既存リポジトリからの変更点
- 既存のリポジトリと本リポジトリの変更点は以下のようになっています。
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
#### 入力
784次元の画像データ(MNISTの手書き数字)

#### 第一層
第一層は、全結合層であり活性化関数にはシグモイド関数を使用しています。
```math
\mathbf{a}^{(1)} = \mathbf{x}\mathbf{W}^{(1)} + \mathbf{b}^{(1)}
```
```math
\mathbf{z}^{(1)} = \mathrm{sigmoid}\left(\mathbf{a}^{(1)}\right)
```

シグモイド関数の式と、グラフは以下のようになっています。
```math
\mathrm{sigmoid}(x) = \frac{1}{1 + e^{-x}}
```

![シグモイド関数](./img/sigmoid.png)

#### 第二層
第二層も第一層と同様に、全結合層であり活性化関数にはシグモイド関数を使用しています。
```math
\mathbf{a}^{(2)} = \mathbf{x}\mathbf{W}^{(2)} + \mathbf{b}^{(2)}
```
```math
\mathbf{z}^{(2)} = \mathrm{sigmoid}\left(\mathbf{a}^{(2)}\right)
```

### 損失関数


## ライセンス
- 本リポジトリは、MITライセンスの下、公開されています。
- このパッケージのコードは、以下のリポジトリ (MIT License) を基に作成しています。
    - [deep-learning-from-scratch](https://github.com/oreilly-japan/deep-learning-from-scratch)