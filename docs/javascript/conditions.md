---
layout: default
title: Conditions
parent: JavaScript
nav_order: 14
---

# JavaScript Conditions
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Conditional Statements

### Conditions Basic

**조건문, 조건을 검사해 참인지 거짓인지에 따라 서로 작은 작업을 실행하는 문장**

* if : 조건이 참일 때 실행되어야 하는 코드 블럭을 특정함

* else : 조검이 거짓일 때 실행되어야 하는 코드 블럭을 특정

* else if : 첫번째 if가 참이 아닐경우 다음 실행되어야 하는 새로운 조건의 코드를 특정함

* switch : 여러 대체 코드블록을 지정하는 데 사용

### The if Statement(true)

**if 조건이 참인 경우 실행할 JavaScript 코드 블록을 지정**

&#9656; if 뒤의 괄호에 조건이 오고, 조건이 될 수 있는 값는 Boolean

&#9656; 소문자가 아닐경우 오류가 발생함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
if (condition) {

  //  block of code to be executed if the condition is true
  
}
</div>
```js
if (hour < 18) {
  greeting = "Good day";
}
```

### The else Statement(false)

**조건이 거짓 인 경우 실행할 코드 블록을 지정**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
if (condition) {

  //  block of code to be executed if the condition is true
  
} else {

  //  block of code to be executed if the condition is false
  
}
</div>
```js
if (hour < 18) {
  greeting = "Good day";
} else {
  greeting = "Good evening";
}
```

### else if Statement

**첫 번째 조건이 거짓인 경우 명령문을 사용하여 새 조건을 지정**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
if (condition1) {

  //  block of code to be executed if condition1 is true
  
} else if (condition2) {

  //  block of code to be executed if the condition1 is false and condition2 is true
  
} else {

  //  block of code to be executed if the condition1 is false and condition2 is false
  
}
</div>
```js
if (time < 10) {
  greeting = "Good morning";
} else if (time < 20) {
  greeting = "Good day";
} else {
  greeting = "Good evening";
}
```

---

## Switch Statement

## Switch Basic

**다른 조건에서 실행되어야 하는 다른 작업들을 지정**

&#8594; 값에따라 서로다른 코드를 작성해야 할 때 if보다 좋다 (조건비교는 if, 값에따른 다른코드작성은 switch)

&#9656; 스위치 표현식은 한 번 계산되고, 표현식의 값은 각 케이스의 값과 비교됨

&#9656; 첫 번째로 일치하는 항목의 코드 블록이 먼저 실행되고, 일치하는 항목이 없으면 기본 코드 블록이 실행

&#9656; case에 따라서 break 문을 사용하지 않으면, 참인 값 뒤로 작성된 case의 값들이 모두 작성

&#9656; default도 없으면 switch문을 끝내고 스위치 이후의 명령문을 계속 진행함

&#9656; 비교되는 값은 상수만 가능함

&#9656; case에 따라서 중괄호 쓰면 안됨

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
switch(expression) {

  case x:
  
  // code block

  break;

  case y:
  
  // code block

  break;
  default:

  // code block

}
</div>
```js
switch (new Date().getDay()) {
  case 0:
    day = "Sunday";
    break;
  case 1:
    day = "Monday";
    break;
  case 2:
     day = "Tuesday";
    break;
  case 3:
    day = "Wednesday";
    break;
  case 4:
    day = "Thursday";
    break;
  case 5:
    day = "Friday";
    break;
  case 6:
    day = "Saturday";
}
```

### The break Keyword

**break 키워드에 도달 하면 스위치 블록을 벗어나고 스위치 블록 내부의 실행이 중지**

### The default Keyword

**어떤 경우 일치하지 않는 경우 실행하는 코드를 지정**

&#9656; The default case does not have to be the last case in a switch block (어디서나 작성 가능)

&#9656; 조건문의 마지막이 아님! 종료는 break keyword

### Common Code Blocks

break 키워드를 사용하지 않고 일부러 아래와 같이 값을 적지않고 뒤로 넘기는 방식이 가능함

```js
case 4:
case 5: var txt = “love myself”
```

### Strict Comparison

**use strict comparison (===)**

&#8594; 그래서 항상 같은타입으로 비교해야함!

예시
{: .label .label-purple .mt-2}
```js
var x = "0";
switch (x) {
  case 0:
    text = "Off";
    break;
  case 1:
    text = "On";
    break;
  default:
    text = "No value found";			//이게 답
}
```
