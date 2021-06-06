---
layout: default
title: Basic 
parent: Array
grand_parent: Java
nav_order: 1
---

# Java Array Basic
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Java Array Basic

### What is Array?

**동일 타입의 데이터를 연속된 공간에 배치시키고 각 데이터에 index를 부여해서 저장하는 자료구조**

변수는 한개의 값만 저장 가능해 저장할 데이터의 수가 많아지면 그 수 만큼의 변수가 필요하게 됨 &#8594; 비효율적

배열은 좀 더 효율적인 방법으로 데이터를 저장할 수 있게 하는것

배열을 구성하는 각각의 값을 배열 요소(element)라고 하며, 배열에서의 위치를 가리키는 숫자를 인덱스(index)

인덱스는 언제나 0부터 시작하며, 0을 포함한 양의 정수만을 가짐

### Features of Array

배열도 모두 객체이므로, 각각의 배열은 모두 자신만의 필드와 메소드를 가지고 있음

배열은 참조변수로서 객체이기 때문에 힙 메모리영역에 저장되고 배열 변수는 힙영역의 배열객체의 메모리주소를 참조하게 됨

참조할 배열 객체가 없다면 배열 변수는 null값으로 초기화 할 수 있음

다차원배열?
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
배열은 선언되는 형식에 따라 1차원 배열, 2차원 배열뿐만 아니라 그 이상의 다차원 배열로도 선언가능

하지만 현실적으로 이해하기가 쉬운 2차원 배열까지가 많이 사용됨
</div>

### Constraint of Array

&#9656; 배열의 길이는 한번 정의하면 변경할 수 없음

&#9656; 동일의 데이터타입만 저장할 수 있음

### Array Syntax

1. 배열 선언

    타입 : 배열 요소로 저장되는 변수의 타입을 명시
    
    배열 이름 : 배열이 선언된 후에 배열에 접근하기 위해 사용

    syntax
    {: .label .mt-2}
    <div class="code-example" markdown="1">
    1. 데이터타입[] 배열이름;

    2. 데이터타입 배열이름[];
    
    &#8594; 되도록 첫번째 방법을 사용하는게 좋음
    </div>
    
2. 실제 배열 생성 

    1) 값의 목록으로 생성하는 방법
    
        **중괄호 안에 값을 항목(요소,element)으로 가지는 객체를 생성하는 방법**
    
        syntax
        {: .label .mt-2}
        <div class="code-example" markdown="1">
        데이터타입[] 배열이름 = {값1, ... ,값n}
        </div>
        ```java
        int[] score1 = {90,80,70,60,50};
        ```

    2) new 연산자로 생성하는 방법

        배열길이 : 해당 배열이 몇 개의 배열 요소를 가지게 되는지 명시

        syntax
        {: .label .mt-2}
        <div class="code-example" markdown="1">
        배열이름 = new 타입[배열길이];
        </div>
    
3. 선언과 생성

    syntax
    {: .label .mt-2}
    <div class="code-example" markdown="1">
    데이터타입[] 배열이름 = new 타입[배열길이];
    </div>
    ```java
    int[] score2 = new int[5];

    int score1[];
    score1 = new int[] {90,80,70,60,50};
    ```
    
### Array Initial Value

**배열 생성 시 자동으로 들어가는 초기값**

| 배열타입	| 초깃값 |
|:--------|:------|
|char	|'\u0000'|
|byte, short, int|	0|
|long	|0L|
|float	|0.0F|
|double	|0.0 또는 0.0D|
|boolean	|false|
|배열, 인스턴스 등	|null|




































