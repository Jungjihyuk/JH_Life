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
```sql
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
```sql
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

```sql
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

## Collections Truthness 

> Python에서 True와 False의 의미를 알 수 있는 문제 

<br>

### Example 

```python
xs = [()]
res = [False] * 2 
if xs:
    res[0] = True 
if xs[0]:
    res[1] = True 
```

<br> 

### My Answer 

```python 
xs = [()]
res = [False] * 2 
if xs:
    res[0] = True 
if xs[0]:
    res[1] = False 
```

**xs 리스트는 첫번째 요소로 tuple을 갖기 때문에 존재론적 관점에서 True, 리스트의 첫번째 요소인 tuple의 첫번째 요소는 아무것도 없기 때문에 존재론적 관점에서 False이다**

<br> 

## Efficient Comparison 

> 효과적인 비교 방법을 찾는 문제 

<br> 
### Example

```python
1. if L < x**y <=R:
2. if x**y > L and x**y <=R:
3. if x**y in range(L+1, R+1):
```

<br>

### My Answer 

```python
def func1(x,y,L,R):
    if L < x**y <=R:
        return True
    else: 
        return False 
	
def func2(x,y,L,R):
    if x**y > L and x**y <=R:
        return True
    else: 
        return False 	

def func3(x,y,L,R):
    if x**y in range(L+1, R+1):
        return True
    else: 
        return False 
	
%%timeit
func1(2,3, 0,10)	

: 480 ns ± 34.7 ns per loop (mean ± std. dev. of 7 runs, 1000000 loops each)

%%timeit
func2(2,3, 0,10)

: 763 ns ± 23.8 ns per loop (mean ± std. dev. of 7 runs, 1000000 loops each)

%%timeit
func3(2,3, 0,10)

: 806 ns ± 45.6 ns per loop (mean ± std. dev. of 7 runs, 1000000 loops each)
```

**func1이 가장 빠르다**

<br>

## Count Bits 

> 숫자 n을 입력하면 bit수를 출력하는 함수

<br> 
### Example

```python
n = 50 
countBits(n) = 6
50(10진수) = 110010(2진수) => 6개 비트로 구성 
```

<br>

### My Answer 

```python 
def countBits(n):
    cnt = 1 
    rest = 0 
    while(n!=1):
        rest = n/2
        n = int(rest) 
        cnt +=1
    
    return cnt
```

**함수가 잘 작동하고 정답처리가 되긴 했지만 자꾸 return문만 써서 간결하게 하라고 해서 다음 단계로 넘어가지 못했음..**

<br>

### Another Answer (Python) 
```python
def countBits(n):
    return n.bit_length()
```

**저런 내장 함수가 있는지 몰랐네...**

<br>

## Modulus

> 숫자 n이 정수형이면 return 1 아니면 return -1 

<br> 
### Example

```python
n = 15
modulus(n) = 1 

n = 23.12 
modulus(n) = -1 
```

<br>

### My Answer 

```python 
def modulus(n):
    if isinstance(n, int):
        return n % 2
    else:
        return -1
```
<br> 

### Another Answer (Python) 
```python
def modulus(n):
    if n==int(n) :
        return n % 2
    else:
        return -1
```

<br>

## Base Conversion

> n진법으로 표기된 String을 16진수로 변환하기 

<br> 

### Example

```python
n = '1302'
x = 5 

1302(5) => 202(10) => ca

baseConversion('1302',5) = 'ca'
```

<br>

### My Answer 

```python
def baseConversion(n:str, x:int)->int:
    result = 0
    for i, n in enumerate(n[::-1]):
        result += int(n) * pow(x, i)
    return hex(result)[2:]
    
def baseConversion(n, x):
    return hex(int(n,x))[2:]        
```

**int 함수는 숫자를 넣었을 때 정수형으로 변환하지만, 문자열 형태의 숫자와 변환하고자 하는 진법의 수를 입력하면 원하는 진법을 변환해주기도 한다**

<br> 

### Another Answer (Python) 

```python
def baseConversion(n, x):
    return format(int(n, x), 'x')
```


<hr>
<a id = '5th'></a>
# Graphs 
