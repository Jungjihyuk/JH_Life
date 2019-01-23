---
layout: post
title: python 문법 정리(자주 까먹는 것들)
date: 2019-01-23
excerpt: 'Do it! 점프 투 파이썬' 책
tag:
- python
- 한눈에 정리
---

# Python
> Do it! 점프 투 파이썬 책에 나온 까먹기 쉬운 내용들로 구성했습니다.
<strong>목차</strong><br>
1. 자료형
2. 클래스(변수와 객체) 
3. 제어문

### 자료형

```
- 숫자
- 문자열
- 리스트 
- 튜플
- 딕셔너리
- 집합
```
![1](https://user-images.githubusercontent.com/33630505/51591743-31bf7400-1f31-11e9-9b71-9850268ac951.jpg)
![2](https://user-images.githubusercontent.com/33630505/51591744-32580a80-1f31-11e9-9276-066bce8166ed.jpg)
![3](https://user-images.githubusercontent.com/33630505/51591745-32580a80-1f31-11e9-9b81-f6c7fcb9cd3a.jpg)
![4](https://user-images.githubusercontent.com/33630505/51591746-32580a80-1f31-11e9-9156-0534ecd4a94d.jpg)
![5](https://user-images.githubusercontent.com/33630505/51591748-32f0a100-1f31-11e9-8f6c-ef46202eacff.jpg)


### 클래스(변수와 객체)

```
변수:  객체를 저장한 공간.
객체: 메모리에 저장된 자료.
클래스(class): Field(상태) + Method(행동) 
        객체를 생성하기 위한 설계도.
인스턴스(instance): 클래스에 의해 생성된 객체
```
* 객체와 인스턴스 구분
```python
# int(정수형 클래스)
a=3
b=5
# a와 b는 서로 다른 객체, 같은 클래스의  인스턴스. 
a is b => False (a와 b가 같은 인스턴스 입니까?/No)
isinstance(a,int) => True (a가 int 클래스의 인스턴스 입니까?/Yes)
isinstance(b,int) => True (a가 int 클래스의 인스턴스 입니까?/Yes)
※ a==b a와 b가 같은 값을 가졌습니까? / No 
```


### 제어문 

```
- if 
- for 
- while 
```
* 제어문은 코드로 알아보자.

### if 문

```python
pocket = {'money':3000,'cellPhone':01090618472}
bag = {'note':'notebook','laptop':'samsung'}
if 'money' not in pocket and bag:
	pass
else: 
	print("버스를 탄다")
```	

### for 문 

```python 
# 순회할 리스트가 있는 경우

scores= [90, 25, 67, 45, 80]
number=0
for score in scores:
	number+1
	if score<60: continue
	print("%d번 학생 축하합니다."%number)
	print("{}점으로 합격입니다.".format(score))
```
```python
# 순회 횟수가 정해져 있는 경우

for i in range(11172):
	print(chr(44032+i), end="")
# 가 부터 힣까지 11172자 한글출력

for i in range(2,10):
	for j in range(1,10):
		print(i*j, end=" ")
	print("")
# 구구단 2~9단 출력 
```
### while 문

```python
coffee = 10
money = 0

while coffee != 0:
    print("남은 커피량 {}개".format(coffee))
    if coffee==1:
        print("커피를 채워주세요.")
        coffee=int(input("채울 커피량을 입력해주세요."))
        continue
    money = int(input("동전을 넣어주세요\n"))
    if (money == 300):
        print("커피가 나왔습니다.")
        coffee -= 1
    elif (money > 300):
        print("거스름돈:{}, 커피나왔습니다.".format(money-300))
        coffee -= 1
    else:
        print("{}원이 반환됩니다, 300원을 넣어주세요.".format(money))
```
