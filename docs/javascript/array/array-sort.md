---
layout: default
title: Array Sort
parent: Arrays
grand_parent: JavaScript
nav_order: 2
---

# JavaScript Array Sort
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Array Sort

### Sorting an Array

* sort()

    **method sorts an array alphabetically** // a-z순

    Syntax
    {: .label .mt-2}
    <div class="code-example" markdown="1">
    fruits.sort()
    </div>
    ```js
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    fruits.sort();        
    //fruits = Apple,Banana,Mango,Orange
    ```

    숫자가 문자보다 먼저 정렬, 문자열인 숫자도 숫자로 이해해서 먼저정렬
    
    전체 숫자값보다 첫 번째 숫자의 오름차순으로 정렬한다 // 23 6 abcd 이렇게 나옴

### Reversing an Array

* reverse() method reverses the elements in an array // sort후 reverse하면 내림차순 됨

### Numeric Sort 

By default, the sort() function sorts values as strings. - 그래서 첫 번째 숫자의 오름차순으로 정렬
해결법 : 함수이용(compare funtion)
* 오름차순: 
var points = [40, 100, 1, 5, 25, 10];
points.sort(function(a, b){return a – b});

* 내림차순: 
var points = [40, 100, 1, 5, 25, 10];
points.sort(function(a, b){return b - a});

### The Compare Function

purpose : to define an alternative sort order.
should return a negative, zero, or positive value, depending on the arguments:
	function(a, b){return a - b}
When the sort() function compares two values, it sends the values to the compare function, and sorts the values according to the returned (negative, zero, positive) value.

If the result is negative a is sorted before b.
If the result is positive b is sorted before a.
If the result is 0 no changes are done with the sort order of the two values.

Example:
The compare function compares all the values in the array, two values at a time (a, b).
When comparing 40 and 100, the sort() method calls the compare function(40, 100).
The function calculates 40 - 100 (a - b), and since the result is negative (-60),  the sort function will sort 40 as a value lower than 100.

You can use this code snippet to experiment with numerically and alphabetically sorting:

### Sorting an Array in Random Order

var points = [40, 100, 1, 5, 25, 10];
points.sort(function(a, b){return 0.5 - Math.random()});

### Find the Highest (or Lowest) Array Value

오름 or 내림차순으로 정렬한 첫 번째나 마지막번째가 highest or lowest value
- 근데 최대나 최소값 하나만 원하면 정말 비효율적임(max() or min()쓰셈)

### Using Math.max() on an Array

Math.max.apply to find the highest number in an array:
	Math.max.apply(null, 배열); 
	or
	Math.max(1, 2, 3) 매개변수에 배열들어가면 안댐, toString이나 join 써도 안댐ㅠ;;
5
### Using Math.min() on an Array

You can use Math.min.apply to find the lowest number in an array:
	Math.min.apply(null, 배열); 
	or
	Math.min(1,2,3)

### My Min / Max JavaScript Methods

: fastest 
max값 구하기(infinity와 부등호를 반대방향으로 돌리면 min)
	function myArrayMax(arr) {
	  var len = arr.length;
	  var max = -Infinity;
	  while (len--) {
	    if (arr[len] > max) {
	      max = arr[len];
	    }
	  }
	  return max;
	}

### Sorting Object Arrays – 문자열, 숫자 정렬이 다름

숫자값만 sort
var cars = [
  {type:"Volvo", year:2016},
  {type:"Saab", year:2001},
  {type:"BMW", year:2010}
];
cars.sort(function(a, b){return a.year - b.year});

문자열 sort
<button onclick="myFunction()">Sort</button>

<p id="demo"></p>

<script>
var cars = [
  {type:"Volvo", year:2016},
  {type:"Saab", year:2001},
  {type:"BMW", year:2010}
];

displayCars();

function myFunction() {
  cars.sort(function(a, b){
    var x = a.type.toLowerCase();
    var y = b.type.toLowerCase();
    if (x < y) {return –1;}			//마이너스면 앞으로 정렬
    if (x > y) {return 1;}			//플로스면 뒤로 정렬 – 그래서 알파벳이 클수록 앞으로감
    return 0;
  });
  displayCars();
}

function displayCars() {
  document.getElementById("demo").innerHTML =
  cars[0].type + " " + cars[0].year + "<br>" +
  cars[1].type + " " + cars[1].year + "<br>" +
  cars[2].type + " " + cars[2].year;
}
</script>
