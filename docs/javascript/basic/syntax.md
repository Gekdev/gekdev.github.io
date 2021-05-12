---
layout: default
title: Syntax
parent: Basic
grand_parent: JavaScript
nav_order: 1
---

# JavaScript Syntax
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Syntax Basic

### Syntax 

**JavaScript 프로그램이 구성되는 일련의 규칙**

```js
var x, y, z;         // How to declare variables
x = 5; y = 6;        // How to assign values
z = x + y;           // How to compute values
```

---

## Syntax Structures

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

* [Variable values](https://gekdev.github.io/docs/javascript/basic/variable/)

    **variables = 변수**

    &#9656; 변수는 데이터를 저장하기 위해 사용되는 값
    
    &#9656; 정의하기 위해 `var` 키워드 사용
    
    &#9656; 할당하기 위해 `=` 연산자 사용

### [Identifiers](https://gekdev.github.io/docs/javascript/basic/variable/#identifiers)

**이름**

&#9656; 식별자는 변수 (및 키워드, 함수 및 레이블)의 이름을 지정하는 데 사용

&#9656; 첫 번째 문자는 문자, 밑줄 (_) 또는 달러 기호 ($)

&#9656; 문자, 숫자, 밑줄 또는 달러 기호

#### Features of Identifiers

* 모든 JavaScript 식별자는 대소 문자를 구분

    ```css
    var lastname, lastName;
    lastName = "Doe";
    lastname = "Peterson";
    ```

* Camel Case

### [Operators](https://gekdev.github.io/docs/javascript/operators/)

**연산자**

&#9656; 변수들을 계산하고 비교하고 할당하기 위해 연산자를 사용**

* 산술 연산자 : + - * / 

* 할당 연산자 : =

### Expression

**표현식**

&#9656; 표현식은 값을 만들어냄, 값 하나로 귀결되는 자바스크립트 코드 조각(snippet)

&#9656; value, variable, operator의 조합

&#9656; 표현식은 우리가 원하는만큼 길어질 수 있지만 언제나 동일한 값이 나오지는 않음

&#9656; 표현식은 반드시 상태(State)를 바꿀 필요는 없다

&#9656; 함수, 익명함수, 함수 호출은 표현식 (값을 만들어내기 때문에)

#### Expression Statements

**세미콜론만 추가하면 표현식 문장**

예시
{: .label .label-purple .mt-2}
```js
2+2 // 그 자체로는 표현식입니다.
foo(2+2) // 그래서 어디든 값이 들어가야 할 곳에서 사용할 수 있죠.
true ? 2+2 : 1 + 1
function foo () {return 2+2}

2+2; // expression statement
foo(); // expression statement
foo(2+2;) // 문법 에러(Syntax Error)

//2+2자체는 표현식, 하지만 그 줄(line) 자체는 표현식 문장(Expression Statements)
```

### Statement

**문장**

&#9656; 자바스크립트에서 문장은 값이 들어와야 할 곳에 들어갈 수 없기 때문에 함수형 프로그래밍의 관점에서 문장은 골치덩어리

&#9656; 함수의 인자로도, 대입 연산의 값으로도, 연산자의 피연산자로도 사용될 수 없음

&#9656; 함수 선언은 문장(Statement)

대표적으로 아래와 같은 문장들이 있음

1. if
2. if-else
3. while
4. do-while
5. for
6. switch
7. for-in
8. with (deprecated)
9. debugger
10. variable declaration


### Comment

* single : //

* multi : /**/

자주 쓰는 습관 들이기!
