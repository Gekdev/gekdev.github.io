---
layout: default
title: Constructors
parent: Objects
grand_parent: JavaScript
nav_order: 4
---

# Objects Constructors
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Object Blueprints Constructors

동일한 "유형"의 많은 객체를 생성하기 위해 "청사진"이 필요하기 때문에 객체 유형을 생성하기 위해서 객체 생성자 함수를 사용해야 함

동일한 유형의 객체는 new 키워드와 함께 생성자 함수를 호출해 생성함

### The this Keyword

JavaScript에서 호출되는 것은 this코드를 "소유"하는 객체

this의 값은 객체로 사용될때는 객체 그 자체를 말함

생성자 함수(constructor function) this에는 값이 없고 새 객체를 대체하는것, this새 개체를 만들때의 값은 새 개체가 됨

!note
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
this는 키워드이기 때문에 값을 변경할 수 없음
</div>

### Adding a Property to an Object

**기존 객체에 새 속성을 추가**

객체가 생성된 후 속성을 추가하는건 괜찮지만 객체 생성자에 새 속성 생성은 안됨

예제
{: .label .label-purple .mt-2}
```js
// Constructor function for Person objects
function Person(first, last, age, eye) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eye;
}

// Create 2 Person objects
var myFather = new Person("John", "Doe", 50, "blue");
var myMother = new Person("Sally", "Rally", 48, "green");

// Add nationality to first object
myFather.nationality = "English";

// Display nationality 
document.getElementById("demo").innerHTML =
"My father is " + myFather.nationality;   

//결과값은 My father is English
```

### Adding a Method to an Object

**기존 객체에 새로운 메소드를을 추가**

예제
{: .label .label-purple .mt-2}
```js
// Constructor function for Person objects
function Person(first, last, age, eye) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eye;
}

// Create 2 Person objects
var myFather = new Person("John", "Doe", 50, "blue");
var myMother = new Person("Sally", "Rally", 48, "green");

// Add a name method to first object
myFather.name = function() {
  return this.firstName + " " + this.lastName;
};

// Display full name
document.getElementById("demo").innerHTML =
"My father is " + myFather.name(); 
// 결과값은 My father is John Doe
```

### Adding a Property to a Constructor

★★ 기존 객체에 새 속성을 추가하는 것과 같은 방식으로 객체 생성자에 따로 새 속성을 추가 할 수 없고 직접 안에 적어야함!

<span class="fs-2">
[W3School](https://www.w3schools.com/js/tryit.asp?filename=tryjs_object_constructor4){: .btn .btn-outline .mt-2}
</span>

### Adding a Method to a Constructor

**생성자 함수는 메소드를 정의 할 수도 있음**

★★ 기존 객체에 새 메소드를 추가하는 것과 같은 방식으로 객체 생성자에 따로 새 메소드를 추가 할 수 없고 직접 안에 적어야함!

<span class="fs-2">
[W3School](https://www.w3schools.com/js/tryit.asp?filename=tryjs_object_constructor7){: .btn .btn-outline .mt-2}
</span>

### Built-in JavaScript Constructors

JavaScript에는 기본 객체에 대한 생성자가 내장되어 있음

&#9656; var x1 = new Object();    // A new Object object

&#9656; var x2 = new String();    // A new String object

&#9656; var x3 = new Number();    // A new Number object

&#9656; var x4 = new Boolean();   // A new Boolean object

&#9656; var x5 = new Array();     // A new Array object

&#9656; var x6 = new RegExp();    // A new RegExp object

&#9656; var x7 = new Function();  // A new Function object

&#9656; var x8 = new Date();      // A new Date object

note!
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
Math는 전역 객체이기 때문에 new키워드를 사용할 수 없음
</div>

★ 자바 스크립트는 기본 데이터 형의 객체 버전이 String, Number하고 Boolean이기 때문에 복잡한 객체를 만들 이유가 없음 (기본 값이 훨씬 빠름)

예제
{: .label .label-purple .mt-2}
```js
var x1 = {};            // new object
var x2 = "";            // new primitive string
var x3 = 0;             // new primitive number
var x4 = false;         // new primitive boolean
var x5 = [];            // new array object
var x6 = /()/           // new regexp object
var x7 = function(){};  // new function object
```
