---
layout: default
title: Math
parent: JavaScript
nav_order: 10
---

# JavaScript Math Object
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Math Object

### Math Object Basic

**숫자에 대한 수학적 작업을 수행할 때 사용**

&#9656; 다른 객체와 다르게 Math 객체에는 생성자(constructor)가 없음 (like new Math ())

&#9656; Math 객체는 정적이며 Math 객체를 생성하지 않고도 모든 메소드와 특성들을 사용할 수 있음

---

## Math Properties

### 8 Math Constants

아래는 Math 속성으로 액세스 할 수 있는 **8개의 수학 상수**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
Math.property
</div>
```js
* Math.E        // returns Euler's number
* Math.PI       // returns PI
* Math.SQRT2    // returns the square root of 2
* Math.SQRT1_2  // returns the square root of 1/2
* Math.LN2      // returns the natural logarithm of 2
* Math.LN10     // returns the natural logarithm of 10
* Math.LOG2E    // returns base 2 logarithm of E
* Math.LOG10E   // returns base 10 logarithm of E
```

---

## Math Methods

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
Math.method.(number)
</div>

### Making Number to Integer

숫자를 정수로 바꾸는 방법

Math.round(x), Math.ceil(x), Math.floor(x), Math.trunc(x), Math.sign()

#### Math.ceil()

**올림**

```js
Math.ceil(4.4);     // returns 5
```

#### Math.round()

**반올림**

```js
Math.round(4.5)     // returns 5
```

#### Math.floor()

**내림**

```js
Math.floor(4.7);    // returns 4
```

#### Math.trunc()

**정수 부분만 반환**

```js
Math.trunc(4.7);    // returns 4
```

#### Math.sign()

**값이 양수이면 1, 0이면 0, 음수이면 -1**

```js
Math.sign(-4);    // returns -1
Math.sign(0);    // returns 0
Math.sign(4);    // returns 1
```

### Calculating the Number 

#### Math.pow()

**제곱**

```js
Math.pow(8, 2);      // returns 64
```

#### Math.sqrt()

**제곱근 square root**

```js
Math.sqrt(64);      // returns 8
```

#### Math.abs()

**무조건 양수로**

```js
Math.abs(-4.7);     // returns 4.7
```

#### Math.sin()

**사인값, radians으로 표시된 x각도의 사인(-1과 1 사이의 값)을 반환**

&#9656; 라디안 대신도를 사용하려면도를 라디안으로 변환해야합

&#9656; 라디안 각도 = 각도 x PI / 180

```js
Math.sin(90 * Math.PI / 180);     // returns 1 (the sine of 90 degrees)
```

#### Math.cos()

**코사인값, radians으로 표시된 x각도의 코사인(-1과 1 사이의 값)을 반환**

&#9656; 라디안 대신도를 사용하려면도를 라디안으로 변환해야합

&#9656; 라디안 각도 = 각도 x PI / 180

```js
Math.cos(0 * Math.PI / 180);     // returns 1 (the cos of 0 degrees)
```

### Finding Certain Number

#### Math.min() and Math.max()

**인수 목록에서 가장 낮은 또는 높은 값**

```js
Math.min(0, 150, 30, 20, -8, -200);  // returns -200
Math.max(0, 150, 30, 20, -8, -200);  // returns 150
```

#### Math.random()

**0(포함)과 1(제외)사이의 난수를 반환**

&#9656; 항상 1보다 작은 값을 반환함

```js
Math.random();     // returns a random number like 0.09714565914195883
```

#### Math.log()

**x의 자연 로그를 반환**

&#9656; Math.E 와 Math.log()는 같음

```js
Math.log(1);    // returns 0
```

<span class="fs-2">
[W3School](https://www.w3schools.com/js/js_math.asp){: .btn .btn-outline .mt-2 }
</span>

### Math Method Technic

#### Random Integers

1. 0부터 9까지 랜덤한 숫자 생성

	```js
	Math.floor(Math.random() * 10);
    ```

2. 0부터 10까지 랜덤한 숫자 생성

	```js
	Math.floor(Math.random() * 11);
	
	or

	Math.floor(Math.random() * 10)+1;
	```

#### A Proper Random Function

**최소값, 최대값을 매개변수로 받는 랜덤 정수 생성함수**

1. 최대값 미포함 

	```js
	function getRndInteger(min, max) {
	    return Math.floor(Math.random() * (max - min) ) + min;
	}
	```

	<span class="fs-2">
	[W3School](https://www.w3schools.com/js/tryit.asp?filename=tryjs_random_function){: .btn .btn-outline .mt-2 }
	</span>
	
2. 최대값 포함

	```js
	function getRndInteger(min, max) {
	    return Math.floor(Math.random() * (max - min + 1) ) + min;
	}
	```

	<span class="fs-2">
	[W3School](https://www.w3schools.com/js/tryit.asp?filename=tryjs_random_function2){: .btn .btn-outline .mt-2 }
	</span>

### Complete Object Methods Reference

Math 객체에 대한 모든 메소드를 볼 수 있음

<span class="fs-2">
[W3School](https://www.w3schools.com/jsref/jsref_obj_math.aspp){: .btn .btn-outline .mt-2 }
</span>
