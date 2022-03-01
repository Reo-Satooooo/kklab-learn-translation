# 図解で理解する NumPy とデータ表現

編集についての議論: [Hacker News (366 points, 21 comments)](https://news.ycombinator.com/item?id=20282985), [Reddit r/MachineLearning (256 points, 18 comments)](https://www.reddit.com/r/MachineLearning/comments/c5nc89/p_a_visual_intro_to_numpy_and_data_representation/)  
翻訳一覧: [中国語 1](http://www.junphy.com/wordpress/index.php/2019/10/24/visual-numpy/), [中国語 2](https://github.com/kevingo/blog/blob/master/ML/visual-numpy.md), [日本語](https://note.mu/sayajewels/n/n95edaedb0fc5), [韓国語](https://chloamme.github.io/2021/12/20/visual-numpy-korean.html)

![](https://jalammar.github.io/images/numpy/numpy-array.png)


[NumPy](https://www.numpy.org/)パッケージは、Python上で利用可能なデータ分析、機械学習、科学計算に用いるライブラリです。このライブラリは、ベクトルと行列の計算処理を大幅に簡素化します。いくつかのPythonの主要なパッケージは、計算基盤の基礎部分を NumPy に依存しています。（パッケージの例としてscikit-learn, SciPy, pandas, tensorflowがあります。）数値データを細かく分割する機能に加え、NumPy をマスターすることはこれらのライブラリを用いて高度な状況の処理やデバックをすることが可能になります。

この記事では、いくつかの NumPy の主な利用方法と、機械学習モデルに活用する前段階でさまざまな種類のデータ（表、画像、テキストなど）をどのように表現するかについて解説します。

```
import numpy as np
```

## 配列の作成

NumPy配列（通称：[ndarray](https://docs.scipy.org/doc/numpy/reference/arrays.ndarray.html)）は `np.array()` を用いてPythonリストを渡すことで作成できます。この場合,Pythonは以下のように配列を作成します。

![](https://jalammar.github.io/images/numpy/create-numpy-array-1.png)

NumPy に配列の値を初期化してもらいたい場合がよくある。NumPy では、このような場合のために `ones()`, `zeros()`, `random.random()` といったメソッドが用意されています。生成してほしい要素数を渡すだけです。

![](https://jalammar.github.io/images/numpy/create-numpy-array-ones-zeros-random.png)

配列の作成が完了したら、次はそれを使って、面白い方法で、操作ができるようになります。

## 配列の算術演算

NumPy の配列の有用性を示すために、2 つの配列を作成してみましょう。 `data`, `ones`と呼ぶことにする。

![](https://jalammar.github.io/images/numpy/numpy-arrays-example-1.png)

位置的に足し算する（各行の値を足す）には、`data + ones` と入力するだけでよい。

![](https://jalammar.github.io/images/numpy/numpy-arrays-adding-1.png)

このようなツールを学び始めたとき、このような抽象化によって、このような計算をループでプログラムする必要がないことが新鮮に感じられたのです。問題をより高いレベルで考えることができる、素晴らしい抽象化です。

さらに、加算だけではなく以下のように四則演算の全てができます。

![](https://jalammar.github.io/images/numpy/numpy-array-subtract-multiply-divide.png)

配列と一つの数値との演算を行いたい場合がよくある（これをベクトルとスカラとの演算と呼ぶこともある）。例えば、距離を表す配列がマイル単位で、それをキロメートルに変換したいとします。単純に`data * 1.6`と言うだけです。

![](https://jalammar.github.io/images/numpy/numpy-array-broadcast.png)

NumPy がこの操作を、各セルで乗算が起こることを意味すると理解したのがわかるだろうか？その考え方は**ブロードキャスト**と呼ばれ、とても便利なものです。

## インデックス作成

Python のリストをスライスするのと同じように、NumPy の配列をインデックスし、スライスすることができる。

![](https://jalammar.github.io/images/numpy/numpy-array-slice.png)

## 集約関数

NumPy が与えてくれるその他の利点は、集約関数である。

![](https://jalammar.github.io/images/numpy/numpy-array-aggregation.png)

`min`、`max`、`sum`に加えて、平均を求める`mean`のような偉大なもの(集約関数)を手に入れることができます。`prod`は、すべての要素を掛け合わせた結果を得ることができます。`std`は、標準偏差を得られ、その他にもたくさんあります。

## 多次元計算

これまで見てきた例では、すべて 1 次元のベクトルを扱っています。NumPy の美しさの主要な部分は、これまで見てきたすべてを任意の数の次元に適用できることである。

### 行列の作成

Python リストを渡して、NumPy にそれを表す行列を作らせることができます。

```
np.array([[1,2],[3,4]])
```

![](https://jalammar.github.io/images/numpy/numpy-array-create-2d.png)

また、上記で紹介した方法(`ones()`, `zeros()`, `random.random()`)と同じように、作成する行列の次元を表すタプルを与えればよい。

![](https://jalammar.github.io/images/numpy/numpy-matrix-ones-zeros-random.png)

### 行列計算

2 つの行列が同じ大きさであれば，算術演算子 (`+`, `-`, `\`, `*`, `/`) を用いて行列の加算や乗算を行うことができます。NumPy はこれらを位置演算として扱います。

![](https://jalammar.github.io/images/numpy/numpy-matrix-arithmetic.png)

異なるサイズの行列に対してこれらの算術演算を行うことができるのは、異なる次元が 1 つである場合に限られます。（行列が 1 列または 1 行しかない場合など）この場合、NumPy はその操作にブロードキャストルールを使用する。

![](https://jalammar.github.io/images/numpy/numpy-matrix-broadcast.png)

### 内積

算術との違いで重要なのは、ドットプロダクトを使った行列の掛け算の場合です。NumPy では、すべての行列に`dot()`メソッドが用意されており、他の行列との内積演算を行うことができます。

![](https://jalammar.github.io/images/numpy/numpy-matrix-dot-product-1.png)

この図の下に行列の寸法を書き加えているのは、2 つの行列が互いに向き合う側の寸法が同じでなければならないことを強調するためです。この操作は、次のように可視化できます。

![](https://jalammar.github.io/images/numpy/numpy-matrix-dot-product-2.png)

### 行列のインデックス

インデックスやスライスの操作は、行列を操作するときに、さらに便利になります。

![](https://jalammar.github.io/images/numpy/numpy-matrix-indexing.png)

### 行列の集約関数

ベクトルを集約するのと同じように、行列を集約することができる。

![](https://jalammar.github.io/images/numpy/numpy-matrix-aggregation-1.png)

行列のすべての値を集約できるだけでなく、axis パラメータを使用すれば、行や列をまたいで集約することも可能です。

![](https://jalammar.github.io/images/numpy/numpy-matrix-aggregation-4.png)

## 行と列の入れ替え

一般的に行列を扱う際に、行と列を入れ替える必要に迫られる場合があります。これは、2つの行列の内積を取り、それらが共有する次元を整列させる必要があるよくあるケースです。NumPy配列には、行列の転置を取得するためのTと呼ばれる便利な機能が用意されています。

![](https://jalammar.github.io/images/numpy/numpy-transpose.png)

より高度なユースケースとして、特定の行列の次元を切り替える必要がある場合があります。このような場合は、特定のモデルがデータセットとは異なる入力の特定の形状を期待する機械学習アプリケーションにおいてよくあります。NumPyの `reshape（）` メソッドは、このような場合に役立ちます。行列に必要な新しい次元を渡すだけです。次元に-1を渡すと、NumPyは行列に基づいて正しい次元を推測できます。

![](https://jalammar.github.io/images/numpy/numpy-reshape.png)

## より多次元において

NumPyは、これまでに示してきたすべてのことをさまざまな次元で実行できます。このため、その中心的なデータ構造は、ndarray（N-Dimensional Array）と呼ばれます。

![](https://jalammar.github.io/images/numpy/numpy-3d-array.png)

多くの場合、新しい次元を扱う際は、NumPy関数のパラメーターにコンマを追加するだけです。

![](https://jalammar.github.io/images/numpy/numpy-3d-array-creation.png)

注：3次元のNumPy配列を印刷する場合、テキスト出力はここに示されているものとは異なる方法で配列を示すことに注意してください。NumPyがn次元配列を印刷する順序は、最後の軸が最も速くループし、最初の軸が最も遅くなることです。これは、`np.ones（（4,3,2））`が次のように出力されることを意味します。

```
array([[[1., 1.],
        [1., 1.],
        [1., 1.]],

       [[1., 1.],
        [1., 1.],
        [1., 1.]],

       [[1., 1.],
        [1., 1.],
        [1., 1.]],

       [[1., 1.],
        [1., 1.],
        [1., 1.]]])
```

## 実用的な使い方

- さて、見返りを受け取る時です。以下では、NumPyが役立つ便利な事柄の例を幾つか紹介します。

### 数式

- 行列やベクトルで機能する数式を実装する事は、NumPyの使用を検討する重要なユースケースです。NumPyが科学的なPythonコミュニティから気に入られているのはそのためです。例えば、回帰分析に取り組む教師有り学習モデルの中心である、平均二乗誤差の数式について考えてみましょう。

![](https://jalammar.github.io/images/numpy/mean-square-error-formula.png)

- これを実装する事は、NumPyにとっては容易い事です。

![](https://jalammar.github.io/images/numpy/numpy-mean-square-error-formula.png)

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-mse-1.png)

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-mse-2.png)

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-mse-3.png)

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-mse-4.png)

- 翻訳中

### Data Representation

- 翻訳中

#### Tables and Spreadsheets

- - 翻訳中

![](https://jalammar.github.io/images/pandas-intro/0%20excel-to-pandas.png)

#### オーディオと時系列

- オーディオファイルは、サンプルの1次元配列です。各サンプルは、音声信号の小さなチャンク（塊）を表す数値です。CD 品質のオーディオは、1 秒あたり 44,100のサンプルを持ち、各サンプルは-32767～32768の間の整数です。つまり、10秒のCD 品質であるWAVEファイルがある場合は、長さ441,000のサンプルとしてNumPy配列に読み込むことができます。オーディオの最初の秒を抽出したいですか？ただファイルを NumPy 配列にロードすれば、audioaudio[:44100]を得ます。

オーディオファイルの一部を次に示します。

![](https://jalammar.github.io/images/numpy/numpy-audio.png)

時系列データ (例えば、時間経過に伴う株価) も同様です。

#### Images

- - 翻訳中

  - - 翻訳中

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-grayscale-image.png)

- - 翻訳中

  ![](https://jalammar.github.io/images/numpy/numpy-color-image.png)

#### Language

- 翻訳中

- 翻訳中

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-nlp-vocabulary.png)

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-nlp-tokenization.png)

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-nlp-ids.png)

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-nlp-embeddings.png)

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-nlp-bert-shape.png)

- 翻訳中

- 翻訳中
