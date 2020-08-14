---
layout: default
title: Dates
parent: JavaScript
nav_order: 9
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

JavaScript Date Object를 사용하면 날짜를 사용할 수 있습니다.

화 2020 년 7 월 21 일 20:59:37 GMT + 0900 (대한민국 표준시)

     
예
var d = new Date();
자바 스크립트 날짜 출력
기본적으로 JavaScript는 브라우저의 시간대를 사용하고 날짜를 전체 텍스트 문자열로 표시합니다.

화 2020 년 7 월 21 일 20:59:37 GMT + 0900 (대한민국 표준시)

이 자습서의 뒷부분에서 날짜를 표시하는 방법에 대해 더 많이 배울 것입니다.

날짜 객체 생성
날짜 개체는 new Date()생성자 로 만들어집니다 .

새 날짜 개체를 만드는 방법 은 4 가지 가 있습니다.

new Date()
new Date(year, month, day, hours, minutes, seconds, milliseconds)
new Date(milliseconds)
new Date(date string)
새로운 날짜 ()
new Date()현재 날짜와 시간 으로 새 날짜 객체를 만듭니다 .

예
var d = new Date();
날짜 개체는 정적입니다. 컴퓨터 시간이 촉박하지만 날짜 개체는 그렇지 않습니다.

새로운 날짜 ( 년, 월, ... )
new Date(year, month, ...)지정된 날짜 및 시간 으로 새 날짜 객체를 만듭니다 .

7 개의 숫자는 연도, 월, 일,시, 분, 초 및 밀리 초를 순서대로 지정합니다.

예
var d = new Date(2018, 11, 24, 10, 33, 30, 0);
참고 : JavaScript는 월을 0에서 11까지로 계산합니다.

1 월은 0입니다. 12 월은 11입니다.

6 개의 숫자는 년, 월, 일,시, 분, 초를 지정합니다.

예
var d = new Date(2018, 11, 24, 10, 33, 30);
5 개의 숫자는 연도, 월, 일, 시간 및 분을 지정합니다.

예
var d = new Date(2018, 11, 24, 10, 33);
4 개의 숫자는 년, 월, 일 및 시간을 지정합니다.

예
var d = new Date(2018, 11, 24, 10);
세 개의 숫자는 연도, 월 및 일을 지정합니다.

예
var d = new Date(2018, 11, 24);
2 자리 숫자는 연도와 월을 지정합니다.

예
var d = new Date(2018, 11);
월은 생략 할 수 없습니다. 하나의 매개 변수 만 제공하면 밀리 초로 처리됩니다.

예
var d = new Date(2018);
지난 세기
1-2 자리 연도는 19xx로 해석됩니다.

예
var d = new Date(99, 11, 24);
예
var d = new Date(9, 11, 24);
새로운 날짜 ( dateString )
new Date(dateString)날짜 문자열 에서 새 날짜 객체를 만듭니다 .

예
var d = new Date("October 13, 2014 11:13:00");
날짜 문자열은 다음 장에서 설명합니다.

JavaScript는 날짜를 밀리 초로 저장합니다
JavaScript는 1970 년 1 월 1 일 00:00:00 UTC (협정 세계시) 이후 날짜를 밀리 초 단위로 저장합니다.

제로 시간은 1970 년 1 월 1 일 00:00:00 UTC입니다.

이제 시간은 1970 년 1 월 1 일의 1595332777468 밀리 초 입니다.

새로운 날짜 ( 밀리 초 )
new Date(milliseconds)0을 더한 밀리 초로 새 날짜 객체를 만듭니다 .

예
var d = new Date(0);
1970 년 1 월 1 일 + 100,000 밀리 초는 1973 년 3 월 3 일입니다.

예
var d = new Date(100000000000);
1970 년 1 월 1 일에서 1 억 밀리 초를 뺀 값 은 대략 1966 년 10 월 31 일입니다.

예
var d = new Date(-100000000000);
예
var d = new Date(86400000);
하루 (24 시간)는 86 4 억 밀리 초입니다.

날짜 방법
Date 객체를 만들 때 여러 가지 방법으로 작업 할 수 있습니다.

Date 메서드를 사용하면 현지 시간 또는 UTC (범용 또는 GMT) 시간을 사용하여 년, 월, 일,시, 분, 초 및 밀리 초의 날짜 개체를 가져오고 설정할 수 있습니다.

날짜 방법과 시간대는 다음 장에서 다룹니다.

날짜 표시
JavaScript는 기본적으로 날짜를 전체 텍스트 문자열 형식으로 출력합니다.

Wed Mar 25 2015 09:00:00 GMT+0900 (대한민국 표준시)
HTML로 날짜 객체를 표시하면 toString()메서드 와 함께 날짜 객체가 자동으로 문자열로 변환됩니다 .

예
d = new Date();
document.getElementById("demo").innerHTML = d;
다음과 같습니다 :
d = new Date();
document.getElementById("demo").innerHTML = d.toString();
이 toUTCString()방법은 날짜를 UTC 문자열 (날짜 표시 표준)로 변환합니다.

예
var d = new Date();
document.getElementById("demo").innerHTML = d.toUTCString();
이 toDateString()방법은 날짜를 더 읽기 쉬운 형식으로 변환합니다.

예
var d = new Date();
document.getElementById("demo").innerHTML = d.toDateString();
이 toISOString()방법은 ISO 표준 형식을 사용하여 날짜를 문자열로 변환합니다.

예
var d = new Date();
document.getElementById("demo").innerHTML = d.toISOString();

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



