---
layout: default
title: Arithmetic
parent: Operator
grand_parent: Java
nav_order: 1
---

# Operator Arithmetic
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Arithmetic Operator

**사칙연산을 다루는 연산자**

가장 기본적이고 많이 사용됨

모두 두 개의 피연산자를 가지는 이항 연산자

결합방향 : 왼쪽 &#8594; 오른쪽

항?
{: .label .mt-2}
<div class="code-example" markdown="1">
항이란 해당 연산의 실행이 가능하기 위해 필요한 값이나 변수를 의미

따라서 이항 연산자란 해당 연산의 실행을 위해서 두 개의 값이나 변수가 필요한 연산자를 의미
</div>

|산술 연산자 |	설명 |
|:----------|:------|
|+	|왼쪽의 피연산자에 오른쪽의 피연산자를 더함|
|-	|왼쪽의 피연산자에서 오른쪽의 피연산자를 뺌|
|*	|왼쪽의 피연산자에 오른쪽의 피연산자를 곱함|
|/	|왼쪽의 피연산자를 오른쪽의 피연산자로 나눔|
|%	|왼쪽의 피연산자를 오른쪽의 피연산자로 나눈 후, 그 나머지를 반환함|

예제
{: .label .label-purple .mt-2}
<div class="code-example" markdown="1">
int num1 = 8, num2 = 4;

System.out.println("+ 연산자에 의한 결과 : "+ (num1 + num2)); //12

System.out.println("- 연산자에 의한 결과 : "+ (num1 - num2)); //4

System.out.println("* 연산자에 의한 결과 : "+ (num1 * num2)); //32

System.out.println("/ 연산자에 의한 결과 : "+ (num1 / num2)); //2

System.out.println("% 연산자에 의한 결과 : "+ (num1 % num2)); //0
</div>

---

## Increment and Decrement operators

**피연산자를 1씩 증가 혹은 감소시킬 때 사용하는 연산자**

피연산자가 단 하나뿐인 단항 연산자

해당 연산자가 피연산자의 어느 쪽에 위치하는가에 따라 연산의 순서 및 결과가 달라짐

| 증감 연산자	| 설명 |
|:----------|:------|
|++x	| 먼저 피연산자의 값을 1 증가시킨 후에 해당 연산을 진행|
|x++	|먼저 해당 연산을 수행하고 나서, 피연산자의 값을 1 증가|
|--x	|먼저 피연산자의 값을 1 감소시킨 후에 해당 연산을 진행|
|x--	|먼저 해당 연산을 수행하고 나서, 피연산자의 값을 1 감소|

### 

피연산자의 어느 쪽에 위치하는가에 따라 연산의 순서가 달라짐
