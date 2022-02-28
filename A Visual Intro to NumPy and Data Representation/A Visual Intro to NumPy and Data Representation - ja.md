# 図解で理解するNumPyとデータ表現

編集についての議論: [Hacker News (366 points, 21 comments)](https://news.ycombinator.com/item?id=20282985), [Reddit r/MachineLearning (256 points, 18 comments)](https://www.reddit.com/r/MachineLearning/comments/c5nc89/p_a_visual_intro_to_numpy_and_data_representation/)  
翻訳一覧: [中国語 1](http://www.junphy.com/wordpress/index.php/2019/10/24/visual-numpy/), [中国語 2](https://github.com/kevingo/blog/blob/master/ML/visual-numpy.md), [日本語](https://note.mu/sayajewels/n/n95edaedb0fc5), [韓国語](https://chloamme.github.io/2021/12/20/visual-numpy-korean.html)

![](https://jalammar.github.io/images/numpy/numpy-array.png) 

[NumPy](https://www.numpy.org/)パッケージは、Python上で利用可能なデータ分析、機械学習、科学計算に用いるライブラリです。このライブラリは、ベクトルと行列の計算処理を大幅に簡素化します。いくつかのPythonの主要なパッケージは、計算基盤の基礎部分をNumPyに依存しています。（パッケージの例としてscikit-learn, SciPy, pandas, tensorflowがあります。）数値データを細かく分割する機能に加え、NumPyをマスターすることはこれらのライブラリを用いて高度な状況の処理やデバックをすることが可能になります。

この記事では、いくつかのNumPyの主な利用方法と、機械学習モデルに活用する前段階でさまざまな種類のデータ（表、画像、テキストなど）をどのように表現するかについて解説します。

```
import numpy as np
```

## 配列の作成

NumPy配列（通称：[ndarray](https://docs.scipy.org/doc/numpy/reference/arrays.ndarray.html)）を作成できます。

![](https://jalammar.github.io/images/numpy/create-numpy-array-1.png) 

- 翻訳中

![](https://jalammar.github.io/images/numpy/create-numpy-array-ones-zeros-random.png) 

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

-   - 翻訳中

![](https://jalammar.github.io/images/pandas-intro/0%20excel-to-pandas.png)  

#### Audio and Timeseries

-   - 翻訳中

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-audio.png)  

- 翻訳中

#### Images

-   - 翻訳中
    
    -   - 翻訳中

- 翻訳中

![](https://jalammar.github.io/images/numpy/numpy-grayscale-image.png)  

-   - 翻訳中
    
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