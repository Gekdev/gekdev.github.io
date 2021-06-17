---
layout: default
title: Basic API 
parent: Java
nav_order: 12
has_children: true
---

# Java Basic API
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Basic API - Object

### hashCode

**객체를 식별하는 하나의 정수값**

객체의 메모리번지를 이용해서 해시코드를 만들어 리턴하기 떄문에 객체마다 다른 값을 가지고 있음

논리적으로 동등비교시 Collection FrameWork에서 hashCode()를 재정의할 필요성이 있는 HashSet, HashMap, HashTable은 equals()로 비교

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
1. 메소드 호출

    객체.hashCode()

2. Override

    @Override

    public 데이터타입 hashCode() {

    return ... ;

    }
</div>
```java
class Key{
    public int number;
	
	Key(int number){
		this.number = number;
	}
	
	@Override
	public int hashCode() {
		return number;
	}
}

...
    
public class KeyMain {
public static void main(String[] args) {

    Key key0 = new Key(0);
    System.out.println(key0);
    System.out.println(key0.toString());
    System.out.println(key0.hashCode());
    System.out.println();

    //헥사코드
    Key key1 = new Key(15);
    System.out.println(key1.toString());
    System.out.println(key1.hashCode());
}}
```

![](hash.jpg)

### toString

**객체의 문자정보(객체를 문자열로 표현한 값)를 리턴**

Object.toString()메서드의 리턴값은 실제적으로는 별 사용가치가 없는 정보이기 때문에 하위 클래스에서는 toString()메서드를 재정의해서 간결하고 유익한 정보를 리턴하도록 함

ex1) 재정의된 java.util.Date.toString()메서드를 보면 현재의 시스템 날짜와 시간정보를 리턴하도록 재정의되어 있음

ex2) String클래스의 toString()메서드는 Object의 toString을 재정의해서 String에서 저장하고 있는 문자열을 리턴하도록 재정의 되어있음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
1. 메소드 호출

    객체.toString()

2. Override

    @Override

    public 데이터타입 toString() {

    return ... ;

    }

3. 리턴값

    클래스명@16진수해시코드

</div>
```java
public class SmartPhone {

	private String company;
	private String os;
	
	public SmartPhone(String company, String os) {
		this.company = company;
		this.os = os;
	}
	
	@Override
	public String toString() {
		return this.company + "-" + os;
	}
	
}

...
    
public class SmartPhoneMain {
public static void main(String[] args) {
	
	SmartPhone smartPhone = new SmartPhone("Apple", "iOS");
	System.out.println(smartPhone);
}
}
```

![](toString.jpg)

### clone

**원본객체의 필드값과 동일한 값을 가지는 새로운 객체를 생성하는것**

&#9656; 객체를 복제하는 이유는 원본객체를 안전하게 보호하기 위해 사용

&#9656; 신뢰하지 않는 영역으로 원본객체를 넘겨서 작업할 경우에 원본 객체의 데이터가 훼손될 수 있기 때문 

&#9656; 복제된 객체를 만들어서 신뢰하지 않는 영역으로 넘겨서 복제된 객체의 데이터가 변경되더라도 원본객체는 아무런 영향을 받지 않도록 해서 원본데이터를 안전하게 보호할 수 있게 됨

객체를 복제하는 방법: 얕은 복제와 깊은 복제

1. 얕은 복제(thin clone)

    **단순히 필드값을 복사해서 객체를 복제하는 것을 말함**

    syntax
    {: .label .mt-2}
    <div class="code-example" markdown="1">
    Object.clone()
    </div>
    

    원본객체와 동일한 필드값을 가지는 얕은 복제가 된 객체를 리턴함

    이 메서드는 객체를 복제하려면 원본객체는 반드시 java.lang.Cloneable 인터페이스를 구현하고 있어야 함

    클래스 설계자가 복제를 허용하지 않도록 한다면 Cloneable 인터페이스를 구현하지 않도록 하면됨

    * 기본값필드 : 값의 복제

    * 참조타입필드 : 얕은 복사가 되어 값이 복제되는게 아니라 참조하는 번지가 복제

        참조하는 번지만 복제가 되기 때문에 원본 객체 필드와 복제된 객체의 필드는 동일한 참조타입인 객체의 번지를 가지게 됨
	
    예제 : Member
    {: .label .label-purple .mt-2}
    ```java
    public class Member implements Cloneable{

        String id;
        String name;
        String password;
        int age;
        boolean adult;
        int[] scores = {90,88,96};

        public Member(String id, String name, String password, int age, boolean adult) {
            super();
            this.id = id;
            this.name = name;
            this.password = password;
            this.age = age;
            this.adult = adult;
        }

        public Member getMember() {
            Member cloned = null;

            try {
                cloned = (Member) super.clone();
            } catch (CloneNotSupportedException e) {
                // TODO Auto-generated catch block
                e.printStackTrace();
            }

            return cloned;
        }

    }
    ```
    
    예제 : MemberMain
    {: .label .label-purple .mt-2}
    ```java
    public class MemberMain {
    public static void main(String[] args) {

        Member 원본객체 = new Member("sohyang", "소향", "12345", 42, true);

        Member 복제객체 = 원본객체.getMember();

        //복제후에 복제된 객체의 암호를 변경
        System.out.println("변경전");
        System.out.println("원본 = " + 원본객체.password);
        System.out.println("복제 = " + 복제객체.password);
        복제객체.password = "abcdef";
        System.out.println("변경후");
        System.out.println("원본 = " + 원본객체.password);
        System.out.println("변경된 복제 = " + 복제객체.password);
        System.out.println();

        //4. 복제후에 복제된 객체의 참조타입(배열 scores)을 변경
        System.out.println("변경전");
        System.out.println("원본 = " + 원본객체.scores[0]);
        System.out.println("복제 = " + 복제객체.scores[0]);
        복제객체.scores[0] = 100;
        System.out.println("변경후");
        System.out.println("원본 = " + 원본객체.scores[0]);
        System.out.println("변경된 복제 = " + 복제객체.scores[0]);
    }}
    ```
    
    ![](clone.jpg)
    
2. 깊은 복제(deep clone)

    **참조하고 있는 참조타입의 객체필드도 복사하는 것**

    Object.clone()메서드를 재정의해서 참조객체를 복제하는 코드를 직접 작성해야 함


    예제 : Car
    {: .label .label-purple .mt-2}
    ```java
    public class Car {
        String model;
        public Car(String model) {
            this.model = model;
        }
    }
    ```

    예제 : Member
    {: .label .label-purple .mt-2}
    ```java
    import java.util.Arrays;

    public class Member implements Cloneable{

        String name;
        int age;
        int[] scores;
        Car car;

        public Member(String name, int age, int[] scores, Car car) {
            super();
            this.name = name;
            this.age = age;
            this.scores = scores;
            this.car = car;
        }

        public Member getMember() {
            Member cloned = null;
            try {
                cloned = (Member) clone();
            } catch (CloneNotSupportedException e) {
                e.printStackTrace();
            }
            return cloned;
        }

        @Override
        protected Object clone() throws CloneNotSupportedException {
            // 1. 얕은 복제
            Member cloned = (Member) super.clone();

            // 2. 깊은 복사
            cloned.scores = Arrays.copyOf(this.scores, this.scores.length);  //깊은 복사
            cloned.car = new Car(this.car.model); //객체를 새로 만들어서 복사

            // 3. 깊은 복제가 된
            return cloned;
        }
    }
    ```
    
    예제 : MemberMain
    {: .label .label-purple .mt-2}
    ```java
    public class MemberMain {
    public static void main(String[] args) {

        // 1. 원본객체생성
        Member 원본객체 = new Member("소향", 42, new int[]{10,20,30}, new Car("포르쉐"));

        // 2. 원본객체를 복제 후 참조타입의 값을 변경
        Member 복제객체 = 원본객체.getMember();

        // 3. 참조타입변수를 변경
        복제객체.scores[0] = 100;
        복제객체.car.model = "BMW";
        System.out.println("원본객체: " + 원본객체.scores[0]+ "," + 원본객체.car.model);
        System.out.println("복제객체: " + 복제객체.scores[0]+ "," + 복제객체.car.model);
        System.out.println();

        // 4. 객체들의 필드값을 출력
        System.out.println("[복제객체의 필드값]");
        System.out.println("이름 = " + 복제객체.name);
        System.out.println("나이 = " + 복제객체.age);
        System.out.print("점수 = {");
        for(int i=0; i<복제객체.scores.length;i++) {
            System.out.print(복제객체.scores[i]);
            System.out.print((i==복제객체.scores.length-1)? "": ", ");
        }
        System.out.println("}");
        System.out.println("차량모델 = " + 복제객체.car.model);

        System.out.println();

        System.out.println("[원본객체의 필드값]");
        System.out.println("이름 = " + 원본객체.name);
        System.out.println("나이 = " + 원본객체.age);
        System.out.print("점수 = {");
        for(int i=0; i<원본객체.scores.length;i++) {
            System.out.print(원본객체.scores[i]);
            System.out.print((i==원본객체.scores.length-1)? "": ", ");
        }
        System.out.println("}");
        System.out.println("차량모델 = " + 원본객체.car.model);

    }
    }
    ```
    
    ![](deepclone.jpg)

### finalize

**객체소멸자, 참조하지 않은 배열이나 객체를 GC(Garbage Collector)가 힙 영역에서 자동으로 소멸시킴**

&#9656; GC는 객체를 소멸하기 직전에 마지막으로 객체의 소멸자(finalize())를 실행시킴

&#9656; 소멸자는 object.finalize()메서드를 말하는데 기본적으로 실행할 내용이 없음 (실행문에 아무것도 없음)

&#9656; 객체가 소멸되기 전에 마지막으로 사용했던 자원(DB연결, 파일 등)을 닫고 싶거나 중요한 데이터를 저장하고 싶다면 object.finalize()를 재정의해서 사용해야 함

&#9656; 자바 9버전 이후로는 사용안함

&#9656; 원하는 시점에 특정한 행위를 하는게 아니라서 조심히 사용해야 함

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
System.gc()
</div>

예제 : Counter
{: .label .label-purple .mt-2}
```java
public class Counter {

	private int no;
	
	public Counter(int no) {
		this.no = no;
	}
	
	@Override
	protected void finalize() throws Throwable {
		System.out.println(this.no + "번 객체의 finalize()가 호출");
		
	}
	
}
```

예제 : FinalizeMain
{: .label .label-purple .mt-2}
```java
public class FinalizeMain {
public static void main(String[] args) {
	
	Counter counter = null;
	
	for(int i = 0 ; i < 50 ; i++) {
		counter = new Counter(i);
		counter = null; //객체를 더이상 참조하지 않음 즉, 쓰레기 객체생성
		System.gc(); //GC에게 쓰레기 객체를 Heap영역에서 제거 요청
	}
	
	
}
}
```

![](final.jpg)

위 이미지와같이 마음대로 실행됨 (매번 다른 결과)

---

## Object API

Object 클래스

**Object(java.lang)와 유사한 이름을 가진 java.util.Object 클래스**

객체의 비교, 해시코드 생성, 객체가 null인지 여부, 객체 문자열반환등의 기능을 수행하는 정적메서드로 구성된 Object의 유틸리티 클래스

### compare(T a, T b, Comparator&#60;T&#62; c)

**객체비교 메서드는 두 객체를 비교해서 int값을 리턴**

java.util.Comparator<T>는 제네릭 인터페이스 타입으로 두 객체를 비교하는 compare(T a, T b)메서드가 정의되어있음

예제
{: .label .label-purple .mt-2}
```java
public class CompareMain {

	static class Student{
		int sno;
		Student (int sno){ this.sno = sno; }
	}
	
	static class StudentComparator implements Comparator<Student>{

		@Override
		public int compare(Student a, Student b) {
			
			//비교를 하는 나의 코딩
			// if(a.sno < b.sno) { return -1; }
			// else if(a.sno == b.sno) { return 0; }
			// else { return 1; }
			
			return Integer.compare(a.sno, b.sno); // -1,0,1을 리턴		
		}
	}
	
public static void main(String[] args) {
	
	//Objects.compare(T a, T b, Comparator<T> c)
	Student s1 = new Student(1);
	Student s2 = new Student(1);
	Student s3 = new Student(3);

	int result = Objects.compare(s1, s2, new StudentComparator());
	System.out.println(result);
	
	result = Objects.compare(s1, s3, new StudentComparator());
	System.out.println(result);
	
	result = Objects.compare(s3, s1, new StudentComparator());
	System.out.println(result);

}
}
```

![](compare.jpg)

### equals() / deepEquals()

**동등비교, 두 객체가 같은 객체인지 여부를 비교**

1. 얕은비교 : Objects.equals(Object a,  Object b)

    **객체가 참조하고 있는 번지를 비교**

    1) a,b 모두 null일 경우 true를 리턴

    2) a,b모두 not null일 경우 a.equals(b)의 결과를 true/false로 리턴

2. 깊은 비교 : Objects.deepEquals(Object a, Object b) 

    **객체의 내부 값까지 비교**

    1) a, b가 서로 다른 배열일 경우 항목의 값까지 비교해서 모두 같을 경우 true아니면 false

    2) deepEquals()는 Arrays.deepEquals(Object[] a, Object[] b)와 동일한 기능을 함

예제 
{: .label .label-purple .mt-2}
```java
public class EqualsMain {
public static void main(String[] args) {
	
	// 1. 일반 객체일 경우
	Integer o1 = 100;
	Integer o2 = 100;
	
	System.out.println(Objects.equals(o1, o2));		// true
	System.out.println(Objects.equals(o1, null));	// false
	System.out.println(Objects.equals(null, o2));	// false
	System.out.println(Objects.equals(null, null));	// true
	System.out.println();
	
	// 2. 배열일 경우
	Integer[] a1 = {1,2}; // new Integer[] {1,2} 즉, 새로운 객체를 생성
	Integer[] a2 = {1,2};
	
	System.out.println(Objects.equals(a1, a2)); // false : 번지를 비교
	System.out.println(Objects.deepEquals(a1, a2)); // true : 값을 비교
	System.out.println(Arrays.deepEquals(a1, a2)); // true : 값을 비교
	
}
}
```

### hash() / hashCode()

**해시코드생성 메서드는 주어진 값들을 이용해서 해시코드를 생성하는 메소드**

주어진 매개 값들로 배열을 생성하고 Arrays.hashCode(Object[])를 호출해서 해시코드를 생성 후에 이 값을 리턴

이 메서드는 클래스가 hashCode()를 재정의 할 때 리터값을 생성하기 위해 사용하면 좋음

클래스가 여러가지 필드값을 가지고 있을 때 이 필드의 값으로 부터 해시코드를 생성하게 되면 동일한 필드값을 가지는 객체는 동일한 해시코드를 얻을 수 있음

예제 
{: .label .label-purple .mt-2}
```java
public class HashCodeMain {
public static void main(String[] args) {
	Student s1 = new Student(1, "소향");
	Student s2 = new Student(1, "소향");
	
	//override되어서 다르지만 똑같게 나옴
	System.out.println(s1.hashCode());
	System.out.println(s2.hashCode());
	System.out.println();
	
	System.out.println(Objects.hashCode(s1));
	System.out.println(Objects.hashCode(s2));
	System.out.println();
}
}

class Student {
	
	int sno;
	String name;
	
	public Student(int sno, String name) {
		super();
		this.sno = sno;
		this.name = name;
	}
	
	@Override
	public int hashCode() {
		return Objects.hash(sno, name);
	}
}
```

![](hashcode.jpg)