---
layout: default
title: Definitions
parent: Functions
grand_parent: JavaScript
nav_order: 1
---

# Functions Definitions
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Definitions

### Function Declarations

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

정의된 함수는 바로 실행되는게 아니라 **나중에 호출되면 실행**되는것

### Function Expressions (Anonymous Function)

&#9656; JavaScript 함수는 표현식을 사용하여 정의 할수도 있음

&#9656; 또한 함수 표현식은 변수에 저장될 수 있음, 그 후 변수는 함수처럼 사용됨

&#9656; 함수에 따로 이름이 없고 변수명으로 사용되는 함수라서 익명 함수라고도 불림

예제
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

### The Function() Constructor

1. `function` 키워드로 정의

2. `Function()` 내장 자바스크립트 함수 생성자

&#8594; 두 방법 모두 동일하지만 첫번째 방법이 편리하기때문에 더 자주 씀

예제
{: .label .label-purple .mt-3}
```js
1. var myFunction = function (a, b) {return a * b};

2. var myFunction = new Function("a", "b", "return a * b");

var x = myFunction(4, 3);
```

!note
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
Most of the time, you can avoid using the new keyword in JavaScript
</div>

### Function Hoisting

&#9656; Hoisting은 선언을 현재 범위의 맨 위로 이동시키는 자바스크립트 기본 동작

&#9656; 변수 선언과 함수 선언에 적용됨, 따라서 함수 선언 전 호출가능

※ 실행문(Expressions)으로 선언된 함수는 게양되지 않음

예제
{: .label .label-purple .mt-3}
```js
myFunction(5);

function myFunction(y) {
  return y * y;
}
```

### Self-Invoking Functions

&#9656; 함수 선언은 자체호출될 수 없고, 함수 표현식은 **자기 호출**이 가능함

&#9656; 표현식 뒤에 `()`가 있으면 함수 표현식이 자동으로 실행

&#9656; 함수 주위에 괄호를 추가하여 함수 표현식임을 표시해야함

예제
{: .label .label-purple .mt-3}
```js
// 익명함수의 자체호출
(function () {
  var x = "Hello!!";  // I will invoke myself
})();

var add = (function () {
  var counter = 0;
  return function () {counter += 1; return counter}
})();
```

### Functions Can Be Used as ..

함수는 value, expression으로 사용될 수 있음

예제
{: .label .label-purple .mt-3}
```js
var x = myFunction(4, 3);       //value
var x = myFunction(4, 3) * 2;   //expressions
```

### Functions are Objects

`typeof` 연산자는 function을 function이라고 반환하지만 함수는 객체로 가장 잘 설명 할 수 있음

&#9656; JavaScript 함수에는 속성 과 메서드가 모두 있음

* arguments.length 

    **함수가 호출될 때 받은 인수의 수를 반환**

    예제
    {: .label .label-purple .mt-3}
    ```js
    function myFunction(a, b) {
      return arguments.length;      //인수 개수에 따라서 0,1,2를 리턴
    }
    ```

* toString() 

    **함수를 문자열로 리턴**
    
    &#9656; toString() 메소드는 모든 데이터 타입에 작용하므로 함수 이름만 호출해도 같은 결과가 나옴

    예제
    {: .label .label-purple .mt-3}
    ```js
    function myFunction(a, b) {
      return a * b;
    }

    var txt = myFunction.toString(); // txt = myFunction 과 같다
    ```

!method
{: .label .mt-2}
<div class="code-example" markdown="1">
객체의 속성으로 정의 된 함수를 객체에 대한 메소드라고함

새로운 객체를 생성하도록 설계된 함수를 객체 생성자라고함
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

