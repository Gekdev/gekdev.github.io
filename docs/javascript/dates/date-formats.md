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

## Array Sort

### Sorting an Array

25. JavaScript Date Formats
JavaScript Date Input
There are generally 3 types of JavaScript date input formats:

Type		Example
ISO Date		"2015-03-25" (The International Standard) // The ISO format follows a strict standard in JavaScript.
Short Date	"03/25/2015"
Long Date	"Mar 25 2015" or "25 Mar 2015"

JavaScript Date Output
default : Wed Mar 25 2015 09:00:00 GMT+0900 (대한민국 표준시)

JavaScript ISO Dates
The ISO 8601 syntax (YYYY-MM-DDTHH:MM:SSZ)
var d = new Date("2015-03-25");	//Wed Mar 25 2015 09:00:00 GMT+0900 (대한민국 표준시
or var d = new Date("2015-03-25T12:00:00Z");

- MM, DD 설정하지 않으면 자동으로 01, 시간은 9시

여러 가지 방법으로 쓸 수 있는데 그냥 YYYY-MM-DD맞춰 쓰세요

Date Input - Parsing Dates – ms로 바꾸는 것
아래 예시는 ms로 바꾼걸 다시 date로 바꾸는 거
	var msec = Date.parse("March 21, 2012");
	var d = new Date(msec);
	document.getElementById("demo").innerHTML = d;
