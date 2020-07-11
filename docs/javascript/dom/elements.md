---
layout: default
title: Elements 
parent: HTML DOM
grand_parent: JavaScript
nav_order: 1
--- 

# HTML DOM Elements
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Finding HTML Elements

요소를 조작하기 위해서는 먼저 찾아야함

요소를 찾는데에는 5가지 방법이 있음

### by Id

**id로 요소 찾기**

가장 쉽고 많이 이용하는 방식, 한개의 요소만 가져올 수 있음

요소가 발견되면 메소드는 요소를 변수의 객체로 리턴

요소를 찾을 수 없으면 `null`

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var a0 = document.getElementById("id");
</div>
```js
var myElement = document.getElementById("intro");
```

### by Tag Name

**태그 이름으로 요소 찾기**

여러가지 요소를 가지고 올 수 있음, 변수에는 요소(들)를 배열 형식으로 가져옴

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var a1 = document.getElementsByTagName("tagname");
</div>
```js
var x = document.getElementsByTagName("p");

var x = document.getElementById("main");
var y = x.getElementsByTagName("p");
//요소 main id를 찾은 후 그 자식들 p태그 찾기
```

### by Class Name

**클래스 이름으로 요소 찾기**

여러가지 요소를 가지고 올 수 있음, 변수에는 요소(들)를 배열 형식으로 가져옴

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var a1 = document.getElementsByClassName("class");
</div>
```js
var x = document.getElementsByClassName("intro");
```

Note!
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
does not work in Internet Explorer 8 and earlier versions
</div>

### by CSS Selectors

**CSS 선택자를 이용해서 요소 찾기**

querySelectorAll() 메소드 사용

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var x = document.querySelectorAll("CSS selector");
</div>
```js
var x = document.querySelectorAll("p.intro");
```

Note!
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
does not work in Internet Explorer 8 and earlier versions
</div>

### by HTML Object Collections

**요소를 배열 형식으로 가져온 변수 출력**

예제
{: .label .label-purple .mt-2}
```js
var x = document.forms["frm1"];
var text = "";
var i;
for (i = 0; i < x.length; i++) {
  text += x.elements[i].value + "<br>";
}
document.getElementById("demo").innerHTML = text;
```

&#8594; form안에 있는 요소들을 x 변수에 모두 담고 하나한 출력한 것

&#8594; x.elements[i].value와 x[i]는 같음

