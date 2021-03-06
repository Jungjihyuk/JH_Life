---
layout: post
title: 밑바닥부터 시작하는 딥러닝
date: 2019-11-03
excerpt: "'Deep Learning from Scratch - 밑바닥부터 시작하는 딥러닝 -'책 정리하기"
tag:
- python
- deep learning
---


# Index 

```
1. Chapter 2 "Perceptron"
2. Chapter 3 "신경망"
3. Chapter 4 "신경망 학습"
```
<br> 

<span style="font-size: 20px; background: rgb(36, 54, 76); color: white; padding: 2px;">Navigation</span> <br>
[<span style="font-size: 18px; background: rgb(76, 217, 229); color: white; padding: 2px;">Perceptron</span>](#1st) &nbsp;
[<span style="font-size: 18px; background: rgb(30, 219, 173); color: white; padding: 2px;">신경망</span>](#2nd) &nbsp;
[<span style="font-size: 18px; background: rgb(226, 71, 0); color: white; padding: 2px;">신경망 학습</span>](#3rd) &nbsp;

<hr>

<a id="1st"></a>
# Chapter 2 "Perceptron" 

<br>

## AND Gate Python으로 구현하기 

```python
# 내가 만든 
def and1(x1:int, x2:int)->int:
    return x1*x2

def and3(x1:int, x2:int)->int:
    x = np.array([x1, x2])
    w = np.array([0.5, 0.5])
    b = -0.7
    temp = np.sum(x*w) + b
    return (lambda x:1 if 1/(1 + np.exp(-x)) > 0.5 else 0)(temp)
    
# 책 내용 변형 
def and2(x1:int, x2:int)->int:
    w1, w2, threshold = 0.5, 0.5, 0.7
    temp = x1*w1 + x2*w2 
    if temp > threshold:
        return 1
    else:
        return 0
        
%%timeit
and1(0,0)
138 ns ± 11.7 ns per loop (mean ± std. dev. of 7 runs, 10000000 loops each)

%%timeit 
and2(0,0)
413 ns ± 53 ns per loop (mean ± std. dev. of 7 runs, 1000000 loops each)

%%timeit
and3(0,1)
12.8 µs ± 389 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)
```

<br>

## OR Gate Python으로 구현하기 

```python
# 내가 만든  
def or1(x1:int, x2:int)->int:
    return (lambda x1, x2: 1 if x1+x2 > 0 else 0)(x1, x2)
    
def or4(x1:int, x2:int)->int:
    x = np.array([x1, x2])
    w = np.array([0.5, 0.5])
    b = -0.1
    temp = np.sum(w*x) + b
    return (lambda x: 1 if 1/(1 + np.exp(-x)) > 0.5 else 0)(temp)
    
# 책 내용 변형
def or2(x1:int, x2:int)->int:
    w1, w2, threshold = 0.5, 0.5, 0.2
    temp = x1*w1 + x2*w2 
    if temp > threshold:
        return 1
    else:
        return 0

import numpy as np

def or3(x1:int, x2:int)->int:
    x = np.array([x1, x2])
    w = np.array([0.5, 0.5])
    b = -0.2
    temp = np.sum(w*x) + b
    if temp > 0:
        return 1
    else:
        return 0
        
%%timeit
or1(0,0)      
385 ns ± 68.5 ns per loop (mean ± std. dev. of 7 runs, 1000000 loops each)

%%timeit
or1(0,1)
418 ns ± 43.6 ns per loop (mean ± std. dev. of 7 runs, 1000000 loops each)

%%timeit
or2(0,0)
501 ns ± 40 ns per loop (mean ± std. dev. of 7 runs, 1000000 loops each)

%%timeit
or2(0,1)
379 ns ± 43.4 ns per loop (mean ± std. dev. of 7 runs, 1000000 loops each)

%%timeit
or3(0,0)
9.47 µs ± 583 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)

%%timeit
or3(0,1)
9.74 µs ± 588 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)

%%timeit
or4(0,0)
13.9 µs ± 1.57 µs per loop (mean ± std. dev. of 7 runs, 10000 loops each)
```

<br>

## XOR Gate Python으로 구현하기 

```python
def and1(x1:int, x2:int)->int:
    x = np.array([x1, x2])
    w = np.array([0.5, 0.5])
    b = -0.7
    temp = np.sum(x*w) + b
    return (lambda x:1 if 1/(1 + np.exp(-x)) > 0.5 else 0)(temp)

def or1(x1:int, x2:int)->int:
    x = np.array([x1, x2])
    w = np.array([0.5, 0.5])
    b = -0.1
    temp = np.sum(w*x) + b
    return (lambda x: 1 if 1/(1 + np.exp(-x)) > 0.5 else 0)(temp)

def nand(x1:int, x2:int)->int:
    x = np.array([x1, x2])
    w = np.array([-0.5, -0.5])
    b = 0.7
    temp = np.sum(x*w) + b
    return (lambda x:1 if 1/(1 + np.exp(-x)) > 0.5 else 0)(temp)
    
def xor(x1:int, x2:int)->int:
    s1 = nand(x1,x2)
    s2 = or1(x1,x2)
    result = and1(s1,s2)
    return result

%%timeit
xor(0,1)
40.7 µs ± 4.55 µs per loop (mean ± std. dev. of 7 runs, 10000 loops each)
```
<br>

<hr>

<a id="2nd"></a>
# Chapter 3 "신경망"

<br>

## 활성화 함수 

> 신호의 총 합을 출력 신호로 변환하는 함수 

<br> 

### 단층 퍼셉트론에서 사용하는 Step Function 

```python 
import numpy as np 
import matplotlib.pyplot as plt

def step(x):
    y = x > 0 
    return y.astype(np.int)

x = np.arange(-10, 10, 1) 
y = step(x)
plt.plot(x, y)
plt.show()
```

![step](https://user-images.githubusercontent.com/33630505/68103497-6b8ac580-ff1a-11e9-9b10-7b83912d064f.JPG)
<br>

### Sigmoid Function 

```python
import numpy as np 
import matplotlib.pyplot as plt

def sigmoid(x):
    return 1 / (1 + np.exp(-x))

x = np.arange(-10, 10, 1) 
y = sigmoid(x)
plt.plot(x, y)
plt.show()
```
![sigmoid](https://user-images.githubusercontent.com/33630505/68103521-79d8e180-ff1a-11e9-8aa6-cd8c23ec31c8.JPG)

<br>

### Relu Function 

```python
import numpy as np 
import matplotlib.pyplot as plt

def relu(x):
    return np.maximum(0, x)

x = np.arange(-10, 10, 1) 
y = relu(x)
plt.plot(x, y)
plt.show()
```
![relu](https://user-images.githubusercontent.com/33630505/68103558-adb40700-ff1a-11e9-91ba-3e00f6e486d2.JPG)

<br>

### Hyperbolic Tangent Function 

> sigmoid보다 output 값의 범위가 넓어 vanishing gradient 문제가 발생할 가능성이 있는 모델에서 사용한다.<br>
> 하지만 여전히 층이 많이 깊어지면 vanishing gradient 문제를 피할 수는 없다. 
<br>

![tanh](https://user-images.githubusercontent.com/33630505/70371772-c8630c80-191a-11ea-8ec7-8302070c9654.JPG)
![tanh func](https://user-images.githubusercontent.com/33630505/70371778-d153de00-191a-11ea-8aed-cc8b1ef1e4ea.JPG)

[그림 출처](http://taewan.kim/post/tanh_diff/) 
<br>

```python 
import numpy as np 
import matplotlib.pyplot as plt

def sigmoid(x):
    return 1 / (1 + np.exp(-x))

def tanh(x):
    return 2*sigmoid(2*x) - 1

x = np.arange(-10, 10, 0.1) 
y = tanh(x)
plt.plot(x, y)
plt.show()
```

![tanh plot](https://user-images.githubusercontent.com/33630505/70371764-a9fd1100-191a-11ea-9f8e-ea7d37267f19.JPG)

<br>


## 선형 VS 비선형

> 중첩의 원리가 적용되면 선형! 적용되지 않으면 비선형! 

<br>

### 입력값 각각을 함수에 대입한 결과의 합과 

```
y = ax1 + bx2 일때 

if x1, x2 => 1, 2 
y1 = a + 2b 

if x1, x2 => 5, 10 
y2 = 5a + 10b 

y = y1 + y2 
  = 6a + 12b 
```
<br>

### 입력값의 합을 함수에 대입한 결과가 서로 같다면 

```
y = ax1  + bx2 일때

if x1, x2 => (1+5), (2+10)
y = 6a + 12b 
```
<br> 

<span style="color: #fe8559; font-size: 30px">바로! 중첩의 원리가 적용되는 것!</span><br>
<br> 

## 신경망에서는 활성화함수로 비선형 함수를 사용하는 이유는? 

```
활성화 함수를 f(x) = ax 라고 했을 때 

Layer가 3개인 다층 신경망을 식으로 나타내면 
y = f(f(f(x)))가 됩니다

그런데 이는 y = a*a*a*x와 같고 하나의 선형 함수로 표현할 수 있기 때문에 
층을 아무리 깊게 해도 아무 의미가 없게 됩니다. 
```
<br> 

## 행렬 곱연산 VS dot VS matmul 


<br>
**행렬 곱연산(Element wise, 일반적인 행렬 곱셈과 다름)**

```python 
n = np.array([1,2])
m = np.array([[[1,2],[3,4]]])

n*m 
: array([[[1, 4],
        [3, 8]]])
        
m*n
: array([list([1, 2, 3, 4, 5]), list([3, 4, 5, 6, 3, 4, 5, 6])],
      dtype=object)
      
 
n = np.array([1,2])
m = np.array([[1,2,3,4,5],[3,4,5,6]])

n*m
: array([list([1, 2, 3, 4, 5]), list([3, 4, 5, 6, 3, 4, 5, 6])],
      dtype=object)
      
m*n
: array([list([1, 2, 3, 4, 5]), list([3, 4, 5, 6, 3, 4, 5, 6])],
      dtype=object)

n = np.array([1,2])
m = np.array([[[1,2,3],[3,4,5]]])

n*m
: ValueError: operands could not be broadcast together with shapes (2,) (1,2,3) 
```
<br>

**dot(Element wise의 합, 내적)**

```python
import numpy as np

g = np.array([[1,2],[1,2]])
h = np.array([2,3])

np.dot(g,h)
: array([8, 8])

i = np.array([[1],[2],[3]])
j = np.array([1,2,3]).reshape(1,3)

np.dot(i,j)
: array([[1, 2, 3],
       [2, 4, 6],
       [3, 6, 9]])
 
# 3차원부터 matmul과 차이난다 
A = np.arange(24).reshape(2,3,4)
B = np.arange(24).reshape(2,4,3)

np.dot(A,B)
: array([[[[  42,   48,   54],
         [ 114,  120,  126]],

        [[ 114,  136,  158],
         [ 378,  400,  422]],

        [[ 186,  224,  262],
         [ 642,  680,  718]]],


       [[[ 258,  312,  366],
         [ 906,  960, 1014]],

        [[ 330,  400,  470],
         [1170, 1240, 1310]],

        [[ 402,  488,  574],
         [1434, 1520, 1606]]]])
```
<br>

**matmul(@, 행렬 곱셈(matrix multiplication))**

```python
g = np.array([[1,2],[1,2]])
h = np.array([2,3])

np.matmul(g,h)
: array([8, 8])

i = np.array([[1],[2],[3]])
j = np.array([1,2,3]).reshape(1,3)

np.matmul(i,j)
: array([[1, 2, 3],
       [2, 4, 6],
       [3, 6, 9]])
       
# 3차원부터 dot과 차이가 난다 
A = np.arange(24).reshape(2,3,4)
B = np.arange(24).reshape(2,4,3)

np.matmul(A,B)
: array([[[  42,   48,   54],
        [ 114,  136,  158],
        [ 186,  224,  262]],

       [[ 906,  960, 1014],
        [1170, 1240, 1310],
        [1434, 1520, 1606]]])

        
g @ h 
: array([8,8])

i @ j 
: array([[1, 2, 3],
       [2, 4, 6],
       [3, 6, 9]])

A @ B
: array([[[  42,   48,   54],
        [ 114,  136,  158],
        [ 186,  224,  262]],

       [[ 906,  960, 1014],
        [1170, 1240, 1310],
        [1434, 1520, 1606]]])
```
<br>

**dot과 matmul** dot은 내적을, matmul은 행렬의 곱을 의미하는데 3차원, 3차원 연산부터 값이 서로 상의 하게 나온다. 내적의 의미는 서로 다른 두 벡터의 방향성을 알 수 있는 연산값이지만 행렬의 곱의 의미는 무엇일까..? 왜 3차원 부터 다른것일까? 아는 사람은 메일 주세요 ㅠ 
{: .notice}

<br>

## 내적(inner product) 

> 방향이 있는 서로 다른 두 벡터가 있을 때 <br>
> 한 벡터를 기준으로 같은 방향이 되도록 다른 한 벡터를 정사영시켜 <br>
> 기준 벡터의 크기와 정사영시켜 생긴 벡터의 크기의 곱이다. <br>
> 즉, 한쪽 방향으로의 크기의 곱! 
<br>
![innerproduct](https://user-images.githubusercontent.com/33630505/68277234-1d102f00-00b2-11ea-8704-d603090c1c6c.JPG)
![innerproduct2](https://user-images.githubusercontent.com/33630505/68277266-2b5e4b00-00b2-11ea-9b1f-3b5ac13758e5.JPG)

<span style="color: #fe8559; font-size: 30px">내적을 구하면 두 벡터의 방향이 얼마나 일치하는지 알 수 있다!</span><br>


<br>

## 다층 신경망 구현하기(3층 신경망 또는 2층 신경망)

![threelayer](https://user-images.githubusercontent.com/33630505/68211627-43cf5680-001b-11ea-80fe-1b7d59955ca9.JPG)
<br>

### version 1 
```python
import numpy as np 

def sigmoid(x):
    return 1 / (1 + np.exp(-x))

def identity_function(x):
    return x

X = np.array([1.0, 0.5])
W1 = np.array([[0.1, 0.3, 0.5], [0.2, 0.4, 0.6]])
B1 = np.array([0.1,0.2,0.3])

L1 = np.dot(X, W1) + B1 
Z1 = sigmoid(L1)

W2 = np.array([[0.1, 0.4], [0.2, 0.5], [0.3, 0.6]])
B2 = np.array([0.1, 0.2]) 

L2 = np.dot(Z1, W2) + B2 
Z2 = sigmoid(L2) 

W3 = np.array([[0.1, 0.3], [0.2, 0.4]])
B3 = np.array([0.1, 0.2]) 

A3 = np.dot(Z2, W3) + B3 
Y = identity_function(A3)
```
<br>

### version 2
```python
import numpy as np 

def sigmoid(x):
    return 1 / (1 + np.exp(-x))

def identity_function(x):
    return x
    
def init_network():
    network = { } 
    network['W1'] = np.random.random((2, 3))
    network['b1'] = np.random.random((1, 3))
    network['W2'] = np.random.random((3, 2))
    network['b2'] = np.random.random((2))
    network['W3'] = np.random.random((2, 2))
    network['b3'] = np.random.random((2))
    
    return network

def forward(network, X):
    W1, W2, W3 = network['W1'], network['W2'], network['W3']
    b1, b2, b3 = network['b1'], network['b2'], network['b3']
    
    L1 = np.dot(X, W1) + b1  # hidden layer
    z1 = sigmoid(L1)
    
    L2 = np.dot(L1, W2) + b2 # hidden layer
    z2 = sigmoid(L2)
    
    L3 = np.dot(L2, W3) + b3 # output layer 
    y = identity_function(L3)
    
    return y
 
network = init_network()
x = np.array([0.1, 0.5])
y = forward(network, x)
print(y) 
```
<br>

## 출력층 설계하기 

> 우선 학습의 결과값으로 유한개의 결과가 나오는가 무한개의 결과가 나오는가 판별해야 합니다 <br>
> 유한개의 결과가 나온다면 분류 문제 (몇개로 분류되는지도 생각해봐야 함) <br>
> 무한개의 결과가 나온다면 회귀 문제 <br>

<span style="color: #fe8559; font-size: 30px">결과값을 달리 해야 하기 때문에 출력층에서 사용하는 활성화 함수도 분류 문제인지, 회귀 문제인지에 따라 달라져야 합니다.</span>

<br>

## 기계학습은 학습과 추론 두 단계를 거친다(backward propagation & forward propagation) 

```
추론 => 지금의 사고방식(가설함수, 모델)로 예측하는 것 
학습 => 예측한 값과 현실의 답(실제값)의 차이를 줄여나가면서 
        기존의 사고방식(가설함수의 가중치 및 하이퍼파라미터)을 업데이트
        
문제를 해결할 때 
사람은 어떤 현상을 보고 패턴을 찾고, 문제에 대한 질문을 생각하고, 답을 찾으며 경험과 직관으로 답을 찾는 반면 
기계는 어떤 현상을 인식하기 위해 데이터를 입력 받고, 패턴을 찾기 위해 데이터에서 중요한 데이터를 찾는 과정인 
특징을 추출하고 그 특징의 패턴을 찾아 모델을 만듭니다.

그런데 어떠한 데이터를 벡터로 변환해야 할때 
변환을 위해 사용되는 특징은 여전히 사람이 설계해야 합니다. 

따라서 문제에 따라서 사람이 적절한 특징을 생각해내야 합니다. 
=> 문제를 해결하려는 도메인의 지식이 중요한 이유!
```
<br>

## 사람 VS 기계학습 VS 딥러닝 

> 딥러닝은 기계학습의 일종이지만 학습을 하는데 있어서 조금 차이를 보입니다. 

<br>

```
ex) 숫자 5를 학습하는 법 

사람 => 경험, 직관, 신념, 사고방식 등... => 숫자 5구나!? 
기계학습 => 사람이 생각한 특징(전처리 등..) => SVM, KNN 등 알고리즘 사용 => 숫자 5구나!? 
딥러닝 => 기계가 데이터를 통해 특징 추출까지 직접 함 => 숫자 5구나!? 
```
<br> 

### 분류 

> 이중 분류라면 step function이나 sigmoid 다중 분류라면 softmax (step, sigmoid, softmax이외에 다른 함수가 될 수도 있다)<br>
> ex) 0 ~ 9사이의 숫자중 어느 하나를 분류해야하는 문제가 있다고 한다면 출력층의 노드의 수는 10개가 되고 <br>
> 2개 이상의 분류이기 때문에 softmax같은 활성화 함수를 활용해 10개의 출력을 하되 마지막에는 가장 확률이 높은 값 하나만을 출력하면 된다

<br>
**step, sigmoid는 많이 다뤘으므로 softmax를 알아보자**
```python
def softmax(x):
    op = np.max(x)  # 오버플로우가 발생 방지 
    x = x - op
    exp = [np.exp(i) for i in x]
    sum_exps = sum(exp)
    return [j/sum_exps for j in exp]
```

**softmax 계산시 오퍼플로우 문제** softmax에 709이상의 입력값을 대입하면 오버플로우 현상이 발생한다. 따라서 오버플로우를 방지하기 위해서 입력값중 가장 큰 값을 뽑아 대입하는 값에 각각을 빼주고 계산하게 되면 각각의 값에 전부 같은 값을 빼주었기 때문에 softmax의 결과는 달라지지 않고 출력됨을 확인할 수 있다. softmax는 발생확률 값을 리턴하기 때문에 출력값의 총 합이 1이되기만 하면 된다. 
{: .notice}

<br>

### MNIST 데이터 셋으로 추론 처리 구현하기(분류)

> test data로 이미 학습된 모델(pickle) 정확도 확인하기 (test data의 예측값과 test data의 실제값 비교) 

```python 
import pickle
import numpy as np
import sys, os
sys.path.append(os.pardir) # 부모 디렉터리의 파일을 가져올 수 있도록 설정
from dataset.mnist import load_mnist

def sigmoid(x):
    return 1 / (1 + np.exp(-x))

def softmax(x):
    op = np.max(x)  
    x = x - op
    exp = [np.exp(i) for i in x]
    sum_exps = sum(exp)
    return [j/sum_exps for j in exp]

def get_data():
    # flatten => 1차원 or 3차원 / normalize => 0 ~ 1 사이 정규화 할지 
    (x_train, y_train), (x_test, y_test) = load_mnist(normalize=True, flatten=True, one_hot_label=False) 
    return x_test, y_test

def init_network():
    with open("sample_weight.pkl", "rb") as f:
        network = pickle.load(f)
    return network

def predict(network, x):
    W1, W2, W3 = network['W1'], network['W2'], network['W3']
    b1, b2, b3 = network['b1'], network['b2'], network['b3']
    
    L1 = np.dot(x, W1) + b1  
    z1 = sigmoid(L1)
    
    L2 = np.dot(L1, W2) + b2
    z2 = sigmoid(L2)
    
    L3 = np.dot(L2, W3) + b3 
    y = softmax(L3)
    
    return y
    
x, y = get_data()
network = init_network()

accuracy_cnt = 0
for i in range(len(x)):
    t = predict(network, x[i])
    p = np.argmax(t)
    if (p == y[i]):
        accuracy_cnt += 1
print("Accuracy: " + str(float(accuracy_cnt) / len(x)))       
```

[MNIST 다운로드](https://github.com/oreilly-japan/deep-learning-from-scratch)

<br>

### 회귀 

### 배치 (Batch)

> 하나로 묶은 입력 데이터를 배치(Batch)라고 합니다. <br>
<br> 

**MNIST데이터는 숫자 이미지 데이터로 이미지 크기가 28 X 28 => 784라고 했을 때**
```
이미지 데이터 1장일 때 
        Input       W1        W2         W3      Output
형상   1 X 784  784 X 50   50 X 100   100 X 10   1 X 10

이미지 데이터 100장일 때 
        Input       W1        W2        W3      Output
형상  100 X 784  784 X 50  50 X 100  100 X 10   100 X 10 
```
<br>

**배치 처리의 장점** 1. numpy가 벡터연산을 효율적으로 처리하기 때문에 한번에 많은 데이터를 입력하더라도 빠른 시간에 처리할 수 있다. 2. 
신경망에서 데이터 전송이 병목으로 작용하는 경우가 자주 있는데, 배치 처리를 함으로써 버스에 주는 부하를 줄일 수 있다.
{: .notice}
<br> 

**배치 처리 구현 (위 MNIST 예제와 동일)**
```python
x, y = get_data()
network = init_network()

batch_size = 100
accuracy_cnt = 0

for i in range(0, len(x), batch_size):
    x_batch = x[i:i+batch_size]
    y_batch = predict(network, x_batch) 
    p = np.argmax(y_batch, axis = 1) # axis = 1하는 이유는? 
    accuracy_cnt += np.sum(p == y[i:i+batch_size])
print("Accuracy: " + str(float(accuracy_cnt) / len(x))) 
```

<br> 

### Batch VS Mini Batch VS Stochastic Gradient Descent 

```
Batch는 여러 데이터를 한 묶음으로 하여 1 Iteration에 사용되는 data set의 모음 
Mini Batch는 전체 데이터에서 특정 Batch Size로 나누어 학습시키는 방법 
 - Batch보다 빠르고 SGD보다는 낮은 오차율을 갖는다 
Stochastic Gradient Descent는 데이터를 한 개씩 뽑아서 처리하고 모든 데이터에 반복하는 방법이다. 
```
<br> 

<a id="3rd"></a>
# Chapter 4 "신경망 학습"
<br>
## 학습하기 

### Lose Function(Cost Function) 

> 신경망 학습에서는 현재 상태를 하나의 지표로 표현하고 <br>
> 그 지표를 가장 좋게 만들어주는 가중치 매개 변수의 값을 탐색해나갑니다. <br>
> 이때 현재 상태와 다음 상태를 비교하여 최적의 상태를 만들기 위한 수단으로 손실 함수를 사용하게 됩니다. 
<br>



<br> 

### Mean Squared Error(평균 제곱 오차) 

```python 
def mse(y, t):
    return 0.5 * np.sum((y-t) **2) 
```
<br>

### Cross Entropy Error(교차 엔트로피 오차) 

```python
def cee(y, t):
    delta = 1e-7
    return -np.sum(t*np.log(y + delta))
    
def cee(y, t):
    delta = 1e-7
    return -np.sum(t*np.log(y + delta) - (1-t)*np.log(1-y + delta))
    
# delta를 더하는 이유는 예측값이 0일 때 연산 결과가 -inf로 나오는 것을 방지하기위해 아주 작은 값을 더했습니다.    
```

<br>

## 해석적 미분 VS 수치 미분 

### 해석적 미분 

> 해석적으로 미분 <br>
> 오차를 포함하지 않는 진정한 미분 값을 구할 수 있다

**1. 전미분**
![전미분](https://user-images.githubusercontent.com/33630505/68744609-57d91080-0638-11ea-9183-15c19533d610.JPG)

<br>

**2. 편미분**
![편미분](https://user-images.githubusercontent.com/33630505/68744724-9969bb80-0638-11ea-8d64-0f900004bb52.JPG)


<br>

### 수치 미분 

> 아주 작은 차분으로 미분하는 것 <br>
> 수치 미분에는 오차가 포함된다 <br> 
<br>

**반올림 오차**

> 반올림 오차는 소수점 8자리 이하가 생략되어 최종 계산에 오차가 생기게 하는 경우를 말한다

<br>
```python
import numpy as np

np.float32(1e-50)
: 0.0 
```


**차분** 
![차분](https://user-images.githubusercontent.com/33630505/68745204-8dcac480-0639-11ea-9f5e-8dd6eb56b002.JPG)

<br>

**중앙 차분**
![중앙 차분](https://user-images.githubusercontent.com/33630505/68745459-18abbf00-063a-11ea-97df-e8ecf7a8e28d.JPG)
<br> 


**수치 미분의 예**

```python
import numpy as np
import matplotlib.pyplot as plt

# 중앙 차분 
def numerical_diff(f, x):
    h = 1e-4
    return(f(x+h) - f(x-h)) / (2*h)

# f(x) = 0.01x^2 + 0.1x 
def func(x):
    return 0.01*x**2 + 0.1*x

# f(x), f(x)' 그래프 그리기 
def func_draw(x1, y1,x2,y2):
    plt.xlabel("x")
    plt.ylabel("f(x)")
    plt.plot(x1,y1, x2,y2, '-r')
    plt.show()

# f(x)' 기울기, y 절편 구하기    
def gen(x,y,f):
    grad = numerical_diff(f, x)
    b = y - grad*x
    return grad, b         
    
x = np.arange(0.0,20.0,0.1)
y = func(x)

# (x=5, y=0.75)
function_1 = gen(5, func(5), func)[0]*x + gen(5, func(5), func)[1]

# (x=10, y=2)
function_2 = gen(10, func(10), func)[0]*x + gen(10, func(10), func1)[1]
```
<br>

**func_draw(x, y, x, function_1)**
![func1](https://user-images.githubusercontent.com/33630505/68746541-27937100-063c-11ea-9dba-b837df7a71c4.JPG)

<br>

**func_draw(x, y, x, function_2)**
![func2](https://user-images.githubusercontent.com/33630505/68746563-3548f680-063c-11ea-8e37-232475752ad3.JPG)

<br>


## 학습 알고리즘 구현하기 

<br>
```
[학습] => 데이터(Feature)의 중요도에 관여하는 가중치와 편향을 훈련 데이터에 적응하도록 조정하는 과정 

[1 단계] > 미니 배치 
: 훈련 데이터 중 일부를 무작위로 가져옵니다. 선별한 데이터를 미니배치라 부르며, 
  미니배치의 loss function 값을 줄이는 것이 목표입니다.
  
[2 단계] > 기울기 산출 
: 미니 배치의 loss function 값을 줄이기 위해 각 가중치 매개변수의 기울기를 구합니다. 
  
 
[3 단계] > 매개변수 갱신 
: 가중치 매개변수의 값을 0에 가까워 지도록 갱신합니다. 
  그 기울기가 0에 가까워지면 정답 - 예측값이 작아짐을 의미하여 학습이 충분히 되었음을 의미합니다. 

[4 단계] > 1~3 단계를 반복한다 
```

