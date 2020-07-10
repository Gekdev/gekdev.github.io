---
layout: default
title: Dates
parent: JavaScript
nav_order: 7
has_children: true
---

# JavaScript Date Objects
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Date Objects

### Creating Date Objects 

(4 ways)

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



