---
layout: default
title: Web API
parent: JavaScript
nav_order: 22
has_children: true
---

# JavaScript Web API
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Geolocation API

### What is Geolocation API?

**locate a user's position**

### Using HTML Geolocation

getCurrentPosition() : used to return the user's position

```html
<button onclick="getLocation()">Click the button to get your coordinates</button>

<p id="demo"></p>

<script>
var x = document.getElementById("demo");
function getLocation() {
  if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition(showPosition);
  } else {
    x.innerHTML = "Geolocation is not supported by this browser.";
  }
}

function showPosition(position) {
  x.innerHTML = "Latitude: " + position.coords.latitude +
  "<br>Longitude: " + position.coords.longitude;
}
</script>
```

[W3C Example](https://www.w3schools.com/html/tryit.asp?filename=tryhtml5_geolocation)
{: .mt-2}

### Handling Errors and Rejections

getCurrentPosition()메소드 의 두 번째 매개 변수는 오류를 처리하는 데 사용됨

사용자의 위치를 얻지 못하면 실행할 함수를 지정

```html
<button onclick="getLocation()">Try It</button>

<p id="demo"></p>

<script>
var x = document.getElementById("demo");

function getLocation() {
  if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition(showPosition, showError);
  } else { 
    x.innerHTML = "Geolocation is not supported by this browser.";
  }
}

function showPosition(position) {
  x.innerHTML = "Latitude: " + position.coords.latitude + 
  "<br>Longitude: " + position.coords.longitude;
}

function showError(error) {
  switch(error.code) {
    case error.PERMISSION_DENIED:
      x.innerHTML = "User denied the request for Geolocation."
      break;
    case error.POSITION_UNAVAILABLE:
      x.innerHTML = "Location information is unavailable."
      break;
    case error.TIMEOUT:
      x.innerHTML = "The request to get user location timed out."
      break;
    case error.UNKNOWN_ERROR:
      x.innerHTML = "An unknown error occurred."
      break;
  }
}
</script>
```

[W3C Example](https://www.w3schools.com/html/tryit.asp?filename=tryhtml5_geolocation_error)
{: .mt-2}

### Displaying the Result in a Map

맵을 표시하려면 맵 서비스를 이용해야함 

네이버, 다음(best), 구글에서 지원함 (구글은 유료)

<span class="fs-2">
[Daum Kakao API](https://apis.map.kakao.com/){: .btn  .btn-outline  .mt-2}
</span>

---

## Drag and Drop API

### Drag and Drop Example

```html
<script>
function allowDrop(ev) {
  ev.preventDefault();
}

function drag(ev) {
  ev.dataTransfer.setData("text", ev.target.id);
}

function drop(ev) {
  ev.preventDefault();
  var data = ev.dataTransfer.getData("text");
  ev.target.appendChild(document.getElementById(data));
}
</script>
</head>
<body>

<p>Drag the W3Schools image into the rectangle:</p>

<div id="div1" ondrop="drop(event)" ondragover="allowDrop(event)"></div>
<br>
<img id="drag1" src="img_logo.gif" draggable="true" ondragstart="drag(event)" width="336" height="69">
```

### Drag and Drop Explain

1. 요소를 끌리게 만들기

    ```html
    <img draggable="true">
    ```
    
2. 무엇을 드래그할지 설정하기

    ```html
    <script>
    function drag(ev) {
      ev.dataTransfer.setData("text", ev.target.id);
    }
    </script>
    
    <img draggable="true" ondragstart="drag(event)">
    ```

    &#9656; ondragstart : 함수를 부르고, 드래그할 데이터를 지정함
    
    &#9656; dataTransfer.setData() : 데이터 유형, 드래그 된 데이터의 값을 설정
    
3. 어디에 드롭할지 설정하기

    &#9656; ondragover : 드래그 한 데이터를 놓을 수있는 위치를 지정
    
    &#9656; event.preventDefault() : 기본적으로 데이터 / 요소는 다른 요소에서 삭제할 수 없어서 드롭을 허용하려면 요소의 기본 처리를 방지해야하기 위해 사용
    
4. 드롭하기
    
    ondrop 드롭한 후 드롭 이벤트 처리하기
    
    ```js
    function drop(ev) {
      ev.preventDefault();
      var data = ev.dataTransfer.getData("text");
      ev.target.appendChild(document.getElementById(data));
    }
    ```

[W3C Example](https://www.w3schools.com/html/tryit.asp?filename=tryhtml5_draganddrop2)
    
---

## Web Storage API

### What is Web Storage?

**웹 애플리케이션이 사용자 브라우저 내에 로컬로 데이터를 저장**

### Features of  Web Storage?

&#9656; 안전하게 웹 사이트 성능에 영향을주지 않고 대량의 데이터를 로컬에 저장

&#9656; 쿠키와 달리 스토리지 제한은 훨씬 크다 (최소 5MB)

&#9656; 정보는 서버로 전송되지 않음

&#9656; 원본과 도메인 및 프로토콜별로 제공

&#9656; 한 출처의 모든 페이지는 동일한 데이터를 저장하고 액세스 할 수 있다

### Web Storage Objects

* window.localStorage 

    **stores data with no expiration date**
    
    브라우저 창이 닫히지 않으면 언제든지 이용가능함 
    
    ```js
    // Store
    localStorage.setItem("lastname", "Smith");

    // Retrieve
    document.getElementById("result").innerHTML = localStorage.getItem("lastname");
    ```
    
    이렇게도 작성 가능함
    
    ```js
    // Store
    localStorage.lastname = "Smith";
    // Retrieve
    document.getElementById("result").innerHTML = localStorage.lastname;
    ```
    
    Removing localStorage Syntax
    {: .label .mt-3}
    <div class="code-example" markdown="1">
    localStorage.removeItem("lastname");
    </div>
    
    Note
    {: .label .label-yellow .mt-3}
    <div class="code-example" markdown="1">
    Name/value pairs are always stored as strings. Remember to convert them to another format when needed!
    </div>
    
    [로컬 저장소를 이용한 숫자세기](https://www.w3schools.com/html/tryit.asp?filename=tryhtml5_webstorage_local_clickcount)
    
* window.sessionStorage 

    **stores data for one session** (data is lost when the browser tab is closed)

    [세션 저장소를 이용한 숫자세기](https://www.w3schools.com/html/tryit.asp?filename=tryhtml5_webstorage_session)

### Check Web Storage Support

Before using web storage, check browser support for localStorage and sessionStorage

```js
if (typeof(Storage) !== "undefined") {
  // Code for localStorage/sessionStorage.
} else {
  // Sorry! No Web Storage support..
}
```
   
---

## Web Workers API

### What is a Web Worker?

**JavaScript that runs in the background, independently of other scripts, without affecting the performance of the page**

You can continue to do whatever you want: clicking, selecting things, etc., while the web worker runs in the background

### Check Web Worker Support

Before creating a web worker, check whether the user's browser supports it

```js
if (typeof(Worker) !== "undefined") {
  // Yes! Web worker support!
  // Some code.....
} else {
  // Sorry! No Web Worker support..
}
```

### How to make Web Worker File

1. Create a Web Worker File (demo_workers.js)

    ```js
    var i = 0;

    function timedCount() {
      i = i + 1;
      postMessage(i);
      setTimeout("timedCount()",500);
    }

    timedCount();
    ```
    
    &#9656; postMessage() : post a message back to the HTML page
    
    Note
    {: .label .label-yellow .mt-3}
    <div class="code-example" markdown="1">
    Normally web workers are not used for such simple scripts, but for more CPU intensive tasks.
    </div>

2. Create a Web Worker Object

    checks if the worker already exists
    
    ```js
    if (typeof(w) == "undefined") {
      w = new Worker("demo_workers.js");
    }
    ```

    can send and receive messages from the web worker
    
    ```js
    w.onmessage = function(event){
      document.getElementById("result").innerHTML = event.data;
    };
    ```
    
    When the web worker posts a message, the code within the event listener is executed. The data from the web worker is stored in event.data.

3. Terminate a Web Worker

    When a web worker object is created, it will continue to listen for messages (even after the external script is finished) until it is terminated.
    
    ```js
    w.terminate();
    ```
    
    &#9656; terminate() : To terminate a web worker, and free browser/computer resources
    
4. Reuse the Web Worker

    If you set the worker variable to undefined, after it has been terminated, you can reuse the code
    
    ```js
    w = undefined;
    ```

[Full Web Worker Example Code](https://www.w3schools.com/html/tryit.asp?filename=tryhtml5_webworker)

---

## SSE API

### Server-Sent Events (One Way Messaging)

**when a web page automatically gets updates from a server**

This was also possible before, but the web page would have to ask if any updates were available. With server-sent events, the updates come automatically

Examples: Facebook/Twitter updates, stock price updates, news feeds, sport results, etc.

### Receive Server-Sent Event Notifications

```js
var source = new EventSource("demo_sse.php");
source.onmessage = function(event) {
  document.getElementById("result").innerHTML += event.data + "<br>";
};
```

&#9656; EventSource : receive server-sent event notifications

### Check Server-Sent Events Support

In the tryit example above there were some extra lines of code to check browser support for server-sent events

```js
if(typeof(EventSource) !== "undefined") {
  // Yes! Server-sent events support!
  // Some code.....
} else {
  // Sorry! No server-sent events support..
}
```

### Server-Side Code Example

The server-side event stream syntax is simple. Set the "Content-Type" header to "text/event-stream". Now you can start sending event streams.

Code in PHP (demo_sse.php)
```php
<?php
header('Content-Type: text/event-stream');
header('Cache-Control: no-cache');

$time = date('r');
echo "data: The server time is: {$time}\n\n";
flush();
?>
```

<br>

Code in ASP (VB) (demo_sse.asp)
```php
<%
Response.ContentType = "text/event-stream"
Response.Expires = -1
Response.Write("data: The server time is: " & now())
Response.Flush()
%>
```

[Example Code](https://www.w3schools.com/html/tryit.asp?filename=tryhtml5_sse)

[Full Explain](https://www.w3schools.com/html/html5_serversentevents.asp)

