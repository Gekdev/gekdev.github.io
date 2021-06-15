---
layout: default
title: Variable
parent: Datatype
grand_parent: Java
nav_order: 1
---

# Datatype Variable
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Variable
{: .no_toc}

### Variable Basic

**변수, 데이터(data)를 저장하기 위해 프로그램에 의해 이름을 할당받은 메모리 공간**

저장된 값은 변경될 수 있음

### Variable Name Rules

**변수뿐만 아니라 클래스, 메소드 등의 이름을 짓는데 반드시 지켜야 하는 공통된 규칙**

1. 변수의 이름은 영문자(대소문자), 숫자, 언더스코어(_), 달러($)로만 구성

2. 변수명의 길이에는 제한이 없음

3. 변수의 숫자로 시작할 수 없고 이름 사이에는 공백을 포함할 수 없음

4. 변수의 이름으로 자바에서 미리 정의된 키워드(keyword)는 사용할 수 없음

5. 첫번째 글자는 소문자로 단어 구분마다 대문자로 선언 - 카멜(관례)

6. 한글 변수명도 가능하지만 사용하지 않음 (관례)

!note
{: .label .mt-2}
<div class="code-example" markdown="1">
변수의 이름은 해당 변수에 저장될 데이터의 의미를 잘 나타내도록 짓는 것이 좋음
</div>

### Types of Variables

변수는 타입에 따라 다음과 같이 구분

1. **기본형(primitive type) 변수 : 실제 연산에 사용되는 변수**

    - 정수형 : byte, short, int, long

    - 문자형 : char

    - 실수형 : float, double

    - 논리형 : boolean

2. **참조형(reference type) 변수 : 8개의 기본형 변수를 사용하여 사용자가 직접 만들어 사용하는 변수**

    &#9656; 객체(Object)가 저장되어 있는 메모리의 주소를 참조하는 타입
    
    - 배열(Array)
    
    - 열거(Enum)
    
    - 클래스(class)
    
    - 인터페이스(Interface)등이 있음
    
    &#9656; 참조타입은 속성, 필드, 메서드 등 생성자들이 있음

![](https://gekdev.github.io/docs/java/datatype/example/ref_type.png)

### Difference between Variables

기본타입과 참조타입의 차이점

**기본타입은 실제값을 변수에 저장하는 반면 참조타입은 객체가 저장되어 있는 메모리의 주소를 값으로 갖음**

주소를 통해 객체를 참조한다는 의미에서 참조타입이라 부름

예제
{: .label .label-purple .mt-2}
```java
String name1 = "권가은";
String name2 = "권가은";
String name3 = new String("권가은");


if(name1==name2) {
    System.out.println("객체가 동일"); // 동일
}else {
    System.out.println("객체가 다름");
}
if(name1==name3) {
    System.out.println("객체가 동일");
}else {
    System.out.println("객체가 다름"); // 다름
}
if(name3==name2) {
    System.out.println("객체가 동일");
}else {
    System.out.println("객체가 다름"); // 다름
}

if(name1.equals(name3)) {
    System.out.println("문자열 값이 동일"); //동일
}else {
    System.out.println("문자열 값이 다름");
}		
if(name2.equals(name3)) {
    System.out.println("문자열 값이 동일"); //동일
}else {
    System.out.println("문자열 값이 다름");
}
```

* String Type

    &#9656; 자바는 문자열을 String참조타입변수에 저장하기 때문에 String 변수를 우선 선언해야 함
    실제로는 문자열을 String변수에 저장한다는 말은 틀린말

    &#9656; 문자열이 직접 변수에 저장되는게 아니라 문자열을 String 객체로 생성해 힙 영역에 저장하고
    String변수는 String객체가 저장되어 있는 메모리 주소를 참조함

    &#9656; 자바는 문자열 리터럴이 동일하다면 String 객체를 공유하도록 설계되어 있음

* new String

    &#9656; 문자를 저장할 경우에는 문자열리터럴을 사용하지만, new 객체생성연산자를 사용해서 직접 String 객체를 생성시킬 수 있음

    &#9656; new연산자는 힙 영역에 새로운 객체를 만들 때 사용하는 연산자로서 "객체 생성 연산자"라고 함

### Declaration Variables

**변수를 사용하기 전에 반드시 먼저 변수를 선언하고 초기화해야 함**

선언하는 방법에는 두가지가 있음 

1. 변수의 선언만 하는 방법

2. 변수의 선언과 동시에 초기화하는 방법

### Only Declaration

위 1번 방법

**먼저 변수를 선언하여 메모리 공간을 할당받고, 나중에 변수를 초기화하는 방법**

&#9656; 이렇게 선언만 된 변수는 초기화되지 않았으므로, 해당 메모리 공간에는 알 수 없는 쓰레깃값이 있음

&#9656; 선언만 된 변수는 반드시 초기화한 후에 사용해야만 함

&#8594; 자바에서는 프로그램의 안전성을 위해 초기화하지 않은 변수는 사용할 수 없도록 하고 있음 (초기화되지 않은 변수를 사용하려고 하면, 자바 컴파일러는 오류를 발생)

&#9656; 다른 타입의 데이터를 저장하려고 하면, 자바 컴파일러는 오류를 발생

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
타입 변수이름[, 변수이름];
</div>
```java
int num;                        // 변수의 선언
System.out.println(num);        // 오류 발생

int num, num1, num2;            // 같은 타입의 변수를 동시에 선언함
```

### Declaration with Initialization

위 2번 방법

**변수의 선언과 동시에 그 값을 초기화**

선언하고자 하는 변수들의 타입이 같다면 이를 동시에 선언할 수도 있음

syntax
{: .label .mt-2}
<div class="code-example" markdown="1">
타입 변수이름 = 초깃값[, 변수이름 = 초깃값];
</div>
```java
int num
num = 20;                         // 변수의 초기화

double num3 = 3.14;              // 선언과 동시에 초기화함
double num4 = 1.23, num5 = 4.56; // 같은 타입의 변수를 동시에 선언하면서 초기화함
System.out.println(num);         // 20
```

!note
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
1. 선언하고자 하는 변수의 타입이 서로 다르면 동시에 선언할 수 없음

2. 여러 변수를 동시에 초기화할 수 없음
</div>
```java
double num1, num2;        // 같은 타입의 변수를 동시에 선언함.
...
num1 = 1.23, num2 = 4.56; // 하지만 이미 선언된 여러 변수를 동시에 초기화할 수는 없음.
```

### Variable Scope

자바스크립트 변수 범위처럼 작용함 **(Local Variable / Global Variable)**

&#9656; 전역 변수는 지역에서 사용가능하고, 지역변수는 전역에서 사용할 수 없음

&#9656; 지역에서 변경한 전역변수는 그대로 값이 변경되어서 남아있음

예제
{: .label .label-purple .mt-2}
```java
public static void main(String[] args) {
    // 변수의 사용범위
    // local(지역변수) vs global(전역변수)
    int var1;
    var1 = 10;
    System.out.println("var1의 값 = " + var1);		//10
    System.out.println();

    if(true) {
        int var2;
        var1 = 20;
        var2 = 20;
        // var3 = 30; 접근 불가
        System.out.println("var1의 값 = " + var1);    //20
        System.out.println("var2의 값 = " + var2);    //20
    }

    System.out.println();

    if(true) {
        int var3;
        var1 = 30;
        var3 = 30;
        System.out.println("var1의 값 = " + var1);    //30
        System.out.println("var3의 값 = " + var3);    //30
    }   

    System.out.println("var1의 값 = " + var1);	     //30
    // System.out.println("var2의 값 = " + var2); 접근 불가능, 둘다 지역변수 이기 때문
    // System.out.println("var3의 값 = " + var3);	
}
```
