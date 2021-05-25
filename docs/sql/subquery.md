---
layout: default
title: Subquery
parent: SQL / Oracle
nav_order: 7
---

# SQL Subquery
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Subquery Basic

**다른 SELECT문의 질의에 삽입된 쿼리문**

&#9656; 메인쿼리 : 외부에 기술하는 쿼리, 서브쿼리 : 내부에 기술하는 쿼리

&#9656; 메인 쿼리에 사용할 값을 반환함, 서브쿼리에서 실행된 결과가 메인 쿼리에 전달되어 최종적인 결과를 출력

&#9656; 두번의 질의가 필요할 때 두 쿼리를 결합해 한 번의 질의로 원하는 결과를 얻어올 수 있음

&#9656; 서브쿼리의 결과값의 개수에 의해서 단일 행 서브 쿼리와 다중 행 서브 쿼리로 나뉨

&#9656; 서브쿼리는 괄호로 묶어야 하며 비교 조건의 오른쪽에 넣음

&#9656; 그룹 함수를 서브쿼리에 사용하는 경우에도 그룹함수가 단일 행을 결과값으로 구하기 때문에 단일 행 서브쿼리에 해당

&#9656; 단일 행 비교연산자 : >, =, <, >=, <=, <>

&#9656; 다중 행 비교연산자 : IN, ANY, SOME, ALL, EXISTS

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
SELECT select_list

FROM table

WHERE expr OPERATOR **(SELECT ...)**

&#9656; OPERATOR는 단일 행 비교연산자와 다중 행 비교연산자로 나뉨 (섞어서 사용할 수 없음)
</div>
```sql
-- SMITH와 동일한 부서에서 일하는 사람들의 이름과 부서번호 구하기
select ENAME, DEPTNO 
from emp 
WHERE DEPTNO = (select deptno from emp where ename = 'SMITH');
```

![](https://gekdev.github.io/docs/sql/example/smith.jpg)

### Example

Q1. 최소급여를 받는 사원의 이름, 담당업무, 급여 출력

```sql
select ename, job, sal
from emp 
where sal = (select min(sal) from emp);
```

![](https://gekdev.github.io/docs/sql/example/min_sal.jpg)

Q2. 부서별 최소 급여가 30번부서의 최소급여보다 큰 부서만 출력

```sql
select deptno, min(sal)
from emp
group by deptno
having min(sal) > (select min(sal) from emp where deptno = 30)
```

![](https://gekdev.github.io/docs/sql/example/hav_q2.jpg)

---

## Multiple Row Subquery

서브 쿼리에서 반환되는 결과가 하나 이상의 행일 때 사용

다중 행 서브쿼리는 반드시 다중 행 연산자와 함께 사용해야 함

| 종류 | 의미 |
|:----|:----|
| IN | 메인 쿼리의 비교조건(= 연산자로 비교할경우)이 서브쿼리의 결과중에서 하나라도 일치하면 참 | 
| ANY,SOME | 메인쿼리의 비교조건이 서브쿼리의 검색 결과와 하나 이상이 일치하면 참 |
| ALL | 메인 쿼리의 비교 조건이 서브 쿼리의 검색 결과와 모든 값이 일치하면 참 |
| EXIST | 메인쿼리의 비교조건이 서브 쿼리의 결과 중에서 만족하는 값이 하나라도 존재하면 참 |


### IN Operator

**메인 쿼리의 비교조건(= 연산자로 비교할경우)이 서브쿼리의 결과중에서 하나라도 일치하면 참**

&#9656; =ANY와 동일함

```sql
--부서별 최소 급여를 받는 사원의 사원번호와 이름을 출력
select empno, ename 
from emp
where sal in (select min(sal) from emp group by deptno);
```

![](https://gekdev.github.io/docs/sql/example/mul_in.jpg)

### ANY Operator

**메인쿼리의 비교조건이 서브쿼리의 검색 결과와 하나 이상이 일치하면 참**

서브쿼리가 반환하는 각각의 값과 비교함

<ANY : 최대값보다 작음, >ANY : 최소값보다 큼, =ANY : IN과동일

```sql
--직급이 SALESMAN이 아니면서 급여가 임의의 SALESMAN보다 낮은 사원을 출력
-- salesman의 최대급여 아래로 나옴
select empno, ename, job, sal
from emp
where sal < any (select sal from emp where job = 'SALESMAN')
and job <> 'SALESMAN'
```

![](https://gekdev.github.io/docs/sql/example/any.jpg)

### ALL Operator

**메인 쿼리의 비교 조건이 서브 쿼리의 검색 결과와 모든 값이 일치하면 참**

서브쿼리가 반환하는 모든 값과 비교

 &#62;ALL : 최대값보다 큼, <ALL : 최소값보다 작음

```sql
-- 직급이 SALESMAN이 아니면서 급여가 SALESMAN보다 낮은 사원을 출력
-- salesman의 최소급여 아래로 나옴
select empno, ename, job, sal
from emp
where sal < all (select sal from emp where job = 'SALESMAN')
and job <> 'SALESMAN'
```

![](https://gekdev.github.io/docs/sql/example/all33.jpg)

