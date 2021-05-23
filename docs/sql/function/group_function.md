---
layout: default
title: Group Function
parent: Function
grand_parent: SQL / Oracle
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

그룹함수는 두번 까지 중첩해서 사용 가능

### count()

&#9656; row를 세서 출력하는 것

&#9656; 조건 상관없이 row 개수만을 출력하고 싶으면 * 사용

&#9656; 중복되는 값 상관없이 데이터만 있다면 갯수를 셈(null값 제외)

syntax
{: .label .mt2}
<div class="code-example" markdown="1">
**count(칼럼명)** : **조회되는 데이터들의 총 건수** 
</div>
```sql
select count(*) from emp;
select count(sal) from emp; 
select count(job) from emp; -- 중복되는 값이 있어도 갯수를 셈
select count(comm) from emp; -- null 값 포함하지 않음
select count(sal), count(comm) from emp;
```

![](https://gekdev.github.io/docs/sql/function/example/count_func.jpg)

### sum()

&#9656; 값이 숫자여야지 오류가 나지 않음

syntax
{: .label .mt2}
<div class="code-example" markdown="1">
**sum(칼럼명)** : **조회되는 데이터들을 총 합계** 
</div>
```sql
select sum(ename) from emp; -- 에러
select sum(sal) from emp;
select count(ename), sum(sal), round(sum(sal)/count(ename),0) from emp;
```

![](https://gekdev.github.io/docs/sql/function/example/sum_func.jpg)

### avg()

&#9656; avg는 null값을 빼고 평균을 구함

syntax
{: .label .mt2}
<div class="code-example" markdown="1">
**avg(칼럼명)** : 조회되는 데이터들을 평균
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

![](https://gekdev.github.io/docs/sql/function/example/avg_func.jpg)

### max() & min()

&#9656; 문자열은 a에 가까울수록 값이 낮다

syntax
{: .label .mt2}
<div class="code-example" markdown="1">
**max(칼럼명) : 조회되는 데이터들중 최대값**

**min(칼럼명) : 조회되는 데이터들중 최소값**
</div>
```sql
-- Q1) 최소급여, 최대급여 구하기
select min(sal), max(sal) from emp;

-- Q1) 가장 빠른 입사일, 가장 늦은 입사일 구하기
select min(hiredate), max(hiredate) from emp;
```

![](https://gekdev.github.io/docs/sql/function/example/min_max_func.jpg)

### stddev()

syntax
{: .label .mt2}
<div class="code-example" markdown="1">
**stddev(칼럼명) : 조회되는 데이터들을 표준편차값**
</div>
```sql
-- Q1) 급여의 표준편차 값 구하기
select round(stddev(sal), 1) from emp;
```

![](https://gekdev.github.io/docs/sql/function/example/stu_func.jpg)

### variance()

syntax
{: .label .mt2}
<div class="code-example" markdown="1">
**stddev(칼럼명) : 조회되는 데이터들을 분산값**
</div>
```sql
-- Q1) 급여의 표준편차 값 구하기
select round(variance(sal), 1) from emp;
```

![](https://gekdev.github.io/docs/sql/function/example/var_func.jpg)
	
---

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

![](https://gekdev.github.io/docs/sql/function/example/gr_ex1.jpg)

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

![](https://gekdev.github.io/docs/sql/function/example/gr_ex1.jpg)

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

![](https://gekdev.github.io/docs/sql/function/example/roll_up_ex.jpg)

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

    ![](https://gekdev.github.io/docs/sql/function/example/un_zero.jpg)

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

    ![](https://gekdev.github.io/docs/sql/function/example/un_one.jpg)

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
    
    ![](https://gekdev.github.io/docs/sql/function/example/rollup_1.jpg)

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
    
    ![](https://gekdev.github.io/docs/sql/function/example/rollup_2.jpg)
    
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
    
    ![](https://gekdev.github.io/docs/sql/function/example/rollup_3.jpg)

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

    ![](https://gekdev.github.io/docs/sql/function/example/q2_union.jpg)

2. rollup()

    ```sql
    select deptno
         , nvl(position, '--------------------') position
         , count(*)
         , sum(pay)
      from professor
     group by rollup(deptno, position);
    ```

    ![](https://gekdev.github.io/docs/sql/function/example/q2_rol.jpg)

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

![](https://gekdev.github.io/docs/sql/function/example/cube.jpg)

---

## Rank Function

**순위함수 사용시에는 order by절은 필수로 정의**

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

![](https://gekdev.github.io/docs/sql/function/example/rank.jpg)

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

![](https://gekdev.github.io/docs/sql/function/example/dense.jpg)

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
  
![](https://gekdev.github.io/docs/sql/function/example/row.jpg)

---

## Other Functions

### sum() over

**누계를 구하는 함수**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
... **sum(컬럼) over (order by 컬럼(기준열))**
</div>
```sql
select p_total, p_qty,
    sum(p_total) over(order by p_total)
from panmae;
```

![](https://gekdev.github.io/docs/sql/function/example/sumover.jpg)  

Q1. 판매테이블에서 1000번대리점의 판매누계 구하기 

```sql
select p_date, p_code, p_qty, p_total
		 , sum(p_total) over(order by p_total) 판매누계
  from panmae
 where p_store = 1000;
```

![](https://gekdev.github.io/docs/sql/function/example/q1_example.jpg)

Q1-2. 상기 예제를 기준으로 제품 코드별 누계구하기, partition by(제품 코드)를 사용

```sql
select p_date, p_code, p_qty, p_total
     , sum(p_total) over(partition by p_code order by p_date)
  from panmae;
```

![](https://gekdev.github.io/docs/sql/function/example/q1_example2.jpg)

Q1-3. 상기 예제를 기준으로 제품 코드/대리점별 누계구하기

```sql
select p_date, p_code, p_store, p_qty, p_total
     , sum(p_total) over(partition by p_code, p_store order by p_date)
  from panmae;
```

![](https://gekdev.github.io/docs/sql/function/example/q1_example3.jpg)

### ratio_to_report()

**비율을 구하는 함수**

```sql
--판매비율
select p_code
    , sum(p_qty) over() tot_qty
    , sum(p_total) over() tot_amt
    , p_store
    , p_total
    , round(p_total / sum(p_total) over(),2)
    , round(p_total / (select sum(p_total) from panmae), 2) --두번 읽어야 해서 별로 안좋음
    , round(ratio_to_report(sum(p_qty)) over() * 100,2) "수량(%)"
    , round(ratio_to_report(sum(p_total)) over() * 100,2) "금액(%)"
from panmae
group by p_code, p_store, p_qty, p_total;
```

![](https://gekdev.github.io/docs/sql/function/example/ratio.jpg)


	10. groupingset()
	11. listagg()
	12. pivot() / unpivot() - 행을 열로, 열을 행으로 
	13. lag()
	14. lead()

---

## Example

Q1. emp 테이블을 사용하여 사원 중에서 급여(sal)와 보너스(comm)를 합친 금액이 가장 많은 경우와 가장 적은 경우 , 평균 금액을 구하세요. 단 보너스가 없을 경우는 보너스를 0 으로 계산하고 출력 금액은 모두 소수점 첫째 자리까지만 나오게 하세요

```sql
select round(max(sal+nvl(comm,0)),1)
		 , round(min(sal+nvl(comm,0)),1)
		 , round(avg(sal+nvl(comm,0)),1)
from emp;
```

![](https://gekdev.github.io/docs/sql/function/example/gr_01.jpg)

Q2. student 테이블의 birthday 컬럼을 참조해서 월별로 생일자수를 출력하세요

-- TOTAL, JAN, ...,  5 DEC

-- 20EA   3EA ....

```sql
select count(*) TOTAL
     , count(case when substr(birthday, 6, 2) ='01' then 1 END) JAN
     , count(case when substr(birthday, 6, 2) ='02' then 1 END) FEB
     , count(case when substr(birthday, 6, 2) ='03' then 1 END) MAR
     , count(case when substr(birthday, 6, 2) ='04' then 1 END) APR
     , count(case when substr(birthday, 6, 2) ='05' then 1 END) MAY
     , count(case when substr(birthday, 6, 2) ='06' then 1 END) JUN
     , count(case when substr(birthday, 6, 2) ='07' then 1 END) JUL
     , count(case when substr(birthday, 6, 2) ='08' then 1 END) AUG
     , count(case when substr(birthday, 6, 2) ='09' then 1 END) SEP
     , count(case when substr(birthday, 6, 2) ='10' then 1 END) OCT
     , count(case when substr(birthday, 6, 2) ='11' then 1 END) NOV
     , count(case when substr(birthday, 6, 2) ='12' then 1 END) DEC
from student;
```

![](https://gekdev.github.io/docs/sql/function/example/gr_02.jpg)

Q3. Student 테이블의 tel 컬럼을 참고하여 아래와 같이 지역별 인원수를 출력하세요.

단, 02-SEOUL, 031-GYEONGGI, 051-BUSAN, 052-ULSAN, 053-DAEGU, 055-GYEONGNAM 으로 출력하세요

```sql
select count(*) TOTAL
     , count(case when substr(tel,1,instr(tel,')')-1) = '02' then 1 END) "02-SEOUL"
     , count(case when substr(tel,1,instr(tel,')')-1) = '031' then 1 END) "31-GYEONGGI"
     , count(case when substr(tel,1,instr(tel,')')-1) = '051' then 1 END) "051-BUSAN"
     , count(case when substr(tel,1,instr(tel,')')-1) = '052' then 1 END) "052-ULSAN"
     , count(case when substr(tel,1,instr(tel,')')-1) = '053' then 1 END) "053-DAEGU"
     , count(case when substr(tel,1,instr(tel,')')-1) = '055' then 1 END) "055-YEONGNAM"
from student;
```

![](https://gekdev.github.io/docs/sql/function/example/gr_03.jpg)

Q4. emp 테이블을 사용하여 직원들의 급여와 전체 급여의 누적 급여금액을 출력, 단 급여를 오름차순으로 정렬해서 출력하세요.

-- sum() over()

```sql
select sal, sum(sal) over(order by sal) "누적 급여금액" from emp;
```

![](https://gekdev.github.io/docs/sql/function/example/gr_04.jpg)

Q5. student 테이블의 Tel 컬럼을 사용하여 아래와 같이 지역별 인원수와 전체대비 차지하는 비율을 출력하세요.

(단, 02-SEOUL, 031-GYEONGGI, 051-BUSAN, 052-ULSAN, 053-DAEGU,055-GYEONGNAM)

```sql
select count(*) TOTAL
     , count(case when substr(tel,1,instr(tel,')')-1) ='02' then 1 END) "02-SEOUL"
     , count(case when substr(tel,1,instr(tel,')')-1) ='031' then 1 END) "031-GYEONGGI"
     , count(case when substr(tel,1,instr(tel,')')-1) ='051' then 1 END) "051-BUSAN"
     , count(case when substr(tel,1,instr(tel,')')-1) ='052' then 1 END) "052-ULSAN"
     , count(case when substr(tel,1,instr(tel,')')-1) ='053' then 1 END) "053-DAEGU"
     , count(case when substr(tel,1,instr(tel,')')-1) ='055' then 1 END) "055-GYEONGNAM"
     , round(count(case when substr(tel,1,instr(tel,')')-1) ='02' then 1 END) / count(*) * 100, 2)  "서울비율(%)"
     , round(count(case when substr(tel,1,instr(tel,')')-1) ='031' then 1 END) / count(*) * 100, 2) "경기비율(%)"
     , round(count(case when substr(tel,1,instr(tel,')')-1) ='051' then 1 END) / count(*) * 100, 2) "부산비율(%)"
     , round(count(case when substr(tel,1,instr(tel,')')-1) ='052' then 1 END) / count(*) * 100, 2) "울산비율(%)"
     , round(count(case when substr(tel,1,instr(tel,')')-1) ='053' then 1 END) / count(*) * 100, 2) "대구비율(%)"
     , round(count(case when substr(tel,1,instr(tel,')')-1) ='055' then 1 END) / count(*) * 100, 2) "경남비율(%)"
from student;
```

![](https://gekdev.github.io/docs/sql/function/example/gr_06.jpg)

Q6. emp 테이블을 사용하여 부서별로 급여 누적 합계가 나오도록 출력하세요. ( 단 부서번호로 오름차순 출력하세요. )

```sql
select deptno, ename, sal,
    sum(sal) over(partition by deptno) 급여누계
from emp;
```

![](https://gekdev.github.io/docs/sql/function/example/gr_07.jpg)

Q8. emp 테이블을 사용하여 각 사원의 급여액이 전체 직원 급여총액에서 몇 %의 비율을 차지하는지 출력하세요. 단 급여 비중이 높은 사람이 먼저 출력되도록 하세요

```sql
select ename, sal
		 , round(ratio_to_report(sal) over() * 100,2) "%비중"
from emp;
```

![](https://gekdev.github.io/docs/sql/function/example/gr_08.jpg)

Q8. emp 테이블을 조회하여 각 직원들의 급여가 해당 부서 합계금액에서 몇 %의 비중을 차지하는지를 출력하세요. 단 부서번호를 기준으로 오름차순으로 출력하세요.

```sql
select deptno, ename, sal 
     , sum(sal) over(partition by deptno)
     , round(ratio_to_report(sal) over (partition by deptno) * 100,2)
from emp;
```

![](https://gekdev.github.io/docs/sql/function/example/gr_09.jpg)
















