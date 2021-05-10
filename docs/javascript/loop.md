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

## Loops

**반복문은 코드 블록을 여러 번 실행할 수 있어서 편리함 = 배열로 작업하는 경우**

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

&#9656; statement 1 코드 블록이 실행되기 전에(한번) 실행

&#9656; statement 2 코드 블록을 실행하기 위한 조건을 정의

&#9656; statement 3 코드 블록이 실행 된 후 (매번) 실행
</div>
```js
for (i = 0; i < 5; i++) {
  text += "The number is " + i + "<br>";
}

//text is The number is 0 The number is 1 The number is 2 The number is 3 The number is 4
```

#### statement1

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

#### Statement 2 (condtion)

**초기 변수의 조건을 평가하는 조건문**

&#9656; 최초 실행 뒤 반복을 결정하는 조건문

&#9656; 선택사항 = 생략가능 하지만 무한루프이기 때문에 you must provide a break inside the loop


#### Statement 3

**초기 변수의 값을 변화하는 조건문**

&#9656; 선택사항 = 루프 내에서 값을 변화시킨다면 생략가능함

### The For/In Loop

**객체의 속성을 통해서 반복**

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


c. The For/Of Loop
The JavaScript for/of statement loops through the values of an iterable objects
for/of lets you loop over data structures that are iterable such as Arrays, Strings, Maps, NodeLists, and more.

syntax:
	for (variable of iterable) {
	  // code block to be executed
	}

* variable - For every iteration the value of the next property is assigned to the variable. 
		Variable can be declared with const, let, or var.
* iterable - An object that has iterable properties.

var cars = ['BMW', 'Volvo', 'Mini']; // string이면 x가 한글자씩 댐
var x;

for (x of cars) {
  document.write(x + "<br >"); // x = BMW, Volvo, Mini
}

35. JavaScript While Loop
The While Loop
: can execute a block of code as long as a specified condition is true.
if you omit condition, loop will never end - crush

Syntax
while (condition) {
  // code block to be executed
}

The Do/While Loop
최초 한번 실행됨(무조건)/ do로 먼저 쓰기때문

do {
  text += "The number is " + i;
  i++;
}
while (i < 10);

for와 while문은 매우비슷하다

5. 반복문(loop / iterate)
	A. while문 – 조건이 true에서 false가 될 때까지 반복실행한다
	 반복문에서 종료조건을 잘못 지정하면 무한반복이 되거나, 반복문이 실행되지 않는다
		var i = 0;
		// 종료조건으로 i의 값이 10보다 작다면 true, 같거나 크다면 false가 된다.
		while(i < 10){
		    // 반복이 실행될 때마다 coding everybody <br />이 출력된다.
		    document.write('coding everybody <br />');
		    // i의 값이 1씩 증가한다.
		    i++
		}
			
	B. for문
		for(초기화; 반복조건; 반복이 될 때마다 실행되는 코드){
		    반복해서 실행될 코드
		}
		
	C. do-while 문
		최소 한번은 실행되며, 조건식을 검사해 ture인 동안 작업문이 반복 실행됨
		var I = 0;
		do{
			document.write(i);
			i++;
		}while(i<10(조건식));

	D. break 문 = 반복문 벗어나기(여러개 중첩일 경우 하나만 벗어남)
	ex) 1에서 얼마까지 더해야 3000이 넘는지 구하기
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

	E. continue 문 = 다음 반복으로 넘어가고자 할 때 사용
		for(){
		.............
		continue; // 아래 ....을 실행하지 않고 작업과 조건식으로 다시 올라감
		.............
		}

		ex) 
		var sum = 0;
	         for(var i=0;i<=10;i++){
	            if(i%3!=1){
	                continue;
	            }
	            document.write(i+" ");
	            sum += i;
	         }
	         document.write("합은:"+sum)
		
	C. 반복문의 제어
	break
			for(var i = 0; i < 10; i++){
			    if(i === 5) {
			        break;
			    }
			    document.write('coding everybody'+i+'<br />');
			}

	continue :실행을 즉시 중단 하면서 반복은 지속
	 　　　　 i의 값이 5가 되었을 때 실행이 중단 됐기 때문에 continue 이후의 구문이 실행되지 않은 것이다. 



36. JavaScript Break and Continue
The Break Statement
:  "jumps out" of a loop.
continues executing the code after the loop (if any)

	for (i = 0; i < 10; i++) {
	  if (i === 3) { break; }
	  text += "The number is " + i + "<br>";
	}

The Continue Statement
: "jumps over" one iteration in the loop.
The continue statement breaks one iteration (in the loop), if a specified condition occurs, and continues with the next iteration in the loop.

3만 안나옴
	for (i = 0; i < 10; i++) {
	  if (i === 3) { continue; }
	  text += "The number is " + i + "<br>";
	}

/안중요한것같아서 공부안함/
JavaScript Labels
To label JavaScript statements, you precede the statements with a label name and a colon:
↓
label:
statements

The break and the continue statements are the only JavaScript statements that can "jump out of" a code block.
Syntax:
	break labelname;
	continue labelname;

The continue statement (with or without a label reference) can only be used to skip one loop iteration.
The break statement, without a label reference, can only be used to jump out of a loop or a switch.
With a label reference, the break statement can be used to jump out of any code block:

ex)
var cars = ["BMW", "Volvo", "Saab", "Ford"];
list: {
  text += cars[0] + "<br>";
  text += cars[1] + "<br>";
  break list;
  text += cars[2] + "<br>";				//안나옴
  text += cars[3] + "<br>";				//안나옴
}

