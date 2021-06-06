---
layout: default
title: Utilize 
parent: Array
grand_parent: Java
nav_order: 1 
---

# Java Array Utilize
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Array Utilize

### Copy Array 

1. System 클래스의 arraycopy() 메소드 : 가장 좋은 성능, 배열의 길이를 마음대로 늘임

2. Arrays 클래스의 copyOf() 메소드 : 가장 많이 사용되는 메소드, 배열의 길이를 마음대로 늘임

3. Object 클래스의 clone() 메소드 : 이전 배열과 같은 길이의 배열

4. for 문과 인덱스를 이용한 복사

```java
int[] arr1 = new int[]{1, 2, 3, 4, 5};
int newLen = 10;

// 1. System 클래스의 arraycopy() 메소드
int[] arr2 = new int[newLen];
System.arraycopy(arr1, 0, arr2, 0, arr1.length); 

// 2. Arrays 클래스의 copyOf() 메소드
int[] arr3 = Arrays.copyOf(arr1, 10); 

// 3. Object 클래스의 clone() 메소드
int[] arr4 = (int[])arr1.clone();

// 4. for 문과 인덱스를 이용한 복사
int[] arr5 = new int[newLen];

...
1. 1 2 3 4 5 0 0 0 0 0 
2. 1 2 3 4 5 0 0 0 0 0 
3. 1 2 3 4 5 
4. 1 2 3 4 5 0 0 0 0 0 
```

예제
{: .label .label-purple .mt-2}
```java
int[] scores = {95,7,84,93,87};
int sum = 0;

for(int i=0;i<scores.length;i++) {
    sum += scores[i];
}

System.out.println("총점" + sum ); // 366
```

### Enhanced for Statement 

JDK 1.5부터는 배열과 컬렉션의 모든 요소를 참조하기 위한 Enhanced for 문이라는 반복문이 새롭게 추가

&#9656; 명시한 배열이나 컬렉션의 길이만큼 반복되어 실행

&#9656; 루프마다 각 요소는 명시한 변수의 이름으로 저장되며, 명령문에서는 이 변수를 사용하여 각 요소를 참조할 수 있음

&#9656; 요소를 참조할 때만 사용하는 것이 좋으며, 요소의 값을 변경하는 작업에는 적합하지 않음

&#9656; Enhance for 문 내부에서 사용되는 배열 요소는 배열 요소 그 자체가 아닌 배열 요소의 복사본

&#8594; 배열 요소의 값을 변경하여도 원본 배열에는 아무런 영향을 주지 못하게 됨

예제
{: .label .label-purple .mt-2}
<div class="code-example" markdown="1">
for (타입 변수이름 : 배열이나컬렉션이름) {

배열의 길이만큼 반복적으로 실행하고자 하는 명령문;

}
</div>
```java
sum = 0;
for(int score:scores) {
    sum += score;
}

System.out.println("총점" + sum ); // 366
```
