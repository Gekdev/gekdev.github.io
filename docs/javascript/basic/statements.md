---
layout: default
title: Statements
parent: Basic
grand_parent: JavaScript
nav_order: 3
---

# JavaScript Statements
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Statements

### JavaScript Programs

컴퓨터 프로그램 : 컴퓨터나 브라우저에 의해 실행되어야 하는 지시문

자바스크립트 프로그램 : 프로그램의 목록 statement (자바스크립토 코드라고도 불림)

### Statements

문장 구성 : Values, Operators, Expressions, Keywords, Comments

실행문은 하나하나 순서대로 진행함

예제
{: .label .label-purple .mt-3}
```js
document.getElementById("demo").innerHTML = "Hello Dolly.";
```

### Semicolons ; and Space

**문장을 구분하는 역할**

별도의 자바스크립트 문

;는 자바스크립트에서 꼭 필요하진 않지만 다른 언어에서도 많이 사용되니까 쓰는 습관들이기!

### White Space

자바스크립트는 **여러줄의 빈공간을 무시**하므로 그냥 읽기 쉽게 만들 수 있음

### Line Breaks

`=` 과같은 **연산자 뒤로 문장을 나눠**쓸 수 있음

예제
{: .label .label-purple .mt-3}
```js
document.getElementById("demo").innerHTML =
"Hello Dolly!";
```

### Code Blocks

**curly brackets {...} 안으로 코드가 뭉칠 수 있음**

같이 실행되기를 원하는 자바스크립트 코드를 묶는것

예제
{: .label .mt-2 .label-purple}
```js
function myFunction() {
  document.getElementById("demo1").innerHTML = "Hello Dolly!";
  document.getElementById("demo2").innerHTML = "How are you?";
}
```

### Keywords

문장은 종종 **수행 할 JavaScript 조치를 구별하기 위해 키워드(keyword)로 시작**

키워드들은 변수명으로 사용하면 안됨!

대표적으로 break, continue, debugger... 가 있음

<span class="fs-2">
[키워드 더보기](https://www.w3schools.com/js/js_reserved.asp){: .btn  .btn-outline .mt-2}
</span>

