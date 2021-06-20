---
layout: default
title: Enum 
parent: Basic API 
grand_parent: Java
nav_order: 6
---

# Basic API Enum
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

Enum 클래스
열거체(enumeration type)
C언어와 C++에서는 열거체를 사용할 수 있지만, JDK 1.5 이전의 자바에서는 열거체를 사용할 수 없었습니다.

하지만 JDK 1.5부터는 C언어의 열거체보다 더욱 향상된 성능의 열거체를 정의한 Enum 클래스를 사용할 수 있습니다.

 

이와 같은 자바의 열거체는 다음과 같은 장점을 가집니다.

 

1. 열거체를 비교할 때 실제 값뿐만 아니라 타입까지도 체크합니다.

2. 열거체의 상숫값이 재정의되더라도 다시 컴파일할 필요가 없습니다.

열거체의 정의 및 사용
자바에서는 enum 키워드를 사용하여 열거체를 정의할 수 있습니다.

문법
enum 열거체이름 { 상수1이름, 상수2이름, ... }

예제
enum Rainbow { RED, ORANGE, YELLOW, GREEN, BLUE, INDIGO, VIOLET }

 

이렇게 정의된 열거체를 사용하는 방법은 다음과 같습니다.

문법
열거체이름.상수이름

예제
Rainbow.RED

열거체의 상숫값 정의 및 추가
위와 같이 정의된 열거체의 첫 번째 상숫값은 0부터 설정되며, 그다음은 바로 앞의 상숫값보다 1만큼 증가되며 설정됩니다.

 

또한, 불규칙한 값을 상숫값으로 설정하고 싶으면 상수의 이름 옆에 괄호(())을 추가하고, 그 안에 원하는 상숫값을 명시할 수 있습니다.

하지만 이때에는 불규칙한 특정 값을 저장할 수 있는 인스턴스 변수와 생성자를 다음 예제와 같이 별도로 추가해야만 합니다.

예제
enum Rainbow {

    RED(3), ORANGE(10), YELLOW(21), GREEN(5), BLUE(1), INDIGO(-1), VIOLET(-11);

 

    private final int value;

    Rainbow(int value) { this.value = value; }

    public int getValue() { return value; }

}

java.lang.Enum 클래스
Enum 클래스는 모든 자바 열거체의 공통된 조상 클래스입니다.

Enum 클래스에는 열거체를 조작하기 위한 다양한 메소드가 포함되어 있습니다.

values() 메소드
values() 메소드는 해당 열거체의 모든 상수를 저장한 배열을 생성하여 반환합니다.

이 메소드는 자바의 모든 열거체에 컴파일러가 자동으로 추가해 주는 메소드입니다.

 

예제
enum Rainbow { RED, ORANGE, YELLOW, GREEN, BLUE, INDIGO, VIOLET }

 

public class Enum01 {

    public static void main(String[] args) {

        Rainbow[] arr = Rainbow.values();

        for (Rainbow rb : arr) {

            System.out.println(rb);

        }

    }

}

코딩연습 ▶

실행 결과
RED

ORANGE

YELLOW

GREEN

BLUE

INDIGO

VIOLET

valueOf() 메소드
valueOf() 메소드는 전달된 문자열과 일치하는 해당 열거체의 상수를 반환합니다.

 

예제
enum Rainbow { RED, ORANGE, YELLOW, GREEN, BLUE, INDIGO, VIOLET }

 

public class Enum02 {

    public static void main(String[] args) {

        Rainbow rb = Rainbow.valueOf("GREEN");

        System.out.println(rb);

    }

}

코딩연습 ▶

실행 결과
GREEN

ordinal() 메소드
ordinal() 메소드는 해당 열거체 상수가 열거체 정의에서 정의된 순서(0부터 시작)를 반환합니다.

이때 반환되는 값은 열거체 정의에서 해당 열거체 상수가 정의된 순서이며, 상숫값 자체가 아님을 명심해야 합니다.

 

예제
enum Rainbow { RED, ORANGE, YELLOW, GREEN, BLUE, INDIGO, VIOLET }

 

public class Enum03 {

    public static void main(String[] args) {

        int idx = Rainbow.YELLOW.ordinal();

        System.out.println(idx);

    }

}

코딩연습 ▶

실행 결과
2

 

다음 예제는 불규칙적인 상숫값을 가지는 열거체에서 ordinal() 메소드를 사용한 예제입니다.

예제
enum Rainbow {

    RED(3), ORANGE(10), YELLOW(21), GREEN(5), BLUE(1), INDIGO(-1), VIOLET(-11);

 

    private final int value;

    Rainbow(int value) { this.value = value; }

    public int getValue() { return value; }

}

 

public class Enum04 {

    public static void main(String[] args) {

        System.out.println(Rainbow.YELLOW.ordinal());

    }

}

코딩연습 ▶

실행 결과
2

대표적인 Enum 메소드
Enum 클래스의 메소드는 다음과 같습니다.

메소드	설명
static E values()	해당 열거체의 모든 상수를 저장한 배열을 생성하여 반환함.
static E valueOf(String name)	전달된 문자열과 일치하는 해당 열거체의 상수를 반환함.
protected void finalize()	해당 Enum 클래스가 final 메소드를 가질 수 없게 됨.
String name()	해당 열거체 상수의 이름을 반환함.
int ordinal()	해당 열거체 상수가 열거체 정의에서 정의된 순서(0부터 시작)를 반환함.