---
layout: default
title: Array 
parent: Java
nav_order: 6
has_children: true
---

# Java Array 
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Array Memory

### Memory Structure

모든 자바 프로그램은 자바 가상 머신(JVM)을 통해서 실행

자바 프로그램이 실행되면, JVM은 운영 체제로부터 해당 프로그램을 수행할 수 있도록 필요한 메모리를 할당받고 JVM은 용도에 따라 구분하여 관리함

![](https://gekdev.github.io/docs/java/array/example/img_java_memory_structure.png)

### Method Area

**자바 프로그램에서 사용되는 클래스에 대한 정보와 함께 클래스 변수(static variable)가 저장되는 영역**

&#9656; 코드에서 사용되는 클래스(~.class)들을 클래스로더(class loader)로 읽어서 상수, 필드, 메서드, 생성자등을 구분해서 저장

&#9656; 이 영역은 모든 쓰레드(프로그램)가 공유하는 영역
      
1. 자바 프로그램에서 특정 클래스가 사용

2. 해당 클래스의 클래스 파일(*.class)를 JVM이 읽어들임

3. 해당 클래스에 대한 정보를 메소드 영역에 저장

### Heap Area

**자바 프로그램에서 사용되는 모든 인스턴스 변수가 저장되는 영역**

객체와 배열이 생성(저장)됨

힙영역에 생성된 객체와 배열은 스택영역의 변수나 다른 객체의 필드에서 참조

1. new 키워드를 사용하여 인스턴스가 생성

2. JVM이 인스턴스의 정보를 힙 영역에 저장

3. 메모리의 낮은 주소에서 높은 주소의 방향으로 할당

Garbage Collector
{: .label .mt-2}
<div class="code-example" markdown="1">
참조하는 변수나 필드가 없다면 의미가 없는 객체가 되기 때문에 이 것을 쓰레기(garbage)로 취급

JVM은 쓰레기수집기(Garbage Collector)를 실행시켜 객체를 힙메모리 영역에서 자동을 제거 

그렇기 때문에 개발자는 제거를 위한 별도의 코드를 작성할 필요가 없음
</div>

### Stack Area

**자바 프로그램에서 메소드가 호출될 때 메소드의 스택 프레임이 저장되는 영역**

1. 자바 프로그램에서 메소드가 호출

2. 메소드의 호출과 관계되는 지역 변수와 매개변수를 스택 영역에 저장

스택 영역은 메소드의 호출과 함께 할당되며, 메소드의 호출이 완료되면 소멸

스택 영역에 저장되는 메소드의 호출 정보를 스택 프레임(stack frame)이라 함

스택 영역은 푸시(push) 동작으로 데이터를 저장하고, 팝(pop) 동작으로 데이터를 인출

스택은 후입선출(LIFO, Last-In First-Out) &#8594; 가장 늦게 저장된 데이터가 가장 먼저 인출

스택 영역은 메모리의 높은 주소에서 낮은 주소의 방향으로 할당
