---
layout: default
title: DDL
parent: Commands
grand_parent: SQL / Oracle
nav_order: 1
---

# DDL Commands
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## DDL Basic

### create Statement

테이블 생성 create

1. 문법
create table 테이블명 (
  컬럼명1 데이터타입(크기),
  ...
  컬럼명n 데이터타입(크기)
);

2. 데이터타입

  1) 문자형

        a. char(n)     : 고정길이 / 최대 2KB / 기본크기 1byte
        b. varchar2(n) : 가변길이 / 최대 4KB / 기본크기 1byte
        c: long        : 가변길이 / 최대 2GB

   2) 숫자형

      a. number(p,s) : 가변숫자 / p(1~38 기본값=38), s(-84~127 기본값=0) / 최대 22bytes
        b. float(p)    : number하위타입 / p(1~128 기본값=128) / 최대 22bytes    

   3) 날짜형

      a. date      : bc 4712.01.01 ~ 9999.12.31까지 연,월,시,분,초까지 입력가능
        b. timestamp : 연,월,일,시,분,초,밀리초까기 입력이 가능

   4) lob타입 : LOB란 Large Object의 약자로 대용량 데이터를 저장할 수 있는 데이터
       타입이아. 일반적으로 그래프, 이미지, 사운드등 비정형 데이터를 저장할 때 LOB
        타입을 사용한다.

        문자형 대용량 데이터는 CLOB나 NLOB를 사용하고 그래프,이미지,동영상등의 데이터
        는 주로 BLOB를 주로 사용한다. 

        a. clob  : 문자형 대용량 객체, 고정길이와 가변길이 문자형을 지원
        b. blob  : 이진형 대용량 객체 주로 멀티미디어자료를 저장
        c. bfile : 대용량 이진파일에 대한 파일의 위치 및 이름을 저장
   
*/
/* A. 테이블생성하기 */
create table mytable(
		no number(3,1)
		 , name varchar2(10)
     , hiredate date
);

select * from mytable;

insert into mytable;

--- 식별자는 한글이름도 가능 / 비추천 
create table 마이테이블(
		번호 number(3)
		, 이름 varchar2(10)
		, 입사일 date
);
insert into 마이테이블 

select * from 마이테이블;

/* 테이블생성시 제한사항
   1. 테이블이름은 반드시 문자로 시작해야 한다. 중간에 숫자가 포함되는 것은 가능하다.
   2. 특수문자도 가능하지만 테이블생성시이 큰따옴표로 감싸야 한다. 하지만 권장하지는 않는다.
   3. 테이블이름이나 컬럼이름은 최대 30byte까지 가능(즉, 한글은 15자리까지만 가능)
   4. 테이블명은 중복할 수가 없다.
   5. 테이블명이나 컬럼이름에는 오라클키워드를 사용하지 않기를 권장
      (하지만 절대로 사용하지 마세요!!!!)
*/


---1/ 테이블에 자료를 추가 
-- insert into table(열명1,....열명n) values(값1,...값n) 열과 값의 갯수가 일치해야 함
-- insert 명령은 컬럼갯수와 값의 개수가 동수이어야 함
-- 또한, 컬럼과 값은 동일 데이터타입이어야 함, 형변환이 가능하다면 가능하지만 변환이 불가능하면 에러발생

insert into mytable(name) vales('소향');
insert into mytable(no, name) values(1, '홍길동');
insert into mytable(no, name) values(2, '홍길순');
insert into mytable(no, name) values(2, '홍길차');
insert into mytable(no, name, hiredate) values(4, '홍길녀', sysdate);
insert into mytable values(5, '홍길군', sysdate); --기본 형식에 맞춰서 들어가짐
insert into mytable values(6, 1000, sysdate); -- 자동형변환
insert into mytable values(7, '김소향', '20210521'); -- 자동형변환

insert into mytable(name) values('소향',1); --error
insert into mytable values(6, '홍길'); --error
insert into mytable(no, name) values(999.9, '홍길리'); --error
insert into mytable(no, name) values('문자', '홍길리'); --error
insert into mytable(no, name) values('문자', '홍길리'); --error
insert into mytable(no, name, hiredate) values(4, '홍길녀', 12345);  --데이터 타입error

select * from mytable;

--2. 테이블 복사
-- emp 테이블을 temptable 복사
select * from temptable;

create table temptable
as
select * from emp;

select * from temptable;

--테이블 구조만 복사
create table temptable1
as
select * from emp
where 1=2;
select * from temptable1;

--특정 자료만 복사할 경우
create table temptable2
as
select * from emp
where deptno = 10;
select * from temptable2;

--B. 테이블 컬럼을 수정
create table dept6 as select * from dept2;
select * from dept6;

--1. 컬럼 추가 dept6에 location varchar2()로 추가
alter table dept6 add(location varchar2(1));

--2. 컬럼 명 변경
alter table dept6 rename column location to loc;

--3. 데이터 타입을 변경
alter table dept6 modify(dname number) -- 데이터 값이 변경되기 위해서는 모두 비어야함
alter table dept6 modify(loc number);

select * from dept6;

--오라클의 테이블 정보 보기
select * from all_tab_columns
where table_name = 'DEPT6';

--칼람 추가시 기본값설정하기
create table dept7 as select * from dept2;
select * from dept7;

alter table dept7 add(lovation varchar2(10) default '서울');
select * from dept7;
alter table dept7 add(xxx number default 0);
alter table dept7 add(hiredate date number sysdate);

-- 6.컬럼크기를 수정하기
-- location 10를 1자리로 수정
alter table dept7 modify(location )
