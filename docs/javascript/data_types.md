---
layout: default
title: Data types
parent: JavaScript
nav_order: 5
has_children: true
---

# JavaScript Data types
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Data type Basic

### The Concept of Data Types

&#9656; 프로그래밍에서 데이터 타입은 중요한 개념

&#9656; 변수를 조작하려면 그 변수가 어떤 데이터 타입인지 알아야 함

&#9656; numbers, strings(text values), object{}, booleans, arrays등이 있음

### Primitive Data

추가적인 속성이나 메소드가 없는 단순한 기본 데이터

string, number, boolean, undefined, empty values가 있음

```js
typeof "John"              // Returns "string"
typeof 3.14                // Returns "number"
typeof true                // Returns "boolean"
typeof false               // Returns "boolean"
typeof x                   // Returns "undefined" (if x has no value)
```

### Complex Data

기본 데이터보다 좀더 복잡한 형식으로 되어있는 데이터들 

function, object (objects, arrays, and null)가 있음

```js
typeof {name:'John', age:34} // Returns "object"
typeof [1,2,3,4]             // Returns "object" (not "array", see note below)
typeof null                  // Returns "object"
typeof function myFunc(){}   // Returns "function"
```

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

---

## Checking Data types

### [The typeof Operator]()

&#8594; 자바스크립트에서 array 는 object인걸 잊지말자

&#8594; function는 object지만 typeof 연산자에서는 function이라고 나옴
