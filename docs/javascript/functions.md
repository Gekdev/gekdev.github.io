---
layout: default
title: Functions
parent: JavaScript
nav_order: 7
has_children: true
---

# JavaScript Functions
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Basic

### What is Function?

**특정한 일을 수행하기 위한 코드블럭**

&#9656; 어떤 무언가가 함수를 불러야지 실행됨

&#9656; 코드를 한번 정의하고 여러번 사용하기 위해 사용됨

### Function Syntax

Syntax
{: .label}
```js
function functionName(parameters) {
  // code to be executed
}
```

&#9656; 자바스크립트 함수는 **function 키워드로 정의**되고 그다음으로 **이름과 ()가 따라옴**

&#9656; **함수 이름으로는 변수명과 같은 조건으로 사용**됨

&#9656; 매개변수(parameters) 들은  함수 정의에서 **,**로 구분되고 () 안에 존재함

&#9656; 함수에 의해 실행되어야 하는 코드들은 {} 안에 종속됨

&#9656; 인수(arguments)는 함수가 호출될 때 함수가 받는 값, 함수 안에서는 인수 (매개변수)가 지역변수처럼 사용된다

!note
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
함수는 실행문이 아니라서 세미콜론으로 끝나지 않음
</div>

---

## Function Definitions

### Function keyword and Function() Constructor

1. `function` 키워드로 정의

2. `new Function()` 내장 자바스크립트 함수 생성자 - 지양해야함

&#8594; 두 방법 모두 동일하지만 첫번째 방법이 편리하기때문에 더 자주 씀

예제
{: .label .label-purple .mt-3}
```js
1. var myFunction = function (a, b) {return a * b};

2. var myFunction = new Function("a", "b", "return a * b");

var x = myFunction(4, 3);
```

---

## Function Sort 

함수의 종류에는 일반함수, 익명함수, 화살표 함수(익명함수)가 있음

### Basic Function Declarations

함수 선언은 앞서 보인것처럼 아래 문법으로 선언됨

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
function functionName(parameters) { <br>
  // code to be executed            <br>
}                               
</div>
```js
function myFunction(a, b) {
  return a * b;
}
```

### Function Expressions (Anonymous Function)

&#9656; JavaScript 함수는 표현식을 사용하여 정의 할수도 있음

&#9656; 또한 함수 표현식은 변수에 저장될 수 있음, 그 후 변수는 함수처럼 사용됨

&#9656; 함수에 따로 이름이 없고 변수명으로 사용되는 함수라서 **익명 함수**라고도 불림

예시
{: .label .label-purple .mt-3}
```js
var x = function (a, b) {return a * b};

var z = x(4, 3);
```

!note
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
익명함수는 표현식(실행문)이기 때문에 세미콜론을 사용해야함 
</div>

### Arrow Functions

**화살표 함수는 함수 표현식 작성을위한 짧은 구문을 허용**

Syntax
{: .label .mt-2}
```js
// ES5
var x = function(x, y) {
  return x * y;
}

// ES6
const x = (x, y) => x * y;
const x = (x, y) => { return x * y };
```

&#9656; 화살표 함수는 `this`가 없어서 객체 메소드를 정의하는데 알맞지 않음

&#9656; 게양되지 않아서 호출되기 전에 선언되어야함

&#9656; `const` 변수 키워드를 사용하는게 안전함 (함수 표현식은 항상 constant value라서)

&#9656; 함수가 단일 명령문일경우 `return` 키워드와 `{}` 생략 가능

!note
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
Arrow functions are not supported in IE11 or earlier
</div>

---

## Function Variables

자바스크립트 변수는 지역이나 전역변수가 될 수 있음

전역 변수를 closer를 사용해 지역 변수로 만들 수 있음

### Local Variables

자바스크립트 안에서 선언된 변수들은 **지역변수**가 됨

Example
{: .label .mt-2}
```js
// code here can NOT use carName

function myFunction() {
  var carName = "Volvo";
  // code here CAN use carName
}

// code here can NOT use carName
```

### Global Variables

함수 외부에서 선언된 변수는 전역변수, 전역변수는 window 객체에 속함

&#9656; 전역변수는 페이지의 모든 스크립트에서 사용 및 변경할 수 있음

&#9656; 지역변수는 정의 된 함수 내에서만 사용 가능함

&#9656; 전역변수와 지역변수의 이름이 같더라도 다른 변수로 인지함

예제
{: .label .label-purple .mt-3}
```js
var a = 4;  //전역변수
function myFunction() {
    var b = 7;  //지역변수
    return a * b;
}
```

!note
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
변수 선언 키워드(var, let, const) 없이 사용된 변수는 항상 전역변수!!!
</div>

Variable Lifetime
{: .label .mt-2}
<div class="code-example" markdown="1">
* 전역변수 : 다른 페이지로 이동하거나 창을 닫을 때 까지 유지

* 지역변수 : 함수가 호출될 때 작성되고 함수가 완료되면 삭제
</div>

#### JavaScript Counting Dilemma

무언가를 세는데 함수를 사용하고 싶을 때 자주 딜레마가 발생됨

예제
{: .label .label-purple .mt-3}
```js
// Initiate counter
var counter = 0;

// Function to increment counter
function add() {
  counter += 1;
}

// Call add() 3 times
add();
add();
add();

// The counter should now be 3
```

&#8594; 페이지의 모든 코드는 add ()를 호출하지 않고 전역 변수를 변경할 수 있어서 문제가 생김

그래서 **중첩 함수를 사용함**

&#9656; 함수를 중첩하면 부모 함수에서 사용된 변수를 자식 함수도 사용할 수 있지만 자식 함수만을 호출할 수 없기 때문에 자식 함수를 사용하기 위해서 자체 호출 함수를 사용함, 자체 호출된 부분은 아무리 불러도 딱 한번만 실행되고, 나머지 지정한 함수 부분만 계속 실행되기 때문에 부모 안에 있는 변수는 한번만 선언되며, 자식 함수도 사용할 수 있음!

예제
{: .label .label-purple .mt-3}
<div class="code-example" markdown="1">
<button type="button" onclick="myFunction()">Count!</button>

<p id="demo">0</p>

<script>
var add = (function () {
  var counter = 0;
  return function () {counter += 1; return counter;}
})();

function myFunction(){
  document.getElementById("demo").innerHTML = add();
}
</script>
</div>
```js
<button type="button" onclick="myFunction()">Count!</button>

<p id="demo">0</p>

<script>
var add = (function () {
  var counter = 0;
  return function () {counter += 1; return counter;}
})();

function myFunction(){
  document.getElementById("demo").innerHTML = add();
}
</script>
```

&#8594; 따라서 카운터는 익명 함수의 범위에 의해 보호되며 add 함수를 통해서만 변경가능 함

---

## Closures

### Function Return

**return문에 도달하면 함수는 실행이 중지**됨

함수는 종종 반환 값을 계산하고, **리턴 값은 호출자에게 반환됨**

★ 이거 때문에 변수에 값을 담고 출력해야 return값이 나옴 because return value needs variable caller !

Example
{: .label .mt-2}
```js
var x = myFunction(4, 3);   // Function is called, return value will end up in x

function myFunction(a, b) {
  return a * b;             // Function returns the product of a and b
}
```

&#8594; 위처럼 함수를 변수값으로 사용할 수 있음
