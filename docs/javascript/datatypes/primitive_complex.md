---
layout: default
title: Primitive and Complex
parent: Data types
grand_parent: JavaScript
nav_order: 1
---
 
# Primitive Data
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Primitive Data

### [Strings](https://gekdev.github.io/docs/javascript/strings/)

**series of characters**

&#9656; 작은 따옴표나 큰 따옴표로 사용됨

&#9656; 문장안에 따옴표가 사용될 경우 서로 겹치지 않게 사용해야함

```js
var answer1 = "It's alright";             // Single quote inside double quotes
var answer2 = "He is called 'Johnny'";    // Single quotes inside double quotes
var answer3 = 'He is called "Johnny"';    // Double quotes inside single quotes
```

### [Numbers](https://gekdev.github.io/docs/javascript/numbers/)

**유일한 숫자타입**

&#9656; 소수점 없이 쓸 수 있음

```js
var x1 = 34.00;     // Written with decimals
var x2 = 34;        // Written without decimals
```

### Booleans

**true or false**

&#9656; 조건문을 테스트할때 자주 사용됨

```js
var x = 5;
var y = 5;
var z = 6;
(x == y)       // Returns true
(x == z)       // Returns false
```

### Undefined

변수 선언 직후에는 변수값이 undefined

변수값을 임의로 비우고 싶을때는 undefined로 할당해주면 됨


```js
car = undefined;    // Value is undefined, type is undefined
```

### Empty Values

빈값이지만 빈게 값이고 속성은 문자열임

undefined와 관련이 없음

```js
var car = "";    // The value is "", the typeof is "string"
```

---

## Complex Data

### [Arrays](https://gekdev.github.io/docs/javascript/array/)

**배열**

&#9656; square brackets `[]`로 쓰임

&#9656; 아이템들은 ,로 구별됨

&#9656; 0부터 시작

```js
var cars = ["Saab", "Volvo", "BMW"];
```

### [Objects](https://gekdev.github.io/docs/javascript/objects/)

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

