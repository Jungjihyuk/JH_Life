---
layout: post 
title: Data Collection
exceprt: 'Data mining, crawling, scraping'
date: 2019-07-15
tag:
- data mining
- crawling
- scraping
- page rank
---


# Data Collection 

> 데이터 수집은 왜 하는 걸까?? 


```
4차 산업혁명 시대를 사는 현대인들 중 Big Data에 관한 존재를 모르는 사람은 없을 것이다
Big Data는 방대한 데이터고 그 많은 데이터로 뭐 어떻게 해보려는 시도가 있다는 건 알겠는데 
도대체 그 Big Data라는 것으로 뭘 하는 걸까? 

마냥 많은 데이터라는 것에서 그쳤으면 Big Data가 이슈가 되지 않았을 것이다 
Big Data라는 엄청난 데이터 속에서 사람의 인지 능력으로는 분석하기 힘든 양을 
한꺼번에 컴퓨터라는 도구로 분석을 해보니 사람보다 연산도 빠르고 분석 성능이 좋았던 것이다 

따라서 Big Data(Data warehouse)를 수집해서 숨겨진 의미 있는 정보를 추출하고
문제를 해결하는 것이 화두가 된 것이다 
```

<br>

## Data 수집 종류 

```
1. 공공데이터(api, file)
2. Portal site ( ex) google, naver, daum..)
3. 그 외 Files
```

> 공공 데이터 api나 file 그리고 dataset(file)은 데이터를 수집하는 절차가 복잡하거나 수집해서 <br>
> 처리하는 작업이 번거롭거나 힘들지 않다 <br>
> 그런데 Portal site에서 데이터를 수집하기 위해서는 제법 까다로운 작업이 필요하다 



## Data from Portal site(Web Data) 

> Web으로부터 데이터를 수집하겠다고 마음 먹은 순간 해야할 작업들이 많다 


<span style="color: skyblue; font-size: 20px">데이터를 가져오려면 Web page 구성을 알아야 한다!</span><br>

> HTML, CSS, JavaScript등 웹 페이지 구성이 어떻게 되는지 공부해야 한다

<span style="color: orange">잘 모른다면 참고하자 =></span> [Object Model](https://jungjihyuk.github.io/JH_Life/objectModel/)<br>


<span style="color: skyblue; font-size: 20px">웹 문서 중 어디서부터 어디까지 찾을 껀데? 수집 범위는 정했니?</span><br>

> 지금부터는 Crawling 기법으로 Hyperlink fetch를 반복해서 페이지 사이 link 구조를 알아내야 한다 <br>
> 그 다음 depth를 설정해서 어디까지 crawling 할 것인가를 정하고 focused crawling으로 crawling하는 페이지를 <br>
> 한정 할 것인지 아니면 페이지를 넘나들며 끊임없이 확장할 것인지도 정해야 한다 (목적에 맞게) <br>
> 이러한 경우를 DFS(Depth First Search)와 BFS(Breadth First Search)라고 한다 <br>

<br>

<span style="color: skyblue; font-size: 20px">Crawling해서 많은 url은 확보 했는데 어떤 url에 유용한 정보가 있는지 아니?</span><br>

> url만으로 정보의 유용성을 판단할 수는 없다 <br>
> 따라서 crawling 해서 database에 저장할때 page rank 개념을 활용하여 저장하는 것이 효율적이다 <br>
> page rank개념은 페이지 참조횟수가 많으면 그만큼 영향력 있고, 가치가 있는 데이터를 포함한 페이지라 간주한다 <br> 
> 결국 page rank가 높은 순으로 url을 분류하고 그 url로 부터 data를 수집 하면 된다 

<span style="color: rgb(180, 75, 92); font-size: 15px;">단, page rank가 높다고 나한테 필요한 데이터라는 보장은 없다.</span><br>
<span style="color: rgb(180, 75, 92); font-size: 15px;">그래서 데이터 추출후 전처리, 패턴 분석 등 여러가지 처리 후 데이터를 사용해야 한다.</span><br>


<br>

<span style="color: skyblue; font-size: 20px">유용한 page url을 알아 냈으니 내가 원하는 data를 수집하자</span><br>

> 

## Data mining 


## Crawling 


## Scraping 


## Page Rank 





