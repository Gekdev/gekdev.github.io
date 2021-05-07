---
layout: default
title: Features
parent: Functions
grand_parent: JavaScript
nav_order: 1
---

# Functions Features
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Features of Function

### Function Hoisting

Hoisting은 선언을 현재 범위의 맨 위로 이동시키는 자바스크립트 기본 동작

&#9656; **변수 선언과 함수 선언에 적용됨, 따라서 함수 선언 전 호출가능**

※ 실행문(Expressions)으로 선언된 함수 = 익명함수는 게양되지 않음

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
