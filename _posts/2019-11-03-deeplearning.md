---
layout: post
title: 밑바닥부터 시작하는 딥러닝
date: 2019-11-03
excerpt: "'Deep Learning from Scratch - 밑바닥부터 시작하는 딥러닝 -'책 정리하기"
tag:
- python
- deep learning
---


# Chater 2 "Perceptron" 

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


## 내적(inner product) 

> 방향이 있는 서로 다른 두 벡터가 있을 때 <br>
> 한 벡터를 기준으로 같은 방향이 되도록 다른 한 벡터를 정사영시켜 <br>
> 기준 벡터의 크기와 정사영시켜 생긴 벡터의 크기의 곱이다. <br>
> 즉, 한쪽 방향으로의 크기의 곱! 
<br>
![innerproduct](https://user-images.githubusercontent.com/33630505/68277234-1d102f00-00b2-11ea-8704-d603090c1c6c.JPG)
![innerproduct2](https://user-images.githubusercontent.com/33630505/68277266-2b5e4b00-00b2-11ea-9b1f-3b5ac13758e5.JPG)

<span style="color: #fe8559; font-size: 30px">내적을 구하면 두 벡터의 방향이 얼마나 일치하는지 알 수 있다!</span><br>




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



## 기계학습은 학습과 추론 두 단계를 거친다(backward propagation & forward propagation) 



