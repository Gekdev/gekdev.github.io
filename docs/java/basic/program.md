---
layout: default
title: Program
parent: Basic
grand_parent: Java
nav_order: 1
---

# Basic Java Program
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Basic Java Program

자바 프로그램은 한 개 이상의 클래스(class)로 구성

이러한 클래스는 한 개 이상의 필드(field)나 메소드(method)로 구성

간단한 자바 프로그램의 기본 구조
{: .label .mt-2}
<div class="code-example" markdown="1">
class 클래스이름 {

필드의 선언

필드의 선언

...

메소드의 선언

메소드의 선언

...

}
</div>
```java
class Test {

    int field1;
    String field2;

    public void method1() {
        System.out.println("자바 프로그래밍!!");
    }

}
```

![](https://gekdev.github.io/docs/java/basic/example/pg_01.jpg)

### main() method

**자바 프로그램이 실행되면 맨 먼저 main() 메소드를 찾아 그 안의 모든 명령문을 차례대로 실행**

&#9656; 하나의 자바 프로그램에는 main() 메소드를 가지는 클래스가 반드시 하나는 존재

&#9656; main() 메소드는 반드시 public static void로 선언 (public, static은 제어자)

syntax
{: .label .mt-2}
```java
public static void main(String[] args) {

    ...

}
```

!note
<div class="code-example" markdown="1">
자바 클래스 파일(*.java)에 public 클래스(class)가 존재하면 소스 파일의 이름은 반드시 해당 public 클래스의 이름과 같아야 함

이러한 public 클래스는 자바 클래스 파일마다 단 한개만 가질 수 있음
</div>

### Statement

명령문 : **자바 프로그램의 동작을 명시하고, 이러한 동작을 컴퓨터에 알려주는 데 사용되는 문장**

자바의 모든 명령문은 반드시 세미콜론(;)

### Comment

**코드에 대한 이해를 돕는 설명을 적거나 디버깅을 위해 작성하는 일종의 메모**

* 한줄주석 : //

* 여러줄 주석 : /**/

&#9656; 자바에서 여러 줄 주석 안에 또 다른 한 줄 주석을 중첩해서 삽입가능 (여러줄안 여러줄은 안됨)

```java
1. 한 줄 주석
//

2. 여러줄 주석 
/* 

*/

---

/* 여러 줄

     // 이렇게 두 줄 주석 안에 또 다른 한 줄 주석을 삽입할 수 있습니다.

주석입니다. */
```
