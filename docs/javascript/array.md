---
layout: default
title: Arrays
parent: JavaScript
nav_order: 5
has_children: true
---

# JavaScript Arrays
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Arrays Basic

### What is an Array?

**한번에 여러가지의 value를 담을 수 있는 특별한 변수**, 목적도 같다

&#9656; **프로퍼티(name)로 숫자(인덱스)를 사용하는 특별한 유형의 객체**이다

### Creating an Array

**배열 리터럴을 사용하는 것이 JavaScript 배열을 만드는 가장 쉬운 방법**

&#9656; 줄바꿈과 공백은 규칙만 지킨다면 여러줄에 걸쳐 사용가능

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var array_name = [item1, item2, ...];
</div>

Note!
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
var a = new Array(“”,“”,“”...); 도 위와 같이 정확하게 동일한 배열을 만드는 방법

하지만 단순성, 가독성, 실행속도를 위해 사용 자제해야 함
</div>

### Avoid new Array()

대신 `[]` 사용하기

```js
var points = new Array();     // Bad
var points = [];              // Good 
```

`new` 키워드는 Array 함수의 매개변수가 **2개 이상**이여야지 제대로 작동하고, 코드를 복잡하게 함

```js
var points = new Array(40);  
points[0] -> undefined	
//because it’s not an Array, just one single element(error)
```

### Associative Arrays

**연관배열**

이름을 가지고 있는 배열을 많은 프로그래밍 언어에서 사용하며 그렇게 명명된 인덱스 배열을 연관배열 이라고 함

&#8594; **자바스크립트는 연관배열을 지원하지 않기 때문에 어떤 인덱스를 사용하고 싶은지에 따라서 명명된 인덱스는 객체, 숫자 인덱스는 배열을 사용하면 됨**

Warning
{: .label .label-red .mt-2}
<div class="code-example" markdown="1">
명명 된 인덱스를 사용하는 경우 JavaScript는 배열을 표준 객체로 재정의, 말 그대로 객체로 정의함

그 후 배열 메소드 및 속성은 잘못된 결과를 생성하니까 사용금지!
</div>

### The Difference Between Arrays and Objects

배열은 숫자 인덱스를 사용, 객체는 명명된 인덱스를 사용

&#9656; 배열은 번호가 매겨진 인덱스를 가진 특별한 종류의 객체

### How to Recognize an Array

`typeof` 오퍼레이터가 object 라고 리턴하기 때문에 문제가 생김

&#9656; 해결 방법: Array.isArray(), own function, instanceof operator

1. **Array.isArray()**
    
    not supported in older browsers
    
    ```js
    Array.isArray(fruits);   
    // returns true
    ```

2. **your own isArray() funtion**
    
    ```js
	function isArray(x) {
	  return x.constructor.toString().indexOf("Array") > -1;
	}

    //returns true if the object prototype contains the word "Array"
    ```
    
3. **instanceof operator**
    
    ```js
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
	fruits instanceof Array;   // returns true

    //returns true if an object is created by a given constructor
    ```
    
### Array Elements Can Be Objects

**배열은 객체이고, 변수는 객체일 수 있어서 동일한 배열에 다른 유형의 변수를 가질 수 있음**

예제
{: .label .label-purple .mt-2}
```js
myArray[0] = Date.now;      //object in array
myArray[1] = myFunction;    //function in array
myArray[2] = myCars;        //array in array
```
