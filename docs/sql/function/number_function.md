---
layout: default
title: Number Function
parent: Function
grand_parent: SQL / Oracle
nav_order: 2
---

# SQL Single Number Function
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Single Number Functions

### ceil()

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**ceil() : 주어진 숫자를 올림** 
</div>
```sql
select 123
    , ceil(123.55)
    , ceil(123.25)
from dual;
```

![](https://gekdev.github.io/docs/sql/function/example/ceil.jpg)

### round()

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**round(실수, 자릿수) : 실수를 특정 자리수에서 반올림** 
</div>
```sql
select round(987.654, 2)
    , round(987.654, 0)
    , round(987.654, -1)
    , round(987.654, -2)
from dual;
```

![](https://gekdev.github.io/docs/sql/function/example/round.jpg)

### floor()

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**floor(실수, 자릿수) : 실수를 특정 자리수에서 내림**

소숫점 기준 0으로 시작함

</div>
```sql
select 123
    , floor(123.99)
from dual;
```

![](https://gekdev.github.io/docs/sql/function/example/floor.jpg)

### trunc()

&#9656; round()와 동일한데 다른 점은 무조건 버림처리

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**trunc(숫자, 자릿수) : 실수를 특정 자리수에서 버림** 
</div>
```sql
select trunc(987.654, 2)
    , trunc(987.654, 0)
    , trunc(987.654, -1)
    , trunc(987.654, -2)
from dual;
```

![](https://gekdev.github.io/docs/sql/function/example/trunc.jpg)

### mod()

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**mod(실수, 자를숫자) : 실수를 자를숫자로 나눈 후 나머지값 반환** 
</div>
```sql
select 121
    , mod(121, 10)
from dual;
```

![](https://gekdev.github.io/docs/sql/function/example/mod.jpg)

### power()

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**power(실수, 승) : 실수의 승을 출력** 
</div>
```sql
select power(2,3)
	, power(3,3) 
from dual;
```

![](https://gekdev.github.io/docs/sql/function/example/power.jpg)

### rownum()

**행번호를 출력해줌**

&#9656; 오라클에서만 사용하는 속성으로 모든 객체에 제공

&#9656; 전체열 즉, *와 같이 사용할 수 없음

```sql
select rownum, * from emp; --오류
select rownum, ename, hiredate from emp;
```

![](https://gekdev.github.io/docs/sql/function/example/rownum.jpg)
