---
layout: default
title: Scope
parent: variable
grand_parent: JavaScript
nav_order: 2
---
 
# Variable Scope
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Scope

**범위는 코드의 다른 부분에서 변수, 개체 및 함수의 접근성을 결정**

### Global Scope

**전역 범위**

&#9656; 전역으로 선언 된 변수(모든 함수 외부)는 전역 범위를 가짐

&#9656; 전역 범위는 JavaScript 환경, HTML에서 전역 범위는 창 개체

&#9656; 전역 변수는 JavaScript 프로그램의 어느 곳에서나 액세스 할 수 있음

예시
{: .label .label-purple .mt-2}
```js
var carName = "Volvo";
// code here can use carName

function myFunction() {
  // code here can also use carName
}
```

### Function(local) Scope

**함수 범위**

&#9656; 함수 내에서 로컬로 선언된 변수(지역변수)는 함수 범위를 가짐

&#9656; 지역 변수는 선언 된 함수 내에서만 액세스할 수 있음

&#9656; 지역 변수는 함수가 시작될 때 생성되고 함수가 완료되면 삭제

&#9656; 지역 변수는 함수 내에서만 인식되기 때문에 같은 이름의 변수를 다른 함수에서 사용 가능

예시
{: .label .label-purple .mt-2}
```js
// code here can NOT use carName

function myFunction() {
  var carName = "Volvo";
  // code here CAN use carName
}

// code here can NOT use carName
```
