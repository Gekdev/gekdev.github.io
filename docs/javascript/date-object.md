---
layout: default
title: Date Objects
parent: JavaScript
nav_order: 3
---

# JavaScript Date Objects
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Date Objects

### JavaScript Programs

24. JavaScript Date Objects
Creating Date Objects (4 ways)
◆ new Date() : current date and time like -> Mon Feb 24 2020 17:48:35 GMT+0900 (대한민국 표준시)
◆ new Date(year, month, day, hours, minutes, seconds, milliseconds): specified date and time.
	You cannot omit month. If you supply only one parameter it will be treated as milliseconds.
	One and two digit years will be interpreted as 19xx: new Date(98,11,22) or(9,3,11) = 1909
◆ new Date(milliseconds) : var d = new Date(2018) -> Thu Jan 01 1970 09:00:02 GMT+0900 (대한민국 표준시)
◆ new Date(date string) : creates a new date object from a date string:
	var d = new Date("October 13, 2014 11:13:00");
	Mon Oct 13 2014 11:13:00 GMT+0900 (대한민국 표준시)

JavaScript Stores Dates as Milliseconds
JavaScript stores dates as number of milliseconds since January 01, 1970, 00:00:00 UTC (Universal Time Coordinated).
Zero time is January 01, 1970 00:00:00 UTC.

new Date(milliseconds)
new Date(milliseconds) creates a new date object as zero time plus milliseconds
-0이면 1970대로 감

Date objects are static. The computer time is ticking, but date objects are not.
JavaScript counts months from 0 to 11.
One day (24 hours) is 86 400 000 milliseconds.

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

26. JavaScript Get Date Methods
how to use ...
	var a = new Date();
	a.method

Get Date Methods
● getFullYear()		Get the year as a four digit number (yyyy)
● getMonth()		Get the month as a number (0-11)
● getDate()		Get the day as a number (1-31)
● getHours()		Get the hour (0-23)
● getMinutes()		Get the minute (0-59)
● getSeconds()		Get the second (0-59)
● getMilliseconds()	Get the millisecond (0-999)
● getTime()		Get the time (milliseconds since January 1, 1970)
● getDay()		Get the weekday as a number (0-6)
● Date.now()		Get the time. ECMAScript 5.

월을 숫자 – 이름변환(요일도 방식은 똑같음)
var d = new Date();
var months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
document.getElementById("demo").innerHTML = months[d.getMonth()];

27. JavaScript Set Date Methods
사용방법은 get date와 똑같음

Set Date Methods
● setDate()		Set the day as a number (1-31)
● setFullYear()		Set the year (optionally month and day used by comma) //d.setFullYear(2020, 11, 3);
● setHours()		Set the hour (0-23)
● setMilliseconds()	Set the milliseconds (0-999)
● setMinutes()		Set the minutes (0-59)
● setMonth()		Set the month (0-11)
● setSeconds()		Set the seconds (0-59)
● setTime()		Set the time (milliseconds since January 1, 1970)

오늘과 시간비교는 그냥 두 개 시간 만든 후 하나는 비교한 날짜를 대입하고 if로 date를 비교하면 끝
https://www.w3schools.com/js/tryit.asp?filename=tryjs_date_compare
