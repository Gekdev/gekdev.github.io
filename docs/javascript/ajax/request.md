---
layout: default
title: Request
parent: AJAX
grand_parent: JavaScript
nav_order: 2
---

# AJAX Request
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Send a Request To a Server

### Request Method

서버에 요청을 보내기 위해 사용되는 `XMLHttpRequest` 객체의 메소드들

open(), send() 메소드들을 주로 사용한다

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
xhttp.open("GET", "ajax_info.txt", true); <br>
xhttp.send();                        
</div>

| Method                                 | Description                                       |
|:---------------------------------------|:--------------------------------------------------|
| open(method, url, async, user, psw)    | 요청을 구체적으로 명시                                |
|                                        | method: the request type GET or POST              |
|                                        | url: the file location                            |
|                                        | async: true (asynchronous) or false (synchronous) |
|                                        | user: optional user name                          |
|                                        | psw: optional password                            |
| send()                                 | 서버에게 요청, Used for GET requests                |
| send(string)                           | 서버에게 요청, Used for POST requests               |
| setRequestHeader()                     | 헤더에게 보내져야 할 라벨/값 쌍을 더함 (POST)          |

### Method - GET or POST ?

GET이 POST 보다 더 빠르고 심플하고 많은 경우에 사용함

POST를 사용하는 경우는 다음과 같음

1. 서버에서 파일 또는 데이터베이스를 업데이트할 경우
2. 서버에 대량의 데이터 전송 (POST에는 크기 제한이 없음)
3. 알 수없는 문자를 포함 할 수있는 사용자 입력, (POST는 GET보다 강력하고 안전)

#### Basic GET Requst Form

기본 GET form
{: .label .mt-2}
<div class="code-example" markdown="1">
xhttp.open("GET", "demo_get.asp", true); <br>
xhttp.send();                       
</div>

정보를 포함해서 메소드를 보낼 때는 뒤에 url을 추가하면 됨

정보 GET form
{: .label .mt-2}
<div class="code-example" markdown="1">
xhttp.open("GET", "demo_get2.asp?fname=Henry&lname=Ford", true); <br>
xhttp.send();                 
</div>
```html
설명: 만약 demo_get2.asp 파일이 HELLO 라는 텍스트 파일이라면, 결과물은 HELLO Henry Ford 라는 값이 나옴 
```

#### Basic POST Requst Form

기본 GET form
{: .label .mt-2}
<div class="code-example" markdown="1">
xhttp.open("POST", "demo_get.asp", true); <br>
xhttp.send();                       
</div>

HTML 양식과 같은 데이터를 POST하려면 `setRequestHeader()`을 사용해 HTTP 헤더를 추가하고, send()로 보내려는 데이터를 지정

정보 GET form
{: .label .mt-2}
<div class="code-example" markdown="1">
xhttp.open("POST", "ajax_test.asp", true); <br>
xhttp.setRequestHeader("Content-type", "application/x-www-form-urlencoded"); <br>
xhttp.send("fname=Henry&lname=Ford");             
</div>
```html
설명: 만약 demo_get2.asp 파일이 HELLO 라는 텍스트 파일이라면, 결과물은 HELLO Henry Ford 라는 값이 나옴 
```

### URL - A File On a Server

`open()` 메소드의 url 매개변수는 **서버에 올려진 파일의 주소**

파일은 .txt, .xml 또는 .asp, .php(서버 스크립팅 파일 : 응답을 다시 보내기 전에 서버에서 작업을 수행 할 수 있는 파일)와 같은 거의 모든 파일이 가능함

<div class="code-example" markdown="1">
xhttp.open("GET", <mark>"ajax_test.asp"</mark>, true);
</div>

### Async - True or False?

#### Asynchronous Request

**서버 요청은 비동기 적으로 보내야함**

`open()` 메소드의 비동기 매개 변수는 true로 설정

비동기식으로 보내면 자바스크립트는 서버 응답을 기다릴 필요가 없음 그 대신 **서버 응답을 기다리는 동안 다른 스크립트를 실행하고, 응답이 준비된 후 응답을 처리할 수 있음**

<div class="code-example" markdown="1">
xhttp.open("GET", "ajax_test.asp", <mark>true</mark>);
</div>

XMLHttpRequest객체의 `onreadystatechange` 속성을 사용하면 **요청이 응답을 받을 때 실행될 함수를 정의할 수 있음**

예제
{: .label .label-purple .mt-3}
```js
function loadDoc() {
  var xhttp = new XMLHttpRequest();
  xhttp.onreadystatechange = function(){...}
  xhttp.open("GET", "ajax_info.txt", true);
  xhttp.send();
}
```

#### Synchronous Request

동기 요청을 실행하려면 open()메소드 의 세 번째 매개 변수를 false로 지정

async = false는 빠른 테스트에 사용, 예전 자바스크립트 코드에서도 종종 찾을 수 있음

<div class="code-example" markdown="1">
xhttp.open("GET", "ajax_test.asp", <mark>true</mark>);
</div>

서버가 응답을 완료할 때 까지 기다리기 때문에 `onreadystatechange` 속성을 사용할 필요 없음

예제
{: .label .label-purple .mt-3}
```js
function loadDoc() {
  var xhttp = new XMLHttpRequest();
  xhttp.open("GET", "ajax_info.txt", false);
  xhttp.send();
  document.getElementById("demo").innerHTML = xhttp.responseText;
}
```

!note
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
서버 응답이 준비 될 때까지 JavaScript가 실행을 중지하므로 동기요청 XMLHttpRequest (async = false)은 권장되지 않음. 서버가 사용 중이거나 느리면 응용 프로그램이 중단되거나 중지됨

동기 XMLHttpRequest가 웹 표준에서 제거되는 중임 (프로세스는 몇 년이 걸릴 수 있음)

최신 개발자 도구는 동기 요청 사용에 대해 경고하고 InvalidAccessError 예외가 발생하면 이를 발생시킬 수 있음
</div>

