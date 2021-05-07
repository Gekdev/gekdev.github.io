---
layout: default
title: Math
parent: JavaScript
nav_order: 8
---

# JavaScript Math Object
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Math Object

### 

28. JavaScript Math Object
* Math.ceil(): 올림
	Math.ceil(4.4);     // returns 5
* Math.round(): 반올림 rounded to its nearest integer
	Math.round(4.5) = 5
* Math.floor(): 내림 rounded down to its nearest integer
	Math.floor(4.7);    // returns 4
* Math.pow(): 제곱
	Math.pow(8, 2);      // returns 64
* Math.sqrt(): 제곱근 square root
	Math.sqrt(64);      // returns 8
* Math.abs(): 무조건 양수로 absolute (positive) value of x
	Math.abs(-4.7);     // returns 4.7
* Math.min() and Math.max()
	Math.min(0, 150, 30, 20, -8, -200);  // returns -200
	Math.max(0, 150, 30, 20, -8, -200);  // returns 150
* Math.random(): returns a random number between 0 (inclusive), and 1 (exclusive)
* Math.sin(): 사인값 / 코자인 함수도 있음(안쓸것같아서 생략함)

Math Constructor
Unlike other global objects, the Math object has no constructor. Methods and properties are static.
All methods and properties (constants) can be used without creating a Math object first.

Complete Math Reference
메소드 엄청 많음 https://www.w3schools.com/jsref/jsref_obj_math.asp

29. JavaScript Random
Math.random():  returns a random number between 0 (inclusive),  and 1 (exclusive) →always lower than 1

JavaScript Random Integers
* Math.floor(Math.random() * 10);     // returns a random integer from 0 to 9  	//*100 0-99
	or you can just add +1 after syntax to make 1-10 or 1-100
	* Math.floor(Math.random()*10)+1 // 1-10
* Math.floor(Math.random() * 11);      // returns a random integer from 0 to 10	//*101 0-100

A Proper Random Function
This JavaScript function always returns a random number between min (included) and max (excluded):
	function getRndInteger(min, max) {
	  return Math.floor(Math.random() * (max - min) ) + min;
	}

This JavaScript function always returns a random number between min and max (both included):
	function getRndInteger(min, max) {
	  return Math.floor(Math.random() * (max - min + 1) ) + min;
	}