---
layout: default
title: Collection Framework
parent: Java
nav_order: 14
has_children : true
---

# Java Collection Framework
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Collection Framework Basic
{: .no_toc}

컬렉션 : 사전적 의미로 요소(객체)를 수집해 저장하는 것

### What is Collection Framework?

**java.util패키지에 데이터를 저장하는 자료 구조와 데이터를 처리하는 알고리즘을 구조화하여 클래스로 구현해 놓은 것**

&#9656; 몇가지 인터페이스를 통해서 다양한 컬렉션을 이용할 수 있도록 하고있음

&#8594; 주요 인터페이스로는 List, Set, Map이 있음

<span class="fs-2">
[자바 컬렉션 프레임워크의 주요 인터페이스에 대한 더 자세한 사항](https://docs.oracle.com/javase/8/docs/technotes/guides/collections/index.html){: .btn .btn-outline .mt-2}
</span>

### Why Use Collection Framework?

애플리케이션을 개발하다보면 다수의 객체를 저장해서 필요할 때마다 꺼내서 사용하는 경우가 많음

이러한 객체를 효율적으로 추가, 검색, 삭제할경우 가장 간단한 방법은 배열을 이용하는 것

기존 배열은 쉽게 생성하고 사용할 수 있지만, 저장객체의 크기가 배열 생성시에 결정(고정)되기 때문에 불특정 다수의 객체를 저장관리하기에는 문제가 있고, 객체를 삭제했을 때 해당 인덱스가 비게 되어 객체를 저장하려면 어디가 비어있는지 확인해야함

배열의 이러한 문제점을 해결하기 위해 **자료구조(Data Structure)를 바탕으로 객체들을 효율적으로 추가, 삭제, 검색할 수 있도록 하기 위해 사용함**

### CF Interface & Class

| 인터페이스 분류  | 소분류 | 특징                                      | 구현클래스                               |
|:----------------|:------|:------------------------------------------|:----------------------------------------|
| Collection      | List  | 순서를 유지하고 저장, 중복 저장가능          | Arraylist, Vector, LinkedList           |
|                 | Set   | 순서를 유지하지 않고 저장, 중복 저장 안됨    | HastSEt, TreeSet                        |
| Map             |       | 키와 값의 쌍으로 저장, 키는 중복 저장이 안됨 | HashMap, Hashtable, TreeMap, Properties |

&#9656; List와 Set은 객체를 추가, 삭제, 검색하는 방법에 공통점이 많아 Collection 인터페이스에 공통 메서드를 정의해두고 있음

![](cf_sort.png)

### Collection class

**컬렉션 클래스(collection class) : 컬렉션 프레임워크에 속하는 인터페이스를 구현한 클래스**

컬렉션 프레임워크의 모든 컬렉션 클래스는 List와 Set, Map 인터페이스 중 하나의 인터페이스를 구현

또한, 클래스 이름에도 구현한 인터페이스의 이름이 포함되므로 바로 구분할 수 있음

Vector나 Hashtable과 같은 컬렉션 클래스는 예전부터 사용해 왔으므로, 기존 코드와의 호환을 위해 아직도 남아 있지만 기존에 사용하던 컬렉션 클래스를 사용하는 것보다는 새로 추가된 ArrayList나 HashMap 클래스를 사용하는 것이 성능 면에서도 더 나은 결과를 얻을 수 있음

예제
{: .label .label-purple .mt-2}
```java
//ArrayList 클래스를 이용하여 리스트를 생성하고 조작하는 예제
import java.util.*;

public class Collection01 {
public static void main(String[] args) {
    // 리스트 생성
    ArrayList<String> arrList = new ArrayList<String>();
    // 리스트에 요소의 저장
    arrList.add("넷");
    arrList.add("둘");
    arrList.add("셋");
    arrList.add("하나");

    // 리스트 요소의 출력
    for(int i = 0; i < arrList.size(); i++) {
        System.out.println(arrList.get(i));
    }
}
}

//실행 결과
//넷
//둘
//셋
//하나
```

### Collection Interface

List와 Set 인터페이스의 많은 공통된 부분을 Collection 인터페이스에서 정의하고, 두 인터페이스는 그것을 상속받음

따라서 Collection 인터페이스는 컬렉션을 다루는데 가장 기본적인 동작들을 정의하고, 그것을 메소드로 제공

Collection 인터페이스 주요 메소드
{: .label .label-red .mt-2}

| 메소드   | 설명 |
|:--------|:----|
| boolean add(E e)	|해당 컬렉션(collection)에 전달된 요소를 추가 (선택적 기능)|
| void clear()	|해당 컬렉션의 모든 요소를 제거 (선택적 기능)|
| boolean contains(Object o)	|해당 컬렉션이 전달된 객체를 포함하고 있는지를 확인|
| boolean equals(Object o)	|해당 컬렉션과 전달된 객체가 같은지를 확인|
| boolean isEmpty()	|해당 컬렉션이 비어있는지를 확인|
| Iterator&#60;E&#62; iterator()	|해당 컬렉션의 반복자(iterator)를 반환|
| boolean remove(Object o)	|해당 컬렉션에서 전달된 객체를 제거 (선택적 기능)|
| int size()	|해당 컬렉션의 요소의 총 개수를 반환|
| Object[] toArray()	|해당 컬렉션의 모든 요소를 Object 타입의 배열로 반환|
