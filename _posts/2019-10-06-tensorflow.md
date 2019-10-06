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

# Back Propagation에 필요한 수식

![solv](https://user-images.githubusercontent.com/33630505/66269409-02fcea00-e883-11e9-8cab-3590e17c9b63.png)


<br>

# Tensorflow 작동 방식 

> 텐서플로우는 기본적으로 그래프 기반으로 작동되는 프레임워크 이다. <br>

**그래프 => 실행**

<br> 

# Tensorflow로 구현하기 

## Data set 

> x는 입력 데이터, y는 결과 데이터 <br>
> 총 데이터 갯수 4개 <br>
> input 값 1개, output 값 1개 <br>

```python
import tensorflow as tf 

x_data = [1,2,3,4]
y_data = [5,8,11,14]
```

## Tensor for Data set 

> placeholder는 최종적으로 받아야 되는 값을 나중에 세팅하기 위해서 변수를 선언하는데 쓰인다


```python
x = tf.placeholder(tf.float32) 
y = tf.placeholder(tf.float32)
```









