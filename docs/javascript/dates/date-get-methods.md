---
layout: default
title: Date Get Methods
parent: Dates
grand_parent: JavaScript
nav_order: 2
---

# JavaScript Date Get Methods
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Date Get Methods

### Sorting an Array

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