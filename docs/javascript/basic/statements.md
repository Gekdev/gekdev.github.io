---
layout: default
title: Statements
parent: Basic
grand_parent: JavaScript
nav_order: 2
---

# JavaScript Statements
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## JavaScript Program Statements

**문장**

컴퓨터 프로그램은 컴퓨터에 의해 "지침"들이 "실행"할 목록

프로그래밍 언어에서 이러한 프로그래밍 명령어(instructions)를 statements 이라고 함

**자바스크립트 프로그램은 프로그래밍 statements 목록** (자바스크립트 코드라고도 불림)

&#9656; [표현식(Expressions)과 다른 개념임!](https://velog.io/@jakeseo_me/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EA%B0%9C%EB%B0%9C%EC%9E%90%EB%9D%BC%EB%A9%B4-%EC%95%8C%EC%95%84%EC%95%BC-%ED%95%A0-33%EA%B0%80%EC%A7%80-%EA%B0%9C%EB%85%90-7-%ED%91%9C%ED%98%84%EC%8B%9D%EA%B3%BC-%EB%AC%B8Statement-%EB%B2%88%EC%97%AD-2xjuhvbal7)

### Statements

지시문 구성물 : Values, Operators, Expressions, Keywords, Comments

&#9656; 실행문은 하나하나 순서대로 진행함

예제
{: .label .label-purple .mt-3}
```js
document.getElementById("demo").innerHTML = "Hello Dolly.";
```

### Semicolons ; and Space

**문장을 구분하는 역할**

&#9656; 별도의 자바스크립트 문

&#9656; ;는 자바스크립트에서 꼭 필요하진 않지만 다른 언어에서도 많이 사용되니까 쓰는 습관들이기!

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

&#9656; 같이 실행되기를 원하는 자바스크립트 코드를 묶는것

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

&#9656; 키워드들은 변수명으로 사용하면 안됨!

&#9656; 대표적으로 break, continue, debugger... 가 있음

<span class="fs-2">
[키워드 더보기](https://www.w3schools.com/js/js_reserved.asp){: .btn  .btn-outline .mt-2}
</span>

