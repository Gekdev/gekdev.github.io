---
layout: default
title: Optional Class
parent: Stream
grand_parent: Java
nav_order: 3
---

# Stream Optional Class
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## java.util.Optional&#60;T&#62; Class

### java.util.Optional&#60;T&#62; Class Basic

**Optional&#60;T&#62;  클래스 : Integer나 Double 클래스처럼 'T'타입의 객체를 포장해 주는 래퍼 클래스(Wrapper class)**

&#8594; **따라서 Optional 인스턴스는 모든 타입의 참조 변수를 저장할 수 있음**

### Why Use Optional class?

Optional 객체를 사용하면 예상치 못한 NullPointerException 예외를 제공되는 메소드로 간단히 회피할 수 있음

즉, 복잡한 조건문 없이도 널(null) 값으로 인해 발생하는 예외를 처리할 수 있게 됨

### Create Optional Object

* of() : null이 아닌 명시된 값을 가지는 Optional 객체를 반환

    &#8594; null이 저장되면 NullPointerException 예외가 발생

* ofNullable() : 명시된 값이 null이 아니면 명시된 값을 가지는 Optional 객체를 반환하며, 명시된 값이 null이면 비어있는 Optional 객체를 반환

    &#8594; 참조 변수의 값이 만에 하나 null이 될 가능성이 있다면 이 메소드를 사용하여 Optional 객체를 생성
    
예제
{: .label .label-purple .mt-2}
```java
Optional<String> opt = Optional.ofNullable("자바 Optional 객체");
System.out.println(opt.get());

//실행 결과
//자바 Optional 객체
```

### Access to Optional Object

* get() : Optional 객체에 저장된 값에 접근

    &#8594; 저장된 값이 null이면, NoSuchElementException 예외가 발생

* isPresent() : get() 메소드를 호출하기 전에 사용하여 Optional 객체에 저장된 값이 null인지 아닌지를 먼저 확인

 
예제
{: .label .label-purple .mt-2}
```java
//isPresent() 메소드를 이용하여 좀 더 안전하게 Optional 객체에 저장된 값에 접근하는 예제
Optional<String> opt = Optional.ofNullable("자바 Optional 객체");

if(opt.isPresent()) {
    System.out.println(opt.get());
}

//실행 결과
//자바 Optional 객체
```

### null Substitution Methods

null 대체값 지정 메소드

1. orElse() : 저장된 값이 존재하면 그 값을 반환하고, 값이 존재하지 않으면 인수로 전달된 값을 반환

2. orElseGet() : 저장된 값이 존재하면 그 값을 반환하고, 값이 존재하지 않으면 인수로 전달된 람다 표현식의 결괏값을 반환

3. orElseThrow() : 저장된 값이 존재하면 그 값을 반환하고, 값이 존재하지 않으면 인수로 전달된 예외를 발생
</div>

예제
{: .label .label-purple .mt-2}
```java
Optional<String> opt = Optional.empty(); // Optional를 null로 초기화함. 

System.out.println(opt.orElse("빈 Optional 객체"));
System.out.println(opt.orElseGet(String::new));

//실행 결과
//빈 Optional 객체
```
 
&#9656; **empty() 메소드 : Optional 객체를 null로 초기화**

### 기본 타입의 Optional 클래스

자바에서는 IntStream 클래스와 같이 기본 타입 스트림을 위한 별도의 Optional 클래스를 제공

1. OptionalInt class

2. OptionalLong class

3. OptionalDouble class

반환 타입이 Optional&#60;T&#62;  타입이 아니라 해당 기본 타입이라는 사실만 제외하면 거의 모든 면에서 비슷함

Optional 객체에서 get() 메소드를 사용하여 저장된 값에 접근할 수 있는 것처럼 클래스별로 저장된 값에 접근할 수 있는 다음과 같은 메소드를 제공

저장된 값에 접근하는 메소드
{: .label .label-purple .mt-2}

| 클래스 | 메소드 |
|:------|:------|
| Optional&#60;T&#62;  |	T get() |
| OptionalInt	| int getAsInt()|
| OptionalLong	| long getAsLong()|
| OptionalDouble	| double getAsDouble()|

예제
{: .label .label-purple .mt-2}
```java
IntStream stream = IntStream.of(4, 2, 1, 3);
OptionalInt result = stream.findFirst();

System.out.println(result.getAsInt());

//실행 결과
//4
```

###  Optional Method Table

Optional 클래스의 메소드

| 메소드 | 설명 |
|:------|:------|
|static &#60;T&#62;  Optional&#60;T&#62;  empty()	|아무런 값도 가지지 않는 비어있는 Optional 객체를 반환|
|T get()	| Optional 객체에 저장된 값을 반환|
|boolean isPresent()	| 저장된 값이 존재하면 true를 반환하고, 값이 존재하지 않으면 false를 반환|
|static &#60;T&#62;  Optional&#60;T&#62;  of(T value)	| null이 아닌 명시된 값을 가지는 Optional 객체를 반환|
|static &#60;T&#62;  Optional&#60;T&#62;  ofNullable(T value)	| 명시된 값이 null이 아니면 명시된 값을 가지는 Optional 객체를 반환하며, 명시된 값이 null이면 비어있는 Optional 객체를 반환 |
| T orElse(T other)	| 저장된 값이 존재하면 그 값을 반환하고, 값이 존재하지 않으면 인수로 전달된 값을 반환|
| T orElseGet(Supplier<? extends T> other)	| 저장된 값이 존재하면 그 값을 반환하고, 값이 존재하지 않으면 인수로 전달된 람다 표현식의 결괏값을 반환|
| &#60;X extends Throwable> T orElseThrow(Supplier<? extends X>  exceptionSupplier)	| 저장된 값이 존재하면 그 값을 반환하고, 값이 존재하지 않으면 인수로 전달된 예외를 발생시킴 |
