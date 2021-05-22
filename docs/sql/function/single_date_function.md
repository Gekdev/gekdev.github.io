---
layout: default
title: Single Date Function
parent: Function
grand_parent: SQL
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

**sysdate : 시스템의 현재 날짜와 시간**

날짜 함수를 사용할 때 유용하게 이용됨

```sql
select sysdate from dual;
```
![](https://gekdev.github.io/docs/sql/function/example/sysdate.jpg)

### months_between()

**두 날짜의 개월수, 결과는 숫자**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**months_between(날짜문자열, 날짜문자열)** 
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

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**add_months(날짜문자열, 숫자)** 
</div>
```sql
select sysdate
     , add_months(sysdate, 2)
from dual;
```

![](https://gekdev.github.io/docs/sql/function/example/add_month.jpg)

### next_day()

**주어진 날짜를 기준으로 돌아오는 날짜를 출력, 결과는 날짜**

1부터 일요일, ... 7 토요일

Sun과 같이 문자열도 사용가능

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**next_day(날짜문자열, 1~7 or sun~sat)** 
</div>
```sql
select sysdate
    , next_day(sysdate, 1) 일요일 -- 1~7 : 일요일~토요일
    , next_day(sysdate, 2) 월
    , next_day(sysdate, 3) 화
    , next_day(sysdate, 4) 수
    , next_day(sysdate, 5) 목
    , next_day(sysdate, 6) 금
    , next_day(sysdate, 7) 토
    , next_day(sysdate, 'SUN')	-- SUN ~ SAT	 
from dual;
```

![](https://gekdev.github.io/docs/sql/function/example/next_day.jpg)

### last_day()

**주어진 날짜가 속한 달의 마지막 날짜를 출력**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**last_day(날짜문자열)** 
</div>
```sql
select sysdate
    , last_day(sysdate)
    , last_day('2024-02-20')
from dual;
```

![](https://gekdev.github.io/docs/sql/function/example/last_day.jpg)

### Date function with round() / trunc()

숫자함수에서 했던 성질 그대로 날짜를 반올림하거나 버림

```sql
select sysdate
     , round(sysdate)
     , trunc(sysdate) 
  from dual;
```
  
![](https://gekdev.github.io/docs/sql/function/example/date_round.jpg)

### Example

Q1. EMP 테이블에서 ename, hiredate, 근속월, 근속년수 출력

```sql
select empno
    , ename
    , hiredate
    , trunc(months_between(sysdate, hiredate), 0) 근속월
    , trunc(trunc(months_between(sysdate, hiredate), 0) / 12, 0) 근속년수
from emp;
```

![](https://gekdev.github.io/docs/sql/function/example/date_example.jpg)

---

## 형변환함수

### to_number()

**문자형을 숫자로 변환**

묵시적 형변환과 명시적 형변환 두가지가 있음
    
문자열이 포함되어 있으면 오류가 발생됨

```sql
select '2a' + 2 from dual;
select 'A' + 2 from dual;
```
![](https://gekdev.github.io/docs/sql/function/example/to_num_error.jpg)

1. 묵시적(자동) 형변환

    ```sql
    select 2 + '2' from dual; 
    select '2' + 2 from dual;
    ```
    
    ![](to_num.jpg)

2. 명시적(수동) 형변환
    
    ```sql
    select to_number('2') + 2 from dual; 
    ```
    
    ![](to_num2.jpg)

### to_char() from date

**날짜형을 문자로 변환**


### to_char() from number

**날짜형을 숫자로 변환**

### to_date() 

**문자형을 날짜형으로 변환**





