---
layout: default
title: Declaration
parent: Variable
grand_parent: JavaScript
nav_order: 1
---
 
# Variable Declaration
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Declaring Variables

### Keywords of Variables 

변수를 선언할때 3가지 키워드가 사용됨

var, int, const 

### Hoisting 

**var로 선언된 변수는 항상 게양되어서 먼저 읽혀짐**

&#9656; let이나 const는 안됨

예시
{: .label .label-purple .mt-2}
```js
carName = "Volvo";
alert(carName);
var carName;
```

---

## var Statement(Keyword)

### Definition and Usage

**var 문은 변수를 선언**

&#9656; 변수를 만드는 것을 변수 선언(declaring)이라고 함

&#9656; 값(value)이 없으면 undefined

&#9656; var키워드로 정의된 전역 변수 는 창개체에 속함

```js
var carName = "Volvo";
// code here can use window.carName
```

&#9656; 2015년 이전에는 var키워드를 사용하는 것이 JavaScript 변수를 선언하는 유일한 방법이였음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var varname = value;

&#9656; varname : Required. Specifies the name of the variable

&#9656; value : Optional. Specifies the value to assign to the variable
</div>
```js
var x = 5;
var y = 6;
var z = x + y;
```

Warning
{: .label .label-red .mt-2}
<div class="code-example" markdown="1">
**var키워드로 선언된 변수 는 Block Scope를 가질 수 없음**

&#9656; 블록 {} 내부에서 선언된 변수를 블록 외부에서도 사용가능 

&#9656; 블록 내부의 변수를 다시 선언하면 블록 외부의 변수도 다시 선언

&#8594; ES2015 이전에는 JavaScript에 Block Scope가 없었기 때문에 그럼
</div>
```js
{
  var x = 2;
}
// x CAN be used here
```

---

## let Keyword

**Block Scope의 변수(및 상수)를 제공**

&#8594; ECMAScript 2015에서 나온 새로운 변수 정의 키워드 (ES2015 이전에는 JavaScript에는 전역범위 와 함수범위 라는 두 가지 유형의 범위만 있었음)

differences between var & let
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
공통점 : let은 Function Scope, Global Scope 거의 동일

차이점 : block scope인식 여부, 전역 범위 조건(window.var), 사용가능 버전 여부가 다름
</div>

### Redeclaring is not allowed  

**같은 이름(식별자)으로 두번 이상 선언 불가**

예시
{: .label .label-purple .mt-2}
```js
let x = 2;       // Allowed
let x = 3;       // Not allowed

{
  let x = 4;   // Allowed
  let x = 5;   // Not allowed
}

// 아래와 같은 방법도 안됨 

var x = 2;       // Allowed
let x = 3;       // Not allowed

{
  var x = 4;   // Allowed
  let x = 5   // Not allowed
}
```

### Block Scope

**블록 범위**

&#9656; let키워드로 선언 된 변수는 블록 범위를 가질 수 있음

&#9656; 블록 내부의 변수를 다시 선언해도 블록 외부의 변수는 다시 선언되지 않음

&#9656; ES2015 이전에는 JavaScript에 Block Scope가 없었음

예시
{: .label .label-purple .mt-2}
```js
{
  let x = 2;
}
// x can NOT be used here
```

### Browser Support

Internet Explorer 11, Chrome 49, Edge 12, Firefox 44, Safari 11, Opera 36  이전 버전들에서는 지원하지 않음

---

## Const Keyword

&#9656; Block Scope의 변수(및 상수)를 제공

&#9656; ECMAScript 2015에서 나온 새로운 변수 정의 키워드 (ES2015 이전에는 JavaScript에는 전역범위 와 함수범위 라는 두 가지 유형의 범위만 있었음)

★ let과 거의 동일

### Redeclaring is not allowed  

**같은 이름(식별자)으로 두번 이상 선언 불가**

예시
{: .label .label-purple .mt-2}
```js
const x = 2;       // Allowed
const x = 3;       // Not allowed
x = 3;             // Not allowed
var x = 3;         // Not allowed
let x = 3;         // Not allowed

{
  const x = 2;   // Allowed
  const x = 3;   // Not allowed
  x = 3;         // Not allowed
  var x = 3;     // Not allowed
  let x = 3;     // Not allowed
}
```

### Cannot be reassigned

**변수에 값을 재할당 할 수 없음**

예시
{: .label .label-purple .mt-2}
```js
const PI = 3.141592653589793;
PI = 3.14;      // This will give an error
PI = PI + 10;   // This will also give an error
```

### Assigned when Declared

**선언 될 때 값을 할당해야만 함**

예시
{: .label .label-purple .mt-2}
```js
const PI;
PI = 3.14159265359;
//WRONG, const PI = 3.14159265359;
```

### Not Real Constants

**상수 primitive 값은 변경할 수 없지만 상수 객체의 속성은 변경 가능**

#### Constant Objects can Change

객체를 변경하거나 추가하는건 가능하지만 새로 정의하는건 안됨

예시
{: .label .label-purple .mt-2}
```js
// You can create a const object:
const car = {type:"Fiat", model:"500", color:"white"};
// ERROR : car = {type:"Volvo", model:"EX60", color:"red"};    

// You can change a property:
car.color = "red";

// You can add a property:
car.owner = "Johnson";
```

#### Constant Arrays can Change

상수 배열의 요소를 변경할수 있지만 새로 정의하는건 안됨

예시
{: .label .label-purple .mt-2}
```js
// You can create a constant array:
const cars = ["Saab", "Volvo", "BMW"];
// ERROR : cars = ["Toyota", "Volvo", "Audi"];  

// You can change an element:
cars[0] = "Toyota";

// You can add an element:
cars.push("Audi");
```

### Browser Support

Internet Explorer 10, Chrome 49, IE / Edge 11, Firefox 36, Safari 10, Opera 36 이전 버전들에서는 지원하지 않음
