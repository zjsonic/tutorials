[TOC]

# HTTP

- HTTP protocol for communication between client and server.
- HTTP meams **Hyper Text Transfer Protocol** .
- HTTP is the underlying protocol used by the World Wide Web.
- HTTP defines:
  + How messages are formatted.
  + How messages are transmitted.
  + What actions the server should take in response to various commands.
  + What actions the client should take in response to various commands.

Various Commands:

- When you enter a URL in your browser, this actually sends an HTTP command to the Server directing it to fetch and transmit the request web page.

## HTTP Features

- HTTP is a stateless protocol.
- HTTP status codes are error messages.
  + 400
  + 401
  + 403
  + 404
  + 408
  + 500
  + 501
  + 502
  + 503
- Custom 404 error pages.

## URI

```
        userinfo     host        port
        ┌─┴────┐ ┌────┴────────┐ ┌┴┐
https://john.doe@www.example.com:123/forum/questions/?tag=networking&order=newest#top
└─┬─┘ └───────┬────────────────────┘└─┬─────────────┘└──┬───────────────────────┘└┬─┘  
scheme     authority                 path              query                      fragment

ldap://[2001:db8::7]/c=GB?objectClass?one
└─┬┘ └───────┬─────┘└─┬─┘ └──────┬──────┘
scheme    authority  path       query

mailto:John.Doe@example.com
└──┬─┘ └─────────┬────────┘
scheme         path

news:comp.infosystems.www.servers.unix
└─┬┘ └───────────────┬───────────────┘
scheme              path

tel:+1-816-555-1212
└┬┘ └──────┬──────┘
scheme     path

telnet://192.0.2.16:80/
└──┬─┘ └──────┬──────┘│
scheme    authority  path

urn:oasis:names:specification:docbook:dtd:xml:4.1.2
└┬┘ └──────────────────────┬──────────────────────┘
scheme                     path

```



百度首页搜索node关键词的Request headers source: 

```javascript
/////////////////////请求方法 请求的资源 HTTP版本号
GET /s?ie=utf-8&csq=1&pstg=20&mod=2&isbd=1&cqid=afbb0bed0014983d&istc=550&ver=RA5hTgFV0b4ajeyfmqrTmO9W1b2-ZS7QD93&chk=5d15916d&isid=6A18A51CBB657680&wd=node&rsv_spt=1&rsv_iqid=0x9f3d835a000368e9&issp=1&f=8&rsv_bp=1&rsv_idx=2&ie=utf-8&tn=baiduhome_pg&rsv_enter=1&rsv_sug3=6&rsv_sug1=6&rsv_sug7=101&rsv_sug2=0&inputT=1003&rsv_sug4=1920&rsv_sug=2&f4s=1&_ck=1170.0.-1.-1.-1.-1.-1&rsv_isid=1430_21120_29135_29238_28519_29099_29131_28839_29220&isnop=1&rsv_stat=1_0_-1_2_4.5.9.4&rsv_bp=1 HTTP/1.1

//////////////////可选的请求首部字段：表示请求和响应的各种条件和属性
//请求资源所在服务器
Host: www.baidu.com

//持久链接解决TCP断开连接问题
Connection: keep-alive

//用户代理课处理的媒体类型
Accept: */*

is_xhr: 1

X-Requested-With: XMLHttpRequest

is_referer: https://www.baidu.com/

//HTTP客户端的信息
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_13_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/75.0.3770.100 Safari/537.36

//对请求中URI的原始获取方
Referer: https://www.baidu.com/s?wd=node&rsv_spt=1&rsv_iqid=0x9f3d835a000368e9&issp=1&f=8&rsv_bp=1&rsv_idx=2&ie=utf-8&tn=baiduhome_pg&rsv_enter=1&rsv_sug3=6&rsv_sug1=6&rsv_sug7=101&rsv_sug2=0&inputT=1003&rsv_sug4=1920&rsv_sug=2

//通过编码提升传输效率
Accept-Encoding: gzip, deflate, br

//优先的语言
Accept-Language: zh-CN,zh;q=0.9,en-US;q=0.8,en;q=0.7

//通过写入cookie信息控制客户端的状态
Cookie: BAIDUID=6A18A52A41B3B60BE7A0DAA966D1CBB6:FG=1; BIDUPSID=6A18A52A41B3B60BE7A0DAA966D1CBB6; PSTM=1558944641; BD_UPN=123253; __cfduid=d713ae97ebd301872d827b26f1ca00c2d1559453170; BDUSS=VphdHFuc2VORndkYW9STlgxUTlNdHB1ME4tYTZROTdqWEI3ZE1QUUl0V2RraDFkSVFBQUFBJCQAAAAAAAAAAAEAAACTqN~Mempzb25pYzYAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAJ0F9lydBfZcR; H_PS_PSSID=1430_21120_29135_29238_28519_29099_29131_28839_29220; BDSFRCVID=l8tOJeC62RzQnerwLVfC5PIT0e4PGf3TH6aoDcjC2dIxgihuXui_EG0PHM8g0Ku-yLM5ogKK0mOTHUFF_2uxOjjg8UtVJeC6EG0P3J; H_BDCLCKID_SF=tR4j_DPbfCvbfP0kKtrhKPk0Mf7t5RJ324o2WbCQ5bcTqpcNLUbWQTt35R3HqlOR2DPHhtoXXK5vsDDwWl75XhD1DPCEtjLetJKJ_Dvqa6uKh6rnh6R-yq8gyxomtjjQKJ7jWn_XLp3vqqcT5fvrbntrMGo2LUkqKCOj-PTyBx3osf3G5fKBWl-uQttjQU3hfIkja-KEKC0bqR7TyU42hf47yboW0q4Hb6b9BJcjfU5MSlcNLTjpQT8rDPCEJ68OtR4f_CtQb-3bKRcGhtr_bICShUFsaqQCB2Q-5KL-LfJq8RRheq3nyPtpbpory-bObNON_MbdJJjoVqRaK4JUyP-sBPo2Jt3T0eTxoUJHQCnJhhvGqtJrjjLebPRiJPr9QgbPBhQ7tt5W8ncFbT7l5hKpbt-q0x-jLn7ZVDKbfC8bbKtr5tTEhP6D-Uv05-PX2DPX3b7EfMTJEq7_bf--D60_-RJdBJ-eBJn9_xJjyRn1olAzy6jxy5K_hPoWtfbPMgQPLU3H-lChbMjHQT3mKfrbbN3i-Crv-ncGWb3cWKJV8UbS3fjPBTD02-nBat-OQ6npaJ5nJq5nhMtRy6Chj6JyDGLJqbbfb-ofL4cSa-5BfJrw5DTjhPrMha7JWMT-0bFHbtclaJ5KfpRKbx-h0MF7DM_JQUbhtan7_JjO3nO8EIogyJ7JMtk0Who0yMQxtNR72CnjtpvhKtTsXjoobUPUDMc9LUvP3ecdot5yBbc8eIna5hjkbfJBQttjQTJZfD7H3KChJD-MbfK; BDORZ=B490B5EBF6F3CD402E515D22BCDA1598; BDRCVFR[feWj1Vr5u3D]=I67x6TjHwwYf0; delPer=0; BD_CK_SAM=1; PSINO=1; COOKIE_SESSION=6_2_9_8_4_39_0_2_7_4_1_0_0_0_0_0_1561178034_1560752670_1561694565%7C9%23707717_9_1561460379%7C3; BD_HOME=1; H_PS_645EC=5276dDs%2Bb51XQ0IvWJ78S1hPc3305odQbWkfmZzWwUUVShPXGF5kECqM8AhTaEYbhdZA
```

- HOST
- Connection
- Cache-Control
- Upgrade-Insecure-Requests
- User-Agent
- Accept
- Accept-Encoding
- Accept-Language
- Cookie

Request Headers parsed

```javascript
Accept: */*
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9,en-US;q=0.8,en;q=0.7
Connection: keep-alive
Cookie: BAIDUID=6A18A52A41B3B60BE7A0DAA966D1CBB6:FG=1; BIDUPSID=6A18A52A41B3B60BE7A0DAA966D1CBB6; PSTM=1558944641; BD_UPN=123253; __cfduid=d713ae97ebd301872d827b26f1ca00c2d1559453170; BDUSS=VphdHFuc2VORndkYW9STlgxUTlNdHB1ME4tYTZROTdqWEI3ZE1QUUl0V2RraDFkSVFBQUFBJCQAAAAAAAAAAAEAAACTqN~Mempzb25pYzYAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAJ0F9lydBfZcR; H_PS_PSSID=1430_21120_29135_29238_28519_29099_29131_28839_29220; BDSFRCVID=l8tOJeC62RzQnerwLVfC5PIT0e4PGf3TH6aoDcjC2dIxgihuXui_EG0PHM8g0Ku-yLM5ogKK0mOTHUFF_2uxOjjg8UtVJeC6EG0P3J; H_BDCLCKID_SF=tR4j_DPbfCvbfP0kKtrhKPk0Mf7t5RJ324o2WbCQ5bcTqpcNLUbWQTt35R3HqlOR2DPHhtoXXK5vsDDwWl75XhD1DPCEtjLetJKJ_Dvqa6uKh6rnh6R-yq8gyxomtjjQKJ7jWn_XLp3vqqcT5fvrbntrMGo2LUkqKCOj-PTyBx3osf3G5fKBWl-uQttjQU3hfIkja-KEKC0bqR7TyU42hf47yboW0q4Hb6b9BJcjfU5MSlcNLTjpQT8rDPCEJ68OtR4f_CtQb-3bKRcGhtr_bICShUFsaqQCB2Q-5KL-LfJq8RRheq3nyPtpbpory-bObNON_MbdJJjoVqRaK4JUyP-sBPo2Jt3T0eTxoUJHQCnJhhvGqtJrjjLebPRiJPr9QgbPBhQ7tt5W8ncFbT7l5hKpbt-q0x-jLn7ZVDKbfC8bbKtr5tTEhP6D-Uv05-PX2DPX3b7EfMTJEq7_bf--D60_-RJdBJ-eBJn9_xJjyRn1olAzy6jxy5K_hPoWtfbPMgQPLU3H-lChbMjHQT3mKfrbbN3i-Crv-ncGWb3cWKJV8UbS3fjPBTD02-nBat-OQ6npaJ5nJq5nhMtRy6Chj6JyDGLJqbbfb-ofL4cSa-5BfJrw5DTjhPrMha7JWMT-0bFHbtclaJ5KfpRKbx-h0MF7DM_JQUbhtan7_JjO3nO8EIogyJ7JMtk0Who0yMQxtNR72CnjtpvhKtTsXjoobUPUDMc9LUvP3ecdot5yBbc8eIna5hjkbfJBQttjQTJZfD7H3KChJD-MbfK; BDORZ=B490B5EBF6F3CD402E515D22BCDA1598; BDRCVFR[feWj1Vr5u3D]=I67x6TjHwwYf0; delPer=0; BD_CK_SAM=1; PSINO=1; COOKIE_SESSION=6_2_9_8_4_39_0_2_7_4_1_0_0_0_0_0_1561178034_1560752670_1561694565%7C9%23707717_9_1561460379%7C3; BD_HOME=1; H_PS_645EC=5276dDs%2Bb51XQ0IvWJ78S1hPc3305odQbWkfmZzWwUUVShPXGF5kECqM8AhTaEYbhdZA
Host: www.baidu.com
is_referer: https://www.baidu.com/
is_xhr: 1
Referer: https://www.baidu.com/s?wd=node&rsv_spt=1&rsv_iqid=0x9f3d835a000368e9&issp=1&f=8&rsv_bp=1&rsv_idx=2&ie=utf-8&tn=baiduhome_pg&rsv_enter=1&rsv_sug3=6&rsv_sug1=6&rsv_sug7=101&rsv_sug2=0&inputT=1003&rsv_sug4=1920&rsv_sug=2
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_13_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/75.0.3770.100 Safari/537.36
X-Requested-With: XMLHttpRequest
```

- Accept
- Accept-Encoding
- Accept-Language
- Cache-Control
- Connection
- Cookie
- Host
- Upgrade-Insecure-Requests
- User-Agent

## weibo.com Response headers

source

```javascript
HTTP/1.1 200 OK
Server: WeiBo/LB
Date: Fri, 28 Jun 2019 05:03:34 GMT
Content-Type: text/html; charset=utf-8
Transfer-Encoding: chunked
Connection: keep-alive
Vary: Accept-Encoding
Cache-Control: no-cache, must-revalidate
Expires: Sat, 26 Jul 1997 05:00:00 GMT
Pragma: no-cache
Content-Security-Policy: block-all-mixed-content;
DPOOL_HEADER: weibo_com11y117
Content-Encoding: gzip
LB_HEADER: venus240
Strict-Transport-Security: max-age=31536000; preload
```



parsed

```javascript
Cache-Control: no-cache, must-revalidate
Connection: keep-alive
Content-Encoding: gzip
Content-Security-Policy: block-all-mixed-content;
Content-Type: text/html; charset=utf-8
Date: Fri, 28 Jun 2019 05:03:34 GMT
DPOOL_HEADER: weibo_com11y117
Expires: Sat, 26 Jul 1997 05:00:00 GMT
LB_HEADER: venus240
Pragma: no-cache
Server: WeiBo/LB
Strict-Transport-Security: max-age=31536000; preload
Transfer-Encoding: chunked
Vary: Accept-Encoding
```



## references
- [https://en.wikipedia.org/wiki/Uniform_Resource_Identifier](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier)
- [https://www.webopedia.com/TERM/H/HTTP.html](https://www.webopedia.com/TERM/H/HTTP.html)

