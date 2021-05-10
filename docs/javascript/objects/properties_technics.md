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

**Property(name) + Property(value) = Properties**

&#9656; **JavaScript객체는 정렬되지 않은 속성의 모음**

&#9656; 속성은 JavaScript 개체와 관련된값

&#9656; 속성은 일반적으로 변경, 추가 및 삭제할 수 있지만 일부는 읽기 전용임

&#9656; 값(value)은 Property의 attributes 중 하나

&#8594; (다른 attributes : enumerable, configurable, and writable)

&#9656; 이 attributes들은 속성들이 어떻게 접근될 수 있는지 정의함

&#9656; 자바스크립트에서는 모든 attributes들은 읽을 수 있지만 value attribute만 값이 바뀔 수 있음

---

## Object Technics

### Simple Way to Creating Object 

**{}로 생성함** (객체를 만드는 가장 쉬운 방법)

&#9656; 값은 주로 **name:value** 쌍으로 나타남 (name and value separated by a colon)

&#9656; 객체 리터럴을 사용하면 한 명령문에서 객체를 정의하고 만들 수 있음

&#9656; 객체 리터럴은 중괄호 ({}) 안에 이름 : 값 쌍의 목록

&#9656; 공백과 줄 바꿈은 중요하지 않음. 객체 정의는 여러 줄에 걸쳐있을 수 있음

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
object literal로 객체생성

**var objectName = {name:value, name:value...}**
</div>
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
//object definition can span multiple lines
```
#### 4 ways to creating a JavaScript Object

새 객체를 만드는 방법에는 네가지 방법이 있음

1. 객체 리터럴을 사용하여 단일 객체를 정의하고 만들기

2. 키워드를 사용하여 단일 객체를 정의하고 만들기 `new`

3. 객체 생성자를 정의한 다음 생성 된 유형의 객체를 만들기

4. ECMAScript 5에서 함수를 사용하여 객체를 만들 수도 있음 `Object.create()`

Using the JavaScript Keyword new
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
위 객체 리터럴을 사용하는 것과 거의 같기 때문에 `new Object()`를 사용할 이유가 없음

따라서 **단순성, 가독성 및 실행 속도를 위해서는 첫 번째 (객체 리터럴 방법)를 사용해야함**
</div>
```js
var person = new Object();
person.firstName = "John";
person.lastName = "Doe";
person.age = 50;
person.eyeColor = "blue";
```

### Accessing Object Properties

1. objectName.propertyName

2. objectName["propertyName"]

3. objectName[expression] 

4. objectName.values()

예제
{: .label .label-purple .mt-2}
```js
var person = {
  firstName: "John",
  lastName : "Doe",
  id     :  5566
};

var x = "id"

document.getElementById("a").innerHTML = person.firstName
document.getElementById("b").innerHTML = person["lastName"]
document.getElementById("c").innerHTML = person[x]
```

#### for in loop

**for...in문은 개체의 속성을 반복**

&#9656; for...in루프 내부의 코드 블록은 각 속성에 대해 한 번씩 실행

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
for (variable in object) {
  // code to be executed
}
</div>
```js
var person = {fname:"John", lname:"Doe", age:25};

for (x in person) {
  txt += person[x];
}
//txt : John Doe 25
```

note!
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
You must use person[x] in the loop

person.x will not work (Because x is a variable)
</div>

### Adding new properties

**단순히 값을 제공하여 기존 객체에 새 속성을 추가할 수 있음**

&#9656; 존재하는 객체에 대해 속성을 부여해야 함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
arr.newPropertyName = value;
</div>
```js
person.nationality = "English";
```

### Deleting properties

#### delete keyword

**속성 값과 속성 자체를 모두 삭제**

&#9656; 삭제 후에는 다시 추가하기 전에 속성을 사용할 수 없음

&#9656; object 속성에만 영향을 주고 변수나 함수에는 영향이 없음

&#9656; 미리 정의된 자바스크립트 객체속성에 사용할 수 없음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
delete arr.newPropertyName;
</div>
```js
var person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};
delete person.age;   // or delete person["age"];
// person.age = undefined 
```







































