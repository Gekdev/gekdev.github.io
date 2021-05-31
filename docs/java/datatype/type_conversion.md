---
layout: default
title: Type Conversion
parent: Datatype
grand_parent: Java
nav_order: 5
---

# Datatype Conversion
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Type Conversion

**하나의 타입을 다른 타입으로 바꾸는 것을 타입 변환**

boolean형을 제외한 나머지 기본 타입 간의 타입 변환을 자유롭게 수행할 수 있음
 
다른 타입끼리의 연산은 우선 피연산자들을 모두 같은 타입으로 만든 후에 수행
 
메모리에 할당받은 바이트의 크기가 상대적으로 작은 타입에서 큰 타입으로의 타입 변환은 생략할 수 있음

!Error
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
메모리에 할당받은 바이트의 크기가 큰 타입에서 작은 타입으로의 타입 변환은 데이터의 손실이 발생

따라서 상대적으로 바이트의 크기가 작은 타입으로 타입 변환을 할 경우 자바 컴파일러는 오류를 발생
</div>

### Types of Type Conversion

자바에서 타입 변환은 크게 다음과 같이 두 가지 방식

1. 묵시적 타입 변환(자동 타입 변환)

2. 명시적 타입 변환(강제 타입 변환)

### Implicit Conversion

**묵시적 타입 변환, 대입 연산이나 산술 연산에서 컴파일러가 자동으로 수행해주는 타입 변환**

자바에서는 데이터의 손실이 발생하지 않거나, 데이터의 손실이 최소화되는 방향으로 묵시적 타입 변환을 진행

자바에서는 데이터의 손실이 발생하는 대입 연산은 허용하지 않음

자바에서는 타입의 표현 범위에 따라 다음과 같은 방향으로 자동 타입 변환이 이루어짐

![](imc.jpg)

예제
{: .label .label-purple .mt-2}
```java
double num1 = 10; // double형 변수에 int형 데이터를 대입 (int형 데이터가 double형으로 자동 타입 변환)

// int num2 = 3.14; // int형 변수가 표현할 수 있는 범위보다 더 큰 double형 데이터를 대입, 데이터의 손실이 발생 = error

double num3 = 7.0f + 3.14; // float형 데이터와 double형 데이터의 산술 연산을 수행

System.out.println(num1);  // 10.0
System.out.println(num3);  // 10.14
```

```java
① byte num1 = 100;        // OK : byte형 변수에 표현 범위가 더 큰 int형 데이터를 대입

② byte num2 = 200;        // Type mismatch : byte형 변수가 표현할 수 있는 범위를 벗어난 int형 데이터는 타입 변환되지 못하고, 오류를 발생

③ int num3 = 9876543210;  // Out of range

④ long num4 = 9876543210; // Out of range

⑤ float num5 = 3.14;      // Type mismatch : float형 변수가 표현할 수 있는 범위를 벗어난 double형 데이터를 대입하므로, 오류를 발생

⑥ int num3 = 9876543210L;  // Type mismatch

long num4 = 9876543210L; // OK
//int형 리터럴보다 더 큰 정수를 사용하기 위해서는 다음 예제처럼 리터럴의 마지막에 L이나 l 접미사를 추가하여 long형 리터럴로 명시
```

### Explicit Conversion

**명시적 타입 변환, 사용자가 타입 캐스트 연산자(())를 사용하여 강제적으로 수행하는 타입 변환**

자바에서 산술 연산을 수행하고 얻는 결괏값의 타입은 언제나 피연산자의 타입과 일치해야 함

즉, int형 데이터끼리의 산술 연산에 대한 결괏값은 언제나 int형 데이터의 결과로 나옴

double형 변수에 그 결과가 대입될 때, double형으로 자동 타입 변환되어 0.0이라는 결과가 출력

따라서 정확한 결과를 얻고자 한다면 ②번 라인처럼 피연산자 중 하나의 타입을 double형으로 강제 타입 변환

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
(변환할타입) 변환할데이터
</div>
```java
int num1 = 1, num2 = 4;

① double result1 = num1 / num2;
② double result2 = (double) num1 / num2;

System.out.println(result1); // 0.0
System.out.println(result2); // 0.25
```
