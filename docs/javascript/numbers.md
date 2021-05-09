---
layout: default
title: Numbers
parent: JavaScript
nav_order: 4
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

## Number Methods

원래 primitive values 즉 [기본값](https://gekdev.github.io/docs/javascript/4.datatypes/#primitive-data)들은 속성이나 메소드들을 가질 수 없지만 **자바스크립트에서는 기본값도 object라고 취급**하기 때문에 그에 관련된 속성과 메소드들을 제공함

### Converting number as a String

#### .toString()

**숫자를 문자열로 반환**

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
num.toString()
</div>
```js
var x = 10	//typeof x = number
x.toString()	//typeof x.toString() = string

var x = 123;
x.toString();            // returns 123 from variable x
(123).toString();        // returns 123 from literal 123
(100 + 23).toString();   // returns 123 from expression 100 + 23

but it doesn’t change it’s own variation 	// so x is still number
```

#### .toFixed() 

**소수 자릿수로 쓴 숫자만큼 문자열로 반환** 

&#9656; 매개변수 까지 반올림

&#9656; 뒤의 숫자가 더 없으면 그대로 0을 채워서 보여줌

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
num.toFixed() 
</div>
```js
var x = 9.656;
x.toFixed(0);           // returns 10
x.toFixed(2);           // returns 9.66
x.toFixed(4);           // returns 9.6560
x.toFixed(6);           // returns 9.656000
```

#### .toExponential()

**지수 표기법을 사용하여 숫자를 반올림하고 쓴 문자열을 반환**

&#9656; 매개 변수는 소수점 뒤의 문자 수를 정의

&#9656; 매개변수는 선택사항(optional)이여서 규정하지 않으면 반올림하지않음

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
num.toExponential()
</div>
```js
var x = 9.656;
x.toExponential(2);     // returns 9.66e+0
x.toExponential(4);     // returns 9.6560e+0
x.toExponential(6);     // returns 9.656000e+0
```

#### .toPrecision()

**지정된 길이로 쓴 숫자로 문자열을 반환**

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
num.toPrecision()
</div>
```js
var x = 9.656;
x.toPrecision();        // returns 9.656
x.toPrecision(2);       // returns 9.7 – (1)이면 10아님 e머시기나옴
x.toPrecision(4);       // returns 9.656
x.toPrecision(6);       // returns 9.65600
```

### Converting Number as a Number

#### .valueOf()

**숫자를 숫자로 반환**

숫자를 객체로 바꾸지 않은 이상 쓸 이유가 없음

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
num.valueOf()
</div>
```js
var x = 123;
x.valueOf();            // returns 123 from variable x
(123).valueOf();        // returns 123 from literal 123
(100 + 23).valueOf();   // returns 123 from expression 100 + 23
```

!Note
{: .label .mt-2}
<div class="code-example" markdown="1">
All JavaScript data types have a valueOf() and a toString() method.
</div>

### Converting Variables to Numbers

숫자 메소드가 아니라 **global JS methods**

&#8594; JavaScript global methods can be used on all JavaScript data types

#### .Number()

**JavaScript 변수를 숫자로 변환하는 데 사용**

```js
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
```

&#8594; 숫자를 변환 할 수 없으면 `NaN`이 반환

The Number() Method Used on Dates
{: .label .mt-2}
<div class="code-example" markdown="1">
**convert a date to a number**

returns the number of milliseconds since 1.1.1970
</div>
```js
Number(new Date("2017-09-30"));    // returns 1506729600000
```

#### .parseInt()

**문자열을 구문 분석하고 정수를 반환**

&#9656; 공백 허용, 하지만 첫 번째 숫자만 반환

```js
parseInt("10");         // returns 10
parseInt("10.33");      // returns 10(정수만 추출)
parseInt("10 20 30");   // returns 10
parseInt("10 years");   // returns 10
parseInt("years 10");   // returns NaN 
```

&#8594; 숫자를 변환 할 수 없으면 `NaN`이 반환

* .parseFloat()

    **문자열을 구문 분석하고 숫자를 반환**
    
    공백 허용, 하지만 첫 번째 숫자만 반환
    
    소숫점도 추출하는 메소드
    
    ```js
    parseFloat("10");        // returns 10
	parseFloat("10.33");     // returns 10.33
	parseFloat("10 20 30");  // returns 10
	parseFloat("10 years");  // returns 10
	parseFloat("years 10");  // returns NaN
    ```
    
    &#8594; 숫자를 변환 할 수 없으면 `NaN`이 반환

### Number Properties

Number라는 숫자 객체에 속한 속성들

**can only be accessed like `Number.property` form**

따라서 변수에는 숫자 속성을 사용할 수 없음

```js
var x = 6;
var y = x.MAX_VALUE;    // y becomes undefined
```

* MAX_VALUE

    **JavaScript에서 가능한 가장 큰 숫자를 반환**
    
    ```js
	var x = Number.MAX_VALUE;
    //1.7976931348623157e+308
    ```

* MIN_VALUE	

    **JavaScript에서 가능한 가장 낮은 숫자를 반환**
    
    ```js
    var x = Number.MIN_VALUE;
    //5e-324
    ```

* POSITIVE_INFINITY

    **양수 무한대**
    
    ```js
    var x = Number.POSITIVE_INFINITY;

    or 
    var x = 1 / 0;

    //Infinity
    ```
    
* NEGATIVE_INFINITY

    **음수 무한대**
        
    ```js
    var x = Number.NEGATIVE_INFINITY;

    or 
    var x = -1 / 0;

    //-Infinity
    ```
    
* NaN			

    **숫자가 유효한 숫자가 아님을 나타내는 JavaScript 예약어**
    
    숫자가 아닌 문자열로 산술을 하면 `NaN` 발생
    
    ```js
	var x = Number.NaN;
    
    or 
    var x = 100 / "Apple";  // x will be NaN (Not a Number)
    ```

### Complete Number Reference

The reference contains descriptions and examples of all Number properties and methods

<span class="fs-2">
[더 찾아보기](https://www.w3schools.com/jsref/jsref_obj_number.asp){: .btn  .btn-outline}
</span>
