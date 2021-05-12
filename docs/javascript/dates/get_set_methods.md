---
layout: default
title: Get and Set Methods
parent: Dates
grand_parent: JavaScript
nav_order: 2
---

# JavaScript Date Get and Set Methods
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Date Get Methods

### getTime()

**1970년 1월 1일 이후의 밀리초 수를 반환**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var d = new Date();

d.getTime();
</div>
```js
var d = new Date();
document.getElementById("demo").innerHTML = d.getTime();
//demo = 1620799209106(현재 코드 작성시간)
```

### getFullYear()

**날짜의 연도를 4자리 숫자로 반환**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var d = new Date();

d.getFullYear();
</div>
```js
var d = new Date();
document.getElementById("demo").innerHTML = d.getFullYear();
//demo = 2021(현재 코드 작성시간)
```

### getMonth()

**날짜의 월을 숫자(0-11)로 반환**

&#9656; 1월부터 0으로 시작함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">

</div>
```js
var d = new Date();
document.getElementById("demo").innerHTML = d.getMonth() + 1;
//To get the correct month, you must add 1:
//demo = 5(현재 코드 작성시간)
```

#### Month number to Month name

**월을 숫자에서 이름으로 변환하는 방법**

&#9656; 요일도 하는 방식은 똑같음

```js
var d = new Date();
var months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
document.getElementById("demo").innerHTML = months[d.getMonth()];
//demo = May(현재 코드 작성시간)
```

### getDate()

**날짜를 숫자(1-31)로 반환**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var d = new Date();

d.getDate();
</div>
```js
var d = new Date();
document.getElementById("demo").innerHTML = d.getDate();
//demo = 12(현재 코드 작성시간)
```

### getHours()

**날짜의 시간을 숫자 (0-23)로 반환**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var d = new Date();

d.getHours();
</div>
```js
var d = new Date();
document.getElementById("demo").innerHTML = d.getHours();
//demo = 15(현재 코드 작성시간)
```

### getMinutes()

**날짜의 분을 숫자 (0-59)로 반환**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var d = new Date();

d.getMinutes();
</div>
```js
var d = new Date();
document.getElementById("demo").innerHTML = d.getMinutes();

// demo = 17(현재 코드 작성시간)
```

### getSeconds()

**날짜의 초를 숫자 (0-59)로 반환**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var d = new Date();

d.getSeconds();
</div>
```js
var d = new Date();
document.getElementById("demo").innerHTML = d.getSeconds();
//demo = 49(현재 코드 작성시간)
```

### getMilliseconds()

**날짜의 밀리 초를 숫자 (0-999)로 반환**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var d = new Date();

d.getMilliseconds();
</div>
```js
var d = new Date();
document.getElementById("demo").innerHTML = d.getMilliseconds();
//demo = 185(현재 코드 작성시간)
```

### getDay()

**날짜의 요일을 숫자 (0-6)로 반환**

&#9656; 0부터 일요일로 간주함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var d = new Date();

d.getDay();
</div>
```js
var d = new Date();
document.getElementById("demo").innerHTML = d.getDay();
//demo = 3(현재 코드 작성시간, 수요일)
```

#### Day number to Day name

**요일을 숫자에서 이름으로 변환하는 방법**

```js
var d = new Date();
var days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
document.getElementById("demo").innerHTML = days[d.getDay()];
//demo = Wednesday(현재 코드 작성시간)
```

### UTC Date Methods

UTC Date methods들은 **UTC 날짜(Universal Time Zone 날짜) 작업에 사용됨**

| Method                | Description                                            |
|:----------------------|:-------------------------------------------------------|
| getUTCDate()          | getDate()와 같지만 UTC date를 가지고 옴                   |
| getUTCDay()           | getDay()와 같지만 UTC day를 가지고 옴                     |
| getUTCFullYear()      | getFullYear()와 같지만 UTC year를 가지고 옴               |
| getUTCHours()         | getHours()와 같지만 UTC hour를 가지고 옴                  |
| getUTCMilliseconds()  | getMilliseconds()와 같지만 UTC milliseconds를 가지고 옴   |
| getUTCMinutes()       | getMinutes()와 같지만 UTC minutes를 가지고 옴             |
| getUTCMonth()         | getMonth()와 같지만 UTC month를 가지고 옴                 |
| getUTCSeconds()       | getSeconds()와 같지만 UTC seconds를 가지고 옴             |

---

## Date Set Methods

### setFullYear()

**날짜 개체의 연도를 설정**

&#9656; 선택적으로 월과 일을 설정할 수 있음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var d = new Date();

d.setFullYear(YYYY);
</div>
```js
var d = new Date();
d.setFullYear(2020, 11, 3);
document.getElementById("demo").innerHTML = d;
//d = Thu Dec 03 2020 15:48:05 GMT+0900 (대한민국 표준시) (현재 코드 작성시간)
```

### setMonth()

**날짜 개체의 월(0-11)을 설정**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var d = new Date();

d.setMonth(MM);
</div>
```js
var d = new Date();
d.setMonth(11);
document.getElementById("demo").innerHTML = d;
//d = Sun Dec 12 2021 15:48:43 GMT+0900 (대한민국 표준시) (현재 코드 작성시간)
```

### setDate()

**날짜 개체의 요일(1-31)을 설정**

&#9656; 날짜를 연산할 수 있음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var d = new Date();

d.setDate(DD);
</div>
```js
var d = new Date();
d.setDate(d.getDate() + 50); // 현재 날짜에서 50일 추가
document.getElementById("demo").innerHTML = d;
//d = Thu Jul 01 2021 15:51:50 GMT+0900 (대한민국 표준시) (현재 코드 작성시간)
```

### setHours()

**날짜 개체의 시간(0-23)을 설정**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var d = new Date();

d.setHours(HH);
</div>
```js
var d = new Date();
d.setHours(22);
document.getElementById("demo").innerHTML = d;
//d = Wed May 12 2021 22:52:49 GMT+0900 (대한민국 표준시) (현재 코드 작성시간)
```

### setMinutes()

**날짜 개체의 분(0-59)을 설정**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var d = new Date();

d.setMinutes(MM);
</div>
```js
var d = new Date();
d.setMinutes(30);
document.getElementById("demo").innerHTML = d;
// d = Wed May 12 2021 15:30:02 GMT+0900 (대한민국 표준시) (현재 코드 작성시간)
```

### setSeconds()

**날짜 개체 (0-59)의 초를 설정**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
var d = new Date();

d.setSeconds(SS);
</div>
```js
var d = new Date();
d.setSeconds(30);
document.getElementById("demo").innerHTML = d;
//d = Wed May 12 2021 15:55:30 GMT+0900 (대한민국 표준시) (현재 코드 작성시간)
```

### Compare Dates

날짜를 미리 설정해놓고 날짜끼리 비교할 수 있음

```js
var today, someday, text;
today = new Date();
someday = new Date();
someday.setFullYear(2100, 0, 14);

if (someday > today) {
  text = "Today is before January 14, 2100.";
} else {
  text = "Today is after January 14, 2100.";
}
document.getElementById("demo").innerHTML = text;
//text = Today is before January 14, 2100. (현재 코드 작성시간)
```

---

## Complete JavaScript Date Reference

<span class="fs-2">
[W3School](https://www.w3schools.com/jsref/jsref_obj_date.asp){: .btn .btn-outline .mt-2}
</span>
