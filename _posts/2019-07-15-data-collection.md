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

### Crawling부터 DB 저장까지 Flow 

```
Data 수집원 OK? ⇒ Dynamic HTML  ⇒  Focused?   ⇒ Selenium + Crawling + url check ⇒ Scraping  => DB
                                      BFS?     ⇒ Selenium + Crawling ⇒ Scraping ⇒ DB 
                      HTML      ⇒  Focused?   ⇒ Crawling + url check ⇒ Scraping ⇒ DB 
                                      BFS?     ⇒ Crawling ⇒ Scraping ⇒ DB 
```

<span style="color: skyblue; font-size: 20px">데이터를 가져오려면 Web page 구성을 알아야 한다!</span><br>

> HTML, CSS, JavaScript등 웹 페이지 구성이 어떻게 되는지 공부해야 한다 <br>
> 사이트 마다 웹 페이지 구성이 다르기 때문에 웹에 대한 이해 없이 무작정 하면 <br>
> 데이터 수집이 안되는 경우를 발견하게 될 것이다 <br> 

![lifecycle](https://user-images.githubusercontent.com/33630505/61360601-ba541700-a8b9-11e9-9031-d4271168bf10.JPG)

```
어떠한 웹 페이지는 요청한 부분만 동적으로 페이지 리로딩 없이 데이터를 가져 와서 
request url을 확인하기 어려운 경우가 있다. 

위 그림에 SPA Lifecycle이 그러한 경우 인데, 
사용자가 직접 클릭을 해야만 데이터를 확인 할 수 페이지라면 
처음에 요청했던 페이지에는 포함되어 있지 않고 클릭 한 순간 
dom객체가 추가 되기 때문에 실시간으로 개발자 도구에서 network 부분을 살피지 않는다면 
절대 숨겨진 데이터를 가져올 수 없을 것이다. 

따라서 어떠한 웹 페이지 인지에 따라 셀레늄같은 automation framework를 사용할지 말지 결정해야 한다.
```

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

<br>

## Crawling vs Scraping 


![crawlerandscraping](https://user-images.githubusercontent.com/33630505/61361477-8548c400-a8bb-11e9-9b09-7b1804aaf054.JPG)

사진출처: [prowebscraping](http://prowebscraping.com/web-scraping-vs-web-crawling/)<br>

<br>

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

crawling 출처: [prowebscraping](http://prowebscraping.com/web-scraping-vs-web-crawling/) &nbsp; [quora](https://www.quora.com/What-the-difference-between-crawling-website-and-counting-link-in-website) &nbsp; [tistory](https://twoearth.tistory.com/19) <br>
논문: [RCrawler: An R package for parallel web crawling and scraping -Salim Khalil, Mohamed Fakir]  <br>


<br>

### Crawling 한 url DB에 저장하기 

```python 
import sqlite3, requests, download

con = sqlite3.connect("bot.db")
cur = con.cursor()

cur.executescript('''
    DROP TABLE IF EXISTS table1;
    CREATE TABLE table1(
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        table2_id INTEGER NOT NULL,
        path TEXT NOT NULL,
        param TEXT,
        depth INTEGER NOT NULL,
        inbound INTEGER NOT NULL, 
        seen BOOLEAN DEFAULT FALSE NOT NULL,
        date TIMESTAMP DEFAUlT CURRENT_TIMESTAMP NOT NULL
    );
    DROP TABLE IF EXISTS table2;
    CREATE TABLE table2(
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        netloc TEXT NOT NULL,
        date TIMESTAMP DEFAULT CURRENT_TIMESTAMP NOT NULL
    );
'''
)

url = "https://www.google.com/search"
html = download.download("get", url, param = {"q": "박보영"})
dom = download.BeautifulSoup(html.text, "lxml")

def parseURL(seed):
    html = download.download("get", seed)
    dom = download.BeautifulSoup(html.text, 'lxml')

    return [requests.compat.urljoin(seed, _["href"]) for _ in dom.find_all("a")  if _.has_attr("href") 
            and len(_["href"]) > 3]
            

for href in [_.find_parent()["href"]
             for _ in dom.select(".LC20lb")]:
    _urlparse = requests.compat.urlparse(href)
    netloc = "://".join(_urlparse[:2])
    cur.execute("SELECT id FROM table2 WHERE netloc=? LIMIT 0,1", [netloc]) #netloc을 시퀀스로 만들어서 넘겨줘야함
    
    netlocID = cur.fetchone()
    if not netlocID:
        cur.execute("INSERT INTO table2(netloc) VALUES(?)", [netloc])
        
        con.commit()
        
        cur.execute("SELECT id FROM table2 WHERE netloc=? LIMIT 0,1", [netloc]) 
        
        netlocID = cur.fetchone()
    
    cur.execute("INSERT INTO table1(table2_id, path, param, depth, inbound) VALUES(?, ?, ?, ?, ?)",[netlocID[0], _urlparse[2], _urlparse[4], 1, 0])
    con.commit()
    print(cur.lastrowid, netlocID)

i = 0
while True: 
    cur.execute('''
        SELECT table1.id, table2.netloc, table1.path, table1.param, table1.depth, table2.id
        FROM table1
        JOIN table2
            ON table1.table2_id=table2.id
        WHERE table1.seen = FALSE and table1.depth < 3
        ORDER BY table1.date ASC
        LIMIT 0, 1;
    ''')
    seed = cur.fetchone()
    if not seed or i > 1000:
        break
    i += 1 
    
    cur .execute('''
        UPDATE table1
        SET seen = TRUE 
        WHERE id = ? 
    ''', [seed[0]])
    con.commit()

    baseURL= "{0}{1}?{2}".format(seed[1],seed[2],seed[3])
    for url in parseURL(baseURL):
        for href in [_.find_parent()["href"] for _ in dom.select(".LC20lb")]:
            _urlparse = requests.compat.urlparse(href)
            netloc = "://".join(_urlparse[:2])
            cur.execute("SELECT id FROM table2 WHERE netloc=? LIMIT 0,1", [netloc]) #netloc을 시퀀스로 만들어서 넘겨줘야함

            netlocID = cur.fetchone()
            if not netlocID:
                cur.execute("INSERT INTO table2(netloc) VALUES(?)", [netloc])

                con.commit()

                cur.execute("SELECT id FROM table2 WHERE netloc=? LIMIT 0,1", [netloc]) 

                netlocID = cur.fetchone()
    
            cur.execute("INSERT INTO table1(table2_id, path, param, depth, inbound) VALUES(?, ?, ?, ?, ?)",[netlocID[0], _urlparse[2], _urlparse[4], seed[4]+1, seed[5]])
            con.commit()
        
#     break
```


![sequence](https://user-images.githubusercontent.com/33630505/61233463-95ea2480-a76b-11e9-9fc1-c8a5e1ff520a.JPG)
![table1](https://user-images.githubusercontent.com/33630505/61232837-2de70e80-a76a-11e9-8571-9d2fcf5d90a9.JPG)
![table2](https://user-images.githubusercontent.com/33630505/61232839-2e7fa500-a76a-11e9-8224-bfdb39180664.JPG)


<a id = "scraping"></a>
## Scraping 

> Crawling한 url로 부터 내가 원하는 데이터를 수집하는 것을 말한다

<br>

### Naver news 본문 scraping 예제 (Dynamic HTML X)

```
from selenium import webdriver
from bs4 import BeautifulSoup
import download

driver = webdriver.Chrome("크롬드라이버 경로")
driver.get("https://news.naver.com/")

dom = BeautifulSoup(driver.page_source, 'lxml')
# crawling으로 url 확보 했다고 가정 
urls=[x['href'] for x in dom.select("#main_content a") if len(x['href']) > 7 and 'read' in x['href']][7:]

def parseContent(url):   # crawling한 url을 인자로 전달하면 제목, 본문내용 parsing
    html = download.download("get", url)
    dom = download.BeautifulSoup(html.text, 'lxml')
    
    return {"title": dom.select_one("#articleTitle").text.strip(), 
            "body": dom.select_one("#articleBodyContents").text.strip()
           }

contents = list()
while urls:                # urls안에 있는 url이 없을때 까지 계속 parsing 
    baseURL = urls.pop(0) 
    contents.append(parseContent(baseURL))        

import sqlite3
con = sqlite3.connect("news.db")
cur = con.cursor()

cur.execute("""
    CREATE TABLE news(
        title TEXT NOT NULL,
        content TEXT NOT NULL
    );
""")

while contents:     # parsing한 data DB에 저장하기 
    content=contents.pop(0)
    cur.execute("""
        INSERT INTO news
        (title, content)
        VALUES(?, ?)
    """, [content['title'], content['body']])
    con.commit()
```

<br>


## Page Rank 



Page Rank 참고: [sungmooncho](https://sungmooncho.com/2012/08/26/pagerank/)<br>


## Selenium 

> Web Browser Automation 

**단점** page rendering중에 scraping 시도를 하면 
{: .notice}

<br>

### Dynamic HTML Scraping 예제 

```python 
from selenium import webdriver 

driver = webdriver.Chrome("chromedriver.exe 경로")  # driver를 생성하면 chrome 브라우저 창 생성 

def html_parser(url):
    driver.get(url)
    
    time.sleep(1)
    
    html = driver.page_source
    dom = BeautifulSoup(html, 'lxml')
    
    resp=dom.select('#main')
    return resp
    
def search(url, country):
    driver.get(url)
    inputTag = driver.find_element_by_css_selector("#search_term")
    inputTag.send_keys(country)
    driver.find_element_by_css_selector("#search").click()
    
    time.sleep(1)
    
    html = driver.page_source
    dom = BeautifulSoup(html, 'lxml')
        
    return [requests.compat.urljoin(url, _['href']) for _ in dom.select("#results a")]
    
    
nation = search("http://example.webscraping.com/places/default/search", "korea")

result = []
while nation:
    baseURL = nation.pop(0)
    
    dom=html_parser(baseURL)
    result.append(dom[0].text)

for x in result:
    print(x)


:
National Flag: Area: 120,540 square kilometresPopulation: 22,912,177Iso: KPCountry: North KoreaCapital: PyongyangContinent: ASTld: .kpCurrency Code: KPWCurrency Name: WonPhone: 850Postal Code Format: ###-###Postal Code Regex: ^(\d{6})$Languages: ko-KPNeighbours: CN KR RU 
Edit


National Flag: Area: 98,480 square kilometresPopulation: 48,422,644Iso: KRCountry: South KoreaCapital: SeoulContinent: ASTld: .krCurrency Code: KRWCurrency Name: WonPhone: 82Postal Code Format: SEOUL ###-###Postal Code Regex: ^(?:SEOUL)*(\d{6})$Languages: ko-KR,enNeighbours: KP 
Edit

driver.close() # 브라우저 창 닫기 
```
