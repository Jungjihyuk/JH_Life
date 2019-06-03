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
: 언어마다 각각의 장단점이 있기 때문이다 <br>
그리고 더 구체적으로는 언어마다 특화되있는 분야가 있기 때문이다 <br>

<br>
## 왜 AI에는 파이썬인가?
```
Life is short, you need! 
파이썬의 슬로건에서 보여주듯이 
파이썬은 개발 속도가 빠르기 때문에 생산성이 좋다! 

1. 생산성
- Efficient  --> 빠르고 체계적인 일처리가 가능하다  
- Effective  --> 원하는 결과를 가져다 준다

2. 멀티 패러다임 
- 절차 지향, 객체지향, 함수지향 프로그래밍이 모두 가능하다 

3. 연구자 친화적 언어, 개발자 친화적 언어  
- 언어중에서 속도가 느린 언어에 속하지만 개발속도는 빠르고 함수적 프로그래밍이 가능하다

그리고 이 파이썬은 크게 3가지 분야에서 유리하다. 
첫번째 시스템 자동화 분야
두번째 웹
세번째 데이터 사이언스 
```
* ※ 이 수업은 Data Science분야를 집중해서 다뤄볼 것이다. <br>
<br>
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

* ※이번 수업은 c로 만든 python으로 사용한다 <br>

* ※python3.3 부터 유니코드로 인한 속도가 개선되었다. <br>
<br>


## Interpreter vs Compiler 

![interpreter vs compiler](https://user-images.githubusercontent.com/33630505/56888295-93eac080-6aae-11e9-977b-2db7ce9cd580.JPG)
<br>
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

<br>

## 자료형 숫자, 문자  

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
'정지혁' * 3 
: 정지혁정지혁정지혁 

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

## 자료형
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

### 정수형 숫자 범위 

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
<br>
**.(점)은 부동소수점을 결정하는 리터럴** <br>
> 리터럴은 데이터 타입을 결정하는 문자를 일컫는 말이다. 

<br>

```
import sys
sys.float_info

sys.float_info(max=1.7976931348623157e+308, max_exp=1024, max_10_exp=308, min=2.2250738585072014e-308, min_exp=-1021, min_10_exp=-307, dig=15, mant_dig=53, epsilon=2.220446049250313e-16, radix=2, rounds=1)
```
<br>

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
(요소가 1개 이상인 데이터 구조)

Sequence ┌─ Indexing   # 요소를 하나씩 출력
         └─ Slicing    # 요소를 한번에 여러개 출력
(순서가 있음)         
Lookup  ┌─ Mapping hash    # key값과 value를 갖는 Dictinary가 갖는 특징    
        └─ set  # 순서가 없는 고유한 원소들의 집합 
(key값으로 이루어진 데이터 구조)
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
:'정지혁'
a[-3:] or a[0:]
:'정지혁' 
a[0:3:2]  # 양수일때 (맨 뒤에 오는 숫자 - 1) 을 하면 건너 뛰는 문자의 개수를 나타낸다
:'정혁' 
a[::-1]  # 음수일때 |맨 뒤에 오는 숫자 + 1|을 하면 건너 뛰는 문자의 개수를 나타내고 거꾸로 출력한다. 
:'혁지정'
a[:-3:-1]
:'혁지'
a[:70] # 슬라이싱은 범위가 벗어나도 에러가 나지 않는다
:'정지혁'
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

<br>

### xxx = xxx 
<span style="background: orange">식별자 or 변수 = 식(Expression), statement </span><br>
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
# statement
for i in range(1, 20+1):
   exec('r' + str(i) + '=' +str(i))

# r1, r2 ...r20 까지 1,2,...20 할당 
```
**결론적으로** 모든 Expression은 Statement지만 어떤 Statement는 expression이지 않다. retrun 3 이런 구문은 평가를 통해 3의 값이 나오는 것이 아니기 때문이다. ex) exec('1+2')는 문제 없지만 eval('a=3')는 오류가 난다 
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
4. KeyError 
- dictionary에서 없는 key값으로 접근할때 발생하는 에러 
5. AttributeError 
- 존재하지 않는 Attribute에 접근하려고 할 때 발생하는 에러 
6. UnboundLocalError
- 할당하기 전에 지역변수를 참조했을 때 발생하는 에러 

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
6. Global , nonlocal 
- global 이용하여 전역번수 접근, 변경하기 # 추천하지 않는 기능
- nonlocal은 함수 중첩시 함수와 함수 사이 변수
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

#Global  nonlocal#

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

def name(t):
	a = t 
	print(a)
	def name2():
		nonlocal a 
		a += 1
		print(a)
	return name2()

name(3)
: 3
  4
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


<span style="color: red">container이지만 Iterable이 아닌것이 set인가?? iterable의 조건중 __ iter__랑 __ getitem__ 두가지가 있어야 되는데 set은 __ iter__ 한가지 밖에 없다 왜지? 찾아보자 </span>

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


## 선언문 2가지

```
1. 함수 선언 
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

<br>
## Parameter vs Argument 

Parameter | Argument 
--------|-------
선언문에서 괄호 안 | 호출문에서 괄호안
키워드 방식이 온다 | 식이 들어갈 수 있다

<br>
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
# Positional + Keyword #
def name(a,b):
   ''' 함수 설명 '''   # Docs String => Shift + Tab 하면 설명이 그대로 나온다
   return a, b        #                참고로 함수 설명에 ( / )가 있을 경우 Positional 방식이라는 뜻
name(1,2)
:(1,2)
 
name(3, b = 4)
:(3,4)

name(a=1,b=2)
:(1,2)

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

**positional only** <br>
[python](https://discuss.python.org/t/pep-570-python-positional-only-parameters/1078)

> Python에서는 Parameter로 받아 올때 Type을 지정해주지 않는다.
Why? Python 철학중 EAFP라는 것이 있는데 이는 '허락보다는 용서를 구하기 쉽다'로 
부부관계를 예시로 설명하면 이해하기 쉽다. 
결혼하고 나면 보통 남자든 여자든 비싼 사치품을 사는 것이 쉽지 않다. 
이때 사치품을 사려고 하는 입장의 사람은 결정해야한다. 
사고 혼날 것인가. 
허락을 받을 것인가.
전자가 더 실행하기 쉽고 빠르다는 것이 Python의 철학인 것이다. 

<br>

**Python Tip1** 파이썬은 오버로딩이 안된다. 즉 같은 함수 이름을 여러개 정의하여 매개변수를 달리하여 사용하는 기법이 허용이 되지 않는다. 파이썬은 오버로딩을 지원하지 않음으로써 속도를 개선했다. 단, 오버라이딩은 사용 가능하다. (매소드 재정의)
{: .notice}


* 오늘의 명언 
<span style="color: orange">자동이 많으면 제약이 많다.</span>

<br>
## 함수의 특징 3가지 

```
1. return이 반드시 있어야 한다 
- python에서는 return을 생략하면 None을 반환하도록 되어 있다 
2. 함수 안에 또 다른 함수를 선언할 수 있다 
3. Global, Local 
- 함수 안에 없는 값을 return 하게 될 경우 가까운 Global 식별자를 return 
- Global 식별자이름 하게 되면 접근, 수정이 가능하다
- 함수 밖에서 함수 안의 식별자에 접근, 수정이 불가능하다 
```
### 함수안의 함수 
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

First class function/Higher order function 관계 그림 수정 

일급 객체: [git blog](https://gyukebox.github.io/blog/%ED%8C%8C%EC%9D%B4%EC%8D%AC%EC%9C%BC%EB%A1%9C-%EC%95%8C%EC%95%84%EB%B3%B4%EB%8A%94-%EC%9D%BC%EA%B8%89-%EA%B0%9D%EC%B2%B4first-class-citizen/), [tistory](https://rednooby.tistory.com/113)<br>


## First class function 

> 함수를 값처럼 사용할 수 있다. 

<br>
## Higher-Order-Function

> 함수를 리턴값으로 쓰는 함수, 함수를 인자로 쓰는 함수

<br>
## 함수의 인자로 함수가 들어가는 경우 

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

<br>

**Python Tip1**  shift + tab 했을 때 나오는 *iterables와 iterable는 차이가 있다. 별표가 있는 것은 iterable 여러개가 오고 별표가 없는 것은 한개만 온다
{: .notice}

<br>
### 별표(*)의 총 7가지 방법 

```
1. Unpacking 방법에서 나머지 
2. Only keyword
3. Variable Positional
4. Variable Keyword
5. Unpacking (벗겨내기, 리스트 쪼개기)
6. 
7. import에서 모두 
```
<br>
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

### 인자에 default값 넣는 꼼수 
```python
n = 0 
def a(n):
   return n
a(n or 3)
# 인자에 디폴트를 사용할 수는 없지만 이렇게 흉내는 낼 수 있다
```
<br>
## 식의 종류 

1. 조건식 
- 3 if a > 0 else 6 
2. 함수식  
- (lambda x: x + 1)(2)
- (lambda x, y=1: x + y)(3)
- (lambda *x: x)(4,1,2)
- list(map(lambda a:a+8, [1,2,3,4,5]))
3. 반복식 
- (x for x in range(10))

```python
# 조건식 + 반복식 

integer = [1,-1,4,0,44,-34,-42,14]
['양수' if i > 0 else ('음수' if i < 0 else 0) for i in integer]
list(map(lambda i: '양수' if i > 0 else ('음수' if i < 0 else 0), integer))

: ['양수', '음수', '양수', 0, '양수', '음수', '음수', '양수']
```

<br>

**Python Tip2**  Local, Argumentation은 stack에 저장되고 Parameter는 heap영역에 들어간다
{: .notice}

**Python Tip3**  default값에 mutable값을 넣으면 값을 공유한다?, 값이 고정된다?
{: .notice}

<br>

```python
import time 
time.time()
1557232234.682229 # 수행할 때마다 값이 변한다

def a(t=time.time()):
   return t 
a()
1557232228.6397958 # 값이 고정된다 
```
<br>

**Python Tip4**  bytearray와 frozenset은 리터럴이 없다
{: .notice}
<br>

### Return의 3가지 형태 

```
1. 자기는 변하지만 return이 None
2. 자기 자신이 변하지 않고 return 값이 있다 
3. 자기 자신도 변하고 return 값도 있다
```

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
<br>

## 파이썬 변수의 유효 범위(Scope)

> 유효 범위 규칙(Scope Rule)은 변수에 접근 가능한 범위, 변수가 유효한 문맥범위를 정하는 규칙 

### LEGB 

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


#### 추가공부 

1. 변수, 인자와 힙, 스택간의 관계


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


## Closure

Closure: [github blog](https://nachwon.github.io/closure/)


## Decorator

> 함수를 추가, 수정해서 재사용 가능하게 해주는 것

```python


```

## Closure  vs  Decorator 




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

```python
1. import <module_name>
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
Namespace Binding: [slideshare](https://www.slideshare.net/dahlmoon/binding-20160229-58415344)<br>
<br>

**__name__**<br>

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

'__main__'
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


## Python의 모든 것은 Object(객체)이다

<span style="background-color: orange">Object</span>는 python이 data를 추상화 한 것이다<br>
쉽게말해 프로그래밍으로 구현될 대상, 현실에 존재하거나 상상가능한 대상을 특징지어 구현될 대상이라고 할 수 있다<br>
그리고 python 프로그램의 모든 data는 객체나 객체간의 관계로 표현된다<br>

> John von neumann's stored program computer model을 따르고 또 그 관점에서 코드 역시 객체로 표현된다 

### 객체를 구현하려면? 

객체를 구현하기 위한 설계도 및 틀을 <span style="color:red">Class(클래스)</span>라고한다<br>
<br>
Class를 실제로 프로그래밍할때 사용하려면 클래스 선언, 메모리 할당, mapping 3가지 단계가 필요하다<br>
이해를 돕기 위해 java의 경우를 예로 들겠다 <br>

```java
package test;

import test.Add;                                 // 1. 선언된 클래스 import (클래스 선언) 

public class Test{
	public static void main(String[] args){
		Add add = null;                  // 참조변수 선언 
		add = new Add();                 // 참조변수에 인스턴스에 대한 참조(참조값) 할당
	        //Add add = new Add(); 위와 동일 // 메모리에 생성되어 저장된 객체 처리 가능
		                                 // add는 레퍼런스 변수, 인스턴스를 가리키는값
						 // 참조변수를 사용하여 멤버변수, 메소드 접근가능
		System.out.print(add.sum(3,4));
	}
}
```

```
1. 클래스 사용을 위해 클래스 선언
2. 클래스 사용시 메모리에 생성 
3. Index table에 참조변수와 메모리 연결을 위한 주소를 매핑하는 참조값이 만들어진다
4. 참조값은 JVM이 자동적으로 생성 
5. 참조값을 사용하게되면 참조값에 연결된 메모리 즉, 인스턴스를 사용한다는 것 

참조 ≒ 참조값(Hash code)
```

> 그렇다면 Python에서 객체의 의미를 살펴보자 

```python
a = 1
print(type(a))
a = 3.2 
print(type(a))
print(a)
a.__class__

: <type 'int'>
  <type 'float'>
  3.2
  int

# Python에서는 선언과 할당을 동시에 하면서 
# 할당값에 의해 변수의 타입(객체의 타입)이 결정되고 naming된 변수 이름이 인스턴스가 되는 것이다
```


참조와 참조변수 : [tistory](https://dohe2014.tistory.com/entry/%EC%B0%B8%EC%A1%B0reference%EC%99%80-%EC%B0%B8%EC%A1%B0%EB%B3%80%EC%88%98reference-variable)<br>


**복습 시간**  18시 22분 ~ 20시 / 총 1시간 38분
{: .notice}



# 2019년 5월 13일 월요일 여덟번째 수업

## Class (클래스) 

1. 값
2. 메소드

두 가지로 이루어져있다 

```python 
class A:
	x = 1
	def a(self, y):
		self.y = y 
		return y
A.x      # 클래스로 클래스 변수 접근 
a = A()  # 인스턴스 생성 
a.x      # 인스턴스 a로 x(클래스 변수)접근 
vars(a)  # 인스턴스 변수 확인 
a.a(3)   # 인스턴스 a로 a() (메소드) 접근 
vars(a)
A.a(a,5) # 클래스로 인스턴스 a와, 5을 인자로 넘겨주고 a함수 접근 
vars(a)  # 인스턴스 변수는 인스턴스마다 고유로 갖을 수 있는 변수 이다 

: 1 
  1
  {}
  3
  {'y':3}
  5
  {'y':5}
  
dir(A)
dir(a)

: ['__class__','__dict__',.......,'a','x'] 
  ['__class__','__dict__',.......,'a','x','y']
  
  
class B:
	x = 2 
	def b():
		print('Access class')

B.b()
b = B()
b.b()

: Access class 
  AttributeError

class B:
	x = 2 
	def b(self):
		print('Access instacne')
B.b()
b = B()
b.b()
B.b(b)

: TypeError 
  Access instance
  Access instance
```

### 클래스 변수 vs 인스턴스 변수 

인스턴스는 모든 것을 사용할 수 있지만 클래스는 인스턴스 변수를 사용할 수 없다 <br>

```python
class A: 
	a = 1                  # class variable, attribute
	def __init__(self, y):
		self.y = y     # instance variable, attribute 
		

# 접근 예제 

class A: 
	x = 1
	y = 2 
	def add(self, x, y):
		sum = x + y 
		self.sum = 20 
		return sum 
a = A()
a.add(3,4)
A.add(a, 10, 20)
vars(a)
a.sum
A.sum

: 7
  30
  {'sum':20}
  20
  AttributeError
 
class B:
    x = 1
    y = 2 
    def sum(self,x, y):
        sum = x+y
        self.sum = 20
        return sum 
b = B()
b.sum(1,2)
B.sum(b, 3, 4)
b.sum
B.sum
vars(b)
vars(B)
dir(b)

: 3 
  7
  20
  <function __main__.B.sum(self,x,y)>
  {'sum': 20}
  mappingproxy({'__module__': '__main__',
              'x': 1,
              'y': 2,
              'sum': <function __main__.B.sum(self, x, y)>,
	      .....})
  ['__class__', ......, 'sum','x','y']
     
```


**실행 순서** 메소드와 변수가 이름이 같을때 변수를 먼저 접근하기 때문에 주의 해야 한다 
{: .notice}

```python 
# ex)

```

**인스턴스.메소드** 클래스안에 선언된 메소드를 사용하기 위해서는 인스턴스 생성을 한후 인스턴스.메소드() 하면 사용가능하다
{: .notice}

**self** 는 인스턴스라고 생각하면 된다. 메소드의 인자로 self가 있는건 self 자리에 인스턴스를 인자로 넘겨받아 해당 함수를 접근해서 사용 가능하게 된다는 의미로 받아들이면 된다 
{: .notice}

```python 
type(int)
type(float)
type(list)

:type
 type
 type
# return값이 type인 경우는 클래스라는 뜻이다 
# type은 meta class 
# type입장에서는 int, float, list 모두 인스턴스 

type(KNeighborsClassifier)
:abc.ABCMeta 
```
### Instance (인스턴스)

클래스를 사용하려면 인스턴스화 해야한다 <br>
인스턴스는 클래스의 값과 메소드에 접근이 가능하다 

```python 
class A(object):                   # 기본적으로 class는 object라는 클래스를 상속받는다
	def __init__(self, x = 0): # 명시하지 않아도 default로 상속한다 
		print('init')	   # object는 공통적인 속성들을 모아둔 class(추상화, 상속)
# init은 내부적으로 인스턴스화 할때 호출함 / 생성자라고도 한다 
# init의 추상화 내용이 마음에 들지 않는 경우 변경 가능함(다형성)  
```

**Type casting** a = list({1,2,3}) 리스트 클래스의 괄호 안에 dict타입을 넣게 되면 리스트 타입으로 변경된다. 파이썬에서는 타입 변경이 없기 때문에 타입 변경시에는 클래스 안에 인자로 넣어 인스턴스화 하여 바꿔준다. 단, 모든것이 되는것은 아니다  
{: .notice}

```python
a = int('0')
a

: 0 
# 원래는 문자를 정수형으로 타입 변환이 되지 않지만 
# 문자형으로 된 숫자를 정수형 타입으로 변환되는 경우가 몇가지 있다 
# 이는 init으로 바꿀 수 있게 해둔 것이다 
```

### classmethod, staticmethod 

```python 
class A:
    a = 1 
    def __init__(self,y):
        self.y = y   
    def getx(self):
        return self.y
    
    @classmethod
    def getxx(cls):  # class method
        print('a')  
    
    @staticmethod    # 똑같이 함수 처럼 사용 
    def y(cls):
        print('b')
```

### 객체 지향의 특징 

```
1. 캡슐화 
- 재활용 가능 
- 파이썬에서는 기본적으로 외부에서 클래스 접근 가능 
- descriptor로 클래스 접근을 막을 수도 있다 
2. 추상화 
- 구체적인것과 추상적인 것을 분리시킨다 
- 특징을 뽑아 객체로 구현 
3. 상속 
- 추상화의 반대 
- 추상화한 클래스를 물려받아 구체적으로 원하는 대로 바꾸어 사용 가능 
4. 다형성 
- 다양한 결과를 낼 수 있다 
```

**Python Tip1** 유지보수를 해야 한다고 느끼면 객체지향 프로그래밍을, 멀티프로세스나 다양한 문제를 다양한 방식으로 풀고 디버깅을 편하게 해야 한다고 느끼면 함수형 프로그래밍을 하면 된다 
{: .notice}

**Python Tip2** 동적으로 인스턴스 변수, 메소드 추가 가능 but 좋지 않은 방식 
{: .notice}

```python 
# ex) 
class Dyn():
	name = 'jh'
	def name(self):
		print('nothing')
dy = Dyn()
dyn.d()
vars(dy)
dy.name
dy.name = 'jane'
dy.name
vars(dy)

: 'nothing'
  {}
  'jh'
  'jane'
  {'name': 'jane'}
```

### Naming 

#### 1. camelCase(카멜 표기법)

첫 문자는 소문자로 표기하고, 그 다음 단어의 첫 시작은 대문자로 표기한다 <br>
원래는 첫 문자는 대,소문자 구분없었지만 요즘은 소문자로 쓰는 방법이 카멜 표기법 이다<br>
ex) helloWorld
<br>
**함수명은 이 표기법을 권장한다. 단 ,소문자 + underscore를 쓰기도 한다**

#### 2. PascalCase(파스칼 표기법)

첫 문자를 대문자로 표기하고, 그 다음 단어의 첫 시작도 대문자로 표기한다 <br>
ex) HelloWorld
<br>
**클래스명은 이 표기법을 권장한다. 단, 이미 만들어져 있는 클래스는 소문자로 시작한다**

#### 3. snake_case(스네이크 표기법)

한 단어마다 _ (underscore)를 붙여 이어나가는 표기법이다 <br>
ex) hello_world
<br>
**모듈은 이 표기법을 권장한다. 내장 함수도 보통 스네이크 표기법을 따른다**

#### 4. 전부 대문자 

전부 대문자를 쓸 경우 상수처럼 쓴다 (관례)<br>
ex) NUMBER = 10 

<br>

c.f 패키지는 소문자로 구성한다 



**복습 시간**  18시 30분 ~ 20시 20분 / 총 1시간 50분 
{: .notice}



# 2019년 5월 14일 화요일 아홉번째 수업


## Design pattern 

20 ~ 30가지가 있다 <br>
주로 사용하는 coding 방식, 웹에서 주로 이용 (MVC 패턴 같은 것들) 


## Class inheritance

```python
class Door:
    colour = 'brown'

    def __init__(self, number, status):
        self.number = number
        self.status = status

    @classmethod              
    def knock(cls):       
        print("Knock!")

    @classmethod
    def paint(cls, colour):  # 클래스, 인스턴스 모두 사용 가능하고 
        cls.colour = colour  # 클래스 변수 바꾼다 
                             # 클래스로 접근한다 / 클래스만 값에 접근 가능
    @classmethod
    def paint2(cls, number):  # number는 인스턴스 변수
        cls.number = number   # classmethod는 클래스 변수만 바꿀 수 있다
    def open(self):
        self.status = 'open'
        
    def close(self):
        self.status = 'closed'
        
class SecurityDoor(Door):      
    pass


Door.knock()
door = Door(1, 'open')
vars(door)
door.knock()
door.paint('red')  # 인스턴스로 클래스 변수 바꿀 수 있음 (@classmethod)
door.colour
Door.colour
door.paint2(2)
door.number
Door.paint2(3)     # 클래스만 인스턴스 변수 바꿀 수 있음 (@classmethod)
door.number
Door.number

: Knock!
  {'number': 1, 'status': 'open'}
  Knock!
  'red'
  'red'
  1
  1
  3
```

### mappingproxy 


### 클래스를 상속 받으면 원래 클래스 변수를 공유한다 

**※ 메모리 번지를 공유**

```python
sdoor = SecurityDoor(1, 'closed')

print(SecurityDoor.colour is Door.colour)  
print(sdoor.colour is Door.colour) 

:True 
 True 
```

## Composition (합성)

> 상속을 하지 않고 클래스내에 객체를 불러와 다른 클래스의 일부 기능을 사용하는 방법.
  
```python 
class SecurityDoor:
    locked = True
    
    def __init__(self, number, status):
        self.door = Door(number, status) # Door의 객체를 갖게 한다
        
    def open(self):
        if self.locked:
            return
        self.door.open()
        
    def __getattr__(self, attr):        # try except와 비슷 
        return getattr(self.door, attr) # Door의 attr를 가져와라 (상속을 비슷하게 사용)


class ComposedDoor:
    def __init__(self, number, status):
        self.door = Door(number, status)
        
    def __getattr__(self, attr): # 없으면 가져와라
        return getattr(self.door, attr) # 바꾸지 않고 불러와서 사용할 때
```

```python 
class A:
	x = 1 
	
a = A()
hasattr(a,'x')
getattr(a,'x')

:True 
 1 
```

**※ Design pattern에서는 상속대신 합성을 주로 사용한다**

Composition : [blog](https://www.fun-coding.org/PL&OOP1-11.html)<br>

## 예외처리문 

> Python의 철학중 양해를 구하기보다 용서를 구하기가 더 쉽다라는 것이 있다. 이처럼 Python에서 예외처리는 빠질 수 없는 부분이다. 

```
하지만 DataScience 분야에서는 많이 사용하지는 않는다.
웹이나 자동화 등 사용자로부터 입력을 받거나 외부 조건에 의해 오류가 많이 날 수밖에 없는 환경에서는 굉장히 중요하다
따라서 오류가 나더라도 중단하지 않고 실행을 시켜야 하는 경우에 대비해서 예외처리문을 삽입하는 것이다 
```

### 예외처리 구조 

```python
a = {'a':1}
try:
    t = a['b']
except:   # 에러가 나면 실행 / 에러종류에 따라 여러개 만들 수 있음 
    print('except')
else:     # 에러가 나지 않으면 실행 
    print('else')
finally:  # 에러 상관없이 실행 
    print('finally')
    
# try, except가 예외처리의 필수   
```

### 응용 

```python
a = {'a':1}
try:
    t = a['n']
except :
    print('all')
except KeyError:
    print('except')
    
# SyntaxError => except 혼자 오는 것은 마지막에 와야 한다 

a = {'a':1}
try: 
    t = a['n']
except KeyError as f:   # 에러에 대한 상세 표시 
    print(f)
except:
    print('except')
    
:'n'

a = {'a':1}
try: 
    t = a['n']
except Exception as f:   # Exception 상속(상위 에러)
    print(f)
except:
    print('except')
```

**syntax error, runtime error** syntax error는 구문오류로 실행자체가 안된다, runtime error는 실행은 되지만 값이 나오지 않는다 
{: .notice}

### 에러를 강제로 발생시키는 방법 

```python
def x(a):
	if a > 0 :
		raise
	else:
		raise SyntaxError
	
x(3)
x(-3)

: RuntimeError
  SyntaxError

a = 3 
assert a > 4

AssertionError 
# 해당 조건이 만족하지 않으면 에러 발생 
```

## 다른 사람 것을 고쳐 쓰는 방법 

```
1. 상속후 오버라이딩 
2. 데코레이터

# 오버로딩은 같은 이름의 메소드를 가지면서 매개변수 유형은 다를때 서로 다른 메소드로 간주하는 것 
# 파이썬에서는 오버로딩이 지원되지 않아 같은 이름의 메소드를 정의할경우 재할당이 된다 
```

**Mangling** 맹글링은 소스 코드에서 선언된 함수 또는 변수의 이름을 컴파일 단계에서 컴파일러가 일정한 규칙을 가지고 변형하는 것을 말한다. 이는 보통 객체 지향에서 오버로딩시 함수의 이름이 같고 파라미터만 다를때 알아서 구별할 수 있도록 하는데 사용된다.
{: .notice}

#### 추가 복습이 필요한 부분 

1. Composition 
2. Decorator  
3. Closure
4. Iterator 
5. Genrator 
6. Comprehension
7. First class function 
8. tatement 3가지 

**복습 시간**  17시 30분 ~  19시, 20시 ~ 20시 30분 / 총 2시간 
{: .notice}



# 2019년 5월 16일 목요일 열번째 수업


## Duck typing 

**미운오리새끼 이야기에서 유래가 되어 오리가 아닌데 오리처럼 행동을 하면 오리라고 간주한다는 개념이다** <br>
**타입을 미리 정하지 않고 실행되었을 때 해당 Method들을 확인하여 타입을 정한다**<br>

### 장점 
- 타입에 대해 자유롭다 
- 상속을 하지 않아도 상속을 한것처럼 클래스의 메소드 사용이 가능하다 

### 단점 
- 원치 않는 타입이 들어 갈 경우 오류가 발생할 수 있다 
- 오류 발생시 원인을 찾기 어려울수 있다  

```python
class Airplane:
    def fly(self):
        print("Airplane flying")

class Whale:
    def swim(self):
        print("Whale swimming")

def lift_off(entity):
    entity.fly()
    
def lift_off2(entity):
    if entity.swim():
        entity.fly()    

airplane = Airplane()
whale = Whale()

lift_off(airplane)
lift_off2(airplane)
lift_off(whale)
lift_off2(whale)
: Airplane flying
  AttributeError 
  Whale swimming
  AttributeError
```

## Duck typing vs Inheritance


## Polymorphism(다형성)

```python

```

### Monkey patch 

런타임상에서 함수, 메소드, 속성을 바꾸는 패치. <br>
런타임 실행중 메모리상의 오브젝트에 적용된다. <br>

```python 
import matplotlib
len(dir(matplotlib))
: 109 

import matplotlib.pyplot as plt
len(dir(matplotlib))
: 172

# 사실 이 예제가 Monkey patch랑 무슨 연관이 있는지 잘 모르겠음 
```

### Runtime

어떤 프로그램이 실행되는 동안의 시간 <br>
그래서 런타임 에러는 '어떤 프로그램이 실행되는 동안 발생하는 에러를 말한다 

**Python Tip1** 1.__dir__ (X) 1 .__dir__ or (1).__dir__ (O) / 연산자 우선순위 때문에 float로 인식하므로 띄어쓰기를 하거나 괄호를 써줘야 한다 
{: .notice}

## Meta class 

**Type** <br>
**Class 행동을 지정할 수 있다** <br>
ex) 인스턴스를 한개만 만들 수 있게 지정 (싱글톤) 


```python 
class MyType(type): # type을 상속받아 메타클래스를 만듦
    pass

class MySpecialClass(metaclass=MyType): # 안적어주면 type 상속 
    pass
    
msp = MySpecialClass()
print(type(msp))
print(type(MySpecialClass))
print(type(MyType))

: <class '__main__.MySpecialClass'>   # 인스턴스 msp의 클래스명은 MySpecialClass
  <class '__main__.MyType'>           # 클래스 MySpecialClass의 메타클래스는 MyType 
  <class 'type'>                      # 메타클래스 MyType의 메타클래스는 type 

# 따라서 메타클래스를 만들기 위해서 type을 상속받아야 한다 
```
<br>
**type, object** type은 최상위 metaclass, object는 최상위 class 
{: .notice}
<br>

## Singleton

```python 
class Singleton(type):
    instance = None
    def __call__(cls, *args, **kw):
        if not cls.instance:
             cls.instance = super(Singleton, cls).__call__(*args, **kw)      
	                    # super().__call__(*args, **kw) 동일 
        return cls.instance

class ASingleton(metaclass=Singleton):
    pass

a = ASingleton()
b = ASingleton()
a is b
: True

```
<br>

**isinstance & issubclass** isinstance는 어떤 객체가 특정 클래스인치 판별하는 predicate issubclass는 어떤 클래스가 특정 클래스의 상속을 받았는지 판별하는 predicate 
{: .notice}

```python
isinstance(1,(str,int))  # 두번째 인자는 tuple도 가능
issubclass(bool,int)

: True
  True 
```

## __getattribute__ vs getattr vs __getattr__

instance.attribute(method) <br>
1. __getattribute__ 실행 (getattr)
2. attribute가 없으면 attribute error 
3. __getattr__가 정의 되어 있으면 실행 
<br>
instance.attribute(variable) <br>


참고 : [tistory](https://brownbears.tistory.com/187)
## as 

1. import할때 명명법 바꾸기 
2. 예외처리문에서 에러에 대한 상세표시 

**__all__** import할때 포함시키고 싶은 범위를 지정해주는 special method
{: .notice}

special method : [slideshare](https://www.slideshare.net/dahlmoon/specialmethod-20160403-70272494)<br>

## _ 7가지 활용 

```
1. _* 
- from module import *에 의해 포함되지 않는 변수명명법 
2. __*__
- magic or special method 명명법 
3. __*
- mangling
- 클래스내에 __를 사용하여 변수명을 바꿔주는 방법 
- 이때 외부에서 해당 변수에 접근을 하지 못하는 private 기능을 하는 것처럼 눈속임을 한다 
4. _ 
- 숫자에 쓰는 언더바 
- ex) a = 100_000
5. _ (이름이 중요하지 않지만 관례상 쓸때)

for i,_,k in zip([1,2,3],[4,5,6],[7,8,9]):
    print(i,_,k)
    
for i,_,_ in zip([1,2,3],[4,5,6],[7,8,9]):
    print(i,_,_)   
# 주의, 맨 마지막에 쓴 값 출력 (할당하지 않으면)
6. _method
- private
7. _  맨 마지막에 쓴 값 출력 (할당하지 않으면)
a = 3
a
-
: 3
  3
(8). _() # 다른 언어지원할 때 
- 라이브러리 사용해야 해서 기본 7가지로 생각
```


##### 추가 복습 

1. 다형성 
2. 추상클래스 
3. getattribute 

**복습 시간**  20시 ~ 22시 30분/ 총 2시간 30분 
{: .notice}



# 2019년 5월 17일 금요일 열한번째 수업

## Multiple inheritance(다중 상속)

말 그대로 상속을 2개 이상을 하는 것 


**function 기법**
- 실행 순서를 직접 정할 수 있다 
- 그러나 같은 값을 중복해서 출력하는 경우가 생긴다 

```python
class x:
    def __init__(self):
        print('x')
class A(x):
    def __init__(self):
        x.__init__(self)
        print('A')
class B(x):
    def __init__(self):
        x.__init__(self)
        print('B')
class C(A,B):
    def __init__(self): 
        B.__init__(self)   
        A.__init__(self)  
        print('C')
	
c = C()

: X 
  B
  X
  A
  C
```

**super**

- super는 상속을 전부 실행하지 않는다 
- 따라서 중복의 문제를 해결할 수 있다.
- 하지만 super와 function을 함께 사용하면 상속을 전부 실행하지 않는다 

```python
class x:
    def __init__(self):
        print('x')
class A(x):
    def __init__(self):
        x.__init__(self)
        print('A')
class B(x):
    def __init__(self):
        x.__init__(self)
        print('B')
class C(B,A):
    def __init__(self): 
        super().__init__()  # super는 부모 인스턴스를 반환 / 클래스 명,self 생략 가능 
        print('C')

c = C()
: X
  B
  C
```

**only super**

- super는 상속 실행 순서를 자동적으로 지정해준다 
- super를 사용할때 전부 super를 사용하면 중복 해결, 원하는 값 출력 가능하다 
- 다이아 문제 해결 

```python

class x:
    def __init__(self):
        print('x')
class B(x):
    def __init__(self):
        super().__init__()
        print('B')
class A(x):
    def __init__(self):
        super().__init__()
        print('A')
class C(A,B):
    def __init__(self): 
        super().__init__() 
        print('C')
c = C()
: x
  B
  A
  C
```

> 왜 실행 순서에 따라 출력되지 않을까? 

```python
C.__mro__
C.mro()

: (__main__.C, __main__.A, __main__.B, __main__.x, object)
  [__main__.C, __main__.A, __main__.B, __main__.x, object]
  # 반환 타입이 서로 다름 
```

**실행 순서는 C -> A -> B -> x 인데 출력 결과는 왜 반대일까?**

<span style="background-color: orange">그 이유는 바로 super사용시 stack에 들어가기 때문이다 </span><br>

<br>
## 다중 상속시 절대 에러가 나지 않게 하는 방법 

<span style="background-color: rgb(229, 68, 91)">Mixins</span>
**특수한 class를 만들어 충돌이 일어나지 않게 다중 상속을 한다**

```python
class FirstMixin(object):
    def test1(self):
        print("first mixin!!!")


class SecondMixin(object):
    def test2(self):
        print("second mixin!!!")


class TestClass(FirstMixin, SecondMixin):
    pass

t = TestClass()
t.test1
t.test2
: first mixin!!!
  second mixin!!!
```

**다이아 문제** 다중 상속시 어느 클래스의 메소드를 상속 받아야 할 지 모호한 경우 
{: .notice}

<br>
## ABC class (Abstract base class)

<span style="color:orange">추상적인 부분은 구현하지 않고 구체적인 부분에서 구현하도록 강제하는 기법 </span><br>

**추상 클래스 특징**

```
1. ABC class를 사용하면 duck typing 문제점을 보완할 수 있다 
2. 상속받는 클래스는 추상메소드를 구현하지 않아도 클래스 기능은 동작한다 
3. abc 모듈을 import 해야한다 
```

추상클래스: [wikidocs](https://wikidocs.net/16075)<br>

```python
# sequence 타입의 조건 
class A:           
    x = 1 
    def __getitem__(self,x):
        print('A')
    def __len__(self):
        print('B')
a = A()
a[0]
: A
```

### ABCMeta

```python
from abc import ABCMeta, abstractmethod 

class Y(metaclass = ABCMeta):
	@abstractmethod
	def a(self):
		return 1
class A(Y):
	pass
	
a = A()

: TypeError 
```

> 오버라이딩을 하지 않는 경우 에러가 발생하기 때문에 오버라이딩을 강제시킨다

```python
class A(Y):
    def a(self):
        return 1

a = A()
a.a()
:1
```

```python
from abc import ABCMeta, abstractclassmethod 

class Y(metaclass = ABCMeta):
    @abstractclassmethod
    def a(self):
        return 1
class B(Y):
    def a(self):
        return 1

b = B()
b.a()
: 1

```

#### abstractmethod vs abstractclassmethod


<kbd>duck typing</kbd>+<kbd>meta class</kbd>+<kbd>abc</kbd> => <kbd>강려크하다</kbd>


### register 

```python
from abc import ABCMeta

class MyABC(metaclass=ABCMeta):
    pass

MyABC.register(tuple)  # tuple처럼 사용 

assert issubclass(tuple, MyABC)
assert isinstance((), MyABC)
```

> 좋지 않은 방법이기 때문에 내가 만든 클래스에서만 사용하도록 권장 


<br>

## Descriptor 

> 점(.)으로 객체의 멤버를 접근할 때, 먼저 인스턴스 변수(__dict__)에서 멤버를 찾는다. 없을 경우 클래스 변수에서 찾는다. 클래스에서 멤버를 찾고 객체가 descriptor 프로토콜을 구현했다면 바로 멤버를 리턴하지 않고 descriptor 메소드(__get__, __set__, __delete__)를 호출한다 

**Descriptor 구현 방법 3가지**
```
1. get, set + composition 

2. Properties

3. Decorator 
```

#### 1. get, set + composition
```python
class RevealAccess:
    def __init__(self, initval = None, name='var'):
        self.val = initval
        self.name = name 
    def __get__(self, obj, objtype):
        print('get')
        return self.val
    def __set__(self, obj, val):
        print('Updating',self.name)
        self.val = val + 10
    def __delete__(self, obj, val):
        print('안지워짐')
class Myclass:
    x = RevealAccess() 
    y = 5
    
m = Myclass()
m.x
: get
m.x = 20
: Updating var
m.x
: get
  30 
```
#### 2. Properties

```python
class C(object):  #getx, setx, delx 이름 상관없음 
    def getx(self): 
        print('AAA')
        return self.__x
    def setx(self, value): 
        self.__x = value
    def delx(self): 
        del self.__x
    x = property(getx, setx, delx, "I'm the 'x' property.")
    
d = C()
d.x
: AAA 
  AttributeError
```

#### 3. Decorator

```python
class D:
    __X = 3   # 실제값은 __X에 저장 
    @property 
    def x(self):
        return self.__X
	
d = D()
d.x()
:TypeError 


class D:
    def __init__(self):
        self._x = 0
    @property 
    def x(self):
        return self.__x
    @x.setter    #이름은 똑같지만 다른 메모리번지에 할당해주는 역할 
    def x(self, x):
        self.__x = x	
```
<span style="background-color:red">Descriptor 부분은 다시 공부하고 정리하기 </span><br>

Descripter : [slideshare](https://www.slideshare.net/dahlmoon/descriptor-20160403)<br>


### 싱글 디스패치, 멀티 디스패치

### epiphany

> 우연한 순간에 귀중한 것들과의 만남, 혹은 깨달음을 뜻하는 통찰이나 직관, 영감을 뜻하는 단어이다.
  python 공부도 그렇듯 계속해서 하다보면 저절로 내것이 될꺼라 믿는다.

epiphany : [brunch](https://brunch.co.kr/@altna84/216)<br>

##### 자습서 공부하기 
- 3 ~ 9장

**복습 시간** 22시 30분 ~ 1시 10분 / 총 2시간 40분  
{: .notice}


# 2019년 5월 20일 월요일 열두번째 수업

## 정보의 진화 단계 

![dikw](https://user-images.githubusercontent.com/33630505/58008628-c1fc7700-7b27-11e9-9e69-6f39608cd81d.JPG)


DIKW : [blog](http://blog.naver.com/PostView.nhn?blogId=gracehappyworld&logNo=221481622524&categoryNo=17&parentCategoryNo=0&viewDate=&currentPage=1&postListTopCurrentPage=1&from=search)

## 인공지능의 시작과 배경 

Physical Labor과 Cognitive Labor의 한계를 극복하기 위해 인공지능으로 자동화 시키는 분야가 발달하게 됨 <br>
그러나 요즘은 보통 물리적 노동보다는 인지적 관점에서 관심이 쏠리고 있다 <br>
아직 인공지능은 이해하는 능력은 부족하지만 인식하는 능력은 사람의 영역 그 이상까지 왔다 <br>

### 지능 

지식을 <br>

1. 이해
2. 인식 
3. 추론
4. 학습 
5. 생성 
6. 해결 
7. 결정 
<br>
할 수 있는 능력 

## 인공지능 
```
'인간을 대체할 수 있는 기계 또는 지능을 갖춘 존재로부터 의사소통, 상황의 상관관계 이해 및 
 결론 도출 등 인간의 행동을 모방할 수 있는 기술'
 
좁은 의미에서 기계학습이라 볼 수 있다 
기계학습은 데이터를 넣어주면 프로그래밍된 논리나 규칙을 바탕으로 
스스로 학습하여 문제해결을 하는 알고리즘을 생성한다
 
deep learning은 인간 신경망을 모델화하여 스스로 데이터 세트를 예측하는 기술이다
deep learning은 인식분야에서 정확도가 높지만 인식이외에 기능은 좋지 않다
deep learning은 정형화 데이터에서 성능이 좋지 않고 비정형 데이터에서 성능이 좋다
```

### AI, Machine learning, deep learning 

![ai](https://user-images.githubusercontent.com/33630505/58009466-7f3b9e80-7b29-11e9-9515-20b4583abaf6.JPG)


### 인공지능 영역의 분류

![ai](https://user-images.githubusercontent.com/33630505/58367430-26e61180-7f1a-11e9-97a3-9c163f0b52d4.JPG)

## 인공지능의 문제해결 전략 

```
인간의 인지적 작업을 
어떻게 Computing Model로 만들어내고 
그것을 Machine에서 구현하여 
그 작업을 자동으로 효율적으로 할 수 있게 할 것인가? 

Computing Model 
- Theory of computation
  컴퓨터 과학의 한 갈래로, 어떤 문제를 컴퓨터로 풀 수 있는지, 또 
  얼마나 효율적으로 풀 수 있는지 
- Programmable 
```

## 파이썬은 연산속도가 느린데 도대체 왜 파이썬으로 AI를 하는가?

### Numpy가 있기 때문에! 

<span style="background-color:rgb(56, 188, 182)">Numpy는 속도가 빠르고 사용하기가 쉽다! </span><br>
Numpy는 벡터 연산, 행렬 연산을 효율적으로 쉽게 만들 수 있다<br>  
Numpy는 속도 개선의 최적화를 하지 않아도 되기 때문에 AI시작시 python말고 Numpy를 한다 <br>
<br>
추가적으로 <br>
pandas, Keras => 100 % Numpy로 만들어짐 <br>
Tensor => Numpy + GPU <br>
matlab이 연산이 빠른 이유는 행렬 계산이 가능하기 때문 <br>
=> 행렬계산은 대량 연산시 빠르다 


Numpy 공식 문서: [docs](https://docs.scipy.org/doc/numpy/reference/?v=20190520142926)


## Numpy 

> Numarray와 Numeric이라는 오래된 Python 패키지를 계승해서 나온 수학 및 과학 연산을 위한 파이썬 패키지이다.


**Numpy는 벡터 기반이다**

- 0차 스칼라 
- 1차 벡터 
- 2차 행렬 
- 3차 텐서 

<br>

**python 속도 개선을 위한 방법**
 
1. Computing Power
- GPU
- Parallel Computing
2. Compiler 
- Cython
- PyPy ....
3. Library 
- Numpy 
4. Algorithm/ Data Structure 
 
<br>

### Vectorization
 
```
loop없이 벡터연산으로 속도 향상을 하는 방법 
요즘은 cpu자체에서 vercotr processor를 지원 
함수형 패러다임 + 선형대수 기법 
```

![array](https://user-images.githubusercontent.com/33630505/58010431-4ef4ff80-7b2b-11e9-81fb-7fb7bba0cd19.JPG)
<br>

**Numpy Tip1** python list와 numpy list는 차이가 있다. python은 linked list , type check로 인해 속도가 느리고, numpy 에서는 type이 통일되어 있어 속도가 빠르다 
{: .notice} 
![list](https://user-images.githubusercontent.com/33630505/58010552-8bc0f680-7b2b-11e9-9c2b-ff3cb5012eaa.JPG) 


### Numpy 사용하기 

```python
import numpy as np

a = np.array(0)
b = np.array([1,2,3])
c = np.array([[1,2],[3,4]])
d = np.array([[[1,2],[3,4],[5,6]]])
a
b
c
d
type(a)

: array(0)
  array([1,2,3])
  array([[1, 2],
       [3, 4]])
  array([[[1, 2],
        [3, 4],
        [5, 6]]])
  numpy.ndarray
```

### 특수 행렬 만들기

```python
import numpy as np

z = np.zeros([3,3])
z
: array([[0., 0., 0.],
       [0., 0., 0.],
       [0., 0., 0.]])
       
y = np.eye(3)
y
: array([[1., 0., 0.],
       [0., 1., 0.],
       [0., 0., 1.]])

t = np.array([[1,2,3],[4,5,6],[7,8,9]])
t.T
: array([[1, 4, 7],
       [2, 5, 8],
       [3, 6, 9]])
 
o = np.ones((5,4))
o
: array([[1., 1., 1., 1.],
       [1., 1., 1., 1.],
       [1., 1., 1., 1.],
       [1., 1., 1., 1.],
       [1., 1., 1., 1.]])
       
f = np.full((3,3),3)
f
: array([[3, 3, 3],
       [3, 3, 3],
       [3, 3, 3]])
       
       
l = np.ones_like(f)
l
: array([[1, 1, 1],
       [1, 1, 1],
       [1, 1, 1]])
```

**array** 는 몇차원 데이터인지 통칭하는 단어이다. 그리고 return 값에 array가 나오면 Numpy형태라는 뜻. 파이썬에서 사용하는 형태를 Numpy로 바꿔준다. 벡터를 만드는 방식이기도 하다 
{: .notice}


### 행렬 연산 함수 

```python
import numpy as np


a = np.array([1,2,3,4,5])
a + 3 
: array([4, 5, 6, 7, 8])

a.dot(a) # 내적 
: 55

np.sum(a)
: 15

t = np.array([[1,2,3],[4,5,6],[7,8,9]])
np.sum(t, axis = 1) # 행연산 
: array([ 6, 15, 24])

np.sum(t,axis=0) # 열연산
:array([12, 15, 18])

```

### Python, Numpy 속도 비교

```python
%timeit np.sum(np.arange(10000000))
: 24.6 ms ± 2.2 ms per loop (mean ± std. dev. of 7 runs, 10 loops each)

%timeit sum(range(10000000))
: 352 ms ± 6.34 ms per loop (mean ± std. dev. of 7 runs, 1 loop each)
```


### 데이터 정보 확인하는 방법 

```
1. dtype
2. size
3. shape 
4. ndim
```
```python
import numpy as np
a = np.arange(10)

a.dtype
a.size
a.shape
a.ndim

: dtype('int32')
  10
  (10,)
  1
```

## Stride

![ndarray](https://user-images.githubusercontent.com/33630505/58012662-f2481380-7b2f-11e9-833e-4966c0e17241.JPG)

```python
import numpy as np

a = np.array([[1,2,3],[4,5,6],[7,8,9]])
a.strides
: (12, 4)

# 8bit = 1byte
# 바이트 단위로 쪼개기 때문에 8로 나누어 주면 (3,1) 즉, 한 행에 3개 열로 구성되어 있다는 뜻 
```

**stride만 바꾸어 shape 자유자재로 바꾸기**<br>

```python
import numpy as np

a = np.arange(10).reshape(2,5)
a
: array([[0, 1, 2, 3, 4],
       [5, 6, 7, 8, 9]])
       
a = np.arange(10).reshape(-1,5)
a
: array([[0, 1, 2, 3, 4],
       [5, 6, 7, 8, 9]])
# -1은 자동으로 알아서 하라는 뜻 / 행렬의 크기를 모를때 유용        
```


## 데이터 형태 변환하기 

```python
import numpy as np

a.astype('float32')
: array([[1., 2., 3.],
       [4., 5., 6.],
       [7., 8., 9.]], dtype=float32)

a.astype('int64')       
: array([[1, 2, 3],
       [4, 5, 6],
       [7, 8, 9]], dtype=int64)   

a.astype('bool')
: array([[ True,  True,  True],
       [ True,  True,  True],
       [ True,  True,  True]])
```

### 자동 형변환 

**coerce** <br>

```python
1/2
: 0.5
```

## Python 문법으로 벡터화 하기 vs Numpy 

```python
def x(a,b):
    return [i+j for i,j in zip(a,b)]
x([1,2,3],[4,5,6])
: [5, 7, 9]

@np.vectorize
def z(a,b):
    return a + b
z([1,2,3],[4,5,6])
: array([5, 7, 9])
```


## array는 sequence type 

> sequence type은 indexing, slicing이 가능하다! 


```python
import numpy as np

n = np.arange(10).reshape(5,2)
n
: array([[0, 1],
       [2, 3],
       [4, 5],
       [6, 7],
       [8, 9]])
       
n[:,1]
: array([1, 3, 5, 7, 9])

n[:][1]
: array([2, 3])

n[1,:]
: array([2, 3])

n[n>3]
: array([4, 5, 6, 7, 8, 9])


```

##### 이해 못함 

```python
import numpy as np

x = np.array([1,2])
x[True,False]
: array([], shape=(0, 2), dtype=int32)
```

##### 자유자재로 indexing, slicing 연습하기  



**복습 시간** 17시 40분 ~ 19시 / 총 1시간 20분
{: .notice}


# 2019년 5월 21일 화요일 열세번째 수업


## Masking 


## ix_ 

<span style="background-color:skyblue">Cartesian product 연산</span><br>

```python
import numpy as np

h = np.arange(25).reshape(5,5)
h
: array([[ 0,  1,  2,  3,  4],
       [ 5,  6,  7,  8,  9],
       [10, 11, 12, 13, 14],
       [15, 16, 17, 18, 19],
       [20, 21, 22, 23, 24]])
h[np.ix_([1,3],[0,1,2,3,4])]
: 
array([[ 5,  6,  7,  8,  9],
       [15, 16, 17, 18, 19]])
```

## Namedtuple

> 이름 있는 튜플 만들기 
sequence tuple 처럼 사용 가능
클래스처럼 이름으로 접근가능 

```python
from collections import namedtuple

t = namedtuped('AttendanceSheet',['name','attendance'])
x=t('jh','yes')
x[0]
x[1]
x.name
x.attendance
type(x)

: jh 
  yes
  jh
  yes
  __main__.AttendanceSheet
```

## broadcasting 

> 벡터연산에서 자동으로 크기 맞춰주는 기법 

```python
import numpy as np

a = np.arange(10)
a + 1 

: array([ 1,  2,  3,  4,  5,  6,  7,  8,  9, 10])
```

![broadcasting](https://user-images.githubusercontent.com/33630505/58095909-e717e500-7c0e-11e9-9adb-d916ca172bf2.JPG)


## ufunc(universal function)

> 범용적인 함수 즉, python, numpy 둘다 있는 함수 but 차이가 있다 

### 1개의 배열에 대한 ufunc 함수 

```
abs,fabs => 절대값 
ceil => 올림 
floor => 내림 
modf => 정수부분과 소수점 부분 분리 
rint => 올림하거나 내림하거나 5를 기준으로 
log, log10, log2, log1p => 로그 값 취하기 
exp => exponential 지수함수 (정확히 어떻게 계산되는지는 모르겠음) 
sqrt => 루트
square => 제곱 
isnan => nan인지 체크 
isinfinite => 유한한 수안자 체크
logical_not => 모르겠음 
sign = > 0을 제외하고 다 1로 반환 (사실 정확하지 않음)
sin, cos, tan => sin, cos, tan값 계산
arcsin, arccos, arctan => 역삼각함수 계산 

```
### 2개의 배열에 대한 ufunc 함수 

```
add => 각 요소 더하기 
subtract => 각 요소 빼기 
multiply => 각 요소 곱하기
divide => 각 요소 나눈 값 
floor_divide => 각 요소 나눈 몫 
mod => 각 요소 나눈 나머지
power => 승 계산 ex) 2,3 => 2의 3 승 : 8 
maximum, fmax => 더 큰 값 
minimum, fmin => 더 작은 값 
greater => 앞 값이 더 크면 True 작으면 False 
greater_equal => 앞 값이 크거나 같으면 True 작으면 False 
less => greater 반대 
less_equal => greater_equal 반대 
equal => 같으면 True
not_equal => 다르면 True 
copysign => 모르겠음 
```

### Python, Numpy ufunc

> python에서는 동시에 사용 못하지만 numpy에서는 한꺼번에 연산 가능 

```python
import math 
math.sqrt(4)
: 2.0 

np.sqrt((4,9))
: array([2., 3.])
```
<hr>

![ufunc1](https://user-images.githubusercontent.com/33630505/58092007-052d1780-7c06-11e9-86ca-8b8a2dae0a74.JPG)
![ufunc2](https://user-images.githubusercontent.com/33630505/58092009-065e4480-7c06-11e9-9dbc-eb9665801c3a.JPG)
![ufunc3](https://user-images.githubusercontent.com/33630505/58092011-078f7180-7c06-11e9-826c-b477930b24a5.JPG)

```python
np.sqrt([4,9])
np.sqrt((4,9))

둘다 가능 
```
**Numpy Tip1** mutable 성질이 중요하지 않으면 list, tuple 혼용 가능 
{: .notice}


### 배열 분할하기, 붙이기 

```python
a = np.arange(16).reshape(4,4)
a
: array([[ 0,  1,  2,  3],
       [ 4,  5,  6,  7],
       [ 8,  9, 10, 11],
       [12, 13, 14, 15]])
       
np.hsplit(a,2), np.split(a,2,axis=1) # 수평축으로 분할(세로, 사실상 수직)
: [array([[ 0,  1],
        [ 4,  5],
        [ 8,  9],
        [12, 13]]), 
   array([[ 2,  3],
        [ 6,  7],
        [10, 11],
        [14, 15]])]
np.hsplit(a,(1,2))
: [array([[ 0],
        [ 4],
        [ 8],
        [12]]), 
   array([[ 1],
        [ 5],
        [ 9],
        [13]]), 
   array([[ 2,  3],
        [ 6,  7],
        [10, 11],
        [14, 15]])]
```


### view & copy 

> python은 기본적으로 shallow copy, numpy는 기본적으로 deep copy 

```python
# python에서 deep copy하기 
import copy

a = [[1,2,3]]
b = copy.deepcopy(a)
a[0][1] = 4 
b 
a

: [[1, 2, 3]]
  [[1, 4, 3]]
  
# numpy는 기본적으로 deep copy 

a = np.array([[1,2,3],[4,5,6]])
b = a.copy()
a[0][0] = 4 
b
a

: array([[1, 2, 3],
       [4, 5, 6]])
  array([[4, 2, 3],
       [4, 5, 6]])     
```

### ravel & flatten 

> Ravel - Bolero (클래식/디지몬 어드벤처 극장판에서 나오는 노래) 
ravel은 몇 차원이건 간에 모두 1차원으로 만들어 준다 
그리고 view 방식이기 때문에 원래 값을 바꾸기 때문에 주의 해야한다 
flatten은 copy 방식

```python
a = np.arange(10).reshape(2,5)

a.ravel()
a.flatten()
: array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
  array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
```

### newaxis 

> return이 None이고 차원을 추가한다 
곱하기 할때에도 활용하는 방법이다.(차원을 맞추어 계산해야 하기 때문) 

```python
a = np.array([[1,2,3],[4,5,6]])
a
a.shape
: array([[1, 2, 3],
       [4, 5, 6]])
  (2,3)

# z축에 추가 
b=a[:,:,np.newaxis]
b
b.shape
: array([[[1],
        [2],
        [3]],

       [[4],
        [5],
        [6]]])
   (2, 3, 1)	## 평면 두개    
                
# y축에 추가 
c=a[:,np.newaxis]
c
c.shape
: array([[[1, 2, 3]],

       [[4, 5, 6]]])
  (2, 1, 3)     ## 평면 두개 
 

# x축에 추가 
d=a[np.newaxis,:]
d
d.shape
: array([[[1, 2, 3],
        [4, 5, 6]]])
  (1, 2, 3)     ## 평면 한개
```

### 행렬의 곱셈

#### matrix product
```python
a = np.array([[1,1],[0,1]])
b = np.array([[2,0],[3,4]])

a@b
: array([[5, 4],
       [3, 4]])
```

#### elementwise product 

```python
a = np.array([[1,1],[0,1]])
b = np.array([[2,0],[3,4]])

a*b
: array([[2, 0],
       [0, 4]])
```


**복습 시간** 18시 30분 ~ 21시 / 총 2시간 30분
{: .notice}


# 2019년 5월 23일 목요일 열네번째 수업


## newaxis 정리 

<span style="color:orange">1차원: 방향이 없는 벡터(스칼라)형태의 데이터만 존재, [] 1개</span><br>
```python
import numpy as np

a = np.array([1,2,3])
a.shape

: (3,)  # 3개의 데이터가 하나로 묶여 있다고 생각
```
<span style="color:orange">2차원 : 행렬, 평면, [] 2개</span> <br>

```python
import numpy as np

a = np.array([1,2,3])
a[np.newaxis]     # x축 추가 행기준으로 묶기 
a[np.newaxis].shape

: array([[1,2,3]]) # 가장 바깥 [] 소거하고 행갯수 세면 x축 데이터 갯수 
                   # 그 다음 안 [] 소거하고 행갯수 세면 y축 데이터 갯수 
  (1,3)
a[:,np.newaxis] # y축 추가 열기준으로 묶기 
a[:,np.newaxis].shape

: array([[1],      # 가장 바깥 [] 소거하고 열갯수 세면 x축 데이터 갯수 
        [2],       # 그 다음 안 [] 소거하고 열갯수 세면 y축 데이터 갯수 
        [3]])
  (3,1)	
```

<span style="background-color:red">행렬은 다른 행이여도 열의 갯수가 같아야 하는데 이런 경우도 가능한건가..?</span> <br>

```python
import numpy as np 
a = np.array([[1,2],[4,5,6]])
a
: array([list([1, 2]), list([4, 5, 6])], dtype=object)
```

<span style="color:orange">3차원 : 행렬 중첩, 평면 겹쳐서 직육면체처럼 [] 3개 </span><br>

```python
import numpy as np

a = np.array([[1,2,3],[4,5,6]])
a[np.newaxis]
a[np.newaxis].shape

: array([[[1, 2, 3],
        [4, 5, 6]]])   # 가장 바깥 []소거하고 []x2인 행갯수 세면 x축 데이터 갯수 
                       # [[1,2,3]] 이라는 평면 1개   
  (1,2,3)              # 그 다음 안 [] 소거하고 []x1인 행갯수 세면 y축 데이터 갯수
                       # 마지막 [] 소거하고 행갯수 세면 z축 데이터 갯수 

a[:,np.newaxis]
a[np.newaxis].shape    # 위와 동일 

: array([[[1, 2, 3]],

       [[4, 5, 6]]])
  (2,1,3)      
  
a[:,:,np.newaxis]
a[:,:,np.newaxis].shape #

: array([[[1],
         [2],
         [3]]])
(2, 3, 1)	
```


## tile 

```python
import numpy as np 

a = np.array([1,2,3])

np.tile(a,3)
: array([1, 2, 3, 1, 2, 3, 1, 2, 3])

np,tile(a,(2,3))
: array([[1, 2, 3, 1, 2, 3, 1, 2, 3],
       [1, 2, 3, 1, 2, 3, 1, 2, 3]])

np.tile(a,[2,3])  # duck typing 
: array([[1, 2, 3, 1, 2, 3, 1, 2, 3],
       [1, 2, 3, 1, 2, 3, 1, 2, 3]])
```

## 파일 불러오기 


### loadtxt, genfromtxt
```python
%%writefile a.csv
1,2,3
4,5,6

: Writing a.csv

x = np.loadtxt('a.csv', delimiter = ',') 
x
: array([[1., 2., 3.],
       [4., 5., 6.]])
       
x = np.genfromtxt('a.csv')
: array([nan, nan])

# loadtxt는 delimiter를 이용해 문자열 구분을 하지 않으면 에러가 나지만 
# getfromtxt는 nan이라는 출력값을 주고 에러를 발생시키지 않는다 
```

### fromfile

```python
x = np.fromfile('a.csv', sep=',') # \n을 만나면 종료
x

: array([1., 2., 3.])
```


## File

### Flat 

```
1. text file  
=> 확장자 상관없이 열 수 있다. 
=> 데이터 교환시 유용함 
2. binary file 
=> 연결프로그램에 의존적 
```


```
np.savez()

np.save()
```

### Raw 


## linear algebra


## view & copy 



#### WhyPythonIsSlow + open_with 내용 복습 

https://docs.scipy.org/doc/numpy/user/quickstart.html 복습 

**복습 시간** 
{: .notice}



# 2019년 5월 24일 금요일 열다섯번째 수업

## Pandas

> Numpy 기반으로 만들어진 데이터 조작, 분석을 위한 프레임워크 


<span style="color:orange">Pandas로 할 수 있는 2가지</span>
```
1. 기초통계분석
2. 전처리 
- 반정형 데이터를 정형데이터로 바꿔준다 
```

## 데이터 종류 

```
1. 정형 데이터 : Dataframe 객체에 정확하게 컬럼에 집어 넣을 수 있는 데이터 
2. 비정형 데이터 
3. 반정형 데이터 
```

## 데이터 타입 만드는 방법 

### Numpy 방식 (structured array)
```python	
import numpy as np

x = np.array([('jihyuk',25,73.0),('thor',35,85.0),('lion',10,30.0)],dtype=[('name','U10'),('age','i4'),('weight','f4')])  

x[0]
: ('jihyuk',25,73.0)
x[0]['name']  # dict의 key값으로 접근
: 'jihyuk'
```

### Python 방식 (namedtuple)

```python
from collections import namedtuple

x = namedtuple('Address',['name','age','weight'])
a = x('jh',25,'73.0)

a.name  # attribute
a.age
: 'jh'
  25
```

## Pandas로 기초통계분석하기 
 
### [첫번째] 데이터 불러들이기 

```python
import pandas as pd

data = pd.read_csv('/Users/SAMSUNG/Desktop/개인공부/AI/AI 이노베이션 스퀘어 기본과정/수업 내용/abc.csv',engine='python')
type(data)
: pandas.core.frame.DataFrame

# read 메소드는 flat file 또는 sql format을 dataframe형태로 불러들인다
# 첫번째 인자는 불러올 파일의 경로인데 현재 작업파일과 동일한 위치에 있다면 파일이름만 적어줘도 된다
# engine = 'python' 이나 encoding = 'cp949'를 인자로 넣어주지 않으면 unicodeerror가 뜬다 
```
![read method](https://user-images.githubusercontent.com/33630505/58368737-26567680-7f2c-11e9-9581-e21370c90f49.JPG)

**filepath_buffer**는 read_csv 메소드의 첫번째 인자로 파일경로나, url이 올 수 있다  
{: .notice}

**Dataframe** 객체는 Numpy에서 structured array방식을 따라 데이터 타입을 생성한다. 왜냐하면 pandas는 Numpy를 기반으로 만들어졌기 때문에 Numpy방식을 그대로 이어받아 속도를 빠르게 하기 위함이다! 그리고 dict, attr 두가지 방법으로 모두 접근 가능하다.
{: .notice}

**Series** 객체는 Dataframe에서 1차원 데이터 한 행이나 한 열, 1차원이기 때문에 방향은 없다. Series는 dataframe 처럼 dictionary 형태로 구성되어 있고 key값으로 index가 자동 생성이 된다.
{: .notice}

```python
import pandas as pd

data = np.read_csv('abc.csv', engine='python')
data.values

: array([['절도', ' 129 ', ' 217 ', ..., ' 1 ', ' - ', nan],
       ['불법사용', ' - ', ' - ', ..., ' - ', ' - ', nan],
       ['침입절도', ' 29 ', ' 38 ', ..., ' - ', ' - ', nan],
       ...,
       ['화재예방·소방시설설치유지및안전관리에관한법률', ' - ', ' - ', ..., ' - ', ' - ', nan],
       ['화학물질관리법', ' 1 ', ' - ', ..., ' 3 ', ' - ', nan],
       ['기타특별법', ' 26 ', ' 226 ', ..., ' 4 ', ' - ', nan]], dtype=object)
       
# dict으로 접근해서 values를 사용하면 numpy format인것을 확인할 수 있다       
```

### Series , Vector 차이점 

Series, Vector 둘다 1차원 데이터에 방향도 없지만 Series는 index가 붙는다

<br>


### [두번째] 분석하고 그래프 그리기 


### 분석하기전 5가지 확인 사항 

> 데이터를 분석하기 전에 분석할 가치가 있는 데이터인지 부터 판단해야 한다!  데이터의 갯수가 충분한지 여부도 체크하고, 내가 불러들일 수 있는 크기의 데이터 양인지 체크하고 편향된 데이터값이 많은지 등등 알고서 분석에 적합한 데이터를 판별해야한다. (데이터가 많으면 많을 수록 분석, 예측시 성능이 좋아진다! 

```
1. info : 데이터의 기본 정보를 보여준다 
2. describe : 숫자형태인 데이터에 대해서 기본 통계값을 보여준다
3. head : default로 앞에서 5개 데이터만 불러온다 (앞에서부터 보고싶은 데이터 갯수 입력 가능)
4. tail : head와 반대로 뒤에서 부터 데이터를 불러온다 
5. sample : 랜덤으로 하나의 데이터를 불러온다 
```

### info, describe로 데이터의 숨겨진 의미 찾기 

1. column 갯수 확인 => 차원의 저주 고려 <br> 
2. 데이터 갯수 확인 => 큰 수의 법칙 고려 <br>
3. 미싱 데이터 찾기 => 미싱데이터를 포함하고 있으면 정확도  <br>
4. 데이터 타입 확인 => 적절한 타입을 썻는지 체크 (category, object는 각각 지원하는 기능이 다르다) <br>


<br>

#### data (도로교통공단_시도_시군구별_도로형태별_교통사고(2018) 공공데이터)

> pandas로 불러오면 rangeindex가 붙는다 

![accident](https://user-images.githubusercontent.com/33630505/58369114-09707200-7f31-11e9-8b4b-cfcc10731401.JPG)


#### info 

```python
import pandas as pd

data = pd.read_csv('load.csv', engine = 'python') 
data.info()

: <class 'pandas.core.frame.DataFrame'>
  RangeIndex: 2001 entries, 0 to 2000
  Data columns (total 9 columns):
  시도      2001 non-null object
  시군구     2001 non-null object
  도로형태    2001 non-null object
  발생건수    2001 non-null int64
  사망자수    2001 non-null int64
  부상자수    2001 non-null int64
  중상      2001 non-null int64
  경상      2001 non-null int64
  부상신고    2001 non-null int64
  dtypes: int64(6), object(3)
  memory usage: 140.8+ KB
  
# 교통사고 공공데이터  
```


#### describe

```python
import pandas as pd 

data = pd.read_csv('load.csv', engine = 'python') 
data.describe()
```
![describe](https://user-images.githubusercontent.com/33630505/58369143-5f451a00-7f31-11e9-8bf4-b9dcac83f844.JPG)


#### head, tail, sample 

```python
import pandas as pd 

data = pd.read_csv('load.csv', engine = 'python') 
data.head(3)
data.tail(3)
data.sample(3) # replace = True 옵션을 주면 복원추출
```

![head](https://user-images.githubusercontent.com/33630505/58369306-78e76100-7f33-11e9-9abc-f94e94aac804.JPG)
![tail](https://user-images.githubusercontent.com/33630505/58369307-7a188e00-7f33-11e9-9254-1fdaa0245e32.JPG)
![sample](https://user-images.githubusercontent.com/33630505/58369313-90bee500-7f33-11e9-8549-92b5635e9a3d.JPG)

#### 표준편차 표로 보기 (boxplot)

![boxplot](https://user-images.githubusercontent.com/33630505/58369325-c237b080-7f33-11e9-9d04-2ec773255130.JPG)

### 왜도(skewness), 첨도(kurtosis) 

**왜도** <br>
왜도는 데이터가 대칭이 아닌 정도를 나타낸다 <br>
왜도의 값이 음수이면 오른쪽으로 치우친 정도를 나타내고 <br>
왜도의 값이 양수이면 왼쪽으로 치우친 정도를 나타낸다 <br>
<br>
**첨도** <br>
첨도는 데이터가 중간값의 분포도의 정도를 나타낸다 <br>
첨도의 값이 3보다 작으면 완만한 분포를 나타내고 <br>
첨도의 값이 3보다 크면 뾰족한 분포를 나타낸다 <br>

```python
import pandas as pd

data = pd.read_csv('load.csv', engine = 'python')
data.skew()
data.kurtosis() # kurt

: 발생건수    3.765094
사망자수    3.820251
부상자수    3.778984
중상      3.541237
경상      3.847238
부상신고    5.351853
dtype: float64

발생건수    17.881821
사망자수    18.509412
부상자수    17.783772
중상      15.962331
경상      18.220330
부상신고    40.538785
dtype: float64
```

## 열 뽑는 4가지 방법 

```
1. dictionary 
2. attribute
3. fancy indexing
4. data type
```

**Pandas Tip1** 데이터 분석시 데이터 조작을 하기위해 할당을 하는 경우에 view방식으로 접근하게되면 원본 데이터도 변경될 수 있으므로 copy방식을 사용해야 한다 
{: .notice}


## 행 뽑는 방법 

iloc

## 문제해결 그리고 예측 

<span style="background-color:orange">많은 데이터 확보 => 기초 통계분석 및 전처리 => 기계학습 및 딥러닝으로 예측 </span>


## Exploratory Data Analysis


### nan값 제거 
```python
import pandas as pd

data = pd.read_csv('abc.csv',engine='python')
data.iloc[4].dropna() 
```


<hr>

##### indexing, slicing 연습 
##### Numpy_exercises 연습하기 
**복습 시간**
{: .notice}


# 2019년 5월 26일 일요일 Jupyter Notebook 오류 

> Numpy 예제 100선을 풀기 위해 파일을 불러오는 도중 해당 파일이 Not trusted 문제가 발생했다 

## Not trusted 

내가 작성한 파일이 아닌 다른 사람에 의해 만들어진 파일이라서 보안상 문제가 될 수 있어 발생한 오류 인것 같다<br>
그래서 열고자 하는 파일이 믿을만하다는 것을 알려주기 위해서 명령 프롬프트를 통해 신뢰할만한 파일이라고 직접 알려줘야 한다<br>

```shell
jupyter trust name.ipynb
```
위 명령어를 입력하자 not trusted 오류는 발생하지 않았다 <br>

## 페이지를 열기 위한 메모리가 충분하지 않음

크롬 브라우저에서 메모리가 부족하다는 것이다. <br>
그래서 쿠키정보를 삭제해보았다.

**해결!** <br>
그러나 힌트파일이 아닌 정답파일은 파일 자체 내용이 많아서 그런지 아직도 안열린다... 



# 2019년 5월 27일 월요일 열여섯번째 수업


## 유니콘이 되려면...

![unicon](https://user-images.githubusercontent.com/33630505/58414654-fedfe500-80b6-11e9-950d-03888fd83082.JPG)

**Data Wrangling** Raw data를 또 다른 형태로 수작업으로 전환하거나 매핑하는 과정. 즉, 여러가지 데이터 포멧을 내가 원하는 데이터 포멧으로 전환하여 사용하기 위한 과정. (Data Munging 이라고도 불린다) 
{: .notice}

## 그래프 그리기 

### describe로 나오는 값들 그래프로 그리기 
```python
import numpy as np
import pandas as pd 
import seaborn as sns 

data = pd.read_csv('file.csv', engine='python')
pd.plotting.boxplot(data)
```
![describe](https://user-images.githubusercontent.com/33630505/58414617-e374da00-80b6-11e9-9e72-168df4140f90.JPG)

### 정규분포가 되는지 확인하는 그래프 그리기 

```python
import numpy as np
import pandas as pd 
import seaborn as sns 

data = pd.read_csv('file.csv', engine='python')
pd.plotting.scatter_matrix(data)
```
![scatter](https://user-images.githubusercontent.com/33630505/58416173-aeb75180-80bb-11e9-8cc3-5d8f83737d5d.JPG)

## matplotlib inline & notebook

```python
%matplotlib inline
data.boxplot()

%matplotlib notebook
data.boxplot()
```

### inline
![inline](https://user-images.githubusercontent.com/33630505/58416292-0f468e80-80bc-11e9-9789-12627d6fbdd7.JPG)

### notebook
![notebook](https://user-images.githubusercontent.com/33630505/58416310-1bcae700-80bc-11e9-90c0-54f9ba8cd9aa.JPG)


## seaborn으로 그래프 이쁘게 그리기 

```python
import seaborn as sns 

data = pd.read_csv('file.csv', engine='python')
sns.pairplot(data)
```

![seaborn](https://user-images.githubusercontent.com/33630505/58416408-63ea0980-80bc-11e9-818c-93fbe478439e.JPG)

## Header name 바꾸기 (전처리 과정중 일부) 

```python
import pandas as pd

data = pd.read_csv('file.csv', engine='python')
data.rename({0:'sl',1:'sw',2:'pl',3:'pw','class':'class_'},axis=1,inplace=True) 

# inplace True하면 자기자신이 바뀜
```

## 짝을 이뤄 그래프 그리기 

> 열(column)에 object가 있을 때 

```python
import pandas as pd

data = pd.read_csv('file.csv', engine='python')
data.rename({0:'sl',1:'sw',2:'pl',3:'pw','class':'class_'},axis=1,inplace=True) 
sns.pairplot(data,hue='class_') 
```

![hue](https://user-images.githubusercontent.com/33630505/58416593-115d1d00-80bd-11e9-8b8a-59429b3f8b51.JPG)


## Tidy Data 

<kbd>Wide format</kbd> ⇒  <kbd>Long format</kbd>

> 분석하기 좋은 데이터. Tidy data 형태로 만들면 차원도 줄고, 유지보수하기도 좋다 

**Tidy Data 특징** 

```
1. 각 변수는 개별의 열(column)로 존재한다
2. 각 관측치는 행(row)으로 구성한다 
3. 각 표는 단 하나의 관측기준에 의해서 조작된 데이터를 저장한다 
4. 만약 여러개의 표가 존재한다면, 적어도 하나이상의 열이 공유되어야 한다
```

> 위 원칙들은 관계형 데이터베이스 원칙과 유사하다 

※ 예시 

변수 : 키, 몸무게, 성별 <br>
값 : 175, 73, 남자 <br>
관측치 : 사람  (값을 측정한 단위가 되는 기준) <br> 

```python
import pandas as pd 

data = pd.read_csv('file.txt')
data.melt(['iso2','year'], var_name='sp', value_name='값').dropna()
```
![tidy data](https://user-images.githubusercontent.com/33630505/58412407-58451580-80b1-11e9-869a-56ce832033bb.JPG)

**주의** <br>
Tidy Data화 하지 않으면 info, describe, 등.. 초기 작업시 엉망으로 값이 나온다 

<br>
### 행 뽑기

```python
tb.loc[5:7]
```
![loc](https://user-images.githubusercontent.com/33630505/58419146-bd563680-80c4-11e9-99e6-fd1fa156b058.JPG)
```python
tb.iloc[1:3] # 파이썬 방식 
```
![iloc](https://user-images.githubusercontent.com/33630505/58419147-bd563680-80c4-11e9-9aeb-d56d82b27083.JPG)
## 상관성 체크하기  (correlation)

> 두 변수간에 어떤 선형적 관계를 갖고 있는지 분석하는 방법이 상관 분석. 그렇다면 상관성 있다는 것은 얼마나 관계가 있는지에 대한 정도라고 볼 수 있다. 만약 상관성이 1에 가깝다면 두 변수는 매우 관련 이 있다. 예를 들어 키가 크면 몸무게가 많이 나가는 것처럼 서로 관계가 가까운것. 

**양의 상관성**: 기준이되는 변수가 커지면 상대 변수도 같이 커진다 <br>
**음의 상관성**: 기준이되는 변수가 커지면 상대 변수는 작아진다 <br> 

<span style='color: red'>상관 분석은 왜 하는거야?</span><br>
데이터 분석시 column이 많아지면 계산이 복잡해지는데 상관관계를 따져 <br>
상관성이 높은 것들은 분석 데이터에서 제외시켜 계산 복잡도를 크게 줄일 수 있기 때문이다.
<br>

```python
import pandas as pd

data = pd.read_csv('file.txt')
data.rename({0:'sl',1:'sw',2:'pl',3:'pw','class':'class_'},axis=1,inplace=True)
data.corr() # method = {'pearson', 'kendall', 'spearman'}
```
![corr](https://user-images.githubusercontent.com/33630505/58418421-a9a9d080-80c2-11e9-9188-af2eb88e45b1.JPG)

**공분산**
```python
data.cov()
```

## 문자열에 사용하는 것들 

### Series에서 object(문자열) 빈도수 체크하기 

```python
import pandas as pd

data = pd.read_csv('file.txt')
data.rename({0:'sl',1:'sw',2:'pl',3:'pw','4':'class_'},axis=1,inplace=True)
data['class_'].value_counts()

: Iris-versicolor    50
  Iris-setosa        50
  Iris-virginica     50
  Name: class_, dtype: int64
  

data['class_'].value_counts().plot.pie()
data['class_'].value_counts().plot.bar()
```
![pie](https://user-images.githubusercontent.com/33630505/58419044-78320480-80c4-11e9-8ebb-cca88b2feb3b.JPG)
![bar](https://user-images.githubusercontent.com/33630505/58419048-79fbc800-80c4-11e9-980c-5105d90b2777.JPG)


### nlargest, nsmallest, unique

```python
x = data['class_'].value_counts()

x.nlargest()
x.nsmallest()
data['class_'].unique() 

: Iris-versicolor    50
  Iris-setosa        50
  Iris-virginica     50
  Name: class_, dtype: int64
 
  Iris-versicolor    50
  Iris-setosa        50
  Iris-virginica     50
  Name: class_, dtype: int64
   
  array(['Iris-setosa', 'Iris-versicolor', 'Iris-virginica'], dtype=object)
```


## 기초 통계 분석시 알아두면 좋은 원칙 및 정리


```
1. Occam's Razor (오캄의 면도날)
- 같은 성능을 보일 때 간단한것을 택한다
2. Curse of dimensionality (차원의 저주)
- 차원이 커지면 커질수록 필요한 데이터의 양이 커져야 한다 
3. Law of large numbers (큰 수의 법칙)
- 큰 모집단에서 무작위로 뽑은 표본의 평균이 전체 모집단의 평균과 가까울 가능성이 높다
- 모집단이 커지면 표본평균은 모평균을 더 정확히 추정할 수 있다
4. Central limit theorem (중심 극한 정리)
- 동일한 확률분포를 가진 독립 확률 변수 n개의 평균의 분포는 n이 적당히 크다면 정규분포에 가까워진다는 정리
```


## Indexing & Slicing (Select data)

내가 필요한 통계값 구하기 위해


## MultiIndex 

![multiindex](https://user-images.githubusercontent.com/33630505/58419324-440b1380-80c5-11e9-9630-d4f56d60c460.JPG)

**Pandas Tip1** 예측 분석을 하려면 문자열을 숫자로 바꿔줘야한다 (Encoding)
{: .notice}

<br>

**예시에 나오는 데이터 출처** : [archive](https://archive.ics.uci.edu/ml/machine-learning-databases/iris/)<br>

**복습시간** 18시 30분 ~ 21시 / 총 2시간 30분 
{: .notice}


# 2019년 5월 28일 화요일 열일곱번째 수업

## loc, iloc + lambda

```python
import pandas as pd 
import numpy as np 

data = pd.DataFrame(np.random.randn(6,4), index = list('abcdef'), columns = list('ABCD')
data
: 	   A	            B               C               D
a	0.427092	1.122736	1.064223	-0.724660
b	0.091881	1.049868	1.263243	-0.193525
c	0.224007	-1.128729	-1.261087	2.461563
d	-0.859961	-0.450851	-0.098474	0.456542
e	0.339599	-0.946570	0.892721	-0.331624
f	1.691290	-0.565636	0.905357	-0.301717

data.loc[lambda x: x.B>0, :]
: 	   A	            B               C               D
a	0.427092	1.122736	1.064223	-0.724660
b	0.091881	1.049868	1.263243	-0.193525

data.loc[:, lambda x:['D','A']]
:           D	           A
a	-0.724660	0.427092
b	-0.193525	0.091881
c	2.461563	0.224007
d	0.456542	-0.859961
e	-0.331624	0.339599
f	-0.301717	1.691290

data.iloc[:,lambda x:[0,3]]
:           A	            D
a	0.427092	-0.724660
b	0.091881	-0.193525
c	0.224007	2.461563
d	-0.859961	0.456542
e	0.339599	-0.331624
f	1.691290	-0.301717

data[lambda x: x.columns[3]]
: a   -0.724660
  b   -0.193525
  c    2.461563
  d    0.456542
  e   -0.331624
  f   -0.301717
Name: D, dtype: float64
```

## columns 

```python
import seaborn as sns 

tips = sns.load_dataset('tips')
tips
:    total_bill	 tip	 sex   smoker	day	time	 size
0	16.99	1.01	Female	 No	Sun	Dinner	  2
1	10.34	1.66	Male	 No	Sun	Dinner	  3
2	21.01	3.50	Male	 No	Sun	Dinner	  3
3	23.68	3.31	Male	 No	Sun	Dinner	  2

tips.melt(tips.columns[:3])    #  열만 따로 뽑기 
:    total_bill	 tip	sex	variable   value
0	16.99	1.01	Female	smoker	     No
1	10.34	1.66	Male	smoker	     No
2	21.01	3.50	Male	smoker	     No
3	23.68	3.31	Male	smoker	     No
```

## index 

```python
import pandas as pd
data = pd.read_csv('billboard.csv',engine='python')
data.melt(data.columns[:7]).set_index('genre').loc['Rock']
 
: 	year	artist.inverted	     track	     time	    date.entered       date.peaked    variable        value
genre								
Rock	2000	Destiny's Child	 Independent         3:38            2000-09-23         2000-11-18    x1st.week      78.0
                                  Women Part I	     		                         	  
Rock	2000	  Santana	 Maria, Maria	     4:18	     2000-02-12	        2000-04-08    x1st.week	     15.0
Rock	2000	Savage Garden	I Knew I Loved You   4:07	     1999-10-23	        2000-01-29    x1st.week	     71.0
Rock	2000	Madonna	             Music	     3:45	     2000-08-12	        2000-09-16    x1st.week	     41.0
````

## Intersection 

```python
a = {1,2,3}
b = {3,4}

a.intersection(b)
: {3}
a.intersection([3,4])
: {3}
a.intersection(range(3))
:{1,2}
```

## 새로운 연산자 만들기 

```python
class x(int):
	def __add__(self, other):
		print('안더해줌')

x(3) + x(4)
: 안더해줌 
```

## isin (predicate)

```python
s = pd.Series(np.arange(5), index=np.arange(5)[::-1], dtype='int64')

s.isin([2, 4, 6])
: 4    False
  3    False
  2     True
  1    False
  0     True
  dtype: bool
  
s[s.isin([2, 4, 6])]  
: 2    2
  0    4
  dtype: int64
```

## where

## split, strip


**복습시간** 12시 ~ 1시 30분 / 총 1시간 30분 
{: .notice}



# 2019년 5월 30일 목요일 열여덟번째 수업


## 기초통계 분석시 그래프 그리는 3가지 

```
1. boxplot
2. pairplot
3. heatmap 
```

### boxplot

```python
import pandas as pd 
import seaborn as sns 

tips = sns.load_dataset('tips')
tips.boxplot()  # tips Dataframe의 attribute로 내장하고 있음 
# or
pd.plotting.boxplot(tips)
```

### pairplot

> 짝을 이뤄 그리는 그래프 

```python
import pandas as pd 
import seaborn as sns 


tips = sns.load_dataset('tips')
sns.pairplot(tips)  # tips Dataframe의 attribute로 내장하고 있지 않다 
sns.pairplot(tips, hue='sex')
```

### heatmap 

> 상관 분석시 그리는 그래프 

```python
import seaborn as sns

tips = sns.load_dataset('tips')
sns.heatmap(tips.corr())
sns.heatmap(tips.corr(), cbar = False, annot = True) # 오른쪽 사이드바 제거, 평면에 상관계수 표시 
```

## Dataframe은 Iterator/Generator 처럼 next연산을 할 수 있다 

```python
import seaborn as sns 

tips = sns.load_dataset('tips')
x = tips.items() # or x = tips.iteritems()
y = tips.iterrows() 
type(x)
type(y)
next(x)
next(y)
: generator 
  generator 
  ('total_bill', 
   0      16.99
   1      10.34
   2      21.01
   3      23.68
   4      24.59
   5      25.29
   (0, total_bill     16.99
   tip             1.01
   sex           Female
   smoker            No
   day              Sun
   time          Dinner
   size               2
   Name: 0, dtype: object)
```


## Pandas data type 종류 

```
1. 숫자      => int64, float64
2. 문자      => object, category
3. 시간/날짜 
```

**Dask**는 메모리의 제한으로 dataframe을 만들 수 없는 경우 도움을 줄 수 있는 패키지 이다. 파이썬으로 작성한 작업을 병렬화 할 수 있다.
{: .notice}


```python
!dir 

: 2019-05-25  오후 10:01             4,173 pandas.ipynb
  2019-05-25  오후 08:49           139,785 pandas2.ipynb
  2019-05-26  오후 02:51           220,247 pandas3.ipynb
  2019-05-27  오후 09:18           749,763 pandas4.ipynb

----------------------------------------------------------
# 오늘 받은 패키지 

!pip install vincent 
!pip install -q pdvega # -q 옵션은 설치시 나오는 메시지 생략 
                       # -U 옵션은 최신 버전이 아닐 경우 업데이트 
```
**Jupyter Tip1** jupyter에서 !(느낌표) 뒤에 cmd에서 작동하는 명령어를 치면 작동한다 
{: .notice}



<br>

**pdvega** <br>

```python
import pdvega

s = tips.groupby('smoker')
s.vgplot.bar()
```

![vgplot](https://user-images.githubusercontent.com/33630505/58626155-11545b80-830f-11e9-8744-da3eb42a2161.JPG)


## Aggregation analysis (집합 분석)

### Groupby의 내부적 구현 순서 

```
1. iterrow 순회 
2. split        => groupby
3. apply        => mean, max ... (통계적으로 대표할 수 있는 값 설정)
4. combine      => 결과 묶기 
```

## Group 3총사 

```
1. groupby 
2. pivot table 
3. crosstab (pd로 접근) 
```

### 2. pivot table
```python
import seaborn as sns

tips = sns.load_dataset('tips')
tips.pivot_table(index='smoker', columns = 'sex', aggfunc = np.sum, margins = True)
# margin은 중간값을 보여줌 

:  	size	                tip	                total_bill
sex	Male	Female	All	Male	Female	All	Male	Female	All
smoker									
Yes	150	74	224	183.07	96.74	279.81	1337.07	593.27	1930.34
No	263	140	403	302.00	149.77	451.77	1919.75	977.68	2897.43
All	413	214	627	485.07	246.51	731.58	3256.82	1570.95	4827.77
```

### 3. crosstab

```python
import seaborn as sns

tips = sns.load_dataset('tips')
a = pd.crosstab(tips.smoker, tips.sex, tips.tip, aggfunc = np.max)
a.index 

# smoker가 index, sex가 column, tip이 value, aggfunc는 value의 대푯값 

: 
sex	Male	Female
smoker		
Yes	10.0	6.5
No	9.0	5.2 

CategoricalIndex(['Yes', 'No'], categories=['Yes', 'No'], ordered=False, name='smoker', dtype='category')

b = pd.crosstab(tips.smoker,[tips.sex,tips.time],tips.tip,aggfunc=np.max)
b.index
# multi columns

: 
sex	Male	        Female
time	Lunch	Dinner	Lunch	Dinner
smoker				
Yes	5.0	10.0	5.00	6.5
No	6.7	9.0	5.17	5.2

CategoricalIndex(['Yes', 'No'], categories=['Yes', 'No'], ordered=False, name='smoker', dtype='category')

c = pd.crosstab([tips.smoker,tips.sex],tips.time,tips.tip,aggfunc=np.max)
c.index

: multi index
        time	Lunch	Dinner
smoker	sex		
Yes	Male	5.00	10.0
        Female	5.00	6.5
No	Male	6.70	9.0
        Female	5.17	5.2

MultiIndex(levels=[['Yes', 'No'], ['Male', 'Female']],
           codes=[[0, 0, 1, 1], [0, 1, 0, 1]],
           names=['smoker', 'sex'])

d = pd.crosstab([tips.smoker,tips.sex],tips.time,tips.tip,aggfunc=np.max).index
d.labels # or d.codes

: FrozenList([[0, 0, 1, 1], [0, 1, 0, 1]])
```


```python
# sequnce 방식 
x.codes 
: FrozenList([[0, 0, 1, 1], [0, 1, 0, 1]])

x.labels[0]

# attribute 방식 
from collections import namedtuple
n = namedtuple('Jung', ['x','y'])
a = n(1,2)
a
: Jung(x=1, y=2)

a.x
a.y
: 1
  2 
```
**Pandas Tip1** 데이터 형태가 []를 포함하면 sequence 방식 , xx = yy 가 있으면 attribute 방식
{: .notice}

## reindex & resetindex

> reindex는 수동으로 index변경, resetindex는 0부터 자동으로 index 변경 

### resetindex
```python
import seaborn as sns 

tips = sns.load_dataset('tips')
n = tips[tips.sex == 'Male'].loc[:15] # 맨처음 index부터 15 index까지 행 뽑기 
n.reset_index(drop=True)  # 기존 index 버리고 0부터 새로 생성

: 	total_bill	tip	sex	smoker	day	time	size
0	  10.34	        1.66	Male	No	Sun	Dinner	  3
1	  21.01	        3.50	Male	No	Sun	Dinner	  3
2	  23.68	        3.31	Male	No	Sun	Dinner	  2
3	  25.29	        4.71	Male	No	Sun	Dinner	  4
4	  8.77	        2.00	Male	No	Sun	Dinner	  2
5	  26.88	        3.12	Male	No	Sun	Dinner	  4
6	  15.04	        1.96	Male	No	Sun	Dinner	  2
7	  14.78	        3.23	Male	No	Sun	Dinner	  2
8	  10.27	        1.71	Male	No	Sun	Dinner	  2
9	  15.42	        1.57	Male	No	Sun	Dinner	  2
10	  18.43	        3.00	Male	No	Sun	Dinner	  4
11	  21.58	        3.92	Male	No	Sun	Dinner	  2

n.reset_index() # 기존의 index 삭제 X 

:     index	total_bill	tip	sex	smoker	day	time	size
0	1	10.34	        1.66	Male	No	Sun	Dinner	  3
1	2	21.01	        3.50	Male	No	Sun	Dinner	  3
2	3	23.68	        3.31	Male	No	Sun	Dinner	  2
3	5	25.29	        4.71	Male	No	Sun	Dinner	  4
4	6	8.77	        2.00	Male	No	Sun	Dinner	  2
5	7	26.88	        3.12	Male	No	Sun	Dinner	  4
6	8	15.04	        1.96	Male	No	Sun	Dinner	  2
7	9	14.78	        3.23	Male	No	Sun	Dinner	  2
8	10	10.27	        1.71	Male	No	Sun	Dinner	  2
9	12	15.42	        1.57	Male	No	Sun	Dinner	  2
10	13	18.43	        3.00	Male	No	Sun	Dinner	  4
11	15	21.58	        3.92	Male	No	Sun	Dinner	  2

```

## 행, 열 위치 변환하기 

### 기준 데이터 
```python
tips.groupby(['sex','smoker']).mean()[['tip']]


		tip
sex	smoker	
Male	Yes	3.051167
        No	3.113402
Female	Yes	2.931515
        No	2.773519

```

### stack 
```python
tips.groupby(['sex','smoker']).mean()[['tip']].stack()

sex     smoker     
Male    Yes     tip    3.051167
        No      tip    3.113402
Female  Yes     tip    2.931515
        No      tip    2.773519

dtype: float64
# 1차원으로 바뀜 
```

### unstack 

```python
tips.groupby(['sex','smoker']).mean()[['tip']].unstack()

	tip
smoker	Yes	        No
sex		
Male	3.051167	3.113402
Female	2.931515	2.773519

```

### Column이 2개 이상일 때 그래프 

#### Stacked = True (Column값을 쌓는다)
```python
tips.groupby(['day','sex']).mean()[['tip']].unstack().plot.bar(stacked=True)
```
![stacked_True](https://user-images.githubusercontent.com/33630505/58628687-5f6c5d80-8315-11e9-9c14-5bc64e11af28.JPG)

#### unstack(0) (index와 열의 조합)
```python
tips.groupby(['day','sex']).mean()[['tip','total_bill']].unstack(0).plot.bar(stacked=True)
```
![zero](https://user-images.githubusercontent.com/33630505/58629825-79f40600-8318-11e9-9a54-a760d7049719.JPG)

#### Stacked = False (Column값을 쌓지 않는다)
```python
tips.groupby(['day','sex']).mean()[['tip']].unstack().plot.bar(stacked=False)
```
![stacked_False](https://user-images.githubusercontent.com/33630505/58628716-714e0080-8315-11e9-812d-006a2a4efea9.JPG)

#### unstack(1) (header와 열의 조합)

```python
tips.groupby(['day','sex']).mean()[['tip','total_bill']].unstack(1).plot.bar(stacked=True)
```

![one](https://user-images.githubusercontent.com/33630505/58629826-79f40600-8318-11e9-81a2-e408173faa35.JPG)

**sci** Stack은 Column을 Index로 바꿔주고, Unstack은 Index를 Column으로 바꿔준다
{: .notice}



**복습시간** 18시 13분 ~ 20시 21분/ 총 2시간 8분 
{: .notice}




# 2019년 5월 30일 금요일 열아홉번째 수업



## Data Visualization 

> 문자나, 숫자 보다 그림으로 혹은 그래프로 시각적인 정보가 사람에게는 더 명확하고 효율적으로 전달 되기 때문에 데이터 분석 결과를 시각화 할 수 있어야 한다 

### 시각화 라이브러리 
![lib](https://user-images.githubusercontent.com/33630505/58707963-5ea8f980-83f1-11e9-8a8e-33d77621fc9d.JPG)

### Python 시각화 라이브러리 분류 
![pylib](https://user-images.githubusercontent.com/33630505/58707964-6072bd00-83f1-11e9-99ab-3f366ebac47e.JPG)

> Costumize하려면 Matplotlib을 사용해야 한다 

**matplotlib, seaborn** matplotlib는 python, numpy format으로 데이터를 처리하고 seaborn은 pandas format으로 데이터를 처리한다. .value는 pandas 데이터 형태를 numpy format으로 바꿔준다 
{: .notice}


## Matplotlib 

1. pyplot 
2. pylab 

> 이제 pylab은 쓰지 않는다 

### 구성요소

![structure](https://user-images.githubusercontent.com/33630505/58708062-ab8cd000-83f1-11e9-842e-c69ea2654837.JPG)

![graph](https://user-images.githubusercontent.com/33630505/58708348-8187dd80-83f2-11e9-96df-29952d1ff993.JPG)

### 그래프 커스터마이징 하기 

```python
import matplotlibl.pyplot as plt 

# canvas, figure, axes는 생략하면 자동으로 생성해서 그래프를 그려준다 
# 단 생략하지 않으면 커스텀 할 수 있다 

plt.figure(figsize=(10,5), facecolor='yellow')    
plt.axes(xlim=(0,10),ylim=(0,10))  # xlim,ylim은 최대 범위를 지정 
plt.title('Title')
plt.xlabel('Time')
plt.ylabel('Rate')
plt.grid(axis='y')
plt.plot([1,2,3,4,5,6],[2,0,4,7,3,10], color='black', marker='o')
```
![plotgraph](https://user-images.githubusercontent.com/33630505/58708975-117a5700-83f4-11e9-9978-19420df353c3.JPG)


### matplotlib에서 제공해주는 스타일 

```python
plt.style.available

['bmh',
 'classic',
 'dark_background',
 'fast',
 'fivethirtyeight',
 'ggplot',
 'grayscale',
 'seaborn-bright',
 'seaborn-colorblind',
 'seaborn-dark-palette',
 'seaborn-dark',
 'seaborn-darkgrid',
 'seaborn-deep',
 'seaborn-muted',
 'seaborn-notebook',
 'seaborn-paper',
 'seaborn-pastel',
 'seaborn-poster',
 'seaborn-talk',
 'seaborn-ticks',
 'seaborn-white',
 'seaborn-whitegrid',
 'seaborn',
 'Solarize_Light2',
 'tableau-colorblind10',
 '_classic_test']
```

**예시**

```python
import seaborn as sns

iris = sns.load_dataset('iris')
plt.style.use('ggplot')
sns.pairplot(iris, hue='species')
```

![ggplot](https://user-images.githubusercontent.com/33630505/58709958-366fc980-83f6-11e9-8d80-2c457a90c1fb.JPG)


**복습시간** 22시 ~ 22시 40분 / 총 40분
{: .notice}


# 2019년 6월 3일 월요일 스무번째 수업

## Folium


folium => 분석에 필요한 단계구분도를 하기 위해서 사용함 


## file 불러오기 

보통 pandas로 파일을 불러오지만 
불러오지 못하는 파일은 open으로 불러와서 text(객체의 의미를 갖지 못함) => csv, json으로 불러와 의미 부여해주면 됨 (csv, json만)

나머지는 pickle로 

## pandas 불러드리는 방법 3가지 



**복습시간**  /
{: .notice}
