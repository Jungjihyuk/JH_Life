---
layout: post 
title: CodeSignal Arcade 문제 풀이 
date: 2019-10-09
excerpt: "Python, Database, 문제해결 프로그래밍"
tag:
- CodeSignal 
- 코딩연습 
- python
- database 
- algorithm
---

# Index 

```
1. Intro     => 문제해결 프로그래밍, 알고리즘 문제
[Intro 바로가기](#1st) 
2. DataBase  => SQL 문제
[DataBase 바로가기](#2nd)
3. The Core  => 아직 안풀어봄
[The Core 바로가기](#3rd)
4. Python    => Python 문법 문제
[Python 바로가기](#4th)
5. Graphs    => 아직 안풀어봄 
[Graphs 바로가기](#5th)
```
<br> 

[<span style="font-size: 15px; background: rgb(76, 217, 229); color: white">Intro</span>](#1st)
[<span style="font-size: 15px; background: rgb(30, 219, 173); color: white">DataBase</span>](#2nd)
[<span style="font-size: 15px; background: rgb(226, 71, 0); color: white">The Core</span>](#3rd)
[<span style="font-size: 15px; background: rgb(71, 182, 127); color: white">Python</span>](#4th)
[<span style="font-size: 15px; background: rgb(125, 73, 194); color: white">Graphs</span>](#5th)

<hr> 
<br>


<a id = '1st'></a>
# Intro 

<br>

## CenturyFromYear 

> 연도를 입력 받으면 몇 세기인지 출력하는 함수 만들기 

<br> 

### Example 
```
For year = 1905, the output should be 
centuryFromYear(year) = 20

For year = 1700, the output should be 
centuryFromYear(year) = 17
```

<br>
### My Answer 
```python
def centuryFromYear(year):
    if year % 100 != 0: 
        year = year / 100 
        return int(year + 1)
    else:
        year = year / 100 
        return int(year) 
```

<br> 

### Another Answer (Python)  
```python
def centuryFromYear(year):
    return (year + 99) // 100
```
<br> 

### Another Answer (JS) 
```javascript 
function checkPalindrome(inputString) {
    return inputString == inputString.split('').reverse().join('');
}
```

<br>
<hr> 

## CheckPalindrome

> 회문인지 체크하는 함수, 앞으로 읽어도 뒤로 읽어도 똑같은 문자열이면 True 반환, 아니면 False 반환 

<br> 

### Example 
```
For inputString = "aabbaa", the output should be checkPalindrome(inputString) = ture

For inputString = "abac", the output should be checkPalindrome(inputString) = false

For inputString = "a", the output should be checkPalindrome(inputString) = true 
```

<br> 

### My Answer 
```python 
def checkPalindrome(inputString):
    if inputString == inputString[::-1]:
        return True
    else:
        return False
```
<br> 

### Another Answer (Python) 
```python 
def checkPalindrome(inputString):
    return inputString == inputString[::-1]
```
<br> 

### Another Answer (C++) 
```cpp
bool checkPalindrome(string is) {
    return is == string(is.rbegin(),is.rend());
}
```
<br> 

## AdjacentElementsProduct

> 인접한 요소의 곱이 가장 큰 값 반환 

<br> 

### Example 
```
For inputArray = [3, 6, -2, -5, 7, 3], the output should be 
adjacentElementsProduct(inputArray) = 21 
```

<br> 

### My Answer 
```python 
def adjacentElementsProduct(inputArray):
    temp = -99999999999 
    for i in range(len(inputArray)-1): 
        result = inputArray[i] * inputArray[i+1]
        if temp < result: 
            temp = result 
    return temp 
```
<br> 

### Another Answer (Python)  
```python
def adjacentElementsProduct(inputArray):
    return max([inputArray[i] * inputArray[i+1] for i in range(len(inputArray)-1)])
```

<br> 

### Another Answer (JS)
```javascript 
# 1 
function adjacentElementsProduct(inputArray) {
    var prod = inputArray[0] * inputArray[1];
    
    for (var i = 1; i<inputArray.length - 1;i++) {
        prod = Math.max(prod, inputArray[i] * inputArray[i+1]);
    }
    
    return prod
}

# 2 
function adjacentElementsProduct(arr) {
  return Math.max(...arr.slice(1).map((x,i)=>[x*arr[i]]))
}
```

<br> 

### Another Answer (Java)
```java
int adjacentElementsProduct(int[] inputArray) {
    return IntStream.range(1, inputArray.length).map(i->inputArray[i]*inputArray[i-1]).max().getAsInt();}
```
<br> 

## ShapeArea 

![polygon](https://user-images.githubusercontent.com/33630505/66472643-a25eee80-eac8-11e9-828c-5f7c78a5c6bb.JPG)


<br>

### My Answer 
```python 
import math
def shapeArea(n):
    return 2 * math.pow(n - 1, 2) + 2 * (n - 1) + 1
```
<br> 

### Another Answer (Python)
```python
def shapeArea(n):
    return n**2 + (n-1)**2
```
<br> 

### Another Answer (JS)
```javascript 
function shapeArea(n) {
    return n*n + (n-1)*(n-1);
}
```
<br>

### Another Answer (C++)
```cpp
int shapeArea(int n) {
    return 1 + 2 * n * (n-1);
}
```
<br> 

<hr>
<a id = '2nd'></a>
# DataBase



<hr>
<a id = '3rd'></a>
# The Core



<hr>
<a id = '4th'></a>
# Python




<hr>
<a id = '5th'></a>
# Graphs 
