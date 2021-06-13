---
layout: default
title: Exception
parent: Java
nav_order: 15
---

# Java Exception
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Error & Exception Basic

### What is Error? 

**에러(Error) : 자바에서 JVM이 실행중에 응용프로그램의 오류가 발생하는 것, 결국 실행이 불가능하게 됨**

이럴 경우 개발자는 프로그램이 정상적으로 실행할 수 있도록 해야되는데 에러를 처리할 방법이 없다면 이를 대처할 수 없게 됨

### What is Exception?

**예외(Exception) : 사용자의 잘못된 조작 또는 개발자의 잘못된 코딩으로 발생하는 프로그램 오류**

예외가 발생하면 프로그램은 곧바로 종료가 된다는 점에서 에러와 동일하지만, 예외는 예외처리를 통해 프로그램을 종료하지 않고 정상적인 실행상태가 유지될 수 있도록 함

일반예외(Exception)와 실행예외(Runtime Exception)가 있음

일반예외와 실행예외는 컴파일시 처리하는지 안하는지 차이, 두가지 모두 예외처리가 필요함

모든 예외클래스는 java.lang.Exception클래스를 상속받음 (일반예외는 Exception을 상속받고, 실행예외는 java.lang.RuntimeException을 상속받음)

자바에서는 예외를 클래스로 관리

JVM은 프로그램을 실행하는 도중에 예외가 발생하면 해당 예외클래스로 객체를 생성함, 그리고 나서 예외처리코드에서 예외객체를 이용할수 있게 함

### Exception

**자바소스를 컴파일하는 과정에서 예외처리코드가 필요한지 여부를 검사하는 예외, 컴파일예외라고도 함** 

예외처리코드가 없다면 컴파일 오류가 발생
	
### Runtime Exception

**컴파일과정에서 예외처리코드의 유무를 검사하지 않는 예외**

실행예외는 자바컴파일러가 예외를 체크하지 않기 때문에 오로지 개발자의 경험에 의해서 예외처리를 해야함

만약, 개발자가 실행예외에 대한 처리를 하는 로직을 코딩하지 않았을 경우 해당 예외가 발생한다면 프로그램은 곧바로 종료

---

## Runtime Exception

### ArrayIndexOutOfBounds

**배열에서 값이 없을때 찾으면 나오는 오류**

예제
{: .label .label-purple .mt-2}
<div class="code-example" markdown="1">
```java
public class ArrayIndexOutOfBoundsMain {
public static void main(String[] args) {
	System.out.println(args.length);
	System.out.println(args[0]);
	System.out.println(args[1]);
	System.out.println("프로그램종료!");
}	
}
```

### ClassCastingException

**클래스 형변환시 발생하는 예외**





























