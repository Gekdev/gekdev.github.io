---
layout: default
title: DML
parent: Commands
grand_parent: SQL / Oracle
nav_order: 3
---

# DML Commands
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## DML Basic

DML : 데이터 조작어

테이블에 새로운 데이터를 삽입하거나 기존의 데이터를 수저하거나 삭제하기 위한 명령어의 집합

---

## INSERT Statement

### CREATE Statement Basic

테이블 생성 조건

1. 테이블명 정의

2. 칼럼의 데이터 타입과 무결성 제약조건을 정의

테이블명, 칼럼명 규칙
{: .label .mt-2}

문자로 시작해야 하며 30자 이내로 작성

문자, 숫자, 특수문자만 사용가능

대소문자 구별이 없음, 소문자로 저장하려면 작은 따옴표로 묶어줘야 함 

동일 사용자가 소유한 다른 객체의 이름과 중복되지 않아야 함

테이블명이나 컬럼이름에는 오라클키워드를 사용 XXXXX

테이블이름이나 컬럼이름은 최대 30byte까지 가능(즉, 한글은 15자리까지만 가능)

한글도 가능하지만 추천하지 않음

syntax
{: .label .mt-2}

CREATE TABLE [schema.(사용자계정)] 테이블명(

칼럼명 데이터타입[DEFAULT expression(기본값)][column_constratin_clause(무결성제약조건)],

...

컬럼명n 데이터타입(크기)
);

DEFAULT expression : 데이터 입력시 값이 생략된 경우에 입력되는 기본값

column_constratin_clause : 칼럼에 대해 정의되는 무결성 제약 조건
</div>
```sql
create table mytable(
    no number(3,1)
    , name varchar2(10)
    , hiredate date
);
```

![]()

!NOTE

식별자는 한글이름도 가능하지만 비추천 

```sql
create table 마이테이블(
    번호 number(3)
    , 이름 varchar2(10)
    , 입사일 date
);
```

### Create table by Subquery

다른 테이블의 구조와 함께 테이트를 복사해 새로운 테이블을 생성

서브쿼리 내의 산술식에 대해서는 별칭을 지정하고 사용해야 함

syntax
{: .label .mt-2}

CREATE TABLE 테이블명[컬럼명,] 
AS subquery;

[]를 명시할경우 데이터타입, 칼럼수가 일치해야 함

[]명시하지 않을경우 서브쿼리 칼럼명이 그대로 생성, 무결성 제약조건은 not null과 default값만 복사된다
</div>

1. 구조와 데이터 모두복사하기

```sql
create table emp_second
as
select * from emp;
```

![]()

2. 데이터 일부만 복사하기

```sql
create table emp_second
as
select * from emp
where deptno = 10;
```

3. 테이블의 구조만 복사하기

서브쿼리 조건절에 항상 거짓이 되는 조건을 지정하면 조건에 맞는 데이터가 발견되지 않아서 데이터는 복사되지 않고 구조만 복사됨 (like where 0=1)

```sql
create table emp_second
as
select * from emp
where 1=2;
```

---

## UPDATE Statement 

테이블의 구조를 변경해야 하는 경우 사용

컬럼명 변경, 칼럼 추가, 수정, 삭제할 수 있음

### Column ADD

**새로운 칼럼을 추가, 추가되는 칼럼에도 기본 값을 지정**

syntax
{: .label mt-2}

ALTER TABLE 테이블명
ADD 칼럼명 데이터타입 DEFAULT expr
</div>
```sql
alter table dept6 add(location varchar2(1));
```

### Column MODIFY

syntax
{: .label mt-2}

ALTER TABLE 테이블명
MODIFY 칼럼명 데이터타입 DEFAULT expr
</div>

### Column RENAME

**칼럼명 변경**

syntax
{: .label mt-2}

ALTER TABLE 테이블명
RENAME 기존 칼럼명 TO 새칼럼명
</div>
```sql
alter table dept6 rename column location to loc;
```

### Column DROP

**테이블 내의 특정 칼럼과 칼럼의 데이터를 제거**

2개 이상의 칼럼이 존재하는 테이블에서만 삭제 가능

한번에 하나의 칼럼만 삭제

syntax
{: .label mt-2}

ALTER TABLE 테이블명
DROP COLUMN 칼럼명
</div>
```sql
alter table dept6 rename column location to loc;
```

### SET UNUSED

**시스템의 요구가 적을 때 칼럼을 제거할 수 있도록 하나 이상의 칼럼을 UNUSED로 표시**

실제로 테이블에서 칼럼이 제거되지는 않음, DROP 명령을 실행하는데 걸리는 시간보다 응답시간이 빨라짐

UNUSED로 표시된 칼럼은 데이터가 존재하는 경우에도 삭제된것으로 처리되기 때문에 SELECT절로 엑세스 불가능

DESCRIBE문으로도 표시되지 않음

syntax
{: .label mt-2}

ALTER TABLE 테이블명
SET UNUSED (칼럼명)
</div>
```sql

```

### DROP UNUSED COLUMNS

**현재 UNUSED로 표시된 모든 칼럼을 제거**

syntax
{: .label mt-2}

ALTER TABLE 테이블명
SET UNUSED (칼럼명)
</div>
```sql

```

---

## DELETE Statement

**테이블을 포함한 객체의 이름을 변경하는 DDL 명령문**

syntax
{: .label mt-2}

RENAME 기존 테이블명 TO 새로운 테이블명;
</div>
```sql

```

---

## TRANSACTION

**기존 테이블과 데이터를 모두 제거**

삭제할 테이블의 기본 키나 고유 키를 다른 테이블에서 참조하고 있는 경우에는 삭제가 불가능 -> 참조하는 테이블을 먼저 제거해야 함

syntax
{: .label mt-2}

DROP TABLE 테이블명;
</div>
```sql

```
