---
layout: default
title: Syntax
parent: Basic
grand_parent: JavaScript
nav_order: 4
---

# JavaScript Syntax
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Syntax basic

Syntax : 일련의 규칙, JavaScript 프로그램 구성 방법

```js
var x, y, z;         // How to declare variables
x = 5; y = 6;        // How to assign values
z = x + y;           // How to compute values
```

### Values 

자바스크립트 문법은 두가지의 값을 정의함: **Fixed values** and **variable values**

* Fixed values 

    **literals 리터럴 (데이터 그 자체)**
    
    &#9656; 변하지 않는 데이터(boolean, char, double, long, int, etc...)를 리터럴(literal)

    &#9656; 숫자(written with or without decimals), 문자(written within double or single quote)가 대표적 

    상수(constant)와 리터럴(literal)의 차이점
    {: .label .mt-2}
    <div class="code-example" markdown="1">
    상수와 리터럴 둘 다, 변하지 않는 값(데이터)이지만

    상수 : 변하지 않는 변수

    따라서 상수에 넣는 데이터는 숫자가 올 수 도 있지만, 클래스나 구조체 같이 기본형에서 파생된 객체나 유도형같은 데이터를 넣을 수 있다
    </div>
    <span class="fs-2">
    [더 알아보기](https://mommoo.tistory.com/14){: .btn  .btn-outline .mt-2}
    </span>

* [Variable value](https://gekdev.github.io/docs/javascript/basic/variable/)

    **variables = 변수**

    &#9656; 변수는 데이터를 저장하기 위해 사용되는 값
    
    &#9656; 정의하기 위해 `var` 키워드 사용
    
    &#9656; 할당하기 위해 `=` 연산자 사용

### [Operators](https://gekdev.github.io/docs/javascript/operators/)

**연산자**

&#9656; 변수들을 계산하고 비교하고 할당하기 위해 연산자를 사용**

* 산술 연산자 : + - * / 

* 할당 연산자 : =

### Expressions

**자바스크립트 문**

&#9656; value, variable, operator의 조합

&#9656; 변수들을 연산자로 곱하고 더하는 형식으로 자바스크립트 문은 표현됨

### Comment

* single : //

* multi : /**/

자주 쓰는 습관 들이기!

