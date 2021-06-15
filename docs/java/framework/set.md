---
layout: default
title: Set
parent: Framework
grand_parent: Java
nav_order: 2
---

# Collection Framework Set
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Collection Set Interface

### Collection Set Features

Set 인터페이스를 구현한 모든 Set 컬렉션 클래스는 다음과 같은 특징을 가짐

1. 요소의 저장 순서를 유지하지 않음 즉, 순서가 없어서 인덱스로 객체를 검색할 수 없음

    대신 전체 객체를 한번씩 반복해서 가져오는 반복자(Iterator)를 제공함

2. 동일 객체 및 동등객체는 중복 저장하지 않음

    판단 과정

    1. hashCode() 리턴값 동일 여부 확인

    2. equals() 동일여부확인

    둘다 true라면 동일객체로 판단 후 저장하지 않음

3. null은 저장가능하지만 단 하나의 null값만 저장할 수 있음

구현클래스 : HashSet&#60;E&#62;, TreeSet&#60;E&#62;, LinkedSet&#60;E&#62;

### Iterator

**반복자는 Iterator 인터페이스를 구현한 객체**

&#8594; iterator()메서드를 호출하면 자료를 얻을 수 있음

메서드
{: .label .label-red .mt-2}
<div class="code-example" markdown="1">
1. hasNext() 

	**가져올 자료가 있을 경우 true, 없으면 false**
	
2. next() 

	**컬렉션에서 하나의 자료(객체)를 가져오는 메서드**

3. remove()

	**컬렉션에서 값을 제거하는 메서드**
</div>

### List Interface Methods

**Set 인터페이스에서 제공하는 주요 메소드**

Set 인터페이스는 Collection 인터페이스를 상속받으므로, Collection 인터페이스에서 정의한 메소드도 모두 사용할 수 있음

| 기능      | 메소드                           | 설명                                      |
|:----------|:--------------------------------|:------------------------------------------|
| 객체 추가  | boolean add(E e)                | 주어진 객체를 맨 끝에 추가 (선택적 기능)     | 
| 객체 검색  | boolean contains(Object o)      | 주어진 객체를 포함하고 있는지를 확인         |
|           | boolean equals(Object o)        | 기존 객체와 전달받은 개체가 같은지 확인      |
|           | boolean isEmpty()               | 컬렉션이 비어 있는지 조사                   |
|           | int size()                      | 저장되어 있는 전체 객체수를 리턴            |
| 객체 삭제  | void clear()                    | 저장된 모든 객체를 삭제                    |           
|           | boolean remove(Object o)        | 주어진 객체를 삭제 (선택적 기능)            |
| 객체 반환  | Object[] toArray()	           | 해당 리스트의 모든 요소를 Object 타입의 배열로 반환 |
| Iterator&#60;E&#62;|iterator()	                  | 해당 집합의 반복자(iterator)를 반환          |


---

## HashSet&#60;E&#62; Class

### HashSet&#60;E&#62; Class Basic

* 객체를 순서없이 저장

* 동일한 객체는 중복저장하지 않음 (동일 객체란 꼭 같은 인스턴스를 뜻하지는 않음)

    1. HashSet객체를 저장하기 전에 먼저 객체의 hashCode()메서드를 호출해서 해시코드를 가져오고 

    2. 이미 저장되어 잇는 객체들의 hashCode()와 비교

    3. 만약 동일한 hashCode가 있다면 다시 equals()메서드로 두 객체를 비교해서 true가 리턴되면 동일객체로 판단하고 중복저장하지 않음

* 해시 알고리즘(hash algorithm)을 사용하여 검색 속도가 매우 빠름

* HashSet 클래스는 내부적으로 HashMap 인스턴스를 이용하여 요소를 저장

예제
{: .label .label-purple .mt-2}
```java
HashSet<String> hs01 = new HashSet<String>();
HashSet<String> hs02 = new HashSet<String>();

// add() 메소드를 이용한 요소의 저장
hs01.add("홍길동");
hs01.add("이순신");
System.out.println(hs01.add("임꺽정")); // true
System.out.println(hs01.add("임꺽정")); // 중복된 요소의 저장이여서 false

// Enhanced for 문과 get() 메소드를 이용한 요소의 출력
for (String e : hs01) {
    System.out.print(e + " ");
} //홍길동 이순신 임꺽정

// add() 메소드를 이용한 요소의 저장
hs02.add("임꺽정");
hs02.add("홍길동");
hs02.add("이순신");

// iterator() 메소드를 이용한 요소의 출력

Iterator<String> iter02 = hs02.iterator();
while (iter02.hasNext()) {
    System.out.print(iter02.next() + " ");
} //홍길동 이순신 임꺽정

// size() 메소드를 이용한 요소의 총 개수
System.out.println("집합의 크기 : " + hs02.size()); //3
```

### HashSet&#60;E&#62; Example

```java
public class HashSetMain1 {
public static void main(String[] args) {
	
	Set<String> set = new HashSet<>();
	
	set.add("Java");
	set.add("Database");
	set.add("Pyshon");
	set.add("R");
	set.add("JDBC");
	set.add("Java"); // exception은 나지 않지만 저장되지 않음
	
	System.out.println("총 객체수 = " + set.size());   //5
	
	// while문을 이용해서 사용하는 방법
	Iterator<String> iterator = set.iterator();
	while(iterator.hasNext()) {
		String element = iterator.next();
		System.out.println(element);		//Java R Database JDBC Pyshon
	}
	// 다 꺼낸 후 다시 부르면 오류가 생김
	// String element = iterator.next();
	System.out.println();
	
	// for문을 이용해서 사용하는 방법
	set.remove("Database");
	System.out.println("총 객체수 = " + set.size());   //4
	for(String element : set) {
		System.out.println(element);          ////Java R JDBC Pyshon
	}
	System.out.println();

	set.clear();
	System.out.println("총 객체수 = " + set.size());   ///0
	
}
}
```
