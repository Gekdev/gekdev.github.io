---
layout: default
title: Iteration
parent: Arrays
grand_parent: JavaScript
nav_order: 4
---

# Array Iteration
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Array Iteration

**배열 반복 방법은 모든 배열 항목에서 작동함**

### forEach()

**각 하나의 원소를 뽑아내는 방법**

&#9656; 각 배열 요소에 대해 함수(콜백 함수)를 한 번 호출

&#9656; 3 개의 인수가 사용됨

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
arr.forEach(value, index, array);

&#9656; The item value

&#9656; The item index       //생략가능

&#9656; The array itself     //생략가능
</div>
```js
var txt = "";
var numbers = [45, 4, 9, 16, 25];
numbers.forEach(myFunction);
document.getElementById("demo").innerHTML = txt;

function myFunction(value, index, array) {
  txt = txt + value + "<br>"; 
}
```

<span class="fs-2">
[W3School](https://www.w3schools.com/js/tryit.asp?filename=tryjs_array_foreach){: .btn  .btn-outline .mt-2}
</span>

### map()

**기존 배열의 value로 새로운 배열을 생성**

&#9656; 값이 없는 배열 요소에 대한 함수를 실행하지 않음

&#9656; 원래 배열을 변경하지 않음

&#9656; 3 개의 인수가 사용됨

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
arr.map(value, index, array);

&#9656; The item value

&#9656; The item index       //생략가능

&#9656; The array itself     //생략가능
</div>
```js
var numbers1 = [45, 4, 9, 16, 25];
var numbers2 = numbers1.map(myFunction);

document.getElementById("demo").innerHTML = numbers2;

function myFunction(value, index, array) {
  return value * 2;
}
```

<span class="fs-2">
[W3School](https://www.w3schools.com/js/tryit.asp?filename=tryjs_array_map){: .btn  .btn-outline .mt-2}
</span>

### filter()

**테스트를 통과하는 배열 요소를 사용하여 새 배열을 만듦**

&#9656; 3개의 인수가 사용됨

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
arr.map(value, index, array);

&#9656; The item value

&#9656; The item index       //생략가능

&#9656; The array itself     //생략가능
</div>
```js
var numbers = [45, 4, 9, 16, 25];
var over18 = numbers.filter(myFunction);

document.getElementById("demo").innerHTML = over18;

function myFunction(value, index, array) {
  return value > 18;
}
```

<span class="fs-2">
[W3School](https://www.w3schools.com/js/tryit.asp?filename=tryjs_array_filter){: .btn  .btn-outline .mt-2}
</span>

### reduce() 

**단일 값을 생성(감소)하기 위해 각 배열 요소에서 함수를 실행**

&#9656; 배열에서 왼쪽에서 오른쪽으로 작동

&#9656; 원래 배열을 줄이지 않음

&#9656; 4개의 인수가 사용됨

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
arr.reduce(total, value, index, array);

&#9656; The total (the initial value / previously returned value)

&#9656; The item value

&#9656; The item index       //생략가능

&#9656; The array itself     //생략가능
</div>
```js
var numbers = [45, 4, 9, 16, 25];
var sum = numbers.reduce(myFunction);
//var sum = numbers1.reduce(myFunction, 100); // 전체 더한거에서 100추가

document.getElementById("demo").innerHTML = "The sum is " + sum;
                //합계 (초기 값 / 이전에 반환 된 값), 나머지값, 번호, 전체배열
function myFunction(total, value, index, array) {
  return total + value; //처음 값부터 끝까지 모두 더하기
}
```

<span class="fs-2">
[W3School](https://www.w3schools.com/js/tryit.asp?filename=tryjs_array_reduce){: .btn  .btn-outline .mt-2}
</span>

### reduceRight()

reduce()와 모두 같은데 그저 첫 번째 값과 나머지값의 순서가 거꾸로 간다(right to left)

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
arr.reduceRight(total, value, index, array);

&#9656; The total (the initial value / previously returned value)

&#9656; The item value

&#9656; The item index       //생략가능

&#9656; The array itself     //생략가능
</div>
```js
var numbers = [45, 4, 9, 16, 25];
var sum = numbers.reduceRight(myFunction);

document.getElementById("demo").innerHTML = "The sum is " + sum;

function myFunction(total, value, index, array) {
  return total + value;
}
```

<span class="fs-2">
[W3School](https://www.w3schools.com/js/tryit.asp?filename=tryjs_array_reduce_right){: .btn  .btn-outline .mt-2}
</span>

### every()

**모든 배열 값이 테스트를 통과했는지 확인**

&#9656; 3개의 인수가 사용됨

&#9656; 콜백 함수가 첫 번째 매개 변수만 사용하는 경우 다른 매개 변수는 생략 할 수 있음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
arr.every(value, index, array);

&#9656; The item value

&#9656; The item index       //생략가능

&#9656; The array itself     //생략가능
</div>
```js
var numbers = [45, 4, 9, 16, 25];
var allOver18 = numbers.every(myFunction);

document.getElementById("demo").innerHTML = "All over 18 is " + allOver18;

function myFunction(value, index, array) {
  return value > 18;
}
```

<span class="fs-2">
[W3School](https://www.w3schools.com/js/tryit.asp?filename=tryjs_array_every){: .btn  .btn-outline .mt-2}
</span>

### some() 

**일부 배열 값이 테스트를 통과했는지 확인**

&#9656; every()는 모두 참이여야 true지만 이거는 하나라도 참이면 true

&#9656; 3개의 인수가 사용됨

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
arr.map(value, index, array);

&#9656; The item value

&#9656; The item index       //생략가능

&#9656; The array itself     //생략가능
</div>
```js
var numbers = [45, 4, 9, 16, 25];
var someOver18 = numbers.some(myFunction);

document.getElementById("demo").innerHTML = "Some over 18 is " + someOver18;

function myFunction(value, index, array) {
  return value > 18;
}
```

<span class="fs-2">
[W3School](https://www.w3schools.com/js/tryit.asp?filename=tryjs_array_some){: .btn  .btn-outline .mt-2}
</span>

### indexOf() 

**배열에서 요소 값을 검색하고 해당 위치를 반환**

&#9656; 항목을 찾을 수 없으면 -1, 두개 이상이면 첫번째 요소 위치 값을 반환함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
arr.indexOf(item, start);

&#9656; 첫번째 항목의 위치는 0이고 두번째 항목의 위치는 1

&#9656; 두번째 매개변수는 선택, 시작 위치를 고를 수 있음

&#9656; 두번째 매개변수의 Negative values will start at the given position counting from the end, and search to the end
</div>
```js
var fruits = ["Apple", "Orange", "Apple", "Mango"];
var a = fruits.indexOf("Apple");
document.getElementById("demo").innerHTML = "Apple is found in position " + a;
```

<span class="fs-2">
[W3School](https://www.w3schools.com/js/tryit.asp?filename=tryjs_array_indexof){: .btn  .btn-outline .mt-2}
</span>

### lastIndexOf()

Array.indexOf()와 비슷하지만 **지정된 요소가 마지막으로 나타나는 위치를 반환**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
arr.lastIndexOf(item, start);

&#9656; 첫번째 항목의 위치는 0이고 두번째 항목의 위치는 1

&#9656; 두번째 매개변수는 선택, 시작 위치를 고를 수 있음

&#9656; 두번째 매개변수의 Negative values will start at the given position counting from the end, and search to the end
</div>
```js
var fruits = ["Apple", "Orange", "Apple", "Mango"];
var a = fruits.lastIndexOf("Apple");
document.getElementById("demo").innerHTML = "Apple is found in position " + (a + 1);
```

<span class="fs-2">
[W3School](https://www.w3schools.com/js/tryit.asp?filename=tryjs_array_lastindexof){: .btn  .btn-outline .mt-2}
</span>

### find()

**테스트 함수를 통과 한 첫 번째 배열 요소의 value를 리턴**

&#9656; 3개의 인수가 사용됨

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
arr.find(value, index, array);

&#9656; The item value

&#9656; The item index       //생략가능

&#9656; The array itself     //생략가능
</div>
```js
var numbers = [4, 9, 16, 25, 29];
var first = numbers.find(myFunction);

document.getElementById("demo").innerHTML = "First number over 18 is " + first;

function myFunction(value, index, array) {
  return value > 18;
}
```

<span class="fs-2">
[W3School](https://www.w3schools.com/js/tryit.asp?filename=tryjs_array_find){: .btn  .btn-outline .mt-2}
</span>

### findIndex()

**테스트 함수를 통과 한 첫 번째 배열 value의 index만 추출**

&#9656; 3개의 인수가 사용됨

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
arr.findIndex(value, index, array);

&#9656; The item value

&#9656; The item index       //생략가능

&#9656; The array itself     //생략가능
</div>
```js
var numbers = [4, 9, 16, 25, 29];
var first = numbers.findIndex(myFunction);

document.getElementById("demo").innerHTML = "First number over 18 has index " + first;

function myFunction(value, index, array) {
  return value > 18;
}
```

<span class="fs-2">
[W3School](https://www.w3schools.com/js/tryit.asp?filename=tryjs_array_find_index){: .btn  .btn-outline .mt-2}
</span>

