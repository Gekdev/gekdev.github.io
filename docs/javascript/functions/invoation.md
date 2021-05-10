---
layout: default
title: Invocation
parent: Functions
grand_parent: JavaScript
nav_order: 2
---

# Functions Invocation
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Invocation

### Function Invocation

무엇인가가 함수를 호출해야지 함수는 실행됨

&#9656; 함수이름과 `()` operator가 특정 함수를 호출함

&#9656; 함수 이름만 호출하면 함수 객체를 가져옴

### Invoking a JavaScript Function

&#9656; "call upon a function", "start a function", or "execute a function" 모두 같은 말

&#9656; JavaScript **function can be invoked without being called**

#### 함수가 호출되는 경우

* When an event occurs (when a user clicks a button)

* When it is invoked (called) from JavaScript code

* Automatically (self invoked)

### Invoking a Function as a Function

함수가 항상 객체에 속하는건 아니지만, **자바스크립트에는 항상 기본 전역 객체가 있음**

HTML에서 **기본 전역 객체는 HTML 페이지 자체**이므로, HTML에서 쓰인 자바스크립트의 함수는 **HTML 페이지에 속하게 됨**, 또한 브라우저에서의 **페이지 객체는 브라우저 윈도우**라서 함수들은 **자동적으로 윈도우 객체의 함수가 됨**

&#8594; 따라서 myFunction()과 window.myFunction()는 같음

예제
{: .label .label-purple .mt-3}
```js
function myFunction(a, b) {
  return a * b;
}
myFunction(10, 2);           // Will return 20
```

!note
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
전역 변수, 메소드 또는 함수는 전역 객체에서 이름 충돌 및 버그를 쉽게 만들 수 있음
</div>

#### The this Keyword

**`this`는 현재 코드를 소유하는 객체를 나타냄** 따라서 함수에서 `this`는 함수를 소유하고 있는 객체를 나타냄

<span class="fs-2">
[JS this Keyword](https://www.w3schools.com/js/js_this.asp){: .btn  .btn-outline .mt-2}
</span>

#### The Global Object

소유자 객체없이 함수를 호출하면 값 `this` 가 전역 객체가 됨

**웹 브라우저에서 글로벌 오브젝트는 브라우저 창**

예제
{: .label .label-purple .mt-3}
```js
var x = myFunction();            // x = [object Window]

function myFunction() {
  return this;  
}
```

!note
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
Using the window object as a variable can easily crash your program
</div>

### Invoking a Function as a Method

**함수를 메소드로 선언할 수 있음**

예제
{: .label .label-purple .mt-3}
```js
var myObject = {
  firstName:"John",
  lastName: "Doe",
  fullName: function () {
    return this.firstName + " " + this.lastName;
  }
}
myObject.fullName();         // Will return "John Doe"
```

&#8594; fullName이 함수, myObject가 객체이자 함수의 소유자 객체

&#8594; `this`는 소유자 객체를 나타내는 말이니 myObject가 됨

### Invoking a Function with a Function Constructor

**함수 호출 앞에 `new` 키워드가 있으면 생성자 호출**

새 함수를 만드는 것처럼 보이지만 JavaScript 함수는 객체이므로 실제로 새 객체를 만드는 것

**새 객체는 생성자에서 속성과 메서드를 상속함**

예제
{: .label .label-purple .mt-3}
```js
// This is a function constructor:
function myFunction(arg1, arg2) {
  this.firstName = arg1;
  this.lastName  = arg2;
}

// This creates a new object
var x = new myFunction("John", "Doe");
x.firstName;                             // Will return "John"
```

