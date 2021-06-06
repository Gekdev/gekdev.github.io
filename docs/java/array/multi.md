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

## Conditional Statements


```java
//일차원배열, 알파벳 넣기
char[] arr = new char[26];
char ch = 'A';

for(int i=0 ; i < arr.length ; i++, ch++) {
    arr[i] = ch;
}

for(int i = 0 ; i<arr.length ; i++) {
    System.out.println(arr[i] + "," + (int)arr[i]);
}

//이차원배열, 알파벳 13행2열로 넣기
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