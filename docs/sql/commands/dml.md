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

### 

---

## MERGE Statement

### 

