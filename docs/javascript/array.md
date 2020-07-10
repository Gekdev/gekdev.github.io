---
layout: default
title: Arrays
parent: JavaScript
nav_order: 6
---

# JavaScript Arrays
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## JavaScript Arrays

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

## Array Properties and Methods


### Looping Array Elements
1. for
text = "<ul>";
for (i = 0; i < fruits.length ; i++) {
  text += "<li>" + fruits[i] + "</li>";
}
text += "</ul>";

2. Array.forEach()
var fruits, text;
fruits = ["Banana", "Orange", "Apple", "Mango"];

text = "<ul>";
fruits.forEach(myFunction);
text += "</ul>";

function myFunction(value) {
  text += "<li>" + value + "</li>";
}

Adding Array Elements
fruits.push("Lemon")
fruits[fruits.length] = "Lemon";
WARNING ! Adding elements with high indexes can create undefined "holes(undefined)" in an array:

Associative Arrays
Many programming languages support arrays with named indexes.
Arrays with named indexes are called associative arrays (or hashes). 
JavaScript does not support arrays with named indexes. - so use objects
In JavaScript, arrays always use numbered indexes.  
ex) - named indexes 
	var person = []; 			//array not an object
	person["firstName"] = "John";	//no error but does not work
	person["lastName"] = "Doe";	//no error but does not work
	person["age"] = 46;		//no error but does not work
	var x = person.length;   		// person.length will return 0
	var y = person[0];         	// person[0] will return undefined

The Difference Between Arrays and Objects
In JavaScript, arrays use numbered indexes.  
In JavaScript, objects use named indexes.

Arrays are a special kind of objects, with numbered indexes.

Avoid new Array()
There is no need to use the JavaScript's built-in array constructor new Array().
Use [] instead.

	var points = new Array(40);  
	points[0] -> undefined	//because it’s not an Array, just one single element(error)

How to Recognize an Array
problem is that the JavaScript operator typeof returns "object":
1. Array.isArray(fruits);   // returns true 				but not supported in older browsers.
2. create your own funtion: it returns true if the object prototype contains the word "Array".
	function isArray(x) {
	  return x.constructor.toString().indexOf("Array") > -1;
	}
3. instanceof operator returns true if an object is created by a given constructor
	var fruits = ["Banana", "Orange", "Apple", "Mango"];
	fruits instanceof Array;   // returns true

21. JavaScript Array Methods
Converting Arrays to Strings
* toString() converts an array to a string of (comma separated) array values. // result is separated by ,
* join() method also joins all array elements into a string. (안에 매개변수로) you can set separator 
	It behaves just like toString(), but in addition you can specify the separator
	
	var x = ["apple", "banana", "potato", "grapes", "flower"]
	document.getElementById("dom11").innerHTML += x.join("*")+ "<br/>";

Popping and Pushing
* pop() : removes the last element from an array,
	The pop() method returns the value that was "popped out"(you can take the value by variable)
* push() : adds a new element to an array (at the end)
	The push() method returns the new array length(add one more)

Shifting Elements
*shift() method removes the first array element and "shifts" all other elements to a lower index.
	Shifting is equivalent to popping, working on the first element instead of the last.
	The shift() method returns the string that was "shifted out"(you can take the value by variable)
*unshift() method adds a new element to an array (at the beginning)
	var fruits = ["Banana", "Orange", "Apple", "Mango"];
	fruits.unshift("Lemon");    // Returns 5

Changing Elements
* change :　fruits[0] = "Kiwi";        // Changes the first element of fruits to "Kiwi“
* add : fruits[fruits.length] = “Kiwi”

Deleting Elements – 그냥 구멍내버리고 채우지않음 (구멍낸 경우 arr.[숫자] = “” 로 채워야함)
* delete
	var fruits = ["Banana", "Orange", "Apple", "Mango"];
	delete fruits[0];           // Changes the first element in fruits to undefined
Using delete may leave undefined holes in the array. Use pop() or shift() instead.

Repeating Elements
* repeat 
	“*”.repeat()

Splicing an Array
* fruits.splice(2, 0, "Lemon", "Kiwi");
	   들어갈자리, 지워야 하는 개수, 넣어야 하는것들(1~..) / 변수에 담으면 지운것들을 리턴함
					생략가능
	<script>
	var fruits = ["Banana", "Orange", "Apple", "Mango"];
	document.getElementById("demo1").innerHTML = "Original Array:<br> " + fruits;

	function myFunction() {
	  var removed = fruits.splice(2, 2, "Lemon", "Kiwi"); 
	  document.getElementById("demo2").innerHTML = "New Array:<br>" + fruits;
	  document.getElementById("demo3").innerHTML = "Removed Items:<br> " + removed; 
	}

         myFunction();
	</script>

스플라이스로 지우기(매개변수 생략으로 삭제만 이용하는 방법) - 좋음ㄱㅊ오류안남
	var fruits = ["Banana", "Orange", "Apple", "Mango"];
	fruits.splice(0, 1);        // Removes the first element of fruits

Merging (Concatenating) Arrays
* concat() method creates a new array by merging (concatenating) existing arrays – return new array
	var myGirls = ["Cecilie", "Lone"];
	var myBoys = ["Emil", "Tobias", "Linus"];
	var myChildren = myGirls.concat(myBoys);   // Concatenates (joins) myGirls and myBoys
매개변수로 위와같이 배열을 가지고 있는 변수를 받을수도 있고, 배열을 바로 받을수도 있음
매개변수 개수는 무한정(넣고싶은 만큼 넣어도 됨)

Slicing an Array
* slice(): method slices out a piece of an array into a new array.
	var fruits = ["Banana", "Orange", "Lemon", "Apple", "Mango"];
	var citrus = fruits.slice(1, 3);
			가져올 값의 인덱스, 마지막 값의 전까지(생략가능, 하면 가져올 값의 인덱스 뒤로 다가져옴)

Automatic toString()
automatically converts an array to a comma separated string when a primitive value is expected.
var fruits = ["Banana", "Orange", "Apple", "Mango"];
document.getElementById("demo").innerHTML = fruits.toString();
document.getElementById("demo").innerHTML = fruits;
그래서 두 개의 값이 같다

All JavaScript objects have a toString() method.

Finding Max and Min Values in an Array
- 자바스크립트에서는 최대소값을 찾아주는 함수가 없어서 아래에서 배울거양

22. JavaScript Sorting Arrays
Sorting an Array
* sort(): method sorts an array alphabetically // a-z순
숫자가 문자보다 먼저 정렬, 문자열인 숫자도 숫자로 이해해서 먼저정렬
전체 숫자값보다 첫 번째 숫자의 오름차순으로 정렬한다 // 23 6 abcd 이렇게 나옴

Reversing an Array
* reverse() method reverses the elements in an array // sort후 reverse하면 내림차순 됨

Numeric Sort 
By default, the sort() function sorts values as strings. - 그래서 첫 번째 숫자의 오름차순으로 정렬
해결법 : 함수이용(compare funtion)
* 오름차순: 
var points = [40, 100, 1, 5, 25, 10];
points.sort(function(a, b){return a – b});

* 내림차순: 
var points = [40, 100, 1, 5, 25, 10];
points.sort(function(a, b){return b - a});

The Compare Function
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

Sorting an Array in Random Order
var points = [40, 100, 1, 5, 25, 10];
points.sort(function(a, b){return 0.5 - Math.random()});

Find the Highest (or Lowest) Array Value
오름 or 내림차순으로 정렬한 첫 번째나 마지막번째가 highest or lowest value
- 근데 최대나 최소값 하나만 원하면 정말 비효율적임(max() or min()쓰셈)

Using Math.max() on an Array
Math.max.apply to find the highest number in an array:
	Math.max.apply(null, 배열); 
	or
	Math.max(1, 2, 3) 매개변수에 배열들어가면 안댐, toString이나 join 써도 안댐ㅠ;;
5
Using Math.min() on an Array
You can use Math.min.apply to find the lowest number in an array:
	Math.min.apply(null, 배열); 
	or
	Math.min(1,2,3)

My Min / Max JavaScript Methods
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

Sorting Object Arrays – 문자열, 숫자 정렬이 다름
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
