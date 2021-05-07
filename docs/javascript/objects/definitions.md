---
layout: default
title: Definitions
parent: Objects
grand_parent: JavaScript
nav_order: 1
---

# Objects Definitions
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## JavaScript Objects

**JavaScript에서 거의 모든 것은 객체**

&#9656; 불린값은 객체 일 수 있음 (new키워드로 정의 된 경우)

&#9656; 숫자는 객체가 될 수 있음 (new키워드로 정의 된 경우)

&#9656; 문자열은 객체가 될 수 있음 (new키워드로 정의 된 경우)

&#9656; 날짜는 항상 객체

&#9656; 수학은 항상 객체

&#9656; 정규 표현식은 항상 객체

&#9656; 배열은 항상 객체

&#9656; 함수는 항상 객체

&#9656; 객체는 항상 객체

&#8594; **primitive를 제외한 모든 JavaScript 값은 객체**

### JavaScript Primitives

primitive value는 어떤 특성 또는 메소드가 없는 값

primitive data 타입은 primitive value값을 가짐

1. string
2. number
3. boolean
4. null
5. undefined

기본 값은 변경할 수 없음 (x = 3.14 인 경우 x 값을 변경할 수 있지만 3.14의 값을 변경할 수 없음)


### Objects are Variables

객체는 변수이지만 변수에는 단일 값이 들어갈 수 있지만 객체에는 많은 값이 포함됨

JavaScript 객체는 named values의 모음

값은 name : value pair (이름과 값을 콜론,으로 구분)으로 작성

예제
{: .label .label-purple .mt-3}
```js
var person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};
```

### Object Properties

JavaScript 객체에서 named values을 properties 라고 함

이름 값 쌍으로 작성된 객체는 다음과 유사함

* Associative arrays in PHP
* Dictionaries in Python
* Hash tables in C
* Hash maps in Java
* Hashes in Ruby and Perl

### Object Methods

**메소드는 오브젝트에서 수행 할 수있는 조치**

&#9656; 객체 속성은 기본 값, 다른 객체 및 함수가 될 수 있음

&#9656; 객체 메소드가 있는 객체 속성인 함수

### Creating a JavaScript Object

새 객체를 만드는 방법에는 여러 가지가 있음

1. 객체 리터럴을 사용하여 단일 객체를 정의하고 만들기
2. 키워드를 사용하여 단일 객체를 정의하고 만들기 `new`
3. 객체 생성자를 정의한 다음 생성 된 유형의 객체를 만들기
4. ECMAScript 5에서 함수를 사용하여 객체를 만들 수도 있음 `Object.create()`

### Using an Object Literal

객체를 만드는 가장 쉬운 방법

객체 리터럴을 사용하면 한 명령문에서 객체를 정의하고 만들 수 있음

객체 리터럴은 중괄호 ({}) 안에 이름 : 값 쌍의 목록

공백과 줄 바꿈은 중요하지 않음. 객체 정의는 여러 줄에 걸쳐있을 수 있음

예제
{: .label .label-purple .mt-3}
```js
var person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};
//네 가지 속성으로 새 JavaScript 객체를 만듦

or 

var person = {
  firstName: "John",
  lastName: "Doe",
  age: 50,
  eyeColor: "blue"
};
```

### Using the JavaScript Keyword new

예제
{: .label .label-purple .mt-3}
```js
var person = new Object();
person.firstName = "John";
person.lastName = "Doe";
person.age = 50;
person.eyeColor = "blue";
```

위 객체 리터럴을 사용하는 것과 거의 같기 때문에 `new Object()`를 사용할 이유가 없음

따라서 **단순성, 가독성 및 실행 속도를 위해서는 첫 번째 (객체 리터럴 방법)를 사용해야함**

### JavaScript Objects are Mutable

객체는 변경 가능함

**사본을 생성하지 않고 그 자체가 됨!!**

var x = person;  // 만약 person이 객체라면, x는 person과 같은 객체가 됨(사본이 아님!)

x와 person은 동일한 객체이므로 x를 변경하면 사람도 변경된다

예제
{: .label .label-purple .mt-3}
```js
var person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"}

var x = person;
x.age = 10;           // This will change both x.age and person.age
```

