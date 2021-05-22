---
layout: default
title: Group Function
parent: SQL
grand_parent: Database
nav_order: 6
---

# SQL Group Function
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Group Functions

### count()

**조회되는 데이터들의 총 건수** 

&#9656; row를 세서 출력하는 것

&#9656; 조건 상관없이 row 개수만을 출력하고 싶으면 * 사용

&#9656; 중복되는 값 상관없이 데이터만 있다면 갯수를 셈(null값 제외)

syntax
{: .label .mt2}
<div class="code-example" markdown="1">
**count(칼럼명)**
</div>
```sql
select count(*) from emp;
select count(sal) from emp; 
select count(job) from emp; -- 중복되는 값이 있어도 갯수를 셈
select count(comm) from emp; -- null 값 포함하지 않음
select count(sal), count(comm) from emp;
```

![](https://gekdev.github.io/docs/database/sql/example/count_func.jpg)

### sum()

**조회되는 데이터들을 총 합계** 

&#9656; 값이 숫자여야지 오류가 나지 않음

syntax
{: .label .mt2}
<div class="code-example" markdown="1">
**sum(칼럼명)**
</div>
```sql
select sum(ename) from emp; -- 에러
select sum(sal) from emp;
select count(ename), sum(sal), round(sum(sal)/count(ename),0) from emp;
```

![](https://gekdev.github.io/docs/database/sql/example/sum_func.jpg)

### avg()

**조회되는 데이터들을 평균**

&#9656; avg는 null값을 빼고 평균을 구함

syntax
{: .label .mt2}
<div class="code-example" markdown="1">
**avg(칼럼명)**
</div>
```sql
-- Q1) 평균급여 구하기
-- sum/count 사용한것과 동일하게 결과가 나옴
select round(avg(sal), 0) 평균급여
     , round(sum(sal) / count(ename), 0) 
  from emp;
  
-- Q2) Null값 포함/미포함 평균 구하기
-- avg는 null값을 빼고 평균을 구함
select count(*), sum(comm), avg(comm) from emp
union all
select count(*), sum(comm), round(avg(nvl(comm, 0)), 0) from emp;
```

![](https://gekdev.github.io/docs/database/sql/example/avg_func.jpg)

### max() & min()

**조회되는 데이터들중 최대/소값**

&#9656; 문자열은 a에 가까울수록 값이 낮다

syntax
{: .label .mt2}
<div class="code-example" markdown="1">
**max(칼럼명)**

**min(칼럼명)**
</div>
```sql
-- Q1) 최소급여, 최대급여 구하기
select min(sal), max(sal) from emp;

-- Q1) 가장 빠른 입사일, 가장 늦은 입사일 구하기
select min(hiredate), max(hiredate) from emp;
```

![](https://gekdev.github.io/docs/database/sql/example/min_max_func.jpg)

### stddev()

**조회되는 데이터들을 표준편차값**

syntax
{: .label .mt2}
<div class="code-example" markdown="1">
**stddev(칼럼명)**
</div>
```sql
-- Q1) 급여의 표준편차 값 구하기
select round(stddev(sal), 1) from emp;
```

![](https://gekdev.github.io/docs/database/sql/example/stu_func.jpg)

### variance()

**조회되는 데이터들을 분산값**

syntax
{: .label .mt2}
<div class="code-example" markdown="1">
**stddev(칼럼명)**
</div>
```sql
-- Q1) 급여의 표준편차 값 구하기
select round(variance(sal), 1) from emp;
```

![](https://gekdev.github.io/docs/database/sql/example/var_func.jpg)

	8. rollup()
	9. cube()
    
	10. groupingset()
	11. listagg()
	12. pivot() / unpivot() - 행을 열로, 열을 행으로 
	13. lag()
	14. lead()
    
	15. rank()
	16. dense_rank()
	
    17. sum() over()
	18. ration_to_report()
	
---

## group by

### group by

**그룹 함수의 결과를 조건에 따라 그룹화하기**

&#9656; select절에 사용된 **그룹함수 이외의 컬럼이나 표현식은 반드시 group by 절에 정의** 되어야 함

&#9656; group by 절에 사용된 컬럼이라도 select절에 사용되지 않아도 됨

&#9656; group by 절에는 반드시 컬럼명이 사용되어야 함 (alias는 사용 불가)

&#9656; group by절을 사용한 select문에 order by절로 정렬을 하기 위해서는 order by절은 group by절 뒤에 정의해야 한다

&#8594; (order by 절에서는 별칭도 정의가 가능)

syntax
{: .label .mt2}
<div class="code-example" markdown="1">
select .... from .... **group by ...** [order by ...];

&#9656; []은 생략가능, group by로 만들어진 그룹에 따라 순서를 정렬하는것
</div>
```sql
-- Q1) 부서별 급여합계
-- ver1) where 절
-- 데이터에 맞는 조건 하나씩(부서 하나의 급여합계)만 검색 가능하고, 
-- 부서별로 급여 합계를 보려면 union all로 합쳐야지 한꺼번에 출력되기 때문에 불편함
select 10 부서, sum(sal) 급여합계 from emp where deptno = 10 
union all
select 20, sum(sal) from emp where deptno = 20   
union all
select 30, sum(sal) from emp where deptno = 30;

-- ver2) sum() 그룹함수
-- group by를 사용하면서 부서별로 급여 합계를 쉽게 볼 수 있음
select deptno 부서, sum(sal) 부서별급여합계
  from emp
 group by deptno
 order by 부서;
```

![](https://gekdev.github.io/docs/database/sql/example/group_by1.jpg)

### having

**집계함수를 가지고 그룹결과를 조건별로 결과 구하기**

&#8594; 단일행 함수에서 사용했던 where조건과 동일

&#8594; 즉, 그룹화에서 조건을 주기위해서는 having절을 사용, where절에는 그룹화 되지 않은 행에서 단일 조건을 검색할 때 사용

&#8594; having절에는 집계함수를 가지고 조건을 비교할 때 사용되며 having절과 group by절과 함께 사용

&#8594; having절은 group by절없이 사용할 수 없고, order by 절보다 일찍 나옴

syntax
{: .label .mt2}
<div class="code-example" markdown="1">
select .... from .... group by .... **having ....** [order by ...];

&#9656; []은 생략가능, group by로 만들어진 그룹에 따라 순서를 정렬하는것
</div>
``` sql
-- Q1) EMP테이블에서 평균 급여가 1600보다 낮은 부서번호와 평균급여를 출력
select deptno
     , round(avg(nvl(sal, 0)), 2) 평균급여
  from emp
 group by deptno
having round(avg(nvl(sal, 0)), 2) < 1600.00;
```

![](https://gekdev.github.io/docs/database/sql/example/hav.jpg)

### Examples

Q1. 부서별로 사원수와 급여합계, 급여평균을 구하기

```sql
select deptno
     , count(ename)
	 , sum(nvl(sal, 0))
	 , round(avg(nvl(sal, 0)), 0)
  from emp
 group by deptno
 order by deptno;
```

![](https://gekdev.github.io/docs/database/sql/example/gr_ex1.jpg)

Q2. 업무별(JOB)로 인원수, 평균급여, 최고급여, 최소급여, 급여합계를 구하기

```sql
select job
     , count(*)
	 , round(avg(nvl(sal, 0)), 2) 평균급여
	 , max(sal) 최고급여
	 , min(sal) 최소급여
     , sum(sal) 급여합계
  from emp
 group by job;
```

![](https://gekdev.github.io/docs/database/sql/example/gr_ex1.jpg)

---

## 소계 및 총계구하기

### rollup()

**데이터의 소계, 총계를 그룹별로 구하기**

&#9656; rollup함수는 group by절과 같이 사용되면 group by절에 의해서 그룹 지어진 집합결과에 대해 좀더 상세한 결과를 반환

&#9656; group by rollup(deptno, job) -> M+1개의 그룹이 생김

&#9656; rollup에 있는 매개변수 순서에 따라서 결과값이 달라짐

syntax
{: .label .mt2}
<div class="code-example" markdown="1">
select .... from .... group by **rollup(컬럼명)** [order by ...];

&#9656; []은 생략가능
</div>

직급별 급여합계와 총합계를 구하기
{: .label mt-2}
```sql 
-- ver1) union all을 사용해서 총계를 따로 더해주는 방법
select *
  from 
(
	select job, sum(sal) from emp group by job
    union all
	select '총계', sum(sal) from emp
) table1
order by job; 

-- ver2) 상기예제를 rollup함수를 이용해서 총계를 구함
select job
	 , sum(sal)
  from emp
 group by rollup(job);
```

![](https://gekdev.github.io/docs/database/sql/example/roll_up_ex.jpg)

### Example

Q1. EMP테이블에서 부서별, 직업별, 평균급여, 사원수를 부서별 합계와 전체 총계를 같이 출력하며, 부서번호와 직업을 순서로 작성

| 부서별  |직업별     |평균급여      |사원수   | 
|:-------|:---------|:-----------|:--------|
| 부서    | 직업      | 평균급여     | 사원수  | 
| 부서    |         | 부서별 합계   | 부서별 사원합계 | 
|        |         | 전체 합계    | 총사원수 | 

1. union all

    방법1
    {: .label .mt-2}
    
    ```sql
    select *
    from(
        -- 부서, 직업, 평균급여, 사원수 출력
        select deptno, job, round(avg(sal), 1) 평균급여, count(*) 사원수 from emp group by deptno, job 
        union all
        -- 부서, 부서별 합계, 부서별 사원합계 출력
        select deptno, null, round(avg(sal), 1) 평균급여, count(*) 사원수 from emp group by deptno
        union all
        -- 전체 합계, 총 사원수 출력
        select null, null, round(avg(sal), 1) 평균급여, count(*) 사원수 from emp
    )
    order by deptno, job; -- 부서번호와 직업 정렬
    ```

    ![](https://gekdev.github.io/docs/database/sql/example/un_zero.jpg)

    방법2 : null값에 이름 주기
    {: .label .mt-2}
    
    ```sql
    select deptno --여기는 null 처리가 안됨
         , nvl(job, '부서합계') JOB
         , 평균급여
         , 사원수
      from (
        select deptno, job, round(avg(sal), 1) 평균급여, count(*) 사원수 from emp group by deptno, job
        union all
        select deptno, null, round(avg(sal), 1) 평균급여, count(*) 사원수 from emp group by deptno
        union all
        select null, null, round(avg(sal), 1) 평균급여, count(*) 사원수 from emp
    )
    order by deptno, job;
    ```

    ![](https://gekdev.github.io/docs/database/sql/example/un_one.jpg)

2. rollup()

    방법1
    {: .label .mt-2}

    ```sql
    select deptno
         , nvl(position, '-------------') position
         , 교수인원수
         , 합계
      from (
        select deptno, position, count(*) 교수인원수, sum(pay) 합계 from professor group by deptno, position
        union all
        select deptno, null, count(*) 교수인원수, sum(pay) 합계 from professor group by deptno
        union all
        select null, null, count(*) 교수인원수, sum(pay) 합계 from professor
    ) 
    order by deptno, position;
    ```
    
    ![](https://gekdev.github.io/docs/database/sql/example/rollup_1.jpg)

    방법2
    {: .label .mt-2}

    ```sql
    select deptno
         , nvl(job, '부서합계')
         , round(avg(sal), 1) 평균급여
         , count(*) 사원수 
      from emp
     group by deptno, rollup(job);
    ```
    
    ![](https://gekdev.github.io/docs/database/sql/example/rollup_2.jpg)
    
    방법3
    {: .label .mt-2}

    ```sql
     select deptno
          , nvl(job, '부서합계')
          , round(avg(sal), 1) 평균급여
          , count(*) 사원수 
      from emp
     group by job, rollup(deptno);
    ```
    
    ![](https://gekdev.github.io/docs/database/sql/example/rollup_3.jpg)

Q2. Professor 테이블에서 deptno, position별로 교수인원수, 급여합계 구하기

1. union all

    ```sql
    select deptno
         , nvl(position, '-------------') position
             , 교수인원수
             , 합계
      from (
        select deptno, position, count(*) 교수인원수, sum(pay) 합계 from professor group by deptno, position
        union all
        select deptno, null, count(*) 교수인원수, sum(pay) 합계 from professor group by deptno
        union all
        select null, null, count(*) 교수인원수, sum(pay) 합계 from professor
    ) 
    order by deptno, position;
    ```

    ![](https://gekdev.github.io/docs/database/sql/example/q2_union.jpg)

2. rollup()

    ```sql
    select deptno
         , nvl(position, '--------------------') position
         , count(*)
         , sum(pay)
      from professor
     group by rollup(deptno, position);
    ```

    ![](https://gekdev.github.io/docs/database/sql/example/q2_rol.jpg)

### cube()함수

### Example

Q1. EMP테이블에서 부서별, 직업별, 평균급여, 사원수를 부서별 합계와 전체 총계를 같이 출력하며, 부서번호와 직업을 순서로 작성

| 부서별  |직급별     |평균급여      |사원수   | 
|:-------|:---------|:-----------|:--------|
| 부서별  |         | 평균급여     | 사원수  | 
|        | 직급별   |     합계   |  사원수 | 
|        |         | 전체 합계    | 총사원수 | 

```sql 
 select deptno
	   , job
		 , round(avg(sal), 1) 평균급여
		 , count(*) 사원수 
  from emp
 group by cube(deptno, job);
```

![](https://gekdev.github.io/docs/database/sql/example/cube.jpg)

---

## 순위함수 

순위함수 사용시에는 order by절은 필수로 정의

### rank()

**순위를 부여하는 함수로서 동일순위처리가 가능(중복순위 1,2,2,4)**

컬럼명 안에 값이 없을 경우 에러가 나옴

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
1. 특정자료의 순위 : **rank(조건값) within group (order by 컬럼명[asc|desc])**

2. 전체자료의 순위 : **rank() over(order by 컬럼명[asc|desc])**

3. 그룹별 순위 : **rank() over(partition by 컬럼명 order by 컬럼명[asc|desc])**
</div>
```sql
-- 1) 특정조건의 순위
-- SMITH가 알파벳순으로 몇번째인지?
select ename from emp order by ename;
select rank('SMITH') within group(order by ename) from emp;
select rank('SMITH') within group(order by hiredate) from emp; -- 에러

-- 2) 전체순위
-- emp에서 사원들의 급여순위?
select empno, ename, sal
     , rank() over(order by sal) 급여오름차순
     , rank() over(order by sal desc) 급여내림차순
  from emp;

-- 3) 그룹별순위
-- 부서별 급여순위는?
select deptno, ename, sal
     , rank() over(partition by deptno order by sal)
  from emp;
```

### dense_rank()

**동일순서의 처리에 영향이 없다 (중복순위, 1,2,2,3)**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
select **dense_rank() over(order by 컬럼명)** 별칭 from 테이블;
</div>
```sql
select empno, ename, sal
	 , dense_rank() over(order by sal) 
  from emp;
```

### row_number() 

**특정순위의 일련번호를 제공하는 함수 동일순위처리 불가 (1,2,3,4,5)**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
select **row_number() over(order by 컬럼명)** 별칭 from 테이블;
</div>
```sql
select empno, ename, sal
	 , row_number() over(order by sal) "ROW_NUMBER"
  from emp;
```
  
![](https://gekdev.github.io/docs/database/sql/example/https://gekdev.github.io/docs/database/sql/example/row.jpg)