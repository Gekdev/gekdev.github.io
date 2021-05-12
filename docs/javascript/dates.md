---
layout: default
title: Dates
parent: JavaScript
nav_order: 11
has_children: true
---

# JavaScript Date Objects
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Date Objects Basic

### What is Date Object?

**브라우저의 시간대를 사용하고 날짜를 전체 텍스트 문자열로 표시할 수 있는 날짜 객체**

&#9656; 날짜 객체는 정적임

### Time Zones

시간대를 지정하지 않고 날짜를 설정할 때 JavaScript는 **브라우저의 시간대를 사용** (가져올때도 동일함)

---

## Date Technic

### Creating Date Objects 

**`new Date()` 생성자로 생성**

1. new Date()

2. new Date(year, month, day, hours, minutes, seconds, milliseconds)

3. new Date(milliseconds)

4. new Date(date string)

#### new Date()

**새 날짜**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
new Date()
</div>
```js
var d = new Date();
document.getElementById("demo").innerHTML = d;
//d = 현재 시간 표시
```

#### new Date(year, month, day, hours, minutes, seconds, milliseconds)

**지정된 날짜 및 시간으로 새 날짜 개체 생성**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
new Date(year, month, day, hours, minutes, seconds, milliseconds)
</div>
```js
var d = new Date(2018, 11, 24, 10, 33, 30, 0);
document.getElementById("demo").innerHTML = d;
//d = Mon Dec 24 2018 10:33:30 GMT+0900 (대한민국 표준시)
```

&#9656; year, month, day, hour, minute, second, millisecond 순으로 진행됨

&#9656; 매개변수를 하나씩 생략하면 뒤부터(milisecond) 사라짐

&#9656; 새 날짜로 날짜 객체를 생성하는데의 최소 매개변수 갯수는 두개, 하나만 남으면 [milisecond값으로 인식](https://www.w3schools.com/js/tryit.asp?filename=tryjs_date_new_numbers1)

&#9656; 자바스크립트는 월을 0부터 11로 센다 (January : 0, December i: 11)

&#9656; 첫번째 매개변수를 10의 자리로 넣으면 자동으로 19라는 값이 붙음

```js
var d = new Date(99, 11, 24);
document.getElementById("demo").innerHTML = d;
// d = Fri Dec 24 1999 00:00:00 GMT+0900 (대한민국 표준시)
```

#### new Date(milliseconds)

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
new Date(milliseconds)
</div>
```js
var d = new Date(1332255600000);
document.getElementById("demo").innerHTML = d;
//d = Wed Mar 21 2012 00:00:00 GMT+0900 (대한민국 표준시)
```
&#9656; new Date() 함수에서 매개변수가 단 하나면 miliseconds로 인식함

&#9656; 1970 년 1 월 1 일 00:00:00 UTC(협정 세계시) 이후 날짜를 밀리 초 단위로 저장

&#9656; 0 시간은 1970 년 1 월 1 일 00:00:00 UTC

&#9656; 하루(24시간)는 86,400,000 밀리 초

#### new Date(date string)

**날짜 문자열 에서 새 날짜 개체를 만듦**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
new Date(date string)
</div>
```js
var d = new Date("October 13, 2014 11:13:00");
document.getElementById("demo").innerHTML = d;
//d = Mon Oct 13 2014 11:13:00 GMT+0900 (대한민국 표준시)
```

뒤 [Date Formats](https://gekdev.github.io/docs/javascript/dates/date-formats/)에서 더 자세하게 설명

### Parsing Date Input 

**Date.parse() method**

**유효한 날짜 문자열이있는 경우 밀리초로 변환 할 수 있음**

&#9656; 1970년 1월 1일 사이의 밀리초 수를 기준으로 Date.parse() 날짜 사이의 밀리초를 반환함

&#9656; [앞서 봤던것처럼](https://gekdev.github.io/docs/javascript/dates/#new-datemilliseconds) 밀리 초 수를 사용하여 날짜 개체로 변환할 수 있음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
Date.parse(date string)
</div>
```js
var msec = Date.parse("March 21, 2012");
document.getElementById("demo").innerHTML = msec;
//msec = 1332255600000

var d = new Date(msec);
document.getElementById("demo").innerHTML = d;
//d = Wed Mar 21 2012 00:00:00 GMT+0900 (대한민국 표준시)
```

### Month number to Month name

다음장 [get date methods](https://gekdev.github.io/docs/javascript/dates/get_set_methods/#month-number-to-month-name) 에서 확인

### Day number to Day name

다음장 [get date methods](https://gekdev.github.io/docs/javascript/dates/get_set_methods/#day-number-to-day-name) 에서 확인