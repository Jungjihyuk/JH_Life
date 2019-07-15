---
layout: post 
title: Data Collection
excerpt: 'Data mining, crawling, scraping'
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

<br>


## Data from Portal site(Web Data) 

> Web으로부터 데이터를 수집하겠다고 마음 먹은 순간 해야할 작업들이 많다 

<br>
<hr>

<span style="color: skyblue; font-size: 20px">데이터를 가져오려면 Web page 구성을 알아야 한다!</span><br>

> HTML, SS, JavaScript등 웹 페이지 구성이 어떻게 되는지 공부해야 한다

<span style="color: orange">잘 모른다면 참고하자 =></span> [Object Model](https://jungjihyuk.github.io/JH_Life/objectModel/)<br>

<br>

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

[Crawling 공부하러가기](#crawling)

<br>

<span style="color: skyblue; font-size: 20px">유용한 page url을 알아 냈으니 내가 원하는 data를 수집하자</span><br>

> scraping

[Scraping 공부하러가기](#scraping)

<br> 
<hr>


## Data mining 


Data mining 출처: [incodom](http://www.incodom.kr/Data_mining_%EC%A0%95%EC%9D%98#h_9e737f73b091295d98128515d2729bbb)<br>

<a id = 'crawling'></a>
## Crawling 

### BFS Crawling 

> google 박보영 검색 결과 crawling 

<br>

```python
headers = {"user-agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/75.0.3770.100 Safari/537.36"}  # 브라우저에서 직접 request보내는 것처럼 흉내내기 위한 header 초기화 

import time, requests
from bs4 import BeautifulSoup 

def download(method, url, param=None, data=None, timeout=1, maxretries=3, headers = headers):
    try:
        resp = requests.request(method, url, params = param, data =  data, headers = headers)  # request요청에 대한 response
        resp.raise_for_status() # 에러 강제하기
    except requests.exceptions.HTTPError as e:    # 에러 처리 
        if (500 <= e.response.status_code < 600 and maxretries >0): 
            print(maxretries)
            time.sleep(timeout)
            resp=download3(method, url, param, data, timeout, maxretries-1)
        else:          
            print(e.response.status_code)
            print(e.response.reason)
    return resp


def parseURL(seed):      # download함수와 BeautifulSoup을 이용해 URL parsing 하는 함수 
    html = download("get", seed)
    dom = BeautifulSoup(html.text, 'lxml')
    
    return [requests.compat.urljoin(seed, _["href"]) for _ in dom.find_all("a")  if _.has_attr("href") and len(_["href"]) > 3]


url = "https://www.google.com/search"
html = download("get", url, param = {"q":"박보영"})
dom = BeautifulSoup(html.text, 'lxml')

queue = list()
queue.extend([_.find_parent()['href'] for _ in dom.select(".LC20lb")]) # 초기 seed값 추가 
seen = list()

while queue:
    baseURL = queue.pop(0)   # queue는 선입 선출 방식이기 때문에 index 가장 앞 0을 꺼낸다 
    seen.append(baseURL)   # 한번 꺼낸 url은 재방문 하지 않도록 seen list에 추가 
    
    time.sleep(5)    # 빈번한 request로 block 당하는 일 방지하기 위해 시간 끌기 
    
    linkList = parseURL(baseURL)  # parsing한 url list에 추가 
    for link in linkList:  # 추가된 url을 하나씩 뽑아 queue에 없거나 seen에 없으면 queue에 추가한다 
        if link not in queue and link not in seen:
            queue.append(link)
    
    print("Queue: {0}, Seen: {1}".format(len(queue), len(seen)))

:
Queue: 862, Seen: 1
Queue: 1291, Seen: 2
Queue: 2259, Seen: 3
Queue: 2381, Seen: 4
Queue: 2416, Seen: 5
Queue: 2426, Seen: 6
.....
.....
```


### DFS Crawling(Focused Crawling)

> naver에 박보영 검색 후 블로그 url parsing 

<br>

```python
import requests, download

def checkBlog(url):
    return requests.compat.urlparse(url)[1] == "blog.naver.com"
    
def parseURL(seed):
    html = download.download("get", seed)
    dom = download.BeautifulSoup(html.text, 'lxml')
    
    if len(dom.select("#mainFrame")) < 1:
        return []
        
    seed = requests.compat.urljoin(seed, dom.select("#mainFrame")[0]["src"])
    
    html = download.download("get", seed)
    dom = download.BeautifulSoup(html.text, 'lxml')

#     print(requests.compat.urljoin(seed, dom.select("#mainFrame")[0]['src']))
    
    return [requests.compat.urljoin(seed, _["href"]) for _ in dom.find_all("a")  if _.has_attr("href") 
            and len(_["href"]) > 3 and checkBlog(requests.compat.urljoin(seed, _['href']))]
            
url = "https://search.naver.com/search.naver"
html = download.download("get", url, param = {"query":"박보영"})
dom = download.BeautifulSoup(html.text, 'lxml')

queue = list()
queue.extend([_['href'] for _ in dom.select("a.sh_blog_title._sp_each_url._sp_each_title") if checkBlog(_['href'])])
seen = list()

while queue:
    baseURL = queue.pop(0)
    seen.append(baseURL)
    
    download.time.sleep(0.5)
    
    linkList = parseURL(baseURL)
    for link in linkList:
        if link not in queue and link not in seen:
            queue.append(link)
    
    print("Queue: {0}, Seen: {1}".format(len(queue), len(seen)))
    
:
Queue: 17, Seen: 1
Queue: 32, Seen: 2
Queue: 48, Seen: 3
Queue: 47, Seen: 4
Queue: 46, Seen: 5
Queue: 45, Seen: 6
Queue: 44, Seen: 7
Queue: 43, Seen: 8
....
....
```

![sequence](https://user-images.githubusercontent.com/33630505/61232836-2de70e80-a76a-11e9-8bad-b48671cc0f5e.JPG)
![table1](https://user-images.githubusercontent.com/33630505/61232837-2de70e80-a76a-11e9-8571-9d2fcf5d90a9.JPG)
![table2](https://user-images.githubusercontent.com/33630505/61232839-2e7fa500-a76a-11e9-8224-bfdb39180664.JPG)


crawling 출처: [prowebscraping](http://prowebscraping.com/web-scraping-vs-web-crawling/) &nbsp; [quora](https://www.quora.com/What-the-difference-between-crawling-website-and-counting-link-in-website) &nbsp; [tistory](https://twoearth.tistory.com/19) <br>
논문: [RCrawler: An R package for parallel web crawling and scraping -Salim Khalil, Mohamed Fakir]  <br>


<br>

### Crawling 한 url DB에 저장하기 

```
```

<a id = "scraping"></a>
## Scraping 


<br>

## Page Rank 




