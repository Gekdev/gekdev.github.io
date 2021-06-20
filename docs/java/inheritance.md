---
layout: default
title: Inheritance
parent: Java
nav_order: 10
has_children : true
---

# Java Inheritance
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

상속(inheritance)이란?
상속(inheritance)이란 기존의 클래스에 기능을 추가하거나 재정의하여 새로운 클래스를 정의하는 것을 의미합니다.

이러한 상속은 캡슐화, 추상화와 더불어 객체 지향 프로그래밍을 구성하는 중요한 특징 중 하나입니다.

 

상속을 이용하면 기존에 정의되어 있는 클래스의 모든 필드와 메소드를 물려받아, 새로운 클래스를 생성할 수 있습니다.

이때 기존에 정의되어 있던 클래스를 부모 클래스(parent class) 또는 상위 클래스(super class), 기초 클래스(base class)라고도합니다.

그리고 상속을 통해 새롭게 작성되는 클래스를 자식 클래스(child class) 또는 하위 클래스(sub class), 파생 클래스(derived class)라고도 합니다.

상속의 장점
자바에서 클래스의 상속은 다음과 같은 장점을 가집니다.

 

1. 기존에 작성된 클래스를 재활용할 수 있습니다.

2. 자식 클래스 설계 시 중복되는 멤버를 미리 부모 클래스에 작성해 놓으면, 자식 클래스에서는 해당 멤버를 작성하지 않아도 됩니다.

3. 클래스 간의 계층적 관계를 구성함으로써 다형성의 문법적 토대를 마련합니다.

자식 클래스(child class)
자식 클래스(child class)란 부모 클래스의 모든 특성을 물려받아 새롭게 작성된 클래스를 의미합니다.

 

자바에서 자식 클래스는 다음과 같은 문법을 통해 선언합니다.

문법
class 자식클래스이름 extend 부모클래스이름 { ... }

 

다음 그림은 부모 클래스와 자식 클래스 간의 포함 관계를 나타낸 그림입니다.

 

상속 다이어그램

 

이처럼 부모 클래스는 자식 클래스에 포함된 것으로 볼 수 있습니다.

따라서 부모 클래스에 새로운 필드를 하나 추가하면, 자식 클래스에도 자동으로 해당 필드가 추가된 것처럼 동작합니다.

 

자식 클래스에는 부모 클래스의 필드와 메소드만이 상속되며, 생성자와 초기화 블록은 상속되지 않습니다.

또한, 부모 클래스의 접근 제어가 private이나 default로 설정된 멤버는 자식 클래스에서 상속받지만 접근할 수는 없습니다.

 

예제
class Parent {

    private int a = 10; // private 필드

    public int b = 20;  // public 필드

}

 

class Child extends Parent {

    public int c = 30;  // public 필드

    void display() {

①      // System.out.println(a); // 상속받은 private 필드 참조

②      System.out.println(b);    // 상속받은 public 필드 참조

③      System.out.println(c);    // 자식 클래스에서 선언한 public 필드 참조

    }

}

 

public class Inheritance01 {

    public static void main(String[] args) {

        Child ch = new Child();

        ch.display();

    }

}

코딩연습 ▶

실행 결과
20

30

 

위 예제의 ②번 라인에서는 자식 클래스의 메소드에서 부모 클래스에서 상속받은 public 필드를 참조하고 있습니다.

이처럼 자식 클래스에서 따로 선언하지 않은 필드라도 해당 이름의 필드를 부모 클래스에서 상속받았다면 문제가 없습니다.

하지만 주석 처리된 ①번 라인처럼 해당 필드가 부모 클래스의 private 필드라면 접근할 수 없으므로, 오류를 발생시킬 것입니다.

또한, 자식 클래스에서는 ③번 라인처럼 자신만의 필드나 메소드를 선언하여 사용할 수 있습니다.

 

자바에서 클래스는 단 한 개의 클래스만을 상속받는 단일 상속만이 가능합니다.
Object 클래스
자바에서 Object 클래스는 모든 클래스의 부모 클래스가 되는 클래스입니다.

따라서 자바의 모든 클래스는 자동으로 Object 클래스의 모든 필드와 메소드를 상속받게 됩니다.

 

즉, 자바의 모든 클래스는 별도로 extends 키워드를 사용하여 Object 클래스의 상속을 명시하지 않아도 Object 클래스의 모든 멤버를 자유롭게 사용할 수 있습니다.

자바의 모든 객체에서 toString()이나 clone()과 같은 메소드를 바로 사용할 수 있는 이유가 해당 메소드들이 Object 클래스의 메소드이기 때문입니다.

 

Object 클래스에 대한 더 자세한 사항은 자바 Object 클래스 수업에서 확인할 수 있습니다.

 

자바 Object 클래스 수업 확인 =>

---

## 메소드 오버라이딩(method overriding)
앞서 배운 오버로딩(overloading)이란 서로 다른 시그니처를 갖는 여러 메소드를 하나의 이름으로 정의하는 것이었습니다.

오버라이딩(overriding)이란 상속 관계에 있는 부모 클래스에서 이미 정의된 메소드를 자식 클래스에서 같은 시그니쳐를 갖는 메소드로 다시 정의하는 것이라고 할 수 있습니다.

 

자바에서 자식 클래스는 부모 클래스의 private 멤버를 제외한 모든 메소드를 상속받습니다.

이렇게 상속받은 메소드는 그대로 사용해도 되고, 필요한 동작을 위해 재정의하여 사용할 수도 있습니다.

즉, 메소드 오버라이딩이란 상속받은 부모 클래스의 메소드를 재정의하여 사용하는 것을 의미합니다.

오버라이딩의 조건
자바에서 메소드를 오버라이딩하기 위한 조건은 다음과 같습니다.

 

1. 오버라이딩이란 메소드의 동작만을 재정의하는 것이므로, 메소드의 선언부는 기존 메소드와 완전히 같아야 합니다.

    하지만 메소드의 반환 타입은 부모 클래스의 반환 타입으로 타입 변환할 수 있는 타입이라면 변경할 수 있습니다.

2. 부모 클래스의 메소드보다 접근 제어자를 더 좁은 범위로 변경할 수 없습니다

3. 부모 클래스의 메소드보다 더 큰 범위의 예외를 선언할 수 없습니다.

메소드 오버라이딩
자바에서는 메소드 오버라이딩을 통해 상속받은 부모 클래스의 메소드를 자식 클래스에서 직접 재정의할 수 있습니다.

 

다음 예제는 부모 클래스인 Parent 클래스의 display() 메소드를 자식 클래스인 Child 클래스에서 오버라이딩하는 예제입니다.

예제
class Parent {

    void display() { System.out.println("부모 클래스의 display() 메소드입니다."); }

}

class Child extends Parent {

    void display() { System.out.println("자식 클래스의 display() 메소드입니다."); }

}

 

public class Inheritance05 {

    public static void main(String[] args) {

        Parent pa = new Parent();

        pa.display();

        Child ch = new Child();

        ch.display();

        Parent pc = new Child();

        pc.display(); // Child cp = new Parent();

    }

}

코딩연습 ▶

실행 결과
부모 클래스의 display() 메소드입니다.

자식 클래스의 display() 메소드입니다.

자식 클래스의 display() 메소드입니다.

 

위의 예제에서 세 번째와 같은 인스턴스의 참조가 허용되는 이유는 바로 자바에서의 다형성(polymorphism) 때문입니다.

위와 같은 다형성에 대한 더 자세한 사항은 자바 다형성의 개념 수업에서 확인할 수 있습니다.

 

자바 다형성의 개념 수업 확인 =>

오버로딩과 오버라이딩
오버로딩과 오버라이딩은 그 단어의 유사함으로 인해 혼동하기 쉽습니다.

하지만 그 개념은 확실히 다르며, 그 차이점을 아는 것이 중요합니다.

 

간단히 정의하면 오버로딩(overloading)은 새로운 메소드를 정의하는 것입니다.

하지만 오버라이딩(overriding)은 상속받은 기존의 메소드를 재정의하는 것입니다.

 

다음 예제는 부모 클래스인 Parent 클래스의 display() 메소드를 자식 클래스인 Child 클래스에서 오버라이딩과 오버로딩을 둘 다 수행하는 예제입니다.

예제
class Parent {

    void display() { System.out.println("부모 클래스의 display() 메소드입니다."); }

}

class Child extends Parent {

    // 오버라이딩된 display() 메소드

    void display() { System.out.println("자식 클래스의 display() 메소드입니다."); }

    void display(String str) { System.out.println(str); } // 오버로딩된 display() 메소드

}

 

public class Inheritance06 {

    public static void main(String[] args) {

        Child ch = new Child();

        ch.display();

        ch.display("오버로딩된 display() 메소드입니다.");

    }

}

코딩연습 ▶

실행 결과
자식 클래스의 display() 메소드입니다.

오버로딩된 display() 메소드입니다.