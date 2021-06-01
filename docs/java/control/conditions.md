---
layout: default
title: Conditions 
parent: Control
grand_parent: Java
nav_order: 1
---

# Java Conditions 
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Conditional Statements

**조건문, 주어진 조건식의 결과에 따라 별도의 명령을 수행하도록 제어하는 명령문**

1. if 문

2. if / else 문

3. if / else if / else 문

4. switch 문

### if Statement

조건식의 결과가 참(true)이면 주어진 명령문을 실행, 거짓(false)이면 아무것도 실행하지 않음

들여쓰기로 가독성이 좋게 만드는것이 좋음

실행될 명령문이 한 줄 뿐이라면 중괄호({})를 생략할 수 있음

syntax
{: .label .mt-2}
```java
if (조건식) {
    조건식의 결과가 참일 때 실행하고자 하는 명령문;
}
```

### if / else Statement

실행될 명령문이 한 줄뿐이라면 중괄호({})를 생략가능
 
syntax
{: .label .mt-2}
```java
if (조건식) {
    조건식의 결과가 참일 때 실행하고자 하는 명령문;
} else {
    조건식의 결과가 거짓일 때 실행하고자 하는 명령문;
}
```

### if / else if / else Statement

실행될 명령문이 한 줄뿐이라면 중괄호({})를 생략가능

syntax
{: .label .mt-2}
```java
if (조건식1) {
    조건식1의 결과가 참일 때 실행하고자 하는 명령문;
} else if (조건식2) {
    조건식2의 결과가 참일 때 실행하고자 하는 명령문;
} else {
    조건식1의 결과도 거짓이고, 조건식2의 결과도 거짓일 때 실행하고자 하는 명령문;
}
```

### Ternary Operator

**삼항연산자로 조건문을 표현할 수 있음**

if / else 문을 삼항 연산자를 이용하여 간결하게 표현가능

syntax
{: .label .mt-2}
```java
조건식 ? 반환값1 : 반환값2
```

### switch Statement

**주어진 조건 값의 결과에 따라 프로그램이 다른 명령을 수행하도록 하는 조건문**

&#9656; if / else 문보다 가독성이 더 좋으며, 컴파일러가 최적화를 쉽게 할 수 있어 속도 또한 빠름

&#9656; default : 건 값이 위에 나열된 어떠한 case 절에도 해당하지 않을 때만 실행

&#8594; 반드시 존재해야 하는 것은 아니며 필요할 때만 선언

&#8594; 맨 마지막에 위치해야 하지만, case절 사이에 위치해도 상관없긴 함

&#9656; 각 case 절 및 default 절은 반드시 break 키워드를 포함(없으면 끝나지를 않음)

switch 조건 값으로 사용 가능한 데이터 타입
{: .label .label-red .mt-2}
<div class="code-example" markdown="1">
1. byte형, short형, char형, int형의 변수나 리터럴 (int형으로 승격할 수 있는(integer promotion)값만 가능)

2. 기본 타입에 해당하는 데이터를 객체로 포장해 주는 래퍼 클래스(Wrapper class) 중에서 위에 해당하는 Byte, Short, Character, Integer 클래스의 객체

3. enum 키워드를 사용한 열거체(enumeration type)와 String 클래스의 객체

&#8594; if/else문보다 사용할 수 있는 상황이 적음
</div>

syntax
{: .label .mt-2}
```java
switch (조건 값) {
    case 값1:
        조건 값이 값1일 때 실행하고자 하는 명령문;
        break;
    case 값2:
        조건 값이 값2일 때 실행하고자 하는 명령문;
        break;
    ...
    default:
        조건 값이 어떠한 case 절에도 해당하지 않을 때 실행하고자 하는 명령문;
        break;
}
```
