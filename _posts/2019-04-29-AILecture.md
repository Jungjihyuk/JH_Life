---
layout: post
title: AI 이노베이션 스퀘어 수업(기본반)
excerpt: "AI 이노베이선 스퀘어에서 배운 AI 공부 정리"
date: 2019-04-29
tag:
- AI
- Lecture
- Python
---

# 2019년 4월 29일 월요일 첫 수업
이 수업은 기본반이라고 되어 있지만 사실상 <kbd>fundamental</kbd> 즉, 핵심적이고, 근본적인, 필수적인 것들을 다루기 때문에 어려운 내용도 포함 하고 있다. 
<br>
## 왜 프로그래밍 언어가 많은 걸까?? <br>
: 언어마다 각각의 장단점이 있다. <br> 
<br>
## 왜 AI에는 파이썬인가?
```
Life is short, you need! 
파이썬의 슬로건에서 보여주듯이 
파이썬은 개발 속도가 빠르기 때문에 생산성이 좋다! 
생산성
- Efficient  --> 빠르고 체계적인 일처리가 가능하다  
- Effective  --> 원하는 결과를 가져다 준다

그리고 이 파이썬은 크게 3가지 분야에서 유리하다. 
첫번째 시스템 자동화 분야
두번째 웹
세번째 데이터 사이언스 
```
* 이 수업은 Data Science분야를 집중해서 다뤄볼 것이다. <br>
<br>
## Python의 특징 

1. 다양한 패러다임을 지원한다. 
2. 글루 언어다. 
- 언어이면서 명세서이다. 
- CPython / De facto -> 많이 쓰여서 표준이된것. (사실상 표준)
3. Library & Tool (많다) 
4. General Purpose <-> domain specific
5. 인터프리터 언어이다.
6. 모바일 지원에 대해 약하다. (이는 절대 개선될 수 없다. 왜냐하면 apple과 google에서 swift, 및 자사 언어를 사용하기 때문에) 
- 그러나 DS분야에서는 그나마 낫다.
7. 속도가 엄청 느리다. (Dynamic language) 

<br>

* 이번 수업은 c로 만든 python으로 사용한다 <br>

* python3.3 부터 유니코드로 인한 속도가 개선되었다. <br>
<br>
## Interpreter vs Compiler 

![interpreter vs compiler](https://user-images.githubusercontent.com/33630505/56888295-93eac080-6aae-11e9-977b-2db7ce9cd580.JPG)
<br>
## REPL vs IDE vs Text Editor 
<kbd>REPL</kbd>: &nbsp; Read-Eval-Print loop의 약자로 컴파일 과정없이 즉석으로 코드를 입력하고 실행결과를 바로 보는 대화형 환경을 말한다.<br>
<kbd>IDE</Kbd>: &nbsp; Integrated Development Environment의 약자로 개발통합환경 즉, 코딩을 위한 편집기, 컴파일, 링크, 디버그 등... 실행 모듈 개발에 필요한 기능을 한곳에 모아둔 프로그램을 말한다. <br>
<kbd>Text Editor</kbd>: &nbsp; 문서 편집기, 메모장이나 노트패드, atom 등을 text editor라고 하고 보통 코딩을 위한 text editor는 코딩을 더 편리하게 도와주는 기능이 탑재되어있다. <br>
atom같은 경우에는 원하는 경우 설치하여 터미널창을 추가할 수도 있고 각 언어별 자동완성기능 등 여러가지 편리한 기능들을 사용할 수있도록 도와주는 프로그램이다. 

<br>
## Jupyter notebook
Python + Markdown 지원 REPL? <br>

Python의 REPL에서 여러줄의 코드를 실행하기 편하고 편집하기 유용한 버전으로 업그레이드 한 것이 IPython Notebook. <br>
IPython의 강점은 한 파일 내에서 쉽게 코드 cell 단위로 실행할 수 있다는 것이다. <br>
다만 IPython는 파이썬 전용이다. 그리고 한 번 실행하고 Python 버전을 바꾸려면 로컬 서버를 내렸다가 다시 올려야 하는 불편함이 있다. <br>
이러한 불편함을 극복하고 만들어진 것이 바로 Jupyter Notebook이다. <br>
Jupyter 이름에는 뜻이 숨어 있다. Ju는 Julia Py는 Python 그리고 R은 R 세 단어를 합친 단어이다. <br>
Jupyter notebook은 특이한 점이 웹에서 사용한다는 것이다. <br>

> 앞으로 이 수업은 파이썬 공식 문서를 이용할 것이다. 왜냐하면 정확한 정보를 제공하고 공식 문서를 보는 연습을 미리 해두면
나중에 공부할때 필히 도움이 될 것이다. &nbsp; [공식 문서](https://docs.python.org/3/)

## Jupyter을 이용하여 python, markdown 활용해보기 

```
자료형 중 숫자는 크게 4가지가 있다. 
1. Integer
2. Float
3. Boolean
4. Complex

Integer는 정수형으로 숫자의 범위가 없다. 따라서 오버플로우가 없다. 
그리고 python에서 정수의 종류는 한 가지

Float는 부동소수로 숫자의 범위가 있다. 따라서 오버플로우가 있다. 
※ 0.1 + 0.1 + 0.1 의 결과값은 0.3000000000000004로 나온다. 
Why? --> 컴퓨터는 근사값을 계산하기 때문에 정확한 값을 출력하지 못한다. 

※ a = 2e3  --> 2000.0
   b = 2e-3 --> 0.002

그리고 컴퓨터가 정수와 부동소수의 저장 방식의 차이 때문에 .의 유무로 정수인지 부동소수인지 판단한다.

Boolean은 True / False 
True는 숫자 1에 대응되고 False는 숫자 0에 대응된다.
※ True 처럼 bold채로 쓰인 것은 키워드이다. 

Complex는 복소수로 j로 표시한다. 
ex) i = 1 + 3j
   : (1+3j)

문자는 크게 3가지가 있다. 
1. String
2. Bytes
3. Bytearray

String은 python3 버전에서 unicode문자에 해당한다. 
Byte는 문자 앞에 b를 붙이면 byte문자로 인식하고 ASCII코드에 해당한다. 
ex) a = b'안녕'
    type(a) 
    bytes
    
※ Python에서는 변수를 식별자라고 명칭한다. 
이때 식별자는 생성 규칙이 정해져 있다. 
1. 영문으로 써야한다.
2. 첫번째문자는 특수문자를 사용할 수 없다.
3. 미리 정의되어있는 문자는 사용할 수 없다. 

※ 파이썬은 동적타입, 즉 타입을 지정해주지 않아도 자동으로 지정해주기 때문에 정수형인지 
부동소수점인지 문자인지 등을 명시하지 않아도 타입이 지정된다.
```

```python
import keyword 
keyword.kwlist

['False',
 'None',
 'True',
 'and',
 'as',
 'assert',
 'async',
 'await',
 'break',
 'class',
 'continue',
 'def',
 'del',
 'elif',
 'else',
 'except',
 'finally',
 'for',
 'from',
 'global',
 'if',
 'import',
 'in',
 'is',
 'lambda',
 'nonlocal',
 'not',
 'or',
 'pass',
 'raise',
 'return',
 'try',
 'while',
 'with',
 'yield']
```
<br>
```python
%whos     # 여태까지 사용한 식별자를 보여줌
 
Variable   Type       Data/Info
-------------------------------
a          int        1
abc        bytes      b'abc'
b          int        2
c          int        3
f          bool       False
i          complex    (1+3j)
keyword    module     <module 'keyword' from 'C<...>conda3\\lib\\keyword.py'>
t          bool       True
w          str        ㅇㅇ
```

```python
'문근영' * 3 
: 문근영문근영문근영 

# 데이터 타입에 따라서 지원되는 연산이 다르다. 
```

### Markdown 문법
<span style="background-color: #fdbb5d">아주 기본적인 마크다운 문법을 배웠고 jupyter에서 작동하는 커멘드를 배웠다.</span><br>
<kbd>ESC</kbd> : &nbsp; 명령 커멘드<br>
<kbd>H</kbd>: &nbsp; Help (도움말)<br> 
<kbd>ESC + Y</kbd>: &nbsp; Code mode<br> 
<kbd>ESC + M</kbd>: &nbsp; Markdown mode<br> 
<kbd>ESC + A</kbd> &nbsp; 현재 라인 위에 새로 추가하기<br>
<kbd>ESC + B</kbd> &nbsp; 현재 라인 밑에 새로 추가하기<br>
<kbd>ESC + L</kbd> : &nbsp; 해당 줄에 숫자 <br>
<kbd>Ctrl + Shift + P</kbd> : &nbsp; Help (도움말)<br> 

**복습 시간**   18시 15분 ~ 19시 30분 / 총 1시간 15분
{: .notice}

<hr>

# 2019년 4월 30일 화요일 두번째 수업

## 자료형은 총 20가지가 있지만 13가지를 배울 것이다.

### 자료형
```
1. 숫자형 [Integer, Float, Boolean, Complex]
2. 문자형 [String, Bytes, Bytearray]
3. List
4. Tuple
5. Set
6. Frozenset
7. Dictionary
8. Range 
```

### 정수형을 표현하는 4가지 방법 

1. 2진수 
- 0b를 숫자 앞에 붙인다.
2. 8진수 
- 0o를 숫자 앞에 붙인다.
3. 16진수
- 0x를 숫자 앞에 붙인다.
4. 10진수
- 아무것도 안쓰면 그냥 10진수이다. 

```python
import sys
sys.maxsize

결과: 9223372036854775807
정수형에서 오버플로우가 없다고 했는데..? 
실제로 메모리에 할당 가능한 최대 숫자 크기가 저 값이고 
초과되었을 때 동적으로 추가 할당이 된다.(?)

sys.int_info

sys.int_info(bits_per_digit=30, sizeof_digit=4)
32비트 python인 경우, 정수는 최대 30비트까지 허용된다? 
```
<br>

### 진법 변환 builtin
bin() => 2진법으로 변환 <br>
oct() => 8진법으로 변환 <br>
hex() => 16진법으로 변환 <br>
2, 8, 16진법의 숫자를 입력하면 자동으로 10진수로 변환<br>
<br>
* bold채가 아닌데 색이 변하는 것은 builtin함수
<br>

### float 

<span style="background-color: skyblue">부동소수는 소수점이 존재하는 수</span><br>
<span style="background-color: skyblue">예외적으로 무한대와 숫자가 아닌 경우도 포함한다.</span><br>
```python
float('inf')
=> inf (infinity)
float('nan')
=> nan (not a number)
# 무한대 개념은 딥러닝에서 미분의 개념을 꼭 알아야 하는데 이때 중요하게 작용한다.
  파이썬은 이처럼 숫자 체계가 범위가 넓기 때문에 인공지능에 이용되는 장점이 있다.
```
.(점)은 부동소수점을 결정하는 리터럴 <br>
* 리터럴은 데이터 타입을 결정하는 문자를 일컫는 말이다. 

```
import sys
sys.float_info

sys.float_info(max=1.7976931348623157e+308, max_exp=1024, max_10_exp=308, min=2.2250738585072014e-308, min_exp=-1021, min_10_exp=-307, dig=15, mant_dig=53, epsilon=2.220446049250313e-16, radix=2, rounds=1)
```


### float형 숫자의 연산 
<kbd>+</kbd> , <kbd>-</kbd> ,<kbd> *</kbd> ,<kbd> /</kbd>, <kbd>//</kbd>,<kbd> %</kbd>, <kbd>**</kbd>가 있다.  

```
단, 음수 나눗셈은 주의 해야 한다. 
ex) 
10 // -3
=> -4 
why? --> -4 + 0.66667 이런식으로 간주하기 때문에 
```

### 자료형을 구별하는 기준 

```
┌─ Mutable    # 추가, 삭제가 가능한 경우 / 특징 : 메모리 번지 안바뀜, 재할당할 필요없음
└─ Immutable  # 추가, 삭제가 불가능한 경우 / 특징 : 재할당으로 메모리 번지 바뀜

Container ┌─ Homogeneous    # 요소들이 서로 같은 타입인 경우
          └─ Heterogeneous  # 요소들이 서로 다른 타입이 가능한 경우 
(요소가 1개 이상)

Sequence ┌─ Indexing   # 요소를 하나씩 출력
         └─ Slicing    # 요소를 한번에 여러개 출력
(순서가 있음)         
Mapping hash    # key값과 value를 갖는 Dictinary가 갖는 특징      
```

### Indexing

```python
a = '정지혁'
a[0]
: 정
```

### Slicing

```python
a = '정지혁'
a[0:3] or a[:3]
: 정지혁
a[-3:] or a[-0:]
:정지혁 
a[0:3:2]  # 양수일때 (맨 뒤에 오는 숫자 - 1) 을 하면 건너 뛰는 문자의 개수를 나타낸다
:정혁 
a[0:-4:-1]  # 음수일때 |맨 뒤에 오는 숫자 + 1|을 하면 건너 뛰는 문자의 개수를 나타내고 거꾸로 출력한다. 
:혁지정
a[:70] # 슬라이싱은 범위가 벗어나도 에러가 나지 않는다
:정지혁
```

### List vs Tuple 
**차이점** List는 수정, 삭제, 추가가 가능하고 인덱싱, 슬라이싱이 가능하지만, Tuple은 수정, 삭제, 추가가 불가능하고 인덱싱, 카운팅만 가능하다. 
{: .notice}

```python
x = [1]
type(x)
: list
y = (1)
type(y)
: int 

#하나의 요소를 갖는 튜플을 생성하려면 콤마를 적어줘야한다.
y = (1,)
```

### Set vs Dictionary 
**공통점** 둘다 집합의 성질을 띄어 중복허용이 불가능하고, 순서가 없다. 
{: .notice}

**차이점** set은 key값만 있는 반면 dictionary는 key, value쌍을 이뤄 mapping hash 타입을 이룬다.
{: .notice}

```python
s = {}
type(s)
:dict
# python이 처음 만들었을 때는 set이 없었기 때문에 공집합을 만들면 Dictionary로 간주한다.
 
# 그렇다면 set은 공집합을 어떻게 만드나?
s = set()
type(s)
: set 
```

<hr>

**Internals** Python은 -5부터 256까지 숫자는 재할당을 해도 메모리 번지가 바뀌지 않도록 인터널 기법을 사용한다. 많이 쓰이는 작은 정수들을 미리 할당해 놓음으로써 메모리 공간과 연산비용을 많이 아낄 수 있게된다. 
{: .notice}

[참고](https://mingrammer.com/translation-cpython-internals-arbitrary-precision-integer-implementation/)<br>

* Garbage Collection은 메모리 관리 기법 중 하나로, 프로그램이 동적으로 할당했던 메모리 영역 중에서 필요 없게 된 영역을 해제하는 기능이다.

### xxx = xxx 
<span style="background: orange">식별자 or 변수 = 식(Expression) </span><br>
<kbd>Expression</kbd>: 연산결과가 하나의 값으로 만들 수 있는 것 <br>
ex) 3 + 1 , float('inf') 등 ...  

### Expression vs Statement 

<kbd>Expression</kbd>은 값 또는 값들과 연산자를 함께 사용해서 표현해 하나의 값으로 수렴하는 것 <br>
이때 함수, 식별자, 할당 연산자 [], 등을 포함한다. <br>
그리고 Expression은 평가가 가능하기 때문에 하나의 값으로 수렴한다. <br>

* 여기서 평가라는 의미를 정확하게 알고 있어야 한다. 평가란 컴퓨터가 이해할 수 있는 기계 이진 코드로 값을 변환하면 리터럴의 형태가 달라도 그 평가값은 같게 되는 것을 말한다. 

ex)
```python
a, b = 4, 5
eval('1+2+3')
eval('a+b')
:6
:9
```
<br>
[참고](https://shoark7.github.io/programming/knowledge/expression-vs-statement.html)<br>

<br>
<kbd>Statement</kbd>는 예약어와 표현식을 결합한 패턴이다. <br>
그리고 실행가능한 최소의 독립적인 코드 조각을 일컫는다. <br>
<span style="color: orange">Statement</span>는 총 5가지 경우가 있다. <br>
1. 할당 (Assignment)
2. 선언 (Declaration)
3. 조건 (if)
4. 반복문 (for, while)
5. 예외처리

<br>
ex)
```python
for i in range(1, 20+1):
   exec('r' + str(i) + '=' +str(i))
```
**결론적으로** 모든 Expression은 Statement지만 어떤 Statement는 expression이지 않다. retrun 3 이런 구문은 평가를 통해 3의 값이 나오는 것이 아니기 때문이다.
{: .notice}


### 기타 내장 함수 
```
dir(obejct) : 어떠한 객체를 인자로 넣어주면 해당 객체가 어떤 변수와 메소드를 가지고 있는지 출력을 합니다. 
type(object) : 어떠한 객체를 인자로 넣어주면 해당 객체의 타입을 반환한다.
len(object) : 어떠한 객체를 인자로 넣어주면 해당 객체의 요소 갯수를 반환한다.
id(object) : 해당 객체가 저장되어 있는 메모리 위치를 반환한다. 
```

#### id함수로 보는 메모리 할당 

```python
x = 10 
y = 10 
hex(id(x))
:'0x7ffb006b9460'
hex(id(y))
:'0x7ffb006b9460'
# -5 ~ 256사이 숫자이기 때문에 재할당을 해도 메모리 주소가 변하지 않는다. 

x = 1000
y = 1000
hex(id(x))
: '0x1bc813b7650'
hex(id(y))
: '0x1bc813b73d0'

x = 2000 
hex(id(x))
: '0x1bc813b7db0'

# 새로운 식별자로 같은 값에 binding을 하거나 reassignment를 하게되면 메모리 주소값이 변경된다.  
```
<br>
※ 메모리 잘 쓰는 방법: &nbsp; [wikidocs](https://wikidocs.net/21057)
<br><br>

### 비교 연산자 

```python
1 == 3 
: False 
1 != 3 
: True 

'정지혁' < '천재'
: True 

[1,2] < [3]
: True 

# 첫번째 요소 끼리 비교후 같으면 그 다음 요소 비교 

[1,2] < 'a' 
: TypeError 

# 비교할 때는 같은 타입끼리 해야 한다. 

a = 1000 
b = 1000 

a is b 
: False 

# 같은 메모리 번지인지까지 따진다. 

'ㅈ' not in '정지혁'
: True 

1 in [1,2,3]
:True 

1 in '정지혁'
: TypeError

# 정수형과 리스트를 in 연산을 했을 때는 타입이 달라도 가능하지만 
# 정수형과 문자형은 불가능하다 
# 기본적으로 멤버쉽 연산자(in)는 container에서만 쓸 수 있고 문자열 일때는 문자열 끼리만 가능하다. 
```

### Error
1. NameError
- 값을 할당하지 않은 식별자를 사용했을 때 발생하는 에러 
2. IndexError
- 인덱스 값에서 벗어난 인덱스를 사용했을 때 발생하는 에러 
3. TypeError
- 서로 다른 타입간의 연산을 했을 경우 발생하는 에러 

**복습 시간**   18시 35분 ~ 20시 5분/ 총 1시간 30분  
{: .notice}

# 2019년 5월 2일 목요일 세번째 수업


### 할당문의 종류 6가지 
```
1. 기본 할당문 
- a = 1
2. Chain assignment 
- a = b = 1
3. Augmentation 
- a += 1 
4. Pakcing
5. Unpacking 
- Container 쪼개기
6. Global not local 
- global 이용하여 전역번수 접근, 변경하기 # 추천하지 않는 기능
```

* Unpacking 방법은 빅데이터 처리시 많이 쓰인다.

```python
# Chain assignment #

a = b = 2 
a
: 2
b
: 2 

b = 3 
a
: 2 
# 변수 어느 하나 재할당 한다고 같이 바뀌지 않는다

-- 주의 --
x = y = [1000,2000]
y.append(3000)
x
: [1000,2000,3000]
y
: [1000,2000,3000]
# 그러나 mutable일때는 같이 변하므로 주의해야 한다! 

# Augmentation #
a = 0
a += 1  # (재할당) 

# 다른 언어처럼 선증가, 후증가가 지원되지 않는다
++a  (X)
a++  (X)
그러나 # ++a는 에러가 나지 않는다 
Why?
# 앞에 있는 플러스를 문자열 취급하기 때문에??? 사실 잘 이해가 안됨...

# Packing 

x = 1,2,3
y = 1,

# Unpacking # 

x,y = 1,2  (O) 
x,y,*z = 1,2,3,4 (O)
*x, = 1,2,3 (O)
*a, = '정지혁' (O)
*u, = {'a':1,'b':2,'c':3,'d':4,'e':1} (O)  # 단, 키 값만 리스트 형태로 반환
*x, y = range(10) (O)

x, = 1,2 (X) # 왼쪽 식별자와 오른쪽 식의 갯수를 맞춰줘야 함
*x, y, *z = 1,2,3,4,5 (X)

# 오른쪽에 오는 식은 Container면 모두 가능 
# * (별표)는 나머지를 리스트로 반환, 그리고 * 두 개이상 못씀

#Global not local#

a = 1 

def name():
   global a 
   a += 1 
   return a
name()
: 2

def name(): 
   a = 1 
   a += 1
   return a
# 위 함수와는 같지 않음 / Why? 밑 함수에서는 a를 그냥 재할당한 것임
```
Packing & Unpacking: &nbsp; [blog](https://python.bakyeono.net/chapter-5-5.html)


### 조건의 형태 3가지 

```
1. if, else & and, or 
2. if, elif, else
3. 중첩 if 
```
<hr>
```python
a = 6 
if 0 < a < 10:
   print(True)
else:
   print(False)

```

#### AND & OR

1. A and B  
- A가 참(Truely)이면 B 체크 => B 반환 
- A가 거짓(Fasly)이면 B 체크 X => A 반환 
2. A or B
- A가 참이면 B 체크 X => A 반환 
- A가 거짓이면 B 체크 => B 반환 


### 반복문 2가지 

```
1. for 
2. while 
```

> 여기서 개념 하나 추가 Iterable! Iterable은 순회, 반복 가능한 것을 말한다. 
그래서 for문에 쓸 수 있다.
보통 container이면 Iterable ※ 아닌것도 있지만 아주 나중에 배운다.

```python
# for # 

for i in {'a':1,'b':2}.values():
   print(i)

for i, j in {'a':1,'b':2}.items():
   print(i,j) 

# in 뒤에 오는 것은 Container, 여러개의 요소를 갖고 있는것은 반복문이 가능하다

# while # 

i = 0 
while i < 10:
   i+=1
   print(i)
   if i == 5:
      break   # 탈출문   
else: 
   print("완료")

# continue는 continue 밑은 실행하지 않고 넘어간다 

```
* for문은 반복횟수를 알때 주로 사용하고, while문은 반복횟수가 정해지지 않았을 때, 모를때 주로 사용한다. 

* 모든 for문은 while문으로 바꿀수 있지만, 모든 while문은 for문으로 바꾸기 어렵다.

#### else문 3가지 쓰임 
1. 조건문에서     => 조건에 맞지 않는 경우  
2. 반복문에서     => 반복문이 정상 완료 되고나서 실행
- 0번도 수행이라고 간주하기 때문에 else문이 실행될 수 있다
3. 예외처리할 때  

#### Dictionary view

1. key
2. values
3. items 


#### 구문 실행시 실행시간 알아보기 

```python
%%timeit 

for i in range(3,10,2):
    for j in range(1,10):
        print(i,"*",j,"=", i*j)
    print()

# 391 µs ± 31.8 µs per loop (mean ± std. dev. of 7 runs, 1000 loops each)
```

#### Python에서 중요한 두 가지 (Two A) 
1. Abstraction
2. Automation 

python 내부 구조 확인 가능 사이트: [pythontutor](http://pythontutor.com)

**복습 시간**   17시 45분~ 18시 43분/ 총 58분 
{: .notice}




# 2019년 5월 3일 금요일 네번째 수업


### 선언문 2가지

```
1. 함수선언 
2. 클래스 선언
```

```python
def name(arg1, arg2 = 2):
   pass       # 에러가 나지 않게 형태만 갖추기
   
name(3)       # 함수 호출(콜)
: (3,2)
```

**Argument**  인자로 어떤 데이터 타입도 올 수 있다. 단 튜플을 넣을 때 괄호를 꼭 써줘야 한다  
{: .notice}

> Python의 또다른 장점 'return'문은 생략 가능하다


### Parameter vs Argument 

Parameter | Argument 
--------|-------
선언문에서 괄호 안 | 호출문에서 괄호안


### Argument 사용법 

```
1. Positional + keyword
2. Only Positional 
3. Only Keyword
4. Variable Positional
5. Variable keyword 
6. Variable Positional + Variable keyword
```

```python 
# Only Positional #
def name(a,b):
   ''' 함수 설명 '''   # Docs String => Shift + Tab 하면 설명이 그대로 나온다
   return a, b        #                참고로 함수 설명에 ( / )가 있을 경우 Positional 방식이라는 뜻
name(1,2)
:(1,2)
 
name(b=3, a=4)
:(4,3)

# Only Keyword #
def name(*,a,b):   
   return a + b 

# Variable Positional#
def name(*a):
   return a[0],a[1:3],a[3:]
name()
:()
name([1,2,3],(4,5,6),{'a':1,'b':2})
:([1, 2, 3], ((4, 5, 6), {'a': 1, 'b': 2}), ())

# !주의! 할당할때 *는 list를 반환하고 함수에서 *는 tuple로 반환한다

# Variable Keyword #
def name(**a):
   return a

name(a = ['a',2], b = {'a':'a','b':2}, c = range(3),d = 5)
:{'a': ['a', 2], 'b': {'a': 'a', 'b': 2}, 'c': range(0, 3), 'd': 5}


# Variable Positional + Variable Keyword #
def name(*b, **a):
   return b, a 
name(2,3,4,5, a = 9, b = 3, c = [1,2])    # !주의! keyword를 쓰기 시작하면 끝까지 keyword를 써야한다 
:((2, 3, 4, 6), {'a': 9, 'b': 3, 'c': [1, 2]})
```

> Python에서는 Parameter로 받아 올때 Type을 지정해주지 않는다.
Why? Python 철학중 EAFP라는 것이 있는데 이는 '허락보다는 용서를 구하기 쉽다'로 
부부관계를 예시로 설명하면 이해하기 쉽다. 
결혼하고 나면 보통 남자든 여자든 비싼 사치품을 사는 것이 쉽지 않다. 
이때 사치품을 사려고 하는 입장의 사람은 결정해야한다. 
사고 혼날 것인가. 
허락을 받을 것인가.
전자가 더 실행하기 쉽고 빠르다는 것이 Python의 철학인 것이다. 

**Python Tip1** 파이썬은 오버로딩이 안된다. 즉 같은 함수 이름을 여러개 정의하여 매개변수를 달리하여 사용하는 기법이 허용이 되지 않는다. 파이썬은 오버로딩을 지원하지 않음으로써 속도를 개선했다. 단, 오버라이딩은 사용 가능하다. (매소드 재정의)
{: .notice}


* 오늘의 명언 
<span style="color: orange">자동이 많으면 제약이 많다.</span>


### 함수의 특징 3가지 

```
1. return이 반드시 있어야 한다 
- python에서는 return을 생략하면 None을 반환하도록 되어 있다 
2. 함수 안에 또 다른 함수를 선언할 수 있다 
3. Global, Local 
- 함수 안에 없는 값을 return 하게 될 경우 가까운 Global 식별자를 return 
- Global 식별자이름 하게 되면 접근, 수정이 가능하다
- 함수 밖에서 함수 안의 식별자에 접근, 수정이 불가능하다 
```
#### 함수안의 함수 
```python
def a():
   def b():
      return 3
   return b
   
a()
:<function __main__.a.<locals>.b()>
a()()
:3

def a():
   def b():
      return 3
   return b() 

a()
:3

# 둘의 차이가 있다 위에것은 함수를 리턴하는 것이고 밑에꺼는 함수 안에서 함수를 호출하여 값을 리턴 
```


**Python Tip2**  return 값이 있는지 없는지 확인하는 방법 1. type() 2. 값을 저장해서 확인하기 
{: .notice}

**Python Tip3**  함수를 리스트에 넣어서 계산을 편리하게 할 수도 있다.
{: .notice}

**Python Tip4**  jupyter에서는 두 가지로 호출할 수 있는 함수인지 판단 가능 1. callable 2. 출력 
{: .notice}

**Python Tip5**  Python keyword는 총 35개다.
{: .notice}

```python
import keyword

cnt = 0 
for x in keyword.kwlist:
   cnt += 1
print(cnt)
:35
```

### 신기한 함수 
```python
import matplotlib.pyplot as plt 

plt.plot([1,2,3,4,5],[9,3,7,3,9])

# 설명에서 plot[x] => 여기서 [] 대괄호는 리스트가 아니고 옵션이라는 뜻
```
![result](https://user-images.githubusercontent.com/33630505/57130958-1e486280-6dd6-11e9-9ee5-2426f4064ba1.JPG)


#### 추가 공부 
1. 동적 프로그래밍에 대해서 찾아보기 
2. 피보나치 다른 방법 공부해보기 
3. 과제란에 올려주시는거 문제 풀어보기 
4. 여태까지 공부했던건 tree형태로 가지치기 map 그려보기
5. Python 철학 처음부터 끝까지 정독해보기 

**복습 시간**   17시 28분 ~ 19시/ 총 1시간 32분   
{: .notice}


# 2019년 5월 7일 화요일 다섯번째 수업

![function](https://user-images.githubusercontent.com/33630505/57440852-b6859200-7283-11e9-92fd-6b7b59ca7de9.png)

### First class function 

> 함수를 값처럼 사용할 수 있다. 

### Higher-Order-Function

> 함수를 리턴값으로 쓰는 함수, 함수를 인자로 쓰는 함수


### 함수의 인자로 함수가 들어가는 경우 

```python
def a(x):
   return x + 1
   
list(map(a,[1,2,3]))
:[2,3,4]

temp = []
for i in [1,2,3]:
   temp.append(i+1)
else:
   print(temp)
:[2,3,4]

def b(x):
   return x > 3
   
list(filter(b,[1,2,3,4,5,6]))) 
:[4,5,6]

```

> filter는 predicate function => True or False를 되돌려 주는 함수 

**Python Tip1**  shift + tab 했을 때 나오는 *iterables와 iterable는 차이가 있다. 별표가 있는 것은 iterable 여러개가 오고 별표가 없는 것은 한개만 온다
{: .notice}

### 별표(*)의 총 7가지 방법 

```
1. Unpacking 방법에서 나머지 
2. Only keyword
3. Variable Positional
4. Variable Keyword
5. Unpacking (벗겨내기, 리스트 쪼개기)
6. 
7. 
```

### Annotation

```python
def xx(x:int) -> int:
   return x 
   
xx.__annotations__ 
{'x': int, 'return': int}
# 타입을 표시해줌 

xx(3.0)
xx('hi') 
# 둘다 가능 
```
<br>

Parameter | Argument 
--------|-------
키워드 방식이 온다 | 식이 들어갈 수 있다

<br>

```python
n = 0 
def a(n):
   return n
a(n or 3)
# 인자에 디폴트를 사용할 수는 없지만 이렇게 흉내는 낼 수 있다
```
### 식의 종류 

1. 조건식 
- 3 if a > 0 else 6 
- a(3 if a > 0 else 6)
2. 함수식  
3. 반복식 

**Python Tip2**  Local, Argumentation은 stack에 저장되고 Parameter는 heep영역에 들어간다
{: .notice}

**Python Tip3**  default값에 mutable값을 넣으면 값을 공유한다?, 값이 고정된다?
{: .notice}

```python
import time 
time.time()
1557232234.682229 # 수행할 때마다 값이 변한다

def a(t=time.time()):
   return t 
a()
1557232228.6397958 # 값이 고정된다 
```

**Python Tip4**  bytearray와 frozenset은 리터럴이 없다
{: .notice}

### Return의 3가지 형태 

1. 자기는 변하지만 return이 None
2. 자기 자신이 변하지 않고 return 값이 있다 
3. 자기 자신도 변하고 return 값도 있다

```python 
# 1 
def xx(y, x=[]):
   return x.append(y)
# 사실 엉터리 코딩 x.append(y)는 None을 리턴하고, 
# 함수 밖에서 x 리스트에 접근도 할 수 없기 때문에

# 2 
def xx(y, x=[]):
   x.append(y)
   return x 
# xx함수를 호출 할때마다 x 리스트가 계속 변한다 

def xx(y):
   x = []
   x.append(y)
   return x
# xx함수를 호출하면 원소가 하나인 리스트 반환
```

일급 객체: [git blog](https://gyukebox.github.io/blog/%ED%8C%8C%EC%9D%B4%EC%8D%AC%EC%9C%BC%EB%A1%9C-%EC%95%8C%EC%95%84%EB%B3%B4%EB%8A%94-%EC%9D%BC%EA%B8%89-%EA%B0%9D%EC%B2%B4first-class-citizen/), [tistory](https://rednooby.tistory.com/113)<br>

클로저: [git blog](https://nachwon.github.io/closure/)

### 파이썬 변수의 유효 범위(Scope)

> 유효 범위 규칙(Scope Rule)은 변수에 접근 가능한 범위, 변수가 유효한 문맥범위를 정하는 규칙 

#### LEGB 

```
1. Local : 함수 내 정의된 지역변수 
2. Enclosing Function Local : 함수를 내포하는 또다른 함수 영역 
- 함수 안의 함수가 있는 경우 함수와 함수 사이
3. Global : 함수 영역에 
4. Built-in : 내장 영역 
- 함수 안의 함수가 있는 경우 함수안의 함수에서 함수 밖의 변수를 사용?

우선순위 => L > E > G > B 
```

#### LEGB 우선순위 확인 예제 
```python
x = 'global'
def outer():
    #x = "local"
    
    def inner():
        #nonlocal x
        #x = "nonlocal"
        #print("inner:", x)
        return x
    
    inner()
    #print("outer:", x)
    return x

outer()
```

**Python Tip5**  함수 중첩은 3번 이상 하지 않는 것이 좋다.
{: .notice}


### 신기한 기능 

```python
import seaborn as sns
tips = sns.load_dataset('tips')

tips.head(10) # 앞에 10개만 보여줘
tips.tail(10) # 뒤에 10개만 보여줘 
tips.sample(10, replace = True) # 랜덤으로 10개 보여줘
```
#### 랜덤 10개 
![python](https://user-images.githubusercontent.com/33630505/57372344-584ba700-71d0-11e9-86f1-21da17a4fc73.JPG)

**복습 시간**  19시 10분 ~ 21시 40분 / 총 2시간 30분  
{: .notice}


# 2019년 5월 9일 목요일 여섯번째 수업


## 함수형 패러다임 

멀티 프로세싱 기법에 최적화된 패러다임 

## 반복을 줄이는 5가지 방법 
(for문을 최대한 쓰지 않고) 

```
1. Iterator 
- 메모리 효율적, 속도 빠름 
- 실행시에 메모리 할당 
2. Generator
3. Comprehension 
- for를 쓰지만 for를 쓰지 않는 기법
4. Recursive function
- 메모리 효율, 속도면에서 성능이 좋지않아 사용안함 
```

**iterable** 1. iterator로 바꿀 수 있는 2. 순회, 반복가능 (요소 하나씩 뽑아냄) 3. for 뒤에 사용할 수 있는 container 
{: .notice}

## 왜 함수형 패러다임에서 반복을 줄여야 하는가? 

<span style="background-color: orange">for문 처럼 대입하는 것은 함수형 패러다임에 맞지 않고 수학적 증명과는 거리가 있기 때문이다. </span>

### Iterator 

<span style="background-color:orange">데이터 스트림을 표현하는 객체, next()메소드를 사용하여 다음 요소를 가져온다</span>

```python
a = [1,2,3]
b = iter(a)
next(b)

:1 
# 실행할 때마다 index 0번지 부터 하나씩 뽑아낸다
```

### 함수형 프로그래밍의 특징 

```
1. 코드가 간결해진다 
- 내부 구조를 몰라도 input, output만 알면 사용 가능
2. 수학적으로 증명이 가능하다
3. for, while문을 자제하고 iter를 사용한다 
4. 수학적 증명이 필요하기 때문에 구현이 어렵다 
- 단, python에서는 multi paradiam이기 때문에 적절히 혼용 가능
5. 디버깅, 테스트가 용이하다 
6. 모듈성, 결합성이 있다.
7. mutable은 처리하지 않는다 
```

### Generator 

<span style="background-color:orange">Iterator를 생성해주는 Function, 그리고 일반 함수와 비슷해 보이지만 Generator는 yield를 포함한다는 점에서 차이가 있다</span>

두 가지 방법으로 만들 수 있다
1. tuple
2. yield 

```python
# tuple로 만들기 
a = (x for x in range(10))
a 

: <generator object <genexpr> at 0x000001EBD55D0DE0>

# yield로 만들기 
def x():
   yield 1
   yield 2 
y = x()
next(y)

:1 
```

**주의** iterator와 generator는 scope를 초과하면 StopIteration 에러가 뜬다. 
{: .notice}


### Iterator vs Generator & Generator vs Function 

<span style="color: skyblue">Iterator vs Generator</span>

Iterator는 반복가능한 객체 그리고 데이터 스트림을 표현하는 객체라고 한다. <br>
예를 들어 list는 반복가능한 자료형 즉 iterable이지만 iterator는 아니다. <br>

```python
for x in [1,2,3]:
   print(x)
```
이처럼 in 다음에 iterable이 오면 반복해서 요소 하나씩 꺼낼 수 있긴 하다<br>
<span style="color:red">하지만</span> list는 iterator는 아니라고 했다<br> 
그렇다면 어떻게 list가 iterator처럼 처리되는가? <br>
<span style="color:red">그 이유는</span> in 다음에 iterable이 오면 iter없이 iterator로 변환 해주기 때문이다
<br>
Generator는 iterator를 생성해주는 Function <br>
따라서 Generator와 iterator는 비슷하다 <br>
하지만 역할이 다르기 때문에 명칭도 다른것!<br>
<br>
<span style="background-color: orange">생성 방식에서 차이가 있고 Iterator는 객체 Generator는 함수</span><br>
<span style="background-color: orange">Generator는 tuple, yield로 만들고 Iterator는 liter() 함수로 만든다</span>
<br>
<span style="color: skyblue">Generator vs Function</span>

Generator <br>

Iterator를 만들어주는 것 <br>
반복 가능한 객체를 만들어주는 함수<br>

```python
def generator():
   while True:
      yield from [1,2,3,4] # Cycling 기법 
e = generator()
next(e)
:1       # 실행할 때마다 1부터 4까지 계속 반복해서 return

# yield는 return과 비슷하다고 생각하면 된다
```

일반적으로 함수는 사용이 종료되면 결과값을 호출한 곳에 반환해주고 함수 자체를 종료 시킨 후 메모리상에서 사라진다 <br>
하지만 yield를 사용할 경우 그 상태로 <span style="color:red">정지</span> 되며 반환 값을 next()를 호출한 쪽을 전달한다<br>
함수 호출이 종료되면 메모리상의 내용이 사리지지 않고 다음 함수 호출까지 대기한다<br>
다음 함수 호출이 발생할 경우 <span style="color:red">yield이후 구문부터 실행된다</span>
<br>

여기서 generator를 사용하는 이유를 알 수 있다 <br>
generator를 사용하면 호출한 값만 메모리에 할당되므로 메모리를 효율적으로 사용할 수 있게된다
<br>
이러한 기법을 <span style="color: orange">Lazy Evaluation</span>이라고 한다 <br>
계산 결과 값이 필요할 때까지 계산을 늦추는 방식 <br>

참고: [tistory](https://bluese05.tistory.com/56)<br>

### Comprehension

<span style="background-color:orange">Iterable한 객체를 생성하기 위한 방법</span>
```
1. List
2. Set
3. Dictionary
```

```python
# list 

# for 앞에는 식이 오면된다
a = [(x,y) for x in range(10) for y in range(20)]
: [(0,0),(0,1),(0,2),......(9,19)]

b = {x+1 for x in range(10) if > 5}
: {7, 8, 9, 10}

c = {x:1 for x in range(10) if x>5}
: {6: 1, 7: 1, 8: 1, 9: 1}

d = (x for x in range(10))
d
: <generator object <genexpr> at 0x000001EBD5645DE0>
```

### Recursive function

재귀함수 <br>

```python
def fib(num): 
    if num < 3:
        return 1
    return fibB(num-1) + fibB(num-2)
fib(10)  # 10번째 항   (1 1 2 3 5 8 13 21 34 55)
: 55 
```


**복습 시간**  18시 ~  19시 50분/ 총 1시간 50분
{: .notice}



# 2019년 5월 10일 금요일 일곱번째 수업

<span style="background-color:orange">함수의 중첩으로 가능한 것들</span>
```
1. Closure

2. Decorator 
```

## Decorator




## Closure


Closure: [github blog](https://nachwon.github.io/closure/)


## Decorator vs Closure 




**Python Tip1** locals(), globals() 함수는 함수내에서 사용하면 메모리상에 올라간 local, global 변수를 각각 확인 할 수 있다
{: .notice}

```python
x = 10
def a():
   y = 20
   def b():
      a = 1
      print(locals())
      b = 2
   return b()
a()
:{'a':1}
# b = 2는 print문 출력 이후에 있기 때문에 locals에 포함되있지 않다
 선언할 때는 모든 것이 메모리에 할당 되지만 실행할때는 순서대로 할당되기 때문이다
```

## name, namespace, module 그리고 __name__

<kbd>name</kbd>은 말 그대로 이름을 붙여주는 즉, 변수명 혹은 식별자라고 생각하면 된다<br>
<kbd>module</kbd>은 파이썬 코드를 담고 있는 파일이다, 좀 더 자세하게 말하면 클래스, 함수, 변수명의 리스트가 들어 있다고 보면 된다 <br>
<kbd>namespace</kbd>는 names(변수명들)을 담을 수 있는 공간이다, 모듈은 자신의 유일한 namespace를 갖고 있으며 모듈의 namespace이름은 보통 모듈이름과 같다. 그래서 동일한 모듈내에서 동일한 이름을 가지는 클래스나 함수를 정의할 수 없다. 또한 모듈은 각각 독립적이기 때문에 동일한 이름을 갖는 모듈을 갖을 수 없다. <br>

<br>
> import를 통해 namespace와 __name__에 대해서 자세히 알아보자 

### import 방법은 3가지가 있다

```
1. import <module_name>
- 모듈의 name을 prefix로 사용함으로써 모듈의 namespace에 접근할 수 있다 
2. from <module_name> import <name,>
3. from <module_name> import *
```
<br>

```python

# 1. import <module_name>
import sys 
sys.path

# sys는 모듈, path는 sys모듈의 namespace에 담겨 있는 name 
# 모듈 prefix sys를 통해 namespace path에 접근

2. from <module_name> import <name,>
from sys import path
path
sys.path

# 모듈 prefix를 사용하거나 사용하지 않고 둘다 접근 가능하다 
# 단, del path를 하거나 name을 재정의 하게되면 모듈의 name을 사용할 수 없게된다
# 몇개의 name만 필요하고 name를 명확하게 구분할 수 있는 상황에서는 써도 무관하다

3. from <module_name> import *
from sys import*
sys.path
path

# 2번방법과 동일, 그러나 모듈에 있는 모든 name을 직접 현재 namespace로 가져오게된다 
# 말할 것도 없이 전체를 import하면 name을 쓰는데 제약이 많이 생긴다
```

> 그렇다면 import와 namespace를 알아보았으니 이젠 __name__을 알아보자 
 
import를 하면 해당 모듈의 names를 namespace에 dict타입으로 할당하는 것을 보았다<br>
이때 import한 모듈의 __name__은 파일명이 된다 <br>
<br>
```python
from sys import *
sys.__dict__  # namespace 불러오기

'__name__': 'sys',
 '__doc__': "This module.......... 
```
<br>
이번엔 import를 하지 않고 main script(최상위 스크립트 환경)에서 직접 shell에서 실행하는 경우에 python interpreter가 최초로 파일을 읽어 실행하는 경우를 생각해보자 <br>
이때는 모듈이름 해당 파일 이름이 아닌 __main__가 된다 <br>

```python
__name__

'__main__
```
<br>

> 따라서 만약에 '이 파일이 interpreter에 의해 실행되는 경우라면' 이라는 의미를 갖는다

```python
if __name__ == '__main__':
   main()
   
if __name__ == '__main__':
	print 'This program is being run by itself'
else:
	print 'I am being imported from another module'
```

__name__의 의미 : [tistory](https://pinocc.tistory.com/175)<br>



참조와 참조변수 : [tistory](https://dohe2014.tistory.com/entry/%EC%B0%B8%EC%A1%B0reference%EC%99%80-%EC%B0%B8%EC%A1%B0%EB%B3%80%EC%88%98reference-variable)<br>

**복습 시간**  18시 22분 ~ 20시 / 총 1시간 38분
{: .notice}
