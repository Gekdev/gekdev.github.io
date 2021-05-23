---
layout: default
title: Join
parent: SQL / Oracle
nav_order: 6
---

# SQL Table Join
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## JOIN

**조인은 여러 테이블에 저장된 테이블을 한번에 조회해야 할 필요가 있을 때 사용**

### Cartesian Product

**카디시안 곱**

&#9656; 조인 조건을 생략 한 경우 행의 모든 조합을 표시하는 카디시안 곱이 생성

&#9656; 조인 결과가 의미를 가지려면 조인할 때 조건을 지정해야 함

### ANSI JOIN

EQUI JOIN, NON-EQUI JOIN, OUTER JOIN, SELF JOIN등을 오라클 9i부터는 **ANSI 표준 SQL 조인 구문으로 제공해 줌**

&#9656; ANSI 표준 SQL 조인 구문은 현재 대부분의 사용 데이터베이스 시스템에서 표준 언어로 ANSI(미국 표준 연구소) SQL 에서 제시한 표준 기능을 준수하고 있음

&#9656; 다른 DBSM와 호환이 가능하기 때문에 잘 알아둬야 함

---

## EQUI JOIN

### EQUI JOIN Syntax

**조인 대상 테이블에서 공통 칼럼을 = 비교를 통해 같은 값을 가지는 행을 연결하여 결과를 생성하는 조인 방법**

&#9656; 여러 테이블의 데이터를 질의하는 방법은 WHERE 절을 이용하는 것

&#9656; 가장 많이 사용되는 JOIN

&#9656; 칼럼명이 같으면 혼란이 오기 때문에 칼럼명 앞에 테이블 명을 기술해야 함 (중복되지 않았다면 테이블 명을 기술하지 않아도 됨)

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**select table1.column, table2.column

from table1, table2 -- 조인 대상 테이블을 기술하고 ,로 구분

where table1.column1 = table.column2;** -- =를 사용해 조인 조건 기술(기본 키와 외래 키에 공통적으로 존재하는 칼럼)
</div>
```sql

```

### Alias Rules

1. 테이블의 별명은 30자까지 가능하지만, 길지 않게 작성

2. from 절에서 테이블명을 명시하고 공백을 둔 다음 테이블 별칭을 지정

3. 하나의 sql명령문에서 테이블명과 별명을 혼용할 수 없음

4. 테이블의 별칭은 해당 SQL 명령문 내에서만 유효함

### NATURL JOIN

**where절을 사용하지 않고 natural join키워드를 사용하면 오라클에서 자동적으로 테이블의 모든 칼럼을 대상으로 일치하는 데이터 유형 및 이름을 가진 공통 칼럼을 조사한 후에 자동으로 조인을 수행**

&#9656; 오라클 9i 이전에 equi join으로 사용하던 것을 대신해서 사용하는 조인방식

&#9656; 조인 칼럼에 테이블 별칭을 사용하면 오류가 발생

&#9656; 조인에 참여하는 두 테이블 모두에서 동일한 이름과 테이블 유형을 가진 칼럼이 존재해야 한다는 점에 주의

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
select table1.column, table2.column

from table1 **natural join** table2;
</div>
```sql



```

---

## NON-EQUI JOIN

---

## SELF JOIN

---

## OUTER JOIN