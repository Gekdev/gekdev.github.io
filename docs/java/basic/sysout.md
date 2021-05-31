---
layout: default
title: Sysout
parent: Basic
grand_parent: Java
nav_order: 2
---

# Basic System.out.println()
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## System Class Basic

**자바 표준 입출력 클래스, 사용자가 프로그램과 대화하기 위해서 사용**

&#9656; 자바에서는 모든 것이 객체로 표현되므로, 입출력을 담당하는 수단 또한 모두 객체

&#9656; C언어의 printf() 함수나 scanf() 함수처럼 자바에서는 System이라는 표준 입출력 클래스를 정의하여 제공

&#9656; System 클래스는 java.lang 패키지에 포함되어 제공

&#9656; System 클래스에는 표준 입출력을 위해 다음과 같은 클래스 변수(static variable)가 정의

1. System.in : 표준 입력 작업을 수행

2. System.out : 표준 출력 작업을 수행

3. System.err : 표준 출력 작업을 수행

### System.out.println()

**모니터에 전달된 데이터를 출력한 후에 줄 바꿈까지 함**

&#9656; 표준 출력 스트림에 전달된 데이터는 스트림을 통해 출력 장치로 전달되어 출력

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
System.out.println(출력할데이터);

System.out.print(); // 줄바꿈을 하지 않음
</div>
```java
System.out.print(7);         // print() 메소드는 줄 바꿈을 하지 않음.

System.out.println(3);       // 정수 출력

System.out.println(3.14);    // 실수 출력

System.out.println("자바!"); // 문자열 출력

System.out.println("문자열끼리의 " + "연결도 가능합니다.");

System.out.println("숫자" + 3 + "과 문자열의 연결도 가능합니다.");
```

![](https://gekdev.github.io/docs/java/basic/example/pg_02.jpg)
