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

### LOOP Statement

**여러번 반복적으로 수행되는 문장이 있을 경우 LOOP문을 사용**

LOOP문에는 3가지 종류가 있음 

| 종류 | 설명|
|:----|:-----|
| BASIC LOOP | 조건 없이 반복작업을 위해 사용 |
|FOR LOOP | COUNT를 기본으로 한 반복작업 |
|WHILE LOOP | 조건을 비교하기 위한 반복작업 |

&#9656; 반복문을 종료하기 위해서는 EXIT문을 사용

1. BASIC LOOP

    BASIC LOOP SYNTAX
    {: .label .mt-2}
    <div class="code-example" markdown="1">
    LOOP

    statement1;

    statement2;

    ...

    EXIT [WHERE condition] --조건이 참이면 EXIT

    END LOOP
    </div>

2. FOR LOOP

    **반복 횟수가 저해진 반복문을 처리**

    FOR LOOP SYNTAX
    {: .label .mt-2}
    <div class="code-example" markdown="1">
    FOR index_counter IN [REVERSE] lower_bound..upper_bound LOOP

    statement1;

    statement2;

    ...

    END LOOP
    </div>
    
    &#9656; index_counter : upper_bound나 lower_bound에 도달할 떄 까지 1씩 자동적으로 증가하거나 감소되는 값을 가진 암시적으로 선언된 정수
    
    &#9656; REVERSE : upper_bound나 lower_bound까지 반복하면서 1씩 감소되도록 함
    
    &#9656; lower_bound : index_counter 값의 범위에 대한 하단 바운값을 지정
    
    &#9656; upper_bound : index_counter 값의 범위에 대한 상단 바운드 값을 지정

3. WHILE LOOP

    **제어조건이 TRUE인 동안만 문장을 반복**

    &#9656; 조건이 반복이 시작될 떄 체크하기 때문에 LOOP내의문장이 한번도 수행되지 않을 경우도 있음

    WHILE LOOP SYNTAX
    {: .label .mt-2}
    <div class="code-example" markdown="1">
    WHILE condition LOOP

    statement1;

    statement2;

    ...

    END LOOP
    </div>
