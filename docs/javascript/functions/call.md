---
layout: default
title: Call
parent: Functions
grand_parent: JavaScript
nav_order: 2
---

# Functions Call
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Method Reuse

### All Functions are Methods

**모든 함수는 메소드**

함수가 자바스크립트 객체의 메소드가 아니라면, 전역 객체(window)의 함수가 됨



### The this Keyword

### The JavaScript call() Method

call() 메소드는 자바스크립트의 미리 정의된 메소드

**소유자 객체를 인수로 사용하여 메소드를 호출**하는 데 사용할 수 있음

call()을 사용하면 **객체가 다른 객체에 속하는 메소드를 사용할 수 있음**

예제
{: .label .label-purple .mt-3}
```js
var person = {
  fullName: function() {
    return this.firstName + " " + this.lastName;
  }
}
var person1 = {
  firstName:"John",
  lastName: "Doe"
}
var person2 = {
  firstName:"Mary",
  lastName: "Doe"
}

person.fullName.call(person1);  // "John Doe"
person.fullName.call(person2);  // "Mary Doe"
```

### The call() Method with Arguments

call()메소드는 인수를 받음

예제
{: .label .label-purple .mt-3}
```js
var person = {
  fullName: function(city, country) {
    return this.firstName + " " + this.lastName + "," + city + "," + country;
  }
}
var person1 = {
  firstName:"John",
  lastName: "Doe"
}
person.fullName.call(person1, "Oslo", "Norway"); // John Doe,Oslo,Norway
```

