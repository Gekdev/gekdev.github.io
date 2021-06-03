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

객체의 기능을 표현하는 함수

### Why Use Method?

1. 중복되는 코드의 반복적인 프로그래밍을 피함

2. 모듈화로 인해 전체적인 코드의 가독성이 좋아짐 

3. 프로그램에 문제가 발생하거나 기능의 변경이 필요할 때도 손쉽게 유지보수가 가능

★ 되도록 하나의 메소드가 하나의 기능만 수행하도록 작성하는게 좋음

### Method Declaration

일반 함수를 정의할때와 비슷하게 정의함

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

**메소드의 선언부에 명시되는 매개변수의 리스트**

&#9656; 만약 두 메소드가 매개변수의 개수와 타입, 그 순서까지 모두 같다면, 이 두 메소드의 시그니처는 같다고 할 수 있음

&#9656; 하나의 클래스에 같은 이름의 메소드를 둘 이상 정의할수 없지만 메소드 오버로딩을 사용하면 가능 함 (메소드 시그니처가 달라야 오버로딩 사용 가능)

### Method Call

**참조 연산자(.)를 사용하여 호출**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
1. 매개변수가 없는 메소드의 호출

    **객체참조변수이름.메소드이름();**

2. 매개변수가 있는 메소드의 호출

    **객체참조변수이름.메소드이름(인수1, 인수2, ...);**
</div>
```java

```

---

## Methods classification

static 키워드의 여부에 따라 다음과 같이 구분됨

1. 클래스 메소드(static method)

2. 인스턴스 메소드(instance method)

예제
{: .label .label-purple .mt-2}
```java
class Car {
    // 인스턴스 변수
    boolean door;                       

    // 인스턴스 메소드
    void openDoor() {                   
        door = true;
    }

    // 클래스 메소드
    static void toggleDoor(boolean d) {
        return !d;
    }

}
```

### Class & Instance Method

* 클래스 메소드(static method) : static 키워드를 가지는 메소드

    &#9656; 클래스 메소드는 클래스 변수와 마찬가지로 인스턴스를 생성하지 않고도 바로 사용

    &#9656; 메소드 내부에서 인스턴스 변수를 사용할 수 없음

    &#8594; 메소드 내부에서 인스턴스 변수나 인스턴스 메소드를 사용하지 않는 메소드를 클래스 메소드로 정의하는 것이 일반적
 
* 인스턴스 메소드(instance method) : static 키워드를 가지지 않는 메소드

예제
{: .label .label-purple .mt-2}
```java
class Method {
    int a = 10, b = 20;                            // 인스턴스 변수
    int add() { return a + b; }                    // 인스턴스 메소드
    static int add(int x, int y) { return x + y; } // 클래스 메소드
}

public class Member02 {
    public static void main(String[] args) {

        System.out.println(Method.add(20, 30)); // 클래스 메소드의 호출
        Method myMethod = new Method();         // 인스턴스 생성
        System.out.println(myMethod.add());     // 인스턴스 메소드의 호출
    }

}
```

---

## Method Overloading

### What is Overloading?

**서로 다른 시그니처를 갖는 같은 이름의 메소드를 중복하여 정의하는것**

&#9656; 메소드 오버로딩의 조건

1. 메소드의 이름이 같아야 함

2. 메소드의 시그니처, 즉 매개변수의 개수 또는 타입이 달라야 함

&#8594; 메소드의 반환 타입과는 관계없음

대표적인 예 printIn()
{: .label .label-purple .mt-2}
```java
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

&#9656; 객체 지향 프로그래밍의 특징 중 하나인 다형성(polymorphism)을 구현

### This Reference Variable

**This 참조변수는 인스턴스가 바로 자기 자신을 참조하는데 사용하는 변수**

this 참조 변수는 해당 인스턴스의 주소를 가리킴

생성자의 매개변수 이름과 인스턴스 변수의 이름이 같을 경우에는 인스턴스 변수 앞에 this 키워드를 붙여 구분해야 함

this 참조 변수를 사용할 수 있는 영역은 인스턴스 메소드뿐이며, 클래스 메소드에서는 사용할 수 없음

모든 인스턴스 메소드에는 this 참조 변수가 숨겨진 지역 변수로 존재

```java
class Car {

    private String modelName;
    private int modelYear;
    private String color;
    private int maxSpeed;
    private int currentSpeed;

    Car(String modelName, int modelYear, String color, int maxSpeed) {
        this.modelName = modelName;
        this.modelYear = modelYear;
        this.color = color;
        this.maxSpeed = maxSpeed;
        this.currentSpeed = 0;
    }

    ...

}
```

### Kind of Overloading

---

## Recursice Call

**재귀호출, 메소드 내부에서 해당 메소드가 또다시 호출되는 것을 의미**

끊임없이 반복되므로 메소드 내에 재귀호출을 중단하도록 조건이 변경될 명령문을 반드시 포함해야 함

중단문이 없으면 stack overflow(메모리 구조 중 스택(stack) 영역에서 해당 프로그램이 사용할 수 있는 메모리 공간 이상을 사용하려고 할 때 발생)가 발생함

재귀 호출은 알고리즘이나 자료 구조론에서는 매우 중요한 개념 중 하나 &#8594; 직관적인 프로그래밍

### Concept of Recursive Call

재귀 호출을 사용하여 1부터 n까지의 합을 구하는 recursiveSum() 메소드

1. 재귀 알고리즘을 구상

    1. 1부터 4까지의 합은 1부터 3까지의 합에 4를 더하면 됩니다.

    2. 1부터 3까지의 합은 1부터 2까지의 합에 3을 더하면 됩니다.

    3. 1부터 2까지의 합은 1부터 1까지의 합에 2를 더하면 됩니다.

    4. 1부터 1까지의 합은 그냥 1입니다.

2. 의사 코드(pseudo code) 작성

    의사코드 : 특정 프로그래밍 언어의 문법에 맞춰 작성된 것이 아닌, 일반적인 언어로 알고리즘을 표현한 코드

    ```java
    시작
        1. n이 1이 아니면, n과 1부터 (n-1)까지의 합을 더한 값을 반환함.
        2. n이 1이면, 그냥 1을 반환함.
    끝
    ```

3. 코드작성

    if문은 재귀호출을 중단하기 위해 반드시 필요함
    
    
    
    ```java
    int recursiveSum(int n) {
        if (n == 1) {                 // n이 1이면, 그냥 1을 반환함.
            return 1;
        }
        return n + recursiveSum(n-1); // n이 1이 아니면, n을 1부터 (n-1)까지의 합과 더한 값을 반환함.

    }
    ```





