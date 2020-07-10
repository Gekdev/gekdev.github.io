---
layout: default
title: Functions
parent: JavaScript
nav_order: 10
has_children: true
---

# JavaScript Functions
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Function Basic

### What is Function?

**특정한 일을 수행하기 위한 코드블럭**

어떤 무언가가 함수를 부르면 실행됨

코드를 한번 정의하고 여러번 사용하기 위해 사용된다

### Function Declarations

Syntax
{: .label}
```js
function functionName(parameters) {
  // code to be executed
}
```

&#9656; 자바스크립트 함수는 **function 키워드로 정의**되고 그다음으로 **이름과 ()가 따라옴**

&#9656; 정의된 함수는 바로 실행되는게 아니라 나중에 호출되면 실행되는것

&#9656; 함수 이름으로는 변수명과 같은 조건으로 사용됨

&#9656; 매개변수 (parameters)들은  함수 정의에서 ,로 구분되고 () 안에 존재함

&#9656; 함수에 의해 실행되어야 하는 코드들은 {} 안에 종속됨

&#9656; 인수 (arguments)는 함수가 호출될 때 함수가 받는 값, 함수 안에서는 인수 (매개변수)가 지역변수처럼 사용된다

매개변수와 인수와의 차이점
{: .label .mt-2}
<div class="code-example" markdown="1">
매개변수는 함수의 정의부분에 나열되어 있는 변수들을 의미하며,

전달인자는 함수를 호출할때 전달되는 실제 값을 의미한다. 

이같은 의미를 명확히 하기 위해 매개변수는 변수(variable)로, 전달인자는 값(value)으로 보는 것이 일반적
</div>

!note
{: .label .mt-2}
<div class="code-example" markdown="1">
함수는 실행문이 아니라서 세미콜론으로 끝나지 않음
</div>

### Local Variables

자바스크립트 안에서 선언된 변수들은 **지역변수**가 됨

예제
{: .label .label-purple .mt-2}
```js
// code here can NOT use carName

function myFunction() {
  var carName = "Volvo";
  // code here CAN use carName
}

// code here can NOT use carName
```

### Function Invocation

무엇인가가 함수를 호출해야지 함수는 실행됨

함수이름과 `()` operator가 특정 함수를 호출함

함수 이름만 호출하면 함수 객체를 가져옴

* 함수가 호출되는 경우

    &#9656; When an event occurs (when a user clicks a button)

    &#9656; When it is invoked (called) from JavaScript code

    &#9656; Automatically (self invoked)

### Function Return

**return문에 도달하면 함수는 실행이 중지**됨

함수는 종종 반환 값을 계산하고, **리턴 값은 호출자에게 반환됨**

&#8594; 이거 때문에 변수에 값을 담고 출력해야 return값이 나옴 because return value needs variable caller !

예제
{: .label .label-purple .mt-2}
```js
var x = myFunction(4, 3);   // Function is called, return value will end up in x

function myFunction(a, b) {
  return a * b;             // Function returns the product of a and b
}
```

위처럼 함수를 변수값으로 사용할 수 있음

