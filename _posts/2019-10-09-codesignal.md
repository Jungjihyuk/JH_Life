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

<br>


## ListBeautifier 

> 어떠한 리스트가 들어와도 리스트의 맨 앞 요소와 맨 뒤 요소가 같거나 빈 리스트를 반환하도록 하는 함수 

<br> 

### Example

```python
a = [3, 4, 2, 4, 38, 4, 5, 3, 2]
b = [1,4,-5]
c = [1,2]

listBeautifier(a) = [4, 28, 4]
listBeatuifier(b) = [4]
listBeatuifier(c) = []
```

<br>

### My Answer 

```python
def listBeautifier1(a):
    res = a[:]
    while res and res[0] != res[-1]:
    	res = res[1:-1]
    return res

def listBeautifier2(a):
    res = a[:]
    while res and res[0] != res[-1]:
        a, *res, b = res  
    return res

%%timeit
listBeautifier1(a)

: 2.32 µs ± 193 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)

%%timeit
listBeautifier2(a)

: 3.05 µs ± 237 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)

# slicing이 아주 살짝 더 빠르다 
```

**Slicing과 Unpacking으로 쉽게 풀 수 있다!**
<br>

## Fix Message 

> 대소문자 고쳐주는 함수 (가장 앞 단어의 첫번째 철자를 대문자로 그리고 나머지는 소문자로) 

<br> 

### Example 

```python
message = "you'll NEVER believe what that 'FrIeNd' of mine did!!1"

fixMessage(message) = "You'll never believe what that 'friend' of mine did!!1"
```

<br> 

### My Answer 

```python 
def fixMessage(message):
    return message.lower().capitalize()
```

<br> 


### Another Answer 

```python 
def fixMessage(message):
    return message.upper()[0] + message[1:].lower()
```

## Cat Walk 

> 내가 자리를 비운 사이 고양이가 내 키보드 위에 올라가 스페이스바를 마구 눌러서 띄어쓰기 간격이 <br>
> 너무 많이 벌어졌다. 늘어난 띄어쓰기 공간을 하나로 줄여라 (이런 말도 안되는..ㅎ) 

<br> 

### Example 

```python
line = "def      m   e  gaDifficu     ltFun        ction(x):"

catwalk(line) = "def m e gaDifficu ltFun ction(x):"
```

<br>

### My Answer 

```python 
1번 
def catWalk(code):
    a = ''
    for i in code.rsplit():
        a += i + ' '
    return a.rstrip()  # rstrip 함수는 원래 값은 변하지 않고 함수 호출시에만 결과값 리턴 
 
2번 
from functools import reduce
def catWalk(code):
    return reduce(lambda x,y:x+' '+y, [i for i in code.rsplit()]) 
```

**내 머리속에서 이런 코드가 나오다니..ㅎ 근데 제출이 안되네 ㅠ**

<br>

### Another Answer 

```python
3번 
def catWalk(code):
    return " ".join(code.split())
```
**이런 쉬운 함수가 있었다니..ㅎ**

<br>

### 속도 차이 

```
%%timeit
catWalk(line)

# 1번 
3.13 µs ± 205 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)

# 2번
4.51 µs ± 233 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)

# 3번
1.2 µs ± 39.3 ns per loop (mean ± std. dev. of 7 runs, 1000000 loops each)

# 결론: 이미 만들어져 있는게 젤 빠르다.. 
```

<br>

## Convert Tabs

> 문자열 안에 Tab(\t)이 들어 있다면 n번의 space로 변환하는 함수 


<br>

### Example

```python
code = "\t\t\t\t\t"
convertTabs(code, 1) = "    "

code = "def add(x, y)\f\treturn x + y"
convertTabs(code, 4) = "def add(x, y)\f    return x + y"

code = "    for x in range(20)"
convertTabs(code, 100) = "    for x in range(20)"
```

<br>


### My Answer 

```python
def convertTabs(code, x):
    return code.replace('\t', ' '*x)
```

<br>


## Feedback Review

> 원하는 크기 이하의 문자열 단위로 쪼개주는 함수 


<br>

### Example

```python
feedback = "This is an example feedback"
size = 8

feedbackReview(feedback, size) = ["This is", 
                                  "an", 
                                  "example", 
                                  "feedback"]
```

<br>


### Another Answer

```python
import textwrap

def feedbackReview(feedback, size):
    return textwrap.wrap(feedback, size)
    
import re

def feedbackReview(feedback, size):
    return re.findall('(?:\s|^)(\S(?:.{0,%d}\S)?)(?=\s|$)' % (size-2),feedback)    
```

<br>

## Is Word Palindrome

> 회문인지 확인하는 함수, 앞으로 읽어도 뒤로 읽어도 같은지 확인하는 함수 


<br>

### Example

```python
word = "aibohphobia"
isWordPalindrome(word) = true;

word = "hehehehehe"
isWordPalindrome(word) = false
```

<br>

### My Answer 

```python
def isWordPalindrome(word):
    return word == word[::-1]
```

<br>



## Permutation Cipher 

> 이름은 순열암호화 인데 사실상 시저 암화랑 같음. 평문하고 키를 넘겨주면 시저암호 처럼 암호화 해주는 함수 


<br>

### Example

```python
password = "iamthebest"
key = "zabcdefghijklmnopqrstuvwxy"

permutationCipher(password, key) = "hzlsgdadrs"

abcdefghijklmnopqrstuvwxyz
||  |  ||   |     || 
vv  v  vv   v     vv
zabcdefghijklmnopqrstuvwxy
```

<br>

### My Answer 

```python
def permutationCipher(password, key):
    table = str.maketrans("abcdefghijklmnopqrstuvwxyz", key)
    return password.translate(table)
```

<br>


### Another Answer

```python
def permutationCipher(password, key):
    table = {ord('a') + i : ord(k) for i, k in enumerate(key)}
    return password.translate(table)
    
def permutationCipher(password, key):
    table = ' '*97+key
    return str(password).translate(table)

def permutationCipher(password, key):
    table = string.maketrans(string.lowercase, key)
    return str(password).translate(table)
```

<br>

## Competitive Eating 

> 설명 못하겠음... 예시 확인 ㄱㄱ 

<br> 

### Example 
```python 
t = 3.1415, width = 10, precision = 2,

competitiveEating(t, width, precision) = "   3.14   "
```

<br> 

### Another Answer 
```python 
def competitiveEating(t, width, precision):
    return '{:^{}.{}f}'.format(t,width,precision)

def competitiveEating(t, width, precision):
    return "{0:.{1}f}".format(t,precision).center(width)

def competitiveEating(t, width, precision):
    return ('{:^{w}.{p}f}').format(t,w=width,p=precision)
```

<br> 

## Get Commit

> 유저 이름과 0, ?, +, !가 포함된 암호화 commit 문자중 4가지 symbol을 제거한 문자열을 추출하라

<br> 


### Example 

```python 
commit = "0??+0+!!someCommIdhsSt"

getCommit(commit) = "someCommIdhsSt"
```

<br> 

### My Answer 
```python
def getCommit(commit):
    return commit.replace('0','').replace('?','').replace('!','').replace('+','')
```
**너무 일차원적인 답변이지만 잘 된다..ㅎ**

<br> 

### Another Answer 
```python 
def getCommit(commit):
    return commit.lstrip('0?+!')
    
def getCommit(commit):
    return commit.strip('0?+!')    

def getCommit(commit):
    return "".join(filter(lambda x: x not in "0?+!", commit))

def getCommit(commit):
    return re.sub('[0?+!]', '', commit)

def getCommit(commit):
    return "".join([c for c in commit if c.islower() or c.isupper()])

def getCommit(commit):
    return re.match(r"^[0\?\+!]*(.*)$", commit).group(1)
``` 

<br> 

## Lists Concatenation  

> 두 리스트를 연결하는 함수. 


<br>

### Example 

```python
lst1 = [2, 2, 1]
lst2 = [10, 11]

listsConcatenation(lst1, lst2) = [2, 2, 1, 10, 11]
```

<br>


### My Answer 

```python
def listsConcatenation(lst1, lst2):
    res = lst1
    res.extend(lst2)
    return res

def listsConcatenation(lst1, lst2):
    res = lst1
    [res.append(i) for i in lst2]
    return res
```

<br>

### Another Answer 

```python
def listsConcatenation(lst1, lst2):
    res = lst1
    res += lst2
    return res
```

<br>

## Two Teams  

> 리스트에 있는 요소에서 [홀수번째 요소 합 - 짝수번째 요소 합 구하는] 함수 


<br>

### Example 

```python
students = [1, 11, 13, 6,14]

twoTeams(students) = 11 
(1 + 13 + 14) - (11 + 6) = 11
```

<br>


### My Answer 

```python
def twoTeams(students):
    return sum(students[::2]) - sum(students[1::2])
```

<br>

### Another Answer 

```python
def twoTeams(students):
    return sum( (-1)**i*I for i,I in enumerate(students))
```

<br>


## Remove Tasks

> 리스트에서 n번째 요소 제거한 리스트 반환하는 함수 

<br> 

### Example 

```python
k = 3
toDo = [1237, 2847, 27485, 2947, 1, 247, 374827, 22]

removeTasks(k, toDo) = [1237, 2847, 2947, 1, 374827, 22]
```

<br> 

### My Answer 

```python
def removeTasks(k, toDo):
    del toDo[k-1::k]
    return toDo
```

<br> 


## Print List

> 설명은 패스 ~ 예시를 참고해주세요~ 

<br> 

### Example 

```python
lst = [1, 2, 3, 4, 5]

printList(lst) = "This is your list: [1, 2, 3, 4, 5]"
```

<br> 

### My Answer 

```python
def printList(lst):
    return 'This is your list: ' + str(lst)
```

<br> 

### Another Answer 

```python 
def printList(lst):
    return f'This is your list: {lst}'
    
def printList(lst):
    return "This is your list: {}".format(lst)        
```

<br> 

## Repeat Char

> 문자열과 숫자를 입력받아 입력받은 숫자만큼 반복하는 문자열을 반환하는 람다

<br> 

### Example 

```python
ch = '*' 
n = 10 

repeatChar(ch, n) = '**********'
```

<br> 

### My Answer 

```python
repeatChar = lambda ch, n : ch *n
```

<br> 

## Get Points

> 채점 해주는 함수. n번째 문제가 맞으면 n점 획득, 틀리면 패널티 점수 차감.

<br> 

### Example 

```python
answer = [True, False, True, False, True, True]
p = 3 

getPoints(answer, p) = 12 => 1 -3 + 3 -3 + 5 + 6 
```

<br> 

### My Answer 

```python
def getPoints(answers, p):
    questionPoints = lambda x,y : x+1 if(y==True) else -p

    res = 0
    for i, ans in enumerate(answers):
        res += questionPoints(i, ans)
    return res
```

<br> 

### Another Answer 

```python 
def getPoints(answers, p):
    questionPoints = lambda i,ans: [-p,i+1][ans]

    res = 0
    for i, ans in enumerate(answers):
        res += questionPoints(i, ans)
    return res
```

<br> 

## Sort Students 

> 성씨를 기준으로 오름차순 정렬하는 함수. (단, 성이 같으면 이름으로)

<br> 

### Example 

```python
name = ["John Smith", "Jacky Mon Simonoff", "Lucy Smith", "Angela Zimonova"]

sortStudents(name) = ['Jacky Mon Simonoff', 'John Smith', 'Lucy Smith', 'Angela Zimonova']
```

<br> 

### Another Answer 

```python
def sortStudents(students):
    # 특정한 데이터를 기준으로 정렬할 수 있도록 함수를 지정할 수 있다 
    students.sort(key=lambda name: name.split(" ")[-1])
    return students

def sortStudents(students):
    students.sort(key= lambda s : s[len(s)-(s[::-1]).find(" "):] )
    return students
```

<br> 

## Is Test Solvable

> 리스트에 있는 숫자들을 다 더하는데, 각 숫자는 각 자리수의 합을 구한 후 더한다. <br>
> 그리고 그 총합이 n으로 나누어지는지 확인해주는 함수를 만든다. 

<br> 

### Example 

```python
ids = [529665, 909767, 644200]
k = 3 

(5+2+9+6+6+5) + (9+0+9+7+6+7) + (6+4+4+2+0+0) = 87 
87/3 = 0 
=> True 
```

<br> 

### My Answer 

```python 
def isTestSolvable(ids, k):
    digitSum = lambda x : sum([int(i) for i in list(str(x))])

    sm = 0
    for questionId in ids:
        sm += digitSum(questionId)
    return sm % k == 0
```

<br> 

### Another Answer 

```python
def isTestSolvable(ids, k):
    digitSum = lambda x: x%10+digitSum(x//10) if x else 0

    sm = 0
    for questionId in ids:
        sm += digitSum(questionId)
    return sm % k == 0

def isTestSolvable(ids, k):
    digitSum = lambda r: sum(map(int,str(r)))

    sm = 0
    for questionId in ids:
        sm += digitSum(questionId)
    return sm % k == 0
```

<br> 


## Create Spiral Matrix 

> 나선형 행렬을 구하는 함수. (맨 오른쪽 아래부터 시작) 

![spiral matrix](https://user-images.githubusercontent.com/33630505/71462109-a19b4600-27f5-11ea-917f-361c3d2f7827.png)


<br> 

### Example 

```python
n = 3 

createSpiralMatrix(n) = [[5, 4, 3],
                         [6, 9, 2],
                         [7, 8, 1]]
```

<br> 

### My Answer 

```python 
# 1번 
def createSpiralMatrix(n):
    dirs = [(-1, 0), (0, -1), (1, 0), (0, 1)]
    curDir = 0
    curPos = (n - 1, n - 1)
    res = [[0 for j in range(n)] for i in range(n)]

    for i in range(1, n * n + 1):
        res[curPos[0]][curPos[1]] = i
        nextPos = curPos[0] + dirs[curDir][0], curPos[1] + dirs[curDir][1]
        if not (0 <= nextPos[0] < n and
                0 <= nextPos[1] < n and
                res[nextPos[0]][nextPos[1]] == 0):
            curDir = (curDir + 1) % 4
            nextPos = curPos[0] + dirs[curDir][0], curPos[1] + dirs[curDir][1]
        curPos = nextPos

    return res

# 2번 
import numpy as np 

def createSpiralMatrix(n):
    dirs = [(-1, 0), (0, -1), (1, 0), (0, 1)]
    curDir = 0
    curPos = (n - 1, n - 1)
    res = np.zeros([n,n])

    for i in range(1, n * n + 1):
        res[curPos[0]][curPos[1]] = i
        nextPos = curPos[0] + dirs[curDir][0], curPos[1] + dirs[curDir][1]
        if not (0 <= nextPos[0] < n and
                0 <= nextPos[1] < n and
                res[nextPos[0]][nextPos[1]] == 0):
            curDir = (curDir + 1) % 4
            nextPos = curPos[0] + dirs[curDir][0], curPos[1] + dirs[curDir][1]
        curPos = nextPos

    return res    
```

**2번도 가능. 그러나 해당 문제에서 numpy 사용 금지.**<br> 
**1번에서 처음에 [[j for j in range(n)] for i in range(n)]를 했지만 계속 인덱스 오류가 남. (이유는 모르겠음..)**

<br> 

### Another Answer 

```python
def createSpiralMatrix(n):
    dirs = [(-1, 0), (0, -1), (1, 0), (0, 1)]
    curDir = 0
    curPos = (n - 1, n - 1)
    res = [[0]*n for x in range(n)]

    for i in range(1, n * n + 1):
        res[curPos[0]][curPos[1]] = i
        nextPos = curPos[0] + dirs[curDir][0], curPos[1] + dirs[curDir][1]
        if not (0 <= nextPos[0] < n and
                0 <= nextPos[1] < n and
                res[nextPos[0]][nextPos[1]] == 0):
            curDir = (curDir + 1) % 4
            nextPos = curPos[0] + dirs[curDir][0], curPos[1] + dirs[curDir][1]
        curPos = nextPos

    return res
```

<br> 

## Construct Shell 

> 오른쪽으로 90도 회전한 산 모양 리스트를 반환하는 함수 

<br> 

### Example 

```python
n = 3 

constructShell(n) = [[0],
                     [0, 0],
                     [0, 0, 0],
                     [0, 0],
                     [0]]
```

<br> 


### My Answer 

```python
def constructShell(n):
    return [[0 for j in range(2*n-i)] if i > n else [0]*i  for i in range(1, 2*n)]
```

<br> 


### Another Answer 

```python
def constructShell(n):
    return [[0]*min(i,2*n-i) for i in range(1,2*n)]
    
def constructShell(n):
    return [[0] * (i - 2 * max(0, i-n) ) for i in range(1, 2 * n)]

def constructShell(n):
    return [[0] * (n-abs(i)) for i in range(-n+1, n)]
```

<br> 

## Word Power 

> 단어를 넣으면 알파벳 순서에 맞게 숫자로 치환하여 각각의 철자의 합을 구하는 함수. 

<br> 

### Example 

```python
word = 'hello'

h => 8 e => 5 l => 12 o => 15 
wordPower(word) = 8 + 5 + 12 + 12 + 15 = 52
```

<br> 

### My Answer 

```python
def wordPower(word):
    num = {b: a+1 for a, b in enumerate('abcdefghijklmnopqrstuvwxyz')}
    return sum([num[ch] for ch in word])
```

<br> 

### Another Answer 

```python
def wordPower(word):
    num = {c: ord(c) - 96 for c in word}
    return sum([num[ch] for ch in word])

def wordPower(word):
    num = dict(zip('abcdefghijklmnopqrstuvwxyz', range(1, 27)))
    return sum([num[ch] for ch in word])

```

<br> 

## Cool Pairs 

> 두 리스트의 요소간 결합으로 만들어지는 숫자 쌍이 (x,y)라 했을 때 (x*y)%(x+y)==0 인 쌍의 갯수를 반환하는 함수 <br>
> 단, 숫자 쌍의 합이 같은 경우가 2개 이상일 때는 하나로 취급한다. 

<br> 

### Example 

```python
a = [4, 5, 6, 7, 8]
b = [8, 9, 10, 11, 12]

# (4,12), (6,12), (8,8)의 경우가 발생 
# 그러나 합으로 봤을 때는 16, 18인 경우 두 가지!

coolPairs(a,b) = 2
```

<br> 

### My Answer 

```python
def coolPairs(a, b):
    uniqueSums = {(x+y) for x in a for y in b if (x*y)%(x+y)==0}
    return len(uniqueSums)
```

<br> 

## Multiplication Table 

> 숫자 n을 입력하면 NxN 행렬을 반환한다. (단, 1행은 1단 2행은 2단 ...n행은 n단의 숫자로 구성) 

<br>

### Example 

```python
n = 5 

multiplicationTable(5) = [[1, 2, 3, 4, 5],
			 [2, 4, 6, 8, 10],
 			 [3, 6, 9, 12, 15],
			 [4, 8, 12, 16, 20],
			 [5, 10, 15, 20, 25]]
```

<br> 

### My Answer 

```python
def multiplicationTable(n):
    return [[a for a in range(b,b*n+1,b)] for b in range(1,n+1)]
```
<br> 

### Another Answer 

```python
def multiplicationTable(n):
    return [range(i, n*i + 1, i) for i in xrange(1,1+n) ]

def multiplicationTable(n):
    return [[x*y for x in range(1,n+1)] for y in range(1,n+1)]
```

<br> 

## Chess Teams 

> 두 개의 리스트를 입력값으로 받으면 각각의 리스트에서 요소 하나씩 뽑아 리스트로 짝지어 리턴해주는 함수 

<br> 

### Example

```python
smarties = ["Jane", "Bob", "Peter"]
cleveries = ["Oscar", "Lidia", "Ann"]

chessTeams(smarties, cleveries) = [['Jane', 'Oscar'], ['Bob', 'Lidia'], ['Peter', 'Ann']]
```

<br> 

### My Answer 

```python
 def chessTeams(smarties, cleveries):
    return list(map(lambda x, y : [x,y], smarties, cleveries))
```

<br> 

### Another Answer 

```python
def chessTeams(smarties, cleveries):
    return list(zip(smarties,cleveries))
```

<br> 

## College Courses 

> 수강한 과목중에 빼야 하는 과목 이름의 길이만 알때 그 과목을 빼는 함수 

<br> 

### Example 

```python
n = 7 
courses = ["Art", "Finance", "Business", "Speech", "History", "Writing", "Statistics"]

collegeCourses(x, courses) = ["Art", "Business", "Speech", "Statistics"]
```
<br>

### My Answer 

```python
def collegeCourses(x, courses):
    def shouldConsider(course):
        return len(course) != x

    return list(filter(shouldConsider, courses))
```

<br> 

## Create Histograme

> 요일마다 과제 수행정도를 보여주는 히스토그램을 만드는 함수.. (사실 그냥 별찍기)

<br> 

### Example 

```python
ch = '*'
assignments = [12, 12, 14, 3, 12, 15, 14]

createHistogram(ch, assignments) = ["************",
                                    "************",
                                    "**************",
                                    "***",
                                    "************",
                                    "***************",
                                    "**************"]
```

<br> 

### My Answer 

```python
def createHistogram(ch, assignments):
    return list(map(lambda x: ch*x, assignments))
    
def createHistogram(ch, assignments):
    return [ch * x for x in assignments]
```

<br> 

## Least Common Denominator 

> 최소공통분모 구하는 함수 

<br> 

### Example 

```python
denominators = [2, 3, 4, 5, 6]

leastCommonDenominator(denominators) = 60 

# 풀이 

2 x 3      4        5        6
----- x  ----- x  ----- x  -----
  1        2        1        6      => (2와 3의 최대공약수, 2x3과 4의 최대 공약수.....) 
```

<br> 


### My Answer 

```python
from functools import reduce
from fractions import gcd

def leastCommonDenominator(denominators):
    return reduce(lambda x,y : (x*y) / gcd(x,y), denominators)


from fractions import gcd

def leastCommonDenominator(denominators):
    return functools.reduce(lambda x,y : (x*y) / gcd(x,y), denominators)    
```

<br> 

## Dictionary Keys 

> Data Type Dictionary에서 key가 될 수 있는 types of objects는? 

<br> 

```
키값은 변하면 안되므로 immutable objects이며 unique해야 한다. 

따라서 frozenset, tuple of immutable objects, integer가 키로써 적합하다. 
```

**그런데 꼭 저 3가지 타입만 키로 가능한건 아니다** 

```python
# tuple of immutable 
{(1,2):'1과 2'}

# frozenset 
{frozenset([1,2]):'1과 2'}
{frozenset((1,2)):'1과 2'}

# integer 
{1:'1과 2'}

-----------------------------------
# tuple of mutable 
{('1','2'):'1과 2'}

# string
{'1과 2': '1과 2'}
{'1':'1과 2'}

# bytes 
{b'1':'1과 2'}

-----------------------------------
# 안되는 것들 
{[1,2],'1과 2'}
{['1','2'],'1과 2'}
{{1,2},'1과 2'}
{bytearray(b'1'):'1과 2'}

=> TypeError: unhashable type: ~~~ 
=> python에서 hashable은 lifetime 동안 변하지 않는 해시 값을 갖을 수 있는지 여부이다. 
   따라서 unhashable type은 해시값을 가질 수 없는 type이란 말이고 결국 유일한 키 값을 
   부여할 수 없는 type임으로 key로써 부적절한 type이라는 뜻이다.
```

<br> 

## Unique Characters 

> 문장에서 사용된 Characters type 문자를 중복없이 순서대로 리스트에 나열하는 함수 

<br> 

### Example 

```python
document = "Todd told Tom to trot to the timber"

uniqueCharacters(document) = [' ', 'T', 'b', 'd', 'e', 'h', 'i', 'l', 'm', 'o', 'r', 't']

' ' < 'T' => True 
'T' < 't' => True 
# 오름차순 정렬
```

<br> 

### My Answer 

```python
# 오름차순일 때 
def uniqueCharacters(document):
    return sorted(list(set(document))) # sorted(set(document)) sorted 함수를 쓰면 리스트로 반환 

# 내림차순일 때 
def uniqueCharacters(document):
    return sorted(list(set(document)), reverse=True)
```

<br> 

## Correct Scholarships 

> 

<br> 

### Example 

```python
bestStudents = [3, 5]
scholarships = [3, 5, 7]
allStudents = [1, 2, 3, 4, 5, 6, 7]

correctScholarships(bestStudents, scholarships, allStudents) = True

bestStudents = [3]
scholarships = [1, 3, 5]
allStudents = [1, 2, 3]

correctScholarships(bestStudents, scholarships, allStudents) = False

bestStudents = [3, 5]
scholarships = [3, 5]
allStudents = [3, 5]

correctScholarships(bestStudents, scholarships, allStudents) = False
```

<br> 

### My Answer 

```python
# Hidden test 1개 빼고 전부 통과.. 
def correctScholarships(bestStudents, scholarships, allStudents):
    return set(bestStudents) | set(scholarships) != set(allStudents) and not ((set(bestStudents) | set(scholarships)) - set(allStudents)) 
```

<br> 

### Another Answer 

```python
def correctScholarships(bestStudents, scholarships, allStudents):
    return len(scholarships) < len(allStudents) and sum([x in allStudents for x in scholarships]) == len(scholarships) and sum([x in scholarships for x in bestStudents])==min(len(bestStudents), len(scholarships))
    
def correctScholarships(bestStudents, scholarships, allStudents):
    return set(bestStudents) <= set(scholarships) < set(allStudents)    
```

<br> 

## Startup Name 

> 스타트업 회사를 차린다고 가정할 때 인기있는 경쟁사의 회사 이름 3개 중 중요한 철자를 골라내는 함수 <br> 
> 결국 3개 집합 전체에서 3개 집합의 대칭차집합을 뺀 부분을 골라내는 함수 

<br> 


### Example 

```python
companies = ["coolcompany", "nicecompany", "legendarycompany"]
startupName(companies) = ['e', 'l']

companies = ["nameone", "nametwo", "namethree"]   
startupName(companies) = ['o', 't']
```

<br> 

### Another Answer 

```python
def startupName(companies):
    cmp1 = set(companies[0])
    cmp2 = set(companies[1])
    cmp3 = set(companies[2])
    res = (set(companies[0]) | set(companies[1]) | set(companies[2])) - (set(companies[0])^set(companies[1])^set(companies[2]))
    return list(sorted(list(res)))
```

<br> 

## Words Recognition 

> 두 단어에서 공통적인 알파벳을 뺀 나머지 부분을 추출하는 함수 

<br> 

### Example 

```python
word1 = "program"
word2 = "develop"

wordsRecognition(word1, word2) = ['agmr', 'delv']
```

<br> 

### My Answer 

```python
def wordsRecognition(word1, word2):
    def getIdentifier(w1, w2):
        return ''.join(sorted((set(w1) ^ set(w2)) - set(w2)))

    return [getIdentifier(word1, word2), getIdentifier(word2, word1)]
```

<br> 

### Another Answer 

```python
def wordsRecognition(word1, word2):
    def getIdentifier(w1, w2):
        return ''.join(sorted(set(w1) - set(w2)))

    return [getIdentifier(word1, word2), getIdentifier(word2, word1)]

def wordsRecognition(word1, word2):
    def getIdentifier(w1, w2):
        return "".join(sorted(frozenset(w1)-frozenset(w2)))

    return [getIdentifier(word1, word2), getIdentifier(word2, word1)]
```

<br> 


**Tip** list or set to string => join
{: .notice}


<br> 

## Transpose Dictionary 

> Dictionary형태의 데이터 타입의 키, 값이 "설명", "확장자 명"으로 되어 있는데 이를 "확장자 명", "설명"으로 <br>
> 구성된 리스트로 바꿔주는 함수 

<br> 

### Example 

```python
scriptByExtension = {
  "validate": "py",
  "getLimits": "md",
  "generateOutputs": "json"
}

transposeDictionary(scriptByExtension) = [["json","generateOutputs"], 
                                          ["md","getLimits"], 
 					  ["py","validate"]]
```

<br> 

### My Answer 

```python
def transposeDictionary(scriptByExtension):
    return sorted([[y, x] for x, y in scriptByExtension.items()])
```

<br> 

### Another Answer 

```python
def transposeDictionary(scriptByExtension):
    return sorted(zip(scriptByExtension.values(), scriptByExtension.keys()))
```

<br> 

## Doodled Password 

> 비밀번호 낙서? / queue의 FIFO 특성을 deque로 구현하는 함수. / 인덱스 수 만큼 First out Last in(맨 앞 요소)를 반복한다 <br> 
> 설명 잘 못하겠으니 밑에 예시를 참고해 주세요 
<br> 

### Example 

```python
digits = [1, 2, 3, 4, 5]

doodledPassword(digits) = [[1, 2, 3, 4, 5], 
			   [2, 3, 4, 5, 1], 
			   [3, 4, 5, 1, 2],
                           [4, 5, 1, 2, 3], 
			   [5, 1, 2, 3, 4]]
```
<br> 

### My Answer 

```python
from collections import deque

def doodledPassword(digits):
    n = len(digits)
    res = [deque(digits) for _ in range(n)]
    [[res[x].insert(len(res)-1, res[x].popleft()) for y in range(x)] for x in range(1, len(res))]
    return [list(d) for d in res]
```

<br> 

### Another Answer 

```python
from collections import deque

def doodledPassword(digits):
    n = len(digits)
    res = [deque(digits) for _ in range(n)]
    map(lambda i: res[i].rotate(-i), range(n))
    return [list(d) for d in res]


from collections import deque

def doodledPassword(digits):
    n = len(digits)
    res = [deque(digits) for _ in range(n)]
    deque(map(lambda x,y: x.rotate(y), res, range(n,0,-1)), 0)
    return [list(d) for d in res]

from collections import deque

def doodledPassword(digits):
    n = len(digits)
    res = [deque(digits) for _ in range(n)]
    deque(map(lambda x: x[1].rotate(-x[0]), enumerate(res)), 0)
    return [list(d) for d in res]
```

<br> 





<a id = '5th'></a>
# Graphs 
