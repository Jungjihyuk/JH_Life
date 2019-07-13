---
layout: post
title: Object Model 
excerpt: "object model로 웹 브라우저 이해하기"
date: 2019-07-13
tag:
- object model
- dom
- bom
- javascript
---


# Object Model 

> 웹 브라우저의 구성요소를 객체화시켜 객체처럼 사용할 수 있도록 하는 것 <br>
> 브라우저에 렌더링되는 HTML문서는 정적인 문서인데, 정적인 요소를 동적으로 제어하기 위한 객체화 방법<br>
> javscript로 제어할 수 있는 객체 형태로 만들어 준다 

![window](https://user-images.githubusercontent.com/33630505/61168962-0be66400-a591-11e9-9ad3-ced452f00481.JPG)
<br>

<span style="color: skyblue; font-size: 30px">Window</span>는 **전역 객체**이면서, 모든 객체가 소속된 **객체**(최상위 객체?)<br>
Document, navigator, object 등은 window의 Property이면서 각각 객체로서 역할을 한다
<br>

object model 출처: [tistory1](https://chrismare.tistory.com/28), &nbsp; [tistory2](https://bravesuccess.tistory.com/25), &nbsp; [youtube](https://www.youtube.com/watch?v=bJg4ywnaZ6Q&t=26s)<br>

<br>

## Window 

### 전역 객체

```html
<!DOCTYPE html>
<html>
<script>
    a = 1;    # window 객체의 property, 전역변수, 함수에 소속되지 않은 변수 
    var b = 2;
    alert('Hello world');        # window 객체의 메소드
    window.alert('Hello world');
</script>
<body>

</body>
</html>
```

<br>

## Document

> Document 객체는 웹 페이지 그 자체를 의미 <br>
> 웹 페이지에 존재하는 HTML요소에 접근하고자 할 때는 DOM으로 만들어야 한다


![document](https://user-images.githubusercontent.com/33630505/61169326-dba1c400-a596-11e9-8093-10a90bd40aac.JPG)
<br>

### Document 메소드 

```
1. HTML 요소 선택 
2. HTML 요소 생성 
3. HTML 이벤트 핸들러 추가 
4. HTML 객체 선택 
```

<br>

#### HTML 요소 선택

![select](https://user-images.githubusercontent.com/33630505/61169268-2f5fdd80-a596-11e9-81cb-19fa54990bbb.JPG)
<br>

#### HTML 요소 생성

![create](https://user-images.githubusercontent.com/33630505/61169273-3be43600-a596-11e9-949a-e016cd992c9d.JPG)
<br>

#### HTML 이벤트 핸들러 추가 

![handler](https://user-images.githubusercontent.com/33630505/61169274-3be43600-a596-11e9-9a60-dca3e5084fe5.JPG)
<br>

#### HTML 객체 선택 

![objectselect](https://user-images.githubusercontent.com/33630505/61169275-3c7ccc80-a596-11e9-8822-2758a0d1db71.JPG)
<br>


사진 출처: [tcpschool](http://tcpschool.com/javascript/js_dom_document)<br>



## Property vs Attribute vs Variable

### 자바스크립트에서 Property와 Variable 

```
Property : 인스턴스로부터 만들어진 변수, 인스턴스에 종속된 변수 

Variable : 인스턴스와 상관없이 만들어진 변수 
```

### 예제로 알아보자 

```html 
<script type="text/javascript">
      var setMyName = function(value){
        this.name = value;
      }
      var setMyName2 = function(value){
        var name = value;
      }

      var setName = new setMyName("jihyuk");  # setName 인스턴스
      var setName2 = new setMyName2("jihyuk2"); # setName2 인스턴스

      console.log(setName);         # Property를 포함함한 객체 
      console.log(typeof(setName)); # setName 인스턴스는 object를 반환한다

      console.log(setName.name);         # Property 값 출력
      console.log(typeof(setName.name)); 

      console.log(setName2);          # Property를 포함하지 않은 객체
      console.log(typeof(setName2));  

      console.log(setName2.name);         # Property가 없다
      console.log(typeof(setName2.name));
</script>
```

![consolelog](https://user-images.githubusercontent.com/33630505/61168413-e05f7b80-a588-11e9-8669-46914714457f.JPG)
<br>
<br>

### Html과 Dom에서 Attribute와 Property 

```
Attribute: HTML관점에서 선택자 

Property: DOM관점에서 선택자 
```

<br>

### 예제로 알아보자 

```html
# HTML 관점 
<div class="name">ji hyuk</div>

# 태그 div는 Element 
# class는 attribute 
# name은 값 
# ji hyuk은 data 

# DOM 관점 

# 태그 div는 Element 
# class는 property 
# name은 값 
# ji hyuk은 data 
```


<hr>

Attribute vs Property: [Medium](https://medium.com/hexlant/attribute-%EC%99%80-property-%EC%9D%98-%EC%B0%A8%EC%9D%B4-c6f1c91ba91)<br>
Variable vs Property: [blog](http://blog.kazikai.net/?p=18)<br>

<br>

# DOM 

> Document Object Model의 약자로 객체 지향 모델로써 구조화된 문서를 표현하는 형식이다. <br>
> Html, xml 같은 문서를 객체형태로 바꾸어 객체로써 이용하기 위한 형태이다. <br>
> DOM은 플랫폼/언어 중립적으로 구조화된 문서를 표현하는 W3C의 공식 표준이기 때문에 문서를 객체로써 쓴다면 DOM 형식을 사용해야한다. <br>
> DOM은 HTML문서의 모든 요소에 접근하는 방법을 정의한 API이기도 하다.<br>
> DOM은 넓은 의미로 웹 브라우저가 HTML 페이지를 인식하는 방식으로 볼 수 있고<br>
> 좁은 의미로는 document 객체와 관련된 객체의 집합으로 볼 수 있다.


## 등장 배경 

```
DOM은 HTML 문서의 요소를 제어하기 위해 웹 브라우저에서 처음 지원되었다.  
브라우저가 다양해지면서 브라우저 사이에 DOM 구현이 호환되지 않음에 따라, 
W3C에서 DOM 표준 규격을 작성하게 되었다.
```




DOM 출처: [tistory](https://na27.tistory.com/228), &nbsp; [wiki](https://ko.wikipedia.org/wiki/%EB%AC%B8%EC%84%9C_%EA%B0%9D%EC%B2%B4_%EB%AA%A8%EB%8D%B8)<br>
