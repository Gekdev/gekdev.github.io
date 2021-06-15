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

**컬렉션 프레임워크(Collection Framework) : java.util패키지에 컬렉션과 관련된 인터페이스와 클래스들을 포함시켜 놓은 것**

&#9656; 컬렉션 프레임워크는 몇가지 인터페이스를 통해서 다양한 컬렉션을 이용할 수 있도록 하고있음

&#8594; 주요 인터페이스로는 List, Set, Map이 있음

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
