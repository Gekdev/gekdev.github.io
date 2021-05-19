---
layout: default
title: Command Types
parent: SQL
grand_parent: Database
nav_order: 1
---

# SQL Command Types
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## DDL(Data Definition Language) 

### DDL Basic

**데이터 정의어**

&#9656; 새로운 데이터베이스 구조를 정의하고 기존 데이터베이스 구조를 변경하는 명령어 집합

&#9656; 데이터베이스 구조를 표현하는 데이터베이스 스키마를 명세하기 위해 사용

사용 명령어
{: .label .label-red .mt-2}
<div class="code-example" markdown="1">
- CREATE : DB객체(user, table, view, index, ...)를 생성

- ALTER : 기존의 테이블(DB객체)을 변경함 (컬럼을 추가하거나 변경)

- RENAME : 테이블(DB객체)의 이름을 변경함

- TRUNCATE : 테이블(DB객체)을 잘라냄 (테이블 내의 저장된 내용 삭제)

- DROP : 기존의 테이블(DB객체)을 삭제함 (테이블의 구조 자체를 제거)
</div>

---

## DQL(Data Query Language)

### DQL Basic

**데이터 조회어**

&#9656; 아래 DML에 포함시키기도 함

사용 명령어
{: .label .label-red .mt-2}
<div class="code-example" markdown="1">
- SELECT : 테이블에 저장된 데이터를 조회하는 데 사용되는 가장 기본적인 문법
</div>

### Select 문

**테이블 내의 데이터를 조회할 때 사용**

SYNTAX
{: .label .mt-2}
<div class="code-example" markdown="1">
SELECT [distinct] 컬럼명 FROM 테이블명 [WHERE ...]

* distinct : 중복제거

* 컬럼명

    1. * : 객체(table, view)의 모든 컬럼을 출력
    
	2. 별칭(alias) : 해당객체 또는 컬럼명을 다른 이름으로 정의
    
	3. 표현식

* [] : where, order by... 절은 생략이 가능
</div>

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

![](https://gekdev.github.io/docs/database/sql/example/sel_bas.jpg)

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

![](https://gekdev.github.io/docs/database/sql/example/smol_quot.jpg)

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

![](https://gekdev.github.io/docs/database/sql/example/distc_jpg)

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

![](https://gekdev.github.io/docs/database/sql/example/ex_name.jpg)

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

![](https://gekdev.github.io/docs/database/sql/example/desc.jpg)

---

## DML(Data Manipulation Language)

### DML Basic

**데이터 조작어**

&#9656; 데이터베이스 안의 데이터를 실제 조작하는 명령어 집합

&#9656; DBMS에게 데이터의 입력, 수정, 삭제 및 검색을 요청하기 위해 사용

사용 명령어
{: .label .label-red .mt-2}
<div class="code-example" markdown="1">
- INSERT : 새로운 데이터를 삽입함

- UPDATE : 기존의 데이터를 변경함

- DELETE : 기존의 데이터를 삭제함 
</div>

### insert 문

**데이터를 해당하는 테이블에 삽입하기 위해 사용**

SYNTAX
{: .label .mt-2}
<div class="code-example" markdown="1">
INSERT INTO employees VALUES ('id','부서이름','연봉' .....);

</div>

### update 문

**테이블에 저장되어 있는 데이터를 수정할 때 사용**

### delete 문

**테이블에 있는 데이터를 삭제할 때 사용**


---

## TCL(Transaction Control Language)

**트랜잭션 제어언어**

&#9656; 데이터의 일관성을 유지하면서 안정적으로 데이터를 복구시키기 위해서 사용

&#9656; Transaction은 여러개의 DML(데이터조작어) 명령문들을 하나의 작업단위로 묶어놓은 집합

&#9656; 실수 없이 완벽하게 입력한 명령어만 영구저장하기 위해 TCL을 사용

&#9656; 한번 커밋하면 롤백 불가

&#9656; 비절차적 언어 : 위에서 오류나도 오류난 것 아래들은 실행됨

사용 명령어
{: .label .label-red .mt-2}
<div class="code-example" markdown="1">
- COMMIT : 변경된 내용을 영구 저장

- ROLLBACK : 변경되기 이전 상태로 되돌림

- SAVAPOINT : 특정 위치까지를 영구 저장 혹은 이전 상태로 돌리기 위해 저장점을 만듬
</div>

---

## DCL(Data Control Language)

**데이터 제어어**

&#9656; 데이터베이스를 제어하고 통제하기 위해 사용하는 명령어 집합

&#9656; 데이터베이스가 무결성을 유지하도록 각종 제약이나 옵션을 설정함

&#9656; Mutual exclusion(상호배제)를 통한 transaction이 서로 방해를 받지 않도록 병행 제어

사용 명령어
{: .label .label-red .mt-2}
<div class="code-example" markdown="1">
- GRANT : 사용자에게 특정 권한을 부여

- REVOKE : 부여했던 권한 제거
</div>

#### Oracle Account Type

* SYS : Oracle DB 관리자, Super 사용자 계정, 모든 관리 기능을 수행할 수 있음

* SYSTEM : 백업 및 복구, 데이터베이스 업그레이드를 제외한 모든 관리 기능 수행 가능

* HT : 오라클을 잘 다루지 못하는 사용자를 위한 교육용 계정
