---
layout: default
title: Integrity Constraint
parent: SQL / Oracle
nav_order: 7
---

# SQL Data Integrity Constraint Rule
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Data Integrity Constraint Rule

### Constraint Rule Basic

**데이터 무결성 제약 조건**

**테이블에 유효하지 않은 데이터가 입력되는 것을 방지하기 위해서 테이블을 생성할 떄 각 칼럼에 대해 정의하는 여러가지 규칙**

&#9656; 새로운 데이터가 삽입되거나 기존 데이터가 수정, 삭제될 때 적용

&#9656; 일반적으로 테이블이 생성될 때 생성되지만, ALTER TABLE로 제약 조건을 추가할 수 있으며 삭제도 가능

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
CREATE TABLE [schema.] table (

column datatype[DEFAULT expression] [column_constraint],

[table_constraint][,...]);

&#9656; 제약조건의 범위 : 칼럼레벨, 테이블레벨
</div>

&#9656; 제약조건의 이름을 지정하지 않으면 오라클에서 SYS_Cn 형태로 이름을 자동 생성

&#9656; 제약 조건을 활성화 혹은 비활성화 할 수 있어서 이를 융통성 있게 사용할 수 있음

&#9656; 특정 테이블에 정의된 제약 조건은 USER_CONSTRAINTS 데이터 사전을 통해 살펴볼 수 있음

### Five different Constraints

**오라클에서 지원하는 제약조건은 아래 5가지** (DEFAULT 추가)

| 무결성 제약 조건 | 역할 |
|:----------------|:-----|
| NOT NULL | 칼럼에 NULL값을 포함하지 못하도록 지정 |
| UNIQUE | 테이블의 모든 로우에 대해서 유일한 값을 갖도록 함 |
| PRIMARY KEY | 테이블의 각 행을 식별하기 위한 것으로 NULL과 중복된 값을 모두 허용하지 않음 (NOT NULL + UNIQUE) |
| FOREIGN KEY | 참조되는 테이블에 칼럼 값이 항상 존재해야 함 |
| CHECK | 저장 가능한 데이터 값의 범위나 조건을 지정하여 설정한 값만을 허용 |
| DEFAULT | 아무런 값을 입력하지 않았을 때 디폴트 제약의 값이 입력 |

### Constraint Rule Scope Level

1. 칼럼 레벨

    **칼럼을 정의할 때 하나의 칼럼에 대해서 제약 조건을 지정하며 모든 제약 조건을 정의할 수 있음**

    예시
    {: .label .label-purple .mt-2}
    ```sql
    create table new_emp_1 (
      no number(4)   	constraint emp_1_no_pk primary key
	, name varchar2(20)	
	, jumin	varchar2(13)
    );
    ```

2. 테이블 레벨

    **칼럼 정의와는 별도로 정의, NOT NULL을 제외한 모든 제약 조건을 정의할 수 있음**

    예시
    {: .label .label-purple .mt-2}
    ```sql
    create table new_emp_1 (
      no number(4)   	
	, name varchar2(20)	
	, jumin	varchar2(13)
    , constraint emp_1_no_pk primary key(no)
    );
    ```

### NOT NULL

**해당 칼럼이 NULL값을 가질 수 없게 함 = 반드시 값을 입력해야 하는 칼럼에 지정**

&#9656; 해당 칼럼에 데이터를 입력할 때 생략하면 오류, 기본 데이터를 NULL로 수정할 때에도 오류

&#9656; 칼럼 레벨로만 정의할 수 있음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
칼럼명 데이터타입 **NOT NULL**
</div>
```sql
create table summer(
 	  weather varchar(20) not null
	, fruits varchar(10) not null
);

insert into summer values('sunny', 'cherry');
insert into summer values(null, 'cherry');
select * from summer;
```

![](notnull.jpg)

### UNIQUE

**특정 칼럼에 모든 값이 고유하게 유지되도록 하는 고유 키를 생성 = 칼럼에 중복된 값을 가질 수 없게 함**

&#9656; 칼럼레벨, 테이블 레벨로 정의 가능

&#9656; 오라클은 고유 키에 대해서 인덱스를 암시적으로 생성

&#9656; NULL은 UNIQUE 제약 조건에 위반되지 않으므로 NULL값을 허용!

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
1. 약식 문법

    칼럼명 데이터타입 **UNIQUE**

2. 정식 문법

    칼럼명 데이터타입 **CONSTRAINT constraint_name UNIQUE**

    &#9656; constraint_name은 테이블명, 칼럼명, 제약 조건 유형을 조합해서 명명함 ex) summer_weather_nn

    &#8594; 다른 데이터 제약 조건들도 같은 방식으로 문법이 형성됨
</div>
```sql
create table customer (
		  id varchar2(20) unique
		, pwd varchar2(20) not null
);

insert into customer values('id_01','pw_12345');
insert into customer values(null,'pw_null');
insert into customer values('id_01','pw_54321');
select * from customer;
```

![](unique.jpg)

SCOTT.SYS_C007066이라는 값은 오라클에서 자동으로 생성한 제약 조건 이름

#### USER_CONSTRAINTS

이 데이터 사전은 **제약 조건이 설정된 테이블 명, 제약 조건 이름, 제약 조건 종류 및 활성화 상태 정보를 저장**

USER_CONS_COLUMNS 데이터 사전 : USER_CONSTRAINTS 데이터 사전으로는 알 수 없는 제약 조건이 설정된 칼럼의 이름을 알려줌 

```sql
select table_name, constraint_name 
from USER_CONSTRAINTS
where table_name in('CUSTOMER');
```
![](constraint_name.jpg)

### PRIMARY KEY

**테이블의 모든 로우를 구별하기 위한 식별자를 정의 = 데이터 구분을 위해 사용**

&#9656; 테이블에 기본키를 생성

&#9656; 두개의 칼럼을 동시에 PRIMARY KEY라고 설정할 수 없음 → ERROR 

&#9656; 고유 키 제약조건과 NOT NULL 제약 조건을 결합한 개념

&#9656; 칼럼레벨, 테이블 레벨로 정의 가능

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
1. 약식 문법

    칼럼명 데이터타입 **PRIMARY KEY**

2. 정식 문법

    칼럼명 데이터타입 **CONSTRAINT constraint_name PRIMARY KEY**

    &#9656; constraint_name은 테이블명, 칼럼명, 제약 조건 유형을 조합해서 명명함 ex) summer_weather_nn

    &#8594; 다른 데이터 제약 조건들도 같은 방식으로 문법이 형성됨
</div>
```sql
create table winter (
	id varchar(20),
	pwd varchar(20) constraint winter_pwd_nn not null,
	phone number(15) constraint winter_number_uq unique,
	constraint winter_id_pk primary key(id)
);

insert into winter values('id_1','pw_12345','01011111111');
insert into winter values('id_1','pw_12345','01011111111');
-- 같은값이 두번 들어가서 unique constraint (SCOTT.WINTER_ID_PK) violated 오류가 뜸
```

![](primary.jpg)

### FOREIGN KEY

****

&#9656; 

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
칼럼명 데이터타입 **NOT NULL**
</div>
```sql

```

![]()

### CHECK

****

&#9656; 

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
칼럼명 데이터타입 **NOT NULL**
</div>
```sql

```

![]()

### DEFAULT

****

&#9656; 

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
칼럼명 데이터타입 **NOT NULL**
</div>
```sql

```

![]()


---

## Change Integrity Constraint

### ADD CONSTRAINT

### DROP CONSTRAINT

### DISABLE CONSTRAINT

### ENABLE CONSTRAINT

