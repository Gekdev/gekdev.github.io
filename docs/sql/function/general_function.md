---
layout: default
title: General Function
parent: Function
grand_parent: SQL / Oracle
nav_order: 3
---

# SQL Single General Function
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Single General Function

### Replace null Value

**테이블의 널값을 대체하는 함수**

&#9656; 컬럼명과 exprN은 반드시 데이터 타입이 일치해야 함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
* **nvl(컬럼명, expr0)** : **null을 0 또는 다른 값으로 변환**

* **nvl2(컬럼명, expr2, expr3)** : **컬럼명을 검사해 결과가 null이면 expr2반환, null이 아니면 expr3을 반환**

&#9656; exprN에는 날짜, 문자, 숫자형이 들어갈 수 있음
</div>
```sql
select ename
     , sal
     , comm
     , nvl(comm,0)
     , sal + comm
     , sal + nvl(comm, 0)
from emp;
```

![](nvl.jpg)

### nullif()

**표현식을 비교해서 널값을 반환하는 함수**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**nullif(expr1, expr2)** : **두 표현식을 비교하여 동일한 경우에는 NULL을 반환하고 동일하지 않으면 첫 번째 표현식을 반환**
</div>
```sql
select nullif('A','A'), nullif('A','B')
from dual;
```

![](nullif.jpg)

### coalesce()

**인수 중 null이 아닌 첫번 째 인수를 반환하는 함수**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**coalesce(expr1, expr2, ... , exprN) : 두 표현식을 비교하여 동일한 경우에는 NULL을 반환하고 동일하지 않으면 첫 번째 표현식을 반환**
</div>
```sql
select ename, sal, comm, coalesce(comm, sal, 0)
from emp
order by job;
```

![](coalesce.jpg)

### decode()

**switch case문과 같은 기능, sql문안에서 사용할 수 있도록 한 오라클고유함수**

&#9656; 조건에 따라 다양한 선택이 가능하도록 함

&#9656; 기본 결과가 명시되지 않았을 경우에는 NULL값을 반환

&#9656; decode(deptno, 101, decode())

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**decode(표현식

  , 조건1, 결과1

  , 조건2, 결과2

  , 조건3, 결과3

  , 기본결과n) as alias**
</div>
```sql
select deptno
     , name
     , decode(deptno, 101, '컴공'
                    , 102, '미디어 융합'
                    , 103, '소프트공학'
                    , '기타학과')
	from professor;
```

![](decode.jpg)

### case

**프로그램 언어의 if else와 같이 사용할 수 있음**

&#9656; decode대신 일반적으로 사용되는 문장(ISO 표준 규격에 더 잘맞음)

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**case expr(

  when 조건1 then 결과1

  when 조건2 then 결과2

  when 조건3 then 결과3
    
  else 결과n
  
  end [as 별칭]
</div>
```sql
```
--       case 조건 when 결과1 then 춝력1,
--                           [when .......]
--                            else 출력n                  
--       end



