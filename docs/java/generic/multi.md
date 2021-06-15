---
layout: default
title: Multi
parent: Generic
grand_parent: Java
nav_order: 1
---

# Generic Multi
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Multi Generic

**여러개의 타입변수를 사용할 때**

Gereric 예제
{: .label .label-purple .mt-2}
```java
public class Product<T, V>{
 
    //Field
	private T kind;
	private V model;
	
    //Setter Getter
	public T getKind() {
		return kind;
	}
	public void setKind(T kind) {
		this.kind = kind;
	}
	public V getModel() {
		return model;
	}
	public void setModel(V model) {
		this.model = model;
	}
	
}

class Car {}
class TV{}

```

```java
public class ProductMain {
public static void main(String[] args) {
	
    // 타입을 정하지 않고 사용할경우 아래와 같이 뭐든지 다 들어가버림
	Product product = new Product();
	product.setKind("문자열");
	product.setKind(1);
	product.setKind(1.0);
	product.setKind(new Car());
	product.setKind(new TV());
	product.setModel(new Car());
	product.setModel(new TV());

    // 마지막으로 정한값이 무엇인지에 따라 강제형변환을 해줘야함
	product.setKind(1);
	int xx = (int) product.getKind();
	product.setKind("문자열");
	String yy = (String) product.getKind();
	
    // TV객체와 문자열 객체로 선언한 tv
	Product<TV, String> tv = new Product<TV, String>();
	//tv.setKind("문자열");    kind에는 TV객체만 들어갈 수 있음
	//tv.setKind(1);
	//tv.setKind(new Car());
	tv.setKind(new TV());
	tv.setModel("스마트 티비");
	TV tv1 = tv.getKind();             // tv.getKind()에 TV객체가 들어가있는걸 확인
	String tvModel = tv.getModel();    // tv.getModel()에 String이 들어가있는걸 확인
	
    // Car객체와 문자열로 선언한 car
	Product<Car, String> car = new Product<>();
	car.setKind(new Car());
	car.setModel("포르쉐");
	Car car1 = car.getKind();
	String carModel = car.getModel();
	
    // 다양한 방법으로 객체를 생성할 수 있음
	Product<String, String> prod1 = new Product<>();
	Product<String, TV> prod2 = new Product<>();
	Product<String, Car> prod3 = new Product<>();
	Product<String, Integer> prod4 = new Product<>();
	
}
}
```
