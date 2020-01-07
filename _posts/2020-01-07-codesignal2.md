---
layout: post
title: CodeSignal Arcade 문제 풀이2
date: 2020-01-07
excerpt: "Python, Database, 문제해결 프로그래밍"
tag:
- CodeSignal2
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


<hr>
<a id = '2nd'></a>
# DataBase (MySQL 문법)

<br>

<hr>
<a id = '3rd'></a>
# The Core

<br>

<hr>
<a id = '4th'></a>
# Python

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
