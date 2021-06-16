---
layout: default
title: Stream
parent: Java
nav_order: 19
has_children: true
---

# Java Stream
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Stream API
{: .no_toc}

입력과 출력의 스트림과는 전혀 다른 개념

Java SE 8부터 추가됨

### Why Use Stream API?

자바에서는 많은 양의 데이터를 저장하기 위해서 배열이나 컬렉션을 사용하고 이렇게 저장된 데이터에 접근하기 위해서는 반복문이나 반복자(iterator)를 사용하여 매번 새로운 코드를 작성

하지만 이렇게 작성된 코드는 길이가 너무 길고 가독성도 떨어지며, 코드의 재사용이 거의 불가능 즉, 데이터베이스의 쿼리와 같이 정형화된 처리 패턴을 가지지 못했기에 데이터마다 다른 방법으로 접근해야만 했음

이러한 문제점을 극복하기 위해서 Java SE 8부터 스트림(stream) API를 도입함

**스트림 API는 데이터를 추상화하여 다루므로, 다양한 방식으로 저장된 데이터를 읽고 쓰기 위한 공통된 방법을 제공해서 이걸 이용하면 배열이나 컬렉션뿐만 아니라 파일에 저장된 데이터도 모두 같은 방법으로 다룰 수 있게 됨**

### Features of Stream API

1. 외부 반복을 통해 작업하는 컬렉션과는 달리 내부 반복(internal iteration)을 통해 작업을 수행

2. 재사용이 가능한 컬렉션과는 달리 단 한 번만 사용 가능

3. 원본 데이터를 변경하지 않음

4. 연산은 필터-맵(filter-map) 기반의 API를 사용하여 지연(lazy) 연산을 통해 성능을 최적화

5. parallelStream() 메소드를 통한 손쉬운 병렬 처리를 지원

### Behavioral flow of Stream API

스트림 API는 다음과 같이 세 가지 단계에 걸쳐서 동작

1. 스트림의 생성

2. 스트림의 중개 연산 (스트림의 변환)

3. 스트림의 최종 연산 (스트림의 사용)

![](img_java_stream_operation_principle.png)

















