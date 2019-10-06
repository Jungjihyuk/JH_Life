---
layout: post
title: tensorflow를 활용한 신경망 구현하기 
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

![solv](https://user-images.githubusercontent.com/33630505/66269409-02fcea00-e883-11e9-8cab-3590e17c9b63.png)


<br>

# Tensorflow 

<span style="font-size: 30px; color: orange;">텐서의 흐름</span> <span style="font-size: 30px; color: rgb(255, 21, 116);">=></span><span style="font-size: 30px; color: orange;">벡터 데이터의 흐름</span><br>
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
> 앞으로 작성될 node들은 이 기본 graph에 자동으로 연결된다

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
> 그리고 placeholder는 shape인수를 유동적으로 지정할 수 있다 


```python
x = tf.placeholder(tf.float32) 
y = tf.placeholder(tf.float32)

type(x) # y도 동일 
: tensorflow.python.framework.ops.Tensor
```

<br>

## Weight & Bias 

> 학습 과정에서 모델의 매개변수로 가중치, 편향치가 입력되는데 <br>
> 이 가중치가 최적화되기 위해 Variable이라는 객체를 사용한다 <br> 
> 가중치가 최적화되는 반복 과정에서 현재의 변수가 다음 반복 과정에 영향을 줄 수 <br>
> 있어야 하기 때문에 Variable 객체를 사용한다 

```python
W = tf.Variable([1], dtype=tf.float32) # 가중치, 편향치 모두 경험적으로 1로 세팅했다
b = tf.Variable([1], dtype=tf.float32)
```

<br>

## Placeholder vs Variable 

> 둘다 변수이긴 변수 인데 variable은 연산이 수행되면서 값이 변하고 <br>
> 다음 연산에 그 값을 유지하고 있어야 하기 때문에 정말 '변하는 수' 같은 느낌이고<br>
> placeholder는 데이터를 담을 공간을 의미하는 변수인거 같다 (확실하지 않음..) 

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

<




