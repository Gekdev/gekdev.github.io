---
layout: default
title: Operators
parent: Operator
grand_parent: Java
nav_order: 1
---

# Operators
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Arithmetic Operator

**사칙연산을 다루는 연산자**, 가장 기본적이고 많이 사용됨

&#9656; 모두 두 개의 피연산자를 가지는 이항 연산자

&#9656; 결합방향 : 왼쪽 &#8594; 오른쪽

항?
{: .label .label-red .mt-2}
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
```java
int num1 = 8, num2 = 4;

System.out.println("+ 연산자에 의한 결과 : "+ (num1 + num2));   //12

System.out.println("- 연산자에 의한 결과 : "+ (num1 - num2));   //4

System.out.println("* 연산자에 의한 결과 : "+ (num1 * num2));   //32

System.out.println("/ 연산자에 의한 결과 : "+ (num1 / num2));   //2

System.out.println("% 연산자에 의한 결과 : "+ (num1 % num2));   //0
```

![]()

---

## Assignment Operator

**변수에 값을 대입할 때 사용하는 이항 연산자**

&#9656; 피연산자들의 결합 방향은 오른쪽에서 왼쪽

&#9656; 대입 연산자와 다른 연산자를 결합하여 만든 다양한 복합 대입 연산자도 있음

| 대입 연산자	| 설명 |
|:-------------|:-----|
|=	|왼쪽의 피연산자에 오른쪽의 피연산자를 대입함 |
|+=	|왼쪽의 피연산자에 오른쪽의 피연산자를 더한 후, 결괏값을 왼쪽의 피연산자에 대입 |
|-=	|왼쪽의 피연산자에서 오른쪽의 피연산자를 뺀 후, 결괏값을 왼쪽의 피연산자에 대입 |
|*=	|왼쪽의 피연산자에 오른쪽의 피연산자를 곱한 후, 결괏값을 왼쪽의 피연산자에 대입 |
|/=	|왼쪽의 피연산자를 오른쪽의 피연산자로 나눈 후, 결괏값을 왼쪽의 피연산자에 대입 |
|%=	|왼쪽의 피연산자를 오른쪽의 피연산자로 나눈 후, 나머지를 왼쪽의 피연산자에 대입 |
|&=	|왼쪽의 피연산자를 오른쪽의 피연산자와 비트 AND 연산한 후, 결괏값을 왼쪽의 피연산자에 대입 |
|`|=`	|왼쪽의 피연산자를 오른쪽의 피연산자와 비트 OR 연산한 후, 결괏값을 왼쪽의 피연산자에 대입 |
|^=	    |왼쪽의 피연산자를 오른쪽의 피연산자와 비트 XOR 연산한 후, 결괏값을 왼쪽의 피연산자에 대입 |
|<<=	| 왼쪽의 피연산자를 오른쪽의 피연산자만큼 왼쪽 시프트한 후, 결괏값을 왼쪽의 피연산자에 대입 |
|>>=	| 왼쪽의 피연산자를 오른쪽의 피연산자만큼 부호를 유지하며 오른쪽 시프트한 후, 결괏값을 왼쪽의 피연산자에 대입 |
|>>>=   | 왼쪽의 피연산자를 오른쪽의 피연산자만큼 부호에 상관없이 오른쪽 시프트한 후, 결괏값을 왼쪽의 피연산자에 대입 |

예제
{: .label .label-purple .mt-2}
```java
int num1 = 7, num2 = 7, num3 = 7;

num1 = num1 - 3;
num2 -= 3;
num3 =- 3;

System.out.println("- 연산자에 의한 결과 : "+ num1);        //4
System.out.println("-= 연산자에 의한 결과 : "+ num2);       //4
System.out.println("=- 연산자에 의한 결과 : "+ num3);       //-3
```

![]()

---

## Increment and Decrement operators

**피연산자를 1씩 증가 혹은 감소시킬 때 사용하는 연산자**

&#9656; 피연산자가 단 하나뿐인 단항 연산자

&#9656; 해당 연산자가 피연산자의 어느 쪽에 위치하는가에 따라 연산의 순서 및 결과가 달라짐

| 증감 연산자	| 설명 |
|:----------|:------|
|++x	| 먼저 피연산자의 값을 1 증가시킨 후에 해당 연산을 진행|
|x++	|먼저 해당 연산을 수행하고 나서, 피연산자의 값을 1 증가|
|--x	|먼저 피연산자의 값을 1 감소시킨 후에 해당 연산을 진행|
|x--	|먼저 해당 연산을 수행하고 나서, 피연산자의 값을 1 감소|

### Calculate Precedence

피연산자의 어느 쪽에 위치하는가에 따라 연산의 순서가 달라짐

예제
{: .label .label-purple .mt-2}
```java
int x = 10;
int y = x-- + 5 + --x;

System.out.println("x : "+ x + ", y : " + y);
```

![](https://gekdev.github.io/docs/java/operator/example/pref.png)

① : 첫 번째 감소 연산자(decrement operator)는 피연산자의 뒤쪽에 위치하므로, 덧셈 연산이 먼저 수행

② : 덧셈 연산이 수행된 후에 감소 연산이 수행 (x의 값 : 9)

③ : 두 번째 감소 연산자는 피연산자의 앞쪽에 위치하므로, 덧셈 연산보다 먼저 수행 (x의 값 : 8)

④ : 감소 연산이 수행된 후에 덧셈 연산이 수행

⑤ : 마지막으로 변수 y에 결괏값의 대입 연산이 수행 (y의 값 : 23)

---

## Relational Operator

**피연산자 사이의 상대적인 크기를 판단하는 연산자**

&#9656; 왼쪽의 피연산자와 오른쪽의 피연산자를 비교하여, 어느 쪽이 더 큰지, 작은지, 또는 서로 같은지를 판단

&#9656; 모두 두 개의 피연산자를 가지는 이항 연산자

&#9656; 결합 방향은 왼쪽 &#8594; 오른쪽

| 비교 연산자	| 설명 |
|:-------------|:-------------------|
| ==	| 왼쪽과 오른쪽이 같으면 참 | 
| !=	| 왼쪽과 오른쪽이 같지 않으면 참| 
| >	| 왼쪽이 오른쪽보다 크면 참| 
| >=	| 왼쪽이 오른쪽보다 크거나 같으면 참| 
| <	| 왼쪽이 오른쪽보다 작으면 참| 
| <=	| 왼쪽이 오른쪽보다 작거나 같으면 참| 

```java

```

![]()

---

## Logical Operator

**주어진 논리식을 판단하여 참(true)과 거짓(false)을 결정**

AND, OR : 이항 연산자, 결합 방향: 왼 &#8594; 오른

NOT : 단항 연산자, 결합 방향 : 왼 ← 오른

| 논리 연산자	 | 설명                                        |
|:--------------|:--------------------------------------------|
|&&             | 모두 참이면 참 (논리 AND 연산)                 |
|`||`	        | 하나라도 참이면 참을 반환함. (논리 OR 연산)      |
|!	            | 결과의 반대로 반환 (논리 NOT 연산)              |

truth table
{: .label .mt-2}

| A	  | B	  | A && B	  | `A || B`  | !A    | 
|:----|:------|:----------|:----------|:------|
|true |	true  |	true      | true	  | false |
|true |	false |	false	  | true   	  | false |
|false|	true  |	false	  | true	  | true  |
|false|	false |	false	  | false	  | true  |

```java

```

![]()

---

## Ternary Operator

**조건 연산자, 유일하게 피연산자가 3개**

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
조건식 ? 반환값1 : 반환값2
</div>
```java

```

![]()

---

## instanceof Operator

**참조 변수가 참조하고 있는 인스턴스의 실제 타입을 반환**

&#9656; 해당 객체가 어떤 클래스나 인터페이스로부터 생성되었는지를 판별해 주는 역할

&#9656; 인스턴스가 클래스나 인터페이스로부터 생성되었으면 true, 아니면 false를 반환

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
인스턴스이름 instanceof 클래스또는인터페이스이름
</div>
```java
class A {}

class B extends A {}

public static void main(String[] args) {

    A a = new A();
    B b = new B();

    System.out.println(a instanceof A); // true
    System.out.println(b instanceof A); // true
    System.out.println(a instanceof B); // false
    System.out.println(b instanceof B); // true

}
```



















