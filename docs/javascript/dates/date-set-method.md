---
layout: default
title: Date Set Methods
parent: Dates
grand_parent: JavaScript
nav_order: 3
---

# JavaScript Date Set Methods
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Date Set Methods

### Sorting an Array

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
