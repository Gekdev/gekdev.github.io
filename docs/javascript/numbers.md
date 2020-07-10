---
layout: default
title: Numbers
parent: JavaScript
nav_order: 3
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

자바스크립트가 사용하는 단 한가지 타입의 숫자를 나타내는 number 데이터 타입

숫자는 소숫점이 있거나 없이 쓰임

JavaScript Numbers are Always 64-bit Floating Point

&#8594; 다른 많은 프로그래밍 언어와 달리 JavaScript는 정수, 짧은, 긴, 부동 소수점 등과 같은 다른 유형의 숫자를 정의하지 않음

### Integers Precision

integers : **정수**

정수 (마침표 나 지수 표기가없는 숫자)는 최대 15 자리

예제
{: .label .label-purple .mt-2}
```js
var x = 999999999999999;   // x will be 999999999999999
var y = 9999999999999999;  // y will be 10000000000000000
```

최대 소수 자릿수는 17이지만 부동 소수점 산술이 항상 100 % 정확하지는 않음

예제
{: .label .label-purple .mt-2}
```js
var x = 0.2 + 0.1;         // x will be 0.30000000000000004

문제를 해결하려면 아래와 같이 해야함
var x = (0.2 * 10 + 0.1 * 10) / 10;       // x will be 0.3
```
    
### Adding Numbers and Strings

Numbers are added, Strings are concatenated

add a number and a string, the result will be a string concatenation
 
예제
{: .label .label-purple .mt-2}
```js
var x = 10;
var y = "20";
var z = "The result is: " + x + y;  		// z = "The result is 1020"
```

왼쪽에서 오른쪽으로 계산되기 때문에 숫자 계산 먼저 됨

예제
{: .label .label-purple .mt-2}
```js
var x = 10;
var y = 20;
var z = "30";
var result = x + y + z;                     // z = "3030"
```

### Numeric Strings

숫자 문자열은 종종 숫자로 계산됨

나누기, 곱하기, 빼기 다 숫자로 계산 되는데 오직 더하기만 concatenation 10010

예제
{: .label .label-purple .mt-2}
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

숫자가 아니라는걸 나타내는 자바스크립트 `NaN`키워드

숫자가 아닌 문자열로 산술을 시도하면 `NaN` 발생

예제
{: .label .label-purple .mt-2}
```js
var x = 100 / "Apple";  
// x will be NaN (Not a Number)
```

NaN 연산시 숫자는 계산되고 문자는 결합됨

```js
NaN + 숫자 = NaN
NaN + "문자열" = NaN문자열
```

* isNaN() 

    **to find out if a value is a number**

    global JavaScript function

    예제
    {: .label .label-purple .mt-2}
    ```js
    var x = 100 / "Apple";
    isNaN(x);               // returns true because x is Not a Number
    ```

* typeof NaN

    ```js
    typeof NaN;            // returns "number"
    ```

### Infinity

Infinity(or -Infinity) : **가능한 가장 큰 숫자 이외의 숫자를 계산하면 JavaScript가 반환하는 값**

예제
{: .label .label-purple .mt-2}
```js
var x =  2 / 0;       // x will be Infinity
var y = -2 / 0;       // y will be -Infinity
```

* typeof Infinity

    ```js
    typeof Infinity;     // returns "number"
    ```
    
## Hexadecimal 

**16진수**

기본적으로 JavaScript는 숫자를 10 진수 로 표시

숫자 상수 앞에 0x가 있으면 16 진수로 해석

숫자 앞에 7을 07와같이 사용하면 (선행 0으로 작성된 경우의) 숫자를 8 진수로 해석합니다

toString으로 기수 2 에서 기수 36으로 숫자를 출력 할 수 있음

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

`new` 키워드는 복잡한 코드라서 계산속도를 늦추기때문에 권장되지 않음

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

## Number Methods

원래 primitive values 즉 [기본값](https://gekdev.github.io/docs/javascript/4.datatypes/#primitive-data)들은 속성이나 메소드들을 가질 수 없지만 **자바스크립트에서는 기본값도 object라고 취급**하기 때문에 그에 관련된 속성과 메소드들을 제공함


### A Number as a String

* .toString()

    ```js
    var x = 10	//typeof x = number
    x.toString()	//typeof x.toString() = string

    but it doesn’t change it’s own variation 	// so x is still number
    ```

The toFixed() Method:  returns a string, with the number written with a specified number of decimals:
0이면 1의자리를 반올림해서 보여줌, ex) 2면 3의자리까지 반올림해서 2자리까지보여줌(= 3의자리는 그냥 0으로 생략), 뒤의 숫자가 더 없으면 그대로 0을 채워서 보여줌
	var x = 9.656;
	x.toFixed(0);           // returns 10 
	x.toFixed(2);           // returns 9.66 -- toFixed(2) is perfect for working with money.
	x.toFixed(4);           // returns 9.6560
	x.toFixed(6);           // returns 9.656000

The toPrecision() Method: returns a string, with a number written with a specified length:
	var x = 9.656;
	x.toPrecision();        // returns 9.656
	x.toPrecision(2);       // returns 9.7 – (1)이면 10아님 e머시기나옴
	x.toPrecision(4);       // returns 9.656
	x.toPrecision(6);       // returns 9.65600

The valueOf() Method: returns a number as a number.
- is used internally in JavaScript to convert Number objects to primitive values.
All JavaScript data types have a valueOf() and a toString() method.
숫자를 오브젝트로 바꾸지 않은 이상 쓸 이유가 없음!

Converting Variables to Numbers(global JS methods)
● The Number() method : Returns a number, converted from its argument, can be used to convert JavaScript variables to numbers
	Number(true);          // returns 1
	Number(false);         // returns 0
	Number("10");          // returns 10
	Number("  10");        // returns 10
	Number("10  ");        // returns 10
	Number(" 10  ");       // returns 10
	Number("10.33");       // returns 10.33
	Number("10,33");       // returns NaN
	Number("10 33");       // returns NaN
	Number("John");        // returns NaN
If the number cannot be converted, NaN (Not a Number) is returned.
● The parseInt() method : Parses its argument and returns a floating point number, parses a string and returns a whole number. Spaces are allowed. Only the first number is returned:
	parseInt("10");         // returns 10
	parseInt("10.33");      // returns 10(정수만 추출)
	parseInt("10 20 30");   // returns 10
	parseInt("10 years");   // returns 10
	parseInt("years 10");   // returns NaN 
If the number cannot be converted, NaN (Not a Number) is returned.
● The parseFloat() method : Parses its argument and returns an integer, parseFloat() parses a string and returns a number. Spaces are allowed. Only the first number is returned: 소숫점도 추출하는 것
	parseFloat("10");        // returns 10
	parseFloat("10.33");     // returns 10.33
	parseFloat("10 20 30");  // returns 10
	parseFloat("10 years");  // returns 10
	parseFloat("years 10");  // returns NaN
If the number cannot be converted, NaN (Not a Number) is returned.

The Number() Method Used on Dates: 
convert a date to a number:
	Number(new Date("2017-09-30"));    // returns 1506729600000
	The Number() method above returns the number of milliseconds since 1.1.1970.

Number Properties - These properties can only be accessed as Number.MAX_VALUE
● MAX_VALUE		Returns the largest number possible in JavaScript
	var x = Number.MAX_VALUE;	//이상한 숫자나옴
● MIN_VALUE		Returns the smallest number possible in JavaScript
● POSITIVE_INFINITY	Represents infinity (returned on overflow)
	var x = Number.POSITIVE_INFINITY; // infinite
● NEGATIVE_INFINITY	Represents negative infinity (returned on overflow)
● NaN			Represents a "Not-a-Number" value
	var x = Number.NaN;

Number Properties Cannot be Used on Variables
Number properties belongs to the JavaScript's number object wrapper called Number.

var x = 6;
var y = x.MAX_VALUE;    // y becomes undefined
more - https://www.w3schools.com/jsref/jsref_obj_number.asp