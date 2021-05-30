---
layout: default
title: PL/SQL
parent: SQL / Oracle
nav_order: 12
has_children: true
---

# PL/SQL
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## PL/SQL Basic

### What is PL/SQL

**Oracle's Procedural Language Extension To SQL**

**SQL의 확장된 개념으로 ORACLE에서 지원하는 프로그래밍 언어의 특성을 수용한 SQL의 확장**

SQL에서는 사용할 수 없는 절차적 프로그래밍 기능을 가지고 있음

PL/SQL Block내에서 SQL DML문과 Query문, 절차형 언어(if, loop)등을 사용하여 절차적 프로그래밍을 가능하게 한 강력한 트랜잭션 언어

블록 구조로 이루어지며, PL/SQL 자신이 컴파일 엔진을 포함하고 있음

### Advantage of PL/SQL

1. Block 구조로 다수의 SQL문을 한번에 ORACLE DB로 보내서 처리하므로 수행속도 향상

2. 모든 요소는 하나 또는 두개 이상의 블록으로 구성하여 모듈화가 가능

3. 보다 강력한 프로그램을 작성하기 위해 큰 블록안에 소블럭을 위치시킬 수 있음

4. Variable, Constant, Cursor, Exception 을 정의하고 SQL문장과 Procedural 문장에서 사용

5. 단순, 복잡한 데이터 형태의 변수를 선언

6. 테이블의 데이터 구조와 Database의 컬럼에 준하여 동적으로 변수를 선언할 수 있음

7. Exception 처리 루틴을 이용해 Oracle Server Error를 처리할 수 있음

8. 사용자 정의 에러를 선언하고 Exception 처리 루틴으로 처리할 수 있음

### Structure of PL/SQL

**논리적인 블록으로 이루어진 구조화된 블록 언어로써 세개의 섹션으로 구성됨**

![](https://gekdev.github.io/docs/sql/pl_sql/example/unnamed.png)

1. DECLARE (선언부)

    **DECLARE문으로 시작하며 블록에서 사용될 변수, 상수, 커서, 예외를 선언하는 섹션**

    &#9656; 필요하지 않으면 생략할 수 있는 선택적 섹션

    &#8594;변수선언, 상수선언, 커서선언, EXCEPTION 선언

2. BEGIN (실행부)

    **BEGIN 문으로 시작하여 END; 문으로 종료하며 수행될 작업의 몸체**

    &#9656; SQL문, 제어문, 반복문, 커서속성 등을 이용하여 블록에서 실행할 몸체를 구성

    &#9656; 생략할 수 없는 필수적 섹션

    &#8594;SELECT/UPDATE, INSERT, DELETE, IF, LOOP, CURSOR

3. EXCETION (예외처리부)

    **END; 문 바로 앞에 위치**

    &#9656; 미리 정의된 예외를 추적하고 명시된 조건이 발생할 경우에 취할 작업을 정의

    &#9656; 필요하지 않으면 생략할 수 있는 선택적 섹션

    &#8594;미리 정의된 예외, 사용자정의 예외, EXCEPTION 함수(SQLCODE, SQLERRM)

NOTE
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
DECLARE, BEGIN EXCEPTION문은 세미콜론 붙으면 안됨

END문과 모든 PL/SQL문장은 줄의 마지막에 세미콜론이 붙음
</div>

### How to write PL/SQL

1. PL/SQL 블록 내에서는 한 문장이 종료될 때마다 세미콜론을 사용

2. END; 사용해 하나의 블록이 끝났다는걸 명시

3. PL/SQL블록의 작성은 편집기를 통해 파일로 작성할 수도 있고, 프롬프트에서 바로 작성도 가능

4. 주석은 SQL과 동일

5. 쿼리문을 수행하기 위해 반드시 '/'가 입력되어야 하며, PL/SQL블록은 행에 /가 있으면 종결된 것으로 간주

### Output Results

PUT_LINE : 화면 출력을 위해 사용하는 오라클에서 제공하는 프로시져, DBMS_OUTPUT패키지에 묶여있음

따라서 **DBMS_OUTPUT.PUT_LINE으로 사용해야함**

오라클에서 제공하는 프로시저를 사용하여 출력되는 내용을 화면에 보여주기 위해서는 환경 변수 SERVEROUTPUT(DEFAULT OFF)를 ON으로 변경해야함

메세지 출력하기
{: .label .mt-2}
```sql
set serveroutput on
begin 
    dbms_output.put_line('Welcome to Oracle!');
end;
/
```

---

## Variable Declare





---

## Sub-Program

**하나의 프로그램을 구성하는 여러 작은 단위의 프로그램**

일련의 명령문을 모아두고, 이를 외부에서 호출할 수 있게 한 구조

보통 프로그래밍 언어에서 Function에 해당함

PL/SQL의 대표적인 부 프로그램에서는 Function, Procedure가 있음

![](https://gekdev.github.io/docs/sql/pl_sql/example/func_pro.jpg)

---

[Enjoy My Life](https://m.blog.naver.com/kmymk/110081331981)

[호기심 많은 오리의 지식 저장소](https://gdtbgl93.tistory.com/149)







