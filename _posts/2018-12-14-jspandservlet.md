---
layout: post
title: Jsp & Servlet
date: 2018-07-28 
excerpt: "JSP & Servlet 한눈에 보기. <br>
          '최범균의 JSP 2.3 웹 프로그래밍'책 정리"
tag: 
- Jsp
- Servlet
- 한눈에 보기 
comments: true
---
## Jsp & Servlet 
> 책을 바탕으로 이해하기 쉽게 재구성 하였습니다. 
목차 <br> 
1. Jsp와 Servlet 이란?
2. Jsp 구성 요소
- 디렉티브 
- 스크립트
- 표현언어(EL)
- 내장객체
- 정적 데이터
- 액션태그
- 커스텀 태그와 표준 태그 라이브러리
3. Model 1 & Model 2 
4. 내장객체 & 메소드
- 요청과 응답
- 출력
- pageContext
- application
- 쿠키
- 세션 
5. EL(Expression Language)
6. JSTL(Java Standard Tag Library)
7. JDBC(Java Database Connectivity)
---

## Jsp와 Servlet 

# Jsp

``` 
Jsp(Java Server Page)는 자바로 서버 페이지를 작성하기 위한 언어 및 파일. 
동적 데이터를 처리할 수 있는 HTML + Java 페이지 또는 언어라고 볼 수도 있다. 
Jsp는 웹 어플리케이션의 관점에서 봤을 때 View의 역할을 한다. 

```
# Servlet

``` 
Servlet(Server + Applet)은 Applet의 단점을 극복하여 만들어진 java기반 서버 프로그램.
Servlet을 사용하면 클라이언트가 웹 브라우저를 통해 요청을 하면 서버에서 실행한 후 결과값만 전송합니다.
쉽게말해 동적 데이터 처리를 담당하여 결과값만 전송해주는 역할을 한다. 
Servlet은 웹 어플리케이션의 관점에서 봤을 때 Controller의 역할을 한다. 

```


