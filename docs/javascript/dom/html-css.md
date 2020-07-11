---
layout: default
title: HTML & CSS 
parent: HTML DOM
grand_parent: JavaScript
nav_order: 2
--- 

# HTML DOM - Changing HTML and CSS
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Changing HTML

### HTML Output Stream

document.write()로 **출력 스트림**에 바로 적을 수 있음

Note!
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
document.write()문서를 넣은 후에는 사용하면 안됨. 문서를 덮어 써서 전에 로드된 웹 페이지가 사라짐
</div>

### HTML Content

**HTML 내용 변경하는 가장 쉬운 방법**

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
document.getElementById(id).innerHTML = new HTML
</div>
```js
document.getElementById("p1").innerHTML = "New text!";
```

### Value of an Attribute

**속성 값 변경**

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
document.getElementById(id).attribute = new value
</div>
```js
document.getElementById("myImage").src = "landscape.jpg";
```

---

## Changing CSS

### HTML Style

**스타일 변경**

스타일 객체를 통해 변경

<span class="fs-2">
[스타일 객체 속성 더 확인하기](https://www.w3schools.com/js/js_htmldom_css.asp){: .btn  .btn-outline .mt-2}
</span>

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
document.getElementById(id).style.property = new style
</div>
```js
document.getElementById("p2").style.color = "blue";
```

### Using Events

**이벤트가 발생됬을때 코드를 실행할 수 있음**

요소에 무슨 일이 발생하면 웹 브라우저는 EVENT를 발생시킴

[Event]()에서 더욱 자세하게 알 수 있음

---

## HTML DOM Animation

### Animation Code

JavaScript 애니메이션은 요소 스타일의 점진적인 변화를 프로그래밍하여 수행됨

변경된 값은 타이머에 의해 호출되고, 타이머 시간 간격이 작으면 연속적으로 보임

기본 코드
{: .label .mt-2}
```js
var id = setInterval(frame, 5);

function frame() {
  if (/* test for finished */) {
    clearInterval(id);
  } else {
    /* code to change the element style */ 
  }
}
```

예제
{: .label .label-purple .mt-3}
```js
function myMove() {
  var elem = document.getElementById("animate");
  var pos = 0;
  var id = setInterval(frame, 5);
  function frame() {
    if (pos == 350) {
      clearInterval(id);
    } else {
      pos++;
      elem.style.top = pos + 'px';
      elem.style.left = pos + 'px';
    }
  }
}
```

