---
layout: default
title: Formats
parent: Dates
grand_parent: JavaScript
nav_order: 1
---

# JavaScript Date Formats
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Date Input and Output 

### Date Input

new Date(date string)으로 생성할때는 일반적으로 3 가지 유형의 JavaScript 날짜 입력형식이 있음

| Type         | Example                                     |
|:-------------|:--------------------------------------------|
| ISO Date     | "2015-03-25" (The International Standard)   |
| Short Date   | "03/25/2015"                                |
| Long Date    | "Mar 25 2015" or "25 Mar 2015"              |

&#8594; ISO format만 자바스크립트의 엄격한 표준에 맞고 나머지들은 정의되어 있지 않으며 브라우저에 따라 다를 수 있음

### Date Output

**입력 형식에 관계없이 JavaScript는(기본적으로) 전체 텍스트 문자열 형식으로 날짜를 출력**

```js
new Date("2015-03-25");

// Wed Mar 25 2015 09:00:00 GMT+0900 (대한민국 표준시)
```

---

## Date Input Formats

### ISO Dates (Date-Time)

**기본적으로 YYYY-MM-DD형식**

&#9656; MM, DD 설정하지 않으면 자동으로 01, 시간은 9시

★ YYYY-MM이나 YYYY로 쓸 수 있는데 그냥 YYYY-MM-DD맞춰 쓰세요

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
new Date("YYYY-MM-DD");
</div>
```js
var d = new Date("2015-03-25");
var d = new Date("2015-03");
var d = new Date("2015");
```

심화
{: .label .label-red .mt-2}
<div class="code-example" markdown="1">
&#9656; YYYY-MM-DDTHH:MM:SSZ 형식으로도 사용할 수 있음

&#9656; 날짜와 시간은 대문자 T로 구분

&#9656; UTC 시간은 대문자 Z로 정의

&#8594;  UTC를 기준으로 시간을 수정하려면 Z를 제거하고 대신 + HH : MM 또는 -HH : MM을 추가
</div>
```js
var d = new Date("2015-03-25T12:00:00Z");
//d = Wed Mar 25 2015 21:00:00 GMT+0900 (대한민국 표준시)

var d = new Date("2015-03-25T12:00:00-06:30");
// d = Thu Mar 26 2015 03:00:00 GMT+0900 (대한민국 표준시)
```

#### no 0 problem

**일부 브라우저에서는 앞에 0이없는 월 또는 일에 오류가 발생할 수 있음**

예시
{: .label .label-purple .mt-2}
```js
var d = new Date("2015-3-25");
```

#### "DD-MM-YYYY" error

**"DD-MM-YYYY"의 동작은 정의되지 않음**

&#9656; 일부 브라우저는 형식을 추측하려고 하고, 일부는 NaN을 반환함

예시
{: .label .label-purple .mt-2}
```js
var d = new Date("25-03-2015");
```

### Short Dates

**/ 사용**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
new Date("MM/DD/YYYY");
</div>
```js
var d = new Date("03/25/2015");
```

#### "YYYY / MM / DD" error

**"YYYY / MM / DD"의 동작은 정의되지 않음**

&#9656; 일부 브라우저는 형식을 추측하려고 하고, 일부는 NaN을 반환함

예시
{: .label .label-purple .mt-2}
```js
var d = new Date("2015/03/25");
```

### Long Dates

**월을 문자로 작성하기**

&#9656; 월과 일은 다른 순서로 작성할 수 있음 (DD MMM YYYY)

&#9656; 월은 전체(January) 또는 약어(Jan)로 작성 가능함

&#9656; ,로 구분가능하고 월은 case insensitive

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
new Date("MMM DD YYYY");
</div>
```js
var d = new Date("Mar 25 2015");
var d = new Date("25 Mar 2015");
var d = new Date("January 25 2015");
var d = new Date("Jan 25 2015");
var d = new Date("JANUARY, 25, 2015");
```
