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

선언된 위치에 따라 구분됨

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

---

## Fields Classification

선언된 위치에 따라서 구분된 필드들의 성격은 아래와 같음

### Static & Instance Initialize

**클래스 변수와 인스턴스 변수의 초깃값 표**

&#9656; 클래스 변수와 인스턴스 변수는 초기화를 하지 않아도 변수의 타입에 맞게 자동으로 초기화

&#8594; 하지만 지역 변수는 사용하기 전에 초기화하지 않으면, 자바 컴파일러가 오류를 발생

| 변수의 타입	   | 초깃값     |
|:----------------|:----------|
| char	          | '\u0000'  |
|byte, short, int |	0         |
|long	          | 0L        |
|float	          | 0.0F      |
|double	          | 0.0 또는 0.0D|
|boolean	      | false     |
|배열, 인스턴스 등	 | null      |

### Static & Instance Fields

* 클래스 변수(static variable) : 클래스 영역에 위치한 변수 중에서 static 키워드를 가지는 변수
    
    &#9656; 인스턴스를 생성하지 않고도 바로 사용 가능, 공유 변수(shared variable)라고도 함

    &#9656; 이 변수는 해당 클래스의 모든 인스턴스가 공유해야 하는 값을 유지하기 위해 사용

* 인스턴스 변수(instance variable) : 클래스 영역에 위치한 변수 중 static 키워드를 가지지 않는 변수
    
    &#9656; 이 변수는 인스턴스마다 가져야 하는 고유한 값을 유지하기 위해 사용

* 지역 변수(local variable) : 메소드나 생성자, 초기화 블록 내에 위치한 변수

| 변수	| 생성 시기	| 소멸 시기	| 저장 메모리	| 사용 방법 |
|:-------|:---------|:--------|:--------------|:---------|
|클래스 변수	|클래스가 메모리에 올라갈 때	|프로그램이 종료될 때	|메소드 영역	|클래스이름.변수이름|
|인스턴스 변수	|인스턴스가 생성될 때	|인스턴스가 소멸할 때	|힙 영역	|인스턴스이름.변수이름|
|지역 변수	|블록 내에서 변수의 선언문이 실행될 때	|블록을 벗어날 때	|스택 영역	|변수이름|

---

## Field Initialize

[TCP](http://tcpschool.com/java/java_member_initBlock)













