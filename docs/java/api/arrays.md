---
layout: default
title: Arrays 
parent: Basic API 
grand_parent: Java
nav_order: 7
---

# Basic API Arrays Class
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Arrays Class
{: .no_toc}

### java.util Package

java.util 패키지에는 프로그램을 개발하는 데 사용할 수 있는 유용한 유틸리티 클래스가 다수 포함되어 있음 (실제로 java.lang 패키지 다음으로 가장 많이 사용되는 패키지가 java.util 패키지)

java.util 패키지는 import 문으로 패키지를 불러오고 나서야 클래스 이름만으로 사용할 수 있음(java.lang 패키지와는 다름)

### java.util.Arrays Class

Arrays 클래스에는 배열을 다루기 위한 다양한 메소드가 포함되어 있음

Arrays 클래스의 모든 메소드는 클래스 메소드(static method)이므로, 객체를 생성하지 않고도 바로 사용할 수 있음

이 클래스는 java.util 패키지에 포함되므로, 반드시 import 문으로 java.util 패키지를 불러오고 나서 사용해야함

### binarySearch()

**전달받은 배열에서 특정 객체의 위치를 이진 검색 알고리즘을 사용하여 검색한 후, 해당 위치를 반환**

이 메소드는 이진 검색 알고리즘을 사용해서, 매개변수로 전달되는 배열이 sort() 메소드 등을 사용하여 미리 정렬되어 있어야만 제대로 동작

예제
{: .label .label-purple .mt-2}
```java
int[] arr = new int[1000];

for(int i = 0; i < arr.length; i++) {
    arr[i] = i;
}

System.out.println(Arrays.binarySearch(arr, 437));

//실행 결과
//437
```

### copyOf()

**전달받은 배열의 특정 길이만큼을 새로운 배열로 복사하여 반환**

&#9656; 첫 번째 매개변수로 원본 배열을 전달받고, 두 번째 매개변수로 원본 배열에서 새로운 배열로 복사할 요소의 개수를 전달받음

&#9656; 원본 배열과 같은 타입의 복사된 새로운 배열을 반환, 이때 새로운 배열의 길이가 원본 배열보다 길면, 나머지 요소는 배열 요소의 타입에 맞게 다음과 같은 기본값으로 채워짐

| 배열 요소의 타입	| 기본값    |
|:---------------|:---------|
| char	         | '\u0000' | 
| byte, short, int| 	0	| 
| long		    | 0L	    | 
| float	        | 0.0F	    | 
| double	    | 0.0 / 0.0D| 
| boolean	    | false	    | 
| 배열, 인스턴스 등| null	   | 
 

예제
{: .label .label-purple .mt-2}
```java
int[] arr1 = {1, 2, 3, 4, 5};

① int[] arr2 = Arrays.copyOf(arr1, 3);  //copyOf() 메소드를 사용하여 배열 arr1의 첫 번째 배열 요소부터 3개의 요소를 복사하여 배열 arr2에 대입

for (int i = 0; i < arr2.length; i++) {
    System.out.print(arr2[i] + " ");
}

② int[] arr3 = Arrays.copyOf(arr1, 10); //배열 arr1에서 10개의 배열 요소를 복사하여 배열 arr3에 대입

for (int i = 0; i < arr3.length; i++) {
    System.out.print(arr3[i] + " ");    //배열 arr1의 길이가 5밖에 안되므로, 배열 arr3의 나머지 배열 요소에는 int형의 기본값인 0
}

//실행 결과
//1 2 3 
//1 2 3 4 5 0 0 0 0 0 
```

### copyOfRange()

**전달받은 배열의 특정 범위에 해당하는 요소만을 새로운 배열로 복사하여 반환**

&#9656; 첫 번째 매개변수 : 복사의 대상이 될 원본 배열

&#9656; 두 번째 매개변수 : 원본 배열에서 복사할 시작 인덱스

&#9656; 세 번째 매개변수 : 마지막으로 복사될 배열 요소의 바로 다음 인덱스

&#8594; 전달된 인덱스 바로 전까지의 배열 요소까지만 복사됨

&#9656; 원본 배열과 같은 타입의 복사된 새로운 배열을 반환

예제
{: .label .label-purple .mt-2}
```java
int[] arr1 = {1, 2, 3, 4, 5};

int[] arr2 = Arrays.copyOfRange(arr1, 2, 4);
for (int i = 0; i < arr2.length; i++) {
    System.out.print(arr2[i] + " ");
}

//실행 결과
//3 4 
```

### fill()

**전달받은 배열의 모든 요소를 특정 값으로 초기화**

&#9656; 첫 번째 매개변수 : 초기화할 배열 

&#9656; 두 번째 매개변수 : 초기값

&#9656; 전달받은 원본 배열의 값을 변경

예제
{: .label .label-purple .mt-2}
```java
int[] arr = new int[10];

Arrays.fill(arr, 7);
for (int i = 0; i < arr.length; i++) {
    System.out.print(arr[i] + " ");
}

//실행 결과
//7 7 7 7 7 7 7 7 7 7 
```

### sort()

**전달받은 배열의 모든 요소를 오름차순으로 정렬**

&#9656; 매개변수 : 정렬할 배열

&#9656; 전달받은 원본 배열의 순서를 변경

예제
{: .label .label-purple .mt-2}
```java
int[] arr = {5, 3, 4, 1, 2};

Arrays.sort(arr);

for (int i = 0; i < arr.length; i++) {
    System.out.print(arr[i] + " ");
}

//실행 결과
//1 2 3 4 5 
```

### Arrays Methods

| 메소드	| 설명 |
|:--------|:----|
| static &#60; T&#62; List&#60;T&#62; asList(T... a)	| 전달받은 배열을 고정 크기의 리스트(list)로 변환하여 반환 |
| static int binarySearch(Object[] a, Object key)	전달받은 배열에서 특정 객체를 이진 검색 알고리즘을 사용하여 검색한 후, 그 위치를 반환 |
| static &#60;T&#62; T[] copyOf(T[] original, int newLength)	| 전달받은 배열을 특정 길이의 새로운 배열로 복사하여 반환 |
| static &#60;T&#62; T[] copyOfRange(T[] original, int from, int to)	| 전달받은 배열의 특정 범위에 해당하는 요소만을 새로운 배열로 복사하여 반환 |
| static boolean equals(Object[] a, Object[] a2) | 전달받은 두 배열이 같은지를 확인|
| static void fill(Object[] a, Object val)	| 전달받은 배열의 모든 요소를 특정 값으로 초기화 |
| static void sort(Object[] a)	| 전달받은 배열의 모든 요소를 오름차순으로 정렬 |
