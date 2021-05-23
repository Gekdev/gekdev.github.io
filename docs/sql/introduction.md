---
layout: default
title: Introduction
parent: SQL / Oracle
nav_order: 1
---

# SQL Introduction
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## SQL

**데이터베이스에서 데이터를 저장, 조작 및 검색하기위한 표준 언어**

&#9656; MySQL, SQL Server, MS Access, Oracle, Sybase, Informix, Postgres 및 기타 데이터베이스 시스템에서 sql이 사용됨

### What is SQL?

**Structured Query Language**

데이터베이스에 액세스하고 조작 할 수 있음

&#9656; SQL은 1986년 ANSI(American National Standards Institute)의 표준이되었고 1987년에는 ISO(International Organization for Standardization)의 표준이 됨

### What Can SQL do?

&#9656; 데이터베이스에서 **데이터를 검색**

&#9656; 데이터베이스에 대해 **쿼리를 실행**

&#9656; 데이터베이스에 **레코드를 삽입, 업데이트, 삭제**

&#9656; **새 데이터베이스 만들기**

&#9656; 데이터베이스에 **새 테이블 만들기**

&#9656; 데이터베이스에 **저장 프로 시저 만들기**

&#9656; 데이터베이스에서 **뷰를 생성**

&#9656; **테이블, 프로 시저 및 뷰에 대한 권한을 설정**

### Purpose of SQL

1. 데이터베이스 구조를 정의

2. 데이터 조회, 입력, 수정, 삭제

3. 더 빠른 데이터 검색

### Features of SQL

&#9656; 다른 시스템으로의 이식성이 좋음 (ex: python 등)

&#9656; 클라이언트/서버 구조

### SQL is a Standard?

SQL은 ANSI / ISO 표준이지만 SQL 언어에는 여러 버전이 있음

**ANSI 표준을 준수하기 위해서는 주요 명령어들은 유사한 방식으로 모두 지원함** (SELECT, UPDATE, DELETE, INSERT, WHERE)

!note
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
대부분의 SQL 데이터베이스 프로그램에는 SQL 표준 외에도 고유한 확장 기능이 있음
</div>

### Using SQL in Your Web Site

데이터베이스의 데이터를 표시하는 웹 사이트를 구축하려면 아래 4개가 필요함

1. RDBMS 데이터베이스 프로그램 (예 : MS Access, SQL Server, MySQL)

2. PHP or ASP와 같은 서버 측 스크립팅 언어

3. SQL : 원하는 데이터를 얻기 위해

4. HTML / CSS : 페이지 스타일을 지정하기 위해

### [RDBMS](https://gekdev.github.io/docs/sql/database/dbms)

**RDBMS는 관계형 데이터베이스 관리 시스템**

&#9656; RDBMS는 SQL 및 MS SQL Server, IBM DB2, Oracle, MySQL 및 Microsoft Access와 같은 모든 최신 데이터베이스 시스템의 기반

&#9656; RDBMS의 데이터는 테이블이라는 데이터베이스 개체에 저장

&#9656; 테이블은 관련 데이터 항목의 모음이며 열과 행으로 구성

---

## Representative Site

### Information

* [W3School](https://www.w3schools.com/sql/default.asp)

* [데이터베이스 기초 강의 (DQL/DML)](https://nackwon.tistory.com/95?category=796152)

* [QL 언어의 종류(DDL, DML, DCL, TCL, DQL)](https://m.blog.naver.com/PostView.naver?blogId=liccorob&logNo=10152844072&proxyReferer=https:%2F%2Fwww.google.com%2F)

* [SQL의 종류](https://webstudynote.tistory.com/46)

* [Practical Oracle SQL](https://www.apress.com/kr/book/9781484256169)

    &#9656; [github](https://github.com/Apress/practical-oracle-sql)

### Quiz

* [W3School](https://www.w3schools.com/sql/sql_quiz.asp)
