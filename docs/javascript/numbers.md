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

## Numbers

### 


18. JavaScript Numbers
Precision 
* Integers (numbers without a period or exponent notation지수표기법) are accurate up to 15 digits.
	var y = 9999999999999999;  // y will be 10000000000000000
* The maximum number of decimals is 17, but floating point arithmetic is not always 100% accurate:
	var x = 0.2 + 0.1;         // x will be 0.30000000000000004
* To solve the problem above, it helps to multiply and divide:
	var x = (0.2 * 10 + 0.1 * 10) / 10;       // x will be 0.3

Adding Numbers and Strings
// warning !! Numbers are added. Strings are concatenated.
	var x = 10;
	var y = 20;
	var z = "The result is: " + x + y;  		// z = “The result is 1020“

Numeric Strings -  strings can have numeric content
나누기, 곱하기, 빼기 다 되는데 더하기는 10010 (because it’s concatenation)
	var x = "100";
	var y = "10";
	var z = x / y;       // z will be 10

NaN(Not a Number) : indicating that a number is not a legal number.
	var x = 100 / "Apple";  // x will be NaN (Not a Number)
However, if the string contains a numeric value , the result will be a number
	var x = 100 / "10";     // x will be 10
global JavaScript function isNaN() to find out if a value is a number: isNaN(x) - true

watchout!!! If you use NaN in a mathematical operation, the result will also be NaN or concatenation
 - like NaN + 3 = NaN / NaN + “3” = NaN3

NaN is a number: typeof NaN returns number

Infinity(or -Infinity)
: is the value JavaScript will return if you calculate a number outside the largest possible number.
Division by 0 (zero) also generates Infinity	
참고~ https://www.w3schools.com/js/tryit.asp?filename=tryjs_numbers_infinity

Infinity is a number: typeof Infinity returns number.

Hexadecimal(toString으로 바꾼 진법과 유사.. 아래에 나와있음)
	var x = 0xFF;        // x will be 255
https://www.w3schools.com/js/js_numbers.asp

Numbers Can be Objects – don’t 
numbers are primitive values created from literals: but numbers can also be defined as objects with the keyword new:
	var x = 500;             
	var y = new Number(500);

// (x == y) is true because x and y have equal values but x === y – false
and also objects cannot be compared (object === object -> false)

19. JavaScript Number Methods
The toString() Method : a number as a string
	var x = 10	//typeof x = number
	x.toString()	//typeof x.toString() = string
	but it doesn’t change it’s own variation 	// so x is still number

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