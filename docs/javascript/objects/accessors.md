---
layout: default
title: Accessors
parent: Objects
grand_parent: JavaScript
nav_order: 5
---

# Objects Accessors
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## JavaScript Accessors (Getters and Setters)

ECMAScript 5 (2009)는 Getter and Setter를 도입함

Getters and setters를 사용하면 **개체 접근자(계산 된 속성)를 정의 할 수 있음**

### JavaScript Getter (The get Keyword)

이 예제는 lang속성 get 값에 language 속성을 사용 

예제
{: .label .label-purple .mt-3}
```js
// Create an object:
var person = {
  firstName: "John",
  lastName : "Doe",
  language : "en",
  get lang() {
    return this.language;
  }
};

// Display data from the object using a getter:
document.getElementById("demo").innerHTML = person.lang;
```

### JavaScript Setter (The set Keyword)

이 예제는 lang속성 set 값에 language 속성을 사용

예제
{: .label .label-purple .mt-3}
```js
var person = {
  firstName: "John",
  lastName : "Doe",
  language : "",
  set lang(lang) {
    this.language = lang;
  }
};

// Set an object property using a setter:
person.lang = "en";

// Display data from the object:
document.getElementById("demo").innerHTML = person.language;
```

### JavaScript Function or Getter?

예제: function
{: .label .label-purple .mt-3}
```js
var person = {
  firstName: "John",
  lastName : "Doe",
  fullName : function() {
    return this.firstName + " " + this.lastName;
  }
};

// Display data from the object using a method:
document.getElementById("demo").innerHTML = person.fullName();
```

예제: getter
{: .label .label-purple .mt-3}
```js
var person = {
  firstName: "John",
  lastName : "Doe",
  get fullName() {
    return this.firstName + " " + this.lastName;
  }
};

// Display data from the object using a getter:
document.getElementById("demo").innerHTML = person.fullName;
```

&#8594; getter가 더 간단한 구문을 제공

### Why Using Getters and Setters?

1. 더 간단한 구문을 제공
2. 속성과 메소드에 대해 동일한 구문을 허용
3. 더 나은 데이터 품질을 보장 할 수 있음
4. 비하인드 스토리를 수행하는 데 유용함
5. getters and setters를 사용할 때 더 나은 데이터 품질을 보장

### Object.defineProperty()

`Object.defineProperty()`를 사용해 Getter 및 Setter를 추가 할 수도 있음

예제
{: .label .label-purple .mt-3}
<div class="code-example" markdown="1">
<p id="demo"></p>

<script>
// Define an object
var obj = {counter : 0};

// Define Setters and Getters
Object.defineProperty(obj, "reset", {
  get : function () {this.counter = 0;}
});
Object.defineProperty(obj, "increment", {
  get : function () {this.counter++;}
});
Object.defineProperty(obj, "decrement", {
  get : function () {this.counter--;}
});
Object.defineProperty(obj, "add", {
  set : function (value) {this.counter += value;}
});
Object.defineProperty(obj, "subtract", {
  set : function (value) {this.counter -= value;}
});

// Play with counter:
obj.reset;
obj.add = 5;
obj.subtract = 1;
obj.increment;
obj.decrement;
document.getElementById("demo").innerHTML = obj.counter;
</script>
</div>
```js
<p id="demo"></p>

<script>
// Define an object
var obj = {counter : 0};

// Define Setters and Getters
Object.defineProperty(obj, "reset", {
  get : function () {this.counter = 0;}
});
Object.defineProperty(obj, "increment", {
  get : function () {this.counter++;}
});
Object.defineProperty(obj, "decrement", {
  get : function () {this.counter--;}
});
Object.defineProperty(obj, "add", {
  set : function (value) {this.counter += value;}
});
Object.defineProperty(obj, "subtract", {
  set : function (value) {this.counter -= value;}
});

// Play with counter:
obj.reset;
obj.add = 5;
obj.subtract = 1;
obj.increment;
obj.decrement;
document.getElementById("demo").innerHTML = obj.counter;
</script>
```

### Browser Support

Internet Explorer 8 이전 버전에서는 Getter 및 Setter가 지원되지 않음