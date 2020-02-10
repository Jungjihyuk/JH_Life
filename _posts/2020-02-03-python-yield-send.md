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

<center> <span style="color: orange; font-size:35px">Generator의 yield와 send에 대해 알아보자!</span></center>

<br> 

> Generator, Yield, Send가 도대체 뭐야? <br> 

<br>

<center>우선 Generator는 iterator를 생성해주는 함수!</center>
<center>그럼 iterator는 무엇이냐! iterator는 반복할 수 있는 객체의 요소를 리턴할 때 호출 한 시점에 값을 리턴하며 값을 지우고 그 상태를 유지해준다.</center>
<center>그러면 Yield는 무슨 관계가 있는데? yield는 generator를 만들때 함수 안에 yield를 삽입하면 yield를 만나는 순간 iterator 처럼 행동한다.</center>


<br> 

> Generator 작동 순서 

<br> 

<span style="color: orange">Step 1: </span>Generator 메소드 호출<br>
<span style="color: orange">Step 2: </span>yield까지 실행<br>
<span style="color: orange">Step 3: </span>첫번째 yield에서 중단(suspend)<br>
<span style="color: orange">Step 4: </span>호출자에게 expression_list 값을 반환(return)<br>
<span style="color: orange">Step 5: </span>중단된 지점에서 모든 상태가 보존(지역 변수들의 현재 연결들, 명령 포인터, 내부 연산 스택, 모든 예외처리)<br>
<span style="color: orange">Step 6: </span>1~5 step 반복<br>

<br>

**※ next함수 vs send함수** next함수를 통해 호출되면 return은 None, send함수를 통해 호출되면 return은 메소드로 전달된 값 
{: .notice}

<br> 

## Example 

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
