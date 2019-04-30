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

**복습 시간**   18시 15분 ~ 19시 30분 / 총 1시간 15
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

하나의 요소를 갖는 튜플을 생성하려면 콤마를 적어줘야한다.
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

### 기타 내장 함수 
```
dir(obejct) : 어떠한 객체를 인자로 넣어주면 해당 객체가 어떤 변수와 메소드를 가지고 있는지 출력을 합니다. 
type(object) : 어떠한 객체를 인자로 넣어주면 해당 객체의 타입을 반환한다.
len(object) : 어떠한 객체를 인자로 넣어주면 해당 객체의 요소 갯수를 반환한다.
```

### Error
1. NameError
- 값을 할당하지 않은 식별자를 사용했을 때 발생하는 에러 
2. IndexError
- 인덱스 값에서 벗어난 인덱스를 사용했을 때 발생하는 에러 

**복습 시간**   18시 35분 ~ 20시 5분/ 총 1시간 30분  
{: .notice}


