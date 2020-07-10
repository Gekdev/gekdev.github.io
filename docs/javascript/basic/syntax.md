---
layout: default
title: Syntax
parent: Basic
grand_parent: JavaScript
nav_order: 3
---

# JavaScript Syntax
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Syntax

### Syntax basic

Syntax : 일련의 규칙, JavaScript 프로그램 구성 방법

```js
var x, y, z;         // How to declare variables
x = 5; y = 6;        // How to assign values
z = x + y;           // How to compute values
```

### Values 

자바스크립트 문법은 두가지의 값을 정의함: Fixed values and variable values

* Fixed values : literals 리터럴 (데이터 그 자체)
    
    변하지 않는 데이터(boolean, char, double, long, int, etc...)를 리터럴(literal)

    숫자(written with or without decimals), 문자(written within double or single quote)가 대표적 

    상수(constant)와 리터럴(literal)의 차이점
    {: .label .mt-2}
    <div class="code-example" markdown="1">
    상수와 리터럴 둘 다, 변하지 않는 값(데이터)이지만

    상수 : 코드적으로는 상수는 변하지 않는 변수

    따라서 상수에 넣는 데이터는 숫자가 올 수 도 있지만, 클래스나 구조체 같이 기본형에서 파생된 객체나 유도형같은 데이터를 넣을 수 있다
    </div>
    <span class="fs-2">
    [더 알아보기](https://mommoo.tistory.com/14){: .btn  .btn-outline .mt-2}
    </span>

* Variable value : variables 변수

    변수는 데이터를 저장하기 위해 사용되는 값
    
    정의하기 위해 `var` 키워드 사용
    
    할당하기 위해 `=` 연산자 사용

### Operators

변수들을 계산하고 비교하고 할당하기 위해 연산자를 사용

* 산술 연산자 : + - * / 

* 할당 연산자 : =

### Expressions

**자바스크립트 문은 value, variable, operator의 조합**

변수들을 연산자로 곱하고 더하는 형식으로 자바스크립트 문은 표현됨

### Identifiers

**식별자**

식별자는 이름, 이름들을 지정하기 위해 사용됨 (변수, 키워드, 함수, 라벨)

첫번째로 시작하는 단어는 문자, _, $만 가능함

나머지로 오는 단어는 letters, digits, _, $가 가능

> ✓ 첫번째 단어로 숫자가 오면 절대 안됨!!

case sensitive : Last 와 last는 다른 변수

### Comment

* single : //
* multi : /**/

자주 쓰는 습관 들이기

