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
2. DataBase  => SQL 문제
3. The Core  => 아직 안풀어봄
4. Python    => Python 문법 문제
5. Graphs    => 아직 안풀어봄 
```
<br> 

<span style="font-size: 20px; background: rgb(36, 54, 76); color: white; padding: 2px;">Navigation</span> <br>
[<span style="font-size: 18px; background: rgb(76, 217, 229); color: white; padding: 2px;">Intro</span>](#1st) &nbsp;
[<span style="font-size: 18px; background: rgb(30, 219, 173); color: white; padding: 2px;">DataBase</span>](#2nd) &nbsp;
[<span style="font-size: 18px; background: rgb(226, 71, 0); color: white; padding: 2px;">The Core</span>](#3rd) &nbsp;
[<span style="font-size: 18px; background: rgb(71, 182, 127); color: white; padding: 2px;">Python</span>](#4th) &nbsp; 
[<span style="font-size: 18px; background: rgb(125, 73, 194); color: white; padding: 2px;">Graphs</span>](#5th) &nbsp;

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
# DataBase (MySQL 문법) 

## MonthlyScholarships 

> 1년치 장학금이 기제되어 있는 DB에서 각 id별로 매달 장학금을 계산해서 id와 scholarship을 조회하라 

### Example 

**Table**
![scholarship](https://user-images.githubusercontent.com/33630505/66551079-b61a5b80-eb81-11e9-9d70-7809ae97b4bf.JPG)<br>
**Result**
![scholarship2](https://user-images.githubusercontent.com/33630505/66551431-6a1be680-eb82-11e9-8e17-f4f8c9c3985a.JPG)

<br>

### My Answer 
```mysql
CREATE PROCEDURE monthlyScholarships()
BEGIN
	SELECT id, scholarship/12 as scholarship FROM scholarships; 
END
```

<br> 

## ProjectsTeam 

> 중복되는 이름은 제거하고 이름을 오름차순으로 정렬하여 조회하라 
<br> 

### Example

**Table**
![projectteam](https://user-images.githubusercontent.com/33630505/66551762-0f36bf00-eb83-11e9-893d-3c28854a652c.JPG)
<br>

**Result**
![projectteam2](https://user-images.githubusercontent.com/33630505/66551799-21186200-eb83-11e9-80db-e9e6c7685b81.JPG)
<br>

### My Answer 
```mysql
CREATE PROCEDURE projectsTeam()
BEGIN
	SELECT DISTINCT name FROM projectLog ORDER BY name;
END
```
<br>

## AutomaticNotifications

> role 칼럼의 admin, premium을 제외한 행의 email을 조회하라 

<br> 

### Example

**Table**
![automaticnotification](https://user-images.githubusercontent.com/33630505/66553990-165fcc00-eb87-11e9-9317-b25645d68d07.JPG)
<br>

**Result**
![automaticnotification2](https://user-images.githubusercontent.com/33630505/66553992-165fcc00-eb87-11e9-90f4-5ccb532d1341.JPG)

### MyAnswer 

```mysql
CREATE PROCEDURE automaticNotifications()
    SELECT email
    FROM users
    WHERE role NOT IN ("admin", "premium")
    ORDER BY email;
```



<hr>
<a id = '3rd'></a>
# The Core



<hr>
<a id = '4th'></a>
# Python




<hr>
<a id = '5th'></a>
# Graphs 
