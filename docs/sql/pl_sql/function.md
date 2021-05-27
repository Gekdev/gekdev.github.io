---
layout: default
title: Function
parent: PL/SQL
grand_parent: SQL / Oracle
nav_order: 3
---

# PL/SQL Function
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## PL/SQL Function

### What is Function?

**값을 계산하고 그 결과값을 반환하기 위해서 function을 사용**

&#9656; 매개변수를 가질 수 있고, 값을 반환하는 명명된 PL/SQL 블록

&#9656; 반복실행을 위한 데이터베이스 객체로서 데이터베이스에서 저장될 수 있음

&#9656; 또한 표현식의 일부로서 호출될 수 있음

&#9656; 대부분 프로시저와 유사하지만 in parameter만 사용 가능하고 return문이 있어야 한다

&#9656; 재이용성, 유지 가능성이 높음

### Function Basic

&#9656; 기본적으로 SQL문 안에서 사용해야 함

&#9656; 오라클에서 기본적으로 제공해주는 함수 = Built-in함수 (concat())

&#9656; PL/SQL에서의 함수 = 사용자가 직접 정의한 함수

syntax
{: .label .mt-2}
```sql
CREATE OR REPLACE FUNCTION 함수이름
    (매개변수1 in 데이터타입, 매개변수2....) 
    RETURN 데이터타입 -- return될 값의 데이터타입을 선언 
IS[AS]
    변수, 상수 선언
BEGIN
    실행부
    
    RETURN 반환값 -- 리턴문이 반드시 존재해야 함
    [EXCEPTION 예외처리부]
END [함수 이름];
```

### Features of Function

1. 선언부와 실행부에 Return 절이 포함되어있어야 함

2. PL/SQL 블록 내에서 호스트/바인드 변수 참조할 수 없음

3. Return 데이터 형은 크기를 지정하지 않음

4. Insert, Update, Delete 명령어는 허용되지 않음

5. pl/sql block은 함수가 수행할 내용을 정의한 본문(body)부분

Note!
{: .label .mt-2}
<div class="code-example" markdown="1">
오라클함수 (function)에서는 기본적으로 dml(insert/delete/update)를 사용불가

하지만 굳이 사용하려면 begin 위에 `pragma autonomous_transaction` 을 선언하면 가능
</div>

### Example

Q1. 사원번호를 입력받아서 사원의 급여를 10% 인상하는 function 

```sql
create or replace function fn_01
    (p_empno in number) 
    return number 
is 
	v_sal number;
	pragma autonomous_transaction; --update를 사용하기 위해
begin
	update emp
	set sal = sal * 1.1
	where empno = p_empno;
	commit;
	
	select sal into v_sal
	from emp
	where empno = p_empno;
	
	return v_sal;
end fn_01;

---
select fn_01(7369) from dual;
select empno, ename, fn_01(empno) from emp where empno = 7369;
```

![](func_q1.jpg)

Q2. 부피를 계산하는 함수, 매개변수는 length, width, height

부피 = length * width * height

```sql
create or replace function fn_02
	(p_length in number, p_width in number, p_height in number)
	return number
is
	v_result number;
begin
	v_result := p_length * p_width * p_height;
	return v_result;
end fn_02;

---
select fn_02(10,20,30) from dual;
```

![](func_q2.jpg)

Q3. 현재일을 입력받아서 해당월의 마지막일자를 구하기(fn_03)

```sql
create or replace function fn_03
	(p_day in date) 
	return date
is
	v_result date;
begin
    v_result := last_day(p_day);
    -- 같은것
    -- v_result := add_months(p_day,1)- to_char(p_day,'DD');
	
	return v_result;
end fn_03;
---
select fn_03(sysdate) from dual;
select fn_03('20200321') from dual;
select fn_03('2020.03.21') from dual;
```

![](func_q3.jpg)

Q4. '홍길동'문자를 받아서 '길동'값을 리턴하는 함수(fn_04)

```sql
create or replace function fn_04
	(p_name in varchar2) 
	return varchar2
is
	v_result varchar2(20);
begin
	v_result := substr(p_name,2);
	return v_result;
end fn_04;
---
select fn_04('권가은') from dual;
select fn_04('가은') from dual;
select fn_04('가은가은') from dual;
select fn_04('Sharon Stom') from dual;
```

![](func_q4.jpg)

Q5. 현재일을 입력받아서 '2020년 07월 17일'형태로 리턴하는 함수(fn_05)

```sql
create or replace function fn_05
	(p_day in date) 
	return varchar2
is
	v_result varchar2(30);
begin

	v_result := to_char(p_day, 'yyyy"년" mm"월" dd"일"');
	return v_result;

end fn_05;
---
select fn_05(sysdate) from dual;
```

![](func_q5.jpg)

Q6. 주민번호를 입력받아서 남자 또는 여자를 리턴하는 함수(fn_06)

```sql
create or replace function fn_06
	(p_jumin in number) 
	return varchar2
is 
	v_result varchar2(10);
begin
	v_result := substr(p_jumin,7,1);
	
  if(v_result = 1 or v_result = 3) then 
		v_result := '남자';
	else 
		v_result := '여자';
	end if;

	-- if v_result in ('1', '3')
	--	 then v_result := '남자';
	-- else v_result := '여자';
    
	return v_result;
end fn_06;
---
select fn_06(9702282234567) from dual union all 
select fn_06(9602281234567) from dual union all 
select fn_06(9702283124567) from dual union all 
select fn_06(9702284123567) from dual ;

select studno, name, jumin, fn_06(jumin) from student;
```

![](func_q6.jpg)

Q7. emp에서 전사원의 hiredate를 현재일 기준으로 근손년월을 계산하는 함수를 작성한 후에 전사원의 근속년월을 출력(fn_07)

```sql
create or replace function fn_07
	(p_hiredate in date)
	return varchar2
is
	v_workdays varchar2(30);
begin
    v_workdays := trunc(months_between(sysdate, p_hiredate)/12, 0) || '년'
               || trunc(mod(months_between(sysdate, p_hiredate), 12)) || '개월';
		
    return v_workdays;
end fn_07;

---
select empno, ename, fn_07(hiredate) 근속년월 from emp;
```

![](func_q7.jpg)

### function 호출위치

### function 삭제