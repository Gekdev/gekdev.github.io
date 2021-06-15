---
layout: default
title: Constant / Literal
parent: Datatype
grand_parent: Java
nav_order: 2
---

# Datatype Constant
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Constant

### Constant Basic

**상수, 변수와 마찬가지로 데이터를 저장할 수 있는 메모리 공간을 의미**

변수와 다른 점은 프로그램이 실행되는 동안 메모리에 저장된 데이터를 변경할 수 없다는 점

&#9656; 자바에서는 final 키워드를 사용하여 선언하고, 상수는 선언과 동시에 반드시 초기화해야 함

&#9656; 자바에서 상수의 이름은 일반적으로 모두 대문자를 사용하여 선언, 여러 단어로 이루어진 이름의 경우에는 언더스코어(_)를 사용하여 구분

&#9656; C++에서는 const 키워드를 사용하여 상수를 선언

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
final int AGES = 30;
</div>

---

## Literal

### Literal Basic

**리터럴(literal)이란 그 자체로 값을 의미하는 것**

변수와 상수와는 달리 데이터가 저장된 메모리 공간을 가리키는 이름을 가지고 있지 않음

예제
{: .label .label-purple .mt-2}
```java
int var = 30;         // 30이 바로 리터럴임.

final int AGES = 100; // 100이 바로 리터럴임.
```

### Literal Types

자바에서 리터럴은 타입에 따라 다음과 같이 구분

| Types  | 설명|
|:-------|:---|
|정수형 리터럴(Integer literals) | 123, -456과 같이 아라비아 숫자와 부호로 직접 표현|
|실수형 리터럴(floating-point literals)| 3.14, -45.6과 같이 소수 부분을 가지는 아라비아 숫자로 표현|
| 논리형 리터럴(boolean literals)| true나 false로 표현|
|문자형 리터럴(character literals)| 'a', 'Z'와 같이 작은따옴표('')로 감싸진 문자로 표현|
|문자열 리터럴(string literals)| "자바", "홍길동"과 같이 큰따옴표("")로 감싸진 문자열로 표현|
|null 리터럴(null literals)| 단 하나의 값인 null로 표현|

### Literal Type Suffix

**리터럴 타입 접미사, 리터럴 뒤에 추가되어 해당 리터럴의 타입을 명시해주는 접미사**

| 타입 접미사 | 리터럴 타입 | 예제 |
| L 또는 l   | long형 |123456789L, ...|
|F 또는 f	|float형	|1.234567F, 8.9f, ...|
|D 또는 d (생략 가능)|double형	|1.2345D, 6.789d, ...|

예제
{: .label .label-purple .mt-2}
<div class="code-example" markdown="1">
자바에서 3.14와 같은 실수형 리터럴을 그대로 사용하면, 해당 리터럴은 실수형 타입 중에서도 double형으로 인식하는데

실수형 리터럴 맨 뒤에 F나 f를 추가하면, 자바는 해당 실수형 리터럴을 float형으로 인식함
</div>
```java
float f;
f = 0.1234f; // 0.1234는 double 타입
f = 0.1111F;

double g;
g = 0.1234;
g = 0.1234d;
g = 0.1234D;
```

### Literal with Decimal

**리터럴 앞에 접두어를 붙여서 진법을 나타낼 수 있음**

기본은 10진수로 나타냄

* 8진수 : 숫자리터럴 앞에 0

* 16진수 : 숫자리터럴 앞에 0x

```java
int var2 = 010;
System.out.println(var2);   // 8

int var3 = 0x10;
System.out.println(var3);   // 16
```
