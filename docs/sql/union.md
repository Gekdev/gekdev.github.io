---
layout: default
title: Union
parent: SQL / Oracle
nav_order: 6
---

# SQL UNION
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## UNION Operator

**집합연산자의 사용조건**

1. 두집합의 select절에 오는 컬럼의 갯수가 동일해야 함

2. 두집합의 select절에 오는 컬럼의 데이터형이 동일 해야함

3. 두집합의 컬럼명은 달라도 상관없음. 제일 처음에 위치한 쿼리문의 컬럼명이 집합결과의 컬럼명이 됨
  
### union 

**두 집합의 결과를 합쳐서 출력, 중복값은 제거, 정렬**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
select ...

**union**

select ...
</div>

### union all

**두 집합의 결과를 합쳐서 출력, 중복값을 제거안하고, 정렬(X)**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
select ...

**union all**

select ...
</div>
```sql
-- 1. union/union all
select count(*) from student; -- 20 

select studno, name, deptno1 from student
union all
select studno, name, deptno1 from student; --40건 나옴(중복제거 x)

select studno, name, deptno1 from student -- 20건
union
select studno, name, deptno1 from student;

select studno, name, deptno1 from student where deptno1 = 101; -- 4개
select studno, name, deptno1 from student where deptno1 = 201; -- 6개
select studno, name, deptno1 from student where deptno1 = 301; -- 2개

select studno, name, deptno1 from student where deptno1 = 101 -- 12개
union all
select studno, name, deptno1 from student where deptno1 = 201
union all -- 여러번 나와도 상관없음
select studno, name, deptno1 from student where deptno1 = 301;

select studno, name from student where deptno1 = 101 --중복 제거되어서 5개
union
select studno, name from student where deptno2 = 201;

select studno, name from student where deptno1 = 101 -- 중복 제거 x 6개
union all
select studno, name from student where deptno2 = 201;
```

![](https://gekdev.github.io/docs/sql/commands/example/unionall.jpg)

### intersect

**두 집합의 교집합을 출력, 정렬**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
select ...

**intersect**

select ...
</div>
```sql
select studno, name from student where deptno1 = 101
intersect
select studno, name from student where deptno2 = 201;
```

![](https://gekdev.github.io/docs/sql/commands/example/intersect.jpg)

### minus

**두 집합의 차집합을 출력, 정렬(쿼리순서가 중요)**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
select ...

**minus**

select ...
</div>
```sql
select studno, name from student where deptno1 = 101
minus
select studno, name from student where deptno2 = 201;

select studno, name from student where deptno2 = 201;
minus
select studno, name from student where deptno1 = 101
```

![](https://gekdev.github.io/docs/sql/commands/example/minus.jpg)
