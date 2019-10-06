---
layout: post
title: Tensorflow를 활용한 신경망 구현하기 
excerpt: "기본적인 것부터 딥러닝 살펴보기"
date: 2019-10-06
tag: 
- deep learning
- tensorflow 
- neural network
---


# 신경망 구조 

![graph](https://user-images.githubusercontent.com/33630505/66269396-d8ab2c80-e882-11e9-9e00-f3b97507db68.png)

<br>
**Multi Layer Neural Networks**
![multi layer](https://user-images.githubusercontent.com/33630505/66271736-b7573a00-e89c-11e9-9563-726d98aee646.JPG)

<br>

# Back Propagation에 필요한 수식

![solv](https://user-images.githubusercontent.com/33630505/66272387-19676d80-e8a4-11e9-99ca-9b0c80896086.png)

<br>

# Tensorflow 

<span style="font-size: 30px; color: orange;">텐서의 흐름</span> <span style="font-size: 30px; color: rgb(255, 21, 116);">&nbsp; => &nbsp;</span><span style="font-size: 30px; color: orange;">벡터 데이터의 흐름</span><br>
**Tensorflow는 벡터 데이터가 흘러 그 데이터를 처리하고 인간의 뇌처럼 작동하는 AI기술인 Deep Learning의 Framework이다.**

<br>

# Tensorflow 작동 방식 

> 텐서플로우는 기본적으로 그래프 기반으로 작동되는 프레임워크 이다. <br>

![tensors_flowing](https://user-images.githubusercontent.com/33630505/66271659-99d5a080-e89b-11e9-80cd-50e0be75b3c0.gif)

출처: [tensorflow](https://www.tensorflow.org/?hl=ko)<br>

```
1. 그래프 생성 
2. 그래프 실행 

그래프 생성 단계에서는 연산 과정을 그래프 형태로 표현한다. 
밑에 그림에서 볼 수 있듯이 
Computational Graph는 Node와 Edge로 이루어진 자료 구조이다. 

Node에는 Operator, Variable, Constant등을 정의하고, node간의 연결인 
edge를 통해 tensor data를 주고받으면서 계산을 할 수 있도록 프로그래밍 한다.

그래프 생성이 끝나면 Session 객체를 통해 생성한 그래프를 실행 할 수 있다. 
```

![Structure](https://user-images.githubusercontent.com/33630505/66271812-727fd300-e89d-11e9-99f1-107c1d7679dc.png)

출처: [gitbooks](https://leonardoaraujosantos.gitbooks.io/artificial-inteligence/content/tensorflow.html)

<br> 

# Tensorflow로 구현하기 

## Tensorflow import 

> Tensorflow를 import하면 그 시점에 비어 있는 기본 graph가 만들어지며, <br>
> 앞으로 작성될 node들은 이 기본 graph에 자동으로 연결된다<br>

```python
import tensorflow as tf 
```

## Data set 

> x는 입력 데이터, y는 결과 데이터 <br>
> 총 데이터 갯수 4개 <br>
> input 값 1개, output 값 1개 <br>

```python
x_data = [1,2,3,4]
y_data = [5,8,11,14]
```

<br>

## Tensor for Data set 

> placeholder는 데이터를 입력받는 비어있는 변수<br>
> 그래프를 구성하고 그래프가 실행되는 시점에 입력 데이터를 넣어주는데 활용된다<br>
> 그리고 placeholder는 shape인수를 유동적으로 지정할 수 있다 <br>


```python
x = tf.placeholder(tf.float32) 
y = tf.placeholder(tf.float32)

type(x) # y도 동일 
: tensorflow.python.framework.ops.Tensor
```

<br>

## Weight & Bias 

> 학습 과정에서 모델의 매개변수로 가중치, 편향치가 입력되는데 <br>
> 이 가중치, 편향치가 최적화되기 위해 Variable이라는 객체를 사용한다 <br> 
> 가중치가 최적화되는 반복 과정에서 현재의 변수가 다음 반복 과정에 영향을 줄 수 <br>
> 있어야 하기 때문에 Variable 객체를 사용한다 <br>

```python
W = tf.Variable([1], dtype=tf.float32) # 가중치, 편향치 모두 경험적으로 1로 세팅했다
b = tf.Variable([1], dtype=tf.float32)
```
**Variable은 학습을 통해 변화하는 배열 값을 저장하기 위한 operation.**

출처: https://webofthink.tistory.com/68 [Web of Think]**

<br>

## Placeholder vs Variable 

> 둘다 변수이긴 변수 인데 variable은 연산이 수행되면서 값이 변하고 <br>
> 다음 연산에 그 값을 유지하고 있어야 하기 때문에 정말 '변하는 수' 같은 느낌이고<br>
> placeholder는 데이터를 담을 공간을 의미하는 변수인거 같다 (확실하지 않음..) <br>

### 1 
```python
set(dir(W)) & set(dir(x)) # 공통점으로 dtype, shape, name 등이 있는걸로 봐서 tensor 객체인것은 공통점

: {'device',
   'dtype',
   'eval',
   'get_shape',
   'graph',
   'name',
   'op',
   'set_shape',
   'shape'}
   
# special method는 제외했음   
```

### 2 
```python
set(dir(W)) - set(dir(x)) # Variable에만 있는 함수와 변수들 

: {'SaveSliceInfo',
   'assign',
   'assign_add',
   'assign_sub',
   'batch_scatter_update',
   'constraint',
   'count_up_to',
   'from_proto',
   'initial_value',
   'initialized_value',
   'initializer',
   'load',
   'read_value',
   'scatter_add',
   'scatter_nd_add',
   'scatter_nd_sub',
   'scatter_nd_update',
   'scatter_sub',
   'scatter_update',
   'to_proto',
   'trainable',
   'value'}
   ```
   
### 3 
```python
set(dir(x)) - set(dir(W)) # placeholder에만 있는 함수와 변수들 

: {'OVERLOADABLE_OPERATORS',
   'consumers',
   'value_index'}
```

<br>

## hypothesis

> 가설값(추측값) = 가중치 X 입력값 + 편향치 <br>
> 가중치를 찾기 위한 함수 혹은 모델 <br>

```python
hypothesis = W * x + b
```

<br>

## cost function 

> (추측값 - 정답)의 제곱의 평균, 즉 내가 추측한 값과 정답 사이의 상관관계를 보기위한 함수<br>
> 이 비용 함수의 목표는 추측값과 정답의 오차를 줄이는 데에 있다<br>
> 앞으로 이 비용 함수의 편미분 값은 가중치 조정 알고리즘에 사용된다<br>

```python 
cost = tf.reduce_mean(tf.square(hypothesis-y))
```

<br>

## optimizer 

> 경사하강법을 사용하기 위한 알고리즘 <br> 
> 이 경사하강법은 비용 함수에서 오차를 최소로 만들기 위해 사용하는 편미분 알고리즘 <br> 

```python 
optimizer = tf.train.GradientDescentOptimizer(learning_rate = 0.1)
# 학습률은 보통 0.1 또는 0.01을 사용한다
# 학습률에 관한 자세한 내용은 추후에 더 공부해보자 
```

<br>

## 가중치 조절 알고리즘

> cost function이 인자로 전달되고 optimizer의 minimize함수를 통해 구현된다<br>
> 이 알고리즘의 목표는 오차가 최소가 되는 지점의 weight와 bias를 구하는 것이다<br> 
> 조정된 가중치 = 가중치 - 학습률 * cost fucntion의 편미분값<br>

```python
train_op = optimizer.minimize(cost)
```

<br>

## session 

> 그래프를 구성한 후 실제 수행을 할때 다양한 실행환경(CPU, GPU, 분산처리)하에서 처리하기 위해<br>
> Client에서 session을 만들어 전달하는 역할을 한다 <br>

```python
sess = tf.Session()
sess.run(tf.global_variables_initializer()) # tensor를 선언하고 초기화 하지 않았기 때문에 
                                            # 초기화를 한 후 실행해야 한다 
```

<br> 

## Epoch 100으로 학습시키기 

```python 
for step in range(100):
    _, cost_val = sess.run([train_op, cost], feed_dict={x: x_data, y: y_data})
    print("Epoch: ",step, "loss: ",cost_val," weight: ", sess.run(W)," bias: ", sess.run(b))

:  Epoch:  0 loss:  41.0  weight:  [4.5]  bias:  [2.2]
   Epoch:  1 loss:  18.415  weight:  [2.1499999]  bias:  [1.4100001]
   Epoch:  2 loss:  8.274352  weight:  [3.72]  bias:  [1.9530001]
   Epoch:  3 loss:  3.721009  weight:  [2.6634998]  bias:  [1.6024001]
   Epoch:  4 loss:  1.6762912  weight:  [3.3670502]  bias:  [1.8501701]
   Epoch:  5 loss:  0.7579173  weight:  [2.8913898]  bias:  [1.696611]
   Epoch:  6 loss:  0.34527153  weight:  [3.2059994]  bias:  [1.8115939]
   Epoch:  7 loss:  0.15970731  weight:  [2.9912033]  bias:  [1.7462754]
   Epoch:  8 loss:  0.076116346  weight:  [3.1312609]  bias:  [1.8014188]
   Epoch:  9 loss:  0.038325354  weight:  [3.0336602]  bias:  [1.7755046]
   Epoch:  10 loss:  0.021112926  weight:  [3.0954175]  bias:  [1.8035736]
   ....
   ....
   ....
   ....
   Epoch:  97 loss:  3.7696707e-05  weight:  [3.004957]  bias:  [1.985426]
   Epoch:  98 loss:  3.5472734e-05  weight:  [3.0048087]  bias:  [1.9858623]
   Epoch:  99 loss:  3.3379514e-05  weight:  [3.0046647]  bias:  [1.9862854] 
```

<span style="font-size: 23px; color: rgb(255, 21, 116)"> loss가 0에 가깝긴 하지만 가중치, 편향치가 3.0046647, 1.9862854인걸로 보아 학습이 살짝 모자라다</span>
<br>

## 학습된 모델로 결과 예측하기 (Epoch 100)

```python 
sess.run(hypothesis, feed_dict={x:5})  # 3*5 + 2 = 17 
sess.run(hypothesis, feed_dict={x:6})  # 3*6 + 2 = 20 

: array([17.00961], dtype=float32)
  array([20.014275], dtype=float32)
```

<br>

## Epoch 1000으로 학습시키기 

```python
sess2 = tf.Session() 
sess2.run(tf.global_variables_initializer())

:  Epoch:  0 loss:  41.0  weight:  [4.5]  bias:  [2.2]
   Epoch:  1 loss:  18.415  weight:  [2.1499999]  bias:  [1.4100001]
   Epoch:  2 loss:  8.274352  weight:  [3.72]  bias:  [1.9530001]
   Epoch:  3 loss:  3.721009  weight:  [2.6634998]  bias:  [1.6024001]
   Epoch:  4 loss:  1.6762912  weight:  [3.3670502]  bias:  [1.8501701]
   Epoch:  5 loss:  0.7579173  weight:  [2.8913898]  bias:  [1.696611]
   Epoch:  6 loss:  0.34527153  weight:  [3.2059994]  bias:  [1.8115939]
   Epoch:  7 loss:  0.15970731  weight:  [2.9912033]  bias:  [1.7462754]
   Epoch:  8 loss:  0.076116346  weight:  [3.1312609]  bias:  [1.8014188]
   Epoch:  9 loss:  0.038325354  weight:  [3.0336602]  bias:  [1.7755046]
   Epoch:  10 loss:  0.021112926  weight:  [3.0954175]  bias:  [1.8035736]
   ....
   ....
   ....
   Epoch:  995 loss:  7.9580786e-13  weight:  [3.000001]  bias:  [1.9999975]
   Epoch:  996 loss:  7.9580786e-13  weight:  [3.000001]  bias:  [1.9999975]
   Epoch:  997 loss:  7.9580786e-13  weight:  [3.000001]  bias:  [1.9999975]
   Epoch:  998 loss:  7.9580786e-13  weight:  [3.000001]  bias:  [1.9999975]
   Epoch:  999 loss:  7.9580786e-13  weight:  [3.000001]  bias:  [1.9999975]
```

<br>

## 학습된 모델로 결과 예측하기 (Epoch 1000)

```python 
sess2.run(hypothesis, feed_dict={x:5})  # 3*5 + 2 = 17 
sess2.run(hypothesis, feed_dict={x:6})  # 3*6 + 2 = 20 

: array([17.000002], dtype=float32)
  array([20.000004], dtype=float32)
```
