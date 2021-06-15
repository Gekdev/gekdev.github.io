---
layout: default
title: Bounded
parent: Generic
grand_parent: Java
nav_order: 3
---

# Generic Bounded
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Bounded Type Parameter
{: .no_toc} 

### Bounded Basic 

**제한된 타입변수, extends 키워드를 사용하면 타입 변수에 특정 타입만을 사용하도록 제한**

클래스와 인터페이스를 동시에 상속받고 구현해야 한다면 엠퍼센트(&) 기호를 사용

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
<T extends 상위타입>
</div>
```java
//클래스 상속
public static <T extends Number>int compare(T t1, T t2)

//클래스와 인터페이스 동시에 상속
class AnimalList<T extends LandAnimal & WarmBlood> { ... }
```

### Why Use extends?

예를 들어 숫자를 연산하는 제네릭 메서드가 있다면 이 메서드는 매개값으로 숫자만 들어와야 함

즉, 매개값을 Number 또는 하위클래스타입(Byte, Integer, Long, Float, Double)등의 인스턴스(객체)만 가져와야 함

이게 제한된 타입파라미터(Bounded Type Parameter)가 필요한 이유

제한된 파라미터를 선언하려면 타입 파라미터 뒤에 extends키워드를 붙이고 상위타입을 명시하면 됨

인터페이스는 implements로 선언하지 않고 클래스와 동일하게 extends키워드를 사용

타입 파라미터에 지정되는 구체적인 타입은 상위타입이거나 상위타입의 하위 또는 구현 클래스만 가능

### Example

Util
{: .label .label-purple .mt-2}
```java
public class Util {

	public static <T extends Number>int compare(T t1, T t2) {
		double v1 = t1.doubleValue();
		double v2 = t2.doubleValue();
		return Double.compare(v1, v2); // -1,0,1
	}
	
}
```

BoundedMain
{: .label .label-purple .mt-2}
```java
public class BoundedMain {
public static void main(String[] args) {
	
	int result = Util.compare(1.0, 2.0);
	System.out.println(result); //-1
	
	result = Util.compare(1.0, 1); 
	System.out.println(result); //0
	
	result = Util.compare(3.0, 2);
	System.out.println(result); //1
	
	// Util.compare()메소드는 Number와 하위타입만 대입하도록 제한
	//result = Util.compare("a", 1); (X)
	
	// 10, 20은 int 타입이지만 Number의 하위타입이기 때문에 대입이 가능
	result = Util.compare(10, 20);
	
}
}
```
