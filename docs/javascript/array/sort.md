---
layout: default
title: Sort
parent: Arrays
grand_parent: JavaScript
nav_order: 3
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
    
    전체 숫자값보다 첫 번째 숫자의 오름차순으로 정렬한다 // 23 6 abcd 이렇게

### Reversing an Array

* reverse()

    **reverses the elements in an array** 
    
    sort후 reverse하면 내림차순

    예제
    {: .label .label-purple .mt-3}
    <div class="code-example" markdown="1">
    <p id="demo"></p>

    <script>
    // Create and display an array:
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    document.getElementById("demo").innerHTML = fruits;

    function myFunction() {
      // First sort the array
      fruits.sort();
      // Then reverse it:
      fruits.reverse();
      document.getElementById("demo").innerHTML = fruits;
    }
    </script>
    </div>
    ```html
    <p id="demo"></p>

    <script>
    // Create and display an array:
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    document.getElementById("demo").innerHTML = fruits;

    function myFunction() {
      // First sort the array
      fruits.sort();
      // Then reverse it:
      fruits.reverse();
      document.getElementById("demo").innerHTML = fruits;
    }
    </script>
    ```
    
### Numeric Sort 

By default, the sort() 함수는 값을 문자열 로 정렬 - 그래서 첫 번째 숫자의 오름차순으로 정렬하기 때문에 25보다 100이 먼저 정렬됨

해결법 : 함수이용(compare funtion)

* 오름차순

    예제
    {: .label .label-purple .mt-3}
    <div class="code-example" markdown="1">
    <button onclick="myFunction()">Try it</button>

    <p id="demo"></p>

    <script>
    var points = [40, 100, 1, 5, 25, 10];
    document.getElementById("demo").innerHTML = points;  

    function myFunction() {
      points.sort(function(a, b){return a - b});
      document.getElementById("demo").innerHTML = points;
    }
    </script>
    </div>
    ```html
    <button onclick="myFunction()">Try it</button>

    <p id="demo"></p>

    <script>
    var points = [40, 100, 1, 5, 25, 10];
    document.getElementById("demo").innerHTML = points;  

    function myFunction() {
      points.sort(function(a, b){return a - b});
      document.getElementById("demo").innerHTML = points;
    }
    </script>
    ```

* 내림차순

    예제
    {: .label .label-purple .mt-3}
    <div class="code-example" markdown="1">
    <button onclick="myFunction()">Try it</button>

    <p id="demo"></p>

    <script>
    var points = [40, 100, 1, 5, 25, 10];
    document.getElementById("demo").innerHTML = points;

    function myFunction() {
      points.sort(function(a, b){return b - a});
      document.getElementById("demo").innerHTML = points;
    }
    </script>
    </div>
    ```html
    <button onclick="myFunction()">Try it</button>

    <p id="demo"></p>

    <script>
    var points = [40, 100, 1, 5, 25, 10];
    document.getElementById("demo").innerHTML = points;

    function myFunction() {
      points.sort(function(a, b){return b - a});
      document.getElementById("demo").innerHTML = points;
    }
    </script>
    ```

* 무작위로

    무작위지만 우선순위가 있음
    
    Fisher Yates Shuffle 방법을 더 선호해서 사용(뒤에 설명되어 있음)

    예제
    {: .label .label-purple .mt-3}
    <div class="code-example" markdown="1">
    <button onclick="myFunction()">Try it</button>

    <p id="demo"></p>

    <script>
    var points = [40, 100, 1, 5, 25, 10];
    document.getElementById("demo").innerHTML = points;  

    function myFunction() {
      points.sort(function(a, b){return 0.5 - Math.random()});
      document.getElementById("demo").innerHTML = points;
    }
    </script>
    </div>
    ```html
    <button onclick="myFunction()">Try it</button>

    <p id="demo"></p>

    <script>
    var points = [40, 100, 1, 5, 25, 10];
    document.getElementById("demo").innerHTML = points;  

    function myFunction() {
      points.sort(function(a, b){return 0.5 - Math.random()});
      document.getElementById("demo").innerHTML = points;
    }
    </script>
    ```

### The Compare Function

비교 함수의 목적은 대체 **정렬 순서를 정의하는 것**

비교 함수는 인수에 따라 음수, 0 또는 양수 값을 반환

```js
function(a, b){return a - b}
```

`sort()`함수는 두 개의 값을 비교하여, 상기 비교 함수 값을 전송하고, 반환(-, 0, +)의 값에 따른 값을 정렬

&#9656; 결과가 음수 이면 b 이전에 a 정렬 

&#9656; 결과가 양수 이면 a 이전에 b 정렬 

&#9656; 결과가 0이면 두 값의 정렬 순서가 변경되지 않음


예제
{: .label .label-purple .mt-3}
<div class="code-example" markdown="1">
<button onclick="myFunction1()">Sort Alphabetically</button>
<button onclick="myFunction2()">Sort Numerically</button>

<p id="demo"></p>

<script>
var points = [40, 100, 1, 5, 25, 10];
document.getElementById("demo").innerHTML = points;  

function myFunction1() {
  points.sort();
  document.getElementById("demo").innerHTML = points;
}
function myFunction2() {
  points.sort(function(a, b){return a - b});
  document.getElementById("demo").innerHTML = points;
}
</script>
</div>
```html
<button onclick="myFunction1()">Sort Alphabetically</button>
<button onclick="myFunction2()">Sort Numerically</button>

<p id="demo"></p>

<script>
var points = [40, 100, 1, 5, 25, 10];
document.getElementById("demo").innerHTML = points;  

function myFunction1() {
  points.sort();
  document.getElementById("demo").innerHTML = points;
}
function myFunction2() {
  points.sort(function(a, b){return a - b});
  document.getElementById("demo").innerHTML = points;
}
</script>
```

### The Fisher Yates Method

위의 무작위 배열에서 사용하는 array.sort() 방법이 정확하지 않아서(우선순위가 있음) Fisher Yates Shuffle 이라는 방법을 자주 씀

예제
{: .label .label-purple .mt-3}
<div class="code-example" markdown="1">
<button onclick="myFunction()">Try it</button>

<p id="demo"></p>

<script>
var points = [40, 100, 1, 5, 25, 10];
document.getElementById("demo").innerHTML = points;  

function myFunction() {
var i, j, k;
  for (i = points.length -1; i > 0; i--) {
    j = Math.floor(Math.random() * i)
    k = points[i]
    points[i] = points[j]
    points[j] = k
  }
  document.getElementById("demo").innerHTML = points;
}
</script>
</div>
```html
<button onclick="myFunction()">Try it</button>

<p id="demo"></p>

<script>
var points = [40, 100, 1, 5, 25, 10];
document.getElementById("demo").innerHTML = points;  

function myFunction() {
var i, j, k;
  for (i = points.length -1; i > 0; i--) {
    j = Math.floor(Math.random() * i)
    k = points[i]
    points[i] = points[j]
    points[j] = k
  }
  document.getElementById("demo").innerHTML = points;
}
</script>
```

### Find the Highest (or Lowest) Array Value

배열에서는 최대 값이나 최소 값을 찾기위한 내장함수가 없음

그래서 **오름 or 내림차순으로 정렬한 첫 번째나 마지막번째가 highest or lowest value**

근데 최대나 최소값 하나만 원하면 정말 비효율적임(max() or min() 사용하는게 효율적)

#### Using Math.max() on an Array

`Math.max.apply` : 배열에서 가장 높은 숫자를 찾는 데 사용

예제
{: .label .label-purple .mt-3}
```js
function myArrayMax(arr) {
	Math.max.apply(null, arr);
	or
	Math.max(1, 2, 3) //이경우 매개변수에 배열이 들어가면 안됨, toString이나 join 써도 안됨ㅠ
}
```

#### Using Math.min() on an Array

`Math.min.apply` : 배열에서 가장 낮은 숫자를 찾는 데 사용

예제
{: .label .label-purple .mt-3}
```js
function myArrayMax(arr) {
	Math.min.apply(null, arr);
	or
	Math.min(1, 2, 3) //이경우에도 매개변수에 배열이 들어가면 안됨, toString이나 join 써도 안됨
}
```

### My Min / Max JavaScript Methods

* 최대 값 찾기

    예제
    {: .label .label-purple .mt-3}
    <div class="code-example" markdown="1">
    <p>The highest number is <span id="demo"></span>.</p>

    <script>
    var points = [40, 100, 1, 5, 25, 10];
    document.getElementById("demo").innerHTML = myArrayMax(points);

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
    </script>
    </div>
    ```html
    <p>The highest number is <span id="demo"></span>.</p>

    <script>
    var points = [40, 100, 1, 5, 25, 10];
    document.getElementById("demo").innerHTML = myArrayMax(points);

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
    </script>
    ```
    
* 최소 값 찾기

    예제
    {: .label .label-purple .mt-3}
    <div class="code-example" markdown="1">
    <p>The lowest number is <span id="demo"></span>.</p>

    <script>
    var points = [40, 100, 1, 5, 25, 10];
    document.getElementById("demo").innerHTML = myArrayMin(points);

    function myArrayMin(arr) {
      var len = arr.length;
      var min = Infinity;
      while (len--) {
        if (arr[len] < min) {
          min = arr[len];
        }
      }
      return min;
    }
    </script>
    </div>
    ```html
    <p>The lowest number is <span id="demo"></span>.</p>

    <script>
    var points = [40, 100, 1, 5, 25, 10];
    document.getElementById("demo").innerHTML = myArrayMin(points);

    function myArrayMin(arr) {
      var len = arr.length;
      var min = Infinity;
      while (len--) {
        if (arr[len] < min) {
          min = arr[len];
        }
      }
      return min;
    }
    </script>
    ```

### Sorting Object Arrays 

배열에 포함된 객체를 정렬할 때 사용

* 숫자 정렬

    예제
    {: .label .label-purple .mt-3}
    <div class="code-example" markdown="1">
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
      cars.sort(function(a, b){return a.year - b.year});
      displayCars();
    }

    function displayCars() {
      document.getElementById("demo").innerHTML =
      cars[0].type + " " + cars[0].year + "<br>" +
      cars[1].type + " " + cars[1].year + "<br>" +
      cars[2].type + " " + cars[2].year;
    }
    </script>
    </div>
    ```html
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
      cars.sort(function(a, b){return a.year - b.year});
      displayCars();
    }

    function displayCars() {
      document.getElementById("demo").innerHTML =
      cars[0].type + " " + cars[0].year + "<br>" +
      cars[1].type + " " + cars[1].year + "<br>" +
      cars[2].type + " " + cars[2].year;
    }
    </script>
    ```

* 문자열 정렬

    예제
    {: .label .label-purple .mt-3}
    <div class="code-example" markdown="1">
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
        if (x < y) {return -1;}
        if (x > y) {return 1;}
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
    </div>
    ```html
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
        if (x < y) {return -1;} //마이너스면 앞으로 정렬
        if (x > y) {return 1;}  //플러스면 뒤로 정렬 – 그래서 알파벳이 클수록 앞으로감
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
    ```
    
    