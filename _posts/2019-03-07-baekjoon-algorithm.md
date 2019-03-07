---
layout: post
title: 백준 알고리즘 문제 풀이
date: 2019-01-13
excerpt: "알고리즘 풀이 with python"
tag:
- algorithm
- 백준
---

## 2439번(정답) 
### 별찍기-2
```python
n = int(input())

for x in range(1, n+1):
	for y in range(x, n):
		print(" ", end="")
	print("*"*x)
```

## 2441번(정답)
### 별찍기-4
```python
n = int(input())

for x in range(1, n+1):
	for y in range(x, n+1):
		print("*", end="")
	print(" ")
	print(" "*x, end="")
```

## 7489번(오답)
### 팩토리얼
```python
for test in range(int(input())):
	num = int(input())
	facto = 1
	i = 0
	j = 0
	array = []
	if num == 1:
		print(1)
		break
	for i in range(2, num+1):
		facto = facto * i
		result = str(facto)
		array = list(result)
		array.reverse()
		length = len(array)
	for j in range(0, length):
		if array[j] == '0':
			continue
		elif array[j] != '0':
			print(array[j])
			break
```
* 테스트 갯수 입력후 숫자 n 입력하면 factorial 결과에서 0이 아닌 가장 마지막 숫자 출력 
  이를 테스트 갯수만큼 실행. (실행은 되지만 백준online에서 오답이라고 표시함)
  왜 틀렸을까...?


