---
layout: default
title: TCL
parent: Commands
grand_parent: SQL / Oracle
nav_order: 4
---

# TCL Commands
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## TCL 

**트랜잭션 제어언어**

Transaction Control Language

### Transcation Basic

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
