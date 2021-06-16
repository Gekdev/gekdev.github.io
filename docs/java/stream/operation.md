---
layout: default
title: Operation
parent: Stream
grand_parent: Java
nav_order: 2
---

# Stream Operation
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Intermediate Operation

### Intermediate Operation Basic

**스트림의 중개 연산**

스트림 API에 의해 생성된 초기 스트림은 중개 연산을 통해 또 다른 스트림으로 변환됨

스트림을 전달받아 스트림을 반환하므로, 중개 연산은 연속으로 연결해서 사용할 수 있음

필터-맵(filter-map) 기반의 API를 사용함으로 지연(lazy) 연산을 통해 성능을 최적화할 수 있음

### Intermediate Operation Methods

스트림 API에서 사용할 수 있는 대표적인 중개 연산과 메소드

1. 스트림 필터링 : filter(), distinct()

2. 스트림 변환 : map(), flatMap()

3. 스트림 제한 : limit(), skip()

4. 스트림 정렬 : sorted()

5. 스트림 연산 결과 확인 : peek()

### filter() / distinct()

스트림 필터링 메소드

* **filter() : 해당 스트림에서 주어진 조건에 맞는 요소만으로 구성된 새로운 스트림을 반환**

* **distinct() : 해당 스트림에서 중복된 요소가 제거된 새로운 스트림을 반환**

    &#9656; 내부적으로 Object 클래스의 equals() 메소드를 사용하여 요소의 중복을 비교

예제
{: .label .label-purple .mt-2}
```java
IntStream stream1 = IntStream.of(7, 5, 5, 2, 1, 2, 3, 5, 4, 6);
IntStream stream2 = IntStream.of(7, 5, 5, 2, 1, 2, 3, 5, 4, 6);
 
// 스트림에서 중복된 요소를 제거함.
stream1.distinct().forEach(e -> System.out.print(e + " "));
System.out.println();

// 스트림에서 홀수만을 골라냄.
stream2.filter(n -> n % 2 != 0).forEach(e -> System.out.print(e + " "));

//실행 결과
//7 5 2 1 3 4 6 
//7 5 5 1 3 5 
```

### map() / flatMap()

스트림 변환

* **map() : 해당 스트림의 요소들을 주어진 함수에 인수로 전달하여, 그 반환값들로 이루어진 새로운 스트림을 반환**

* **flatMap() : 각 배열의 각 요소의 반환값을 하나로 합친 새로운 스트림을 얻음**

예제 : map
{: .label .label-purple .mt-2}
```java
Stream<String> stream = Stream.of("HTML", "CSS", "JAVA", "JAVASCRIPT");

stream.map(s -> s.length()).forEach(System.out::println);

//실행결과
//4
//3
//4
//10
```

예제 : flatMap
{: .label .label-purple .mt-2}
```java
String[] arr = {"I study hard", "You study JAVA"};
Stream<String> stream = Arrays.stream(arr);
stream.flatMap(s -> Stream.of(s.split(" +"))).forEach(System.out::println);

//실행결과
//I
//study
//hard
//You
//study
//JAVA
```

### limit() / skip()

스트림 제한

* **limit() : 해당 스트림의 첫 번째 요소부터 전달된 개수만큼의 요소만으로 이루어진 새로운 스트림을 반환**

* **skip() : 해당 스트림의 첫 번째 요소부터 전달된 개수만큼의 요소를 제외한 나머지 요소만으로 이루어진 새로운 스트림을 반환**

예제
{: .label .label-purple .mt-2}
```java
IntStream stream1 = IntStream.range(0, 10);
IntStream stream2 = IntStream.range(0, 10);
IntStream stream3 = IntStream.range(0, 10);

stream1.skip(4).forEach(n -> System.out.print(n + " "));
stream2.limit(5).forEach(n -> System.out.print(n + " "));
stream3.skip(3).limit(5).forEach(n -> System.out.print(n + " "));

//실행 결과
//4 5 6 7 8 9 
//0 1 2 3 4 
//3 4 5 6 7 
```

### sorted()

스트림 정렬

**sorted() 메소드 : 해당 스트림을 주어진 비교자(comparator)를 이용하여 정렬**

이때 비교자를 전달하지 않으면 기본적으로 사전 편찬 순(natural order)으로 정렬하게 됨

예제
{: .label .label-purple .mt-2}
```java
Stream<String> stream1 = Stream.of("JAVA", "HTML", "JAVASCRIPT", "CSS");
Stream<String> stream2 = Stream.of("JAVA", "HTML", "JAVASCRIPT", "CSS");

stream1.sorted().forEach(s -> System.out.print(s + " ")); 
stream2.sorted(Comparator.reverseOrder()).forEach(s -> System.out.print(s + " "));

//실행결과
//CSS HTML JAVA JAVASCRIPT 
//JAVASCRIPT JAVA HTML CSS 
```

### peek()

스트림 연산 결과 확인

**peek() 메소드 : 결과 스트림으로부터 요소를 소모하여 추가로 명시된 동작을 수행**

이 메소드는 원본 스트림에서 요소를 소모하지 않으므로, 주로 연산과 연산 사이에 결과를 확인하고 싶을 때 사용

&#8594; 개발자가 디버깅 용도로 많이 사용

예제
{: .label .label-purple .mt-2}
```java
IntStream stream = IntStream.of(7, 5, 5, 2, 1, 2, 3, 5, 4, 6);

stream.peek(s -> System.out.println("원본 스트림 : " + s))
    .skip(2)
    .peek(s -> System.out.println("skip(2) 실행 후 : " + s))
    
    .limit(5)
    .peek(s -> System.out.println("limit(5) 실행 후 : " + s))
    
    .sorted()
    .peek(s -> System.out.println("sorted() 실행 후 : " + s))
    
    .forEach(n -> System.out.println(n));
```

### Intermediate Operation Methods Table

**스트림 API에서 사용할 수 있는 대표적인 중개 연산을 위한 메소드**

| 메소드	 | 설명 |
|:---------|:----|
| Stream&#60;T&#62; filter(Predicate<? super T> predicate) | 해당 스트림에서 주어진 조건(predicate)에 맞는 요소만으로 구성된 새로운 스트림을 반환 |
| &#60;R&#62; Stream&#60;R&#62; map(Functoin<? super T, ? extends R> mapper) | 해당 스트림의 요소들을 주어진 함수에 인수로 전달하여, 그 반환값으로 이루어진 새로운 스트림을 반환 | 
| &#60;R&#62; Stream&#60;R&#62; flatMap(Functoin<? super T, ? extends Stream<? extends R>> mapper) | 해당 스트림의 요소가 배열일 경우, 배열의 각 요소를 주어진 함수에 인수로 전달하여, 그 반환값으로 이루어진 새로운 스트림을 반환 |
| Stream&#60;T&#62; distinct()	| 해당 스트림에서 중복된 요소가 제거된 새로운 스트림을 반환, 내부적으로 Object 클래스의 equals() 메소드를 사용|
|Stream&#60;T&#62; limit(long maxSize)	|해당 스트림에서 전달된 개수만큼의 요소만으로 이루어진 새로운 스트림을 반환|
|Stream&#60;T&#62; peek(Consumer<? super T> action)	| 결과 스트림으로부터 각 요소를 소모하여 추가로 명시된 동작(action)을 수행하여 새로운 스트림을 생성하여 반환|
|Stream&#60;T&#62; skip(long n)	| 해당 스트림의 첫 번째 요소부터 전달된 개수만큼의 요소를 제외한 나머지 요소만으로 이루어진 새로운 스트림을 반환|
|Stream&#60;T&#62; sorted() / Stream&#60;T&#62; sorted(Comparator<? super T> comparator) | 해당 스트림을 주어진 비교자(comparator)를 이용하여 정렬 / 비교자를 전달하지 않으면 영문사전 순(natural order)으로 정렬 |

---

## Terminal Operation

### Terminal Operation Basic

스트림 API에서 중개 연산을 통해 변환된 스트림은 마지막으로 최종 연산을 통해 각 요소를 소모하여 결과를 표시

즉, 지연(lazy)되었던 모든 중개 연산들이 최종 연산 시에 모두 수행되는 것

이렇게 최종 연산 시에 모든 요소를 소모한 해당 스트림은 더는 사용할 수 없게 됨

### Terminal Operation Methods

스트림 API에서 사용할 수 있는 대표적인 최종 연산과 그에 따른 메소드

1. 요소의 출력 : forEach()

2. 요소의 소모 : reduce()

3. 요소의 검색 : findFirst(), findAny()

4. 요소의 검사 : anyMatch(), allMatch(), noneMatch()

5. 요소의 통계 : count(), min(), max()

6. 요소의 연산 : sum(), average()

7. 요소의 수집 : collect()

### forEach()

요소의 출력

forEach() : 스트림의 각 요소를 소모하여 명시된 동작을 수행

반환 타입이 void이므로 보통 스트림의 모든 요소를 출력하는 용도로 많이 사용

예제
{: .label .label-purple .mt-2}
```java
Stream<String> stream = Stream.of("넷", "둘", "셋", "하나");
stream.forEach(System.out::println);

//실행결과
//넷
//둘
//셋
//하나
```

### reduce()

요소의 소모

스트림의 최종 연산은 모두 스트림의 각 요소를 소모하여 연산을 수행하지만 **reduce() : 첫 번째와 두 번째 요소를 가지고 연산을 수행한 뒤, 그 결과와 세 번째 요소를 가지고 또다시 연산을 수행**

&#8594; 이런 식으로 해당 스트림의 모든 요소를 소모하여 연산을 수행하고, 그 결과를 반환

인수로 초깃값을 전달하면 초깃값과 해당 스트림의 첫 번째 요소와 연산을 시작하며, 그 결과와 두 번째 요소를 가지고 계속해서 연산을 수행

예제
{: .label .label-purple .mt-2}
```java
Stream<String> stream1 = Stream.of("넷", "둘", "셋", "하나");
Stream<String> stream2 = Stream.of("넷", "둘", "셋", "하나");

Optional<String> result1 = stream1.reduce((s1, s2) -> s1 + "++" + s2);
result1.ifPresent(System.out::println);

String result2 = stream2.reduce("시작", (s1, s2) -> s1 + "++" + s2);
System.out.println(result2);

//실행 결과
//넷++둘++셋++하나
//시작++넷++둘++셋++하나
```

&#9656; 인수로 초깃값을 전달하는 reduce() 메소드의 반환 타입은 Optional&#60;T&#62;가 아닌 T 타입

&#8594; 그 이유는 비어 있는 스트림과 reduce 연산을 할 경우 전달받은 초깃값을 그대로 반환해야 하기 때문

### findFirst() / findAny()

요소의 검색

**findFirst()/ findAny() : 해당 스트림에서 첫 번째 요소를 참조하는 Optional 객체를 반환**

두 메소드 모두 비어 있는 스트림에서는 비어있는 Optional 객체를 반환

예제
{: .label .label-purple .mt-2}
```java
//스트림의 모든 요소를 정렬한 후, 첫 번째에 위치한 요소를 출력하는 예제
IntStream stream1 = IntStream.of(4, 2, 7, 3, 5, 1, 6);
IntStream stream2 = IntStream.of(4, 2, 7, 3, 5, 1, 6);

OptionalInt result1 = stream1.sorted().findFirst();
System.out.println(result1.getAsInt());

OptionalInt result2 = stream2.sorted().findAny();
System.out.println(result2.getAsInt());

//실행결과
//1
//1
```

병렬 스트림인 경우에는 findAny() 메소드를 사용해야만 정확한 연산 결과를 반환

### anyMatch() / allMatch() / noneMatch()

요소의 검사

해당 스트림의 요소 중에서 특정 조건을 만족하는 요소가 있는지, 아니면 모두 만족하거나 모두 만족하지 않는지 확인

* **anyMatch() : 해당 스트림의 일부 요소가 특정 조건을 만족할 경우에 true를 반환**

* **allMatch() : 해당 스트림의 모든 요소가 특정 조건을 만족할 경우에 true를 반환**

* **noneMatch() : 해당 스트림의 모든 요소가 특정 조건을 만족하지 않을 경우에 true를 반환**

세 메소드 모두 인수로 Predicate 객체를 전달받으며, 요소의 검사 결과는 boolean 값으로 반환

예제
{: .label .label-purple .mt-2}
```java
//스트림의 모든 요소를 검사하여 80보다 큰 값을 가지는 요소가 하나라도 존재하는지를 검사하는 예제
IntStream stream1 = IntStream.of(30, 90, 70, 10);
IntStream stream2 = IntStream.of(30, 90, 70, 10);

System.out.println(stream1.anyMatch(n -> n > 80));
System.out.println(stream2.allMatch(n -> n > 80));

//실행 결과
//true
//false
```

### count() / min() / max()

요소의 통계 

* **count() : 해당 스트림의 요소 갯수를 반환, 해당 스트림의 요소의 총 개수를 long 타입의 값으로 반환**

* **max() / min() : 해당 스트림의 요소 중에서 가장 큰 값과 가장 작은 값을 가지는 요소를 참조하는 Optional 객체를 얻을 수 있음**

예제
{: .label .label-purple .mt-2}
```java
IntStream stream1 = IntStream.of(30, 90, 70, 10);
IntStream stream2 = IntStream.of(30, 90, 70, 10);

System.out.println(stream1.count());
System.out.println(stream2.max().getAsInt());

//실행결과
//4
//90
```


### sum() / average()

요소의 연산

* **sum() : 해당 스트림의 모든 요소의 합**

* **average() : 해당 스트림의 모든 요소의 평균, 각 기본 타입으로 래핑 된 Optional 객체를 반환**

IntStream이나 DoubleStream과 같은 기본 타입 스트림에있음

예제
{: .label .label-purple .mt-2}
```java
IntStream stream1 = IntStream.of(30, 90, 70, 10);
DoubleStream stream2 = DoubleStream.of(30.3, 90.9, 70.7, 10.1);

System.out.println(stream1.sum());
System.out.println(stream2.average().getAsDouble());

//실행결과
//200
//50.5
```

### collect()

요소의 수집

**collect() : Collectors 객체에 구현된 방법대로 스트림의 요소를 수집**

&#9656; Collectors 클래스에는 미리 정의된 다양한 방법이 클래스 메소드로 정의

&#9656; 사용자가 직접 Collector 인터페이스를 구현하여 자신만의 수집 방법을 정의할수도 있음

스트림 요소의 수집 용도별 사용할 수 있는 Collectors 메소드
{: .label .label-red .mt-2}
<div class="code-example" markdown="1">
1. 스트림을 배열이나 컬렉션으로 변환 : toArray(), toCollection(), toList(), toSet(), toMap()

2. 요소의 통계와 연산 메소드와 같은 동작을 수행 : counting(), maxBy(), minBy(), summingInt(), averagingInt() 등

3. 요소의 소모와 같은 동작을 수행 : reducing(), joining()

4. 요소의 그룹화와 분할 : groupingBy(), partitioningBy()
</div>

예제
{: .label .label-purple .mt-2}
```java
Stream<String> stream = Stream.of("넷", "둘", "하나", "셋");

List<String> list = stream.collect(Collectors.toList());
Iterator<String> iter = list.iterator();
while(iter.hasNext()) {
    System.out.print(iter.next() + " ");
}

//실행결과
//넷 둘 하나 셋
```

예제
{: .label .label-purple .mt-2}
```java
//Collectors 클래스의 partitioningBy() 메소드를 이용하여 
//해당 스트림의 각 요소별 글자 수에 따라 홀수와 짝수로 나누어 저장하는 예제
Stream<String> stream = Stream.of("HTML", "CSS", "JAVA", "PHP");

Map<Boolean, List<String>> patition = stream.collect(Collectors.partitioningBy(s -> (s.length() % 2) == 0));

List<String> oddLengthList = patition.get(false);
System.out.println(oddLengthList);

List<String> evenLengthList = patition.get(true);
System.out.println(evenLengthList);

//실행 결과
//[CSS, PHP]
//[HTML, JAVA]
```


### Terminal Operation Methods Table

**스트림 API에서 사용할 수 있는 대표적인 최종 연산을 위한 메소드**

| 메소드	 | 설명 |
|:---------|:----|
| void forEach(Consumer<? super T> action)	| 스트림의 각 요소에 대해 해당 요소를 소모하여 명시된 동작을 수행|
| Optional&#60;T&#62; reduce(BinaryOperator&#60;T&#62; accumulator) / T reduce(T identity, BinaryOperator&#60;T&#62; accumulator) | 처음 두 요소를 가지고 연산을 수행한 뒤, 그 결과와 다음 요소를 가지고 또다시 연산을 수행함. 이런 식으로 해당 스트림의 모든 요소를 소모하여 연산을 수행하고, 그 결과를 반환 |
|Optional&#60;T&#62; findFirst() / Optional&#60;T&#62; findAny() | 해당 스트림에서 첫 번째 요소를 참조하는 Optional 객체를 반환 (findAny() 메소드는 병렬 스트림일 때 사용함)|
| boolean anyMatch(Predicate<? super T> predicate) |해당 스트림의 일부 요소가 특정 조건을 만족할 경우에 true를 반환 |
| boolean allMatch(Predicate<? super T> predicate)	| 해당 스트림의 모든 요소가 특정 조건을 만족할 경우에 true를 반환 |
| boolean noneMatch(Predicate<? super T> predicate)	| 해당 스트림의 모든 요소가 특정 조건을 만족하지 않을 경우에 true를 반환 |
| long count()	| 해당 스트림의 요소의 개수를 반환 |
| Optional&#60;T&#62; max(Comparator<? super T> comparator)	| 해당 스트림의 요소 중에서 가장 큰 값을 가지는 요소를 참조하는 Optional 객체를 반환 |
| Optional&#60;T&#62; min(Comparator<? super T> comparator)	|해당 스트림의 요소 중에서 가장 작은 값을 가지는 요소를 참조하는 Optional 객체를 반환 |
| T sum() | 해당 스트림의 모든 요소에 대해 합을 구하여 반환 |
| Optional&#60;T&#62; average()	|해당 스트림의 모든 요소에 대해 평균값을 구하여 반환|
| <R,A> R collect(Collector<? super T,A,R> collector) | 인수로 전달되는 Collectors 객체에 구현된 방법대로 스트림의 요소를 수집 |

