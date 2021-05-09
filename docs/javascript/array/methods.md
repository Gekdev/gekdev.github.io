---
layout: default
title: Methods
parent: Arrays
grand_parent: JavaScript
nav_order: 2
---

# Array Methods
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Changing Array Elements

### Adding, Shifting and Deleting Elements

#### push() 

**배열의 끝에 새로운 요소를 추가하거나 새로운 배열 길이를 반환**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
arr.push(str);
</div>
```js
//추가
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.push("Kiwi");       //  Adds a new element ("Kiwi") to fruits

//반환
var fruits = ["Banana", "Orange", "Apple", "Mango"];
var x = fruits.push("Kiwi");   //  x = 5
```

Same result different way
{: .label .mt-2}
<div class="code-example" markdown="1">
arr[arr.length]도 동일하게 작동함
</div>
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

#### unshift()

**배열의 처음에 새 요소를 추가하고 이전 요소를 뒤로 밀음, 새로운 배열 길이 반환**

&#9656; 첫 번째 요소대신 마지막 요소에서 작업하는 push()와 비슷함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
arr.unshift(str);
</div>
```js
//추가
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.unshift("Lemon");    // Adds a new element "Lemon" to fruits

//반환
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.unshift("Lemon");    // Returns 5
```

#### pop()

**배열에서 마지막 요소를 제거하거나 튀어나온 요소를 리턴**

&#9656; 리턴하고 싶으면 변수에 값을 담아서 사용해야함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
arr.pop();
</div>
```js
//제거
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.pop();              // Removes the last element ("Mango") from fruits

//리턴
var fruits = ["Banana", "Orange", "Apple", "Mango"];
var x = fruits.pop();      // x = "Mango"
```

#### shift() 

**첫 번째 배열 요소를 제거하고 다른 모든 요소를 더 낮은 인덱스로 이동, 전환된 문자열을 리턴** 

&#9656; 첫 번째 요소대신 마지막 요소에서 작업하는 pop()과 비슷함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
arr.shift();
</div>
```js
//제거
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.shift();            // Removes the first element "Banana" from fruits

//리턴
var fruits = ["Banana", "Orange", "Apple", "Mango"];
var x = fruits.shift();    // x = "Banana"
```

#### delete operator 

JavaScript 배열은 객체이므로 **JavaScript 연산자 `delete`를 사용하여 요소를 삭제가능**

&#9656; 그냥 구멍내버리고 채우지않음 (구멍낸 경우 arr.[숫자] = “” 로 채워야함)

&#9656; 그래서 pop() 이나 shift()를 대신 사용함

&#9656; splice()도 요소를 지우는데 사용가능함

예제
{: .label .label-purple .mt-2}
```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
delete fruits[0];           // Changes the first element in fruits to undefined
```

### Splicing an Array Elements

#### splice()

**배열에 항목을 추가/제거하고 제거 된 항목을 반환**

&#9656; 원래 배열을 변경함

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
arr.splice(index, howmany(optional), item1(optional), ....., itemX)

&#9656; index : 어디서부터 추가하거나 지워야하는지

&#9656; howmany : 몇개의 요소가 지워져야 하는지

&#9656; item1... : 어떤 요소가 들어가야 하는지
</div>
```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.splice(2, 0, "Lemon", "Kiwi");

//Banana,Orange,Lemon,Kiwi,Apple,Mango
```

&#9656; 인덱스0 으로 삭제만 이용하는 방법도 있다 - 오류 x 좋은방법임!

```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.splice(0, 1);        // Removes the first element of fruits
```

---

## Creating New Arrays

### Merging (Concatenating) Arrays

#### concat()

**기존 배열을 병합(연결)하여 새 배열**을 만듦

&#9656; 매개변수로 배열을 가지고 있는 변수를 받을수도 있고, 배열을 바로 받을수도 있음

&#9656; 매개변수 개수는 무한(,를 사용해서 넣고싶은 만큼 넣어도 됨)

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var arr3 = arr1.concat(arr2);
</div>
```js
var myGirls = ["Cecilie", "Lone"];
var myBoys = ["Emil", "Tobias", "Linus"];
var myChildren = myGirls.concat(myBoys);   
// Concatenates (joins) myGirls and myBoys

...

arr1.concat(arr2, arr3, "Peter");
```

### Slicing an Array

#### slice()

**배열의 일부를 새로운 배열로 잘라냄**

Syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
array.slice(start, end)

&#9656; start : 어디서부터 잘라낼지 결정, 매개변수와 맞는 인덱스에 있는 요소부터 시작하고 자름 (포함)

&#9656; end : 매개변수(optional)는 종료 인수 선택 (포함하지 않음)
</div>
```js
var fruits = ["Banana", "Orange", "Lemon", "Apple", "Mango"];
var citrus = fruits.slice(1);
//citrus = Orange, Lemon, Apple, Mango

var citrus = fruits.slice(1,3);
//citrus = Orange,Lemon
```

---

## Other Arrays Methods

### Converting Arrays to Strings

#### toString() 

**모든 배열 요소를 쉼표로 구분 한 문자열로 변환**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
arr.toString();
</div>
```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo").innerHTML = fruits.toString();
//Banana,Orange,Apple,Mango
```
  
Automatic toString()
{: .label .mt-2}
<div class="code-example" markdown="1">

**배열을 부르면 배열을 쉼표로 구분된 문자열로 자동 변환해서 출력함**

&#8594; 자동으로 toString()메소드가 사용되는 것
</div>
```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];

//fruits.toString(); = fruits;
```

!Note
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
All JavaScript data types have a valueOf() and a toString() method.
</div>

#### join() 

**모든 배열 요소를 지정한 구분자로 구분한 문자열로 변환**

&#9656; 매개변수를 지정하지 않으면 ,로 구분함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
fruits.join("특수문자");
</div>
```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo").innerHTML = fruits.join(" * ");
//Banana * Orange * Apple * Mango
```

---

## Complete Array Reference

The reference contains descriptions and examples of all Array properties and methods.

<span class="fs-2">
[더 찾아보기](https://www.w3schools.com/jsref/jsref_obj_array.asp){: .btn  .btn-outline}
</span>
