---
layout: default
title: Array Iteration
parent: Advanced
grand_parent: JavaScript
nav_order: 3
---

# JavaScript Array Iteration
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Array Iteration

### Converting Arrays to Strings

23. JavaScript Array Iteration Methods
* Array.forEach(): 각 하나의 원소를 뽑아내는 방법
: calls a function (a callback function) once for each array element.

사용방법
	var txt = "";
	var numbers = [45, 4, 9, 16, 25];
	numbers.forEach(myFunction);
			       can be omitted
	function myFunction(value, index, array) {
	  txt = txt + value + "<br>";
	}

Array.forEach() is supported in all browsers except Internet Explorer 8 or earlier:

* Array.map(): 기존 배열의 value로 새로운 배열을 생성하는 법
● The map() method creates a new array by performing a function on each array element.
● The map() method does not execute the function for array elements without values.
● The map() method does not change the original array.

사용방법 
	<script>
	var numbers1 = [45, 4, 9, 16, 25];
	var numbers2 = numbers1.map(myFunction);		//[90,8,18,32,50]

	document.getElementById("demo").innerHTML = numbers2;
			       can be omitted
	function myFunction(value, index, array) {
	  return value * 2;
	}
	</script>
Array.map() is supported in all browsers except Internet Explorer 8 or earlier.
 
* Array.filter(): 시험에 통과한 value만 새로운 배열의 value로 넣는방법
creates a new array with array elements that passes a test.

사용방법
	var numbers = [45, 4, 9, 16, 25];
	var over18 = numbers.filter(myFunction);
			       can be omitted
	function myFunction(value, index, array) {
	  return value > 18;
	}
Array.filter() is supported in all browsers except Internet Explorer 8 or earlier.

* Array.reduce() : function on each array element to produce (reduce it to) a single value
The reduce() method works from left-to-right in the array.

The reduce() method does not reduce the original array.

var numbers1 = [45, 4, 9, 16, 25];
var sum = numbers1.reduce(myFunction);
		   첫 번째값, 나머지값, 번호, 전체배열
function myFunction(total, value, index, array) {
	return total + value;
}

The reduce() method can accept an initial value:
var sum = numbers1.reduce(myFunction, 100); - 그럼 전체 더한거에서 100추가

* Array.reduceRight()
-reduce()와 모두 같은데 그저 첫 번째 값과 나머지값의 순서가 거꾸로 간다(right to left)

* Array.every() : check if all array values pass a test.

var numbers = [45, 4, 9, 16, 25];
var allOver18 = numbers.every(myFunction); //allOver18 = false
			  생략가능  
function myFunction(value, index, array) {
  return value > 18;
}

* Array.some() : check if some array values pass a test.
- every()는 모두 참이여야 true지만 이거는 하나라도 참이면 true
* Array.indexOf() : 배열 안 원소의 번호 찾기

var fruits = ["Apple", "Orange", "Apple", "Mango"];
var a = fruits.indexOf("Apple");	//a = 0

syntax: array.indexOf(item, start)
	start is optional

* Array.lastIndexOf()
거꾸로 세는건데 jhonna 햇갈림 ㅠ;; - 쓰지마셈

* Array.find():  returns the value of the first array element that passes a test function.
- 처음으로 통과된 value만 추출됨

var numbers = [4, 9, 16, 25, 29];
var first = numbers.find(myFunction);  //first = 25

function myFunction(value, index, array) {
  return value > 18;
}

* Array.findIndex(): returns the index of the first array element that passes a test function.
- 처음으로 통과된 value의 index만 추출

Most of them are supported in all browsers except Internet Explorer 8 or earlier.
