---
layout: default
title: Syntax
parent: JSON
grand_parent: JavaScript
nav_order: 1
---

# JSON Syntax
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Syntax

### JSON Syntax Rules

JSON 구문은 **JavaScript 구문의 하위 집합**

JSON 구문은 JavaScript 객체 표기법 구문에서 파생

&#9656; 데이터가 이름 / 값 쌍에 있음

&#9656; 데이터는 쉼표로 구분

&#9656; 중괄호는 객체를 고정

&#9656; 대괄호는 배열을 보유

### A Name and a Value

JSON 데이터는 이름 / 값 쌍으로 작성

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
field name(in double quotes) : value
</div>
```json
"name":"John"
```

!note
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
JavaScript 이름은 그렇지 않지만, JSON 이름에는 큰 따옴표가 필요
</div>

### Evaluates to JavaScript Objects

**JSON 형식은 JavaScript 객체와 거의 동일함**

JSON에서 `Key`는  **큰 따옴표로 작성된 문자열**이어야함

```json
{ "name":"John" }
```

JavaScript에서 키는 문자열, 숫자 또는 식별자 이름일 수 있음

```js
{ name:"John" }
```

### JSON Values

JSON의 value 데이터의 종류

* string
* number
* object (JSON object)
* array
* boolean
* null

자바 스크립트에서는 위 값을 포함해서

* function
* date
* undefined

와 같은 유효한 JavaScript 표현식을 모두 value 값으로 지정할 수 있음

### JSON Uses JavaScript Syntax

JSON 구문은 JavaScript 객체 표기법에서 파생되므로 JavaScript 내에서 JSON으로 작업하는데에는 약간의 추가 소프트웨어가 필요함

JavaScript를 사용하면 다음과 같이 객체를 만들고 데이터를 할당 할 수 있음

예제
{: .label .label-purple .mt-3}
<div class="code-example" markdown="1">
<p>Access a JavaScript object</p>

<p id="demo1"></p>
<p id="demo2"></p>

<p>modify a JavaScript object</p>

<p id="demo3"></p>
<p id="demo4"></p>

<script>
var myObj, x;
myObj = { name: "John", age: 30, city: "New York" };
    
x1 = myObj.name;
x2 = myObj["name"];

myObj.age = "18"
myObj["city"] = "California"

document.getElementById("demo1").innerHTML = x1;
document.getElementById("demo2").innerHTML = x2;

document.getElementById("demo3").innerHTML = myObj.name;
document.getElementById("demo4").innerHTML = myObj.city;
</script>
</div>
```html
<p>Access a JavaScript object</p>

<p id="demo1"></p>
<p id="demo2"></p>

<p>modify a JavaScript object</p>

<p id="demo3"></p>
<p id="demo4"></p>

<script>
var myObj, x;
myObj = { name: "John", age: 30, city: "New York" };
    
x1 = myObj.name;
x2 = myObj["name"];

myObj.age = "18"
myObj["city"] = "California"

document.getElementById("demo1").innerHTML = x1;
document.getElementById("demo2").innerHTML = x2;

document.getElementById("demo3").innerHTML = myObj.name;
document.getElementById("demo4").innerHTML = myObj.city;
</script>
```

### JavaScript Arrays as JSON

JavaScript 객체를 JSON으로 사용하는 것과 같은 방법으로 JavaScript 배열을 JSON으로 사용할 수도 있음

[뒤에서 자세하게 설명]()

### JSON Files

JSON 파일의 파일 형식 : **.json**

JSON 텍스트의 MIME 유형 : **application / json**
