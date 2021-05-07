---
layout: default
title: Closures
parent: Functions
grand_parent: JavaScript
nav_order: 5
---

# Functions Closures
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Closures

자바스크립트 변수는 지역이나 전역변수가 될 수 있음

전역 변수를 closer를 사용해 지역 변수로 만들 수 있음

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

### Variable Lifetime

* 전역변수 : 다른 페이지로 이동하거나 창을 닫을 때 까지 유지

* 지역변수 : 함수가 호출될 때 작성되고 함수가 완료되면 삭제

### JavaScript Closures

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

