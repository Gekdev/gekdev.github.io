---
layout: default
title: Conditions
parent: JavaScript
nav_order: 11
---

# JavaScript Conditions
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Conditions

### 

조건문(conditional statement) : 조건을 검사해 참인지 거짓인지에 따라 서로 작은 작업을 실행하는 문장
참일때 if나 else if를 한다! - 앞에서 이미 true가 나와서 실행이 되면 그 뒤로는 실행이 되지않음
else if의 모든 조건이 false라면 else가 실행된다. else는 생략 가능하다.

32. JavaScript if, else and else if (conditions)

: are used to perform different actions based on different conditions.

The if Statement(true)
The else Statement(false)
The else if Statement : to specify a new condition if the first condition is false.

using uppercase(If or IF) will make error 

A. if : 조건문은 if로 시작한다. if 뒤의 괄호에 조건이 오고, 조건이 될 수 있는 값는 Boolean이다. 
		Boolean의 값이 true라면 조건이 담겨진 괄호 다음의 중괄호 구문이 실행된다.
			if(true/false){
			}else if(){
			}else{}

33. JavaScript Switch Statement
The switch statement is used to perform different actions based on different conditions.

Syntax
	switch(expression) {
	  case x:
	    // code block
	    break;
	  case y:
	    // code block
	    break;
	  default:
	    // code block
	}

This is how it works:
	The switch expression is evaluated once.
	The value of the expression is compared with the values of each case.
	If there is a match, the associated block of code is executed.

The break Keyword
This will stop the execution of inside the switch block.
Note: If you omit the break statement, the next case will be executed even if the evaluation does not match the case.

The default Keyword
: specifies the code to run if there is no case match
The default case does not have to be the last case in a switch block(어디서나 작성 가능)

Common Code Blocks
case 4:
case 5: var txt = “love myself”처럼
값을 적지않고 뒤로 넘기는 방식ㄱㄴ

Switching Details
* 첫 번째로 일치하는 case가 먼저 선택됨
* 일치하는게 없으면 default까지 찾음
* default도 없으면 switch문을 끝내고 continue the rest of statements

Strict Comparison
Switch cases use strict comparison (===).
operands should be same type

	var x = "0";
	switch (x) {
	  case 0:
	    text = "Off";
	    break;
	  case 1:
	    text = "On";
	    break;
	  default:
	    text = "No value found";			//이게 답
	}

B. switch문 : 값에따라 서로다른 코드를 작성해야 할 때 if보다 좋다
		case에 따라서 중괄호 쓰면 안됨
		case문의 값은 상수만 가능!(조건비교는 if, 값에따른 다른코드작성은 switch)
		case에 따라서 break 문을 사용하지 않으면, 참인 값 뒤로 작성된 case의 값들이 모두 작성이 된다.

		ex) var day = “mon”
		    switch(day){
			case “mon”:
			case “tue”:
			case “wed”:
			case “thu”:
			case “fri”: document.write(“정상영업”);
				  break;
			case “sat”:
			case “sun”: document.write(“휴무”);
				   break;


			}
