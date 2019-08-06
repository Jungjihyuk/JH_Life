---
layout: post
title: Bootstrap4 
excerpt: "부트스트랩 활용하기" 
date: 2019-08-07
tag:
- FrontEnd
- bootstrap
- css
- js
---

# 부트스트랩 시작하기 

## CSS 

```html 
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
```

<br>

## js

```html
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js" integrity="sha384-UO2eT0CpHqdSJQ6hJty5KVphtPhzWj9WO1clHTMGa3JDZwrnQq4sF86dIHNDz0W1" crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script>
```

<br>

## 예시 
```html
<!DOCTYPE html>
<html lang="ko"> <!-- Html 문서 페이지를 음성으로 읽어주는 기능을 사용할때 lang에 명시된 언어로 읽어준다 -->
<head> <!-- 로봇이나 기계에게 제공하는 정보를 담는 태그, 사람이 직접 보지 않는 부분 -->
    <meta charset="UTF-8">
    <title>지혁이네</title>
    
    <!-- device별로 1대1로 크기를 매칭시켜 보여줄때 쓰는 태그, Cross browsing 기법-->
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    
    <!-- 장점: 웹 브라우저가 request 할때 / core 주소당 한개씩 처리?? (속도가 빠르다) -->
    <!-- 단점: 참조하는 사이트가 서버 오류가 발생하면 같이 영향을 받아 오류가 발생할 수 있다 -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
</head>
<body>

    <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js" integrity="sha384-UO2eT0CpHqdSJQ6hJty5KVphtPhzWj9WO1clHTMGa3JDZwrnQq4sF86dIHNDz0W1" crossorigin="anonymous"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script>
</body>
</html>
```

<br>

**Cross browsing**  웹표준 기술을 적용하여 서로 다른 OS 또는 플랫폼(브라우저)에서도 인터넷이 이상 없이 구현되는 기술을 말한다.
{: .notice}

<br>


## Layout 

```
1. container 
2. container-fluid
```







