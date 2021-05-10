---
layout: default
title: Prototypes
parent: Objects
grand_parent: JavaScript
nav_order: 5
---

# Objects Prototypes
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Prototype Basic

**모든 JavaScript 객체는 프로토 타입의 속성과 메서드를 상속**

### Prototype Inheritance

**자바스크립트는 프로토타입 기반 언어**, 클래스가 없어서 프로토타입으로 상속 기능을 흉내내며 작동함

&#9656; ECMA6 표준에서는 Class 문법이 추가되었지만 클래스 기반으로 바뀐건 아님

&#9656; **Object.prototype**은 모든 프로토 타입 상속 체인의 상단에 존재

&#9656; Date 객체는 Date.prototype, Array 객체는 Array.prototype, Person 객체는 Person.prototype에서 메소드와 속성을 상속받음

---

## Adding Properties and Methods to Objects

### Using the prototype Property

속성과 메소드 모두 같은 방식으로 넣을 수 있음

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
arr.prototype.name = value;
</div>
```js
function Person(first, last, age, eyecolor) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eyecolor;
}

Person.prototype.nationality = "English";   //속성넣기

Person.prototype.name = function() {        //메소드 넣기 
  return this.firstName + " " + this.lastName;
};

var myFather = new Person("John", "Doe", 50, "blue");
document.getElementById("demo").innerHTML =
"The nationality of my father is " + myFather.nationality; 
// result is The nationality of my father is English

var myFather = new Person("John", "Doe", 50, "blue");
document.getElementById("demo").innerHTML =
"My father is " + myFather.name(); 
// result is My father is John Doe
```

---

## Prototype Advanced

### Reference

[Javascript 기초 - Object prototype 이해하기](http://insanehong.kr/post/javascript-prototype/)

[Javascript 프로토타입 이해하기](https://medium.com/@bluesh55/javascript-prototype-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-f8e67c286b67)
