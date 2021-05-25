---
layout: default
title: Data Transfer Function
parent: Function
grand_parent: SQL / Oracle
nav_order: 4
---

# SQL Single Date Function
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Data Type Transfer Function

**형변환 함수, 데이터 타입을 변환해야 하는 경우 사용**

![](https://gekdev.github.io/docs/sql/function/example/changing.jpg)

### to_number()

**문자형을 숫자로 변환**

&#9656; 묵시적 형변환과 명시적 형변환 두가지가 있음
    
&#9656; 문자열이 포함되어 있으면 오류가 발생됨

```sql
-- 1. 묵시적 형변환(암묵적, 자동)
select 2 + '2' from dual; 
select '2' + 2 from dual;

-- 2. 명시적 형변환
select to_number('2') + 2 from dual; 

-- error
select '2a' + 2 from dual;
select 'A' + 2 from dual;
```

![](https://gekdev.github.io/docs/sql/function/example/to_num_error.jpg)

### to_char()

**날짜형이나 숫자를 문자로 변환**

&#9656; 형식에는 날짜, 시간, 숫자형식이 있음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**to_char(number / date, 'format')** 
</div>

날짜 형식(format) 모델
{: .label .label-purple .mt-2}

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

시간 형식(format) 모델
{: .label .label-purple .mt-2}

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

숫자 형식(format) 모델
{: .label .label-purple .mt-2}

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
