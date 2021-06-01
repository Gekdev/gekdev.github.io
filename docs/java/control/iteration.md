---
layout: default
title: Iteration 
parent: Control
grand_parent: Java
nav_order: 2
---

# Java Iteration Statements 
{: .no_toc .text-beta .fw-700}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Iteration Statements 

**반복문, 똑같은 명령을 일정 횟수만큼 반복해 수행하도록 하는 명령문**

1. while 문

2. do / while 문

3. for 문

4. Enhanced for 문

### while Statement

**특정 조건을 만족할 때까지 계속해서 주어진 명령문을 반복 실행**

&#9656; 조건식이 참(true)인지를 판단하여, 참이면 내부의 명령문을 실행

&#9656; 내부의 명령문을 전부 실행하고 나면, 다시 조건식으로 돌아와 또 한 번 참인지를 판단

&#9656; 조건식의 검사를 통해 반복해서 실행되는 반복문을 루프(loop)라고 함

&#9656; 실행될 명령문이 한 줄 뿐이라면 중괄호({}) 생략가능

![](https://gekdev.github.io/docs/java/control/example/loop.png)

syntax
{: .label .mt-2}
```java
while (조건식) {
    조건식의 결과가 참인 동안 반복적으로 실행하고자 하는 명령문;
}
```

### do / while Statement

**while과는 다르게 루프를 무조건 한 번 실행한 후에 조건식을 검사**

syntax
{: .label .mt-2}
```java
do {
    조건식의 결과가 참인 동안 반복적으로 실행하고자 하는 명령문;
} while (조건식);
```

![](https://gekdev.github.io/docs/java/control/example/do_while.png)

### for Statement

**자체적으로 초기식, 조건식, 증감식을 모두 포함하고 있는 반복문**

&#9656; 실행될 명령문이 한 줄 뿐이라면 중괄호({}) 생략가능

syntax
{: .label .mt-2}
```java
for (초기식; 조건식; 증감식) {
    조건식의 결과가 참인 동안 반복적으로 실행하고자 하는 명령문;
}

초기식, 조건식, 증감식은 각각 생략가능
```

![](https://gekdev.github.io/docs/java/control/example/for.png)

### Enhanced for Statement

**명시한 배열이나 컬렉션의 길이만큼 반복되어 실행**

&#9656; 루프마다 각 요소는 명시한 변수의 이름으로 저장, 명령문에서는 이 변수를 사용하여 각 요소를 참조

&#9656; 요소를 참조할 때만 사용하는 것이 좋으며, 요소의 값을 변경하는 작업에는 적합하지 않음

&#9656; Enhance for 문 내부에서 사용되는 배열 요소는 배열 요소 그 자체가 아닌 배열 요소의 복사본

&#8594; 배열 요소의 값을 변경하여도 원본 배열에는 아무런 영향을 주지 못함

syntax
{: .label .mt-2}
```java
 for (타입 변수이름 : 배열이나컬렉션이름) {
    배열의 길이만큼 반복적으로 실행하고자 하는 명령문;
}
```

[tcp](http://tcpschool.com/java/java_array_application)

---

## Loop Control Statements

루프로 진입하면 다음 조건식을 검사하기 전까지 루프 안에 있는 모든 명령문 실행

하지만 **continue와 break는 이런 일반적인 루프의 흐름을 사용자가 직접 제어할 수 있게 도와줌**

### continue Statement

**해당 루프의 나머지 부분을 건너뛰고, 바로 다음 조건식의 판단으로 넘어감**

&#8594; 반복문 내에서 특정 조건에 대한 예외 처리를 하고자 할 때 자주 사용

예제
{: .label .label-purple .mt-2}
```java

```

### break Statement

**해당 반복문을 완전히 종료시킨 뒤, 반복문 바로 다음에 위치한 명령문을 실행**

&#8594; 루프 내에서 조건식의 판단 결과와 상관없이 반복문을 완전히 빠져나가고 싶을 때 사용

예제
{: .label .label-purple .mt-2}
```java

```

### break with label

이름을 가지는 반복문

일반적으로 break문은 단 하나의 반복문만 빠져 나가게 하기 때문에 중첩된 상황에서 한번에 모든 반복문을 빠져나가거나, 특정 반복문까지 나가게 하고싶을 때 사용

빠져나가고 싶은 특정 반복문에 이름을 설정한 후, break 키워드 다음에 해당 이름을 명시

그러면 break 키워드는 현재 반복문이 아닌 해당 이름의 반복문 바로 다음으로 프로그램의 실행을 옮김

note!
{: .label .label-yellow .mt-2}
<div class="code-example" markdown="1">
이름(label)은 가리키고자 하는 반복문의 키워드 바로 앞에 위치해야 함

이름과 반복문의 키워드 사이에 명령문이 존재하면, 자바 컴파일러는 오류를 발생
</div>

예제 : 구구단 2~4단
{: .label .label-purple .mt-2}
```java
allLoop :
for (int i = 2; i < 10; i++) {
    for (int j = 2; j < 10; j++) {
        if (i == 5) {
            break allLoop;
        }
        System.out.println(i + " * " + j + " = " + (i * j));
    }
}

//변수 i의 값이 5가 되는 순간, 해당 프로그램의 제어는 두 개의 for 문을 모두 빠져나와 종료
```
