---
layout: default
title: Iteration
parent: Arrays
grand_parent: JavaScript
nav_order: 4
---

# JavaScript Array Iteration
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Array Iteration

### Array.forEach ()

각 배열 요소에 대해 함수 (콜백 함수)를 한 번 호출

각 하나의 원소를 뽑아내는 방법

이 함수에는 3 개의 인수가 사용됨

1. The item value
2. The item index       //생략가능
3. The array itself     //생략가능

예제
{: .label .label-purple .mt-3}
<div class="code-example" markdown="1">
<p id="demo"></p>

<script>
var txt = "";
var numbers = [45, 4, 9, 16, 25];
numbers.forEach(myFunction);
document.getElementById("demo").innerHTML = txt;

function myFunction(value, index, array) {
  txt = txt + value + "<br>"; 
}
</script>
</div>
```html
<p id="demo"></p>

<script>
var txt = "";
var numbers = [45, 4, 9, 16, 25];
numbers.forEach(myFunction);
document.getElementById("demo").innerHTML = txt;

function myFunction(value, index, array) {
  txt = txt + value + "<br>"; 
}
</script>
```

### Array.map()

**기존 배열의 value로 새로운 배열을 생성**

값이 없는 배열 요소에 대한 함수를 실행하지 않음

원래 배열을 변경하지 않음

1. The item value
2. The item index       //생략가능
3. The array itself     //생략가능

예제
{: .label .label-purple .mt-3}
<div class="code-example" markdown="1">
<p id="demo"></p>

<script>
var numbers1 = [45, 4, 9, 16, 25];
var numbers2 = numbers1.map(myFunction);

document.getElementById("demo").innerHTML = numbers2;

function myFunction(value, index, array) {
  return value * 2;
}
</script>
</div>
```html
<p id="demo"></p>

<script>
var numbers1 = [45, 4, 9, 16, 25];
var numbers2 = numbers1.map(myFunction);

document.getElementById("demo").innerHTML = numbers2;

function myFunction(value, index, array) {
  return value * 2;
}
</script>
```

### Array.filter()

**테스트를 통과하는 배열 요소를 사용하여 새 배열을 만듦**

이 함수에는 3 개의 인수가 사용됨

1. The item value
2. The item index       //생략가능
3. The array itself     //생략가능

예제
{: .label .label-purple .mt-3}
<div class="code-example" markdown="1">
<p id="demo"></p>

<script>
var numbers = [45, 4, 9, 16, 25];
var over18 = numbers.filter(myFunction);

document.getElementById("demo").innerHTML = over18;

function myFunction(value, index, array) {
  return value > 18;
}
</script>
</div>
```html
<p id="demo"></p>

<script>
var numbers = [45, 4, 9, 16, 25];
var over18 = numbers.filter(myFunction);

document.getElementById("demo").innerHTML = over18;

function myFunction(value, index, array) {
  return value > 18;
}
</script>
```

### Array.reduce() 

**단일 값을 생성(감소)하기 위해 각 배열 요소에서 함수를 실행**

배열에서 왼쪽에서 오른쪽으로 작동

원래 배열을 줄이지 않음

이 함수에는 4 개의 인수가 사용됨

1. The total (the initial value / previously returned value)
2. The item value
3. The item index   //생략가능
4. The array itself //생략가능

예제
{: .label .label-purple .mt-3}
<div class="code-example" markdown="1">
<p id="demo"></p>

<script>
var numbers = [45, 4, 9, 16, 25];
var sum = numbers.reduce(myFunction);

document.getElementById("demo").innerHTML = "The sum is " + sum;

function myFunction(total, value, index, array) {
  return total + value;
}
</script>
</div>
```html
<p id="demo"></p>

<script>
var numbers = [45, 4, 9, 16, 25];
var sum = numbers.reduce(myFunction);
//var sum = numbers1.reduce(myFunction, 100); // 전체 더한거에서 100추가

document.getElementById("demo").innerHTML = "The sum is " + sum;
                //합계 (초기 값 / 이전에 반환 된 값), 나머지값, 번호, 전체배열
function myFunction(total, value, index, array) {
  return total + value; //처음 값부터 끝까지 모두 더하기
}
</script>
```

### Array.reduceRight()

reduce()와 모두 같은데 그저 첫 번째 값과 나머지값의 순서가 거꾸로 간다(right to left)

예제
{: .label .label-purple .mt-3}
<div class="code-example" markdown="1">
<p id="demo"></p>

<script>
var numbers = [45, 4, 9, 16, 25];
var sum = numbers.reduceRight(myFunction);

document.getElementById("demo").innerHTML = "The sum is " + sum;

function myFunction(total, value, index, array) {
  return total + value;
}
</script>
</div>
```html
<p id="demo"></p>

<script>
var numbers = [45, 4, 9, 16, 25];
var sum = numbers.reduceRight(myFunction);

document.getElementById("demo").innerHTML = "The sum is " + sum;

function myFunction(total, value, index, array) {
  return total + value;
}
</script>
```

### Array.every()

**모든 배열 값이 테스트를 통과했는지 확인**

이 함수에는 3 개의 인수가 사용됨

1. The item value
2. The item index       //생략가능
3. The array itself     //생략가능

콜백 함수가 첫 번째 매개 변수만 사용하는 경우 다른 매개 변수는 생략 할 수 있음

예제
{: .label .label-purple .mt-3}
<div class="code-example" markdown="1">
<p id="demo"></p>

<script>
var numbers = [45, 4, 9, 16, 25];
var allOver18 = numbers.every(myFunction);

document.getElementById("demo").innerHTML = "All over 18 is " + allOver18;

function myFunction(value, index, array) {
  return value > 18;
}
</script>
</div>
```html
<p id="demo"></p>

<script>
var numbers = [45, 4, 9, 16, 25];
var allOver18 = numbers.every(myFunction);

document.getElementById("demo").innerHTML = "All over 18 is " + allOver18;

function myFunction(value, index, array) {
  return value > 18;
}
</script>
```

### Array.some() 

**일부 배열 값이 테스트를 통과했는지 확인**

every()는 모두 참이여야 true지만 이거는 하나라도 참이면 true

이 함수에는 3 개의 인수가 사용됨

1. The item value
2. The item index
3. The array itself

예제
{: .label .label-purple .mt-3}
<div class="code-example" markdown="1">
<p id="demo"></p>

<script>
var numbers = [45, 4, 9, 16, 25];
var someOver18 = numbers.some(myFunction);

document.getElementById("demo").innerHTML = "Some over 18 is " + someOver18;

function myFunction(value, index, array) {
  return value > 18;
}
</script>
</div>
```html
<p id="demo"></p>

<script>
var numbers = [45, 4, 9, 16, 25];
var someOver18 = numbers.some(myFunction);

document.getElementById("demo").innerHTML = "Some over 18 is " + someOver18;

function myFunction(value, index, array) {
  return value > 18;
}
</script>
```

### Array.indexOf() 

**배열에서 요소 값을 검색하고 해당 위치를 반환**

첫 번째 항목의 위치는 0이고 두 번째 항목의 위치는 1

두번째 매개변수는 선택, 시작 위치를 고를 수 있음

항목을 찾을 수 없으면 -1, 두개 이상이면 첫번째 요소 위치 값을 반환함

예제
{: .label .label-purple .mt-3}
<div class="code-example" markdown="1">
<p id="demo"></p>

<script>
var fruits = ["Apple", "Orange", "Apple", "Mango"];
var a = fruits.indexOf("Apple");
document.getElementById("demo").innerHTML = "Apple is found in position " + a;
</script>
</div>
```html
<p id="demo"></p>

<script>
var fruits = ["Apple", "Orange", "Apple", "Mango"];
var a = fruits.indexOf("Apple");
document.getElementById("demo").innerHTML = "Apple is found in position " + a;
</script>
```

### Array.lastIndexOf()

Array.indexOf()와 비슷하지만 **지정된 요소가 마지막으로 나타나는 위치를 반환**

### Array.find()

**테스트 함수를 통과 한 첫 번째 배열 요소의 value를 리턴**

이 함수에는 3 개의 인수가 사용됨

1. The item value
2. The item index
3. The array itself

예제
{: .label .label-purple .mt-3}
<div class="code-example" markdown="1">
<p id="demo"></p>

<script>
var numbers = [4, 9, 16, 25, 29];
var first = numbers.find(myFunction);

document.getElementById("demo").innerHTML = "First number over 18 is " + first;

function myFunction(value, index, array) {
  return value > 18;
}
</script>
</div>
```html
<p id="demo"></p>

<script>
var numbers = [4, 9, 16, 25, 29];
var first = numbers.find(myFunction);

document.getElementById("demo").innerHTML = "First number over 18 is " + first;

function myFunction(value, index, array) {
  return value > 18;
}
</script>
```

### Array.findIndex()

**테스트 함수를 통과 한 첫 번째 배열 value의 index만 추출**

이 함수에는 3 개의 인수가 사용됨

1. The item value
2. The item index
3. The array itself

예제
{: .label .label-purple .mt-3}
<div class="code-example" markdown="1">
<p id="demo"></p>

<script>
var numbers = [4, 9, 16, 25, 29];
var first = numbers.findIndex(myFunction);

document.getElementById("demo").innerHTML = "First number over 18 has index " + first;

function myFunction(value, index, array) {
  return value > 18;
}
</script>
</div>
```html
<p id="demo"></p>

<script>
var numbers = [4, 9, 16, 25, 29];
var first = numbers.findIndex(myFunction);

document.getElementById("demo").innerHTML = "First number over 18 has index " + first;

function myFunction(value, index, array) {
  return value > 18;
}
</script>
```

