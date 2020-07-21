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

### Using Built-In Methods

String 객체의 메서드 `toUpperCase()`를 사용하여 텍스트를 대문자로 변환

예제
{: .label .label-purple .mt-3}
```js
var message = "Hello world!";
var x = message.toUpperCase();
// x = HELLO WORLD!
```

### Adding a Method to an Object

**객체에 메소드 추가**

예제
{: .label .label-purple .mt-3}
```js
person.name = function () {
  return this.firstName + " " + this.lastName;
};
```

