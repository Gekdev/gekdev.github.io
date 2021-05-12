---
layout: default
title: Type Conversion
parent: Data types
grand_parent: JavaScript
nav_order: 3
---
 
# Type Conversion
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Type Conversion Technic

**JavaScript 변수는 새 변수 및 다른 데이터 유형으로 변환 할 수 있음**

* JavaScript function을 사용

* JavaScript 자체에 의해 자동으로

### [Numbers to Strings](https://gekdev.github.io/docs/javascript/numbers/properties_methods/#converting-number-as-a-string)

* 전역 메서드 String()

    &#9656; 모든 유형의 숫자, 리터럴, 변수 또는 표현식에 사용

    예시
    {: .label .label-purple .mt-2}
    ```js
    String(x)
    String(123)
    String(100+23)
    ```

* Number 메서드 toString()

    예시
    {: .label .label-purple .mt-2}
    ```js
    x.toString()
    (123).toString()
    (100 + 23).toString()
    ```
    
### Booleans to Strings

* 전역 메서드 String()

    예시
    {: .label .label-purple .mt-2}
    ```js
    String(false)      // returns "false"
    String(true)       // returns "true"
    ```
    
* Boolean 메서드 toString()

    예시
    {: .label .label-purple .mt-2}
    ```js
    false.toString()   // returns "false"
    true.toString()    // returns "true"
    ```

### [Dates to Strings](https://gekdev.github.io/docs/javascript/dates/get_set_methods/#date-get-methods)

* 전역 메서드 String()

    예시
    {: .label .label-purple .mt-2}
    ```js
    String(Date())  // returns "Thu Jul 17 2014 15:38:19 GMT+0200 (W. Europe Daylight Time)"
    ```
    
* Dates 메서드 toString()

    예시
    {: .label .label-purple .mt-2}
    ```js
    Date().toString()  // returns "Thu Jul 17 2014 15:38:19 GMT+0200 (W. Europe Daylight Time)"
    ```

### [Strings to Numbers](https://gekdev.github.io/docs/javascript/numbers/properties_methods/#converting-variables-to-numbers)

#### The Unary + Operator

**단항 연산자**

&#9656; + 연산자는 숫자에 변수를 변환

&#9656; 변수를 변환 할 수 없는 경우에도 숫자가되지만 값은 NaN

예시
{: .label .label-purple .mt-2}
```js
var y = "5";      // y is a string
var x = + y;      // x is a number

var z = "John";   // z is a string
var q = + z;      // q is a number (NaN)
```

### [Booleans to Numbers](https://gekdev.github.io/docs/javascript/numbers/properties_methods/#number)

* 전역 메서드 Number()

    예시
    {: .label .label-purple .mt-2}
    ```js
    Number(false)     // returns 0
    Number(true)      // returns 1
    ```

### Dates to Numbers

* 전역 메서드 Number()

    예시
    {: .label .label-purple .mt-2}
    ```js
    d = new Date();
    Number(d)          // returns 1404568027739
    ```
    
* 날짜 메서드 getTime()

    예시
    {: .label .label-purple .mt-2}
    ```js
    d = new Date();
    d.getTime()        // returns 1404568027739
    ```

---

## Automatic Conversion

## Type Conversion

**JavaScript가 잘못된 데이터 유형에 대해 작동하려고하면 값을 올바른 유형으로 변환하려고 시도**

예시
{: .label .label-purple .mt-2}
```js
5 + null    // returns 5         because null is converted to 0
"5" + null  // returns "5null"   because null is converted to "null"
"5" + 2     // returns "52"      because 2 is converted to "2"
"5" - 2     // returns 3         because "5" is converted to 5
"5" * "2"   // returns 10        because "5" and "2" are converted to 5 and 2
```

### String Conversion

**객체나 변수를 출력 하려고 할 때 자동으로 변수의 toString() 함수를 호출**

예시
{: .label .label-purple .mt-2}
```js
document.getElementById("demo").innerHTML = myVar;

// if myVar = {name:"Fjohn"}  // toString converts to "[object Object]"
// if myVar = [1,2,3,4]       // toString converts to "1,2,3,4"
// if myVar = new Date()      // toString converts to "Fri Jul 18 2014 09:08:55 GMT+0200"
// if myVar = 123             // toString converts to "123"
// if myVar = true            // toString converts to "true"
// if myVar = false           // toString converts to "false"
```

---

## JavaScript Type Conversion Table

| Original Value 	| Converted to Number | Converted to String	| Converted to Boolean |
|:------------------|:--------------------|:--------------------|:---------------------|
| false	            | 0                   | "false"	            | false                |	
| true	            | 1                   |	"true" 	            | true	               |
| 0	                | 0                   |	"0"		            | false                |	
| 1	                | 1                   |	"1"		            | true	               |	
| "0"	            | 0                   |	"0"		            | true	               |	
| "000"	            | 0                   |	"000"		        | true	               |	
| "1"	            | 1                   |	"1"		            | true	               |	
| NaN	            | NaN	              | "NaN"		        | false                |	
| Infinity	        | Infinity            |	"Infinity"		    | true	               |	
| -Infinity	        | -Infinity	          | "-Infinity"		    | true	               |	
| ""	            | 0                   |	""		            | false                |	
| "20"	            | 20                  |	"20"		        | true	               |	
| "twenty"	        | NaN	              |	"twenty"		    | true	               |	
| [ ]	            | 0	                  | ""		            | true	               |	
| [20]	            | 20	              | "20"		        | true	               |	
| [10,20]	        | NaN	              | "10,20"		        | true	               |	
| ["twenty"]	    | NaN	              | "twenty"		    | true	               |	
| ["ten","twenty"]	| NaN	              | "ten,twenty"		| true	               |	
| function(){}	    | NaN	              | "function(){}"		| true	               |	
| { }	            | NaN	              | "[object Object]"	| true	               |	
| null	            | 0	                  | "null"		        | false                |	
| undefined	        | NaN	              | "undefined"		    | false                |

