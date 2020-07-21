---
layout: default
title: Objects
parent: JavaScript
nav_order: 5
has_children: true
---

# JavaScript Objects Basic 
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Objects Basic 

### Object Syntax

객체는 많은 값을 담을 수 있음, 속성이나 메소드의 컨테이너라고 생각하면 됨

값은 주로 **name:value** 쌍으로 나타남 (name and value separated by a colon)

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
 