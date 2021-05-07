---
layout: default
title: Complex Data
parent: Data types
grand_parent: JavaScript
nav_order: 2
---

# JavaScript Data types
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Complex Data

### Arrays

**배열**

&#9656; square brackets `[]`로 쓰임

&#9656; 아이템들은 ,로 구별됨

&#9656; 0부터 시작

```js
var cars = ["Saab", "Volvo", "BMW"];
```

### Objects

**객체**

&#9656; curly braces `{}` 로 쓰임

&#9656; name:value 짝으로 사용되고 ,로 구별됨

```js
var person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};
```

### null

**nothing, something that doesn't exist**

&#9656; data type : object

&#9656; 대소문자 구분해서 사용해야함 소문자 null만 가능

&#9656; 객체를 비우기위해 null이라고 지정해줄 수 있음 (undefined와 비슷한 느낌으로)

```js
var person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};
person = null;    // Now value is null, but type is still an object
```

&#9656; 비우는게 목적이라면 primitive data의 undefined도 있지만 객체의 값과 속성이 달라짐

```js
var person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};
person = undefined;   // Now both value and type is undefined
```
	
Difference Between Undefined and Null
{: .label .mt-3 }
<div class="code-example" markdown="1">
**equal value but different type**

typeof undefined           // undefined
typeof null                // object

null === undefined         // false
null == undefined          // true
</div>
