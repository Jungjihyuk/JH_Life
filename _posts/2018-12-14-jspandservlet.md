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
# Jsp & Servlet 
> 책을 바탕으로 이해하기 쉽게 재구성 하였습니다. <br>
<strong>목차</strong> <br> 
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

# Jsp와 Servlet 

## Jsp

``` 
Jsp(Java Server Page)는 자바로 서버 페이지를 작성하기 위한 언어 및 파일. 
동적 데이터를 처리할 수 있는 HTML + Java 페이지 또는 언어라고 볼 수도 있다. 
Jsp는 웹 어플리케이션의 관점에서 봤을 때 View의 역할을 한다. 
물론! JSP도 Controller 역할을 할 수 있다.
```
## Servlet

``` 
Servlet(Server + Applet)은 Applet의 단점을 극복하여 만들어진 java기반 서버 프로그램.
Servlet을 사용하면 클라이언트가 웹 브라우저를 통해 요청을 하면 서버에서 실행한 후 결과값만 전송합니다.
쉽게말해 동적 데이터 처리를 담당하여 결과값만 전송해주는 역할을 한다. 
Servlet은 웹 어플리케이션의 관점에서 봤을 때 Controller의 역할을 한다. 

```

**잠깐!!** JSP도 controller 역할을 할 수 있는데 굳이 Servlet을 이용해서 MVC 패턴을 구성하는가? 
{: .notice}

**Watch out!** This paragraph of text has been [emphasized](#) with the `{: .notice--warning}` class.
{: .notice--warning}

**Watch out!** This paragraph of text has been [why](#) with the `{: .notice--info}` class.
{: .notice--info}

**Watch out!** JSP도 controller 역할을 할 수 있는데 굳이 Servlet을 이용해서 MVC 패턴을 구성하는가? 
{: .notice--info}


## JSP 구성 요소 

1. <kbd><strong>디렉티브</strong></kbd> <br> 
- page : jsp 페이지에 대한 정보를 지정한다. (문서 타입, 출력버퍼의 크기, 에러 페이지 등)
- taglib: jsp 페이지에서 사용할 태그 라이브러리 지정 (코어태그)
- include: jsp 페이지의 특정 영역에 다른 문서를 포함시킨다. 

2. <kdb><strong>스크립트</strong></kdb> <br>
스크립트 기반 태그들은 <strong><%로 시작해서 %></strong>로 끝나는 것이 특징입니다.
- 주석문(comment) <br>
  jsp 주석문 <%- -%> <br>
  html 주석문 <!- ->
- 지시자(directive) <br>
  page: jsp 페이지에 종속적인 설정 정보를 알려준다. <br>
  contentType: 웹 브라우저에 전송되는 문서의 타입과 문자코드를 지정한다. <br>
  import: 내장 패키지를 사용할 때 해당 패키지를 사용할 수 있게 불러온다. <br>
  errorPage, is ErrorPage: jsp 페이지에서 오류가 발생했을 때 오류를 처리하기 위한 속성. <br>
  pageEncoding: jsp 소스 저장시 사용할 문자코드를 지정한다. <br>
  session: 해당 jsp 페이지의 세션 관리 처리 여부를 지정할 때 사용된다. <br>
  include: 다른 jsp 파일을 삽입한다. <br>
  language: 페이지에서 사용되는 스크립트 언어를 지정한다.<br>
- 스크립트릿(scriptlet) <br>
  <% %> <br>
  jsp 페이지 내에서 자바코드를 실행 하고 싶을 때 사용한다.
- 표현식(expression) <br>
  <%= %> <br>
  동적 데이터를 응답 결과에 포함 시키기 위해 사용한다. 
- 선언문(declaration) <br>
  <%! %> <br>
  jsp 페이지 내에서 사용할 멤버 변수를 선언하고 메소드를 정의하고자 할 때 사용된다. 

## Model 1 & Model 2 

## 내장객체 & 메소드

## EL(Expression Language)

## JSTL(Java Standard Tag Library)

## JDBC(Java Database Connectivity)

