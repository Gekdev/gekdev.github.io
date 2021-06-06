---
layout: default
title: Field
parent: Class
grand_parent: Java
nav_order: 1
---

# Class Field
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Field Basic

### What is Field?

**클래스에 포함된 변수(variable)를 의미**

&#9656; 필드는 객체의 고유데이터, 부품객체, 상태정보를 저장하는 곳

&#9656; 선언형태는 변수와 비슷하지만 필드를 변수라고 부르지 않음

&#9656; 변수는 생성자와 메서드에서만 사용되고 생성자와 메서드가 실행이 종료가 되면 자동으로 소멸
   
&#9656; 선언된 위치에 따라 구분됨

1. 클래스 변수(static variable)

2. 인스턴스 변수(instance variable)

3. 지역 변수(local variable)

예제
{: .label .label-purple .mt-2}
```java
class Car {
    static int modelOutput; // 클래스 변수
    String modelName;       // 인스턴스 변수

    void method() {
        int something = 10; // 지역 변수
    }

}
```

### Static Fields

클래스 변수(static variable) : **클래스 영역에 위치한 변수 중에서 static 키워드를 가지는 변수**
    
&#9656; 인스턴스를 생성하지 않고도 바로 사용 가능, 공유 변수(shared variable)라고도 함

&#9656; 해당 클래스의 모든 인스턴스가 공유해야 하는 값을 유지하기 위해 사용

### Instance Fields

인스턴스 변수(instance variable) : **클래스 영역에 위치한 변수 중 static 키워드를 가지지 않는 변수**
    
&#9656; 인스턴스마다 가져야 하는 고유한 값을 유지하기 위해 사용

### Local variable

지역 변수(local variable) : **메소드나 생성자, 초기화 블록 내에 위치한 변수**

### Field Features

| 변수	| 생성 시기	| 소멸 시기	| 저장 메모리	| 사용 방법 |
|:-------|:---------|:--------|:--------------|:---------|
|클래스 변수	|클래스가 메모리에 올라갈 때	|프로그램이 종료될 때	|메소드 영역	|클래스이름.변수이름|
|인스턴스 변수	|인스턴스가 생성될 때	|인스턴스가 소멸할 때	|힙 영역	|인스턴스이름.변수이름|
|지역 변수	|블록 내에서 변수의 선언문이 실행될 때	|블록을 벗어날 때	|스택 영역	|변수이름|


---

## Field Initialize

### Static & Instance Initialize

**클래스 변수와 인스턴스 변수의 초깃값 표**

&#9656; 클래스 변수와 인스턴스 변수는 초기화를 하지 않아도 변수의 타입에 맞게 자동으로 초기화됨

&#9656; 지역 변수는 사용하기 전에 초기화하지 않으면, 자바 컴파일러가 오류를 발생

★ 따라서 지역 변수와 마찬가지로 적절한 값으로 초기화한 후에 사용하는 것이 좋음

기본 초기값

| 변수의 타입	   | 초깃값     |
|:----------------|:----------|
| char	          | '\u0000'  |
|byte, short, int |	0         |
|long	          | 0L        |
|float	          | 0.0F      |
|double	          | 0.0 또는 0.0D|
|boolean	      | false     |
|배열, 인스턴스 등	 | null      |

### How to Initialize Fields

1. 명시적 초기화

    **지역 변수를 초기화하는 방법과 마찬가지로 필드를 선언과 동시에 초기화**
    
    ```java
    class Field {

        static int classVar = 10; // 클래스 변수의 명시적 초기화
        int instanceVar = 20;     // 인스턴스 변수의 명시적 초기화

    }
    ```

2. 생성자를 이용한 초기화

    **객체의 생성과 동시에 필드를 초기화하는 방법**
    
    생성자를 이용한 초기화는 인스턴스를 생성할 때까지 필드를 초기화할 수 없음

3. 초기화 블록을 이용한 초기화

    **초기화 블록이란 클래스 필드의 초기화만을 담당하는 중괄호({})로 둘러싸인 블록**

    생성자보다 먼저 호출되며, static 키워드의 유무에 따라 인스턴트와 클래스로 나뉨

### Initialization block

1. 인스턴스 초기화 블록

    **단순히 중괄호({})만을 사용하여 정의**
    
    생성자와 마찬가지로 인스턴스가 생성될 때마다 실행
    
    하지만 언제나 인스턴스 초기화 블록이 생성자보다 먼저 실행
    
    생성자와 인스턴트 초기화 블럭은 거의 비슷해서 잘 사용되지 않지만 여러개의 생성자가 있으면 모든 생성자에서 공통으로 사용되는 코드를 작성해서 코드의 중복을 막음

    ```java
    class Car {
        private String modelName;
        private int modelYear;

        { // 인스턴스 초기화 블록
            this.currentSpeed = 0;
        }
    }
    ```
    
2. 클래스 초기화 블록

    **인스턴스 초기화 블록에 static 키워드를 추가하여 정의**
    
    클래스 초기화 블록은 클래스가 처음으로 메모리에 로딩될 때 단 한 번만 실행
    
    생성자나 인스턴스 초기화 블록으로는 수행할 수 없는 클래스 변수의 초기화를 수행할 때 사용
    
    ```java
    class InitBlock {
        static int classVar; // 클래스 변수
        int instanceVar;     // 인스턴스 변수

        static { // 클래스 초기화 블록을 이용한 초기화
            classVar = 10;
        }

    }
    ```
    
### Initialization Order

필드의 초기화 순서

**여러 번 초기화하면, 제일 마지막으로 초기화한 값이 남음**

1. 클래스 변수 : 기본값 → 명시적 초기화 → 클래스 초기화 블록

2. 인스턴스 변수 : 기본값 → 명시적 초기화 → 인스턴스 초기화 블록 → 생성자

예시
{: .label .label-purple .mt-2}
```java
class InitBlock {
    static int classVar = 10;         // 클래스 변수의 명시적 초기화
    int instanceVar = 10;             // 인스턴스 변수의 명시적 초기화
    static { classVar = 20; }         // 클래스 초기화 블록을 이용한 초기화
    { instanceVar = 20; }             // 인스턴스 초기화 블록을 이용한 초기화
    InitBlock() { instanceVar = 30; } // 생성자를 이용한 초기화
}

결과값 classVar = 20, instanceVar = 30
```