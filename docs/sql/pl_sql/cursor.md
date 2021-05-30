---
layout: default
title: Cursor
parent: PL/SQL
grand_parent: SQL / Oracle
nav_order: 2
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

오라클 서버는 SQL문을 실행하고 처리한 정보를 저장하기 위헤 'Private SQL Area'라는 메모리 작업공간을 이용, 이 영역에 **이름을 부여하고 저장된 정보를 처리할 수 있게 해주는 데 이를 커서(Cursor)라고 함**

&#9656; 커서는 SELECT문의 수행 결과가 여러개의 로우로 구해지는 경우에 모든 로우에 대해 처리를 하려면 커서를 사용해야 함

&#9656; Cursor는 DML문과 SELECT문에 의해 내부적으로 선언되는 묵시적커서와 명시적커서가 있음 

&#9656; PL/SQL에서 SELECT문은 한개의 row만 검색할 수 있기 때문에 하나 이상의 row를 검색하기 위해서는 명시적 커서를 사용해야 함

&#9656; 묵시적커서의 경의 pl/sql블럭의 begin..end에 sql문이 있다면 pl/sql은 "SQL"이라는 이름의 커서를 자동을 생성

![](cursorbasic.jpg)

---

## Implicit Cursor

**묵시적(Implicit)커서**

&#9656; 묵시적커서는 오라클이나 pl/sql실행 매커니즘에 의해 처리되는 SQL문장이 처리되는 곳에 대한 익명의 주소

&#9656; 오라클데이터베이스에서 실행되는 모든 SQL문장은 묵시적인 커서가 생성이 되면 커서속성을 사용

&#9656; 묵시적커서는 SQL문이 실행되는 순간에 자동으로 open과 close를 실행

묵시적 커서는 세션 내에 단 한개만 선언되ㄴ어 사용되었다가 문장이 종료됨가 동시에 정리

묵시적 커서에 저장되는 데이터는 1행만 가능하며, 여러 행을 저장해서 작업해야 할 경우에는 묵시적 커서를 사용할 수 없음 

* SQL%rowcount : 해당 커서에서 실행한 총 행의 개수

* SQL%found    : 해당 커서 안에 아직 수행해야 할 데이터가 있을 경우 true, 없을경우 false

* SQL%notfound : 해당 커서 안에 수행해야 할 데이터가 없을경우 true, 있을경우 false

* SQL%isopen   : 현재 묵시적 커서가 메모리에 open되어 있을 경우 true값을, 그렇지 않을 경우에는 false


예제
{: .label .label-purple .mt-2}
```sql
-- 묵시적 커서를 활용해서  emp table 에서  sal 이 100이하인 경우와  1000 - 2000 사이인 경우를 지우고 각 몇 건이 지워졌는지 화면에 출력
BEGIN
delete emp
WHERE sal < 1000;
DBMS_OUTPUT.PUT_LINE('=====================================');
DBMS_OUTPUT.PUT_LINE('1000 이하  : '||sql%rowcount||' 건 삭제되었습니다');

delete emp
WHERE sal between 1000 and 2000 ;
DBMS_OUTPUT.PUT_LINE('=====================================');
DBMS_OUTPUT.PUT_LINE('1000 - 2000 사이  : '||sql%rowcount||' 건 삭제되었습니다');
END;
/
```

### Example

```sql
-- 사원번호를 전달 받아서 자료가 존재여부를 확인
create or replace procedure pro_18
	(p_empno in emp.empno%type)
is
	v_ename emp.ename%type;
	v_sal 	emp.sal%type;
	v_update_row number;

begin
	select ename, sal into v_ename, v_sal --v_sal에 넣음
	from emp
	where empno = p_empno;

	--1. 자료가 있는 경우, 없는 경우
	-- sql%found
	if sql%found
		then dbms_output.put_line(v_ename || '의 급여는' || v_sal || '원 입니다!');
    else dbms_output.put_line(p_empno || '사원 자료는 없습니다!');
	end if;
	
	--2. 데이터 행의 갯수
	-- sql%rowcount
	update emp
	set sal = 0
	where empno = p_empno; -- between 100 and 110;
	
	v_update_row := sql%rowcount;
	dbms_output.put_line('급여가 수정된 사원의 건수' || v_update_row);
	
	exception 
		when no_data_found then dbms_output.put_line( p_empno || 'exception 사원 자료는 없습니다!');
end pro_18;

---

select * from emp where empno = 7369;
```

![](cur_q1.jpg)

---

## Explicit Cursor

명시적(Explicit)커서

**프로그래머에 의해 선언되고 이름이 부여된 커서**

주로 여러 개의 행을 처리하고자 할 경우 사용

* 커서이름%ROWCOUNT : FETCH 문에 의해 읽혀진 데이터의 총 행 수. 가장 마지막에 처리된 행이 몇 번째 인지를 반환.

* 커서이름%FOUND : FETCH 문이 수행되었을 경우, 읽혀진(FETCH) 행이 있을 경우에는 TRUE값을, 그렇지 않을 경우에는  FALSE값을 가지는 속성

* 커서이름%NOTFOUND : FETCH 문이 수행되었을 경우, 읽혀진(FETCH ) 행이 없을 경우에는 TRUE값을, 그렇지 않을 경우에는  FALSE값을 가지는 속성

* 커서이름%ISOPEN : 명시적 커서가 메모리에 확보(선언)되어 있을 경우에는 TRUE값을, 그렇지 않을 경우에는  FALSE(거짓) 값을 가지는 속성

명시적커서의 진행순서는 **선언 -> OPEN -> FETCH -> CLOSE**로 진행

1. 선언 

    &#9656; 커서의 이름을 기술하고 is뒤에 커서 내에서 수행할 select문을 정의
    
    &#9656; select문장에서는 into절을 포함하지 않아야 함
    
    syntax
    {: .label .mt-2}
    <div class="code-example" markdown="1">
    CURSOR 커서명 IS select문;
    </div>

2. 커서열기(open)

    **커서의 열기는 open문을 사용**

    &#9656; 커서를 오픈하면 검색 조건에 만족하는 모든 로우로 구성된 결과 set이 구해지고 첫 번째 로우를 가르키게 됨
    
    &#9656; 커서안의 검색이 실행되면 데이터가 추출되진 않아도 에러는 발생하지 않음

    syntax
    {: .label .mt-2}
    <div class="code-example" markdown="1">
    OPEN 커서명;
    </div>
    
3. 커서패치(fetch)

    &#9656; 현재 행에 대한 정보를 얻어와서 into 뒤에 기술한 변수에 저장한 후 다음 로우로 이동
    
    &#9656; 얻어진 여러개의 로우에 대한 결과값을 모두 처리하려면 반복적으로 fetch문을 수행해야 함

    &#9656; 커서의 select문의 컬럼수와 output변수의 수가 동일 해야 함

    &#9656; 커서컬럼의 타입과 output변수의 타입은 동일해야 함

    &#9656; 커서는 한라인씩 데이터를 fetch
    syntax
    {: .label .mt-2}
    <div class="code-example" markdown="1">
    FETCH 커서명 INTO 변수1... 변수N;
    </div>
    
4. 커서닫기(close)

    &#9656; 사용이 끝난 커서는 반드시 닫아 주어야 함

    &#9656; 필요할 경우 커서를 다시 오픈할 수 있음

    &#9656; 커서를 닫은 경우에는 fetch할 수 없음

    syntax
    {: .label .mt-2}
    <div class="code-example" markdown="1">
    CLOSE 커서명;
    </div>
    
예제
{: .label .label-purple .mt-2}
```sql
BEGIN
DBMS_OUTPUT.PUT_LINE(' 학과명과  학과의 위치 안내 입니다');
DBMS_OUTPUT.PUT_LINE('------------------------------------------');
FOR depart_cur IN ( SELECTdname,build
                     FROM department
                    WHERE build is not null
                    ORDER BY 1)  서브쿼리
LOOP
DBMS_OUTPUT.PUT_LINE(depart_cur.dname||' ---> '||
                           depart_cur.build||' 에 있습니다');
END LOOP;
END;
/
```

* 명시적 커서 처리단계

![](cursor_set.jpg)

### CURSOR FOR LOOP

명시적 CURSOR에서 로우를 여러건 처리

내부적으로 OPEN, FETCH, CLOSE되기 때문에 DECLARE절에서 선언만 하고 바로 사용할 수 있어서 간편 

변수도 따로 선언하지 않아도 됨 

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
FOR record_name IN cursor_name LOOP

statement1;

statement2;

...

END LOOP;
</div>

### Example

1. 한건 : 특정부서의 평균 급여와 사원수를 출력

```sql
create or replace procedure pro_19
	(p_deptno in dept.deptno%type)
is
	cursor dept_avg is
	select dpt.dname, count(emp.empno), round(avg(emp.sal),2)
	from emp emp, dept dpt
	where emp.deptno = p_deptno
	and emp.deptno = dpt.deptno
	group by dpt.dname;
	
	v_dname dept.dname%type;
	v_emp_count number;
	v_emp_avg 	number;
	
begin
		--1. cursor open
		open dept_avg;
		--2. cursor fetch: 한 건씩 자료를 꺼내옴
		fetch dept_avg into v_dname, v_emp_count, v_emp_avg;
		-- select ... into 와 동일한 형태
		
		dbms_output.put_line('부서명: ' || v_dname || '사원수: ' || v_emp_count || '급여평균: '  || v_emp_avg);
		
		--3. cursor close
		close dept_avg;
		
	exception 
			when others then dbms_output.put_line(sqlerrm || 'ERROR');
	
end pro_19;
```

![](cur_q2.jpg)