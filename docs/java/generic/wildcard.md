---
layout: default
title: WildCard
parent: Generic
grand_parent: Java
nav_order: 4
---

# Generic WildCard
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## WildCard

## WildCard Basic

**제네릭 타입을 매개값이나 리턴타입으로 사용할 때 구체적인 타입대신 사용**

&#9656; 코드에서 ?를 일반적으로 와일드 카드라고 함

&#9656; 자바의 제네릭에서는 물음표(?) 기호를 사용하여 이러한 와일드카드를 사용할 수 있음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
<?>           // 타입 변수에 모든 타입을 사용

<? extends 상위타입> // 상위타입과 상위타입을 상속받는 자손 클래스 타입만을 사용 (상위타입제한)

<? super 하위타입>   // 하위타입과 하위타입이 상속받은 조상 클래스 타입만을 사용 (하위타입제한)
</div>

### Example

Person
{: .label .label-purple .mt-2}
```java
public class Person {

    // 이름 필드 설정
	private String name;
	
    // 생성자
	public Person(String name) {
		this.name = name;
	}

    // Getter Setter
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}

    // toString()
	@Override
	public String toString() {
		return name;
	}

}
```

Worker, Student, HighStudent extends Person
{: .label .label-purple .mt-2}
```java
//각각 객체를 생성하면 이름을 설정할 수 있게 함
public class Worker extends Person {

	public Worker(String name) {
		super(name);
	}
}

...
    
public class Student extends Person {

	public Student(String name) {
		super(name);
	}
}

...
    
public class HighStudent extends Student {

	public HighStudent(String name) {
		super(name);
	}
}
```

Course
{: .label .label-purple .mt-2}
```java
public class Course<T> {

    //강좌에는 이름과 수강인원가 배열로 들어가있어야함
	private String name;
	private T[] students;
	
	public String getName() {
		return name;
	}

	public T[] getStudents() {
		return students;
	}

    // 생성자
	public Course(String name, int capacity) {
		this.name = name;
		this.students = (T[]) new Object[capacity]; // 수강인원
	}
	
	public void add(T t) {
		for(int i=0;i<students.length;i++) {
			if(students[i] == null) {
				students[i] = t;
				break;
			}
		}
	}
}
```

WildCardMain : 실행부
{: .label .label-purple .mt-2}
```java
public class WildCardMain {

	// 수강생등록 메소드
	// 1. 모두 등록가능
	public static void registerCourse(Course<?> course) {
		System.out.println(course.getName() + " 수강생 : " + 
			Arrays.toString(course.getStudents())
		);
	}
	// 2. 학생만 등록가능
	public static void registerCourseStudent(Course<? extends Student> course)  {
		System.out.println(course.getName() + " 수강생 : " + 
			Arrays.toString(course.getStudents())
		);		
	}
	// 3. 직장인만 등록가능
	public static void regusterCourseWorker(Course<? super Worker> course) {
		System.out.println(course.getName() + " 수강생 : " + 
			Arrays.toString(course.getStudents())
		);		
		
	}
	
	public static void main(String[] args) {
		
		// 1. 모두 수강등록이 가능한 코스
        // 과정을 생성 후
		Course<Person> personCourse = new Course<>("일반인과정", 4);
		//하나하나 과정에 넣어줌
        personCourse.add(new Person("일반인"));
		personCourse.add(new Worker("직장인"));
		personCourse.add(new Student("학생"));
		personCourse.add(new HighStudent("고등학생"));
		
	    // 2. 학생만 수강등록이 가능한 코스
		Course<Student> studentCourse = new Course<>("학생과정", 4);
		studentCourse.add(new Student("학생"));
		studentCourse.add(new HighStudent("고등학생"));
	
		// 3. 고등학생만 수강등록이 가능한 코스
		Course<Student> highStudentCourse = new Course<>("고등학생과정", 4);
		highStudentCourse.add(new HighStudent("고등학생"));
		
		// 4. 직장인만 수강등록이 가능한 코스
		Course<Worker> workerCourse = new Course<>("직장인과정", 4);
		workerCourse.add(new Worker("직장인"));
		
		// a. 수강등록 :  registerCourse(Course<?> course)
        // 하나하나 넣은 과정의 수강생들을 출력
		registerCourse(personCourse);
		registerCourse(studentCourse);
		registerCourse(highStudentCourse);
		registerCourse(workerCourse);
		System.out.println();
		
		// b. 수강등록 :  registerCourseStudent(Course<? extends Student> course)
		// registerCourseStudent(personCourse); (X)
		// registerCourseStudent(workerCourse); (X)
		registerCourseStudent(studentCourse);
		registerCourseStudent(highStudentCourse);
		System.out.println();
		
		// c. 수강등록 :  regusterCourseWorker(Course<? super Worker> course)
		regusterCourseWorker(personCourse);
		regusterCourseWorker(workerCourse);
		// regusterCourseWorker(studentCourse); (x)
		// regusterCourseWorker(highStudentCourse); (x)
	}

}
```

![](https://gekdev.github.io/docs/java/generic/example/wildcard.jpg)