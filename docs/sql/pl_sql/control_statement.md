---
layout: default
title: Control Statement
parent: PL/SQL
grand_parent: SQL / Oracle
nav_order: 1
---

# PL/SQL Control Statement
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Control Statement

**제어문은 문장의 흐름을 변경할 때 필요**

### IF Statement

**조건에 따라 어떤 명령을 선택적으로 처리하기 위해 사용**

&#9656; ELSIF절은 여러번 사용 가능하지만, ELSE절은 한번만 사용가능

&#9656; 가장 간단한 형태는 IF ~ THEN ~ END IF로만 구성된 형태

&#9656; 조건이 TRUE이면 THEN 이하의 문장을 실행하고 FALSE나 NULL이면 다음 조건을 물어봄

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
IF condition THEN
    
statements;

ELSIF condition THEN    -- 여러번 중복 사용 가능
    
statements;

ELSE condition THEN     -- 한번만 가능
    
statements;

END IF;
</div>

