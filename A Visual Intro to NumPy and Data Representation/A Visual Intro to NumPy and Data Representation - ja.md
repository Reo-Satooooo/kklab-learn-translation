# 図解で理解するNumPyとデータ表現

編集についての議論: [Hacker News (366 points, 21 comments)](https://news.ycombinator.com/item?id=20282985), [Reddit r/MachineLearning (256 points, 18 comments)](https://www.reddit.com/r/MachineLearning/comments/c5nc89/p_a_visual_intro_to_numpy_and_data_representation/)  
翻訳一覧: [中国語 1](http://www.junphy.com/wordpress/index.php/2019/10/24/visual-numpy/), [中国語 2](https://github.com/kevingo/blog/blob/master/ML/visual-numpy.md), [日本語](https://note.mu/sayajewels/n/n95edaedb0fc5), [韓国語](https://chloamme.github.io/2021/12/20/visual-numpy-korean.html)

![](https://jalammar.github.io/images/numpy/numpy-array.png) 

- 翻訳中

```
import numpy as np
```

## Creating Arrays

- 翻訳中

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