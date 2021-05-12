---
layout: default
title: Checking Data type
parent: Data types
grand_parent: JavaScript
nav_order: 2
---
 
# Checking Data type
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Two ways to Check Data type

### [The typeof Operator](https://gekdev.github.io/docs/javascript/operator/#type-operators)

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

&#9656; NaN의 데이터 유형은 숫자

&#9656; 배열의 데이터 유형은 객체

&#9656; 날짜의 데이터 유형은 객체

&#9656; null의 데이터 유형은 객체

&#9656; 정의되지 않은 변수의 데이터 유형이 정의되지 않음

&#9656; 값이 할당되지 않은 변수의 데이터 유형도 정의되지 않음

&#8594; function는 object지만 typeof 연산자에서는 function이라고 나옴

#### The Data Type of typeof

연산자에는 데이터 유형이 없지만, **typeof 연산자의 데이터 유형은 문자열**

### The constructor Property

**생성자 속성**

&#9656; constructor속성은 모든 JavaScript 변수에 대한 생성자 함수를 반환

예시
{: .label .label-purple .mt-2}
```js
"John".constructor                // Returns function String()  {[native code]}
(3.14).constructor                // Returns function Number()  {[native code]}
false.constructor                 // Returns function Boolean() {[native code]}
[1,2,3,4].constructor             // Returns function Array()   {[native code]}
{name:'John',age:34}.constructor  // Returns function Object()  {[native code]}
new Date().constructor            // Returns function Date()    {[native code]}
function () {}.constructor        // Returns function Function(){[native code]}
```

#### Find out if an object is an Array

문자열로 찾거나 생성자 속성으로 찾는 아래 두가지 방법이 있음

```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo").innerHTML = isArray(fruits);

function isArray(myArray) {
    //ver1. contains the word "Array"
    return myArray.constructor.toString().indexOf("Array") > -1;
    //ver2. check if the object is an Array function
    return myArray.constructor === Array;
}
```

#### Find out if an object is a Date

문자열로 찾거나 생성자 속성으로 찾는 아래 두가지 방법이 있음

```js
var myDate = new Date();
document.getElementById("demo").innerHTML = isDate(myDate);

function isDate(myDate) {
    //ver1. contains the word "Date"
    return myDate.constructor.toString().indexOf("Date") > -1;
    //ver2. check if the object is a Date function
    return myDate.constructor === Date;               
}
```
