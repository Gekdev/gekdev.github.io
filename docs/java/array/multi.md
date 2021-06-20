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

예제
{: .label .label-purple .mt-2}
```java
int[][] arr = {
    {10, 20, 30},
    {40, 50, 60}
};
```
