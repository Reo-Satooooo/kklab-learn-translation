# 図解で理解する NumPy とデータ表現

編集についての議論: [Hacker News (366 points, 21 comments)](https://news.ycombinator.com/item?id=20282985), [Reddit r/MachineLearning (256 points, 18 comments)](https://www.reddit.com/r/MachineLearning/comments/c5nc89/p_a_visual_intro_to_numpy_and_data_representation/)  
翻訳一覧: [中国語 1](http://www.junphy.com/wordpress/index.php/2019/10/24/visual-numpy/), [中国語 2](https://github.com/kevingo/blog/blob/master/ML/visual-numpy.md), [日本語](https://note.mu/sayajewels/n/n95edaedb0fc5), [韓国語](https://chloamme.github.io/2021/12/20/visual-numpy-korean.html)

![](https://jalammar.github.io/images/numpy/numpy-array.png)

NumPy パッケージは、Python エコシステムにおけるデータ解析、機械学習、科学計算の主力製品です。ベクトルや行列の操作や計算を大幅に簡素化することができます。Python の主要なライブラリのいくつかは、インフラの基本的な部分として NumPy に依存しています（例：scikit-learn、SciPy、pandas、および tensorflow）。数値データを切り刻む能力だけでなく、Numpy をマスターすることで、これらのライブラリで高度なユースケースを扱い、デバッグする際に有利になります。

この記事では、NumPy の主な使用方法と、機械学習モデルに提供する前にさまざまな種類のデータ（表、画像、テキスト...など）を表現する方法について見ていきます。

```
import numpy as np
```

## 配列の作成

Python のリストを渡して ` np.array()` を使えば、NumPy の配列（別名、_強大な_ ndarray）を作成することができます。この場合、python は右のような配列を作成します。

![](https://jalammar.github.io/images/numpy/create-numpy-array-1.png)

NumPy に配列の値を初期化してもらいたい場合がよくある。NumPy では、このような場合のために `ones()`, `zeros()`, `random.random()` といったメソッドが用意されています。生成してほしい要素数を渡すだけです。

![](https://jalammar.github.io/images/numpy/create-numpy-array-ones-zeros-random.png)

配列の作成が完了したら、次はそれを使って、面白い方法で、操作ができるようになります。

## Array Arithmetic

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-arrays-example-1.png)

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-arrays-adding-1.png)

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-array-subtract-multiply-divide.png)

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-array-broadcast.png)

- 翻訳中

## Indexing

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-array-slice.png)

## Aggregation

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-array-aggregation.png)

- 翻訳中

## In more dimensions

- 翻訳中

### Creating Matrices

- 翻訳中

```
np.array([[1,2],[3,4]])
```

![](https://jalammar.github.io/images/numpy/numpy-array-create-2d.png)

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-matrix-ones-zeros-random.png)

### Matrix Arithmetic

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-matrix-arithmetic.png)

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-matrix-broadcast.png)

### Dot Product

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-matrix-dot-product-1.png)

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-matrix-dot-product-2.png)

### Matrix Indexing

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-matrix-indexing.png)

### Matrix Aggregation

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-matrix-aggregation-1.png)

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-matrix-aggregation-4.png)

## Transposing and Reshaping

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-transpose.png)

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-reshape.png)

## Yet More Dimensions

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-3d-array.png)

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-3d-array-creation.png)

- 翻訳中

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

## Practical Usage

- 翻訳中

### Formulas

- 翻訳中

![](https://jalammar.github.io/images/numpy/mean-square-error-formula.png)

- 翻訳中

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

#### Audio and Timeseries

- - 翻訳中

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-audio.png)

- 翻訳中

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
