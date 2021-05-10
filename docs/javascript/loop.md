---
layout: default
title: Loop
parent: JavaScript
nav_order: 9
---

# JavaScript Loop
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## JavaScript Loops

**반복문은 코드 블록을 여러 번 실행할 수 있어서 편리함 = 배열로 작업하는 경우 주로 사용**

### Different Kinds of Loops

자바스크립트는 다섯가지 반복문을 제공함

* for : 코드 블록을 여러 번 반복

* for/in : 개체의 속성을 반복

* for/of : 반복 가능한 객체의 값을 반복

* while : 지정된 조건이 참인 동안 코드 블록을 반복

* do/while : 지정된 조건이 참인 동안 코드 블록을 반복

### The For Loop

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
for (statement 1; condition ; statement 3) {

  // code block to be executed
  
}

&#9656; statement 1 : 초기화, 코드 블록이 실행되기 전에(한번) 실행

&#9656; statement 2 : 코드 블록을 실행하기 위한 반복조건을 정의

&#9656; statement 3 : 코드 블록이 실행 된 후 (매번) 실행되는 코드
</div>
```js
for (i = 0; i < 5; i++) {
  text += "The number is " + i + "<br>";
}

//text is The number is 0 The number is 1 The number is 2 The number is 3 The number is 4
```

#### Statement1

**루프에서 사용되는 변수를 초기화함**

&#9656; 선택사항 = 루프가 시작되기 전에 값이 설정되었다면 생략가능함

&#9656; 실행문 1안에서 ,를 사용해서 다양한 변수를 선언할 수 있음

```js
var i = 2;
var len = cars.length;
var text = "";
for (; i < len; i++) {
  text += cars[i] + "<br>";
}
```

#### Statement2 (condtion)

**초기 변수의 조건을 평가하는 조건문**

&#9656; 최초 실행 뒤 반복을 결정하는 조건문

&#9656; 선택사항 = 생략가능 하지만 무한루프이기 때문에 you must provide a break inside the loop

#### Statement3

**초기 변수의 값을 변화하는 조건문**

&#9656; 선택사항 = 루프 내에서 값을 변화시킨다면 생략가능함

### The For/In Loop

**객체나 배열을 속성을 통해서 조건문을 반복**

&#9656; 각 반복은 property의 name(index)을 배출함 

#### Object loop

syntax 
{: .label .mt-2}
<div class="code-example" markdown="1">
for (key in object) {

  // code block to be executed
  
}
</div>
```js
var person = {fname:"John", lname:"Doe", age:25};

var text = "";
var x;
for (x in person){
  text += person[x];
}
//text is John Doe 25
```

#### Array loop

syntax 
{: .label .mt-2}
<div class="code-example" markdown="1">
for (variable in array) {

  code
  
}
</div>
```js
var numbers = [45, 4, 9, 16, 25];

var txt = "";
var x;
for (x in numbers) {
  txt += numbers[x] + "<br>";
}
document.getElementById("demo").innerHTML = txt;
//text is 45 4 9 16 25
```

### The For/Of Loop

**반복 가능한 객체의 값을 반복**

&#9656; 배열, 문자열,지도, NodeLists 등과 같은 반복 가능한 데이터 구조를 반복 할 수 있음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
for (variable of iterable) {

  // code block to be executed
  
}

&#9656; variable : 모든 반복에 대해 다음 속성의 값이 변수에 할당됨, 변수는 const, let, var로 선언 할 수있음

&#9656; iterable : 반복 가능한 속성이있는 객체
</div>


#### Array loop

```js
let cars = ["BMW", "Volvo", "Mini"];
let text = "";

for (let x of cars) {
  text += x + "<br>";
}
//text is BMW Volvo Mini
```

#### String loop

```js
let language = "JavaScript";
let text = "";

for (let x of language) {
text += x + "<br>";
}
//하나하나 따로 글자가 나옴!
```

### The While Loop

**지정된 조건에 해당하는 만큼의 코드 블록을 루핑**

&#9656; 조건이 true에서 false가 될 때까지 반복실행

&#9656; 조건에 사용된 변수를 조작하는것이 생략되면 무한루프에 걸림

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
while (condition) {

  // code block to be executed
  
}
</div>
```js
while (i < 10) {
  text += "The number is " + i;
  i++;
}
```

for과 while의 차이점
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
for(;arr[i];) / while (arr[i])

for문은 반복문 함수 매개변수에 세미콜론이 있어야함!
</div>

### The Do/While Loop

While문과 거의 동일하지만 do로 먼저 쓰기때문에 **최초 한번 실행됨** (무조건)

&#9656; 조건이 테스트되기 전에 코드 블록이 실행되기 때문에 조건이 거짓 인 경우에도 루프는 항상 한 번 이상 실행

&#9656; 조건에 사용된 변수를 조작하는것이 생략되면 무한루프에 걸림

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
do {

  // code block to be executed
  
}

while (condition);
</div>
```js
do {
  text += "The number is " + i;
  i++;
}
while (i < 10);
```

---

## JavaScript Break and Continue

### break Statement  

**반복문 벗어나기** (여러개 중첩일 경우 하나만 벗어남)

예제
{: .label .label-purple .mt-2}
```js
// 1에서 얼마까지 더해야 3000이 넘는지 구하기
var t = 0;
var sum = 0;
while(true){
sum += t
    if(sum>3000){			
        break;
    }
    t++ //sum 먼저 검사해야댕
}
document.write(t+"까지 더하면 3000이 넘어요"+sum)
```

### continue Statement 

**다음 반복으로 넘어가고자 할 때 사용**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
for(){

.............

continue; // 아래 ....을 실행하지 않고 작업과 조건식으로 다시 올라감

.............
    
}
</div>
```js
var text = "";
var i;
for (i = 0; i < 10; i++) {
  if (i === 3) { continue; }
  text += "The number is " + i + "<br>";
}

//3빼고 모두 출력됨
```

### JavaScript Labels

JavaScript 문에 레이블을 지정하려면 문 앞에 레이블 이름과 콜론을 추가

&#9656; break과 continue문은 코드 블록 "밖으로 점프"할 수있는 유일한 자바 스크립트 구문

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
label:

statements
</div>

<span class="fs-2">
[W3School](https://www.w3schools.com/js/tryit.asp?filename=tryjs_break_list){: .btn .btn-outline .mt-2 }
</span>
