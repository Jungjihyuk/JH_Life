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

**잠깐!!** JSP도 controller 역할을 할 수 있는데 굳이 Servlet을 이용해서 MVC 패턴을 구성하는가? (MVC 패턴이 익숙하지 않다면 model1 & model2 파트를 읽어보세요!)
{: .notice}
```
좋은 프로그래밍이란 무엇일까?
먼저 객체 지향 프로그래밍에 있어서 코드의 재사용성, 가독성, 효율성은 굉장히 중요한 문제이다.
정상적으로 프로그램이 동작하더라도 코드를 실행이 되는것에만 
집중하여 만든다면 나중에 분명 후회하게 될것이다.
만약 누군가와 같이 협업을 하거나 비슷한 로직을 다시 구현해야 할 때가 오면 
코드가 복잡해서 유지보수 하기 힘들거나 개발 시간이 늘어나기 마련이다. 

그래서!! 
가독성, 재사용성, 효율성을 극대화 하기 위해서는 프로세스 단위를 적절하게 분리해 두는 것이 중요하다.
따라서 대부분의 로직들을 Servlet으로 만들고 보여지는 부분을 JSP로 구현하면 코드의 가독성도 높아지고 
재사용성, 효율성이 높아진다.

결과적으로 Servlet과 JSP의 분리로 프론트 엔드 개발자, 디자이너와 백엔드 개발자 작업환경이 쾌적해지는 것은 덤이다.
```

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
JSP로 구성된 웹 어플리케이션을 개발하다 보면 빠질 수 없는 개념이 있다. <br>
바로 Model 1, Model 2 그리고 MVC 패턴. <br>
Model1, 2은 웹 어플리케이션의 아키텍쳐이다. <br>
브라우저와 서버, 그리고 데이터베이스 간의 소통을 어떤 패턴으로 하는지에 대한 정형화된 방식이라고 생각하면 된다.<br>
이해가 가지 않는다면 Model1과 2는 각각의 프로그래밍하는 방식이라고만 생각해도 된다.<br> 
<br>
MVC 패턴은 Model, View, Controller의 약자로 Model 1과 2방식에서 사용되는 패턴이다.<br>
브라우저에서 url로 특정 어플리케이션을 요청하면 Controller가 어떤 행위인지 판단하고, 처리를 담당하는데 처리에 필요한 데이터를 <br>
Model에서 꺼내와 다시 Controller가 처리를 마치면 View를 통해 결과를 보여준다.<br>
<br>

그렇다면 MVC패턴이 적용된 Model 1과 2는 정확히 무엇일까? <br>

#### Model 1
![model1](https://user-images.githubusercontent.com/33630505/56863468-84597200-69f1-11e9-84e7-45fcfd0d04d3.JPG)

#### Model 2
![model2](https://user-images.githubusercontent.com/33630505/56863469-86233580-69f1-11e9-84a4-de7c0952a9bd.JPG)

위 그림을 보면 Model 1방식은 JSP가 View와 Controller의 역할을 하고 JavaBean이 Model역할을 한다. <br>
그리고 Model 2방식은 Servlet이 Controller역할을, JSP가 View 역할을 하고 JavaBean이 Model역할을 한다.<br>
<br>
여기서 Database를 공부해 본사람이라면 의문이 들수 있다. <br>
Model에서 데이터를 갖고 온다면 Database가 Model인거 아닐까? 라고 생각할 수 있다. <br>
그런데 Database에서 매번 데이터를 직접 꺼내오게되면 문제가 생긴다. <br>
보안상의 문제가 될수 있고, 처리 속도측면에서 저하될 가능성이 있다. (확인되지 않은 추측이므로 이부분은 그냥 넘어가도 좋다. 확실히 하고 싶다면 추가적으로 공부하도록 하자!) <br>
따라서 Model은 Database에서 필요한 데이터만 미리 저장해두고 이용하는 부분이라고 생각하면 된다.<br>


## 내장객체 & 메소드

## EL(Expression Language)

## JSTL(Java Standard Tag Library)

## JDBC(Java Database Connectivity)

