---
layout: default
title: Objects
parent: Objects
grand_parent: JavaScript
nav_order: 4
---

# Objects Objects
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Display Objects

### How to Display JavaScript Objects?

JavaScript 객체를 표시하면 [object Object] 가 출력됨

<div class="code-example" markdown="1">
<p id="demo"></p>

<script>
var person = {name:"John", age:30, city:"New York"};

document.getElementById("demo").innerHTML = person;
</script>
</div>
```html
<p id="demo"></p>

<script>
var person = {name:"John", age:30, city:"New York"};

document.getElementById("demo").innerHTML = person;
</script>
```

1. Object Properties by name
1. Object Properties in a Loop
1. Object using Object.values()
1. Object using JSON.stringify()

위의 4가지 방법으로 출력할 수 있음

### Displaying Object Properties

**객체.이름으로 출력하기**

예제
{: .label .label-purple .mt-3}
```js
var person = {name:"John", age:30, city:"New York"};

document.getElementById("demo").innerHTML =
person.name + "," + person.age + "," + person.city;
```

### Displaying the Object in a Loop

**루프로 출력**

루프에서 x 는 변수 이기 때문에 person [x] 를 사용해야 함

예제
{: .label .label-purple .mt-3}
```js
var x, txt = "";
var person = {name:"John", age:30, city:"New York"};

for (x in person) {
txt += person[x] + " ";
};

document.getElementById("demo").innerHTML = txt;
```

### Using Object.values()

**`Object.values()`로 객체를 배열로 변환**

키는 없어지고 값만 배열로 남음

예제
{: .label .label-purple .mt-3}
```js
var person = {name:"John", age:50, city:"New York"};

var myArray = Object.values(person);
document.getElementById("demo").innerHTML = myArray;
```

### Using JSON.stringify()

`JSON.stringify()` 함수를 사용하여 모든 객체를 문자열화 (문자열로 변환) 할 수 있음

**결과는 JSON 표기법에 따른 문자열**

JSON.stringify()는 JavaScript에 포함되어 있으며 모든 주요 브라우저에서 지원됨

예제
{: .label .label-purple .mt-3}
```js
var person = {name:"John", age:30, city: "New York"};

var myString = JSON.stringify(person);
document.getElementById("demo").innerHTML = myString;
// { "name": "John", "age": 50, "city": "New York"}
```

#### Stringify Dates

날짜를 문자열로 변환

예제
{: .label .label-purple .mt-3}
```js
var person = {name:"John", today:new Date()};

var myString = JSON.stringify(person);
document.getElementById("demo").innerHTML = myString;
```

### Stringify Functions

**함수를 문자열화 하지 않고 없애버림**

스트링 화하기 전에 함수를 문자열로 변환하면 없애지 않고 표시해줌

예제
{: .label .label-purple .mt-3}
```js
var person = {name:"John", age:function () {return 30;}};

var myString = JSON.stringify(person);
document.getElementById("demo").innerHTML = myString;
//{"name":"John"}

or

var person = {name:"John", age:function () {return 30;}};
person.age = person.age.toString();

var myString = JSON.stringify(person);
document.getElementById("demo").innerHTML = myString;
//{"name":"John","age":"function () {return 30;}"}
```

### Stringify Arrays

**배열을 문자열화**

예제
{: .label .label-purple .mt-3}
```js
var arr = ["John", "Peter", "Sally", "Jane"];

var myString = JSON.stringify(arr);
document.getElementById("demo").innerHTML = myString;
//["John","Peter","Sally","Jane"]
```

