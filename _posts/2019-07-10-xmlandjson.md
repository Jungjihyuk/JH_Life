---
layout: post 
title: XML & JSON 
excerpt: "XML과 JSON에 대한 이해 그리고 오픈 api 불러오기"
date: 2019-07-10
tag:
- xml
- json
- api
---

# Markup Language 

> 태그 등을 이용하여 문서나 데이터의 구조를 명기하는 언어의 한가지 이다. <br>


```
마크업 언어를 사용하여 데이터를 기술하면 
컴퓨터도 이해하고 사람도 이해할 수 있는 방식으로 문서를 정의하고 데이터를 구조화 할 수 있다.
데이터를 문서화, 구조화 할 뿐만아니라 그 문서를 컴퓨터 화면에 보여줄 수도 있다.
```


# XML 

## XML 이란? 

> Extensible Markup Language의 약자로 W3C에서 개발된 다목적 마크업 언어이다. <br>
> XML은 데이터를 전달하고 저장하는 목적으로 만들어졌다. <br>

## XML 등장 배경 

```
정부나 항공우주 기업의 대규모 계획 사업에서 기계 판독형 문서를 공유할 목적으로 SGML(Standard Generalized Markup Language)라는 마크업 언어가 있었는데, 사용하기에 너무 복잡하고 HTML의 한계를 극복하기 위해 XML이 탄생했다. 
```

## XML의 특징 

```
1. 데이터의 표현이 자유롭다 
- XML은 데이터에 의미를 부여하는 메타데이터를 기술 할 수 있다
2. 데이터의 확장성이 뛰어나다
3. 유효성 체크를 한다는 점이 엄청난 장점이다. 
- Valid XML과 Well formed XML는 서로 다르다
- ex) <?xml ~>으로 시작하면 XML문서로서 가능하지만 가능하다고 해서 
- 모두 well formed xml은 아닐 수 있다 (well formed 조건에 부합하지 않는 것이 하나라도 있을때)
4. 텍스트(Unicode) 기반으로 작성되어 읽기 쉽다
5. Well-formed Documents
- root element를 가져야한다
- closing tag가 있어야 한다
- tag는 대소문자에 민감하다 
- ex) <body>body</Body> (X) <body>body</body> (O)
- tag는 적절하게 감싸야 한다 
- ex) html에서는 tag의 시작점과 끝점이 명확하지 않아도 상관없지만 
- xml은 정확하게 명시해야 한다. <b><i>Hello</b></i> => HTML에서는 가능 , XML에서는 불가능
- attribute 값은 쌍 따옴표로 감싸야 한다
- ex) <note date= 19/7/10></note> (X) <note date= "19/7/10"></note> (O) 
```

## HTML vs XML 

**HTML은 데이터를 표현하는 것에 초점을 두고 XML은 데이터를 구조화 하고 전달하는 것에 초점이 맞춰저 있다.**


## XML 구성 요소 

```
1. XML declaration
2. DTD(Document type declaration) 
- DTD를 사용하면 어떤 문서의 종류인지 확인이 가능하고 
- 해당 문서의 규칙을 따를 수 있도록 유효성 검사를 작동하게 된다. 
3. Root Element start tag, end tag
4. Comment
5. Elements 
6. Characters
7. Attributes
8. Entity 
```

![xml](https://user-images.githubusercontent.com/33630505/60965241-51681e80-a350-11e9-8b7b-ac25b974d4a3.JPG)

### XML Tree

![xmltree](https://user-images.githubusercontent.com/33630505/60965240-51681e80-a350-11e9-8555-bc1646001a49.png)

