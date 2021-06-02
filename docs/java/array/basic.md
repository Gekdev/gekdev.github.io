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

**같은 타입의 변수들로 이루어진 유한 집합**

배열을 구성하는 각각의 값을 배열 요소(element)라고 하며, 배열에서의 위치를 가리키는 숫자를 인덱스(index)

인덱스는 언제나 0부터 시작하며, 0을 포함한 양의 정수만을 가짐

배열도 모두 객체이므로, 각각의 배열은 모두 자신만의 필드와 메소드를 가지고 있음

note!
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
배열은 선언되는 형식에 따라 1차원 배열, 2차원 배열뿐만 아니라 그 이상의 다차원 배열로도 선언가능

하지만 현실적으로 이해하기가 쉬운 2차원 배열까지가 많이 사용됨
</div>

### Array Syntax

1. 배열 선언

    타입 : 배열 요소로 저장되는 변수의 타입을 명시
    
    배열 이름 : 배열이 선언된 후에 배열에 접근하기 위해 사용

    syntax
    {: .label .mt-2}
    <div class="code-example" markdown="1">
    1. 타입[] 배열이름;

    2. 타입 배열이름[];
    
    &#8594; 되도록 첫번째 방법을 사용하는게 좋음
    </div>
    ```java

    ```
    
    ![]()
    
2. 실제 배열 생성

    new 키워드를 사용해서 실제 배열로 생성
    
    배열길이 : 해당 배열이 몇 개의 배열 요소를 가지게 되는지 명시
    
    syntax
    {: .label .mt-2}
    <div class="code-example" markdown="1">
    배열이름 = new 타입[배열길이];
    </div>
    ```java

    ```
    
    ![]()
    
3. 선언과 생성

    syntax
    {: .label .mt-2}
    <div class="code-example" markdown="1">
    타입[] 배열이름 = new 타입[배열길이];
    </div>
    ```java

    ```
    
    ![]()
    
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





































