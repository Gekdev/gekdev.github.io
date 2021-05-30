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
1. 정식문법

    칼럼명 데이터타입 **CONSTRAINT 칼럼명 NOT NULL**

2. 약식문법

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

![](https://gekdev.github.io/docs/sql/example/notnull.jpg)

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

![](https://gekdev.github.io/docs/sql/example/unique.jpg)

SCOTT.SYS_C007066이라는 값은 오라클에서 자동으로 생성한 제약 조건 이름

#### USER_CONSTRAINTS

이 데이터 사전은 **제약 조건이 설정된 테이블 명, 제약 조건 이름, 제약 조건 종류 및 활성화 상태 정보를 저장**

USER_CONS_COLUMNS 데이터 사전 : USER_CONSTRAINTS 데이터 사전으로는 알 수 없는 제약 조건이 설정된 칼럼의 이름을 알려줌 

```sql
select table_name, constraint_name 
from USER_CONSTRAINTS
where table_name in('CUSTOMER');
```
![](https://gekdev.github.io/docs/sql/example/constraint_name.jpg)

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

![](https://gekdev.github.io/docs/sql/example/primary.jpg)

### FOREIGN KEY

**외래 키 제약조건**

참조의 무결성은 테이블과 테이블 사이의 주종관계설정을 위한 제약 조건

&#9656; FOREIGN KEY는 참조테이블의 컬럼이 PK or UK인 컬럼만 foreign key로 지정할 수 있음

* 자식테이블 : 다른테이블의 칼럼값을 참조하는 테이블

* 부모테이블 : 다른 테이블에 의해 참조되는 테이블

* 외래키 : 부모 테이블의 칼럼 값을 자식테이블의 칼럼

* 부모키(참조키) : 자식테이블에서 참조하는 부모테이블의 칼럼

    &#8594; 부모키가 되기 위한 칼럼은 부모 테이블의 기본키나 유일키로 설정되어 있어야 함

![](https://gekdev.github.io/docs/sql/example/fkpk.jpg)

&#9656; 부모키로 설정된 칼럼에 존재하는 값만 추가하고 존재하지 않는 값이라면 추가하지 않음

&#9656; **자식 테이블에서 데이터를 추가할 떄 왜래키에는 부모테이블에 저장된 기본키나 유일키의 정보중 하나가 정보가 일치하거나 null만 입력 가능해야 한다는 조건이 참조의 무결성 제약조건**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
1. 정식문법

    칼럼명 데이터타입 **CONSTRAINT constraint_name REFERENCES 부모테이블(칼럼명)**

2. 약식문법

    칼럼명 데이터타입 **REFERENCES 부모테이블(칼럼명)**
</div>
```sql
CREATE TABLE NEW_EMP1(
      deptno    varchar2(6) 	constraint emp_1_deptno_fk references dept2(dcode)
    , deptno    varchar2(6) 	references dept2(dcode)
)
```

### CHECK

**칼럼에서 허용 가능한 데이터의 범위나 조건을 정의**

&#9656; 입력되는 값을 체크해 설정된 값 이외의 값이 들어오면 오류 메시지와 함께 명령이 수행되지 못하게 하는 것

&#9656; 데이터값의 범위, 특정 패턴의 숫자나 문자를 설정할 수 있음

&#9656; 조건의 수에는 제한이 없기 때문에 하나의 칼럼에 여러개의 CHECK조건을 정의할 수 있음

NOTE!
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
CURRVAL, NEXTVAL, ROWNUM과 같은 의사칼럼이나 SYSDATE,USER와 같은 함수에는 사용 불가능
</div>

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
1. 정식문법

    칼럼명 데이터타입 **CONSTRAINT constraint_name CHECK(조건문)**

2. 약식문법

    칼럼명 데이터타입 **CHECK(조건문)**
</div>
```sql
CREATE TABLE NEW_EMP1(
      loc_code	number(1)    constraint emp_1_loc_code_ck check(loc_code < 5)
    , loc_code	number(1)    check(loc_code < 5)
)
```

### DEFAULT

**아무런 값을 입력하지 않았을 때 디폴트 제약의 값이 입력**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
칼럼명 데이터타입 **DEFAULT 값**
</div>
```sql
CREATE TABLE NEW_EMP1(
      loc_code	number(1) DEFAULT 1
)
```

---

## Change Integrity Constraint

ALTER TABLE문을 사용해서 기존 테이블에 대해서 제약 조건을 추가하거나 삭제하고 변경할 수 있음

### ADD CONSTRAINT

**기존 테이블에 대해서도 제약 조건 추가**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
ALTER TABLE 테이블명 
ADD CONSTRAINT constraint_name 제한조건(칼럼명);
</div>
```sql
-- PRIMARY KEY 제약조건 추가하기
ALTER TABLE NEW_EMP1
ADD CONSTRAINT emp_copy_eno_pk PRIMARY KEY(ENO);

-- FOREIGN KEY 제약조건 추가하기
ALTER TABLE NEW_EMP1
ADD CONSTRAINT emp_copy_eno_pk FOREIGN KEY(ENO) REFERENCES dept_copy(dno);
```

### MODIFY CONSTRAINT 

**제약조건을 다른 조건에서 NOT NULL로 수정하기**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
ALTER TABLE 테이블명 
MODIFY 칼럼명 CONSTRAINT constraint_name NOT NULL;
</div>
```sql
-- NOT NULL로 NULL값 허용하지 않게 하기
ALTER TABLE EMP_COPY
MODIFY ename CONSTRAINT emp_copy_ename_nn NOT NULL;
```

### DROP CONSTRAINT

**제약 조건 제거하기**

&#9656; 외래 키 제약 조건으로 지정되어 있는 부모 테이블의 기본 키 제약 조건을 제거하려면 자식 테이블의 FK제약 조건을 먼저 제거한 후 제거나 CASCADE옵션을 사용

&#9656; CASCADE옵션을 사용하면 제거하려는 칼럼을 참조하는 참조 무결성 제약 조건도 함께 제거됨 

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
ALTER TABLE 테이블명 
DROP PRIMARY KEY/ UNIQUE(COLUMN)/ CONSTRAINT constraint_name [CASCADE]
</div>
```sql
-- PK 제거하기
ALTER TABLE EMP_COPY
DROP PRIMARY KEY;

-- PK 종속 까지 제거하기
ALTER TABLE EMP_COPY
DROP PRIMARY KEY CASCADE;

-- NOTNULL 제거하기
ALTER TABLE EMP_COPY
DROP CONSTRAINT EMP_COPY_ENAME_NN;
```

### DISABLE CONSTRAINT

**제약 조건을 삭제하지 않고 일시적으로 비활성화**

&#8594; 특별한 데이터를 처리하는 과정에서 무결성 제약 조건(FK)으로 인해 처리 시간이 오래 걸리는 경우가 있어서 비활성화 하는 경우가 있음

&#9656; disable 옵션은 2가지 : novalidate, validate

&#9656; novalidate : 해당 제약 조건을 무효화 시킴

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
ALTER TABLE 테이블명 
DISABLE CONSTRAINT constraint_name [CASCADE]
</div>
```sql
-- PK 제거하기
ALTER TABLE EMP_COPY
DISABLE CONSTRAINT EMP_COPY_DNO_FK;
```

### ENABLE CONSTRAINT

**제약 조건 활성화**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
ALTER TABLE 테이블명 
ENABLE CONSTRAINT constraint_name [CASCADE]
</div>
```sql
-- PK 제거하기
ALTER TABLE EMP_COPY
ENABLE CONSTRAINT EMP_COPY_DNO_FK;
```

### Check Constraints

**데이터 사전으로 제약조건을 확인할 수 있음**

```sql
select * from all_constraints
where owner = 'SCOTT'
and table_name like 'NEW_EMP%';
```
