---
layout: default
title: Lambda
parent: Java
nav_order: 18
---

# Java Lamda Experssions
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Lamda Experssions

### what is Lambda?

**익명함수를 생성하기 위한 식**

&#9656; 자바는 람다식을 함수적 인터페이스의 익명 구현 객체로 취급

&#9656; 람다식의 형태는 매개변수를 가진 코드블럭이지만 런타임시에는 익명구현객체를 생성

&#9656; 어떤 인터페이스를 구현할지는 대입되는 인터페이스에 달려있음

&#9656; 객체지향언어보다 함수지향언어에 가까움

### Target Funtion 

&#9656; 람다식형태는 매개변수를 가진 코드블럭이기 때문에 자바의 메서드를 선언하는 것처럼 보여지지만 자바에서는 메서드를 단독으로 선언할 수 없고 항상 클래스의 멤버로 선언하기 때문에 람다식은 **단순히 메서드를 선선하는게 아니라 객체를 생성하는 것**

&#9656; 람다식은 인터페이스 변수에 대입됨 즉, "인터페이스의 익명구현객체를 생성"

&#9656; 인터페이스는 직접 객체화 할 수 없기 때문에 구현 클래스가 필요한데 람다식은 클래스 선언 없이 익명구현객체를 직접 생성하고 객체화 함

**람다식은 대입될 인터페이스의 종류에 따라 달라지기 때문에 람다식이 대입될 인터페이스를 람다식의 타겟타입(Target Type)이라고 함**

### Functional Interface

**함수적 인터페이스, @FunctionalInterface**

&#9656; 모든 인터페이스를 람다식의 타겟타입으로 사용할 수는 없음

&#9656; 람다식이 하나의 메서드를 정의하기 때문에 두 개 이상의 추상메서드가 선언된 인터페이스는 람다식을 이용할 수 없음

&#9656; 하나의 추상메서드가 선언된 인터페이스만이 람다식의 타겟타입이 될 수 있는데 이러한 인터페이스를 함수적 인터페이스라고 함

&#9656; 함수적 인터페이스를 작성할 때 2개 이상의 추상메서드가 선언되지 않도록 컴파일러가 확인할 수 있도록 인터페이스 선언시에 @FunctionalInterface 애너테이션을 선언

### History of Lambda

람다식은 수학자 알론조 처치(Alonzo Church)가 발표한 계산법

제자 존 메카시(John McCharthy)가 프로그래밍 언어에 도입

&#8594; 람다 계산법에서 사용된 식을 프로그래밍 언어에 접목하게 된것

### Why Use Lambda?

1. 코드가 간결해짐

2. 컬렉션요소(대용량 데이터)를 필터링 또는 매핑해 쉽게 집계함

### Syntax of Lambda

&#9656; 하나의 매개변수만 있을 경우에는 괄호() 생략가능

&#9656; 하나의 실행문만 있다면 중괄호 {} 생략가능

&#9656; 매개변수가 없다면 괄호 생략 불가

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
(매개변수 ... ) -> { ... 실행문 ... }

실행문이 한 문장일경우 실행문의 {}를 생략해도 됨
</div>
```java
public class FuntionalInterfaceMain {
public static void main(String[] args) {

	//추상메서드는 구현객체에서 반드시 정의해야함
	MyFuncInter fi = new MyFuncInter() {	
		@Override
		public void method() { System.out.println("추상메서드 구현 - 익명구현객체"); }
	};
	fi.method(); //추상메서드 구현 - 익명구현객체
	
	//람다식
	fi = () -> { System.out.println("추상메서드 구현 - 람다식(1)");	};
	fi.method(); //추상메서드 구현 - 람다식(1)	
	
	fi = () -> System.out.println("추상메서드 구현 - 람다식(2)");
	fi.method(); //추상메서드 구현 - 람다식(2)
	
}
}

//메소드를 하나만 가짐
@FunctionalInterface
interface MyFuncInter{
	void method();
}
```

### Lambda with Arguments

&#9656; 람다식에서는 런타임시에 대입되는 값에 따라 자동으로 인식될 수 있기 때문에 람다식에서는 매개변수의 타입을 일반적으로 언급하지는 않음

예제
{: .label .label-purple .mt-2}
```java
public class FunctionalInterfaceMain {
public static void main(String[] args) {
	
	MyFuncInter fi;
	
	fi = (int x) -> {
		int result = (x * 5);
		System.out.println(x + " * 5 = " + result);
	};
	fi.method(5);   //25
	
	fi = (x) -> System.out.println(x + " * 5 = " + x*5 );
	fi.method(10);  //50
	
	fi = x -> System.out.println(x + " * 10 = " + x*10 );
	fi.method(10);  
	
}
}

@FunctionalInterface
interface MyFuncInter{
	void method(int x);
}
```

### Lambda Return

void가 아닌 리턴값이 있는 interface 가상메소드를 사용한다면 Lambda에 리턴값이 있어야함

실행문이 리턴문 하나밖에 없으면 리턴 키워드도 생략할 수 있음

예제
{: .label .label-purple .mt-2}
```java
public class FunctionalInterfaceMain {
public static void main(String[] args) {
	
	MyFuncInter fi;
	
	fi = (x , y) -> {
		int result = x + y;
		return result; // 리턴값 반환
	};
	
	int result = fi.method(10, 20);
	System.out.println(result);
	System.out.println(fi.method(10, 20));
	
	fi = (x,y) -> { return x+y;	};	
	System.out.println(fi.method(10, 200));
	
	//실행문이 리턴문 하나밖에 없으면 리턴 키워드도 생략할 수 있음
	fi = (x,y) -> x/y; 
	System.out.println(fi.method(10, 3));

	fi = (x,y) -> divide(10, 5);
	System.out.println(fi);
	
}

private static int divide(int x, int y) {
	return x/y;
}

}

@FunctionalInterface
interface MyFuncInter {
	int method (int x, int y);
}
```

### Target Funtion 

&#9656; 람다식형태는 매개변수를 가진 코드블럭이기 때문에 자바의 메서드를 선언하는 것처럼 보여지지만 자바에서는 메서드를 단독으로 선언할 수 없고 항상 클래스의 멤버로 선언하기 때문에 람다식은 **단순히 메서드를 선선하는게 아니라 객체를 생성하는 것**

&#9656; 람다식은 인터페이스 변수에 대입됨 즉, "인터페이스의 익명구현객체를 생성"

&#9656; 인터페이스는 직접 객체화 할 수 없기 때문에 구현 클래스가 필요한데 람다식은 클래스 선언 없이 익명구현객체를 직접 생성하고 객체화 함

**람다식은 대입될 인터페이스의 종류에 따라 달라지기 때문에 람다식이 대입될 인터페이스를 람다식의 타겟타입(Target Type)이라고 함**

### Functional Interface

**함수적 인터페이스, @FunctionalInterface**

&#9656; 모든 인터페이스를 람다식의 타겟타입으로 사용할 수는 없음

&#9656; 람다식이 하나의 메서드를 정의하기 때문에 두 개 이상의 추상메서드가 선언된 인터페이스는 람다식을 이용할 수 없음

&#9656; 하나의 추상메서드가 선언된 인터페이스만이 람다식의 타겟타입이 될 수 있는데 이러한 인터페이스를 함수적 인터페이스라고 함

&#9656; 함수적 인터페이스를 작성할 때 2개 이상의 추상메서드가 선언되지 않도록 컴파일러가 확인할 수 있도록 인터페이스 선언시에 @FunctionalInterface 애너테이션을 선언

### Class Member with Local Variables

람다식의 실행블럭에는 클래스 멤버 (필드, 메서드) 및 로컬 변수를 사용할 수 있음

&#9656; 클래스 멤버는 제약없이 사용할 수 있지만 로컬변수는 제약이 있음

&#9656; 클래스 멤버를 사용할 때 this 키워드를 사용할 때는 일반적으로 익명객체 내부에서 this는 익명객체를 참조하지만 람다식에서 this는 내부적으로 생성되는 익명객체가 아니라 람다식을 실행한 객체를 의미

UsingThis
{: .label .label-purple .mt-2}
```java
public class UsingThis {

	public int outterField = 10;
	
    //내부클래스의 가상메소드를 람다식으로 선언
	public class Inner {
		int innerField = 20;
		
		void method() {			
			MyFuncInter fi;
			fi = () -> { 
				System.out.println("outterField = " + outterField); //10
				System.out.println("outterField = " + UsingThis.this.outterField); //10
				System.out.println("innerField = " + innerField); //20
				System.out.println("innerField = " + this.innerField); //20
			};
			fi.method();
		}
	}

}

@FunctionalInterface
interface MyFuncInter {
	void method();
}
```

UsingThisMain : 실행부
{: .label .label-purple .mt-2}
```java
public class UsingThisMain {
public static void main(String[] args) {
	
    //객체 생성 후 
	UsingThis usingThis = new UsingThis();
    //그 객체의 내부 클래스 객체를 만든 후
	UsingThis.Inner inner = usingThis.new Inner();
	//내부클래스 객체의 함수실행
    inner.method();
}
}
```