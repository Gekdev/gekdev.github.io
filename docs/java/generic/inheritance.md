---
layout: default
title: Inheritance
parent: Generic
grand_parent: Java
nav_order: 4
---

# Generic Inheritance
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Inheritance

### Inheritance Basic

제네릭타입의 상속과 구현
	
제네릭타입도 다른 타입과 마찬가지로 부모클래스가 될 수 있음

부모클래스에서 상속받은 자식클래스는 부모클래스에 정의된 타입을 정의해야 함

또한, 자식클래스는 타입변수를 추가할 수 있드며 제네릭 인터페이스를 구현한 클래스에서도 제네릭타입으로 정의되어야 함 
	
Product
{: .label .label-purple .mt-2}
```java
public class Product<T, M> {

	private T kind;
	private M model;
	
	public T getKind() {
		return kind;
	}
	public void setKind(T kind) {
		this.kind = kind;
	}
	public M getModel() {
		return model;
	}
	public void setModel(M model) {
		this.model = model;
	}
	
}

class Car {}
class TV {}
```

ChildProduct
{: .label .label-purple .mt-2}
```java
// Generic C가 추가되었음
public class ChildProduct<T, M, C> extends Product<T, M>{

	private String company;

	public String getCompany() {
		return company;
	}

	public void setCompany(String company) {
		this.company = company;
	}
	
}
```

```java
public class ExtendsImplMain {

	public static void main(String[] args) {
		
		// 1. 클래스상속
		ChildProduct<TV, String, String> tv = new ChildProduct<TV, String, String>();
		tv.setKind(new TV());
		tv.setModel("스마트TV");
		tv.setCompany("LG전자");
		
		ChildProduct<Car, String, String> car = new ChildProduct<Car, String, String>();
		car.setKind(new Car());
		car.setModel("911카레라");
		car.setCompany("포르쉐");
		
		// 2. 인터페이스구현
		Storage<TV> storage = new StorageImpl(100);
		storage.add(new TV(), 0);
		TV tv1 = storage.get(0);
		System.out.println(tv1);
		System.out.println();
		
		Storage<Car> storage1 = new StorageImpl<>(100);
		storage1.add(new Car(), 0);
		Car car1 = storage1.get(0);
		System.out.println(car1);
	}

}

interface Storage<T> {
    
	void add(T item, int index);
	T get(int index);
                      
}

class StorageImpl<T> implements Storage<T> {

	private T[] array;
	
    //생성자
	public StorageImpl(int capacity) {
		this.array = (T[]) (new Object[capacity]);
	}
	
	@Override
	public void add(T item, int index) {
		array[index] = item;
	}

	@Override
	public T get(int index) {
		return array[index];
	}
	
}
```
