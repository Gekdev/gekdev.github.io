---
layout: default
title: Date Formats
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

## Date Formats

### Date Input

일반적으로 3 가지 유형의 JavaScript 날짜 입력 형식이 있음

| Type         | Example                                     |
|:-------------|:--------------------------------------------|
| ISO Date     | "2015-03-25" (The International Standard)   |
| Short Date   | "03/25/2015"                                |
| Long Date    | "Mar 25 2015" or "25 Mar 2015"              |

&#9656; ISO format만 자바스크립트의 엄격한 표준에 맞고 나머지들은 정의되어 있지 않으며 브라우저에 따라 다를 수 있음

### Date Output (ISO Dates)

**입력 형식에 관계없이 JavaScript는(기본적으로) 전체 텍스트 문자열 형식으로 날짜를 출력**

&#9656; 기본적으로 YYYY-MM-DD형식

&#9656; MM, DD 설정하지 않으면 자동으로 01, 시간은 9시

★ 여러 가지 방법으로 쓸 수 있는데 그냥 YYYY-MM-DD맞춰 쓰세요

```js
new Date("2015-03-25");

// Wed Mar 25 2015 09:00:00 GMT+0900 (대한민국 표준시)
```

#### ISO Dates (Date-Time)

YYYY-MM-DDTHH:MM:SSZ 형식으로도 사용할 수 있음

```js
var d = new Date("2015-03-25T12:00:00Z");
//d = Wed Mar 25 2015 21:00:00 GMT+0900 (대한민국 표준시)
```

&#9656; 날짜와 시간은 대문자 T로 구분

&#9656; UTC 시간은 대문자 Z로 정의

&#9656; UTC를 기준으로 시간을 수정하려면 Z를 제거하고 대신 + HH : MM 또는 -HH : MM을 추가

```js
var d = new Date("2015-03-25T12:00:00-06:30");
// d = Thu Mar 26 2015 03:00:00 GMT+0900 (대한민국 표준시)
```

Date Input - Parsing Dates – ms로 바꾸는 것
아래 예시는 ms로 바꾼걸 다시 date로 바꾸는 거
	var msec = Date.parse("March 21, 2012");
	var d = new Date(msec);
	document.getElementById("demo").innerHTML = d;

### Short Dates

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
new Date("MM/DD/YYYY");
</div>
```js
var d = new Date("03/25/2015");
```

### Warnings!

#### no 0 problem

**일부 브라우저에서는 앞에 0이없는 월 또는 일에 오류가 발생할 수 있음**

예시
{: .label .label-purple .mt-2}
```js
var d = new Date("2015-3-25");
```

#### "YYYY / MM / DD" error

**"YYYY / MM / DD"의 동작은 정의되지 않음**

&#9656; 일부 브라우저는 형식을 추측하려고 하고, 일부는 NaN을 반환함

예시
{: .label .label-purple .mt-2}
```js
var d = new Date("2015/03/25");
```

#### "DD-MM-YYYY" error

**"DD-MM-YYYY"의 동작은 정의되지 않음**

&#9656; 일부 브라우저는 형식을 추측하려고 하고, 일부는 NaN을 반환함

예시
{: .label .label-purple .mt-2}
```js
var d = new Date("25-03-2015");
```
