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

**자바에서는 여러 형태의 타입을 미리 정의하여 제공함, 이게 기본 타입(primitive type)**

자바의 기본 타입은 모두 8종류가 제공 &#8594; 정수형, 실수형, 문자형 그리고 논리형 타입

![](https://gekdev.github.io/docs/java/datatype/example/primitive.png)

---

## Integer Type

**정수란 부호를 가지고 있으며, 소수 부분이 없는 수를 의미**

&#9656; byte, short, int, long타입이 있음

&#9656; int : 정수형 타입 중 기본이 되는 타입

&#8594; 내부적으로 정수형 중에서도 int형의 데이터를 가장 빠르게 처리

정수형 타입에 따른 메모리의 크기 및 데이터의 표현 범위
{: .label .mt-2}

| 정수형 타입	| 할당되는 메모리의 크기	| 데이터의 표현 범위 |
|:-------------|:---------------------|:----------------|
|byte	       | 1바이트	       | -128 ~ 127 |
|short	       | 2바이트	       | -215 ~ (215 - 1) = -32,768 ~ 32,767 |
|int	       | 4바이트	       | -231 ~ (231 - 1) = -2,147,483,648 ~ 2,147,483,647|
|long	       | 8바이트	       | -263 ~ (263 - 1) = -9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807|

&#9656; 정수형 데이터의 타입을 결정할 때에는 반드시 자신이 사용하고자 하는 데이터의 최대 크기를 고려해야 함

&#8594; 해당 타입이 표현할 수 있는 범위를 벗어난 데이터를 저장하면, 오버플로우(overflow)가 발생해 전혀 다른 값이 저장될 수 있기 때문

### Overflow

**해당 타입이 표현할 수 있는 최대 범위보다 큰 수를 저장할 때 발생하는 현상**

최상위 비트(MSB)를 벗어난 데이터가 인접 비트를 덮어쓰므로, 잘못된 결과를 얻을 수 있음

비슷하게 언더플로우(underflow) : 해당 타입이 표현할 수 있는 최소 범위보다 작은 수를 저장할 때 발생하는 현상이 있음 

예시
{: .label .label-purple .mt-2}
```java
public static void main(String[] args) {

    byte num1 = 127;
    byte num2 = -128;

    num1++; // 127 + 1
    num2--; // -128 - 1

    System.out.println(num1); // -128
    System.out.println(num2); // 127
}
```

### Exponential notation

**지수 표기법**

e 하나는 0을 나타냄

예시
{: .label .label-purple .mt-2}
```java
int i1 = 3000000;		//3000000
double d5 = 3e6;		//3000000.0
float f4 = 3e6f;		//3000000.0
double d6 = 3e-6; 		//3.0E-6
```

### Long Type

```java
long l1= 10;	// 10은 정수, 자동형변환(묵시적 형변환)
                // 10이라는 정수에서 long타입 l2로 형변환후 저장
long l2= 10l;	// 명시적으로 10l 즉, long타입으로 선언
long l3= 10L;	// 
// long l4 = 100000000000; 정수의 크기 초과 에러
long l4 = 100000000000l;
```

### Example

```java
public static void main(String[] args) {
    // byte 타입
    byte b1 = -128;
    byte b2 = 127;

    // char 타입
    char c1 = 'A'; //문자를 저장하지만 내부적으로 ascii 값 
    char c2 = 65; // 직접 ascii값으로 저장 
    char c3 = '\u0041'; //16진수(유니코드)값으로 저장
    System.out.println(c1 + "," + c2 + "," + c3);

    char c4 = '가';
    char c5 = 44032;
    char c6 = '\uac00';
    System.out.println(c4 + "," + c5 + "," + c6);

    int uniCode1 = c4;
    int uniCode2 = '나';
    System.out.println(uniCode1 + "," + uniCode2);

}

// 결과값
A,A,A
가,가,가
44032,45208
```

---

## Floating Point Type

**실수형 타입, 소수부나 지수부가 있는 수를 가리키며, 정수보다 훨씬 더 넓은 표현 범위를 가짐**

&#9656; float, double 타입이 있음

&#9656; double : 실수형 타입 중 기본형

| 실수형 타입	| 지수의 길이	| 가수의 길이	| 유효 자릿수 |
|:-------------|:--------------|:-------------|:-----------|
| float	| 8 비트	| 23 비트	| 소수 부분 6자리까지 오차없이 표현|
| double |	11 비트 | 52 비트 |	소수 부분 15자리까지 오차없이 표현|

|실수형 타입	| 할당되는 메모리의 크기 | 데이터의 표현 범위	| 리터럴 타입 접미사 |
|:---------|:--------------------|:----------------|:-----------------|
|float	|4바이트	|(3.4 X 10-38) ~ (3.4 X 1038)	| F 또는 f|
|double	| 8바이트	| (1.7 X 10-308) ~ (1.7 X 10308)|	D 또는 d (생략 가능함)|

### Double to Float

double값에 포함되는 실수 리터럴을 float타입으로 바꾸고 싶을때, 반대로도 가능

Double to Float : **f,F 접미사 사용**

Float to Double : **d,D 접미사 사용**

```java
float f;
f = 0.1234f; // 0.1234는 double 타입
f = 0.1111F;

double g;
g = 0.1234;
g = 0.1234d;
g = 0.1234D;
```

### Precision 

**실수는 정밀도에서 주의해야 함**

실수형 데이터의 오차는 자바뿐만 아니라 모든 프로그래밍 언어에서 발생하는 공통된 문제

즉, 정확한 값이 아니라 근사치가 리턴됨

```java
System.out.println(1.0 - 0.9);              //0.09999999999999998
System.out.println(1*0.1);                  //0.1
System.out.println((1.0*10 - 0.9*10)*0.1);  //0.1
```

### Example

```java
// 실수의 기본 데이터형은 double;
double d1 = 3.14;
double d2 = 3.14d;
double d3 = 3.14D;
System.out.println(d1+ "," +d2+ "," +d3);

// float f1 = 3.14; 8바이트에서 4바이트로 만들려면 짤림
float f1 = 3.14f;
float f2 = 3.14F;
System.out.println(f1+ "," +f2);
```

---

## String Type

**문자형 타입, 작은 정수나 문자 하나를 표현할 수 있는 타입을 의미**

&#9656; char : 유니코드(unicode)를 사용하여 문자를 표현, 음수가 없음

|문자형 타입	|할당되는 메모리의 크기	|데이터의 표현 범위|
|:---------|:--------------------|:----------------|
|char	|2 바이트	|0 ~ 216|

---

## Logical Type

**논리형은 참(true)이나 거짓(false) 중 한 가지 값만을 가질 수 있는 불리언 타입을 의미**

&#9656; boolean : 기본값은 false, 기본 타입 중 가장 작은 크기인 1바이트의 크기

|논리형 타입	|할당되는 메모리의 크기	|데이터의 표현 범위|
|:---------|:--------------------|:----------------|
|boolean	|1바이트	             |true 또는 false|

### Example

```java
public static void main(String[] args) {
    // boolean 타입의 값은 true, false 2가지의 값만 가지고 있음
    // 내부적으로는 true 1, false 0인 값을 저장하고 있음
    boolean stop = false;

    if(true) {
        System.out.println("Stop");     //stop
    } else {
        System.out.println("Start");
    }

    if(stop) {
        System.out.println("Stop");
    } else {
        System.out.println("Start");    //start
    }

    if(1==1) {
        System.out.println("Stop");     //stop
    } else {
        System.out.println("Start");
    }

    if(1==2) {
        System.out.println("Stop");
    } else {
        System.out.println("Start");    //start
    }

    if(!stop) {
        System.out.println("Stop");     //stop
    } else {
        System.out.println("Start");
    }


    }
```