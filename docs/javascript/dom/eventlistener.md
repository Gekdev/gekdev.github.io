---
layout: default
title: Event Listener
parent: HTML DOM
grand_parent: JavaScript
nav_order: 4
---

# HTML DOM Event Listener
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## DOM Event Listener

### The addEventListener() method

**특정한 요소에 이벤트 핸들러를 넣을 때 사용**

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
element.addEventListener(event, function, useCapture);

&#9656; event : [이벤트 유형](https://www.w3schools.com/jsref/dom_obj_event.asp)

&#9656; function: 이벤트가 발생할 때 호출하려는 함수

&#9656; useCapture(optional) : 이벤트 버블링 사용 여부 또는 이벤트 캡처 사용 여부를 지정
</div>
```js
document.getElementById("p2").style.color = "blue";
```

&#9656; 기존 이벤트 핸들러를 겹쳐 쓰지 않고 이벤트 핸들러를 요소에 첨부하면서 하나의 요소에 많은 이벤트 핸들러를 추가할 수 있음

예제
{: .label .label-purple .mt-3}
<div class="code-example" markdown="1">
element.addEventListener("mouseover", myFunction);
element.addEventListener("click", mySecondFunction);
element.addEventListener("mouseout", myThirdFunction);
</div>

&#9656; HTML 요소뿐만 아니라 모든 DOM 객체(HTML 요소, HTML 문서, 윈도우 객체 또는 객체와 같은 이벤트를 지원하는 기타 객체와 같은 HTML DOM 객체)에 이벤트 리스너를 추가 할 수 있음

예제
{: .label .label-purple .mt-3}
<div class="code-example" markdown="1">
<p id="demo"></p>

<script>
window.addEventListener("resize", function(){
  document.getElementById("demo").innerHTML = " 크기가 달라졌네요!";
});
</script>
</div>
```html
<p id="demo"></p>

<script>
window.addEventListener("resize", function(){
  document.getElementById("demo").innerHTML = " 크기가 달라졌네요!";
});
</script>
```

&#9656; 이 메소드를 사용하면 JavaScript는 HTML 마크 업과 분리되어 가독성을 높이고, HTML 마크 업을 제어하지 않더라도 이벤트 리스너를 추가 할 수 있음

&#9656; 이 메소드를 사용하면 이벤트가 버블 링에 반응하는 방식을보다 쉽게 제어 할 수 있음

&#9656; removeEventListener()로 이벤트 리스너를 제거할 수 있음

Note!
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
you don't use the "on" prefix for the event; use "click" instead of "onclick"
</div>

### Add an Event Handler to an Element

함수 매개변수에는 모든 종류의 함수가 다 올 수 있음

예제
{: .label .label-purple .mt-3}
<div class="code-example" markdown="1">
<button id="myBtn">Try it</button>

<script>
document.getElementById("myBtn").addEventListener("click", function() {
  alert("Hello World!");
});
</script>
</div>
```html
<button id="myBtn">Try it</button>

<script>
document.getElementById("myBtn").addEventListener("click", function() {
  alert("Hello World!");
});
</script>
```

매개 변수 값을 전달해야 할때는 매개 변수와 함께 지정된 함수를 호출하는 익명 함수를 사용

예제
{: .label .label-purple .mt-3}
<div class="code-example" markdown="1">
<button id="myBtn">Try it</button>

<p id="demo"></p>

<script>
var p1 = 5;
var p2 = 7;

document.getElementById("myBtn").addEventListener("click", function() {
  myFunction(p1, p2);
});

function myFunction(a, b) {
  var result = a * b;
  document.getElementById("demo").innerHTML = result;
}
</script>
</div>
```html
<button id="myBtn">Try it</button>

<p id="demo"></p>

<script>
var p1 = 5;
var p2 = 7;

document.getElementById("myBtn").addEventListener("click", function() {
  myFunction(p1, p2);
});

function myFunction(a, b) {
  var result = a * b;
  document.getElementById("demo").innerHTML = result;
}
</script>
```

### Event Bubbling or Event Capturing?

HTML DOM에는 버블 링 및 캡처라는 두 가지 이벤트 전파 방법이 있습니다.

이벤트 전파는 이벤트가 발생할 때 요소 순서를 정의하는 방법입니다. <div> 요소 내에 <p> 요소가 있고 사용자가 <p> 요소를 클릭하면 어떤 요소의 "click"이벤트가 먼저 처리되어야합니까?

에서 버블 링 내부 대부분의 요소의 이벤트는 먼저 다음 외부 처리됩니다의 <p> 요소의 클릭 이벤트가 먼저 다음 <DIV> 요소의 클릭 이벤트를 처리합니다.

에서는 촬상 가장 외부 요소의 경우 1 및 그 내부 처리 다음 <div> 요소의 클릭 이벤트가 제 다음 <p> 요소의 클릭 이벤트를 처리한다.

addEventListener () 메소드를 사용하면 "useCapture"매개 변수를 사용하여 전파 유형을 지정할 수 있습니다.

### The removeEventListener() method

### Browser Support

### HTML DOM Event Object Reference



