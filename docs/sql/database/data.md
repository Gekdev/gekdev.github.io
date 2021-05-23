---
layout: default
title: Data
parent: Database
grand_parent: SQL / Oracle
nav_order: 1
---

# Database Data 
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Classification of data (Bigdata)

정형 데이터와 비정형 데이터는 서로 배척관계가 아님

### Structured Data

**정형 데이터**

&#9656; 구조화된 데이터, 즉 미리 정해진 구조(schema)에 따라 저장된 데이터

ex) 엑셀의 스프레드시트, 관계 데이터베이스의 테이블

### Semi-structured Data

**반정형 데이터**

&#9656; 구조에 따라 저장된 데이터이지만, 데이터 내용 안에 구조에 대한 설명이 함께 존재

&#9656; 구조 파악하는 파싱(parsing) 과정 필요

&#9656; 보통 파일 형태로 저장

ex) HTML, XML, JSON 문서, 웹 로그, 센서 데이터

### Unstructured Data

**비정형 데이터**

&#9656; 정해진 구조가 없이 저장된 데이터

ex) 소셜 데이터의 텍스트, 영상, 이미지, 워드, PDF 문서 등의 멀티미디어 데이터

![](https://gekdev.github.io/docs/sql/database/example/datatype3.png)
{: .mt-3}

---

## Database datas

### Database Datatype

**데이터베이스에 저장할 수 있는 데이터는 타입을 가짐**

&#8594; 데이터를 삽입할 때 이를 유의해야 함

![](https://gekdev.github.io/docs/sql/database/example/db_datatype.png)

### Data Integrity Constraints

데이터 무결성 제약 조건

**칼럼에 들어가는 값을 제한하여 데이터의 정확성과 일관성을 보장해야 함**

ex) 대학교에 학생 정보를 저장하는 테이블에서 그 학교 학생이라면 무조건 학번을 가져야 하고, 한 학생이 가지는 유일한 값이 되어야 함

#### NOT NULL 제약 조건

&#9656; NULL = 어느 값도 정해지지 않은 불확실한 값

**테이블에 무조건 입력해야 하는 필수 입력 컬럼을 NOT NULL제약 조건으로 걸어줌**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
NOT NULL
</div>
```sql
ex) CREATE TABLE emp(
    ename VARCHAR2(20) NOT NULL,
    empno NUMBER(5) NOT NULL
);

-- 테이블 생성 시 NOT NULL을 입력해 제약 조건을 걸 수 있음
```

#### 기본키 제약 조건

**칼럼이 동일한 값을 가질 수 없도록 제약 조건을 걸어주는 것**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
PRIMARY KEY
</div>
```sql
CREATE TABLE emp(
    snum NUMBER(5) PRIMARY KEY
);

-- 테이블 생성 시 기본키에 해당하는 컬럼명 뒤에 primary key를 입력
```

#### 외래 키 제약 조건

관계형 데이터베이스는 데이터가 중복되는 것을 막기 위해 정보를 여러 테이블에 나눠 저장해 두었다가 원하는 정보를 얻기 위해 여러 테이블을 연결하여 사용

**특정 테이블의 칼럼이 다른 테이블의 칼럼을 참조하게 되는 경우가 생김, 이러한 칼럼을 외래키라고 함**

예시
{: .label .label-purple .mt-2}
<div class="code-example" markdown="1">
예를 들어 회사 사원 테이블에는 사원에 대한 정보와 부서번호/부서명 칼럼이 존재할 것입니다. 하지만 부서에 대한 정보는 담고 있지 않습니다. 부서에 대한 정보는 부서테이블에 정보가 담겨 있겠죠.

그렇다면 사원 테이블의 부서번호와 부서 테이블의 부서번호가 서로 연결이 된다는 것을 알 수 있습니다.

만약 사원 테이블의 부서번호와 부서 테이블의 부서번호가 일치되는 것이 없다면 부서 정보를 얻어오는데 문제가 발생합니다. 

그래서 서로 참조할 수 있도록 제약을 걸어 둔 것이 외래키 제약 조건
</div>

