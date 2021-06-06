---
layout: default
title: Singleton
parent: Class
grand_parent: Java
nav_order: 7
---

# Class Singleton
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Singleton

**하나의 애플리케이션 내에서 단 하나만 생성되는 객체**

프로그램에서 단 한개의 객체만 생성하도록 해야 하는 경우가 있음

객체가 단 한개만 생성된다고 해서 싱글톤객체라고 함

### How to create Singleton?

1. 외부에서 new 연산자로 생성자를 호출할 수 없도록 막기

    &#8594; 생성자를 호출 한 수만큼 객체가 생성되기 때문에 private접근 제한자를 생성자 앞에 붙임
    
2. 클래스 자신의 타입으로 정적 필드 선언하고 자신의 객체를 생성하서 초기화

    내부에 new연산자로 생성자를 호출해서 객체를 생성해 초기화 
    
    정적필드(singleton)도 private접근 제한자를 붙여 외부에 필드 값 변경 불가하도록 막기
    
3. 외부에서 호출할 수 있는 정적 메소드인 getInstance() 선언

    외부에서 호출할 수 있는 정적메서드 getInstance()를 선언하고
    
    정적 필드인 singleton에서 참조하고 있는 자신의 객체를 리턴
    
```java
public class Singleton {
    //필드
	private static Singleton singleton = new Singleton();
	
	//생성자
	private Singleton() {};
	
	//메소드
	static Singleton getInstance() {
		return singleton;
	}                   
}

...
    
public class SingletonMain {
public static void main(String[] args) {
    
    Singleton xxx = Singleton.getInstance();
	System.out.println(xxx.toString());
	System.out.println(xxx.hashCode()); //헥사값을 10진수로 바꿈
	Singleton yyy = Singleton.getInstance();
	System.out.println(yyy.toString());
	System.out.println(yyy.hashCode()); //헥사값을 10진수로 바꿈
	Singleton zzz = Singleton.getInstance();
	System.out.println(zzz.toString());
	System.out.println(zzz.hashCode()); //헥사값을 10진수로 바꿈
	
	if(xxx == yyy) {
		System.out.println("동일객체, 메모리 주소가 동일합니다");
	}
	
	if(xxx.equals(zzz)) {
		System.out.println("동일객체, 메모리 주소가 동일합니다");
	}
                                        
}
}
```

![](https://gekdev.github.io/docs/java/class/example/singleton1.jpg)

### Example

Calculator Class Singleton 생성

```java
public class Calculator {

	//필드
	private static Calculator calculator = new Calculator();
	
	//생성자
	private Calculator(){}
	
	//메소드
	static Calculator getInstance() {
		return calculator;
	}
	
	int plus(int x, int y) {return x+y;}
	int minus(int x, int y) {return x-y;}
	int multiply(int x, int y) {return x*y;}
	int division(int x, int y) {return x/y;}
}
```

생성한 Singleton 사용

```java
public class CalculatorMain {
public static void main(String[] args) {
	
	/* 생성자를 private하는 순간 사용할 수 없음
	Calculator cal = new Calculator();
	System.out.println(cal.plus(100, 100));
	System.out.println(cal.minus(500, 100));
	*/
	
	Calculator cal = Calculator.getInstance();
	System.out.println(cal.plus(100, 100));
	System.out.println(cal.minus(500, 100));
	
}
}
```

