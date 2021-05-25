---
layout: default
title: Date Function
parent: Function
grand_parent: SQL / Oracle
nav_order: 3
---

# SQL Single Date Function
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Single Date Functions

### sysdate

**시스템의 현재 날짜와 시간**

&#9656; 날짜 함수를 사용할 때 유용하게 이용됨

```sql
select sysdate from dual;
```
![](https://gekdev.github.io/docs/sql/function/example/sysdate.jpg)

#### 날짜 계산하기

| 종류 | 결과 | 의미|
|:----|:-----|:---|
|date+number | 날짜 | 날짜에 일수를 더하여 날짜 계산    |
|date-number | 날짜 | 날짜에 일수를 빼서 날짜를 계산    |
|date-date   | 일수 | 날짜와 날짜를 빼서 일수를 계산    |
|date+number/24 | 날짜 | 날짜에 시간을 더하여 날짜 계산 |


### months_between()

**두 날짜의 개월수가 몇 개월인지를 반환함, 결과는 숫자**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
months_between(날짜문자열, 날짜문자열) 
</div>
```sql
select months_between(sysdate, '19981205')
    , months_between(sysdate, hiredate)
    , round(months_between(sysdate, hiredate),0)
from emp;
```

![](https://gekdev.github.io/docs/sql/function/example/month_between.jpg)

### add_months()

**주어진 날짜에 개월수를 더함, 결과는 날짜**

&#9656; 숫자는 정수여야 하고 음수일수도 있음 

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
add_months(날짜문자열, 숫자) 
</div>
```sql
select sysdate
     , add_months(sysdate, 2)
from dual;
```

![](https://gekdev.github.io/docs/sql/function/example/add_month.jpg)

### next_day()

**주어진 날짜를 기준으로 돌아오는 날짜를 출력, 결과는 날짜**

&#9656; 1부터 일요일, ... 7 토요일

&#9656; Sun과 같이 문자열도 사용가능

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
next_day(날짜문자열, 1~7 or sun~sat) 
</div>
```sql
select sysdate
    , next_day(sysdate, 1) 일요일 -- 1 : 일요일
    , next_day(sysdate, 2) 월    -- 2
    , next_day(sysdate, 3) 화    -- 3
    , next_day(sysdate, 4) 수    -- 4
    , next_day(sysdate, 5) 목    -- 5
    , next_day(sysdate, 6) 금    -- 6
    , next_day(sysdate, 7) 토    -- 7
    , next_day(sysdate, 'SUN')	-- SUN ~ SAT	 
from dual;
```

![](https://gekdev.github.io/docs/sql/function/example/next_day.jpg)

### last_day()

**주어진 날짜가 속한 달의 마지막 날짜를 출력**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
last_day(날짜문자열) 
</div>
```sql
select sysdate
    , last_day(sysdate)
    , last_day('2024-02-20')
from dual;
```

![](https://gekdev.github.io/docs/sql/function/example/last_day.jpg)

### round() / trunc()

**숫자함수에서 했던 성질 그대로 날짜를 반올림하거나 버림**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
round(date, format) 

trunc(date, format) 
</div>

| 포멧 모델 | 단위 |
|:---------|:-----|
|CC, SCC | 자리 연도의 끝 두 글자를 기준으로 반올림 |
|SYYY, YYYY, YEAR, SYEAR, YYY, YY, Y | 년(7월 1일부터 반올림) |
|DDD, D, J | 일을 기준 |
|HH, HH12, HH24 | 시를 기준 |
|Q | 한 분기의 두번째 달에 16일을 기준으로 반올림 |
|MONTH, MON, MM, RM | 월(16일을 기준으로 반올림) |
|DAY, DY, D | 한 주가 시작되는 날짜 |
|MI | 분을 기준 |

```sql
select sysdate
     , round(sysdate)
     , trunc(sysdate) 
  from dual;
```
  
![](https://gekdev.github.io/docs/sql/function/example/date_round.jpg)

---

## Example

Q1. EMP 테이블에서 ename, hiredate, 근무일수, 근속월, 근속년수 출력

```sql
select empno
    , ename
    , hiredate
    , trunc(sysdate-hiredate) 근무일수
    , trunc(months_between(sysdate, hiredate), 0) 근속월
    , trunc(trunc(months_between(sysdate, hiredate), 0) / 12, 0) 근속년수
from emp;
```

![](https://gekdev.github.io/docs/sql/function/example/date_example.jpg)
