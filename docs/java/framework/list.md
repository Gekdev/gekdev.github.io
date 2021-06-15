---
layout: default
title: List
parent: Framework
grand_parent: Java
nav_order: 1
---

# Collection Framework List
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Collection List Interface

### List Interface Features

List 인터페이스를 구현한 모든 List 컬렉션 클래스는 다음과 같은 특징을 가짐

1. 객체를 일렬로 늘어 놓은 구조

2. 객체를 인덱스로 관리하기 때문에 객체를 저장하면 자동으로 인덱스가 부여됨

3. 이 인덱스로 객체를 검색, 삭제할 수 있는 기능을 제공

4. 동일한 객체를 중복저장 할 수 있는데 이 경우 동일한 번지가 참조됨

5. null도 저장이 가능한데 이 경우에는 해당 인덱스는 객체를 참조하지 않음

구현클래스 : ArrayList&#60;E&#62;, Vector&#60;E&#62;, LinkedList&#60;E&#62;, Stack&#60;E&#62;이 있음

### List Interface Methods

**List 인터페이스에서 제공하는 주요 메소드**

List 인터페이스는 Collection 인터페이스를 상속받아서 Collection 인터페이스에서 정의 한 메소드들을 모두 사용할 수 있음

| 기능      | 메소드                           | 설명                                      |
|:----------|:--------------------------------|:------------------------------------------|
| 객체 추가  | boolean add(E e)                | 주어진 객체를 맨 끝에 추가 (선택적 기능)     | 
|           | void add(int index, E element)  | 주어진 인덱스에 객체를 추가 (선택적 기능)    |
|           | E set(int index, E e)           | 주어진 인덱스에 저장된 객체를 전달받은 객체로 바꿈 (선택적 기능) |
| 객체 검색  | boolean contains(Object o)      | 주어진 객체를 포함하고 있는지를 확인         |
|           | boolean equals(Object o)        | 기존 객체와 전달받은 개체가 같은지 확인      |
|           | E get(int index)                | 주어진 인덱스에 저장된 객체를 리턴           |
|           | boolean isEmpty()               | 컬렉션이 비어 있는지 조사                   |
|           | int size()                      | 저장되어 있는 전체 객체수를 리턴            |
| 객체 삭제  | void clear()                    | 저장된 모든 객체를 삭제                    |
|           | boolean remove(Object o)        | 주어진 객체를 삭제 (선택적 기능)            |
|           | boolean remove(int index)       | 주어진 인덱스에 저장된 객체를 삭제           |

---

## ArrayList&#60;E&#62; Class

### ArrayList&#60;E&#62; Class Basic

**내부 배열에 객체를 저장해서 인덱스로 관리**

* 저장용량(capacity)

    객체의 크기를 지정하지 않고 생성하면 기본으로 10개의 크기를 갖음

    초기용량 : 10 (따로 지정 가능)

    객체의 크기를 지정할 경우에는 `ArrayList<>(20)` 형태로 지정

* 객체 추가, 제거

    바로 뒤 인덱스부터 마지막 인덱스까지 모두 앞으로 당겨지거나 미뤄짐

    저장용량을 초과한 객체들이 들어오면 자동으로 늘어남, 고정도 가능함

Difference between Array & ListArray<E>
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
**일반 배열과의 차이점**

일반 배열과 ArrayList는 인덱스로 객체를 관리한다는 점에서는 유사하지만 큰 차이점이 있음

일반 배열은 생성시에 크기가 고정되고 사용중에는 크기를 변경할 수 없지만, ArrayList는 저장용량을 초과할 경우 객체가 추가되면 자동으로 저장용량이 증가됨
</div>

### ArrayList Declaration

**ArrayList 배열 선언방법**

```java
List<객체> list = new ArrayList();
List<객체> list = new ArrayList<>();
List<객체> list = new ArrayList<객체>();
```

### Speed of ArrayList

ArrayList는 기본적으로 배열을 이용하고 검색할 때 속도가 빠름

객체를 추가, 제거 하게되면 새로운 배열을 생성하고 기존의 요소들을 옮겨야 하는 복잡한 과정을 자동으로 함

하지만 기본적으로 요소의 추가 및 삭제 작업에 걸리는 시간이 매우 길어서 배열의 값이 수시로 변경된다면 사용 지양해야함

ArrayList vs LinkedList 성능 비교
{: .label .mt-2}
```java
List<String> arrlist = new ArrayList();
List<String> lnklist = new LinkedList();

long start;
long finish;

// 1. ArrayList
start = System.nanoTime();
for(int i=0 ; i < 100000 ; i++) {
    arrlist.add(0, String.valueOf(i));
}
finish = System.nanoTime();
System.out.println("ArrayList 소요시간 = " + (finish - start) + "ns" ); //ArrayList 소요시간 = 766779500ns

// 2. Linkedlist
start = System.nanoTime();
for(int i=0 ; i < 100000 ; i++) {
    lnklist.add(0, String.valueOf(i));
}
finish = System.nanoTime();
System.out.println("Linkedlist 소요시간 = " + (finish - start) + "ns" ); //Linkedlist 소요시간 = 7088900ns
```

### How to get ArrayList Elements

1. for문을 이용한 출력

    ```java
    for(int i = 0; i<arr.size(); i++)

    System.out.println(arr.get(i));
    ```

2. 향상된 for문(enhanced for)을 이용한 출력(for each)

    ```java
    for(int num : arr)

    System.out.println(num);
    ```

3. Iterator&#60;E&#62; iterator() 메소드를 이용한 출력

    **해당 리스트의 반복자(iterator)를 반환**

    ```java
    Iterator<Integer> iter = arr.iterator();
    while(iter.hasNext())
    System.out.println(iter.next());
    ```

### ArrayList&#60;E&#62; Example

List 인터페이스에서 제공하는 주요 메소드를 사용해서 배열 조작하기

```java
public class ArrayListMain {
public static void main(String[] args) {
	
	List xxx = new ArrayList();
	xxx.add("문자열");
	xxx.add(new Apple());
	xxx.add(new Car());
	xxx.add(new Hammer());
	xxx.add(10);
	
	String l0 = (String) xxx.get(0);
	Apple l1 = (Apple) xxx.get(1);
	// Car l2 = (Apple) xxx.get(1); error 
	
	//기본 배열의 크기는 10;
	List<String> list = new ArrayList();
	// List<String> list = new ArrayList<>();
	// List<String> list = new ArrayList<String>();
	
	// 1-1. 추가 - add()
	// list.add(new Apple());
	list.add("Java");
	list.add("JSP");
	list.add("Python");
	list.add("R");
	list.add("C#");
	System.out.println("리스트의 크기 = " + list.size()); //리스트의 크기 = 5
	
	// 1-2. 삽입 - add(index, 값)
	list.add(3, "Spring");
	System.out.println("삽입된 값 = " + list.get(3)); //삽입된 값 = Spring
	//List[0] "Java" List[1] "JSP" List[2] "Python" List[3] "Spring" List[4] "R" List[5] "C#" 
	for(int i = 0; i < list.size() ;i++) {
		System.out.print("List[" + i + "] \"" + list.get(i) + "\" ");
	}
	System.out.println();
	System.out.println("리스트의 크기 = " + list.size()); //리스트의 크기 =6
	
	// 2. 읽기 - get()
	System.out.println(list.get(0));	//Java
	System.out.println(list.get(1));	//JSP
	
	// 3. 삭제 - remove()
	list.remove(3);
	//List[0] "Java" List[1] "JSP" List[2] "Python" List[3] "R" List[4] "C#" 
	for(int i = 0; i < list.size() ;i++) {
		System.out.print("List[" + i + "] \"" + list.get(i) + "\" ");
	}
	System.out.println();
	
	//List[0] "Java" List[1] "JSP" List[2] "R" List[3] "C#" 
	list.remove(2);
	for(int i=0;i<list.size();i++) {
		System.out.print("List[" + i + "] \"" + list.get(i) + "\" ");
	}
	System.out.println();
	
	// 4. 전체삭제 - clear()
	list.clear();
	System.out.println("리스트의 크기 =" + list.size());
	
}
}


class Apple{}
class Car{}
class Hammer{}
```

---

## LinkedList&#60;E&#62; Class

## LinkedList&#60;E&#62; Class Basic

**내부적으로 연결 리스트(linked list)를 이용하여 요소를 저장**

&#9656; 연결 리스트는 저장된 요소가 비순차적으로 분포되며, 이러한 요소들 사이를 링크(link)로 연결하여 구성

* 단일 연결 리스트(singly linked list) : 다음 요소를 가리키는 참조만을 가지는 연결 리스트

    요소의 저장과 삭제 작업이 다음 요소를 가리키는 참조만 변경하면 되므로, 아주 빠르게 처리

    하지만 단일 연결 리스트는 현재 요소에서 이전 요소로 접근하기가 매우 어려움

    ![](img_java_singly_linked_list.png)

* 이중 연결 리스트(doubly linked list) : 다음과 이전 요소를 가리키는 참조를 가지는 연결 리스트

    LinkedList 클래스가 여기에 속함

    이전 요소를 가리키는 참조도 가지는 이중 연결 리스트(doubly linked list)가 좀 더 많이 사용
    
    ![](img_java_doubly_linked_list.png)

&#9656; ArrayList 클래스가 배열을 이용하여 요소를 저장함으로써 발생하는 단점을 극복하기 위해 고안

&#9656; List인터페이스의 구현객체이므로 ArrayList와 사용방법은 동일함

&#9656; 특정 인덱스의 객체를 제거하면 앞뒤 링크만 변경되고 나머지 링크는 변경되지 않음 (삽입할 경우에도 동일)

### Create LinkedList&#60;E&#62;

저장할 객체 타입을 타입변수<E>로 표기하고 기본생성자를 호출

처음 생성될 때에는 어떤 링크도 만들어지지 않아 내부는 비어있음

특정 인덱스에서 객체를 제거하거나 추가하게 되면 바로 앞뒤 링크만 변경

빈번한 객체 삭제와 삽입이 일어나는 곳에서는 ArrayList보다 성능이 좋지만 검색만 자주 할 경우에는 ArrayList가 성능이 좋음

---

## Vector&#60;E&#62; Class

## Vector&#60;E&#62; Class Basic 

ArrayList 클래스와 같은 동작을 수행하는 클래스

* 스레드 동기화 

    ArrayList와 다른점, Vector는 동기화(Synchronized) 메서드로 구성되어 있기 때문에 멀티 쓰레드가 동시에 이 메서드를 실행할 수 없고 하나의 쓰레드가 실행을 완료해야 다른 쓰레드를 실행할 수 있음

    복수의 스레드가 동시에 vector에 접근해 객체를 추가, 삭제하더라도 스레드에 안전함

* Vector를 생성 : 저장할 객체타입을 타입변수로 표기하고 기본생성자를 호출하면 됨

&#9656; 현재에는 기존 코드와의 호환성을 위해서만 남아있으므로, Vector 클래스보다는 ArrayList 클래스를 사용함

예제
{: .label .label-purple .mt-2}
```java
import java.util.ArrayList;
import java.util.List;
import java.util.Vector;

public class VectorMain {
public static void main(String[] args) {
	
	List<Board> list = new ArrayList();
	List<Board> vector = new Vector();
	
	vector.add(new Board(1, "G7정상회의1", "123", "영국에서 G7정상회의 개최"));
	vector.add(new Board(2, "G7정상회의2", "123", "영국에서 G7정상회의 개최"));
	vector.add(new Board(3, "G7정상회의3", "123", "영국에서 G7정상회의 개최")); //삭제
	vector.add(new Board(4, "G7정상회의4", "123", "영국에서 G7정상회의 개최"));
	vector.add(new Board(5, "G7정상회의5", "123", "영국에서 G7정상회의 개최"));
	
	vector.remove(2); 
	for(int i=0 ; i<vector.size() ; i++) {
		Board board = vector.get((i));
		System.out.println(board.toString());
	}
}
}

class Board{
	int no;
	String title;
	String writer;
	String content;
	
	public Board(int no, String title, String writer, String content) {
		this.no = no;
		this.title = title;
		this.writer = writer;
		this.content = content;
	}

	@Override
	public String toString() {
		return "Board [no=" + no + ", title=" + title + ", writer=" + writer + ", content=" + content + "]";
	}
	
}
```



Object[] toArray()	
