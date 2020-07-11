---
layout: default
title: Parameters
parent: Functions
grand_parent: JavaScript
nav_order: 2
---

# Functions Parameters
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Parameters

### Function Parameters and Arguments

Parameter는 함수 정의에 사용된 변수들

Argument는 함수를 지나가는 진짜 값들

매개변수와 인수와의 차이점
{: .label .mt-2}
<div class="code-example" markdown="1">
매개변수는 함수의 정의부분에 나열되어 있는 변수들을 의미하며,

전달인자는 함수를 호출할때 전달되는 실제 값을 의미한다. 

이같은 의미를 명확히 하기 위해 매개변수는 변수(variable)로, 전달인자는 값(value)으로 보는 것이 일반적
</div>

### Parameter Rules

**매개변수 규칙**

JavaScript 함수 정의는 **매개 변수의 데이터 유형을 지정하지 않음**

JavaScript 함수는 **인자에 대한 아무런 검사를 수행하지 않음**

JavaScript 함수는 **수신 된 인수 수를 확인하지 않음**

### Parameter Defaults

매개변수는 있지만, 인수가 주어지지 않았다면 매개변수는 undefined 값을 가짐

때로는 이것이 허용되지만 아래와 같이 매개 변수에 기본값을 할당하는 것이 좋음

```js
function myFunction(x, y) {
  if (y === undefined) {
    y = 0;
  }
}
```

아니면 아래와 같이 기본 매개 변수값을 허용

```js
function (a=1, b=1) {
  // function code
}
```

---

## Arguments

### The Arguments Object

JavaScript 함수에는 **arguments 객체라는 내장 객체**가 있음

정의된 매개변수보다 인수가 더 많을 때 인수(객체)는 함수가 호출될 때 인수 배열을 포함해서 여러가지의 값을 한번에 넣을 수 있음

예제: 가장 큰 값 찾기
{: .label .label-purple .mt-3}
```js
x = findMax(1, 123, 500, 115, 44, 88);

function findMax() {
  var i;
  var max = -Infinity;
  for (i = 0; i < arguments.length; i++) {
    if (arguments[i] > max) {
      max = arguments[i];
    }
  }
  return max;
}
```

예제: 평균 값 찾기
{: .label .label-purple .mt-3}
```js
x = sumAll(1, 123, 500, 115, 44, 88);

function sumAll() {
  var i;
  var sum = 0;
  for (i = 0; i < arguments.length; i++) {
    sum += arguments[i];
  }
  return sum;
}
```

### Arguments are Passed by Value

함수 호출에서 매개 변수는 함수의 인수

JavaScript 인수는 값 으로 전달됨

함수는 인수의 위치가 아니라 **값만** 알 수 있음

함수가 인수의 값을 변경해도 매개 변수의 원래 값은 변경되지 않음

**함수 외부에서는 인수에 대한 변경 사항이 보이지 않음**

### Objects are Passed by Reference

JavaScript에서 object references는 값

이로 인해 객체는 **reference로 전달** 된 것처럼 동작함

함수가 객체 속성을 변경하면 원래 값이 변경됨

**객체 속성에 대한 변경사항은 함수 외부에서 반영됨**

