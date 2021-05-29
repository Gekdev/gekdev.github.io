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

```sql
select * from emp, dept; 
```

![](https://gekdev.github.io/docs/sql/example/cart.jpg)

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
select table1.column, table2.column

from table1, table2 -- 조인 대상 테이블을 기술하고 ,로 구분

where table1.column1 = table.column2; -- =를 사용해 조인 조건 기술(기본 키와 외래 키에 공통적으로 존재하는 칼럼)
</div>
```sql
select emp.deptno, emp.ename, emp.hiredate, dept.dname
from emp, dept
where emp.deptno = dept.deptno;
```

![](https://gekdev.github.io/docs/sql/example/join1.jpg)

### EQUI JOIN with AND

테이블을 조인할 경우 조인 뿐만 아니라 고려 대상인 행을 제한하기 위해 where 절에 조건을 추가해야 하는 경우가 있음

```sql
select emp.deptno, emp.ename, dept.dname
from emp, dept
where emp.deptno = dept.deptno and dname = 'SALES';
```

![](https://gekdev.github.io/docs/sql/example/join_and.jpg)

### Alias Rules

1. 테이블의 별명은 30자까지 가능하지만, 길지 않게 작성

2. from 절에서 테이블명을 명시하고 공백을 둔 다음 테이블 별칭을 지정

3. 하나의 sql명령문에서 테이블명과 별명을 혼용할 수 없음

4. 테이블의 별칭은 해당 SQL 명령문 내에서만 유효함

```sql
select d.deptno, e.ename, d.dname
from emp e, dept d
where e.deptno = d.deptno;
```

![](https://gekdev.github.io/docs/sql/example/ansi.jpg)

### JOIN ~ ON

임의의 조건을 지정하거나 조인할 칼럼을 지정하려면 ON절을 사용

조인 조건만을 ON절에 기술하고 다른 검색이나 필터 조건은 WHERE절에 분리해서 기술할 수 있음

```sql
select dpt.deptno, emp.ename, dpt.dname
from emp emp inner join dept dpt 
on emp.deptno = dpt.deptno;
```

![](https://gekdev.github.io/docs/sql/example/join_on.jpg)

### EQUI JOIN Multiple Tables

**여러개의 테이블을 동시에 조인하는 방법**

```sql
-- 1. where 조건으로 연결
select stu.name studentname
     , pro.name professorname
     , dpt.dname subject
	from student stu, professor pro, department dpt 
	where stu.profno = pro.profno and stu.deptno1 = dpt.deptno;

-- 2. inner join으로 연결
select stu.name studentname
     , pro.name professorname
     , dpt.dname subject
	from student stu inner join professor pro on stu.profno = pro.profno
	                 inner join department dpt on stu.deptno1 = dpt.deptno;
```

![](https://gekdev.github.io/docs/sql/example/three_join.jpg)

---

## NON-EQUI JOIN

![](https://gekdev.github.io/docs/sql/example/join_img.png)

### EQUI JOIN Syntax

**비등가 조인, 조인 조건에 특정 범위 내에 있는지를 조사하기 위해서 사용**

&#9656; where절에 < 나 between a and b와 같은 =이 아닌 조건연산자를 사용

```sql
-- 고객명과 상품명, 마일리지를 출력
select cus.gname 고객명, gif.gname 상품명, to_char(cus.point, '999,999') 마일리지 
from customer cus, gift gif
where cus.point between gif.g_start and gif.g_end;
```

![](https://gekdev.github.io/docs/sql/example/uneq.jpg)

### NON-EQUI JOIN Multiple Tables

3개의 테이블을 조인하는 방법

```sql
--표준
select name 학생명, scr.total 점수, hak.grade 학점 
from student stu, score scr, hakjum hak
where stu.studno = scr.studno 
    and scr.total between hak.min_point and hak.max_point;

--ansi
select name 학생명, scr.total 점수, hak.grade 학점 
from student std inner join score scr on std.studno = scr.studno
                 inner join hakjum hak on scr.total between hak.min_point and hak.max_point;
```

![](https://gekdev.github.io/docs/sql/example/non_equl_three.jpg)

---

## SELF JOIN

**self join은 주로 테이블에 Hierarchical structure가 있을 때 flat structure로 바꾸는 역할**

&#9656; 한 테이블에서 두 개의 칼럼을 연결할 때 FROM 절에서 하나의 테이블에 테이블 별칭을 지정

![](https://gekdev.github.io/docs/sql/example/employee1.png)

<span class="fs-2">
[참조하기](https://junyongs.wordpress.com/2014/01/16/sql%EC%97%90%EC%84%9C-self-join%EC%9D%B4-%EB%AC%B4%EC%97%87%EC%9D%B4%EB%A9%B0-%EC%99%9C-%EC%82%AC%EC%9A%A9%ED%95%98%EB%82%98%EC%9A%94/){: .btn .btn-outline .mt-2}
</span>

---

## OUTER JOIN

**EQUI JOIN에서 양측 칼럼 값 중의 하나가 NULL 이지만 조인 결과로 출력할 필요가 있는 경우 사용**

&#9656; WHERE 절의 조인 조건에서는 OUTER JOIN 연산자인 + 기호를 사용, 조인 조건문에서 NULL이 출력되는 테이블의 칼럼에 + 기호를 추가

### LEFT OUTER JOIN

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
select table1.column, table2.column

from table1, table2 

**where table1.column = table.column2(+);**

-- join on 절

select table1.column, table2.column

from table1 left outer join table2 

on table1.column1 = table.column2;
</div>
```sql
 --left outer join, 학생에 배정받은 교수 없음
select std.name 학생이름, pro.name 교수이름
from student std, professor pro
where std.profno = pro.profno(+); -- left outer join, 오라클에서만 사용 

select std.name 학생이름, pro.name
from student std left outer join professor pro 
on std.profno = pro.profno; 
```

![](https://gekdev.github.io/docs/sql/example/left_outer.jpg)

### RIGHT OUTER JOIN

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
select table1.column, table2.column

from table1, table2 

**where table1.column1(+) = table.column2**;

-- join on 절

select table1.column, table2.column

from table1 **right outer** join table2 

on table1.column1 = table.column2;
</div>
```sql
--right outer join, 교수에 배정받은 학생없음 
select std.name 학생이름, pro.name 교수이름
from student std, professor pro
where std.profno(+) = pro.profno; -- right outer join, 오라클에서만 사용 

select std.name 학생이름, pro.name
from student std right outer join professor pro 
on std.profno = pro.profno;
```

![](https://gekdev.github.io/docs/sql/example/right_outer.JPG)

### FULL JOIN

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
select table1.column, table2.column

from table1 **full outer** join table2 

on table1.column1 = table.column2;
</div>
```sql
select std.name 학생이름, pro.name
from student std full outer join professor pro 
on std.profno = pro.profno; 
```

![](https://gekdev.github.io/docs/sql/example/full_join.jpg)
