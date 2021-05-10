---
layout: default
title: Methods
parent: Objects
grand_parent: JavaScript
nav_order: 3
---

# Objects Methods
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## JavaScript Methods

### Object Methods

**Methods : 객체에서 수행할 수 있는 함수**

&#9656; 메소드는 속성으로 저장된 함수라고 보면 됨

&#9656; 객체 속성은 기본 값, 다른 객체 및 함수가 될 수 있음

예시
{: .label .label-purple .mt-2}
<div class="code-example" markdown="1">
| Property      | Property Value                                                |
|:--------------|:--------------------------------------------------------------|
| firstName     | John                                                          |
| fullName      | function() {return this.firstName + " " + this.lastName;}     |
</div>
```js
var person = {
  firstName: "John",
  fullName : function() {
    return this.firstName + " " + this.lastName;
  }
};
```

### Accessing Object Methods

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
1. objectName.methodName()

2. name = person.fullName();

&#9656; ()없이 사용하면 함수 정의를 불러옴
</div>
```js
var person = {
  firstName: "Kwon",
  lastName: "Grace",
  fullName : function() {
    return this.firstName + " " + this.lastName;
  }
};

function change(){
    document.getElementById("a").innerHTML = person.fullName()
}
```

### Adding a Method to an Object

**객체에 새로운 메소드 생성하기**

예제
{: .label .label-purple .mt-3}
```js
var person = {
  firstName: "John",
  lastName : "Doe",
  id     : 5566,
};
person.name = function() {
  return this.firstName + " " + this.lastName;
};

document.getElementById("demo").innerHTML =
"My father is " + person.name(); 
```

### Using Built-In Methods

객체의 내장 메소드를 이용하기

예제
{: .label .label-purple .mt-3}
<div class="code-example" markdown="1">
String 객체의 메서드 `toUpperCase()`를 사용하여 텍스트를 대문자로 변환
</div>
```js
var message = "Hello world!";
var x = message.toUpperCase();
// x = HELLO WORLD!
```

