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

**sysdate : 시스템의 현재 날짜와 시간**

날짜 함수를 사용할 때 유용하게 이용됨

```sql
select sysdate from dual;
```
![](https://gekdev.github.io/docs/sql/function/example/sysdate.jpg)

날짜 계산하기
{: .label .mt-2}

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

&#9656; 숫자는 정수여야 하고 음수일수도 있음 
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

**숫자함수에서 했던 성질 그대로 날짜를 반올림하거나 버림**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**round(date, format)** 

**trunc(date, format)** 
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

### Example

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

---

## Data Type Transformation Function

형변환 함수, **데이터 타입을 변환해야 하는 경우 사용**

![](https://gekdev.github.io/docs/sql/function/example/changing.jpg)

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

**날짜형이나 숫자를 문자로 변환**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**to_char(number / date, 'format')** 
</div>

1. 날짜 형식 모델

    | 종류 | 의미 |
    |:---------|:-----|
    | YYYY | 연도 표현(4자리)|
    | YY | 연도 표현(2자리) |
    | MM | 월을 숫자로 표현 |
    | MON | 월을 알파벳으로 표현 |
    | DAY | 요일 표현 |
    | DY | 요일을 약어로 표현 |

    ```sql
    --입사일에서 입사년도와 월만 출력하거나 입사일을 출력하되 요일까지 함께 출력
    select ename, hiredate
        , to_char(hiredate, 'YY-MM')
        , to_char(hiredate, 'YYYY/MM/DD DAY')
    from emp;
    ```

    ![](https://gekdev.github.io/docs/sql/function/example/to_char3.jpg)
    
2. 시간 형식 모델

    | 종류 | 의미 |
    |:---------|:-----|
    | AM, PM | 오전, 오후 시각 표시 |
    | A.M, P.M | 오전, 오후 시각 표시 |
    | HH, HH12 | 시간 표시 |
    | HH24 | 24시간으로 표현(0~23) |
    | MI | 분 표현 |
    | SS | 초 표현 |

    ```sql
    select to_char(sysdate, 'YYYY/MM/DD, HH24:MI:SS')
    from dual;
    ```
    
    ![](https://gekdev.github.io/docs/sql/function/example/to_char2.jpg)

3. 숫자 형식 모델

    | 구분      | 설명 |
    |:---------|:-----|
    | 0 | 자리수를 나타내며 자릿수가 맞지 않으면 0으로 채움 |
    | 9 | 자리수를 나타내며 자릿수가 맞지 않아도 채우지 않음 |
    | L | 각 지역별 통화 기호 표시 |
    | $ | 달러 기호 표시 |
    | . | 소숫점을 표시 |
    | , | 천 단위 자리 구분을 표시 |

    ```sql
	select ename, to_char(sal, 'L999,999')
    from emp;
    ```

    ![](https://gekdev.github.io/docs/sql/function/example/to_char1.jpg)

### to_date() 

**문자형을 날짜형으로 변환, 오라클에서 제공하는 함수**

&#9656; 날짜를 나타내는 문자열을 지정된 format에 따라 날짜 값으로 변환

&#9656; format이 생략되면 오라클의 기본 날짜 형식(YY/MM/DD)으로 인식함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**to_date('char', 'format')** 
</div>
```sql
select ename, hiredate
from emp
where hiredate = to_date(19810220, 'YYYYMMDD')
```

![](https://gekdev.github.io/docs/sql/function/example/to_date.jpg)
