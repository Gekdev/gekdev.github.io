---
layout: default
title: DDL
parent: Commands
grand_parent: SQL / Oracle
nav_order: 1
--- 

# DDL Commands
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## DDL Basic

**데이터 정의어**

**테이블의 구조 자체를 생성, 수정, 제거하도록 하는 명령문의 집합**

### Data type

1. 문자형
          
    * char(n) : 고정길이, 최대 2KB, 기본크기 1byte
    
    * varchar2(n) : 가변길이, 최대 4KB, 기본크기 1byte
    
    * long : 가변길이, 최대 2GB

2. 숫자형

    * number(p,s) : 가변숫자, p(1~38 기본값=38), s(-84~127 기본값=0), 최대 22bytes
    
    * float(p) : number하위타입, p(1~128 기본값=128), 최대 22bytes    

3. 날짜형

    * date : bc 4712.01.01 ~ 9999.12.31까지 연,월,시,분,초까지 입력가능
    
    * timestamp : 연,월,일,시,분,초,밀리초까기 입력이 가능

4. lob타입 

    **Large Object의 약자로 대용량 데이터를 저장할 수 있는 데이터타입**
    
    일반적으로 그래프, 이미지, 사운드등 비정형 데이터를 저장할 때 LOB타입을 사용

    문자형 대용량 데이터는 CLOB나 NLOB를 사용하고 그래프,이미지,동영상등의 데이터
    는 주로 BLOB를 주로 사용

    * clob  : 문자형 대용량 객체, 고정길이와 가변길이 문자형을 지원
    
    * blob  : 이진형 대용량 객체 주로 멀티미디어자료를 저장
    
    * bfile : 대용량 이진파일에 대한 파일의 위치 및 이름을 저장
            
---

## CREATE Statement

### CREATE Statement Basic

**테이블 생성 명령문**

테이블 생성 조건

1. 테이블명 정의

2. 칼럼의 데이터 타입과 무결성 제약조건을 정의

테이블명, 칼럼명 규칙
{: .label .mt-2}

&#9656; 문자로 시작해야 하며 30자 이내로 작성

&#9656; 문자, 숫자, 특수문자만 사용가능

&#9656; 대소문자 구별이 없음, 소문자로 저장하려면 작은 따옴표로 묶어줘야 함 

&#9656; 동일 사용자가 소유한 다른 객체의 이름과 중복되지 않아야 함

&#9656; 테이블명이나 컬럼이름에는 오라클키워드를 사용 XXXXX

&#9656; 테이블이름이나 컬럼이름은 최대 30byte까지 가능(즉, 한글은 15자리까지만 가능)

&#9656; 한글도 가능하지만 추천하지 않음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
CREATE TABLE [schema.(사용자계정)] 테이블명(

칼럼명 데이터타입[DEFAULT expression(기본값)][column_constratin_clause(무결성제약조건)],

...

컬럼명n 데이터타입(크기)
);

&#9656; DEFAULT expression : 데이터 입력시 값이 생략된 경우에 입력되는 기본값

&#9656; column_constratin_clause : 칼럼에 대해 정의되는 무결성 제약 조건
</div>
```sql
create table mytable(
    no number(3,1), 
    name varchar2(10),
    hiredate date
);
```

![](https://gekdev.github.io/docs/sql/commands/example/create.jpg) 

!NOTE
<div class="code-example" markdown="1">
식별자는 한글이름도 가능하지만 비추천 
</div>
```sql
create table 마이테이블(
    번호 number(3), 
    이름 varchar2(10),
    입사일 date
);
```

### Create table by Subquery

**다른 테이블의 구조와 함께 테이트를 복사해 새로운 테이블을 생성**

&#9656; 서브쿼리 내의 산술식에 대해서는 별칭을 지정하고 사용해야 함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
CREATE TABLE 테이블명[컬럼명,]

AS subquery;

[]를 명시할경우 데이터타입, 칼럼수가 일치해야 함

[]명시하지 않을경우 서브쿼리 칼럼명이 그대로 생성, 무결성 제약조건은 not null과 default값만 복사된다
</div>

1. 구조와 데이터 모두 복사하기

    ```sql
    create table 새로운_테이블명
    as
    select * from 복사하고싶은_테이블명;
    ```

2. 데이터 일부만 복사하기

    ```sql
    create table 새로운_테이블명
    as
    select * from 복사하고싶은_테이블명
    where 조건식
    ```

3. 테이블의 구조만 복사하기

    서브쿼리 조건절에 항상 거짓이 되는 조건을 지정하면 조건에 맞는 데이터가 발견되지 않아서 데이터는 복사되지 않고 구조만 복사됨 (like where 0=1)

    ```sql
    create table 새로운_테이블명
    as
    select * from 복사하고싶은_테이블명
    where where
    ```

---

## ALTER Statement

**테이블의 구조를 변경해야 하는 경우 사용**

컬럼명 변경, 칼럼 추가, 수정, 삭제할 수 있음

### Column ADD

**새로운 칼럼을 추가, 추가되는 칼럼에도 기본 값을 지정**

syntax
{: .label mt-2}
<div class="code-example" markdown="1">
ALTER TABLE 테이블명

**ADD** (칼럼명 데이터타입 DEFAULT expr);
</div>
```sql
ALTER TABLE emp_second 
add(location varchar2(50));
```

* 칼럼 추가시 기본 값 설정하기

    ```sql
    alter table dept7 add(lovation varchar2(10) default '서울');
    alter table dept7 add(xxx number default 0);
    alter table dept7 add(hiredate date number sysdate);
    ```

### Column MODIFY

**칼럼의 타입, 크기, 기본값을 변경할 수 있음**

&#9656; 기존 칼럼에 데이터가 없는 경우에는 칼럼 타입이나 크기 변경이 자유롭지만, 기존 데이터가 존재하는 경우에는 타입 변경은 char와 varchar2만 가능

&#9656; 변경한 칼럼의 크기가 저장된 데이터의 크기보다 같거나 클 경우에만 변경 가능 

&#9656; 숫자 타입은 폭 혹은 전체 자릿수를 늘릴 수 있음

&#9656; 기본값의 변경은 변경 후에 입력되는 데이터부터 적용 

syntax
{: .label mt-2}
<div class="code-example" markdown="1">
ALTER TABLE 테이블명

**MODIFY** 칼럼명 데이터타입 DEFAULT expr
</div>
```sql
ALTER TABLE emp_second 
MODIFY (location varchar2(100));
```

### Column RENAME

**칼럼명 변경**

syntax
{: .label mt-2}
<div class="code-example" markdown="1">
ALTER TABLE 테이블명

**RENAME COLUMN** 기존 칼럼명 TO 새칼럼명
</div>
```sql
ALTER TABLE emp_second 
RENAME COLUMN location to loc;
```

### Column DROP

**테이블 내의 특정 칼럼과 칼럼의 데이터를 제거**

&#9656; 2개 이상의 칼럼이 존재하는 테이블에서만 삭제 가능

&#9656; 한번에 하나의 칼럼만 삭제

syntax
{: .label mt-2}
<div class="code-example" markdown="1">
ALTER TABLE 테이블명

**DROP COLUMN** 칼럼명
</div>
```sql
ALTER TABLE emp_second 
DROP COLUMN loc;
```

### SET UNUSED

**시스템의 요구가 적을 때 칼럼을 제거할 수 있도록 하나 이상의 칼럼을 UNUSED로 표시**

&#9656; 실제로 테이블에서 칼럼이 제거되지는 않음, DROP 명령을 실행하는데 걸리는 시간보다 응답시간이 빨라짐

&#9656; UNUSED로 표시된 칼럼은 데이터가 존재하는 경우에도 삭제된것으로 처리되기 때문에 SELECT절로 엑세스 불가능

&#9656; DESCRIBE문으로도 표시되지 않음

syntax
{: .label mt-2}
<div class="code-example" markdown="1">
ALTER TABLE 테이블명

**SET UNUSED** (칼럼명)
</div>
```sql
ALTER TABLE emp_second 
SET UNUSED (comm);
```

### DROP UNUSED COLUMNS

**현재 UNUSED로 표시된 모든 칼럼을 제거**

syntax
{: .label mt-2}
<div class="code-example" markdown="1">
ALTER TABLE 테이블명

**DROP UNUSED COLUMNS**;
</div>
```sql
ALTER TABLE emp_second 
DROP UNUSED COLUMNS;
```

---

## RENAME Statement

**테이블을 포함한 객체의 이름을 변경하는 DDL 명령문**

syntax
{: .label mt-2}
<div class="code-example" markdown="1">
**RENAME** 기존 테이블명 **TO** 새로운 테이블명;
</div>
```sql
RENAME EMP_SECOND TO EMP_THIRD;
```

---

## DROP Statement

**기존 테이블과 데이터를 모두 제거**

삭제할 테이블의 기본 키나 고유 키를 다른 테이블에서 참조하고 있는 경우에는 삭제가 불가능 &#8594; 참조하는 테이블을 먼저 제거해야 함

syntax
{: .label mt-2}
<div class="code-example" markdown="1">
DROP TABLE 테이블명;
</div>
```sql
DROP TABLE EMP_THIRD;
```

---

## TRUNCATE Statement 

**테이블의 모든 로우를 제거(데이터 제거)**

&#9656; 테이블의 구조는 그대로 유지하고, 테이블의 데이터와 할당된 공간만 해제

&#9656; 테이블에 생성된 제약 조건과 연관된 인덱스, 뷰, 동의어는 유지됨

syntax
{: .label mt-2}
<div class="code-example" markdown="1">
TRUNCATE TABLE 테이블명;
</div>
```sql
TRUNCATE TABLE EMP_FOURTH;
```

---

## Data Dictionary

데이터사전 : **사용자와 데이터베이스 자원을 효율적으로 관리하기 위한 다양한 정보를 저장하는 시스템 테이블의 집합**

&#9656; 사용자가 테이블을 생성하거나 사용자를 변경하는 등의 작업을 할 때 데이터 베이스 서버에의해 자동으로 갱신되는 테이블

&#9656; 사용자는 데이터 사전의 내용을 직접 수정하거나 삭제할 수 없고 사용자가 이해할 수 있는 데이터를 산출해 줄 수 있도록 하기 위해 읽기 전용 뷰 형태로 정보를 제공 

&#9656; 오라클 서버는 데이터베이스의 이름이나 생성 시각, 사용자 권한 및 데이터의 변경사항을 반영하기 위해 지속적으로 수정, 관리를 하고있음

데이터 사전은 크게 세가지로 나뉨

| 접두어 | 의미 | 
|:------|:----|
| USER | 자신의 계정이 소유한 객체 등에 관한 정보 조회|
| ALL | 자신 계정 소유 또는 권한을 부여 받은 객체 등에 관한 정보 조회|
| DBA | 데이터베이스 관리자만 접근 가능한 객체 등의 정보 조회|

### USER_ Data Dictionary

**사용자와 가장 밀접하게 관련된 뷰**

&#9656; 자신이 생성한 테이블, 인덱스, 뷰, 동의어 등의 객체나 해당 사용자에게 부여된 권한 정보를 제공

* USER_TABLES : 사용자가 소유한 테이블의 정보를 조회

* USER_SEQUENCES : 사용자가 소유한 시퀀스의 정보를 조회

* USER_INDEXES : 사용자가 소유한 인덱스 정보를 조회

* USER_VIEWS : 사용자가 소유한 뷰 정보를 조회

&#9656; 데이터사전은 USER 뒤에 원하는 객체를 기술하고 뒤에 기술되는 명칭은 S가 붙은 복수 타입임을 주의

```sql
SELECT TABLE_NAME FROM USER_TABLES;
```

![](https://gekdev.github.io/docs/sql/commands/example/user_tables.jpg)

### ALL_ Data Dictionary

**전체 사용자와 관련된 뷰**

&#9656; 사용자가 접근할 수 잇는 모든 객체에 대한 정보를 조회할 수 있음

&#9656; 조회중인 객체가 누구의 소유인지를 확인하기 위해 OWNER칼럼 제공

&#9656; all_tables로 자신이 소유하거나 권한을 부여받은 테이블에 대한 정보를 조회

```sql
SELECT OWNER, TABLE_NAME FROM ALL_TABLES;
```

![](https://gekdev.github.io/docs/sql/commands/example/all_tables.jpg)

* 오라클의 테이블 정보 보기

    ```sql
    select * from all_tab_columns
    where table_name = 'DEPT6';
    ```
    
    ![](table_name.jpg)

### DBA_ Data Dictionary

**시스템 관리와 관련된 뷰**

&#9656; DBA나 시스템 권한을 가진 사용자만 접근 가능 

&#9656; 현재 접속한 사용자가 HR이라면 DBA_로 시작하는 데이터 사전을 조회할 권한이 없기때문에 DBA권한을 가진 SYSTEM 계정으로 접속해야 함

```sql
SELECT OWNER, TABLE_NAME FROM dba_tables;
```

![](https://gekdev.github.io/docs/sql/commands/example/dba_tables.jpg)

### Example

![](https://gekdev.github.io/docs/sql/commands/example/ddl_q1.jpg)

```sql
-- Q1. 
create table new_emp(
		no number(5)
	, name varchar2(20)
	, hiredate date
	, bonus number(6,2)
);

select * from new_emp;
```

![](https://gekdev.github.io/docs/sql/commands/example/ddl_q2.jpg)

```sql
-- Q2.
create table new_emp2
as
select no, name, hiredate from new_emp;

select * from new_emp2;
```

![](https://gekdev.github.io/docs/sql/commands/example/ddl_q3.jpg)

```sql
-- Q3. 
create table new_emp3
as
select * from new_emp2
where 1=2;

select * from new_emp3;
```

![](https://gekdev.github.io/docs/sql/commands/example/ddl_q4.jpg)

```sql
-- Q4. 
alter table new_emp2 add(birthday varchar2(10) default sysdate);

select * from new_emp2;
```

![](https://gekdev.github.io/docs/sql/commands/example/ddl_q5.jpg)

```sql
-- Q5. 
alter table new_emp2 rename column BIRTHDAY to birth;

select * from new_emp2;

-- Q6. 
alter table new_emp2 modify(no number(7));

select * from new_emp2;

-- Q7. 
alter table new_emp2 drop column birth;

select * from new_emp2;

-- Q8. 
truncate table new_emp2;

select * from new_emp2;

-- Q9. 
drop table new_emp2;

select * from new_emp2;

```