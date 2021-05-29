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

**데이터 조작어**

**테이블에 새로운 데이터를 삽입하거나 기존의 데이터를 수정하거나 삭제하기 위한 명령어의 집합**

---

## INSERT Statement

### INSERT Basic

**테이블에 새로운 데이터를 입력(추가)하기 위해 사용**

&#9656; 컬럼갯수와 값의 개수가 동수이어야 함

&#9656; 테이블의 모든 컬럼에 자료를 입력하는 경우에는 컬럼목록을 기술하지 않아도 됨 (컬럼목록이 생략되면 values절에 있는 값들이 테이블의 기본컬럼순서대로 입력)

&#9656; 컬럼과 값은 동일 데이터타입이어야 함, 형변환이 가능하다면 가능하지만 변환이 불가능하면 에러발생

&#9656; 데이터베이스에 영구적으로 데이터를 저장하기 위해 commit 명령문을 실행해야 함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
INSERT INTO 테이블명(칼럼명, ... , 칼럼N)

VALUES(값, .... 값N)
</div>
```sql
-- HIREDATE는 NULL로 들어감
INSERT INTO mytable(no, name) values(1, '홍길동');
INSERT INTO mytable(no, name) values(2, '홍길순');

INSERT INTO mytable values(1, '홍길동', sysdate);
INSERT INTO mytable(no, name, hiredate) values(2, '홍길순', sysdate);
```

### INSERT TABLE

**바로 select절을 사용해서 다른 테이블을 복사해올 수 있음(서브쿼리)**

INSERT절의 칼럼수와 서브쿼리의 칼럼수가 일치해야 함 

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
INSERT INTO 테이블명(칼럼명, ... , 칼럼N)

subquery;
</div>
```sql
-- 교수 테이블에서 교수번호가 4000보다 많은 데이터만 전체 복사
INSERT INTO professor4
select * from professor 
where profno > 4000;

--일부복사
insert into professor4
select profno, name from professor
where profno between 2000 and 2999;
```

![](ins_table.jpg)

### INSERT ALL

1. **각각의 테이블에 서로 다른 자료를 한번에 추가**

    &#9656; 각각 하는것보다 실행속도가 더 빠르다

    ```sql
    -- 1. 테이블 구조 생성
    create table ins_A_1 as select * from prof_3 where 1=2;
    create table ins_A_2 as select * from prof_3 where 1=2;

    -- 2. 테이블에 데이터 추가
    insert all
        when profno between 1000 and 1999 then into ins_A_1 values(profno, name) 
        when profno between 2000 and 2999 then into ins_A_2 values(profno, name) 
    select profno, name from professor;

    -- 3. 데이터 보기
    select * from ins_A_1;
    select * from ins_A_2;
    ```

    ![](ina.jpg)

2. **각각의 테이블에 동일 자료를 한번에 추가**

    ```sql
    -- 1. 테이블 구조 생성
    create table ins_A_1 as select * from prof_3 where 1=2;
    create table ins_A_2 as select * from prof_3 where 1=2;

    -- 2. 테이블에 데이터 추가
    insert all
        into ins_A_1 values(profno, name)
        into ins_A_2 values(profno, name)
    select profno, name from professor
    where profno between 3000 and 3999;

    -- 3. 데이터 보기
    select * from ins_A_1;
    select * from ins_A_2;
    ```

    ![](ina2.jpg)

### INSERT NULL

**해당 컬럼 값을 모르거나 확정되지 않았을 경우에는 칼럼의 값으로 NULL입력**

1. 암시적인 방법
    
    **칼럼명 리스트에 해당 칼럼을 생략**
    
    ```sql
    --LOC 칼럼 NULL
    INSERT INTO dept_copy(dno, dname)
    VALUES(30, 'SALES');
    ```

2. 명시적인 방법

    **VALUES절에 명시적으로 NULL을 입력**
    
    &#9656; 문자나 날짜 타입에 대해서는 공백 문자열을 지정할 수 있음

    ```sql
    -- 1. LOC 칼럼 NULL 지정
    INSERT INTO dept_copy
    VALUES(30, 'SALES', NULL);
    
    -- 2. 공백지정
    INSERT INTO dept_copy
    VALUES(30, 'SALES', '');
    ```

### INSERT DATA TYPE

**날짜 데이터를 입력하려면 해당 시스템에서 요구하는 기본 날짜 형식으로 입력해야 함**

&#9656; 오라클은 YYYY/MM/DD

1. 일반적인 방법

    ```sql
    INSERT INTO emp_copy
    VALUES (7000, 'CANDY', 'MANAGER', '2012/05/30', 10);
    ```

2. TO_DATE 함수

    ```sql
    INSERT INTO emp_copy
    VALUES (7000, 'CANDY', 'MANAGER',
            TO_DATE('2012, 05, 01','YYYY,MM,DD'), 10);
    ```

3. SYSDATE 함수 

    **시스템에 저장된 현재 날짜 데이터를 반환**
    
    ```sql
    INSERT INTO emp_copy
    VALUES (7000, 'CANDY', 'MANAGER', SYSDATE, 10);
    ```

---

## UPDATE Statement 

### UPDATE Basic

**테이블에 저장된 데이터를 수정하기 위한 DML**

&#9656; ,를 사용해서 여러개의 컬럼값을 변경할 수 있음

&#9656; WHERE 절을 생략하면 테이블에 있는 모든 행이 수정됨

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
UPDATE 테이블명

SET 행이름1 = 값1, 행이름2 = 값2, ...

WHERE conditions;
</div>
```sql
update emp999
set deptno = 10, sal = 0;
```

![](update.jpg)

### UPDATE with SELECT Statement

SET절에서 서브쿼리를 기술하면 서브쿼리를 수행한 결과로 내용이 변경

,로 여러개의 칼럼값을 수정할 수 있음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
UPDATE 테이블명

SET 행이름1 = **(Subquery)**, 행이름2 = **(Subquery)**, ...

WHERE conditions;
</div>
```sql
update dept_copy
set loc = (select loc from dept_copy where dno=20)
where dno = 10;
```

### Example

실습1) emp999에서 모든 사원의 급여를 10%인상하기(수정) 

```sql
update emp999
set sal = sal*1.1;
```

실습2) emp999에서 모든 사원의 입사일을 현재일(sysdate)로 수정

```sql
update emp999
set hiredate = sysdate;
```

실습3) professor에서 직급이 'assistant professor'인 사람의 bonus를 200으로 인상

```sql
update professor
set bonus = nvl(bonus, 0) + 200
	 where position = 'assistant professor';
```

실습4) professor에서 'Sharon Stone'과 직급이 동일한 교수들의 급여를 15%인상

&#9656; 서브쿼리를 이용 -> where절에 서브쿼리를 지정

&#9656; where position = (서브쿼리 즉, select문을 정의)

```sql
update professor
set pay = nvl(pay,0) * 1.5
where position = (select position from professor where name = 'Sharon Stone');
```

---

## DELETE Statement

**테이블에서 기존에 저장되어 있던 데이터를 삭제**

&#9656; where 절을 생략하면 테이블에 있는 모든 행이 삭제됨

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
DELETE [FROM] 테이블명

WHERE conditions;
</div>
```sql
-- 1. 특정 로우 삭제
delete dept_copy
where conditions;

-- 2. 모든 로우 삭제
delete dept_copy;
```

### DELETE with Subquery

```sql
DELETE emp_copy
where dno = (select dno from department where dname = 'SALES')
```

---

## MERGE Statement

**여러개의 테이블을 한개의 테이블로 병합하는 명령**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
MERGE INTO 테이블1

USING 테이블2 ON 병합조건

WHEN MATCHED THEN UPDATE SET 업데이트 할 내용

DELETE WHERE 조건절 WHEN NOT MATCHED THEN INSERT VALUES(...)
</div>
```sql
merge into charge_total tot
using charge_01 c01 on (tot.u_date = c01.u_date)
when     matched then update set tot.cust_no = c01.cust_no
when not matched then insert values(c01.u_date, c01.cust_no, c01.u_time, c01.charge);

select * from charge_total;
```

### Transcation

**여러가지의 DML 작업을 하나의 단위로 묶어서 처리하는 것을 의미**

&#9656; commit 작업을 최종적으로 확정, rollback 작업을 취소

&#9656; commit, rollback은 트랜잭션을 위해 오라클에서 제공하는 명령어

&#9656; 오라클은 트랜잭션을 기반으로 데이터의 일관성을 보장 

&#9656; 오라클 명령어 중에서 DDL과 DCL은 하나의 명령어가 하나의 트랜잭션으로 구성됨

&#9656; DML은 데이터를 일관성 있게 변경하기 위해서 하나 이상의 DML문으로 구성됨

&#9656; ALL-OR-Nothing 방식으로 처리됨, 즉 여러개의 명령어 중 하나의 명령어라도 잘못되면 전체를 취소하기 때문에 데이터의 일관성을 유지하면서 안정적으로 데이터를 복구할 수 있게 함

&#9656; 데이터의 추가, 수정, 삭제 등 데이터를 조작하는 명령어 DML은 실행됨과 동시에 트랜잭션이 진행됨, 이들 작업이 성공적으로 처리되도록 하기 위해서는 COMMIT 명령을, 취소하기 위해서는 ROLLBACK명령을 실행

&#9656; 첫번째 DML문이 실행될 때 시작되어 다음 이벤트가 발생하면 종료 

&#9656; 트랜잭션이 종료되면 실행 가능한 다음 SQL문이 다음 트랜잭션을 자동으로 시작

&#9656; DDL, DCL문이 실행되는 경우에는 자동으로 COMMIT되고 오라클이 종료되면 자동으로 ROLLBACK됨

* COMMIT 

    **모든 작업들을 정상적으로 처리하겠다고 확정하는 명령어**
    
    &#9656; 트랜잭션의 처리 과정을 데이터베이스에 모두 반영하기 위해서 변경된 내용을 모두 영구 저장
    
    &#8594; commit 명령어를 수행하게 되면 하나의 트랜잭션 과정을 종료
    
* ROLLBACK

    **작업 중 문제가 발생해 트랜잭션 처리 과정에서 발생한 변경 사항을 취소하는 명령어**
    
    &#9656;  트랜잭션으로 인한 하나의 묶음 처리가 시작되기 이전의 상태로 되돌림
    
    &#8594; ROLLBACK역시 트랜잭션 과정을 종료하게 됨
    
예제1. 내용 복구 가능
{: .label .label-purple .mt-2}
```sql
delete dept_copy;

ROLLBACK

select * from dept_copy;
```

예제2. 내용 복구 불가능
{: .label .label-purple .mt-2}
```sql
-- 내용 복구 불가능
delete dept_copy;

COMMIT

ROLLBACK

select * from dept_copy;
```

---

## Example

Q1.

테이블명 : STAR_WARS (영화 정보를 저장한다)

컬럼 : EPISODE_ID : 에피소드 아이디로써, 숫자형 타입으로 기본 키가 된다.

EPISODE_NAME : 에피소드에 따른 영화 제목, 가변길이문자형(50 BYTE)이다.

OPEN_YEAR : 개봉년도로써, 숫자형 타입이다.

```sql
create table star_wars(
      episode_id       number(5,0)  not null
   , episode_name   varchar2(50)
   , open_year         number(5,0)
   , constraint star_wards_pk primary key(episode_id)
);
```


Q2. 

테이블명 : CHARACTERS ( 등장인물 정보를 저장한다)

컬럼 : CHARACTER_ID   : 등장인물 아이디로써, 숫자형 타입(5자리), 기본키

CHARACTER_NAME : 등장인물 명으로 가변 길이 문자형 타입(30 BYTE)이다.

MASTER_ID      : 등장인물이제다이일 경우 마스터아이디값, 숫자형(5자리)

ROLE_ID        : 등장인물의 역할 아이디로써, INTEGER 타입이다.

EMAIL          : 등장인물의 이메일 주소로 varchar2(40 BYTE)이다.

```sql
create table characters(
      character_id      number not null
   , character_name    varchar2(30)
   , master_id          number(5)
   , role_id             number(5)
   , email                varchar2(40)
   , constraint characters_pk primary key(character_id)   
);
```

Q3. 

테이블명 : CASTING ( 등장인물과 실제 배우의 정보를 저장한다)

컬럼 : EPISODE_ID: 에피소드 아이디로써, 숫자형 타입(5자리)으로 기본키

CHARACTER_ID: 등장인물 아이디로써, 숫자형 타입(5자리)이며 참조키

REAL_NAME : 등장인물의 실제 이름으로, varchar2(30 BYTE)이다.

```sql
create table casting(
      episode_id       number(5) not null
   , character_id   number(5) not null
   , real_name         varchar2(30)
   , constraint casting_pk primary key(episode_id, character_id)   
);
```

Q4. 

INSERT 문을 사용하여 STAR_WARS 테이블에 다음과 같이 데이터를 저장해보자. 

| EPISODE_ID  | EPISODE_NAME                          |    OPEN_YEAR  |
|:-----------|:---------------------------------------|:--------------|                
| 1           |   보이지 않는 위험(The Phantom Menace)   |       1999    |               
| 2           |   클론의 습격(Attack of the Clones)      |       2002   |                
| 3           |   시스의 복수(Revenge of the Sith)       |       2005   |
| 4           |   새로운 희망(A New Hope)                |       1977   |                
| 5           |   제국의 역습(The Empire Strikes Back)   |       1980   |                
| 6           |   제다이의 귀환(Return of the Jedi)      |       1983    |

```sql
insert into star_wars values(1, '보이지 않는 위험(The Phantom Menace)', 1999 );
insert into star_wars values(2, '클론의 습격(Attack of the Clones)', 2002);
insert into star_wars values(3, '시스의 복수(Revenge of the Sith)', 2005);
insert into star_wars values(4, '새로운 희망(A New Hope)', 1977); 
insert into star_wars values(5, '제국의 역습(The Empire Strikes Back) ', 1980);
insert into star_wars values(6, '제다이의 귀환(Return of the Jedi)', 1983);
select * from star_wars;
```

Q5. 

CHARACTERS 테이블에 다음의 데이터를 저장해보자.

| CHARACTER_ID  |  CHARACTER_NAME       |EMAIL                   |                 
|:--------------|:---------------------|:------------------------| 
| 1             |    루크 스카이워커      |    luke@jedai.com        |                   
| 2             |    한 솔로             |     solo@alliance.com    |                    
| 3             |    레이아 공주          |    leia@alliance.com     |                   
| 4             |    오비완 케노비        |    Obi-Wan@jedai.com     |                   
| 5             |    다쓰 베이더          |    vader@sith.com         |                  
| 6             |    다쓰 베이더(목소리)   |    Chewbacca@alliance.com |                  
| 7             |    C-3PO              |     c3po@alliance.com     |                   
| 8             |    R2-D2              |     r2d2@alliance.com     |                   
| 9             |    츄바카              |     Chewbacca@alliance.com |                  
| 10           |     랜도 칼리시안|                                   |
| 11            |    요다(목소리)         |     yoda@jedai.com      |                     
| 12            |    다스 시디어스|                               |
| 13            |    아나킨 스카이워커    |    Anakin@jedai.com       |                  
| 14            |    콰이곤 진| |
| 15            |    아미달라 여왕| |
| 16            |    아나킨 어머니| |
| 17            |    자자빙크스(목소리) |       jaja@jedai.com |
| 18            |    다스 몰          | |
| 19           |     장고 펫 | |
| 20             |   마스터 윈두       |       windu@jedai.com      |                    
| 21            |    듀크 백작         |       dooku@jedai.com |

```sql
select * From characters
insert into characters(character_id, character_name, email) 
   values(1, '루크 스카이워커', 'luke@jedai.com');
insert into characters(character_id, character_name, email) 
   values(2, '한 솔로', 'solo@alliance.com');
insert into characters(character_id, character_name, email) 
   values(3, '레이아 공주', 'leia@alliance.com');
insert into characters(character_id, character_name, email) 
   values(4, '오비완 케노비', 'Obi-Wan@jedai.com');                               
insert into characters(character_id, character_name, email) 
   values(5, '다쓰 베이더', 'vader@sith.com');
insert into characters(character_id, character_name, email) 
   values(6, '다쓰 베이더(목소리)', 'Chewbacca@alliance.com');
insert into characters(character_id, character_name, email) 
   values(7, 'C-3PO', 'c3po@alliance.com');                                   
insert into characters(character_id, character_name, email) 
   values(8, 'R2-D2', 'r2d2@alliance.com');
insert into characters(character_id, character_name, email) 
   values(9, '츄바카', 'Chewbacca@alliance.com');
insert into characters(character_id, character_name, email) 
   values(10, '랜도 칼리시안', null);
insert into characters(character_id, character_name, email) 
   values(11, '요다(목소리)', 'yoda@jedai.com');
insert into characters(character_id, character_name, email) 
   values(12, '다스 시디어스', 'Anakin@jedai.com');
insert into characters(character_id, character_name, email) 
   values(13, '아나킨 스카이워커', null);
insert into characters(character_id, character_name, email) 
   values(14, '콰이곤 진', null);
insert into characters(character_id, character_name, email) 
   values(15, '아미달라 여왕', null);
insert into characters(character_id, character_name, email) 
   values(16, '아나킨 어머니', null);
insert into characters(character_id, character_name, email) 
   values(17, '자자빙크스(목소리)', 'jaja@jedai.com');
insert into characters(character_id, character_name, email) 
   values(18, '다스 몰', null);
insert into characters(character_id, character_name, email) 
   values(19, '장고 펫', null);
insert into characters(character_id, character_name, email) 
   values(20, '마스터 윈두', 'windu@jedai.com');
insert into characters(character_id, character_name, email) 
   values(21, '듀크 백작', 'dooku@jedai.com');
```

Q6. 

ROLES 테이블에 다음의 데이터를 저장해보자

ROLE_ID(number5,0) pk, ROLE_NAME(varchar2 30)

```sql
create table roles (
         role_id number(5) primary key not null
      , role_name varchar2(30)
);
```

| ROLE_ID            |   ROLE_NAME                   |   
|:-------------------|:------------------------------| 
| 1001               |    제다이                       |  
| 1002               |    시스                        |   
| 1003                |   반란군 |

```sql
INSERT INTO ROLES ( ROLE_ID, ROLE_NAME ) VALUES (1001, '제다이');
INSERT INTO ROLES ( ROLE_ID, ROLE_NAME ) VALUES (1002, '시스');
INSERT INTO ROLES ( ROLE_ID, ROLE_NAME ) VALUES (1003, '반란군');
select * from roles;
```

Q7. 

CHARACTERS 에는 ROLE_ID 란 컬럼, 이 값은 ROLES 테이블의 ROLE_ID 값을 참조 

CHARACTERS 변경하여 ROLE_ID 컬럼이 ROLES의 ROLE_ID 값을 참조하도록 참조 키를 생성

```sql
alter table characters
  add constraint characters_fk foreign key(role_id) references roles(role_id);
```

Q8. 

참조 키를 생성후, 다음으로 CHARACTERS 테이블의 ROLE_ID 값을 변경해보자. 

값의 참조는 ROLES 테이블의 ROLE_ID 값을 참조한다. 예를 들면 루크 스카이워커,   

오비완 캐노비, 요다 등은 제다이 기사이므로 1001 값을 가질 것이며, 

다쓰 베이더, 다쓰 몰은 시스 족이므로 1002에 해당한다. 자신이 아는 범위 내에서 

이 값을 갱신하는 UPDATE 문장을 작성해 보자.

```sql
update characters
    set role_id = 1001
 where character_id in (1, 4, 11, 13, 14, 20, 21);
 
update characters
    set role_id = 1002
 where character_id in (5,6,12,18); 

update characters
    set role_id = 1003
 where character_id in (2,3,7,8,9); 
 
select * from characters;
```

Q9.

CHARACTERS MASTER_ID 란 컬럼, 이 컬럼의 용도는 EMPLOYEES 테이블의 MANAGER_ID 

와 그 역할이 같다. 즉 제다이나 시스에 속하는 인물 중 그 마스터의 CHARACTER_ID 값을 

찾아 이 컬럼에 갱신하는 문장을 작성

| 제자               |    마스터                 |
|:------------------|:-------------------------|
| 아나킨 스카이워커    | 오비완 캐노비            |
| 루크 스카이워크      | 오비완 캐노비        |
| 마스터 윈두        |   요다                   |
| 듀크 백작          |   요다                     |
| 다쓰 베이더        |   다쓰 시디어스             |
| 다쓰 몰           |    다쓰 시디어스           |
| 오비완 캐노비      |   콰이곤 진                |
| 콰이곤 진         |    듀크 백작              |

```sql
update characters set master_id = 4 where character_id = 13;
UPDATE CHARACTERS
   SET MASTER_ID = 4
 WHERE CHARACTER_ID = 1;
 
UPDATE CHARACTERS
   SET MASTER_ID = 11
 WHERE CHARACTER_ID = 20; 
 
UPDATE CHARACTERS
   SET MASTER_ID = 11
 WHERE CHARACTER_ID = 21;  
 
UPDATE CHARACTERS
   SET MASTER_ID = 12
 WHERE CHARACTER_ID = 5;  

UPDATE CHARACTERS
   SET MASTER_ID = 12
 WHERE CHARACTER_ID = 18;  
 
UPDATE CHARACTERS
   SET MASTER_ID = 14
 WHERE CHARACTER_ID = 4;  
 
UPDATE CHARACTERS
   SET MASTER_ID = 21
 WHERE CHARACTER_ID = 14; 
```

Q10.

CASTING의 PK는 EPISODE_ID와 CHARACTER_ID 이다. 

이 두 컬럼은 각각 STAR_WARS와 CHARACTERS 테이블의 기본 키를 참조하고 있다. 

CASTING 테이블에 각각 이 두 테이블의 컬럼을 참조하도록 참조 키를 생성 

```sql
alter table casting
  add constraint casting_episode_id_fk 
       foreign key(episode_id)
         references star_wars(episode_id);

alter table casting
  add constraint casting_character_id_fk 
       foreign key(character_id)
         references characters(character_id);
         
select * from casting;
```

Q11.  

다음 문장을 실행해 보자

```sql
DELETE ROLES
 WHERE ROLE_ID = 1001;
```

이 문장을 실행하면 그 결과는 어떻게 되는가? 또한 그러한 결과가 나오는 이유는 무엇인지 설명해 보자.


Q12.  

characters에 character_name 인덱스 생성하기

```sql
create index characters_ix_01 on characters(character_name);
```

Q13.

상기작업들의 data dictionary를 조회

```sql
select * from user_constraints;
select * from user_indexes where table_name = 'CHARACTERS';
```