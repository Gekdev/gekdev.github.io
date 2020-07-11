---
layout: default
title: Events
parent: HTML DOM
grand_parent: JavaScript
nav_order: 4
---

# HTML DOM Events
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Events Basic

### Reacting to Events

JavaScript lets you execute code when events are detected

HTML을 사용하면 JavaScript 코드가있는 이벤트 핸들러 속성 을 HTML 요소에 추가 할 수 있다

Syntax
{: .label .mt-2}
```html
<element event="some JavaScript">
```
    
자주 사용되는 돔 이벤트
{: .label .mt-3}

| Event         | Description                                           |
|:--------------|:------------------------------------------------------|
| onchange      | An HTML element has been changed                      |
| onclick       | The user clicks an HTML element                       |
| onmouseover   | The user moves the mouse over an HTML element         |
| onmouseout    | The user moves the mouse away from an HTML element    |
| onkeydown     | The user pushes a keyboard key                        |
| onload        | The browser has finished loading the page             |

<span class="fs-2">
[더 알아보기](https://www.w3schools.com/jsref/dom_obj_event.asp){: .btn  .btn-outline .mt-2}
</span>

### Assign Event Attributes

**이벤트 속성을 사용해서 html태그에 이벤트를 할당할 수 있음**

예제
{: .label .label-purple .mt-3}
```js
<button onclick="displayDate()">Try it</button>
```

### Assign Events Using the HTML DOM

**돔을 사용해서 HTML 이벤트를 할당할 수 있음**

예제
{: .label .label-purple .mt-3}
```js
document.getElementById("myBtn").onclick = displayDate;
```

---

## DOM Events

### Document/Window Events

* onload
    
    **페이지를 들어갈 때 트리거**

    방문자의 **브라우저 유형 및 브라우저 버전을 확인하고 정보를 기반으로 올바른 버전의 웹 페이지를 로드**하는 데 사용
    
    쿠키를 처리하는 데 사용할 수 있음

    예제
    {: .label .label-purple .mt-3}
    <div class="code-example" markdown="1">
    <body onload="checkCookies()">

    <p id="demo"></p>

    <script>
    function checkCookies() {
      var text = "";
      if (navigator.cookieEnabled == true) {
        text = "Cookies are enabled.";
      } else {
        text = "Cookies are not enabled.";
      }
      document.getElementById("demo").innerHTML = text;
    }
    </script>

    </body>
    </div>
    ```html
    <body onload="checkCookies()">

    <p id="demo"></p>

    <script>
    function checkCookies() {
      var text = "";
      if (navigator.cookieEnabled == true) {
        text = "Cookies are enabled.";
      } else {
        text = "Cookies are not enabled.";
      }
      document.getElementById("demo").innerHTML = text;
    }
    </script>

    </body>
    ```

* onunload 

    **페이지를 나갈 때 트리거**
    
    쿠키를 처리하는 데 사용할 수 있음

### Form Event

* onchange

    **사용자가 입력 필드의 내용을 변경하는 경우 트리거**

    입력 필드의 유효성 검사와 함께 사용
    
    예제
    {: .label .label-purple .mt-3}
    <div class="code-example" markdown="1">
    <script>
    function myFunction() {
      var x = document.getElementById("fname");
      x.value = x.value.toUpperCase();
    }
    </script>
    </head>
    <body>

    Enter your name: <input type="text" id="fname" onchange="myFunction()">

    </body>
    </div>
    ```html
    <input type="text" id="fname" onchange="upperCase()">
    ```
    
### Mouse Events

* onclick

* onmouseover

    **마우스가 들어가면 트리거**

    예제
    {: .label .label-purple .mt-3}
    ```html
    <input type="text" id="fname" onchange="upperCase()">
    ```
    
* onmouseout 

    **사용자가 마우스를 나가면 트리거**

* onmousedown

* onmouseup


























