---
layout: default
title: Arrays 
parent: Basic API 
grand_parent: Java
nav_order: 7
---

# Basic API Arrays
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---
Arrays 클래스
java.util 패키지
java.util 패키지에는 프로그램을 개발하는 데 사용할 수 있는 유용한 유틸리티 클래스가 다수 포함되어 있습니다.

실제로 java.lang 패키지 다음으로 가장 많이 사용되는 패키지가 java.util 패키지입니다.

하지만 import 문을 사용하지 않아도 바로 사용할 수 있는 java.lang 패키지와는 달리 java.util 패키지는 import 문으로 패키지를 불러오고 나서야 클래스 이름만으로 사용할 수 있습니다.

java.util.Arrays 클래스
Arrays 클래스에는 배열을 다루기 위한 다양한 메소드가 포함되어 있습니다.

Arrays 클래스의 모든 메소드는 클래스 메소드(static method)이므로, 객체를 생성하지 않고도 바로 사용할 수 있습니다.

이 클래스는 java.util 패키지에 포함되므로, 반드시 import 문으로 java.util 패키지를 불러오고 나서 사용해야 합니다.

binarySearch() 메소드
binarySearch() 메소드는 전달받은 배열에서 특정 객체의 위치를 이진 검색 알고리즘을 사용하여 검색한 후, 해당 위치를 반환합니다.

이 메소드는 이진 검색 알고리즘을 사용하므로, 매개변수로 전달되는 배열이 sort() 메소드 등을 사용하여 미리 정렬되어 있어야만 제대로 동작합니다.

예제
int[] arr = new int[1000];

for(int i = 0; i < arr.length; i++) {

    arr[i] = i;

}

 

System.out.println(Arrays.binarySearch(arr, 437));

코딩연습 ▶

실행 결과
437

copyOf() 메소드
copyOf() 메소드는 전달받은 배열의 특정 길이만큼을 새로운 배열로 복사하여 반환합니다.

 

copyOf() 메소드는 첫 번째 매개변수로 원본 배열을 전달받고, 두 번째 매개변수로 원본 배열에서 새로운 배열로 복사할 요소의 개수를 전달받습니다.

그리고 원본 배열과 같은 타입의 복사된 새로운 배열을 반환합니다.

 

이때 새로운 배열의 길이가 원본 배열보다 길면, 나머지 요소는 배열 요소의 타입에 맞게 다음과 같은 기본값으로 채워집니다.

배열 요소의 타입	기본값
char	'\u0000'
byte, short, int	0
long	0L
float	0.0F
double	0.0 또는 0.0D
boolean	false
배열, 인스턴스 등	null
 

예제
int[] arr1 = {1, 2, 3, 4, 5};

① int[] arr2 = Arrays.copyOf(arr1, 3);

 

for (int i = 0; i < arr2.length; i++) {

    System.out.print(arr2[i] + " ");

}

 

② int[] arr3 = Arrays.copyOf(arr1, 10);

for (int i = 0; i < arr3.length; i++) {

    System.out.print(arr3[i] + " ");

}

코딩연습 ▶

실행 결과
1 2 3 

1 2 3 4 5 0 0 0 0 0 

 

위 예제의 ①번 라인에서는 copyOf() 메소드를 사용하여 배열 arr1의 첫 번째 배열 요소부터 3개의 요소를 복사하여 배열 arr2에 대입하고 있습니다.

②번 라인에서는 배열 arr1에서 10개의 배열 요소를 복사하여 배열 arr3에 대입하려고 합니다.

하지만 배열 arr1의 길이가 5밖에 안되므로, 배열 arr3의 나머지 배열 요소에는 int형의 기본값인 0이 채워지게 됩니다.

copyOfRange() 메소드
copyOfRange() 메소드는 전달받은 배열의 특정 범위에 해당하는 요소만을 새로운 배열로 복사하여 반환합니다.

 

copyOfRange() 메소드는 첫 번째 매개변수로 복사의 대상이 될 원본 배열을 전달받습니다.

두 번째 매개변수로는 원본 배열에서 복사할 시작 인덱스를 전달받고, 세 번째 매개변수로는 마지막으로 복사될 배열 요소의 바로 다음 인덱스를 전달받습니다.

즉, 세 번째 매개변수로 전달된 인덱스 바로 전까지의 배열 요소까지만 복사됩니다.

그리고 원본 배열과 같은 타입의 복사된 새로운 배열을 반환합니다.

예제
int[] arr1 = {1, 2, 3, 4, 5};

 

int[] arr2 = Arrays.copyOfRange(arr1, 2, 4);

for (int i = 0; i < arr2.length; i++) {

    System.out.print(arr2[i] + " ");

}

코딩연습 ▶

실행 결과
3 4 

fill() 메소드
fill() 메소드는 전달받은 배열의 모든 요소를 특정 값으로 초기화해 줍니다.

 

fill() 메소드는 첫 번째 매개변수로 초기화할 배열을 전달받고, 두 번째 매개변수로 초기값을 전달받습니다.

따라서 이 메소드는 전달받은 원본 배열의 값을 변경하게 됩니다.

예제
int[] arr = new int[10];

 

Arrays.fill(arr, 7);

for (int i = 0; i < arr.length; i++) {

    System.out.print(arr[i] + " ");

}

코딩연습 ▶

실행 결과
7 7 7 7 7 7 7 7 7 7 

sort() 메소드
sort() 메소드는 전달받은 배열의 모든 요소를 오름차순으로 정렬합니다.

 

sort() 메소드는 매개변수로 정렬할 배열을 전달받으며, 따라서 이 메소드는 전달받은 원본 배열의 순서를 변경하게 됩니다.

예제
int[] arr = {5, 3, 4, 1, 2};

 

Arrays.sort(arr);

for (int i = 0; i < arr.length; i++) {

    System.out.print(arr[i] + " ");

}

코딩연습 ▶

실행 결과
1 2 3 4 5 

대표적인 Arrays 메소드
Arrays 클래스의 메소드는 매우 다양하며, 그중에서 많이 사용되는 메소드는 다음과 같습니다.

메소드	설명
static <T> List<T> asList(T... a)	
전달받은 배열을 고정 크기의 리스트(list)로 변환하여 반환함.

static int binarySearch(Object[] a, Object key)	전달받은 배열에서 특정 객체를 이진 검색 알고리즘을 사용하여 검색한 후, 그 위치를 반환함.
static <T> T[] copyOf(T[] original, int newLength)	
전달받은 배열을 특정 길이의 새로운 배열로 복사하여 반환함.

static <T> T[] copyOfRange(T[] original, int from, int to)	
전달받은 배열의 특정 범위에 해당하는 요소만을 새로운 배열로 복사하여 반환함.

static boolean equals(Object[] a, Object[] a2)	전달받은 두 배열이 같은지를 확인함.
static void fill(Object[] a, Object val)	
전달받은 배열의 모든 요소를 특정 값으로 초기화함.

static void sort(Object[] a)	
전달받은 배열의 모든 요소를 오름차순으로 정렬함.