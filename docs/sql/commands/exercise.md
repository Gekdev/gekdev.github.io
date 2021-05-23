---
layout: default
title: Exercise
parent: Commands
grand_parent: SQL / Oracle
nav_order: 99
---

# Commands Exercise
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Commands Exercise

### Connection Operator

Q1. 

![](https://gekdev.github.io/docs/sql/commands/example/con_op1.png)

```sql
select name 
    || '''s ID : ' 
    || id 
    || ', weight is ' 
    ||  weight 
    || 'kg'  "ID and Weight"
from student;
```

![](https://gekdev.github.io/docs/sql/commands/example/con_qa_1.jpg)

Q2.

![](https://gekdev.github.io/docs/sql/commands/example/con_op2.png)

```sql
select ename 
    || '('
    || job
    || ') , '
    || ename
    || ''''
    || job
    || ''''  "Name and Job"
from emp;
```

![](https://gekdev.github.io/docs/sql/commands/example/con_qa_2.jpg)

Q3.

![](https://gekdev.github.io/docs/sql/commands/example/con_op3.png)

```sql

```

![](https://gekdev.github.io/docs/sql/commands/example/con_qa_3.jpg)
