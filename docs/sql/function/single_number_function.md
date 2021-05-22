---
layout: default
title: Single Number Function
parent: Function
grand_parent: SQL / Oracle
nav_order: 3
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

**주어진 숫자를 올림**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**ceil()** 
</div>
```sql

```

![](https://gekdev.github.io/docs/sql/function/example/ceil.jpg)

### round()

**주어진 숫자를 반올림**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**round(실수, 반올림위치)** 
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

**주어진 숫자를 내림**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**floor()** 
</div>
```sql
select 123
    , floor(123.99)
from dual;
```

![](https://gekdev.github.io/docs/sql/function/example/floor.jpg)

### trunc()

**주어진 숫자를 버림**

round()와 동일한데 다른 점은 무조건 버림처리

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**trunc(숫자, 잘릴위치)** 
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

**주어진 숫자를 나누기 후 나머지**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**mod()** 
</div>
```sql
select 121
    , mod(121, 10)
from dual;
```

![](https://gekdev.github.io/docs/sql/function/example/mod.jpg)

### power()

**주어진 숫자의 숫자의 승을 출력**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**power()** 
</div>
```sql
select power(2,3)
	, power(3,3) 
from dual;
```

![](https://gekdev.github.io/docs/sql/function/example/power.jpg)

### rownum()

**행번호를 출력해줌**

오라클에서만 사용하는 속성으로 모든 객체에 제공

전체열 즉, *와 같이 사용할 수 없음

```sql
select rownum, * from emp; --오류
select rownum, ename, hiredate from emp;
```

![](https://gekdev.github.io/docs/sql/function/example/rownum.jpg)
