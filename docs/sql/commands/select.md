---
layout: default
title: Select
parent: Commands
grand_parent: SQL / Oracle
nav_order: 1
---

# Commands Select
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Select Statement Basic

### select basic

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

| 절                  | 기능                                            |
|:--------------------|:-----------------------------------------------|
| SELECT 절           | 조회하고자 하는 칼럼명의 리스트를 나열               |
| DISTINCT 절         | 동일한 내용(데이터)를 한번씩만 출력하여 중복을 제거    |
| FROM 절             | 조회하고자 하는 테이블명의 리스트를 나열             |
| WHERE 절            | 조회하고자 하는 로우의 조건을 나열                  |
| GROUP BY 절         | 동일한 값을 갖는 롱들을 한 그룹으로 묶음             |
| HAVING 절           | 로우들의 그룹이 만족해야 하는 조건을 제시            |
| ORDER BY 절         | 로우들의 정렬 순서를 제시                          |

테이블 기본 조회법
{: .label .mt-2}
```sql
select * from emp; 
    -- emp 전체 테이블 조회
    
select ename, empno, job from emp;
    -- ename, empno, job 컬럼 조회
```

![](https://gekdev.github.io/docs/sql/commands/example/sel_bas.jpg)

### distinct 절

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

### Comparison operator

**숫자, 문자, 날짜의 크기나 순서를 비용하기 위해 사용**

&#9656; 날짜 문자열을 비교하기 위해서는 문자상수와 마찬가지로 작은 따옴표로 묶어줘야 함

|연산자  | 의미                       |
|:------|:---------------------------|
|=      | 비교대상과 같은 조건을 검색    |
|!=, <> | 같지 않다                   |
|>      | 크다                       |
||>=    | 크거나 같다                 |
|<      | 작다                       |
|<=     | 작거나 같다                 |

```sql
select * from emp
where hiredate <= '1981.06.09'
```

![](https://gekdev.github.io/docs/sql/commands/example/comp.jpg)

#### example

```sql
/* /////////////////////////////
A. 비교연산자
///////////////////////////// */

-- 1. 사원번호가 7900인 자료만 조회하기
select *
	from emp
	where empno = 7900;

-- 2. 급여(sal)가 900보다 작은 사원만 출력
select *
	from emp
	where sal < 900;
	
-- 3. 이름이 smith인 사원만 출력
select *
	from emp
	where ename = 'SMITH'; --"와 공백은 같은것, '만 문자열로 나타남, 리터럴 값은 소문자 대문자 구별함

-- 4. 입사일(hiredate) 1980-12-17인 사원만 출력
select *
	from emp
	where hiredate =  '1980-12-17'; -- 형변환(암묵)되어서 date타입을 비교하게됨

select *
	from emp
	where hiredate =  '19801217'; 
				
select *
	from emp
	where hiredate =  '1980-dec-17'; 	
	
select *
	from emp
	where hiredate =  '1980-DEC-17'; 	
	
select *
	from emp
	where hiredate =  '1980.12.17'; 	
		
select *
	from emp
	where hiredate =  '80/12/17'; -- DB환경설정때문에 error	
													
select *
	from emp
	where hiredate =  '1980.80.17'; 	-- 80월이 시스템으로 없기때문에 error
	
select *
	from emp
	where hiredate =  '1980.10.40'; 	-- 40일이 시스템으로 없기때문에 error
```

![](https://gekdev.github.io/docs/sql/commands/example/comp2.jpg)

```sql    
-- 5. 기본 연산자를 이용해서 현재 급여를 인상
-- 인상전급여, 인상후급여 = 인상전급여의 10% 인상
select 인상전급여, 인상후 급여 from emp;
select sal 인상전급여 , sal*1.1 인상후급여 from emp;
select sal 인상전급여 , (sal*1.1 + 100)/2 인상후급여 from emp; --db에 전혀 영향이 안감, 조회만 하는것(select)

-- 6. 급여가 4000보다 크거나 같은 사원만 출력
select * from emp where sal >= 4000;
select ename,sal from emp where 4000 <= sal;

-- 7. 사원명이 'W'보다 크거나 같은 사원만 출력
select * from emp where ename >= 'W';

-- 8. 급여가 2000보다 크면서 3000보다 작거나 같은 사원만 출력
select * from emp where sal between 2000 and 3000;
select * from emp where sal > 2000 and sal <= 3000;
```



### Logical operator

|연산자  | 의미                                          |
|:------|:---------------------------------------------|
|AND    | 두가지 이상의 조건 모두 만족해야만 검색            |
|OR     | 두가지 이상의 조건 중에서 한가지만 만족해도 검색 가능|
|NOT    | 조건에 만족하지 못하는 것만 검색                  |



2. between a and b : a와 b사이 범위의 값
3. in(a,b,c) : a,b,c값을 가지고 있는 데이터
4. like : 특정패턴을 가지고 있는 조건의 데이터
5. is null / is not null : null값을 검색

 
#### group by 절

**동일한 값을 갖는 로우들을 한 그룹으로 묶음**

#### order by 절

**특정 칼럼을 기준으로 순서대로 나열할 때 사용**

&#9656; asc 오름차순, desc 내림차순

order by 사용법
{: .label .mt-2}
```sql
select distinct deptno from emp order by deptno;

select distinct deptno from emp order by deptno asc; 
	-- default, 오름차순
	
select distinct deptno from emp order by deptno desc;
	-- 내림차순
```

![](https://gekdev.github.io/docs/sql/commands/example/desc.jpg)
