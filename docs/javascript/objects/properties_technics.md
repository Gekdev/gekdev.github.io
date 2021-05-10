---
layout: default
title: Properties and Technics
parent: Objects
grand_parent: JavaScript
nav_order: 1
---

# Object Properties and Technics
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

### Object Properties

**Property(name) + Property Value(volvo) = Properties**

### Accessing Object Properties

1. objectName.propertyName

2. objectName["propertyName"]

예제
{: .label .label-purple .mt-3}
<div class="code-example" markdown="1">
<div id="a"></div>
<div id="b"></div>

<script>
var person = {
  firstName: "John",
  lastName : "Doe",
  id     :  5566
};

document.getElementById("a").innerHTML = person.firstName
document.getElementById("b").innerHTML = person["lastName"]
</script>
</div>
```html
<div id="a"></div>
<div id="b"></div>

<script>
var person = {
  firstName: "John",
  lastName : "Doe",
  id     :  5566
};

document.getElementById("a").innerHTML = person.firstName
document.getElementById("b").innerHTML = person["lastName"]
</script>
```

### Object Methods

**Methods : 객체에서 수행할 수 있는 함수**

메소드는 속성으로 저장된 함수라고 보면 됨

| Property      | Property Value                                                |
|:--------------|:--------------------------------------------------------------|
| firstName     | John                                                          |
| fullName      | function() {return this.firstName + " " + this.lastName;}     |

```js
var person = {
  firstName: "John",
  fullName : function() {
    return this.firstName + " " + this.lastName;
  }
};
```

### Accessing Object Methods

1. objectName.methodName()

2. name = person.fullName();

()없이 사용하면 함수 정의를 불러옴

예제
{: .label .label-purple .mt-3}
<div class="code-example" markdown="1">
<div id="a" onclick="change()">Click here!</div>
<script>
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
</script>
</div>
```html
<div id="a" onclick="change()">Click here!</div>
<script>
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
</script>
```

Do Not Declare Strings, Numbers, and Booleans as Objects!
{: .label .label-red .mt-3}
<div class="code-exmaple" markdown="1">
When a JavaScript variable is declared with the keyword `new`, the variable is created as an object

this code slow down your execution speed
</div>
```js
var x = new String();        // Declares x as a String object
var y = new Number();        // Declares y as a Number object
var z = new Boolean();       // Declares z as a Boolean object
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

#### Using an Object Literal

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

#### Using the JavaScript Keyword new

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

