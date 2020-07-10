---
layout: default
title: Arrays
parent: JavaScript
nav_order: 6
has_children: true
---

# JavaScript Arrays
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Arrays

### What is an Array?

**한번에 여러가지의 value를 담을 수 있는 특별한 변수**, 목적도 같음

배열은 **프로퍼티(name)로 숫자(인덱스)**를 사용하는 특별한 유형의 **객체**이다

### Creating an Array

**배열 리터럴을 사용**하는 것이 JavaScript 배열을 만드는 가장 쉬운 방법

줄바꿈과 공백은 규칙만 지킨다면 여러줄에 걸쳐 사용가능

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var array_name = [item1, item2, ...];
</div>

Note!
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
var a = new Array(“”,“”,“”...); 도 위와 같이 정확하게 동일한 배열을 만드는 방법

하지만 단순선, 가독성, 실행속도를 위해 사용 자제
</div>

### Access the Elements

**인덱스 번호로 배열 값에 접근하기**

&#9656; 인덱스는 0부터 시작

&#9656; 배열 전체로 접근하려면 []없이 이름만 사용

```js
var name = a[0];    //0번째 값 가져오기
var name = a        //a배열 전체 가져오기
```

### Change the Elements

**배열 값 바꾸기**

```js
a[0] = “A”          //0번째 배열값을 바꾸기
```

### Array Elements Can Be Objects

배열은 객체이고, 변수는 객체일 수 있어서 동일한 배열에 다른 유형의 변수를 가질 수 있음

```js
myArray[0] = Date.now;      //object in array
myArray[1] = myFunction;    //function in array
myArray[2] = myCars;        //array in array
```

---

## Array Properties and Methods

배열은 정말 좋은 built-in 배열 속성과 메소드가 있다

### The length Property

**배열의 길이 (배열 요소 수)를 반환**

index가 0부터 시작하기 때문에 항상 가장 높은 배열 인덱스보다 하나 이상

```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.length;   // the length of fruits is 4
```

* Accessing the Last Array Element

    ```js
    fruits = ["Banana", "Orange", "Apple", "Mango"];
    var last = fruits[fruits.length - 1];
    ```
    
* Looping Array Elements

    1. for loop

        ```js
        text = "<ul>";
        for (i = 0; i < fruits.length ; i++) {
          text += "<li>" + fruits[i] + "</li>";
        }
        text += "</ul>";
        ```

    2. Array.forEach()

        ```js
        var fruits, text;
        fruits = ["Banana", "Orange", "Apple", "Mango"];

        text = "<ul>";
        fruits.forEach(myFunction);
        text += "</ul>";

        function myFunction(value) {
          text += "<li>" + value + "</li>";
        }
        ```

### Adding Array Elements

push() : **배열에 새 요소를 추가**

arr[arr.length] 도 동일

```js
fruits.push("Lemon")

fruits[fruits.length] = "Lemon";
```

Warning
{: .label .label-red .mt-2}
<div class="code-example" markdown="1">
인덱스가 높은 요소를 추가하면 배열에 정의되지 않은 "구멍"이 생성 될 수 있음

그 "구멍"의 값은 undefined
</div>

### Associative Arrays

**연관배열**

이름을 가지고 있는 배열을 많은 프로그래밍 언어에서 사용하고 명명 된 인덱스 배열을 연관 배열이라고 하지만, 자바스크립트에서는 인덱스만이 배열의 이름. 따라서 자바스크립트는 연관배열을 지원하지 않기 때문에 어떤 인덱스를 사용하고 싶은지에 따라서 명명된 인덱스는 객체, 숫자 인덱스는 배열을 사용하면 됨

Warning
{: .label .label-red .mt-2}
<div class="code-example" markdown="1">
명명 된 인덱스를 사용하는 경우 JavaScript는 배열을 표준 객체로 재정의, 말 그대로 객체로 정의함

그 후 배열 메소드 및 속성은 잘못된 결과 를 생성하니까 사용금지
</div>

### The Difference Between Arrays and Objects

배열 은 숫자 인덱스를 사용, 체 는 명명 된 인덱스를 사용

배열은 번호가 매겨진 인덱스를 가진 특별한 종류의 객체

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

### How to Recognize an Array

`typeof` 오퍼레이터가 object 라고 리턴하기 때문에 문제가 생김

해결 방법: Array.isArray(), owun function, instanceof operator

1. Array.isArray()
    
    not supported in older browsers
    
    ```js
    Array.isArray(fruits);   
    // returns true
    ```

2. your own isArray() funtion
    
    ```js
	function isArray(x) {
	  return x.constructor.toString().indexOf("Array") > -1;
	}
    ```
    
    returns true if the object prototype contains the word "Array"
    
3. instanceof operator 
    
    ```js
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
	fruits instanceof Array;   // returns true
    ```
    
    returns true if an object is created by a given constructor

