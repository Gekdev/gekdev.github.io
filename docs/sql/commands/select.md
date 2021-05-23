---
layout: default
title: Select
parent: Command Types
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


#### select basic

**select coll, ... colN from 테이블명**

&#9656; 특정 테이블의 자료 조회하기

테이블 기본 조회법
{: .label .mt-2}
```sql
select * from emp; 
    -- emp 전체 테이블 조회
    
select ename, empno, job from emp;
    -- ename, empno, job 컬럼 조회
```

![](https://gekdev.github.io/docs/sql/commands/example/sel_bas.jpg)

&#9656; 문자열 사용할때는 주의해야 함, 작은 따옴표 안에 작은 따옴표 nesting 불가 (에러)

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

#### distinct 절

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

#### 표현식

**'리터럴, 상수, 문자', 표현식은 작은 따옴표로 정의해야 함**

&#9656; 큰따옴표 에러

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

#### alias

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

#### concat(),||

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

#### Search Other 스키마 Table

```sql
-- 사용자의 접근 권한에 따라서 조회를 할 수 있음
select * from hr.employees; 
select * from scott.emp; --hr 사용자에서는 접근할 수 없음
```

#### where 절

**테이블에 저장된 데이터 중 원하는 데이터만 선택적으로 추출 가능**

&#9656; 문자 데이터를 조회할 때는 반드시 작은 따옴표('')로 묶어 표현해야 하고 대소문자 주의

1. 비교연산자
    
    ```sql
     =      : 비교대상과 같은 조건을 검색
     !=, <> : 같지 않다
     >      : 크다
     >=     : 크거나 같다.
     <      : 작다
     <=     : 작거나 같다.
     ```

2. between a and b : a와 b사이 범위의 값
3. in(a,b,c) : a,b,c값을 가지고 있는 데이터
4. like : 특정패턴을 가지고 있는 조건의 데이터
5. is null / is not null : null값을 검색
6. a and b : a와 b의 조건을 만족하는 데이터
7. a or b  : a이거나 b인 조건을 만족하는 데이터
8. not a : a가 아닌 모든 데이터
 
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
