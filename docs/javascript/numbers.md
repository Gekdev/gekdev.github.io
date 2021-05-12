---
layout: default
title: Numbers
parent: JavaScript
nav_order: 8
has_children: true
---

# JavaScript Numbers
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc} 

---

## Numbers Basic

### What is Numbers?

자바스크립트가 사용하는 **단 한가지 타입의 숫자를 나타내는 number 데이터 타입**

&#9656; 숫자는 소숫점이 있거나 없이 쓰임

&#9656; JavaScript Numbers are Always 64-bit Floating Point

&#9656; 다른 많은 프로그래밍 언어와 달리 JavaScript는 정수, 짧은, 긴, 부동 소수점 등과 같은 다른 유형의 숫자를 정의하지 않음

### Integers Precision

integers : **정수**

&#9656; 정수 (마침표 나 지수 표기가없는 숫자)는 최대 15 자리

```js
var x = 999999999999999;   // x will be 999999999999999
var y = 9999999999999999;  // y will be 10000000000000000
```

&#9656; 최대 소수 자릿수는 17이지만 부동 소수점 산술이 항상 100 % 정확하지는 않음

```js
var x = 0.2 + 0.1;         // x will be 0.30000000000000004

문제를 해결하려면 아래와 같이 해야함
var x = (0.2 * 10 + 0.1 * 10) / 10;       // x will be 0.3
```
    
### Adding Numbers and Strings

**Numbers are added, Strings are concatenated**

&#9656; add a number and a string, the result will be a string concatenation

&#9656; 왼쪽에서 오른쪽으로 계산되기 때문에 숫자 계산 먼저 됨

```js
var x = 10;
var y = "20";
var z = "The result is: " + x + y;  		// z = "The result is 1020"

...

var x = 10;
var y = 20;
var z = "30";
var result = x + y + z;                     // z = "3030"
```

### Numeric Strings

**숫자 문자열은 종종 숫자로 계산됨**

&#9656; 나누기, 곱하기, 빼기 다 숫자로 계산 되는데 오직 더하기만 Concatenation 

```js
var x = "100";
var y = "10";
var z = x / y;       // z will be 10
var z = x * y;       // z will be 1000
var z = x - y;       // z will be 90
var z = x + y;       // z will not be 110 (It will be 10010)
```

### NaN(Not a Number) 

**a number is not a legal number**

&#9656; 숫자가 아니라는걸 나타내는 자바스크립트 `NaN`키워드

&#9656; 숫자가 아닌 문자열로 산술을 시도하면 `NaN` 발생

&#9656; NaN 연산시 숫자는 계산되고 문자는 결합됨

```js
var x = 100 / "Apple";  
// x will be NaN (Not a Number)

...

NaN + 숫자 = NaN
NaN + "문자열" = NaN문자열
```

#### isNaN() 

**to find out if a value is a number**

&#9656; global JavaScript function

```js
var x = 100 / "Apple";
isNaN(x);               // returns true because x is Not a Number
```

#### typeof NaN

```js
typeof NaN;            // returns "number"
```

### Infinity

**가능한 가장 큰 숫자 이외의 숫자를 계산하면 JavaScript가 반환하는 값**

&#9656; -Infinity도 있음

```js
var x =  2 / 0;       // x will be Infinity
var y = -2 / 0;       // y will be -Infinity
```

#### typeof Infinity

```js
typeof Infinity;     // returns "number"
```
    
### Hexadecimal 

**16진수**

&#9656; 기본적으로 JavaScript는 숫자를 10 진수로 표시

&#9656; 숫자 상수 앞에 0x가 있으면 16 진수로 해석

&#9656; 숫자 앞에 7을 07와같이 사용하면 (선행 0으로 작성된 경우의) 숫자를 8 진수로 해석

&#9656; toString으로 기수 2 에서 기수 36으로 숫자를 출력 할 수 있음

예제
{: .label .label-purple .mt-2}
```js
var myNumber = 32;
myNumber.toString(10);  // 10진법, returns 32
myNumber.toString(32);  // 32진법, returns 10
myNumber.toString(16);  // 16진법, returns 20
myNumber.toString(8);   // 8진법, returns 40
myNumber.toString(2);   // 2진법, returns 100000
```

### Numbers Can be Objects

숫자를 객체로 선언할 수 있음

&#9656; `new` 키워드는 복잡한 코드라서 계산속도를 늦추기때문에 권장되지 않음

예제
{: .label .label-purple .mt-2}
```js
var x = 123;
var y = new Number(123);

// typeof x returns number
// typeof y returns object
```

위 예제는 `==` 는 true지만 `===`는 false

또한 둘다 객체로 선언될 경우 **객체는 비교될수 없기 때문에 모두 false**가 나온다

---
