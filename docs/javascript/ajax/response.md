---
layout: default
title: Response
parent: AJAX
grand_parent: JavaScript
nav_order: 3
---

# AJAX - Server Response
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Server Response

### Server Response Properties

| Property                               | Description                                                          |
|:---------------------------------------|:---------------------------------------------------------------------|
| onreadystatechange                     | readyState 속성이 변할 때 호출될 함수를 정의하고 호출                      |
| readyState                             | XMLHttpRequest의 상태를 홀드                                           |
|                                        | 0: request not initialized                                           |
|                                        | 1: server connection established                                     |
|                                        | 2: request received                                                  | 
|                                        | 3: processing request                                                |
|                                        | 4: request finished and response is ready                            |
| status                                 | XMLHttpRequest의 객체의 상태를 유지, 상태를 보유하고 메시지를 숫자로 리턴    |
|                                        | 200: "OK"                                                            |
|                                        | 403: "Forbidden"                                                     |
|                                        | 404: "Not Found"                                                     |
|                                        | [더보기](https://www.w3schools.com/tags/ref_httpmessages.asp)         |
| statusText	                         | XMLHttpRequest의 객체의 상태를 보유, 상태 메시지를 텍스트로 리턴            |


예제
{: .label .label-purple .mt-3}
```js
function loadDoc() {
  var xhttp = new XMLHttpRequest();
  xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
      document.getElementById("demo").innerHTML =
      this.responseText;
    }
  };
  xhttp.open("GET", "ajax_info.txt", true);
  xhttp.send();
}

//onreadystatechange는 readyState가 4가 될때까지 4번 실행됨
```

### Using a Callback Function

콜백 함수는 **다른 함수에 매개 변수로 전달되는 함수**

웹 사이트에 둘 이상의 AJAX 태스크가있는 경우 XMLHttpRequest오브젝트 를 실행하기 위한 함수 하나와 각 AJAX 태스크마다 하나의 콜백 함수를 작성해야 함

함수 호출에는 URL과 응답이 준비 될 때 호출 할 함수가 포함되어야 함

예제
{: .label .label-purple .mt-3}
```js
loadDoc("url-1", myFunction1);

loadDoc("url-2", myFunction2);

function loadDoc(url, cFunction) {
  var xhttp;
  xhttp = new XMLHttpRequest();
  xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
      cFunction(this);
    }
  };
  xhttp.open("GET", url, true);
  xhttp.send();
}

function myFunction1(xhttp) {
  // action goes here
}
function myFunction2(xhttp) {
  // action goes here
}
```

### Server Response Properties

| Property                               | Description                                                  |
|:---------------------------------------|:-------------------------------------------------------------|
| responseText	                         | 문자열로 response 데이터를 리턴                                 |
| responseXML	                         | XML data로 response 데이터를 리턴                              |

* responseText 

    **서버 응답을 JavaScript 문자열로 반환하며 그에 따라 사용**
    
    예제
    {: .label .label-purple .mt-3}
    ```js
    document.getElementById("demo").innerHTML = xhttp.responseText;
    ```
    
* responseXML  

    XMLHttpRequest 객체에는 XML parser가 있음
    
    responseXML특성은 서버 응답을 XML DOM 객체로 리턴, 이 특성을 사용해 응답을 XML DOM 오브젝트로 구문 분석 할 수 있음
    
    객체이기 때문에 객체처럼 다뤄줘야 함!!
    
    예제
    {: .label .label-purple .mt-3}
    ```js
    xmlDoc = xhttp.responseXML;
    txt = "";
    x = xmlDoc.getElementsByTagName("ARTIST");
    for (i = 0; i < x.length; i++) {
      txt += x[i].childNodes[0].nodeValue + "<br>";
    }
    document.getElementById("demo").innerHTML = txt;
    xhttp.open("GET", "cd_catalog.xml", true);
    xhttp.send();
    ```
    
    <span class="fs-2">
    [W3C Example](https://www.w3schools.com/js/tryit.asp?filename=tryjs_ajax_responsexml){: .btn  .btn-outline .mt-2}
    </span>

    [XML DOM]()에서 더 알아보기

### Server Response Properties

| Method                                 | Description                                       |
|:---------------------------------------|:--------------------------------------------------|
| getAllResponseHeaders()                | 헤더의 정보를 리턴                                   |
| getResponseHeader()                    | 헤더의 특정한 정보를 리턴                             |

* getAllResponseHeaders()

    **서버 응답에서 모든 헤더 정보를 리턴**
    
    예제
    {: .label .label-purple .mt-3}
    ```js
    var xhttp = new XMLHttpRequest();
    xhttp.onreadystatechange = function() {
      if (this.readyState == 4 && this.status == 200) {
        document.getElementById("demo").innerHTML =
        this.getAllResponseHeaders();
      }
    };
    ```

* getResponseHeader()

    **서버 응답에서 특정 헤더 정보를 리턴**
    
    `getAllResponseHeaders`에서 일부 정보만 가지고 오고 싶을 때 사용!
    
    case-inseneitive 함
    
    예제
    {: .label .label-purple .mt-3}
    ```js
    var xhttp = new XMLHttpRequest();
    xhttp.onreadystatechange = function() {
      if (this.readyState == 4 && this.status == 200) {
        document.getElementById("demo").innerHTML =
        this.getResponseHeader("Last-Modified");
      }
    };
    xhttp.open("GET", "ajax_info.txt", true);
    xhttp.send();
    ```
    
    <span class="fs-2">
    [W3C Example](https://www.w3schools.com/js/tryit.asp?filename=tryjs_ajax_lastmodified){: .btn  .btn-outline .mt-2}
    </span>

