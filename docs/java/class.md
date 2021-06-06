---
layout: default
title: Class 
parent: Java
nav_order: 7
has_children: true
---

# Java Class 
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## OOP, Object-Oriented Programming

**객체 지향 프로그래밍에서는 모든 데이터를 객체(object)로 취급**

&#8594; 객체가 바로 프로그래밍의 중심

쉽게 얘기하자면 객체는 사물, 객체의 상태(state)와 행동(behavior)을 구체화하는 형태의 프로그래밍이 바로 객체 지향 프로그래밍

**이때 객체를 만들어 내기 위한 설계도와 같은 개념을 클래스(class)라고 함**

---

## Class 

### Class Basic

**객체를 정의하는 틀 또는 설계도와 같은 의미로 사용**

&#8594; 자바에서는 이러한 설계도인 클래스를 가지고, 여러 객체를 생성하여 사용

&#9656; 클래스 구성물에는 필드, 메소드, 생성자가 있음

* 필드(field) : 속성을 표현, 클래스에 포함된 변수

* 메소드(method) : 기능을 표현, 특정 작업을 수행하기 위한 명령문의 집합

* 생성자(constructor) : 생성된 객체의 필드를 초기화

**클래스란 객체 지향 프로그래밍의 추상화라는 개념을 직접 구현한 것**

### Class Declaration

**클래스 선언방법**

&#9656; 개발자의 편의를 위해 유용하게 사용할 수 있는 많은 수의 클래스를 미리 정의하여 제공

&#9656; 개발자가 원하는 동작을 하는 새로운 클래스를 손쉽게 작성할 수 있음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
![](https://gekdev.github.io/docs/java/class/example/img_java_class_definition.png)

&#9656; 접근 제어자 : 정보 은닉(data hiding)을 위한 키워드
</div>
```java
접근제어자 class 클래스이름 {

    접근제어자 필드1의타입 필드1의이름;
    접근제어자 필드2의타입 필드2의이름;
    ...

    접근제어자 메소드1의 원형
    접근제어자 메소드2의 원형
    ...

};
```

---

## Instance

**인스턴스, 클래스 타입의 객체**

클래스를 사용하기 위해 해당 클래스 타입의 객체를 선언해야 함 &#8594; 클래스의 인스턴스 화

**즉, 클래스로 만들어낸 복제품을 instance라고 함**

&#9656; 하나의 클래스로부터 여러 개의 인스턴스를 생성할 수 있음

&#9656; 생성된 인스턴스는 독립된 메모리 공간에 저장된 자신만의 필드를 가짐

&#9656; 해당 클래스의 모든 메소드(method)는 해당 클래스에서 생성된 모든 인스턴스가 공유

### Create Instance

인스턴스를 생성하는데에는 3가지 방법이 있음

1. 방법1) 참조 변수 선언

    <div class="code-example" markdown="1">
    클래스이름 객체참조변수이름;
    </div>
    ```java
    Car myCar;
    ```

2. 방법2) new 키워드로 인스턴스를 생성

    해당 인스턴스의 주소를 미리 선언한 참조변수에 저장후 사용

    <div class="code-example" markdown="1">
    객체참조변수이름 = new 클래스이름();
    </div>
    ```java
    myCar = new Car();
    ```

3. 방법3) 참조변수의 선언과 인스턴스의 생성 동시에 하기
    
    <div class="code-example" markdown="1">
    클래스이름 객체참조변수이름 = new 클래스이름();
    </div>
    ```java
    Car myCar = new Car();
    ```
    
---

## Example

* 클래스(class)

    - 차(Car) : 설계도

* 필드(field)

    - car.modelName = "람보르기니" 

    - car.modelYear = 2016

    - car.color = "주황색"

    - car.maxSpeed = 350

* 메소드(method)

    - car.accelerate()

    - car.brake()

* 인스턴스(instance)

    - 내 차(myCar) : 설계도에 의해 생산된 차량

    - 친구 차(friendCar) : 설계도에 의해 생산된 또 다른 차량

예시
{: .label .label-purple .mt-2}
```java
// 클래스 이름
class Car {                    

    // 필드
    private String modelName;  
    private int modelYear;    

    // 생성자
    Car(String modelName, int modelYear) {
        this.modelName = modelName;
        this.modelYear = modelYear;
    }

    // 메소드
    public String getModel() {
        return this.modelYear + "년식 " + this.modelName + " " + this.color;
    }

}
```
