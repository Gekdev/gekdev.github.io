---
layout: default
title: Primitive
parent: Datatype
grand_parent: Java
nav_order: 3
---

# Datatype Primitive
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Primitive

**자바에서는 여러 형태의 타입을 미리 정의하여 제공하고 있는데, 이것을 기본 타입(primitive type)이라고 함**

자바의 기본 타입은 모두 8종류가 제공되며, 크게는 정수형, 실수형, 문자형 그리고 논리형 타입이 있음

### Integer Type

**정수란 부호를 가지고 있으며, 소수 부분이 없는 수를 의미**

1. byte

2. short

3. int : 정수형 타입 중 기본이 되는 타입, 내부적으로 정수형 중에서도 int형의 데이터를 가장 빠르게 처리

4. long

정수형 타입에 따른 메모리의 크기 및 데이터의 표현 범위
{: .label .mt-2}
| 정수형 타입	| 할당되는 메모리의 크기	| 데이터의 표현 범위 |
|:-------------|:---------------------|:----------------|
|byte	|1바이트	|-128 ~ 127|
|short	|2바이트	|-215 ~ (215 - 1) = -32,768 ~ 32,767|
|int	|4바이트	|-231 ~ (231 - 1) = -2,147,483,648 ~ 2,147,483,647|
|long	|8바이트	|-263 ~ (263 - 1) = -9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807|

정수형 데이터의 타입을 결정할 때에는 반드시 자신이 사용하고자 하는 데이터의 최대 크기를 고려해야 함

해당 타입이 표현할 수 있는 범위를 벗어난 데이터를 저장하면, 오버플로우(overflow)가 발생해 전혀 다른 값이 저장될 수 있기 때문

overflow
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
**오버플로우 : 해당 타입이 표현할 수 있는 최대 범위보다 큰 수를 저장할 때 발생하는 현상**

최상위 비트(MSB)를 벗어난 데이터가 인접 비트를 덮어쓰므로, 잘못된 결과를 얻을 수 있음

비슷하게 언더플로우(underflow) : 해당 타입이 표현할 수 있는 최소 범위보다 작은 수를 저장할 때 발생하는 현상이 있음 
</div>
```java
public class Datatype04 {
    public static void main(String[] args) {

        byte num1 = 127;
        byte num2 = -128;
 
        num1++; // 127 + 1
        num2--; // -128 - 1

        System.out.println(num1); // -128
        System.out.println(num2); // 127
    }
}
```

### Floating Point Type

**실수형 타입, 소수부나 지수부가 있는 수를 가리키며, 정수보다 훨씬 더 넓은 표현 범위를 가짐**

실수형 데이터의 오차는 자바뿐만 아니라 모든 프로그래밍 언어에서 발생하는 공통된 문제

1. float

2. double : 실수형 타입 중 기본형

### String Type

**문자형 타입, 작은 정수나 문자 하나를 표현할 수 있는 타입을 의미**

1. char : 유니코드(unicode)를 사용하여 문자를 표현

|문자형 타입	|할당되는 메모리의 크기	|데이터의 표현 범위|
|:---------|:--------------------|:----------------|
|char	|2 바이트	|0 ~ 216|

### Logical Type

**논리형은 참(true)이나 거짓(false) 중 한 가지 값만을 가질 수 있는 불리언 타입을 의미**

1. boolean : 기본값은 false, 기본 타입 중 가장 작은 크기인 1바이트의 크기

|논리형 타입	|할당되는 메모리의 크기	|데이터의 표현 범위|
|:---------|:--------------------|:----------------|
|boolean	|1바이트	             |true 또는 false|
