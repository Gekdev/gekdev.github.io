---
layout: default
title: Creating
parent: Stream
grand_parent: Java
nav_order: 1
---

# Stream Creating
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Stream Creating
{: .no_toc}

### How to Create Stream

다양한 데이터 소스에서 생성할 수 있음

1. 컬렉션

2. 배열

3. 가변 매개변수

4. 지정된 범위의 연속된 정수

5. 특정 타입의 난수들

6. 람다 표현식

7. 파일

8. 빈 스트림

### Collection

**자바에서 제공하는 모든 컬렉션의 최고 상위 조상인 Collection 인터페이스에는 stream() 메소드가 정의되어있음**

&#9656; Collection 인터페이스를 구현한 모든 List와 Set 컬렉션 클래스에서도 stream() 메소드로 스트림을 생성할 수 있음

&#9656; parallelStream() 메소드를 사용하면 병렬 처리가 가능한 스트림을 생성할 수 있음

예제
{: .label .label-purple .mt-2}
```java
ArrayList<Integer> list = new ArrayList<Integer>();

list.add(4);
list.add(2);
list.add(3);
list.add(1);

// 컬렉션에서 스트림 생성
Stream<Integer> stream = list.stream();
// forEach() 메소드를 이용한 스트림 요소의 순차 접근
stream.forEach(System.out::println);

//실행 결과
//4
//2
//3
//1
```

forEach() 메소드 : 해당 스트림의 요소를 하나씩 소모해가며 순차적으로 요소에 접근하는 메소드

같은 데이터에서 또 다른 스트림을 생성하여 forEach() 메소드를 호출하는 것은 가능

### Array

**Arrays 클래스에는 다양한 형태의 stream() 메소드가 클래스 메소드로 정의**

기본 타입인 int, long, double 형을 저장할 수 있는 배열에 관한 스트림이 별도로 정의 (IntStream, LongStream, DoubleStream 인터페이스)

Arrays 클래스의 stream() 메소드는 전체 배열뿐만 아니라 배열의 특정 부분만을 이용하여 스트림을 생성할수도 있음

예제
{: .label .label-purple .mt-2}
```java
String[] arr = new String[]{"넷", "둘", "셋", "하나"};

// 배열에서 스트림 생성
Stream<String> stream1 = Arrays.stream(arr);
stream1.forEach(e -> System.out.print(e + " "));
System.out.println();

// 배열의 특정 부분만을 이용한 스트림 생성
Stream<String> stream2 = Arrays.stream(arr, 1, 3);
stream2.forEach(e -> System.out.print(e + " "));

//실행 결과
//넷 둘 셋 하나
//둘 셋 
```

### Variable Parameters

**Stream 클래스의 of() 메소드를 사용하면 가변 매개변수(variable parameter)를 전달받아 스트림을 생성할 수 있음**

예제
{: .label .label-purple .mt-2}
```java
// 가변 매개변수에서 스트림 생성
Stream<Double> stream = Stream.of(4.2, 2.5, 3.1, 1.9);
stream.forEach(System.out::println);

//실행 결과
//4.2
//2.5
//3.1
//1.9
```

### Continuous Integers in the Specified Range

**지정된 범위의 연속된 정수를 스트림으로 생성하기 위해 IntStream나 LongStream 인터페이스에는 range()와 rangeClosed() 메소드가 정의되어 있음**

* range() 메소드 : 명시된 시작 정수를 포함하지만, 명시된 마지막 정수는 포함하지 않는 스트림을 생성

* rangeClosed() 메소드 : 명시된 시작 정수뿐만 아니라 명시된 마지막 정수까지도 포함하는 스트림을 생성

예제
{: .label .label-purple .mt-2}
```java
// 지정된 범위의 연속된 정수에서 스트림 생성
IntStream stream1 = IntStream.range(1, 4);
stream1.forEach(e -> System.out.print(e + " "));
System.out.println();

IntStream stream2 = IntStream.rangeClosed(1, 4);
stream2.forEach(e -> System.out.print(e + " "));

//실행 결과
//1 2 3 
//1 2 3 4 
```

### Certain types of Random Numbers

**특정 타입의 난수로 이루어진 스트림을 생성하기 위해 Random 클래스에는 ints(), longs(), doubles()와 같은 메소드가 정의**

매개변수로 스트림의 크기를 long 타입으로 전달받을 수 있음

매개변수를 전달받지 않으면 크기가 정해지지 않은 무한 스트림(infinite stream)을 반환

이때에는 limit() 메소드를 사용하여 따로 스트림의 크기를 제한해야함

예제
{: .label .label-purple .mt-2}
```java
// 특정 타입의 난수로 이루어진 스트림 생성
IntStream stream = new Random().ints(4);
stream.forEach(System.out::println);

//실행결과
//1072176871
//-649065206
//133298431
//-616174137
```

### Lambda Expression

**람다 표현식을 매개변수로 전달받아 해당 람다 표현식에 의해 반환되는 값을 요소로 하는 무한 스트림을 생성하기 위해 Stream 클래스에는 iterate()와 generate() 메소드가 정의**

* iterate() 메소드 : 시드(seed)로 명시된 값을 람다 표현식에 사용하여 반환된 값을 다시 시드로 사용하는 방식으로 무한 스트림을 생성

* generate() 메소드 : 매개변수가 없는 람다 표현식을 사용하여 반환된 값으로 무한 스트림을 생성

예제
{: .label .label-purple .mt-2}
```java
//iterator() 메소드 사용
IntStream stream = Stream.iterate(2, n -> n + 2); // 2, 4, 6, 8, 10, ...
```

### Files

**파일의 한 행(line)을 요소로 하는 스트림을 생성하기 위해 java.nio.file.Files 클래스에는 lines() 메소드가 정의**

java.io.BufferedReader 클래스의 lines() 메소드를 사용하면 파일뿐만 아니라 다른 입력으로부터도 데이터를 행(line) 단위로 읽어 올 수 있음

예제
{: .label .label-purple .mt-2}
```java
String<String> stream = Files.lines(Path path);
```

### Empty Stream

**아무 요소도 가지지 않는 빈 스트림은 Stream 클래스의 empty() 메소드를 사용하여 생성**

예제
{: .label .label-purple .mt-2}
```java
// 빈 스트림 생성
Stream<Object> stream = Stream.empty();
System.out.println(stream.count()); // 스트림의 요소의 총 개수를 출력함.

//실행결과
//0
```






















