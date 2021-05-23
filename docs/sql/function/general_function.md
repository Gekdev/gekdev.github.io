---
layout: default
title: General Function
parent: Function
grand_parent: SQL / Oracle
nav_order: 3
---

# SQL Single General Function
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Single General Function

### Replace null Value

**테이블의 널값을 대체하는 함수**

&#9656; 컬럼명과 exprN은 반드시 데이터 타입이 일치해야 함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
* **nvl(컬럼명, expr0)** : **null을 0 또는 다른 값으로 변환**

* **nvl2(컬럼명, expr2, expr3)** : **컬럼명을 검사해 결과가 null이면 expr2반환, null이 아니면 expr3을 반환**

&#9656; exprN에는 날짜, 문자, 숫자형이 들어갈 수 있음
</div>
```sql
select ename
     , sal
     , comm
     , nvl(comm,0)
     , sal + comm
     , sal + nvl(comm, 0)
from emp;
```

![](nvl.jpg)

### nullif()

**표현식을 비교해서 널값을 반환하는 함수**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**nullif(expr1, expr2)** : **두 표현식을 비교하여 동일한 경우에는 NULL을 반환하고 동일하지 않으면 첫 번째 표현식을 반환**
</div>
```sql
select nullif('A','A'), nullif('A','B')
from dual;
```

![](nullif.jpg)

### coalesce()

**인수 중 null이 아닌 첫번 째 인수를 반환하는 함수**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**coalesce(expr1, expr2, ... , exprN) : 두 표현식을 비교하여 동일한 경우에는 NULL을 반환하고 동일하지 않으면 첫 번째 표현식을 반환**
</div>
```sql
select ename, sal, comm, coalesce(comm, sal, 0)
from emp
order by job;
```

![](coalesce.jpg)

### decode()

**switch case문과 같은 기능, sql문안에서 사용할 수 있도록 한 오라클고유함수**

&#9656; 조건에 따라 다양한 선택이 가능하도록 함

&#9656; 기본 결과가 명시되지 않았을 경우에는 NULL값을 반환

&#9656; decode(deptno, 101, decode())

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**decode(표현식

  , 조건1, 결과1

  , 조건2, 결과2

  , 조건3, 결과3

  , 기본결과n) as alias**
</div>
```sql
select deptno
     , name
     , decode(deptno, 101, '컴공'
                    , 102, '미디어 융합'
                    , 103, '소프트공학'
                    , '기타학과')
	from professor;
```

![](decode.jpg)

### case

**프로그램 언어의 if else와 같이 사용할 수 있음**

expr이 조건 1과 일치하면 1반환... 값이 없거나 null일 경우에는 else 다음 기술한 결과n을 반환함

&#9656; decode대신 일반적으로 사용되는 문장(ISO 표준 규격에 더 잘맞음)

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
**case expr

  when 조건1 then 결과1

  when 조건2 then 결과2

  when 조건3 then 결과3
    
  else 결과n
  
  end [as 별칭]
</div>

### Example

Q1. student에서 전공이 101인 학생들중에 jumin 성별구분해서 1=남자 2=여자를 출력

name, jumin, gender 

```sql
select name
, substr(jumin,7,1)
, decode(substr(jumin,7,1), 1, '남자', '여자') gender
	from student;
```

Q2. Student 테이블에서 1 전공이 (deptno1) 101번인 학생의 이름과 연락처와 지역을 출력하세요

단,지역번호가 02 는 "SEOUL" , 031 은 "GYEONGGI", 051 은 "BUSAN", 052 는 "ULSAN", 055 는 "GYEONGNAM"

```sql
select name
		 , tel
		 , substr(tel,0, instr(tel,')')-1)
     , decode(substr(tel,0, instr(tel,')')-1), 02, 'SEOUL'
									  , 031, 'GYEONGGI'
										, 051, 'BUSAN'
										, 052, 'ULSAN'
										, 053, 'DAGUE'
										, 055, 'GYEONGNAM') decode
		 , case substr(tel,0, instr(tel,')')-1) -- ISO  표준 규격에 더 맞음
					When '02' then 'SEOUL'
					When '051' then 'GYEONGGI'
					When '052' then 'ULSAN'
					When '053' then 'DAGUE'
					When '055' then 'GYEONGNAM'
			 end as 지역번호
	from student 
 where deptno1 = 101;
```

Q3. when 조건 between 값1 and 값2 then 출력

emp에서 sal 1~1000 1등급, 1001~2000 2등급, 2001~3000 2등급, 3001~4000 2등급, 4001보다 크면 5등급

```sql
 select ename
      , sal
			, case when sal between    1 and 1000 then '1등급'
						 when sal between 1001 and 1000 then '2등급'
						 when sal between 2001 and 3000 then '3등급'
						 when sal between 3001 and 4000 then '4등급'
						 when sal > 4001 then '5등급'
			 end as 등급 
	 from emp
  order by sal desc;
```

Q4. student에서 jumin에 월참조해서 해당월의 분기를 출력(1Q, 2Q, 3Q, 4Q)

name, jumin, 분기

```sql
select name
			, jumin
			, substr(jumin,3,2) month
			, case when substr(jumin,3,2) between 1 and 3 then '1Q'
						 when substr(jumin,3,2) between 4 and 6 then '2Q'
						 when substr(jumin,3,2) between 7 and 9 then '3Q'
						 when substr(jumin,3,2) >= 10 then '4Q'
			  end as 분기
	 from student;
```

Q5. emp에서 10=회계부, 20=연구실, 30=영업부, 40=전산실

deptno, 부서명

```sql
-- 1) decode
-- 2) case
select deptno
     , decode(deptno, 10, '회계부'
                      , 20, '연구실'
                      , 30, '영업부'
                     , 40, '전산실') 부서명
     , case deptno When 10 then '회계부'
                                 When 20 then '연구실'
                                 When 30 then '영업부'
                                 When 40 then '전산실'
			 end as 부서명
  from emp;
```

Q6. 급여인상율을 다르게 적용하기

emp에서 sal < 1000 0.8%인상, 1000~2000 0.5%, 2001~3000 0.3% 그 이상은 0.1% 인상분 출력

ename, sal(인상전급여), 인상후급여 

```sql
-- 1) decode
-- 2) case 
select * from emp;
select ename, sal
		 , decode(sign(sal-1000), -1, sal*1.08,
                                   0, sal*1.05,
                                   1, decode(sign(sal-2000), -1, sal*1.05,0, sal*1.05, 1, decode(sign(sal-3000),-1, sal*1.03, 0, sal*1.03, 1, sal*1.01)))
		 , case when sal < 1000  then sal*1.08
						when sal between 1000 and 2000 then sal*1.05
						when sal between 2001 and 3000 then sal*1.03
						when sal > 3000 then sal*1.01
				end as 인상후급여
  from emp; 
```