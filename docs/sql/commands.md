---
layout: default
title: Commands
parent: SQL / Oracle
nav_order: 4
has_children: true
---

# SQL Commands
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

### [Select 문]()

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
