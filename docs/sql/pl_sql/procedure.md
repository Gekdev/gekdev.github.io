---
layout: default
title: Procedure
parent: PL/SQL
grand_parent: SQL / Oracle
nav_order: 3
---

# PL/SQL Procedure
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## PL/SQL Procedure

### What is Procedure?

**작업을 수행하는 명명된 PL/SQL블록**

반복실행을 위한 DB객체로서 DB에 저장

매개변수를 가질 수 있고 호출될 수 있음

머리말, 선언부, 실행부, 예외처리부로 구성

재이용성, 유지가능성을 높여줌

### Procedure Basic

syntax
{: .label .mt-2}
```sql
CREATE OR REPLACE PROCEDURE 프로시저 이름
    ( 매개변수명1[ IN | OUT | IN OUT ] 데이터타입[:= 디폴트값],
    매개변수명2[ IN | OUT | IN OUT ] 데이터타입[:= 디폴트값], ... )
IS[AS]
    변수, 상수 등 선언
BEGIN
    실행
    [EXCEPTION 예외처리부]
END [프로시저 이름]
```

### 매개변수의 스코프

IN = 프로시저 내부에서 참조만 가능, 값 할당 불가, 상수나 리터럴 문자를 전달할 수 있다. 매개변수 타입을 지정하지 않으면 디폴트로 IN으로 설정된다.

OUT = 값 할당 가능. 전달받기 불가

IN OUT = 참조와 값 할당 모두 가능.

** OUT, IN OUT 매개 변수에는 디폴트값 설정 불가, 반드시 변수에 값을 담아서 전달해야 함.

### 매개변수 전달 방법
### Delete Procedure
