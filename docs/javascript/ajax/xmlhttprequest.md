---
layout: default
title: XMLHttpRequest
parent: AJAX
grand_parent: JavaScript
nav_order: 1
---

# AJAX XMLHttpRequest
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## XMLHttpRequest Basic

### XMLHttpRequest Object

**AJAX의 핵심**

모든 최신 브라우저는 `XMLHttpRequest` 객체를 지원함

`XMLHttpRequest` 객체는 뒤에서 웹 서버와 데이터를 교환할 수 있어서 전체 페이지를 로드하지 않고도 웹 페이지의 일부를 업데이트 할 수 있음

### Access Across Domains

보안상의 이유로 브라우저는 도메인간 엑세스를 허용하지 않기 때문에 엑세스 하려면 **로드하려는 웹 페이지와 XML 파일이 모두 동일한 서버**에 있어야 함

즉 AJAX를 사용하려면 XML 파일이 홈페이지와 동일한 자체 서버에 있어야함

### Create an XMLHttpRequest Object

모든 최신 브라우저에는 내장 `XMLHttpRequest`객체가 있음

XMLHttpRequest 객체 생성 구문
{: .label .mt-2}
<div class="code-example" markdown="1">
variable = new XMLHttpRequest();
</div>

### ActiveX for Older Browsers

오래된 브라우저는 `XMLHttpRequest`객체 대신 `ActiveX` 객체를 사용함

ActiveX 객체 생성 구문
{: .label .mt-2}
<div class="code-example" markdown="1">
variable = new ActiveXObject("Microsoft.XMLHTTP");
</div>

### Create Object for All Browsers

따라서 모든 브라우저에서 `XMLHttpRequest`객체를 이용하기 위해 아래 구문을 사용함

IE5,6까지 처리하는 코드
{: .label .mt-2}
```js
if (window.XMLHttpRequest) {
   // code for modern browsers
   xmlhttp = new XMLHttpRequest();
 } else {
   // code for old IE browsers
   xmlhttp = new ActiveXObject("Microsoft.XMLHTTP");
}
```

### XMLHttpRequest Objext Methods

| Method                                 | Description                                       |
|:---------------------------------------|:--------------------------------------------------|
| new XMLHttpRequest()                   | XMLHttpRequest 객체 생성                           |
| abort()                                | 현재 요청 취소                                      |
| getAllResponseHeaders()                | 헤더의 정보를 리턴                                   |
| getResponseHeader()                    | 헤더의 특정한 정보를 리턴                             |
| open(method, url, async, user, psw)    | 요청의 타입을 구체적으로 명시                         |
|                                        | method: the request type GET or POST              |
|                                        | url: the file location                            |
|                                        | async: true (asynchronous) or false (synchronous) |
|                                        | user: optional user name                          |
|                                        | psw: optional password                            |
|                                        | psw: optional password                            |
|                                        | psw: optional password                            |
| send()                                 | 서버에게 요청, Used for GET requests                |
| send(string)                           | 서버에게 요청, Used for POST requests               |
| setRequestHeader()                     | 헤더에게 보내져야 할 라벨/값 쌍을 더함                 |

[Request 페이지]()에서 더욱 자세하게 설명

### XMLHttpRequest Objext Properties

| Property                               | Description                                                  |
|:---------------------------------------|:-------------------------------------------------------------|
| onreadystatechange                     | readyState 속성이 변할 때 함수가 호출 결정                       |
| readyState                             | XMLHttpRequest의 상태를 홀드                                   |
|                                        | 0: request not initialized                                   |
|                                        | 1: server connection established                             |
|                                        | 2: request received                                          | 
|                                        | 3: processing request                                        |
|                                        | 4: request finished and response is ready                    |
| responseText	                         | 문자열로 response 데이터를 리턴                                 |
| responseXML	                         | XML data로 response 데이터를 리턴                              |
| status                                 | 요청의 상태 메시지를 숫자로 리턴                                 |
|                                        | 200: "OK"                                                    |
|                                        | 403: "Forbidden"                                             |
|                                        | 404: "Not Found"                                             |
|                                        | [더보기](https://www.w3schools.com/tags/ref_httpmessages.asp) |
| statusText	                         | 상태 메시지를 -텍스트로 리턴 (e.g. "OK" or "Not Found")          |
| send(string)                           | 서버에게 요청, Used for POST requests                          |
| setRequestHeader()                     | 헤더에게 보내져야 할 라벨/값 쌍을 더함                            |

[Request 페이지]()에서 더욱 자세하게 설명
