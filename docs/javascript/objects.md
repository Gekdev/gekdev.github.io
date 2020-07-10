---
layout: default
title: Objects
parent: JavaScript
nav_order: 11
has_children: true
---

# JavaScript Objects
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Objects

### Object Definition

objects can contain many values

values are written as **name:value** pairs (name and value separated by a colon)

objects are containers for named values called properties or methods

object literal로 객체 생성하기
{: .label .mt-3 }
```js
var person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};

or

var person = {
  firstName: "John",
  lastName: "Doe",
  age: 50,
  eyeColor: "blue"
};
//object definition can span multiple lines
```

### Object Properties

name:values pairs are called properties

Property : name

+

Property Value : volvo

= Properties

### Accessing Object Properties

<div class="code-exmaple" markdown="1">
1. objectName.propertyName

2. objectName["propertyName"]
</div>

### Object Methods

Methods : **actions that can be performed on objects**

Methods are stored in properties as function definitions. (A method is a function stored as a property)

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

<div class="code-exmaple" markdown="1">
1. objectName.methodName()

2. name = person.fullName();

()없이 사용하면 함수 정의를 불러옴
</div>


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
 