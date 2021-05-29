---
layout: default
title: DCL
parent: Commands
grand_parent: SQL / Oracle
nav_order: 5
---

# DCL Commands
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## DCL Basic

**데이터 제어어(Data Control Language)**

-- 사용자권한부여
-- scott사용자에 hr스키마를 접근할 수 있는 권한 부여
-- hr권한으로 부여할 수 있다.
grant select on employees to scott;
grant select on departments to scott;

-- 권한취소
revoke select on countries from scott; 

select * from hr.employees;
select * from hr.departments;

