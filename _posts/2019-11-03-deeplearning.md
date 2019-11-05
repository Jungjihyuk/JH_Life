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

### 입력값의 합을 함수에 대입한 결과는 서로 같다면 
```
y = ax1  + bx2 일때

if x1, x2 => (1+5), (2+10)
y = 6a + 12b 
```
<br> 

<span style="color: #fe8559; font-size: 30px">중첩의 원리가 적용되는 것!</span><br>

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

**행렬 곱연산(Element wise)**
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

**dot(Element wise의 합)**
```python
import numpy as np

g = np.array([[1,2],[1,2]])
h = np.array([2,3])

np.dot(g,h)
: array([8, 8])

g = np.array([[1],[2],[3]])
h = np.array([1,2,3]).reshape(1,3)

np.dot(g,h)
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

**matmul**
```python
g = np.array([[1,2],[1,2]])
h = np.array([2,3])

np.matmul(g,h)
: array([8, 8])

g = np.array([[1],[2],[3]])
h = np.array([1,2,3]).reshape(1,3)

np.matmul(g,h)
: array([[1, 2, 3],
       [2, 4, 6],
       [3, 6, 9]])
       
# 3차원부터 dot과 차이가 난다 
A = np.arange(24).reshape(2,3,4)
B = np.arange(24).reshape(2,4,3)

np.matmul(A,B)
: 
array([[[  42,   48,   54],
        [ 114,  136,  158],
        [ 186,  224,  262]],

       [[ 906,  960, 1014],
        [1170, 1240, 1310],
        [1434, 1520, 1606]]])
```
<br>



