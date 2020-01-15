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

> 예시 설명을 참고 해주세요.

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


## Frequency Analysis

> 암호문으로 변경하는 encrypt 함수. 평문에서 가장 빈도수가 높은 문자로 치환한다. 

<br>

### Example

```python
encryptedText = "$~NmiNmim$/NVeirp@dlzrCCCCfFfQQQ"

frequencyAnalysis(encryptedText) = 'C'
```
<br>

### My Answer

```python
from collections import Counter

def frequencyAnalysis(encryptedText):
    return Counter(encryptedText).most_common(1)[0][0]
    
def frequencyAnalysis(encryptedText):
    return list(set(encryptedText))[[encryptedText.count(x) for x in list(set(encryptedText))].index(max([encryptedText.count(x) for x in list(set(encryptedText))]))]    
```

<br>

### Another Answer

```python
from collections import Counter

def frequencyAnalysis(encryptedText):
    return sorted(encryptedText, key=encryptedText.count, reverse=True)[0]
```

<br>

## Cyclic Name 

> 문자열이 주어지면 원하는 길이로 문자열이 순환하는 문자열 반환하는 함수 

<br>

### Example 

```python
name = 'jihyuk'
n = 12 

cyclicName(name, n) = 'jihyukjihyuk'
```

<br>

### My Answer 

```python
from itertools import cycle

def cyclicName(name, n):
    gen = (x for x in cycle(name))
    res = [next(gen) for _ in range(n)]
    return ''.join(res)
   
def cyclicName(name, n):
    gen = cycle(name)
    res = [next(gen) for _ in range(n)]
    return ''.join(res)   
```

<br> 

**cycle 함수로 만든 객체는 generator 이다**

<br> 

## Memory Pills 

> 리스트의 요소중 길이가 짝수인 요소 다음부터 3개 요소를 추출하는 함수. 단, 추출된 요소가 3개 미만일 때 <br> 
> 부족한 요소는 ""로 채운다. 

<br> 

### Example 

```python
pills = ["Notforgetan", "Antimoron", "Rememberin", "Bestmedicen", "Superpillsus"]

=> 11 , 9 , 10 , 11 , 12
# 따라서 10뒤부터 11, 12에 해당하는 요소와 ""를 반환하면 된다. 


memoryPills(pills) = ["Bestmedicen", "Superpillsus", ""]
```

<br> 


### Another Answer 

```python 
from itertools import dropwhile

def memoryPills(pills):
    gen = dropwhile(lambda x: len(x)%2!=0, pills + [""]*3)
    next(gen)
    return [next(gen) for _ in range(3)]
    
from itertools import dropwhile, cycle, chain

def memoryPills(pills):
    gen = chain(dropwhile(lambda x: len(x)%2 > 0,pills),cycle([""]))
    next(gen)
    return [next(gen) for _ in range(3)]    
```

<br> 

## Float Range 

> 시작, 끝, 간격을 입력값으로 주면(정수, 실수 둘다 가능) 시작부터 끝이전까지 간격을 순회로 하는 리스트를 반환하는 함수 

<br> 

### Example 

```python 
floatRange(-0.9, 0.45, 0.2) = [-0.9, -0.7, -0.5, -0.3, -0.1, 0.1, 0.3]
```

<br> 


### My Answer 

```python
from itertools import takewhile, count

def floatRange(start, stop, step):
    gen = takewhile(lambda x: x < stop, count(start, step))
    return list(gen)
```

<br> 

### Another Answer 

```python
from itertools import islice

def floatRange(start, stop, step):
    gen =islice(map(lambda x:float(x)/100000.0,list(range(int(start*100000),int(stop*100000),int(step*100000)))),int((stop-start)/step)+1) 
    return list(gen)

```

<br> 

## Rock Paper Scissors 

> N명의 사람이 있다고 했을 때 모든 사람이 모든 사람들과 2번씩 경기를 할 수 있도록 명단을 짜주는 함수 

<br> 

### Example 

```python
players = ["trainee", "warrior", "ninja"]

rockPaperScissors(players) = 
```

<br> 

### My Answer 

```python
from itertools import permutations

def rockPaperScissors(players):
    return sorted(list(permutations(players, 2))
```

<br>

## Kth Permutation

> n개의 순열 조합 중 n번째 순열을 뽑는 함수 

<br>

### Example 

```python
numbers = [1, 2, 3, 4, 5]
k = 4 

kthPermutation(numbers, k) = [1, 2, 4, 5, 3]
```

<br> 

### My Answer 

```python
from itertools import permutations

def kthPermutation(numbers, k):
    return list(permutations(numbers, len(numbers)))[k-1]
```

<br> 

### Another Answer 

```python
from itertools import islice, permutations

def kthPermutation(numbers, k):
    return next(islice(permutations(numbers), k - 1, None)) # None대신 k도 가능 
```

<br>

## Crazyball 

> n개의 리스트에서 k개를 뽑아 조합하는 함수. (combination)

<br> 

### Example

```python
players = ["Ninja", "Warrior", "Trainee", "Newbie"]
k = 3

crazyball(players, k) = [['Ninja', 'Warrior', 'Trainee'],
			 ['Ninja', 'Warrior', 'Newbie'],
 			 ['Ninja', 'Trainee', 'Newbie'],
 			 ['Warrior', 'Trainee', 'Newbie']]
```

<br>

### My Answer 

```python
from itertools import combinations

def crazyball(players, k):
    return list(combinations(sorted(players), k))
```

<br>

## Twins Score

> 두 개의 리스트를 입력값으로 받아 같은 인덱스끼리 합하여 하나의 리스트로 반환하는 함수 

<br> 

### Example 

```python
b = [22, 13, 45, 32]
m = [28, 41, 13, 32]

twinsScore(b, m) = [50, 54, 58, 64]
```

<br> 

### My Answer 

```python
import numpy as np 
def twinsScore(b, m):
    return list(np.array(b)+np.array(m))

def twinsScoer(b,m):
    return [x[0]+x[1] for x in list(zip(b,m))]
```

<br> 

### Another Answer 

```python
def twinsScore(b, m):
    return map(sum, zip(b,m))

def twinsScore(b, m):
    return [u + v for u, v in zip(b, m)]
```

<br> 

## Pressure Gauges 

> 두 개의 리스트를 입력 받으면 각각의 인덱스에 맞게 짝지어 작은 값을 1행 리스트에 큰 값을 2행 리스트에 묶어 반환하는 함수 

<br> 

### Example 

```python
morning = [3, 5, 2, 6]
evening = [1, 6, 6, 6]

pressureGauges(morning, evening) = [[1, 5, 2, 6], 
 				    [3, 6, 6, 6]]
```

<br> 

### My Answer 

```python
def pressureGauges(morning, evening):
    return [list(map(min, zip(morning,evening))), list(map(max, zip(morning,evening)))]

def pressureGauges(morning, evening):
    return [[min(x) for x in zip(morning, evening)], [max(x) for x in zip(morning, evening)]]
```

<br> 

### Another Answer 

```python
def pressureGauges(morning, evening):
    return list(zip(*map(sorted, zip(morning, evening))))

def pressureGauges(morning, evening):
    return [list(map(op, zip(morning, evening))) for op in [min, max]]    
```

<br>

<span style="color: orange">zip과 *의 조합으로 여러개 리스트를 받을 때 각각의 인덱스에 해당하는 요소끼리 합칠 수 있다.</span><br> 

```python
a = [1,2,3,4]
b = [1,2,3,4]
c = [[1,2],[3,4],[5,6]]
d = [[1,2,10],[3,4,11],[5,6,12]]

list(zip(a,b))
=> [(1, 1), (2, 2), (3, 3), (4, 4)]

list(zip(*c))
=> [(1, 3, 5), (2, 4, 6)]

list(zip(*d))
=> [(1, 3, 5), (2, 4, 6), (10, 11, 12)]
```

<br>

<a id = '5th'></a>
# Graphs
