---
layout: default
title: Precedence
parent: Operator
grand_parent: JavaScript
nav_order: 99
---
 
# Operator Precedence
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Operator Precedence Table

**연산 우선순위**

&#124; value가 높을수록 우선

| Value        | Operator   | Description               | Example           |
|:-------------|:-----------|:--------------------------|:------------------|
| 20           | ()         | Expression grouping       | (3 + 4)           |
| &#8290;      | &#8290;    | &#8290;                   | &#8290;           |
| 19           | .          | Member                    | person.name       |
| 19           | []         | Member                    | person["name"]    |
| 19           | ()         | Function call             | myFunction()      |
| 19           | new        | Create                    | new Date()        |
| &#8290;      | &#8290;    | &#8290;                   | &#8290;           |
| 17           | ++         | Postfix Increment         | i++               |
| 17           | --         | Postfix Decrement         | i--               |
| &#8290;      | &#8290;    | &#8290;                   | &#8290;           |
| 16           | ++         | Prefix Increment          | ++i               |
| 16           | --         | Prefix Decrement          | --i               |
| 16           | !          | Logical not               | !(x==y)           |
| 16           | typeof     | Type                      | typeof x          |
| &#8290;      | &#8290;    | &#8290;                   | &#8290;           |
| 15           | **         | Exponentiation (ES2016)   | 10 ** 2           |
| &#8290;      | &#8290;    | &#8290;                   | &#8290;           |
| 14           | *          | Multiplication            | 10 * 5            |
| 14           | /          | Division                  | 10 / 5            |
| 14           | %          | Division Remainder        | 10 % 5            |
| &#8290;      | &#8290;    | &#8290;                   | &#8290;           |
| 13           | +          | Addition                  | 10 + 5            |
| 13           | -          | Subtraction               | 10 - 5            |
| &#8290;      | &#8290;    | &#8290;                   | &#8290;           |
| 12           | <<         | Shift left                | x << 2            |
| 12           | >>         | Shift right               | x >> 2            |
| 12           | >>>        | Shift right (unsigned)    | x >>> 2           |
| &#8290;      | &#8290;    | &#8290;                   | &#8290;           |
| 11           | <          | Less than                 | x < y             |
| 11           | <=         | Less than or equal        | x <= y            |
| 11           | >          | Greater than              | x > y             |
| 11           | <=         | Greater than or equal     | x >= y            |
| &#8290;      | &#8290;    | &#8290;                   | &#8290;           |
| 10           | ==         | Equal                     | x == y            |
| 10           | ===        | Strict equal              | x === y           |
| 10           | !=         | Unequal                   | x != y            |
| 10           | !==        | Strict unequal            | x !== y           |
| &#8290;      | &#8290;    | &#8290;                   | &#8290;           |
| 9            | &          | Bitwise AND               | x & y             |
| 8            | ^          | Bitwise XOR               | x ^ y             |
| 7            | &#124;     | Bitwise OR                | x &#124; y        |
| 6            | &&         | Logical AND	            | x && y            |
| 5            |&#124;&#124;| Logical OR                | x &#124;&#124; y  |
| 4            | ?:         | Condition	                | ? "Yes" : "No"    |
| &#8290;      | &#8290;    | &#8290;                   | &#8290;           |
| 3            | +=         | Assignment                | x += y            |
| 3            | /=         | Assignment                | x /= y            |
| 3            | -=         | Assignment                | x -= y            |
| 3            | *=         | Assignment                | x *= y            |
| 3            | %=         | Assignment                | x %= y            |
| 3            | <<=        | Assignment                | x <<= y           |
| 3            | >>=        | Assignment                | x >>= y           |
| 3            | >>>=       | Assignment                | x >>>= y          |
| 3            | &=         | Assignment                | x &= y            |
| 3            | ^=         | Assignment                | x ^= y            |
| 3            | &#124;=    | Assignment                | x &#124;= y       |
| &#8290;      | &#8290;    | &#8290;                   | &#8290;           |
| 2            | yield      | Pause Function            | yield x           |
| 1            | ,          | Comma                     | 5, 6              |

