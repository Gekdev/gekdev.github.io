---
layout: default
title: Multi Dimension
parent: Array
grand_parent: Java
nav_order: 1
---

# Java Multi Dimensional Array
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Multi-Dimension Array

**2차원 이상의 배열을 의미하며, 배열 요소로 또 다른 배열을 가지는 배열을 의미**

계속 배열을 추가하고 싶으면 []만 추가하면 됨

### Two Dimensional Array

**배열의 요소로 1차원 배열을 가지는 배열**

2차원 배열 선언 syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
1. 타입[][] 배열이름;

2. 타입 배열이름[][];

3. 타입[] 배열이름[];
</div>

![](https://gekdev.github.io/docs/java/array/example/img_java_array23.png)

### Initialize TD Array

**선언과 동시에 초기화**

syntax
{: .label .mt-2}
```java
타입 배열이름[열의길이][행의길이] = {
    {배열요소[0][0], 배열요소[0][1], ...},
    {배열요소[1][0], 배열요소[1][1], ...},
    {배열요소[2][0], 배열요소[2][1], ...},
    ...
};
```
```java
int[][] arr = {
    {10, 20, 30},
    {40, 50, 60}
};
```

### Dynamic Array

**가변 배열(dynamic array) : 행마다 다른 길이의 배열을 저장할 수 있는 배열**

2차원 배열을 생성할 때 열의 길이를 명시하지 않음으로써, 행마다 다른 길이의 배열을 요소로 저장할 수 있음

배열을 생성할 때 두 번째 첨자를 생략하면 가변 배열

가변 배열도 초기화 블록을 사용하여 배열을 선언과 동시에 초기화할 수 있음

```java
int[][] arr = new int[3][];
arr[0] = new int[2];
arr[1] = new int[4];
arr[2] = new int[1];

...
    
int[][] arr = {
    {10, 20},
    {10, 20, 30, 40},
    {10}
};
```

가변배열 출력하기
{: .label .mt-2}
```java
//2차원배열에 값을 선언하기
//int[][] korScores = {{95,60},{92,86,88,76,87}};

for(int i=0 ; i<korScores.length ; i++) {
    for(int j=0 ; j < korScores[i].length ; j++) {
        System.out.println("korScores["+i+"]["+j+"]" + korScores[i][j]);
    }
}
```

### Array Example

1. 일차원배열, 알파벳 넣기

    ```java
    char[] arr = new char[26];
    char ch = 'A';

    for(int i=0 ; i < arr.length ; i++, ch++) {
        arr[i] = ch;
    }

    for(int i = 0 ; i<arr.length ; i++) {
        System.out.println(arr[i] + "," + (int)arr[i]);
    }
    ```

2. 이차원배열, 알파벳 13행2열로 넣기

    ```java
    char[][] arr2 = new char[13][2];
    char ch2 = 'A';

    for(int i = 0 ; i< arr2.length; i++) {
        // arr2.length = 13
        for(int j = 0 ; j<arr2[i].length ; j++, ch2++) {
            arr2[i][j] = ch2;
        }
        System.out.println(arr2[i]);
    }
    ```
