---
layout: default
title: Operator
parent: JavaScript
nav_order: 4
has_children: true
---
 
# JavaScript Operator
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Operator Basic

### What is Operator?

**프로그래밍에서 쓰이는 기호, 여러 종류의 연산을 위한을 위해 사용**

---

## Operator Sort

### Arithmetic Operators

**산술연산자**

2개 이상의 숫자들 (리터럴 또는 변수)에 산술을 시행함

| Operator      | Description                   |
|:--------------|:------------------------------|
| +             | addition                      |
| -             | subtraction                   |
| *             | multiplication                |
| **            | Exponentiation                |
| /             | division                      |
| %             | Modulus (Division Remainder)  |

&#9656; +는 숫자는 더하기, 문자는 결합의 속성 [(순서 중요함)](https://www.w3schools.com/js/tryit.asp?filename=tryjs_datatypes_addstrings_2)

&#9656; x ** y produces the same result as Math.pow(x,y)

&#9656; % : 나머지값까지 모두 실수

&#9656; 숫자들은 리터럴(1+1), 변수(a+b), 표현식((1+1)*a)일 수 있음

&#9656; 숫자들을 operands 피연산자라고 부름

Operator Precedence
{: .label .mt-2}
<div class="code-exmaple" markdown="1">
일반 수학처럼 * / 가 + - 보다 연산 우선순위를 갖음
</div>

### Increment and Decrement Operators

**증감연산자**

| Operator      | Description                   |
|:--------------|:------------------------------|
| ++            | Increment                     |
| --            | Decrement                     |

두가지 연산 방법이 있음

* 전위연산(++a) : 먼저 계산해서 내가됨

* 후위연산(a++) : 다 하고 난 후 내가 더해짐

Example
{: .label .mt-2}
```js
var number = 10;
document.write(++number + '<br>'); // 11, 전위증감
document.write(number++ + '<br>'); // 11, 후위증감
document.write(--number + '<br>'); // 11, 전위증감
document.write(number++ + '<br>'); // 11, 후위증감

이후에 number이 12가 된다
```

### Assignment Operators

**할당연산자**

| Operator     | Example     | Same As    |
|:-------------|:------------|:-----------|
| =            | x = y       | x = y      |
| +=           | x += y      | x = x + y  |
| -=           | x -= y      | x = x - y  |
| *=           | x *= y      | x = x * y  |
| /=           | x /= y      | x = x / y  |
| %=           | x %= y      | x = x % y  |
| **=          | x **= y     | x = x ** y |

&#9656; 증감연산자가 할당연산자의 속도보다 빠르다 a++ > a = a+1

&#9656; +, +=는 문자열을 결합할때도 사용

!Note
{: .label .label-yellow .mt-2}
<div class="code-exmaple" markdown="1">
The **= operator is an experimental part of the ECMAScript 2016 proposal (ES7). It is not stable across browsers. Do not use it.
</div>

### Comparison Operators

**비교연산자**

값으로 true or false

| Operator      | Description                       |
|:--------------|:----------------------------------|
| ==            | equal to                          |
| ===           | equal value and equal type        |
| !=            | not equal                         |
| !==           | not equal value or not equal type |
| >             | greater than                      |
| <             | less than                         |
| >=            | greater than or equal to          |
| <=            | less than or equal to             |

&#9656; 문자열로 되어있는 숫자면(둘중 하나가) 숫자로 치환해서 비교해주고 ex) 1 < “3” true

&#9656; 문자열과 숫자를 비교할때는 숫자를 문자열로 치환해서 비교함

&#9656; 둘다 문자열로 되어있으면 알파벳 순으로 비교해서 = it works like sort()

Example
{: .label .mt-2}
```js
document.write(("3" >= 1)) 		// true
document.write(("273" == 273))  // true
document.write((“2” < “12”))    // false 
```

&#9656; 빈 문자열 = 0

&#9656; 숫자로 바꿀 수 없는 문자열 = NaN – so result is always false

&#9656; 문자끼리는 순서대로 나열해 알파벳이 뒤에있을수록 값이 크다 

Example
{: .label .mt-2}
```js
age = Number(age);
	if (isNaN(age)) {
	  voteable = "Input is not a number";
	} else {
	  voteable = (age < 18) ? "Too young" : "Old enough";
	}
```

### Conditional Operator

**조건연산자**

값으로 true or false이 나옴

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
variablename = (condition) ? value1:value2
</div>
```js
	var voteable = (age < 18) ? "Too young":"Old enough";
```

| Operator      | Description                       |
|:--------------|:----------------------------------|
| ?             | ternary operator                  |

&#9656; 조건 연산을 계속 겹쳐서 사용할 수 있음

### Logical Operators

**논리 연산자**

값으로 true or false이 나옴

| Operator      | Description             |
|:--------------|:------------------------|
| &&            | and                     |
| &#124;&#124;  | or                      |
| !             | not                     |

&#9656; ! : if a = true ==> false , a = false ==> true

### Type Operators

**변수나 표현식의 데이터 타입을 찾기위해 사용하는 연산자**

| Operator      | Description                                                   |
|:--------------|:--------------------------------------------------------------|
| typeof        | Returns the type of a variable                                |
| instanceof    | Returns true if an object is an instance of an object type    |

예시
{: .label .label-purple .mt-2}
```js
typeof "John"                 // Returns "string"
typeof 3.14                   // Returns "number"
typeof NaN                    // Returns "number"
typeof false                  // Returns "boolean"
typeof [1,2,3,4]              // Returns "object"
typeof {name:'John', age:34}  // Returns "object"
typeof new Date()             // Returns "object"
typeof function () {}         // Returns "function"
typeof myCar                  // Returns "undefined" (if x has no value)
typeof null                   // Returns "object"
```

### Bitwise Operators

Bit operators work on **32 bits numbers**

비트 : 비트의 논리 연산

비트 시프트 : 새로운 비트를 끝에 삽입하면서 비트의 자리를 이동하는 연산

<span class="fs-2">
[W3School](https://www.w3schools.com/js/js_bitwise.asp){: .btn  .btn-outline .mt-2}
</span>
