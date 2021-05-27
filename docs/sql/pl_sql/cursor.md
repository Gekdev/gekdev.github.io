---
layout: default
title: Cursor
parent: PL/SQL
grand_parent: SQL / Oracle
nav_order: 3
---

# PL/SQL Cursor
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## PL/SQL Cursor

### What is Cursor?

 1. Cursor(커서)?
   
      오라클 서버는 SQL문을 실행하고 처리한 정보를 저장하기 위헤 'Private 
       SQL Area'라는 메모리 작업공간을 이용한다. 이 영역에 이름을 부여하고
       저장된 정보를 처리할 수 있게 해주는 데 이를 커서(Cursor)라고 한다.
       
       Cursor는 DML문과 select문에 의해 내부적으로 선언되는 묵시적커서와 
       명시적커서가 있다. 
       
       PL/SQL에서 select문은 한개의 row만 검색할 수 있기 때문에 하나 이상의
       row를 검색하기 위해서는 명시적 커서를 사용해야 한다. 
       
       묵시적커서의 경의 pl/sql블럭의 begin..end에 sql문이 있다면 pl/sql은
       "SQL"이라는 이름의 커서를 자동을 생성한다.
   
   2. Cursor종류
      
       1) 암시적(Implicit)커서
       
          암시적커서는 오라클이나 pl/sql실행 매커니즘에 의해 처리되는 SQL문장이
            처리되는 곳에 대한 익명의 주소이다. 오라클데이터베이스에서 실행되는
            모든 SQL문장은 암시적인 커서가 생성이 되면 커서속성을 사용할 수 있다.
            암시적커서는 SQL문이 실행되는 순간에 자동으로 open과 close를 실행한다.
       
           암시적커서의 속성은
            
            a. SQL%rowcount : 해당 sql문에서 영향을 받는 행의 수
            b. SQL%found    : 해당 sql문에서 행의 수가 한개 이상일 때 true를 리턴
            c. SQL%notfound : 해당 sql문에서 행의 수가 없을 경우에 true를 리턴
            d. SQL%isopen   : 항상 false, 암시적커서가 열려있는지 여부를 검색
                        
       2) 명시적(Explicit)커서
  
         프로그래머에 의해 선언되고 이름이 부여된 커서를 말한다.
            명시적커서의 진행순서는 "선언 -> open -> fetch -> close"로 진행한다.
            
            a. 문법 : cusor 커서명 is select문
            b. 커서명령
               a) 커서열기(open)
                
                    ... 커서의 열기는 open문을 사용
                     ... 커서안의 검색이 실행되면 데이터가 추출되진 않아도 에러는 
                         발생하지 않는다.
                    ... 문법 : open 커서명;
                
                b) 커서패치(fetch)
                
                   ... 커서의 fetch는 현재 데이터행을 output변수에 반환 
                     ... 커서의 select문의 컬럼수와 output변수의 수가 동일 해야 한다.
                     ... 커서컬럼의 타입과 output변수의 타입은 동일해야 한다.
                    ... 커서는 한라인씩 데이터를 fetch한다.
                    ... 문법 : fetch 커서명 into 변수1...변수n   
                     
                c) 커서닫기(close)
                
                   ... 사용이 끝난 커서는 반드시 닫아 주어야 한다.
                     ... 필요할 경우 커서를 다시 오픈할 수 있다.
                     ... 커서를 닫은 경우에는 fetch할 수 없다.
                     ... 문법: close 커서명;
   