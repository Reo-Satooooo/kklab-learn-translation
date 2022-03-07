# 図解で理解する基本のニューラルネットワーク数学

[以前の記事では](https://jalammar.github.io/visual-interactive-guide-basics-neural-networks/)ニューラルネットワークの基本的な概念を解説しました。では、ニューラルネットワークを用いた予測の基礎となる数学的考え方を説明するためにいくつか別の例を見ていきましょう。

 [![some of the basic mathematical ideas involved in prediction with neural networks](https://jalammar.github.io/images/two-input-one-output-sigmoid-network.png)](https://jalammar.github.io/images/titanic_nn_calculation.mp4 "some of the basic mathematical ideas involved in prediction with neural networks")
 - 上記画像には動画がリンクされています。

もしあなたがタイタニック号に乗船していて、沈没から生き延びるにはどうしたでしょうか？生存確率の予測モデルを立てたのではないでしょうか。

これは[以前の記事](https://jalammar.github.io/visual-interactive-guide-basics-neural-networks/)で論じた内容に基づいて構築したニューラルネットワークモデルになります。ただし隠れた階層と活性化関数を利用するため、予測精度が高くなります。

今回利用するデータセットはKaggleのタイタニック号の乗船客リストになります。リストには乗船客の氏名とその他の情報や乗船客が沈没からどのように生き延びたか、または生き延びることができなかったかについて示されています。
The dataset we’ll use this time will be the Titanic passenger list from Kaggle. It lists the names and other information of the passengers and shows whether each passenger survived the sinking event or not.

実際のデータセットは以下のようになっています:

| PassengerId | Survived | Pclass | Name | Sex | Age | SibSp | Parch | Ticket | Fare | Cabin | Embarked |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | 0 | 3 | Braund, Mr. Owen Harris | male | 22.0 | 1 | 0 | A/5 21171 | 7.2500 | NaN | S |
| 2 | 1 | 1 | Cumings, Mrs. John Bradley (Florence Briggs Th… | female | 38.0 | 1 | 0 | PC 17599 | 71.2833 | C85 | C |
| 3 | 1 | 3 | Heikkinen, Miss. Laina | female | 26.0 | 0 | 0 | STON/O2. 3101282 | 7.9250 | NaN | S |

現時点で大半の列については気にしないでください。特徴量として性別と年齢の列を利用し、生存を予測します。

| Age | Sex | Survived? |
| --- | --- | --- |
| 22 | 0 | 0 |
| 38 | 1 | 1 |
| 26 | 1 | 1 |
| … 891 rows total |

乗船客が生き延びたかどうかについての予測をするネットワークを構築します。

ニューラルネットワークは入力に数値が必要です。ですので性別の列を男性は「0」、女性は「1」に変換します。お気づきかも知れませんが、同様に生存の列を生き延びたを「1」、生き延びなかったを「0」に変換します。

この予測を作成するための単純なニューラルネットワークは以下のようになります:

![neural netowrk with two inputs, one output, and sigmoid output activation](https://jalammar.github.io/images/two-input-one-output-sigmoid-network.png)予測演算は「年齢」と「性別」の値を組み込むことでなされます。その演算は左から右へと行われます。ただし、予測にこのネットワークを使用する前に、値に重み（W）とバイアス（b）を与える「学習」プロセスを実行しなければなりません。
注: 以前の記事からネットワークの表現を少し変更しました。詳しくはバイアスノードを以下のように以下のように置き換えました。

では、このネットワークを構成する要素とそれらがどのように機能するのかまとめてみましょう:

![input neuron](https://jalammar.github.io/images/input-neuron.png)

入力ニューロンは（人の年齢などの）値の入力を行う部分です。そこから演算が始まります。外向きの矢印とその他の図は予測演算を行うために必要なその他の計算を示しています。

![weighted neuron image](https://jalammar.github.io/images/weight.png)

矢印上に重みがある場合、値が通過する際に重みが乗算されます。

```
connection_output = weight * connection_input
接点の出力 = 重み * 接点の入力
```

![ neuron image](https://jalammar.github.io/images/neuron.png)

ニューロンに入力がある場合、それらは加算され、合計は外向き矢印の方向に出力されます。

```
ノードの出力 = 入力_1 + 入力_2
node_output = input_1 + input_2
```

### Sigmoid [#](https://jalammar.github.io/feedforward-neural-networks-visual-interactive/#sigmoid)

![sigmoid neuron](https://jalammar.github.io/images/sigmoid-neuron.png)

To turn the network’s calculation into a probability value between 0 and 1, we have to pass the value from the output layer through a “sigmoid” formula. Sigmoid squashes the output value of a neuron to between 0 and 1 according to a specific curve.

f(x)= 11+e−x\\frac{1}{1 + e^{-x}}

Where e is the mathematical constant approximately equal to 2.71828

```
def sigmoid(x):
    return 1/(1 + math.exp(-x))

output = sigmoid(value)
```

### Sigmoid Visualization [#](https://jalammar.github.io/feedforward-neural-networks-visual-interactive/#sigmoid-visualization)

<table><tbody><tr><td>0</td><td><img src="https://jalammar.github.io/images/sigmoid-neuron.png"></td><td>0.50000000000</td></tr></tbody></table>

Interact a little with sigmoid to see how it transforms various values

f(0) = 11+e−x\\frac{1}{1 + e^{-x}} = 0.50000000000

\-20\-15\-10\-5051015200.00.51.0Output0.50000000000

![weighted neuron image](https://jalammar.github.io/images/two-input-one-output-sigmoid-network.png)

To bring it all together, calculating a prediction with this shallow network looks like this:

```
def sigmoid(x):
    return 1/(1 + math.exp(-x))

def calculate_prediction(age, sex, weight_1, weight_2, bias):

    # Multiply the inputs by their weights, sum the results up
    layer_2_node = age * weight_1 + sex * weight_2 + 1 * bias

    prediction = sigmoid(layer_2_node)
    return prediction
```

Now that we know the structure of our network, we can train it using \[gradient descent\] running on the first 600 rows of the 891-row dataset. I will not be addressing the training process in this post because that’s a separate concern at the moment. For now, I just want you to be comfortable with how a trained network calculates a prediction. Once you get this intuition down, we’ll proceed to training in a future post.

The training process gives us the following values (with an accuracy of 73.20%):

```
weight_1 =   -0.016852 # Associated with "Age"
weight_2 =   0.704039  # Associated with "Sex" (where male is 0, female is 1)
bias =       -0.116309
```

Intuitively, the weights indicate how much their associated property contribute to the prediction – odds of survival improve the younger a person is (since a larger age multiplied by the negative weight value gives a bigger negative number). They improve more if the person is female.

### Prediction Calculation [#](https://jalammar.github.io/feedforward-neural-networks-visual-interactive/#prediction-calculation)

The trained network now looks like this: (hover or click on values in the table to see their individual predictions)

|  | Age | Sex | Survived |
| --- | --- | --- | --- |
|  | 22 | 0 | 0 |
|  | 38 | 1 | 1 |
|  | 26 | 1 | 1 |
|  | 35 | 1 | 1 |
|  | 35 | 0 | 0 |
|  | 14 | 1 | 0 |
|  | 25 | 0 | 0 |
|  | 54 | 0 | 0 |

SurvivedAgeSexBias\-0.01690.704\-0.1163σ

An accuracy of 73.20% isn’t very impressive. This is a case that can benefit from adding a hidden layer. Hidden layers give the model more capacity to represent more sophisticated prediction functions that may do a better job ([Deep Learning ch.5 page 113](http://www.deeplearningbook.org/contents/ml.html)).

![weighted neuron with activation](https://jalammar.github.io/images/neuron_with_activation.png)

It’s often useful to apply certain math functions to the weighted outputs. These are called “activation functions” because historically they translated the output of the neuron into either 1 (On/active) or 0 (Off).

```
def activation_function(x):
    # Do something to the value
    ...

weighted_sum = weight * (input_1 + input_2)
output = activation_function(weighted_sum)
```

Activation functions are vital for hidden layers. Without them, deep networks would be no better than a shallow linear network. Read the “Commonly used activation functions” section from [Neural Networks Part 1: Setting up the Architecture](https://cs231n.github.io/neural-networks-1/) for a look at various activation functions.

### ReLU [#](https://jalammar.github.io/feedforward-neural-networks-visual-interactive/#relu)

![weighted neuron with activation](https://jalammar.github.io/images/relu.png)

A leading choice for activation function is called ReLU. It returns 0 if its input is negative, returns the number itself otherwise. Very simple!

f(x) = max(0, x)

```
# Naive scalar relu implementation. In the real world, most calculations are done on vectors
def relu(x):
    if x < 0:
        return 0
    else:
        return x


output = relu(value)
```

### ReLU Visualization [#](https://jalammar.github.io/feedforward-neural-networks-visual-interactive/#relu-visualization)

<table><tbody><tr><td>0</td><td><img src="https://jalammar.github.io/images/relu.png"></td><td>0</td></tr></tbody></table>

Interact a little with relu to see how it transforms various values

f(0) = max( 0, 0.00) = 0

\-20\-15\-10\-50510152002468101214161820Output0

## Closing

This post has been parked for more than a year. I had attempted to visualize a deeper network after this point, but that never materialized. I hope you enjoyed it. Let me know on [@JayAlammar on Twitter](https://twitter.com/JayAlammar) if you have any feedback.