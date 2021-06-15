---
layout: default
title: Method
parent: Generic
grand_parent: Java
nav_order: 2
---

# Generic Method
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Generic Method
{: .no_toc}

### Generic Method Basic

제네릭 클래스를 메소드에서 이용

**제네릭 메소드란 메소드의 선언부에 타입 변수를 사용한 메소드를 의미**

이때 타입 변수의 선언은 메소드 선언부에서 반환 타입 바로 앞에 위치

Generic Class
{: .label .label-purple .mt-2}
```java
public class Box<T> {

	private T t;
	
	public T get() {
		return t;
	}
	
	public void set(T t) {
		this.t = t;
	}
	
}
```

Generic Method
{: .label .label-purple .mt-2}
```java
public class Util {

	//1. 일반메서드
	public static Box method(Box box) {
		Box box1 = new Box();
		box1.set("hammer");
		return box1;
	}
	
	//2. 제네릭메서드
    //Box<T>를 객체로 해서 제네릭으로 선언된 타입만 들어오게  메소드를 선언하고 있음
    //호출하면 안에서 데이터 타입에 맞는 box객체를 생성후 값을 지정한후 돌려줌
	public static <T> Box<T> boxing(T t) {
		Box<T> box = new Box();
		box.set(t);
		return box;
	}
	
}
```

실행부
{: .label .label-purple .mt-2}
```java
public class MethodMain {
public static void main(String[] args) {
	
	Box<Integer> boxA = Util.boxing(1000);
	Integer val1 = boxA.get();
	System.out.println(val1);
	
	Box<String> boxB = Util.boxing("망치");
	String val2 = boxB.get();
	System.out.println(val2);
	
	Box<Car> boxC = Util.boxing(new Car());
	Car car = boxC.get();
	System.out.println(car);
	
	Box<Apple> 사과상자 = Util.boxing(new Apple());
	Apple apple = 사과상자.get();
	System.out.println(apple);
}
}

class Car{
	@Override
	public String toString() {
		// TODO Auto-generated method stub
		return "포르쉐";
	}
}
```

### Method Compare

**메소드가 동일 객체인지 확인하는 방법**

1. Util 클래스에서 정적제네릭 메서드 compare()메서드를 정의하고
2. main()에서 compare() 메서드를 호출해서 
3. pair클래스에서는 제네릭 타입으로 Key, Value(K,Y)를 정의한 후에 동일객체 여부를 비교

Pair 
{: .label .label-purple .mt-2}
```java
public class Pair<K, V> {

	private K key;
	private V value;
	
	public Pair(K key, V value) {
		super();
		this.key = key;
		this.value = value;
	}

	public K getKey() {
		return key;
	}

	public void setKey(K key) {
		this.key = key;
	}

	public V getValue() {
		return value;
	}

	public void setValue(V value) {
		this.value = value;
	}
	
}
```

Util 
{: .label .label-purple .mt-2}
```java
public class Util {
	
	public static <K, Y> boolean compare(Pair<K, Y> p1, Pair<K, Y> p2){
		
		boolean keyCompare = p1.getKey().equals(p2.getKey());
		boolean valCompare = p1.getValue().equals(p2.getValue());
		return keyCompare && valCompare;
		
	}
	
}
```

CompareMain 
{: .label .label-purple .mt-2}
```java
public class CompareMain {
public static void main(String[] args) {
    
	Pair<Integer, String> p1 = new Pair<Integer, String>(1, "소향");
	Pair<Integer, String> p2 = new Pair<Integer, String>(1, "소향");
	Pair<String, String> p3 = new Pair<String, String>("홍길동", "소향동");
	Pair<String, String> p4 = new Pair<String, String>("홍길동", "소향");
                                        
	// 1. 제네릭 메서드를 명시적으로 호출
	Boolean result = Util.<Integer, String>compare(p1, p2);
	if(result) {
		System.out.println("논리적으로 동일 객체");
	}else {
		System.out.println("논리적으로 다른 객체");
	}
	
	// 2. 제네릭메서드를 묵시적으로 호출(추정)
	result = Util.compare(p3, p4);
	if(result) {
		System.out.println("논리적으로 동일 객체");
	}else {
		System.out.println("논리적으로 다른 객체");
	}
	
}
}
```