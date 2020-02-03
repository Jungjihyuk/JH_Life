---
layout: post 
title: Yield와 send 함수를 알아보자 (Python)
date: 2020-02-03
excerpt: 'generator yield와 send함수'
tag:
- python
- generator
- yield
- send
---

<center> <span style="color: orange; font-size:45px">Generator의 yield와 send에 대해 알아보자!</span></center>

<br> 

```python
def double(number):
    while True:
        number *= 2 
	yield number 

d = double(3)
d.send(None)  # 처음에 왜 None을 넣어야 모르겠음 .... ㅠㅠ 
: 6 
d.send(1)
: 12 
d.send(10)
: 24 

def double2(number):
    while True:
        number *= 2 
	number = yield number
	
d2 = double2(4) 
d2.send(None)
: 8
d2.send(1)
: 2
d2.send(100)
: 200

def check1():
    while True:
        x = yield
        yield x == number

number = 123 

c1 = check1()
c1.send(None)
c1.send(123)
: True
c1.send(None)
c1.send(1234)
: False 

def check2():
    x = yield 
    yield x == number2

number2 = 1234 

c2 = check2() 
c2.send(None)
c2.send(1234)
:True 
c2.send(1234) 
: StopIteration

def check3():
    yield (yield) == number3 
    
number3 = 2

c3 = check3()
c3.send(None) 
c3.send(123)
: False 
c3.send(2)
: StopIteration 

def check4():
    while True: 
        yield (yield) == number4

number4 = 777

c4 = check4()
c4.send(None) 
c4.send(123)
: False 
c4.send(7777) # interger 객체 7777은 return 값이 None이기 때문에 None을 넣었을 때와 같음 
c4.send(777) 	
: True

for x in range(4):
    n = c4.send(777)
    print(n)
: None
  True
  None 
  True 
  None
```
