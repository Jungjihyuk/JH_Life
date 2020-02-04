---
layout: post 
title: Helper Function for Clean code (Python) 
excerpt: "파이썬 코딩의 기술 책 Better way 4 정리" 
date: 2020-02-04
tag: 
- python
- clean code
- helper function
---


<center><span style="color: orange; font-size: 35px">Python 코드의 가독성을 높여보자</span></center>

<br>


# #상황 1. URL에서 쿼리 문자열을 디코드해야 할 때 

<br> 

> URL에서 인코딩, 디코딩의 의미는 보안에서의 의미와 살짝 다르다. <br> 
> 인코딩 : http://www.google.com/떡볶이 먹고싶다!! 
        => http://www.google.com/search?sxsrf=ACYBGNTgapWszfC06soR1IlVyLsC2w_7EQ%
        3A1580777854450&source=hp&ei=fsE4Xri1GdWRr7wPvM2UOA&q=떡볶이+먹고싶다!! <br> 
> 주소에 한글/공백/특수기호가 들어가면 안되기 때문에 가능하도록 변환하는 작업 <br> 
> 디코딩은 그 반대 

## Boolean 표현식 

```python 
from urllib.parse import parse_qs
 
my_values = parse_qs('red=5&blue=0&green=',keep_blank_values=True)

# 값 전체 (dictionary로 저장) 
print(my_values) 
: {'red': ['5'], 'green':[''],'blue':['0']}

# 각각의 값을 뽑을 때 
red = my_values.get('red',[''])[0] or 0
green = my_values.get('green',[''])[0] or 0
opacity = my_values.get('opacity',[''])[0] or 0
```

**평가 =>** 이 표현식은 일기도 불편하고 필요한 작업을 수행하지도 못하는 좋지 못한 코딩 
{: .notice}

<br> 

### Boolean 표현식 변형 

```python 
red = my_values.get('red',[''])[0] or 0
green = my_values.get('green',[''])[0] or 0
opacity = my_values.get('opacity',[''])[0] or 0
                    ∥
                    ∨
red = int(my_values.get('red',[''])[0] or 0)
green = int(my_values.get('green',[''])[0] or 0)
opacity = int(my_values.get('opacity',[''])[0] or 0)               
```

<br> 

## if/else 조건식(삼항 표현식) 

```python
from urllib.parse import parse_qs
 
my_values = parse_qs('red=5&blue=0&green=',keep_blank_values=True)

red = my_values.get('red',[''])
red = int(red[0]) if red[0] else 0

green = my_values.get('green',[''])
green = int(green[0]) if green[0] else 0

opacity = my_values.get('opacity',[''])
opacity = int(opacity[0]) if opacity[0] else 0
```
<br> 

**평가 =>** 삼항 표현식은 코드를 짧게 유지하면서도 명확하게 표현 할 수 있는 장점이 있지만 복잡한 로직일 경우 남발하면 안된다. 
{: .notice}

<br> 

## 여러줄에 걸친 if/else 문

```python 
green = my_values.get('green',[''])
if green[0]: 
    green = int(green[0]) 
else: 
    green = 0
    
red = my_values.get('red',[''])
if red[0]: 
    red = int(red[0]) 
else: 
    red = 0
    
opacity = my_values.get('opacity',[''])
if opacity[0]: 
    opacity = int(opacity[0]) 
else: 
    opacity = 0    
```

<br> 

**평가 =>** 직관적이고 이해하기 편하나 코드의 길이가 길어 속도가 느려질 수 있다. 그리고 오히려 복잡한 수학 문제 같은 경우 코드가 길면 이해하기 더 힘들 수 있다.
{: .notice}

<br>


## Helper Function 

```python
 def get_first_int(values, key, default=0):
     found = values.get(key, [''])
     if found[0]: 
         found = int(found[0])
     else:
         found = default
     return found 

green = get_first_int(my_values, 'green')
red = get_first_int(my_values, 'red')
opacity = get_first_int(my_values, 'opacity')
```

**평가 =>** 복잡한 표현식보다 호출 코드가 훨씬 명확해진다. 하지만 아주 간단한 문제인데도 불구하고 너무 헬퍼 함수를 쓰는 것도 그리 좋지 않다. 
{: .notice}


<center><span style="color: #ca6257; font-size: 20px">최종 평가</span></center>

```
상황에 잘 맞게 적절하게 코드를 짜야 한다! 
그리고 
표현식이 복잡해지기 시작하면 최대한 빨리 해당 표현식을 작은 조각으로 분할하고 
로직을 헬퍼 함수로 옮기는 방안을 고려해야 한다. 

무조건 짧은 코드를 만들기보다는 가독성을 선택하는 편이 나을때가 많다. 
```





