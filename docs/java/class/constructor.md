---
layout: default
title: Constructor
parent: Class
grand_parent: Java
nav_order: 3
---

# Class Constructor
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Constructor Basic

### Initialize Instance Fields

클래스를 가지고 객체를 생성하면, 해당 객체는 메모리에 즉시 생성되는데, 이 객체는 모든 인스턴스 변수가 아직 초기화 되지 않은 상태임

자바에서 클래스 변수와 인스턴스 변수는 별도로 초기화 하지 않으면 자동 초기화됨

| 변수의 타입	   | 초깃값     |
|:----------------|:----------|
| char	          | '\u0000'  |
|byte, short, int |	0         |
|long	          | 0L        |
|float	          | 0.0F      |
|double	          | 0.0 또는 0.0D|
|boolean	      | false     |
|배열, 인스턴스 등	 | null      |

사용자가 원하는 방식으로 변수를 초기화 할때는 인스턴스 변수에는 private 변수가 있어서 사용자나 프로그램이 직접 접근할 수 없기 때문에 일반적인 방식으로 초기화 할 수 없음

따라서 private 인스턴스 변수에도 접근할 수 있는 초기화만을 위한 public 메소드가 필요함

초기화만을 위한 메소드는 객체가 생성된 후부터 사용되기 전까지 반드시 인스턴스 변수의 초기화를 위해 호출되어야 함

### What is Constructor?

**객체의 생성과 동시에 인스턴스 변수를 원하는 값으로 초기화할 수 있는 생성자(constructor)라는 메소드**

클래스를 가지고 객체를 생성하면, 해당 객체는 메모리에 즉시 생성

&#9656; 생성자는 메서드와 비슷하게 생겼지만 클래스명과 동일하고 리턴타입이 없음

&#8594; 이렇게 생성된 객체는 모든 인스턴스 변수가 아직 초기화되지 않은 상태

### Features of Constructor

1. 생성자는 반환값이 없지만, 반환 타입을 void형으로 선언하지 않음

2. 생성자는 초기화를 위한 데이터를 인수로 전달받을 수 있음

3. 객체를 초기화하는 방법이 여러 개 존재할 경우에는 하나의 클래스가 여러 개의 생성자를 가질 수 있음

4. 클래스에 내부에 기본생성자 이외의 생성자를 선언했을 경우에는 기본생성자는 자동생성되지 않음

5. 생성자가 명시적으로 선언된 것이 하나도 없다면 자바 컴파일러는 기본생성자를 자동으로 컴파일시에 자동으로 추가

&#8594; 생성자도 하나의 메소드이므로, 메소드 오버로딩이 가능하다는 의미

### Constructor Declaration

**클래스 생성자를 선언하는 문법**

클래스의 생성자(constructor)는 어떠한 반환값도 명시하지 않음에 주의 

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
1. 매개변수가 없는 생성자 선언

    클래스이름() { ... }                  

2. 매개변수가 있는 생성자 선언

    클래스이름(인수1, 인수2, ...) { ... }
</div>

### Constructor Call

**new 키워드를 사용하여 객체를 생성할 때 자동으로 생성자가 호출**

예제
{: .label .label-purple .mt-2
```java
public class Method02 {
    public static void main(String[] args) {
        Car myCar = new Car("아반떼", 2016, "흰색", 200); // 생성자의 호출
        System.out.println(myCar.getModel()); // 생성자에 의해 초기화되었는지를 확인함.
    }
}
```

---

## Default Constructor 

모든 클래스에는 하나 이상의 생성자가 정의되어 있어야 하지만 특별히 생성자를 정의하지 않고도 인스턴스를 생성할 수 있음
 
자바 컴파일러가 기본 생성자(default constructor)를 기본적으로 제공해 줌

### Features of Default Constructor 

&#9656; 기본 생성자는 매개변수를 하나도 가지지 않으며, 아무런 명령어도 포함하지 않음

&#9656; 컴파일 시 클래스에 생성자가 하나도 정의되어 있지 않으면, 자동으로 다음과 같은 기본 생성자를 추가

&#9656; 기본 생성자는 아무런 동작도 하지 않으므로, 인스턴스 변수를 클래스 필드에서 바로 초기화

&#9656; 인스턴스 변수의 초기화는 생성자를 사용하여 수행할 수도 있지만, 클래스 필드에서 바로 수행

&#9656; 매개변수를 가지는 생성자를 하나라도 정의했다면, 기본 생성자는 자동으로 추가되지 않음

&#9656; 매개변수를 가지는 생성자를 하나 이상 정의한 후 기본 생성자를 호출하면, 오류발생

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
클래스이름() {}
</div>
```java
Car() {}
```

---

## This()

**같은 클래스의 다른 생성자를 호출할 때 사용**

&#9656; 생성자 내부에서만 사용할 수 있음

&#9656; this() 메소드에 인수를 전달하면, 생성자 중에서 [메소드 시그니처]()가 일치하는 다른 생성자를 찾아 호출

&#9656; 내부적으로 다른 생성자를 호출하여 인스턴스 변수를 초기화

예제
{: .label .label-purple .mt-2}
```js
public class Car {
    
    public Car() {}

    public Car(String model) {
        this(model, null, 100); //매개변수가 동일한 생성자를 호출함
    }

    public Car(String model, String color) {
        this(model, color, 100);
    }

    public Car(String model, String color, int maxSpeed) {
        super();
        this.model = model;
        this.color = color;
        this.maxSpeed = maxSpeed;
    }
}
```
