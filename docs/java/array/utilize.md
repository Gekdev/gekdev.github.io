---
layout: default
title: Utilize 
parent: Array
grand_parent: Java
nav_order: 1 
---

# Java Utilize Array
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Conditional Statements

### For 

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

### Advanced For 

예제
{: .label .label-purple .mt-2}
```java
//Advanced For문
sum = 0;
for(int score:scores) {
    sum += score;
}

System.out.println("총점" + sum ); // 366
```

