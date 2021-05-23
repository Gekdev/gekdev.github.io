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

### Replace null value

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
* **nvl(컬럼명, expr0)** : **null을 0 또는 다른 값으로 변환**

* **nvl2()** : **대문자를 소문자로 변환**

&#9656; expr0에는 날짜, 문자, 숫자형이 들어갈 수 있음
</div>
```sql
-- upper(lower(ename))는 소문자 변환한걸 대문자로 다시 변환한 모습
select ename
    , lower(ename)
    , upper(ename)
    , initcap(ename)
    , upper(lower(ename)) 
from emp;
```

![](https://gekdev.github.io/docs/sql/function/example/upper_lower.jpg)

