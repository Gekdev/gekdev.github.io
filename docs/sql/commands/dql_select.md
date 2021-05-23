---
layout: default
title: DQL Select
parent: Commands
grand_parent: SQL / Oracle
nav_order: 2
---

# DQL Commands Select 
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Select Statement Basic

### Select basic

**테이블에 저장된 데이터를 검색하기 위한 명령문**

&#9656; * = 에스테리스크

&#9656; 여러개의 절(clause)로 구성, 가독성을 위해 줄 구분과 들여쓰기를 함 

&#9656; 명령어는 대소문자를 구분하지 않음

&#9656; []안에 있는 절은 생략 가능함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
select [distinct] { * / column[alias]... }

from table

[where condition]

[group by groub_by_expression]

[having group_condition]

[order by column];
</div>
```sql
select * from emp; 
    -- emp 전체 테이블 조회
    
select ename, empno, job from emp;
    -- ename, empno, job 컬럼 조회
```

![](https://gekdev.github.io/docs/sql/commands/example/sel_bas.jpg)

| 절                  | 기능                                            |
|:--------------------|:-----------------------------------------------|
| SELECT 절           | 조회하고자 하는 칼럼명의 리스트를 나열               |
| DISTINCT 절         | 동일한 내용(데이터)를 한번씩만 출력하여 중복을 제거    |
| FROM 절             | 조회하고자 하는 테이블명의 리스트를 나열             |
| WHERE 절            | 조회하고자 하는 로우의 조건을 나열                  |
| GROUP BY 절         | 동일한 값을 갖는 롱들을 한 그룹으로 묶음             |
| HAVING 절           | 로우들의 그룹이 만족해야 하는 조건을 제시            |
| ORDER BY 절         | 로우들의 정렬 순서를 제시                          |

### Distinct clause

**동일한 내용을 한 번씩만 출력해 중복을 제거**

&#9656; 무조건 특정한 컬럼명보다 앞에 와야함

distinct 사용법
{: .label .mt-2}
```sql
select distinct deptno from emp order by deptno;
    --emp 테이블에서 deptno 중복을 제거한 값을 순서대로 나타냄

select distinct deptno from emp order by deptno desc;
```

![](https://gekdev.github.io/docs/sql/commands/example/distc_jpg)

### Expression

**'리터럴, 상수, 문자'의 표현식은 작은 따옴표로 정의해야 함**

&#9656; 큰따옴표 에러, 큰따옴표는 별칭을 지정할때만 사용

&#9656; 컬럼명은 소문자, 대문자 상관하지 않음, 큰따옴표로 정의할 경우에는 대문자 사용

표현식 사용법
{: .label .mt-2}
```sql
select '이름=', ename from emp; 
    -- 정상
    
select '이름=', ENAME from emp; 
    -- 정상
    
select "이름=", ename from emp; 
    -- 에러 : 큰따옴표 
    
select '이름=', "ENAME" from emp; 
    -- 정상
    
select '이름=', "ename" from emp; 
    -- 에러 : 컬럼명을 소문자 큰따옴표
```

![](https://gekdev.github.io/docs/sql/commands/example/ex_name.jpg)

### String 

문자열 사용할때는 주의해야 함, 작은 따옴표 안에 작은 따옴표 nesting 불가 (에러)

single quotation
{: .label .mt-2}
```sql
select '한"글', ename from emp; 
    -- 쌍 따옴표는 가능

select '''', ename from emp;
    -- 가능, 두번 동시에 사용해야 함
    
select '한'글', ename from emp; 
    -- 에러    
```

![](https://gekdev.github.io/docs/sql/commands/example/smol_quot.jpg)

### Alias

**별칭, 해당객체 또는 컬럼명을 다른 이름으로 정의**

&#9656; as는 생략가능

&#9656; 별칭이 컬럼명이 되고 그냥 적거나 쌍따옴표로 적어야 함

alias 사용법
{: .label .mt-2}
```sql
--      값       이름
select '이름=' 한글, ename 사원이름 from emp; 
    -- 열이름 부여하기

select '이름=' as "한글", ename as "사원이름" from emp; 
    
select '이름=' as 한글, ename 사원이름 from emp;
```

### Arithmetic Operators

**+ - * /**

**칼럼 값에 수학에서 사용하는 산술 연산자를 적용해 계산된 결과 값을 출력할 수 있음**

&#9656; 숫자 또는 날짜 형태의 데이터 타입에만 사용이 가능

&#9656; 우선순위는 수학과 동일, 같은 우선순위일 경우 왼쪽에서 오른쪽, 우선순위 변경시 () 사용

```sql
select sal
    , sal +300
    , sal -300
    , sal *3
    , sal /3
 from emp;
```
![](https://gekdev.github.io/docs/sql/commands/example/arith.jpg)

### concat(),||

**컬럼 및 문자열 연결**

```sql
select ename || deptno from emp;
    -- 연결 기본

select ename || '(' || deptno || ')' from emp; 
    -- 보기쉽게 연결됨
    
select ename || '(' || deptno || ')' as "사원명(부서)" from emp; 
    -- 보기좋게 연결됨 (컬럼명이 별칭으로 됨)

select ename || '(' || deptno || ')' as 사원명(부서) from emp; 
    -- ()는 표현식, 열이름으로 인식하기 때문에 문자로 사용하려면 큰따옴표로 감싸야 함
````

### Searching Other Table

**더 높은 사용자 권한이 있는 사용자가 하위 사용자의 테이블을 조회할 때 사용**

```sql
-- 사용자의 접근 권한에 따라서 조회를 할 수 있음
select * from hr.employees; 
select * from scott.emp; --hr 사용자에서는 접근할 수 없음
```

### DUAL table

**결과를 출력하기 위해 제공되는 테이블로 오라클에서 자동생성**

&#9656; varchar2(1)으로 정의된 하나의 DUMMY 칼럼으로 구성되어 있고 데이터는 X

&#9656; 계산이나 함수를 실행하고 나서 결과값을 한번 표시하고 싶을 때 사용

```sql
select * from dual;
```

![](https://gekdev.github.io/docs/sql/commands/example/dual.jpg)

---

## Where Clause

**테이블에 저장된 데이터 중 원하는 데이터만 선택적으로 추출하기 위해 사용**

&#9656; 문자나 날짜 타입의 상수값은 반드시 작은 따옴표('')로 묶어 표현

&#9656; 영문자 상수값은 대소문자를 구분함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
select ... from ... **where condition**

&#9656; **condition에는 컬럼명, 연산자, 비교대상이 되는 상수값(숫자, 문자, 날짜)로 구성**
</div>

### Comparison Operator

**숫자, 문자, 날짜의 크기나 순서를 비용하기 위해 사용**

&#9656; 날짜 문자열을 비교하기 위해서는 문자상수와 마찬가지로 작은 따옴표로 묶어줘야 함

|연산자  | 의미                       |
|:------|:---------------------------|
|=      | 비교대상과 같은 조건을 검색    |
|!=, <> | 같지 않다                   |
|>      | 크다                       |
|>=     | 크거나 같다                 |
|<      | 작다                       |
|<=     | 작거나 같다                 |

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
column_name **comparison operator** data
</div>
```sql
select * from emp
where hiredate <= '1981.06.09'
```

![](https://gekdev.github.io/docs/sql/commands/example/comp.jpg)

#### example

↓ 기본 연습

```sql
-- Q1. 사원번호가 7900인 자료만 조회하기
select * from emp where empno = 7900;

-- Q2. 급여(sal)가 900보다 작은 사원만 출력
select * from emp where sal < 900;

-- Q3. 이름이 smith인 사원만 출력
select * from emp where ename = 'SMITH'; 
    --"와 공백은 같은것, '만 문자열로 나타남, 리터럴 값은 소문자 대문자 구별함

-- Q4. 입사일(hiredate) 1980-12-17인 사원만 출력
select * from emp where hiredate = '1980-12-17'; 
    -- 형변환(암묵)되어서 date타입을 비교하게됨

select * from emp where hiredate = '19801217'; 

select * from emp where hiredate = '1980-dec-17'; 	

select * from emp where hiredate = '1980-DEC-17'; 	

select * from emp where hiredate = '1980.12.17'; 	

select * from emp where hiredate = '80/12/17'; 
    -- DB환경설정때문에 error	

select * from emp where hiredate = '1980.80.17'; 	
    -- 80월이 시스템으로 없기때문에 error

select * from emp where hiredate = '1980.10.40'; 	
    -- 40일이 시스템으로 없기때문에 error

-- Q5. 기본 연산자를 이용해서 현재 급여를 인상
-- 인상전급여, 인상후급여 = 인상전급여의 10% 인상
select 인상전급여, 인상후 급여 from emp;
select sal 인상전급여 , sal*1.1 인상후급여 from emp;
select sal 인상전급여 , (sal*1.1 + 100)/2 인상후급여 from emp; --db에 전혀 영향이 안감, 조회만 하는것(select)

-- Q6. 급여가 4000보다 크거나 같은 사원만 출력
select * from emp where sal >= 4000;
select ename,sal from emp where 4000 <= sal;

-- Q7. 사원명이 'W'보다 크거나 같은 사원만 출력
select * from emp where ename >= 'W';

-- Q8. 급여가 2000보다 크면서 3000보다 작거나 같은 사원만 출력
select * from emp where sal between 2000 and 3000;
select * from emp where sal > 2000 and sal <= 3000;
```

↓ 연습문제

```sql
-- ex01) 급여가 1000보다 작은 사원만 출력하기(ename/sal/hiredate 만 출력)
select ename, sal, hiredate from emp where 1000 > sal

-- ex02) 부서(dept)테이블에서 부서번호와, 부서명을 별칭으로 한 sql문을 작성
select * from dept
select deptno as 부서번호, dname as 부서명 from dept

-- ex03) 사원테이블에서 직급만 출력하는데 중복되지 않게 출력하는 sql문
select distinct job from emp

-- ex04) 급여가 800인 사원만 조회
select * from emp where 800 = sal
select * from emp where '800' = sal --내부적으로 변환됨, 위보다 실행속도가 느리다

-- ex05) 사원명이 BLAKE인 사원만 출력
select * from emp where 'BLAKE' = ename

-- ex06) 사원이름 JAMES-MATIN사이의 사원을 사원번호, 사원명, 급여를 출력
--  and betweem 두가지 형태로 작성
select * from emp;
select * from emp where ename >= 'JAMES' and ename <= 'MATIN'
select * from emp where ename between 'JAMES' and 'MATIN'	--실행속도가 더 빠름
```

### Logical Operator

**조건을 여러 개 조합해서 결과를 얻어야 할 경우에 조건을 연결해 주는 역할**

|연산자  | 의미                                          |
|:------|:---------------------------------------------|
|AND    | 두가지 이상의 조건 모두 만족해야만 검색            |
|OR     | 두가지 이상의 조건 중에서 한가지만 만족해도 검색 가능|
|NOT    | 조건에 만족하지 못하는 것만 검색                  |

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**not** column_name ... data **and / or** column_name ... data 
</div>
```sql
-- 1. and 연산자 사용
select * from emp where deptno = 10 and sal > 1000;

-- 2. or 연산자 사용
select * from emp where deptno = 10 or deptno = 20;

-- 3. not 연산자 사용
select * from emp where not deptno = 10;
```

![](https://gekdev.github.io/docs/sql/commands/example/and.jpg)

#### example

* 연습문제

    ```sql
    -- ex01) 입사일이 1982-01-01 이후이면서 급여가 3000보다 크거나 같은 사원목록
    select * from emp where hiredate > '1982-01-01' and sal >=3000;
    
    -- ex02) 입사일이 1982-01-01 이후이거나 급여가 3000보다 크거나 같은 사원목록
    select * from emp where hiredate > '1982-01-01' or sal >=3000;
    
    -- ex03) 사원이름은 S로 시작되면서 급여가 800인 사원
    select * from emp where ename like 'S%' and sal = 800;
    
    -- ex04) 급여가 1000보다 크면서 (comm이 1000보다 작거나 comm이 null) 인사원
    select * from emp where (comm <1000 or comm is null) and sal > 1000;
    ```
    
### between a and b 

**특정 칼럼의 데이터 값이 하한값과 상한값 사이에 포함되는 로우를 검색하기 위한 연산자**

&#9656; 비교연산자와 논리연산자를 합친것과 같음

&#9656; 날짜나 문자 상수에 사용할 경우에는 작은 따옴표로 묶어줘야 함

SYNTAX
{: .label .mt-2}
<div class="code-example" markdown="1">
column_name **between A and B**
</div>
```sql
select * from emp
where deptno between 20 and 30;
    -- and 연산자와 비교연산자를 사용한것과 같음 

select * from emp
where deptno not between 20 and 25; 
    -- or 연산자와 비교연산자 사용한것과 같음
```

![](https://gekdev.github.io/docs/sql/commands/example/between.jpg)

### in(a,b,c)

**특정 칼럼의 값이 A,B,C중에 하나라도 일치하면 참이 되는 연산자**

&#9656; or 연산자를 사용한것과 동일함

&#9656; 앞에 not을 붙이면 <>, != 연산자를 사용한것과 동일함

SYNTAX
{: .label .mt-2}
<div class="code-example" markdown="1">
column_name **in(A,B,C)**
</div>
```sql
--1. emp에서 부서번호가 10, 20인 사원만 조회
select ename, sal, deptno
from emp where deptno in(10,20)

select ename, sal, deptno
from emp where deptno = 10 or deptno = 20; 
    -- 위와 같은 방법이지만 코드가 길어지기 때문에 안좋음
	
select ename, sal, deptno
	from emp
	where deptno in (10,20)
	order by deptno;
	
select ename, deptno, sal
	from emp
	where deptno in (10,20)
	order by 1; -- 숫자는 열 번호 순서를 고름
	
select ename, deptno, sal
	from emp
	where deptno in (10,20)
	order by 2, 3 asc; --먼저 정렬해야 하는걸 먼저 정렬함
	
select deptno, ename, sal
	from emp
	where deptno in (10,20)
	order by deptno, sal desc, 2; 
```

![](https://gekdev.github.io/docs/sql/commands/example/in.jpg)

### Like Operator

**칼럼에 저장된 문자 상수 중 like연산자에서 지정한 문자 패턴과 부분적으로 일치하면 참이 되는 연산자**

&#9656; 데이터의 일부만 일치하더라도 조회가 가능하도록 하기 위해서 사용

&#9656; pattern에는 두가지가 있음

|연산자  | 의미                                              |
|:------|:-------------------------------------------------|
| %     | 문자가 없거나 하나 이상의 문자가 어떤 값이 와도 상관없음 |
| _     | 하나의 문자가 어떤 값이 와도 상관없음(_의 갯수만큼 따짐) |

SYNTAX
{: .label .mt-2}
<div class="code-example" markdown="1">
column_name **like pattern**
</div>
```sql
select * from emp where ename like 'A%';
select * from emp where ename between 'A' and 'AZ';

--이름이 N으로 끝나는 사원
select * from emp where ename like '%N';

--이름에 A를 포함하는 사원
select * from emp where ename like '%A%';

--sal이 50으로 끝나는 사원만 출력
select * from emp where SAL like '%50';

--입사일이 1980년대 입사한 사람
select * from emp where HIREDATE like '198%';

--입사월이 12월에 입사한 사람
select empno, ename, sal, hiredate from emp where HIREDATE like '_____12%';
select empno, ename, sal, hiredate from emp where HIREDATE like '____-12%';
```

![](https://gekdev.github.io/docs/sql/commands/example/like.jpg)

### is null / is not null

**is null 연산자는 칼럼 값 중에서 null을 포함하는 로우를 검색하기 위해 사용하는 연산자**

&#9656; null이 저장되어 있는 경우에는 = 연산자로 판단할 수 없음

&#9656; is not null은 정의가 반대

SYNTAX
{: .label .mt-2}
<div class="code-example" markdown="1">
column_name **is null / is not null**
</div>
```sql
select * from emp where comm is null;
    -- comm이 null인 값 검색
    
select * from emp where comm is not null;
    -- comm이 null이 아닌 값 검색
```
 
![](https://gekdev.github.io/docs/sql/commands/example/isnull.jpg)

---

## Order by Clause

**특정 칼럼을 기준으로 순서대로 나열할 때 사용**

&#9656; 등수정하기와 같음, ~부터, 기준으로, ~순으로라는 말이 나오면 order by한것

&#9656; 여러개의 칼럼값을 지정할 수 있음, 컴마(,)로 구분하고 먼저 지정한 순서대로 나열

&#9656; asc 오름차순, desc 내림차순

&#9656; 숫자 데이터가 아닌 문자 데이터로 지정하면 알파벳 순서대로 나옴(a,b,c... 오름차순)

&#9656; 날짜 데이터로 지정하면 과거가 가장 먼저 나옴

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
select 1,2,3... from ... where ... **order by column_name(1,2,3...) sorting**

&#9656; column_name 여러개 설정 가능, 숫자로 설정하면 표현되는 컬럼을 기준으로 순서를 셈 
</div>
```sql
select distinct deptno from emp order by deptno;

select distinct deptno from emp order by deptno asc; 
	-- default, 오름차순
	
select distinct deptno from emp order by deptno desc;
	-- 내림차순
    
select deptno, ename from emp order by deptno desc, ename asc;
```

![](https://gekdev.github.io/docs/sql/commands/example/desc.jpg)

![](https://gekdev.github.io/docs/sql/commands/example/orderby.jpg)

---

## Group By Clause

**동일한 값을 갖는 로우들을 한 그룹으로 묶음**

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
