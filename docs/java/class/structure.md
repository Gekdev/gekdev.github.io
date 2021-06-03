---
layout: default
title: Method
parent: Class
grand_parent: Java
nav_order: 2
---

# Class Method
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Method

### What is Method?

**어떠한 특정 작업을 수행하기 위한 명령문의 집합**

&#8594; 객체의 기능을 표현함

### Why Use Method?

&#9656; 중복되는 코드의 반복적인 프로그래밍을 피함

&#9656; 모듈화로 인해 전체적인 코드의 가독성이 좋아짐 

&#9656; 프로그램에 문제가 발생하거나 기능의 변경이 필요할 때도 손쉽게 유지보수가 가능

★ 되도록 하나의 메소드가 하나의 기능만 수행하도록 작성하는게 좋음

### Method Declaration

일반 함수를 정의할때와 비슷함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
접근제어자 반환타입 메소드이름(매개변수목록) { // 선언부

    // 구현부

}

&#9656; 접근 제어자 : 해당 메소드에 접근할 수 있는 범위

&#9656; 반환 타입(return type) : 메소드가 모든 작업을 마치고 반환하는 데이터의 타입

&#9656;  메소드 이름 : 메소드를 호출하기 위한 이름

&#9656; 매개변수 목록(parameters) : 메소드 호출 시에 전달되는 인수의 값을 저장할 변수들

&#9656; 구현부 : 메소드의 고유 기능을 수행하는 명령문의 집합
</div>
```java

```

### Method Signature

**메소드 시그니처, 메소드의 선언부에 명시되는 매개변수의 리스트**

&#9656; 만약 두 메소드가 매개변수의 개수와 타입, 그 순서까지 모두 같다면, 이 두 메소드의 시그니처는 같다고 할 수 있음

&#9656; 하나의 클래스에 같은 이름의 메소드를 둘 이상 정의할수 없지만 메소드 오버로딩을 사용하면 가능 함 (메소드 시그니처가 달라야함)

### Method Call

**참조 연산자(.)를 사용하여 호출**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
1. 매개변수가 없는 메소드의 호출

    객체참조변수이름.메소드이름();

2. 매개변수가 있는 메소드의 호출

    객체참조변수이름.메소드이름(인수1, 인수2, ...); 
</div>
```java

```

---

## Method Overloading

### What is Overloading?

**메소드 오버로딩, 서로 다른 시그니처를 갖는 같은 이름의 메소드를 중복하여 정의하는것**

### Overloaing Condition

1. 메소드의 이름이 같아야 함

2. 메소드의 시그니처, 즉 매개변수의 개수 또는 타입이 달라야 함

&#8594; 메소드의 반환 타입과는 관계없음

예제
{: .label .label-purple .mt-2}
```java
// 대표적인 예 printIn()
// 전달받는 매개변수의 타입에 따라 다음과 같이 다양한 원형 중에서 적절한 원형을 호출
1. println()

2. println(boolean x)

3. println(char x)

4. println(char[] x)

5. println(double x)

6. println(float x)

7. println(int x)

8. println(long x)

9. println(Object x)

10. println(String x)
```

### Overloading Advantage

&#9656; 메소드에 사용되는 이름을 절약할 수 있음

&#9656; 메소드를 호출할 때 전달해야 할 매개변수의 타입이나 개수에 대해 크게 신경을 쓰지 않고 호출할 수 있게됨

&#8594; 객체 지향 프로그래밍의 특징 중 하나인 다형성(polymorphism)을 구현

### Kind of Overloading




