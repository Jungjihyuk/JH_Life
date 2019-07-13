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

<br>
<hr>

# XML 

## XML 이란? 

> Extensible Markup Language의 약자로 W3C에서 개발된 다목적 마크업 언어이다. <br>
> XML은 데이터를 전달하고 저장하는 목적으로 만들어졌다. <br>

<br>

## XML 등장 배경 

```
정부나 항공우주 기업의 대규모 계획 사업에서 기계 판독형 문서를 공유할 목적으로 
SGML(Standard Generalized Markup Language)라는 마크업 언어가 있었는데, 
사용하기에 너무 복잡하고 HTML의 한계를 극복하기 위해 XML이 탄생했다. 
```

<br>

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

<br>

## HTML vs XML 

**HTML은 데이터를 표현하는 것에 초점을 두고 XML은 데이터를 구조화 하고 전달하는 것에 초점이 맞춰저 있다.**


<br>

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
9. XML Schema 
- namespaces, data types 지원 
- XML 문법 준수 
```

![xml](https://user-images.githubusercontent.com/33630505/60965241-51681e80-a350-11e9-8b7b-ac25b974d4a3.JPG)

<br>

### XML Schema 

```html 
<?xml version="1.0"?>

<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
<xs:element name="note">
   <xs:complexType>
      <xs:sequence>
         <xs:element name="to" type="xs:string"/>
         <xs:element name="to" type="xs:string"/>
         <xs:element name="to" type="xs:string"/>
      </xs:sequence>
   <xs:complexType>
</xs:element>
</xs:schema>     
<!-- xs는 namespace -->   
```

<br>

### XML Tree

![xmltree](https://user-images.githubusercontent.com/33630505/60965240-51681e80-a350-11e9-8555-bc1646001a49.png)

## XML vs LXML

### LXML

> XML보다 속도가 빠르고 자주 쓰는 방법

<br>

#### 예제 

```python
from lxml import etree

bookStore = etree.Element("bookstore") 

book1 = etree.SubElement(bookStore, "book")
book2 = etree.SubElement(bookStore, "book", attrib={"category":"children"})

book1.attrib["category"] = "cooking"

title1 = etree.Element("title", lang="en")
title1.text = "Everyday Italian"
book1.append(title1)

etree.SubElement(book1, "author").text = "Giada De Lausadlf"
etree.SubElement(book1, "year").text = "2003"
etree.SubElement(book1, "price").text = "40.3"

title2 = etree.Element("title")
title2.set("lang", title1.get("lang"))
title2.text = "Harry Potter"
book2.append(title2)

etree.SubElement(book2, "author").text = "Giada De Lausadlf"
etree.SubElement(book2, "year").text = "2003"
etree.SubElement(book2, "price").text = "40.3"

xmlBytes = etree.tostring(bookStore, encoding="UTF-8", pretty_print=True, xml_declaration=True)
xmlstr = etree.tounicode(bookStore, pretty_print=True)

etree.dump(bookStore)
:
<bookstore>
  <book category="cooking">
    <title lang="en">Everyday Italian</title>
    <author>Giada De Lausadlf</author>
    <year>2003</year>
    <price>40.3</price>
  </book>
  <book category="children">
    <title lang="en">Harry Potter</title>
    <author>Giada De Lausadlf</author>
    <year>2003</year>
    <price>40.3</price>
  </book>
</bookstore>

xmlRoot = xmlTree.getroot()
for childNode in xmlRoot:
    print(childNode.tag, childNode.attrib)
:
book {'category': 'cooking'}
book {'category': 'children'}
```

#### 예제 (Write, Parse)

```python
# bookStore는 위 예제와 동일 
xml = etree.XML(etree.tostring(bookStore))
xmlTree = etree.ElementTree(xml)
xmlRoot = xmlTree.getroot()

# xmlTree book_tree, book_root 이름의 xml 파일을 생성한다
xmlTree.write("book_tree.xml")
etree.ElementTree(xmlRoot).write("book_root.xml")

getxmlTree = etree.parse("book_tree.xml")
xmlRoot = getxmlTree.getroot()

etree.dump(xmlRoot)
:
<bookstore>
  <book category="cooking">
    <title lang="en">Everyday Italian</title>
    <author>Giada De Lausadlf</author>
    <year>2003</year>
    <price>40.3</price>
  </book>
  <book category="children">
    <title lang="en">Harry Potter</title>
    <author>Giada De Lausadlf</author>
    <year>2003</year>
    <price>40.3</price>
  </book>
</bookstore>
```

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

<br>
<hr>

# JSON 

## JSON 이란?

> JavaScript Object Notation의 약자

<br>

## JSON 등장 

> XML의 대안으로서 좀 더 쉽게 데이터를 교환하고 저장하기 위해 고안되었다. <br>
> XML보다 가볍고 사용하기 편하다.

<br>

## 왜 json을 쓰는가? 



<br>

## JSON의 특징 

### 장점 

```
1. javascript 객체 표기법을 따른다
2. 사람과 기계 모두 읽기 편하다 
- XML보다 가독성이 뛰어나다
3. 프로그래밍 언어와 운영체제에 독립적이다
- 언어에 관계없이 통일된 데이터를 주고받을 수 있다
4. 가볍다
- XML보다 메모리가 효율적이다
```

### 단점 

```
1. 문법 오류에 민감하다 
- 콤마가 누락되거나 중괄호가 잘못 닫히는 등 구두점에서 오타가 나면 전체 JSON 파일이 망가진다
2. 주석을 지원하지 않는다
3. 데이터 타입을 강제할 수 없다 (JSON Schema로 보완은 가능하지만 데이터 스스로 타입을 기술할 수 없다)
```

<br>

## XML vs JSON 

```
1. JSON은 종료 태그를 사용하지 않는다
2. JSON의 구문은 XML 구문보다 짧다
3. XML은 배열을 사용할 수 없지만, JSON은 배열을 사용할 수 있다
4. XML은 XML 파서로 파싱되며, JSON은 자바스크립트 표준 함수인 eval() 함수로 파싱된다
5. XML 문서는 XML DOM을 이용하여 문서에 접근하지만 JSON은 문자열을 전송 받은 후에 
   해당 문자열을 바로 파싱하므로, XML보다 더 빠른 처리 속도를 보여준다
6. JSON은 전송받은 데이터의 무결성을 사용자가 직접 검증해야 하지만 XML은 
   스키마를 사용하여 무결성을 검증할 수 있다(JSON Schema로 보완 가능하긴 함)
```

출처: [tcpschool](http://tcpschool.com/json/json_intro_xml)<br>

<br>

## JSON 구성 요소 

```
1. 데이터는 이름과 값의 쌍으로 이루어진다
2. Array (대괄호 [])
3. Object (중괄호 {}) 
```

![jsonstructure](https://user-images.githubusercontent.com/33630505/60967707-444e2e00-a356-11e9-968d-dc80f8e9ecb3.JPG)

<br>

## 데이터 타입 

```
1. Number
2. String
3. Boolean
4. Object
5. Array
6. Null 
```

![datatype](https://user-images.githubusercontent.com/33630505/60967709-444e2e00-a356-11e9-9fc4-c7d6bd34f645.JPG)

<br>

## Stringify & Parse

> Stringify는 JSON파일을 Serialize하고 Parse는 Deserialize한다 <br>
> Stringify는 json객체를 string객체로 변환하고 parse는 string객체를 json 객체로 변환한다

### 예시
```html 
<html>
<head></head>
<body>
<script>
    var obj = {name: "jh", "age": 25, "car": true};
    objstr = JSON.stringify(obj, function(k,v){if(v===23)return;else return v;});
    console.log("obj: ",obj);
    console.log("objstr1", objstr);
    objstr = JSON.stringify(obj, null, 10/* ' ', '\t' */);
    console.log("objstr2", objstr);

    objbyte = JSON.parse(objstr);
    console.log("objbyte",objbyte);
</script>
</body>
</html>
```

![jsonjavascript](https://user-images.githubusercontent.com/33630505/60969067-93e22900-a359-11e9-839f-f3e3b9af7a43.JPG)

<br>

## Open API JSON형태로 불러오기 

```python
import json, urllib

url = 'http://openapi.airkorea.or.kr/openapi/services/rest/ArpltnInforInqireSvc/getCtprvnRltmMesureDnsty'

params = {
    "serviceKey": "rHPpLuWO16wWq7c2Z87Q8gwiZ7z6agbTuwvSDBpCEC7dqDXusPHYkC%2FVMq029DVkRJegegKOoUETTvYa82Dc2Q%3D%3D",
    "numOfRows": 10,
    "pageNo": 1,
    "startPage": 1,
    "sidoName": "인천",
    "dataTerm": "DAILY",
    "ver":"1.3",
    "_returnType": "JSON"
}

params["serviceKey"] = urllib.parse.unquote(params["serviceKey"])
params = urllib.parse.urlencode(params)
params = params.encode("UTF-8")
req = urllib.request.Request(url, data=params)
res = urllib.request.urlopen(req)
resStr = res.read()
resStr = resStr.decode("UTF-8")
resObj = json.loads(resStr)
resJSON = json.dumps(resObj, indent="  ")

x = resObj['list']
for i in x:
    print(i['stationName'], i['pm25Value'])

: 
신흥 9
송림 9
구월동 2
숭의 10
석바위 31
부평역 20
부평 5
연희 -
검단 7
계산 8
```

## JSON Schema



