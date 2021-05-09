---
layout: default
title: Properties and Methods
parent: Numbers
grand_parent: JavaScript
nav_order: 1
---

# Numbers Methods and Properties
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Number Object Properties

**Number라는 숫자 객체(Object)에 속한 속성들**

&#9656; can only be accessed like `Number.property` form

&#8594; 따라서 아래와 같이 변수에는 숫자 속성을 사용할 수 없음

```js
var x = 6;
var y = x.MAX_VALUE;    // y becomes undefined
```

### Returning Specific Number

#### MAX_VALUE

**JavaScript에서 가능한 가장 큰 숫자를 반환**

syntax
{: .label .mt-2}
```js
var x = Number.MAX_VALUE;
//1.7976931348623157e+308
```

#### MIN_VALUE	

**JavaScript에서 가능한 가장 낮은 숫자를 반환**

syntax
{: .label .mt-2}
```js
var x = Number.MIN_VALUE;
//5e-324
```

#### POSITIVE_INFINITY

**양수 무한대**

syntax
{: .label .mt-2}
```js
var x = Number.POSITIVE_INFINITY;

or 
var x = 1 / 0;

//Infinity
```

#### NEGATIVE_INFINITY

**음수 무한대**

syntax
{: .label .mt-2}
```js
var x = Number.NEGATIVE_INFINITY;

or 
var x = -1 / 0;

//-Infinity
```

#### NaN			

**숫자가 유효한 숫자가 아님을 나타내는 JavaScript 예약어**

&#9656; 숫자가 아닌 문자열로 산술을 하면 `NaN` 발생

syntax
{: .label .mt-2}
```js
var x = Number.NaN;

or 
var x = 100 / "Apple";  // x will be NaN (Not a Number)
```

---

## Number Methods

원래 primitive values 즉 [기본값](https://gekdev.github.io/docs/javascript/4.datatypes/#primitive-data)들은 속성이나 메소드들을 가질 수 없지만 **자바스크립트에서는 기본값도 object라고 취급**하기 때문에 그에 관련된 속성과 메소드들을 제공함

### Converting number as a String

#### .toString()

**숫자를 문자열로 반환**

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
num.toString();
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
num.toFixed();
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

&#9656; 매개변수는 선택사항(optional)이여서 규정하지 않으면 반올림하지 않음

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
num.toExponential();
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
num.toPrecision();
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

&#9656; 숫자를 객체로 바꾸지 않은 이상 쓸 이유가 없음

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
num.valueOf();
</div>
```js
var x = 123;
x.valueOf();            // returns 123 from variable x
(123).valueOf();        // returns 123 from literal 123
(100 + 23).valueOf();   // returns 123 from expression 100 + 23
```

!Note
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
All JavaScript data types have a valueOf() and a toString() method.
</div>

### Converting Variables to Numbers

숫자 메소드가 아니라 **global JS methods**

&#8594; JavaScript global methods can be used on all JavaScript data types

#### .Number()

**JavaScript 변수를 숫자로 변환하는 데 사용**

&#9656; 숫자를 변환 할 수 없으면 `NaN`이 반환

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
Number(value);
</div>
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

&#9656; 숫자를 변환 할 수 없으면 `NaN`이 반환

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
parseInt("string");
</div>
```js
parseInt("10");         // returns 10
parseInt("10.33");      // returns 10(정수만 추출)
parseInt("10 20 30");   // returns 10
parseInt("10 years");   // returns 10
parseInt("years 10");   // returns NaN 
```

####  .parseFloat()

**문자열을 구문 분석하고 숫자를 반환**

&#9656; 공백 허용, 하지만 첫 번째 숫자만 반환

&#9656; .parseInt와 다른점은 소숫점도 추출한다는것

&#9656; 숫자를 변환 할 수 없으면 `NaN`이 반환

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
parseFloat("string");
</div>
```js
parseFloat("10");        // returns 10
parseFloat("10.33");     // returns 10.33
parseFloat("10 20 30");  // returns 10
parseFloat("10 years");  // returns 10
parseFloat("years 10");  // returns NaN
```

---

## Complete Number Reference

The reference contains descriptions and examples of all Number properties and methods

<span class="fs-2">
[더 찾아보기](https://www.w3schools.com/jsref/jsref_obj_number.asp){: .btn  .btn-outline}
</span>
